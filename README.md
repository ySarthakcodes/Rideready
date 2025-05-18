# Rideready
RideReady is a full-stack cab booking platform built using the MERN stack (MongoDB, Express.js, React.js, Node.js). It enables users to book rides in real-time, track driver locations, and manage their trip history, while providing drivers with an intuitive interface for managing ride requests.
# RideReady: Real-Time Cab Booking App - Complete Documentation

## 🚀 Overview
RideReady is a full-stack MERN application (MongoDB, Express.js, React.js, Node.js) that allows users to book rides and enables drivers to accept them in real-time. It uses WebSockets for live communication and Google Maps APIs for route data.
Cab Booking App
Category: Full Stack Development MERN

Skills Required:
HTML,CSS,Javascript,Bootstrap,React.js,Node.js,Mongo DB,Express

Project Description:

Introducing RideEase, the innovative cab booking app that simplifies your transportation needs with just a few taps. Say goodbye to the frustration of traditional taxi services and welcome the convenience of RideEase, crafted on the MERN (MongoDB, Express.js, React, Node.js) stack.

With RideEase, arranging your rides becomes effortless. Our user-friendly interface allows you to book cabs seamlessly, whether you're at home or on the move. Browse through available drivers, select your preferred vehicle type, and confirm your booking hassle-free.

Experience the flexibility of RideEase as you schedule your rides according to your convenience. Access real-time driver availability and track your cab's location in real-time. Take advantage of exclusive discounts, promotions, and loyalty rewards to make your journeys even more enjoyable.

RideEase isn't just a cab booking app; it's your ultimate transportation solution. Gain insights into your destinations, discover the best routes, and receive guidance to make informed decisions about your travel choices. Additionally, RideEase offers features like donation options for local causes or the opportunity to purchase refreshments during your ride, enhancing your overall travel experience.

Whether you're commuting to work or exploring a new city, RideEase caters to your needs. Our flexible platform adapts to your requirements, ensuring a smooth and reliable ride every time.

Say hello to the future of transportation and bid farewell to the hassles of traditional cab services. Experience the ease of RideEase, your trusted companion for every journey.
Scenario Based Case Study:-
Sarah, a frequent traveler, needed to reach the airport quickly for her flight as she was running late and couldn't find any cabs nearby. Then, she discovered a cab booking app, opened it, booked a cab to the airport, and arrived on time, thus avoiding missing her flight.

User Registration/Login:  Sarah opens the cab booking app on her smartphone and logs in with her account credentials. She is already a registered user.

Location Selection:  Sarah's current location is detected using GPS, and she enters the airport as her destination. The app suggests the nearest pickup point based on her location.

Service Selection:  Sarah chooses a standard taxi for her ride to the airport.

Ride Options and Pricing: The app displays available taxis nearby, along with their estimated fares and arrival times. Sarah selects a taxi with a reasonable fare and a short arrival time.

Booking Confirmation:  Sarah confirms the booking, and the app notifies her that a taxi has been assigned to her. She sees the driver's name, vehicle number, and estimated arrival time on her screen.

Real-time Tracking:  Sarah can track the taxi's location in real-time on the app's map. She sees the taxi approaching her pickup point and knows exactly when it will arrive.

Payment:  Sarah has saved her credit card details in the app. The fare for the ride is automatically deducted from her account once she reaches her destination.

Booking History:  Sarah can view the details of her ride in the app's booking history, including the date, time, location, fare, and driver details.

Customer Support:  If Sarah encounters any issues during the ride, she can contact customer support through the app for assistance.


