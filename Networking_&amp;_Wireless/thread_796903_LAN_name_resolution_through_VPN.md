---
title: "LAN name resolution through VPN"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Merlus on 2008-05-16
I have Poptop installed on Ubuntu 7.10. The machine is running Shorewall firewall, and functions as the gateway to my network.

I have created the VPN tunnel, and I can connect to the VPN, I can ping all LAN IP addresses, I have internet access through the VPN.

However, I cannot ping by name, computers on my LAN. It is strange because I CAN ping one of them and it works sometimes, I have had a look and I cannot see anything that differentiates this machine to others. It was previously a DNS server and PPTP VPN server windows 2003, but I have since removed both server roles for testing, and I could still resolve that address by name when connected to the VPN.

The PPTP connection is assigned DNS and WINS entries, but nslookup shows the local dns server at the client side and not the DNS server in my network.

Please help if you can, I can provide any other information that may be usefull, just bear in mind this setup is almost completely working bar the name resolution of local addresses.

---

