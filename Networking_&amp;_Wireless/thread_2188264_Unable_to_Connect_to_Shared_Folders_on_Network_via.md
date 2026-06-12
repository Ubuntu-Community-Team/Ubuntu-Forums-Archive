---
title: "Unable to Connect to Shared Folders on Network via Wireless"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by rsepostproduction on 2013-11-16
Hi Guys

I'm having a bit of a strange problem, and all my research through forums has led me to absolutely no solutions. Kindly help.

I have multiple machines connected to a network. A few running Windows 7, a few running Mac OSX Mavericks, and a few running Ubuntu. I have an old machine running Lubuntu 13.10 which I use just to store and share files over the network. I have a folder on this Lubuntu workstation shared, which is currently accessible without any issues from the Windows and Mac workstations via wired ethernet and wireless as well.

The trouble seems to be my laptop machines running Ubuntu 13.10 connecting to the network via wireless. On these laptops, the WiFi works fine in terms of accessing the internet. However, when I double-click on the "Network Servers" icon, it just stalls and times out, until I get a pop-up saying [Could not display "network:///". The file is of an unknown type.] It gives me an option to select the application to open with. I select "files" and it shows me the workgroups I have on my network. When I double-click on a particular workgroup, it says "Unable to access location. Failed to retrieve shared list from server: Connection timed out."

I am at a complete loss as to what I have to do. I have all the necessary Samba packages installed. This is especially puzzling because I have no issues accessing this workgroup and machines shared on it via Windows and Mac based computers.

Thank you in advance for your help.

---

### Post by TheFu on 2013-11-17
Having wifi and wired on the same subnet is asking for trouble. Pick 1.
The output from **route** will help too. Basically, the network stack gets confused when there are 2 interfaces on the same subnet.

If the interfaces are on different networks, check that the default route for each is reasonable.

---

### Post by bab1 on 2013-11-17
> **TheFu said:**
> Having wifi and wired on the same subnet is asking for trouble. Pick 1.
Why do you say that?  I don't see any Ethernet or TCP/IP reason why these two connection methods can't coexist in the same network (subnet).

---

### Post by TheFu on 2013-11-17
They definitely CAN coexist, but then the admin has accepted the responsibility to handle routing manually. The automatic method never works here. For a beginner, that is asking alot.

---

### Post by bab1 on 2013-11-17
> **TheFu said:**
> They definitely CAN coexist, but then the admin has accepted the responsibility to handle routing manually. The automatic method never works here. For a beginner, that is asking alot.
What routing differences?  If they are all on the same subnet they all have the same gateway.

---

### Post by bab1 on 2013-11-17
> **rsepostproduction said:**
> 
The trouble seems to be my laptop machines running Ubuntu 13.10 connecting to the network via wireless. On these laptops, the WiFi works fine in terms of accessing the internet. However, when I double-click on the "Network Servers" icon, it just stalls and times out, until I get a pop-up saying [Could not display "network:///". The file is of an unknown type.] It gives me an option to select the application to open with. I select "files" and it shows me the workgroups I have on my network. When I double-click on a particular workgroup, it says "Unable to access location. Failed to retrieve shared list from server: Connection timed out."

The problem here appears to be a Samba problem.  Post the output from the terminal of this command ```
smbtree -d3
```

---

### Post by TheFu on 2013-11-18
I've had the same symptoms when using this sort of setup. Removing one or the other network connection solved it.  I think it was due to there being 2 "correct" routes to the other machines AND the metrics for both being identical. It has never been worth figuring out for me. Much easier to just turn off wifi.

---

### Post by bab1 on 2013-11-18
> **TheFu said:**
> I've had the same symptoms when using this sort of setup. Removing one or the other network connection solved it.  I think it was due to there being 2 "correct" routes to the other machines AND the metrics for both being identical. It has never been worth figuring out for me. Much easier to just turn off wifi.

The symptom  "Failed to retrieve shared list from server" is typically a LAN problem and therefore does not involve a route to anywhere.   As a mater of fact the OP states that his Internet connectivity is fine ( "the WiFi works fine in terms of accessing the internet"), so the LAN gateway is correctly configured.  Respectfully, this is a Samba problem not a internetworking problem.

---

