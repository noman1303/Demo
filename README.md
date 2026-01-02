
📍 Nearby Places Finder (SwiftUI)

A modern SwiftUI iOS app that allows users to search for nearby places such as ATMs, restaurants, spas, hospitals, cafés, and more — similar to Google Maps search experience.

The app automatically detects the user’s location, displays the location name (city/state), and shows nearby places in a clean, professional UI.

⸻

✨ Features
	•	🔍 Search anything (ATM, spa, restaurant, hospital, etc.)
	•	📍 Auto-detects current user location
	•	🏙️ Shows human-readable location name (not latitude/longitude)
	•	🧭 Nearby search using real-world place data
	•	⏳ Loading indicator while searching
	•	🧱 Professional card-based UI
	•	🆓 Uses free Google Places API credits
	•	🧼 Clean MVVM architecture
	•	⚡ Built entirely with SwiftUI

⸻

📱 App Preview (Behavior)

📍 Ahmedabad, Gujarat, India
[ Search ATM, spa, restaurant... ]

🔴 HDFC ATM
   Near CG Road, Ahmedabad

🔴 Relax Spa
   Navrangpura, Ahmedabad


⸻

🏗️ Project Architecture (MVVM)

NearbyPlacesApp
│
├── Models
│   └── Place.swift
│
├── Services
│   ├── LocationManager.swift
│   └── PlacesAPIService.swift
│
├── ViewModels
│   └── PlacesViewModel.swift
│
├── Views
│   └── ContentView.swift
│
└── NearbyPlacesAppApp.swift


⸻

🧠 How This Project Works

1️⃣ Get User Location (Apple – Free)
	•	Uses CoreLocation
	•	Requests user permission
	•	Fetches latitude & longitude
	•	Converts coordinates into city/state/country using reverse geocoding

➡ No Google API required for location name.

⸻

2️⃣ User Searches a Place

User types:

atm
spa
restaurant
coffee shop


⸻

3️⃣ Call Places API (Text Search)

The app sends a request to the Places Text Search API from Google Maps:

https://maps.googleapis.com/maps/api/place/textsearch/json

With parameters:
	•	Search text (atm near me)
	•	User latitude & longitude
	•	Radius (nearby area)
	•	API key

⸻

4️⃣ API Returns Nearby Places

The response includes:
	•	Place name
	•	Address
	•	Location details

The app parses the JSON and converts it into Swift models.

⸻

5️⃣ Display Results (SwiftUI)
	•	Shows results in card-style UI
	•	Uses LazyVStack for performance
	•	Shows loading indicator during search

⸻

🧩 Code Explanation (Key Files)

⸻

📦 Place.swift

Model representing a place result.

struct Place: Identifiable {
    let id = UUID()
    let name: String
    let address: String
}


⸻

📍 LocationManager.swift
	•	Requests location permission
	•	Fetches user coordinates
	•	Converts coordinates to city/state name

@Published var locationName: String = "Fetching location..."

Uses CLGeocoder (Apple, free).

⸻

🌐 PlacesAPIService.swift

Handles API communication.
	•	Builds request URL
	•	Calls Places Text Search API
	•	Parses JSON response
	•	Returns [Place]

func searchPlaces(query: String, location: CLLocation, completion: @escaping ([Place]) -> Void)


⸻

🧠 PlacesViewModel.swift

Business logic layer.
	•	Handles search input
	•	Manages loading state
	•	Connects API results to UI

@Published var places: [Place] = []
@Published var isLoading: Bool = false


⸻

🎨 ContentView.swift

UI layer.
	•	Displays location name
	•	Search bar
	•	Loading indicator
	•	Results list (cards)

Uses:
	•	@StateObject
	•	LazyVStack
	•	Custom PlaceCardView

⸻

🔑 How to Get Google Places API Key (Step-by-Step)

1️⃣ Open Google Cloud Console

👉 https://console.cloud.google.com/

2️⃣ Create a Project
	•	Click New Project
	•	Give it a name

3️⃣ Enable Places API
	•	APIs & Services → Library
	•	Search Places API
	•	Enable it

4️⃣ Create API Key
	•	APIs & Services → Credentials
	•	Create Credentials → API Key

5️⃣ Use the API Key in Code

private let apiKey = "YOUR_API_KEY_HERE"


⸻

💰 Is This API Free?

✅ Yes (for learning & small apps)
	•	Google provides free monthly credits
	•	This project easily stays within free limits
	•	No backend required
	•	Billing account is needed, but no charge if under limit

👉 Perfect for:
	•	Learning
	•	Portfolio
	•	Demo apps
	•	Interview projects

⸻

🔐 Security Note (Important)
	•	❌ Do NOT commit your API key to GitHub
	•	Use key restrictions in production
	•	For development, restriction can be None

⸻

🛠 Requirements
	•	Xcode 15+
	•	iOS 16+
	•	SwiftUI
	•	Internet connection
	•	Location permission enabled

⸻

🚀 Possible Enhancements
	•	🔍 Autocomplete suggestions (Google Maps style)
	•	🗺️ Map view with pins
	•	📍 Distance from user (km)
	•	⭐ Ratings & open/close status
	•	🧭 Directions via Apple Maps
	•	🧪 Unit testing

⸻

🎯 Why This Project Is Good for Learning
	•	Real-world API usage
	•	Clean MVVM structure
	•	Modern SwiftUI UI
	•	Location-based logic
	•	Interview-ready explanation

⸻

📄 License

This project is for educational and learning purposes.
Google Places API usage must comply with Google’s terms.

⸻
 
