---
title: "Need a app to scan my network..."
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2007-08-27
something that pings the entire range of the network.
There is a Windows utility named LanHelper that does that, but I'm no longer a 
windows user.

thanks for your help.

---

### Post by spd106 on 2007-08-27
The best tool to use is nmap. It's a cli tool with lots of options for scanning networks, but there is also a gui front end available separately (nmapfe). 

You can find current stable version in the universe repository, though if you want the latest and greatest you can download and build it from source quite easily.

---

### Post by xeo_pt on 2007-08-27
spd106:
thanks a lot for your help nmap works perfectly, and it only needs a line to do the job:

nmap -sP 192.168.50.0/24

scans the network in the range 192.168.0.1 to 192.168.0.255 to check if are anything connected.

Thanks a lot.

---

