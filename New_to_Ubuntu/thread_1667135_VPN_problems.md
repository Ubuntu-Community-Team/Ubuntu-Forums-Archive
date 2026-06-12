---
title: "VPN problems"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-01-14
I am trying to set up a VPN using OpenVPN on my network at home.  When I go to the network connections through system > preferences > network connections and then go to the VPN tab and click on add I only get Point-to-Point Tunneling Protocol as an option.  On my laptop I get PPTP and an OpenVPN option.  My question is how do I add the OpenVPN option to my desktop.  I want that to be the server of my VPN.

---

### Post by djyoung4 on 2011-01-15
bump

---

### Post by smuthavarapu on 2011-01-15
This is what I do when I want to connect to My office via VPN.

Install "network-manager-vpnc" Synaptics

Then open the "Network Managers", Go to VPN, and Import the pcf file.

That will do for me. no Extra packages  needed.

---

### Post by djyoung4 on 2011-01-18
> **smuthavarapu said:**
> This is what I do when I want to connect to My office via VPN.

Install "network-manager-vpnc" Synaptics

Then open the "Network Managers", Go to VPN, and Import the pcf file.

That will do for me. no Extra packages  needed.

that was close to what I was looking for.  
```
sudo apt-get install network-manager-openvpn
```
that worked for me.  thank you though

---

