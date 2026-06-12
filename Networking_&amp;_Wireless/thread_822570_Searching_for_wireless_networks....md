---
title: "Searching for wireless networks..."
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Drumm3r4lyfe on 2008-06-08
Hey,

I'm new to Linux, and I just managed to install Ubuntu 8.04. After I started using Linux it was a blast! I managed to get it connected to the internet, and do some browsing. But after I shut it down and restarted, I could not manage to connect to the internet anymore.:confused:

Things that I should tell you:
-Im using a Belkin wireless G network adapter Part#(F5D7050)
-I accidentally removed the little icon that lets you choose what network to connect to in the task bar
-I'm totally new to Linux, and Im O.K. with Windows, but I'm still a newbie, so try to keep things simple. 

I think the only thing I need to do is to find out how I can get that little gadget that lets you connect to a wireless network running. :(

Thanks in advance,

<Drumm3r>

---

### Post by Drumm3r4lyfe on 2008-06-08
Can anyone help me?

<Drumm3r>

---

### Post by rlzyoner on 2008-06-08
-I accidentally removed the little icon that lets you choose what network to connect to in the task bar

Run the command
nm-applet 

This should bring back the icon you mentioned.

Ensure that your wireless adaptor is enabled.
Run this command

ifconfig wlan0 up (change wlan0 to the name of your wireless adaptor)
To find this, run the command iwconfig

---

### Post by Drumm3r4lyfe on 2008-06-08
Thanks!

I'll boot to ubuntu and try it out...

<Drumm3r>

---

### Post by rlzyoner on 2008-06-09
No problem, let me know if you still have any issues.
Peace

---

