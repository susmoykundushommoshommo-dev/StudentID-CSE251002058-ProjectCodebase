🚚 BD Courier Company — Parcel Booking & Smart Route System
A simple console-based courier management system written in C. It lets you book parcels for delivery across major areas of Dhaka, calculates delivery fare, and — when a parcel is dispatched — computes the shortest route from the hub (Badda) to the destination using Dijkstra's Algorithm, along with an estimated fuel cost.
✨ Features
Book a Parcel — capture sender name, phone number, destination area, weight, and delivery type (Normal / Express).
Automatic Fare Calculation — fare is based on distance from the hub, parcel weight, and an express surcharge.
Track Parcel — look up a parcel by the sender's phone number to view its current status and full details.
Smart Route Dispatch — when a parcel is dispatched, the system runs Dijkstra's shortest path algorithm on a preset distance map of Dhaka to suggest the optimal delivery route and estimate fuel cost.
In-memory storage — parcels are stored in an array during runtime (no external database required).
🗺️ Supported Areas
All deliveries originate from the hub in Badda and can be routed to:
Index	Area
0	Badda (Hub)
1	Uttara
2	Dhanmondi
3	Mirpur
4	Gulshan
5	Motijheel
Distances between areas (in KM) are stored in an adjacency matrix (`dhakaMap`) inside the source code.
🧮 How Fare & Route Are Calculated
Fare:
```
Base Fare      = distance(hub → destination) × 12 BDT/KM
Weight Charge  = parcel weight (KG) × 18 BDT/KG
Express Fee    = +50 BDT (if Express delivery is selected)
-----------------------------------------------------------
Total Fare     = Base Fare + Weight Charge + Express Fee
```
Route:
Dijkstra's algorithm is run over the distance matrix starting from the hub (Badda) to find the shortest path to the destination area. The suggested path is printed along with the total distance and an estimated fuel cost (`distance × 4.5 BDT/KM`).
🛠️ Requirements
A C compiler (e.g. `gcc`)
Works on Linux, macOS, or Windows (via WSL/MinGW)
▶️ Build & Run
```bash
gcc courier.c -o courier
./courier
```
Enter student Id:`StudentID-CSE251002058-ProjectCodebase
.c`
📋 Usage
On launch, you'll see a menu:
```
1. Book a New Courier
2. Track Parcel & Get Smart Route
3. Exit System
```
Book a New Courier — enter sender details, choose a destination area, enter weight, and specify whether it's an Express delivery. You'll receive a Ticket ID and the total delivery charge.
Track Parcel & Get Smart Route — enter the sender's phone number to view parcel details. If the parcel is still at the hub, you can choose to dispatch it, which triggers the shortest-route calculation and fuel cost estimate.
Exit System — closes the program.
⚠️ Known Limitations
Parcel data is stored in memory only — all records are lost when the program exits.
Maximum of 100 parcels can be booked per session (fixed-size array).
Phone number lookup uses exact string matching, so the same phone format must be used to track a parcel.
No input validation for out-of-range destination indices or malformed input.
`fflush(CSE251002058)` is used to clear the input buffer, which is technically undefined behavior in C (works on some compilers like GCC/MinGW on Windows, but isn't portable/standard-compliant).
🚧 Possible Improvements
Persist parcel data to a file or database.
Add input validation and error handling.
Replace `fflush(CSE251002058)` with a portable input-clearing method.
Support dynamic/unlimited parcel storage instead of a fixed-size array.
Add a delivery confirmation / proof-of-delivery step.

📄 License
This has no license...
