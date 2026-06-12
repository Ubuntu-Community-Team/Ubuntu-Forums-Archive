---
title: "Atheros AR8132 Fast Ethernet - network failure"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by daria2 on 2013-09-28
Hi there, first time user here. Downloaded Lubuntu 13.04, can't seem to get my wired connection working.
Trying to connect at my workplace with my Asus EEE laptop, which worked great when I had windows. 
In "Network connections" I filled out all the IPv4 settings that worked for me in the past.
When running ifconfig i have data for et0, lo and wlan0. An hour ago network connections claimed I had internet access (pages in chromium did not load, however), now it's not connecting at all :\

Tried google and digged through the forums - no luck.

Please help!

---

### Post by Iowan on 2013-09-28
Are you configuring a static address, or DHCP?
Is **ifconfig** showing a valid IP address?

---

### Post by daria2 on 2013-09-28
Not sure about static or DHCP, I chose 'manual' when editing the connection. And ifconfig is indeed showing a valid ip.

---

### Post by daria2 on 2013-09-28
wait, now i see that the ip in ifconfig is different from what i entered...

---

### Post by Iowan on 2013-09-28
With a manual setup, you will probably need to set up routing information, also (maybe you already did). 
You might try an Automatic (DHCP) configuration - you can always change it back...

(Oops,  busy typing)

---

### Post by daria2 on 2013-09-28
Tried both automatic options, but no luck.
I'm trying to connect to a private network at my workplace, and have had no problem when used windows XP.

Could the reason be that IP address? It's strange, i'm changing to valid addresses manually, but when checking ifconfig, another address appears. I know that that address is used by another computer on the network :/

---

### Post by daria2 on 2013-09-28
Restarted the computer and it was fixed XD

Thanks for the help, Iowan!

---

