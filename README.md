# multi-state-static-routing
Packet Tracer project demonstrating multi-state static routing configuration.
 
Packet Tracer Network Documentation
Project Title: Multi-State Enterprise Network
Author: Sourav Barua
Date: July 29, 2025
________________________________________
1. Overview
This is a multi-location simulated enterprise network topology in Cisco Packet Tracer, featuring interconnected routers for five U.S. states: NY, NJ, PA, VA, and FL. Each location includes its own subnet, switches, and end devices. The network simulates realistic enterprise communication with static routing, serial and Gigabit connections, and access to a shared data center in Florida (FL) hosting a server, printer, and IP phone.
________________________________________
2. IP Addressing and Subnet Map
Location	Subnet	Router Interface	Notes
NY	192.168.1.0/24	Gi0/0	PCs (PC6, PC7)
NJ	195.168.1.0/24	Gi0/0	PCs (PC12, PC13)
VA	194.168.1.0/24	Gi0/0	PCs (PC10, PC11)
PA	193.168.1.0/24	Gi0/0	PCs (PC8, PC9)
FL	200.168.1.0/24	Gi0/0	Printer, IP Phone, Server
________________________________________
3. Inter-Router WAN Links
Connection	Serial Interface (Source → Destination)	IP/Subnet
NY ↔ NJ	S0/0/1 ↔ S0/1/1	199.168.1.0/24
NY ↔ PA	S0/1/0 ↔ S0/1/1	196.168.1.0/24
NJ ↔ VA	S0/0/1 ↔ S0/0/1	198.168.1.0/24
PA ↔ VA	S0/0/1 ↔ S0/1/1	197.168.1.0/24
VA ↔ FL	S0/0/0 ↔ S0/0/0	201.168.1.0/24
PA ↔ FL	S0/0/0 ↔ S0/1/1	202.168.1.0/24
NY ↔ FL	S0/0/0 ↔ S0/0/1	203.168.1.0/24
NJ ↔ FL	S0/0/0 ↔ S0/1/0	204.168.1.0/24
________________________________________
⚙️ 4. Static Routing Summary
Each router is using static routing to reach non-directly connected networks. Below is an example of notable static routes:
NY Router
•	Has direct access to 192.168.1.0, 196.168.1.0, 199.168.1.0, 203.168.1.0
•	Static routes to:
o	193.168.1.0 via 196.168.1.0 (PA)
o	195.168.1.0 via 199.168.1.0 (NJ)
o	200.168.1.0 via 203.168.1.2 (FL)
NJ Router
•	Connected to 195.168.1.0, 198.168.1.0, 199.168.1.0, 204.168.1.0
•	Static routes to:
o	192.168.1.0 via 199.168.1.0 (NY)
o	200.168.1.0 via 204.168.1.2 (FL)
VA Router
•	Direct access to 194.168.1.0, 197.168.1.0, 198.168.1.0, 201.168.1.0
•	Static routes to:
o	192.168.1.0 via 197.168.1.1 (NY via PA)
o	200.168.1.0 via 201.168.1.2 (FL)
PA Router
•	Directly connected to 193.168.1.0, 196.168.1.0, 197.168.1.0, 202.168.1.0
•	Static routes to:
o	192.168.1.0 via 196.168.1.0 (NY)
o	200.168.1.0 via 202.168.1.2 (FL)
FL Router
•	Direct access to 200.168.1.0 (data center), 201.168.1.0, 202.168.1.0, 203.168.1.0, 204.168.1.0
•	Static routes to:
o	192.168.1.0 via 203.168.1.1 (NY)
o	193.168.1.0 via 202.168.1.1 (PA)
o	194.168.1.0 via 201.168.1.1 (VA)
o	195.168.1.0 via 204.168.1.1 (NJ)
________________________________________
5. Devices Overview
•	Switches: 2960-24TT at each site
•	End Devices:
o	PCs at all branch locations
o	Florida site includes:
	Server0 (Data center access)
	Printer0
	IP Phone 7960
________________________________________
📡 6. Routing Table Validation
All routing tables show a consistent use of /24 static routes and directly connected routes. No default route (0.0.0.0) or dynamic protocols are used.
________________________________________