Technical Architecture:
![image](https://github.com/user-attachments/assets/fd770caa-281b-42e5-b7e1-791bdb8239bf)


• User Interface: The intuitive web interface that allows users to interact with the system, enabling them to explore destinations, select activities, and complete bookings effortlessly.	

• Web Server: Hosts the user interface, serving dynamic web pages to users and ensuring a smooth experience throughout their Cab Booking process.

• API Gateway: Serves as the central entry point for client requests, directing them to the relevant services within the system, ensuring efficient communication and data flow.

• Authentication Service: Manages user authentication and authorization, ensuring secure access to the system and protecting sensitive user information during the cab booking and booking process.

• Database: Stores persistent data related to trip destinations, activity bookings, user profiles, payments, and other essential entities crucial to the cab booking system.

• Driver Management Service: Manages information about available drivers, including their availability, location, and ratings, ensuring efficient matching with customer ride requests.

• Booking Service: Facilitates the booking process, allowing users to request rides, specify their pick-up and drop-off locations, and track the status of their bookings in real-time.

RideEase's MERN-based architecture ensures a robust and scalable platform, empowering users to book rides effortlessly and travel with confidence.
---

## 📁 Repository Structure
```
RideReady/
├── backend/                 # Server-side logic
│   ├── controllers/         # Handle requests and responses
│   ├── models/              # MongoDB schemas
│   ├── routes/              # API route definitions
│   ├── services/            # Business logic (APIs, utilities)
│   ├── middleware/          # Authentication and request handling
│   ├── config/              # DB and environment configuration
│   ├── socket.js            # Real-time Socket.IO server
│   ├── server.js            # Entry point of backend app
│
├── frontend/                # Client-side logic
│   ├── public/              # Static files
│   ├── src/
│   │   ├── components/      # Reusable UI components
│   │   ├── pages/           # Route-based views
│   │   ├── App.js           # Main React component
│   │   ├── index.js         # Entry point of frontend app
```

---

## 🔧 Backend - Detailed Breakdown

### 1. `server.js`
- Starts the Express app
- Connects to MongoDB using `mongoose`
- Configures middleware like `cors` and `express.json()`
- Initializes Socket.IO for real-time communication

### 2. `socket.js`
- Sets up event listeners for:
  - Driver location updates
  - Ride requests and responses
  - Trip status notifications

### 3. Authentication Middleware - `auth.middleware.js`
- Verifies JWT tokens
- Attaches user info to `req.user` if valid

### 4. Captain Module (Driver Logic)
- **Model**: `captain.model.js` defines driver schema (location, availability, etc.)
- **Controller**: `captain.controller.js` handles requests (register, update location)
- **Service**: Business logic for CRUD operations
- **Routes**: API endpoints like `/api/captains/update-location`

### 5. Ride Module
- **Model**: `ride.model.js` defines ride schema (pickup, drop, driverId, status)
- **Controller**: `ride.controller.js` manages ride flow (create, accept, complete)
- **Service**: Handles DB interactions and logic
- **Routes**: `/api/rides/request`, `/api/rides/accept`

### 6. Map & Directions
- **Service**: `map.service.js` calls Google Maps APIs
- **Controller/Routes**: Serve route details to frontend

---

## 🌐 Frontend - Detailed Breakdown

### 1. `App.js` and Routing
- Uses `react-router-dom` for navigation between pages (Login, Book Ride, Live Map, History)

### 2. Pages
- **Login/Register**: Authenticates and stores token
- **Home**: Search for cabs
- **Live Map**: Displays route, live driver tracking
- **History**: Past rides shown

### 3. Components
- **Header/Nav**: Navigation bar
- **RideCard**: Info on ongoing/past rides
- **MapComponent**: Shows routes using Google Maps API

### 4. Real-Time Flow
- Connects to backend via `socket.io-client`
- Listens for `ride-request`, `ride-accepted`, `location-update`
- Updates state and UI instantly on new events

### 5. Ride Booking Flow
1. User picks source and destination.
2. App estimates fare using map service.
3. Sends request to backend → broadcast to drivers.
4. First available driver accepts.
5. Live tracking begins.

---

## 🔐 Security Features
- JWT-based authentication
- Protected routes (middleware)
- Cross-Origin Resource Sharing (CORS) config

---

## 🛠 Running the App

### Backend:
```bash
cd backend
npm install
npm run dev
```

### Frontend:
```bash
cd frontend
npm install
npm start
```

---

## 📌 Future Enhancements
- Payment gateway integration
- Rating & reviews
- Admin dashboard for managing users and rides

---

## 👨‍🏫 For New Developers
1. Clone the repo.
2. Install dependencies in both `backend` and `frontend`.
3. Set up `.env` with Mongo URI, JWT secret, Google Maps API key.
4. Explore API endpoints using Postman.
5. Start playing with the React frontend and Socket.IO events.



Ideation Phase
Define the Problem Statements

Date	26 April 2025
Team ID	145219
Project Name	Rideready cab booking app
Maximum Marks	2 Marks

Customer Problem Statement Template:
Create a problem statement to understand your customer's point of view. The Customer Problem Statement template helps you focus on what matters to create experiences people will love.
A well-articulated customer problem statement allows you and your team to find the ideal solution for the challenges your customers face. Throughout the process, you’ll also be able to empathize with your customers, which helps you better understand how they perceive your product or service.

 ![Screenshot (113)](https://github.com/user-attachments/assets/65ca508b-659f-418f-8a17-d332de0342ce)


Ideation Phase
Empathize & Discover

Date	26April 2025
Team ID	145219
Project Name	Rideready-cab booking app
Maximum Marks	4 Marks

Empathy Map Canvas:
An empathy map is a simple, easy-to-digest visual that captures knowledge about a user’s behaviours and attitudes. 

It is a useful tool to helps teams better understand their users.
Creating an effective solution requires understanding the true problem and the person who is experiencing it. The exercise of creating the map helps participants consider things from the user’s perspective along with his or her goals and challenges.
 
![image](https://github.com/user-attachments/assets/6b5d4d5f-af70-4dc8-bdf8-a40b9c1c7a4a)


screenshots

![ride screenshot](https://github.com/user-attachments/assets/ef285fd3-909b-4cd0-a21f-242f9168f355)
![RideReady App_ Vehicle Options and Map](https://github.com/user-attachments/assets/4b2e558e-59e5-4bdd-b500-72b5081e3c46)



