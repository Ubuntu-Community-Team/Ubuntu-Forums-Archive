---
title: "network-manager and changing mac address... Problems!"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by talz13 on 2006-10-17
I finally got network manager working, WPA working, and got a stable connection with my wireless.  However, I have to change my MAC address for my school wifi connection since I changed wireless cards a couple months ago (I was on windows before and just changed it with an app).

Now that I have Ubuntu set up, I tried adding the line like:
```
#pre-up ifconfig eth1 hw ether xx:xx:xx:xx:xx:xx
```
but then the wireless connection won't come up.  If I comment that line out it'll work again after I reboot.

Is there a way I can change the MAC address while continuing to use network manager?

---

### Post by talz13 on 2006-10-17
I really need to get this figured out until I have time to get down to the campus networking people to get my new MAC updated on their list!

---

### Post by talz13 on 2006-10-17
OK, all is well as I have updated them with my new MAC... It was just easier and I happened to have a little time this morning to get it done.

If anybody does have any solutions to that problem, though, please post so others may find out if they really need it!

---

