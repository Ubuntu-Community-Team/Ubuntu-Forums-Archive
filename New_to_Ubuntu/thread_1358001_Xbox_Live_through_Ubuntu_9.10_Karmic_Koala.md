---
title: "Xbox Live through Ubuntu 9.10 Karmic Koala"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-12-17
I have a 360 and rather than pay $100 for the wireless adapter, I have always ran it through my laptop and used that to get onto Xbox live. I recently switched from Vista (which I used for Xbox live) to Ubuntu 9.10 and I was wondering if/how to get your Xbox online through my laptop

---

### Post by jamieleshaw on 2009-12-17
Hello, please have a look at [http://ubuntuforums.org/showthread.php?t=508145](http://ubuntuforums.org/showthread.php?t=508145)

---

### Post by marshmallow1304 on 2009-12-18
^That should work, but I don't think it needs to be that complicated.  9.10 has excellent setup for internet connection sharing.


Right-click on the network manager in the tray and select "Edit Connections...".  Navigate to the Wired tab and find your wired connection (probably eth0).  Select it and click "Edit..." Select the IPv4 Settings tab and change Method to "Shared to other computers".  Click apply.
I'm not familiar with Xbox, but I assume it can use DHCP?  If yes, you should be all set.  If not, configure the Xbox like so

IP Address: 10.42.43.10
Subnet Mask: 255.255.255.0
Gateway: 10.42.43.1


Remember to reset eth0 to Automatic if you need to use the wired connection for connecting the laptop to a network.

---

### Post by Captainflowers91 on 2009-12-18
YES!!!!!!!!!!!! [marshmallow1304]("http://ubuntuforums.org/member.php?u=663154"), you are a genius, it worked like a charm, I tried following the guide, but it wouldn't work out. Its working perfectly now, thanks a ton, I didn't even need to change my IP address or anything, it linked to live automatically.

---

### Post by totheleft on 2009-12-18
Thanks from me as well marshmellow1304 as i had no idea how to do that either.

---

