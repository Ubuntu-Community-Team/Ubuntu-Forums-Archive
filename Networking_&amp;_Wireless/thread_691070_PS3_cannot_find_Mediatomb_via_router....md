---
title: "PS3 cannot find Mediatomb via router..."
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by roger4306 on 2008-02-08
Hi,

- Ubuntu 7.10
- Mediatomb
- Router: D-LINK DIR-655

Before I got the router, PS3 did find and streamed media from server trough the Network supplier box on the wall, which I guess worked as a HUBor switch.

Here is my problem:
After using the router, PS3 are online on internett (wireless), but it can't see Mediatomb. I guess because this worked without the router, this is a configuration issue. Please help me with this one.:confused:



Rgds,
Roger

---

### Post by Nicklas Overgaard on 2008-02-08
Hi,

Maybe your router does not allow devices connected to the wireless access to the devices connected on the ethernet ports.

It it possible for you to connect the PS3 to an ethernet port in the router and check if the problem persists?

---

### Post by fanpan on 2008-03-06
I had this problem too. I solved it by starting mediatomb with the -i option to specify the IP Adress. Find out which IP adress is assigned to your computer and start up with "sudo mediatomb -i xxx.xxx.xxx.xxx"

---

