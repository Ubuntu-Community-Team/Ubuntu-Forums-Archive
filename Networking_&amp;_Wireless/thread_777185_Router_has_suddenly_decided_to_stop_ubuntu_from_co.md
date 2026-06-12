---
title: "Router has suddenly decided to stop ubuntu from connecting to it"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by mat28590 on 2008-05-01
I'm running Ubuntu 8.04 hardy heron in a dual boot with vista (ew). Using a dlink DI-524 router, linksys wmp54g wirelesss card.

Both wireless and wired connections from the computer to the router (and internet) were AND STILL ARE working fine on VISTA. To start with, i could only get wired connection to work on Ubuntu. THen i managed to get the wireless setup, both were working. But when i rebooted the computer neither connection type was working ON UBUNTU. 

The router refuses connections from ubuntu when i do 192.168.0.1 and Ubuntu can't access the internet at all. Vista works fine. Ubuntu internet WILL work if i plug the cable straight into the modem. I have tried resetting my router, but that didn't work.

Any thoughts?

---

### Post by Ayuthia on 2008-05-01
If your wireless was working before and then just stops working (even though Vista is fine), it might be that the driver is picking up some interference with other signals.  You might try changing the channel on your router to see if that fixes it.

---

### Post by Jonas Wakefield on 2008-05-01
I have the same problem...

After installing b43fwcutter (wired) I was online perfect then got wireless to work but after turning my laptop on in the morning it doesnt work but knows the router is there. My problem, I think has something to do with a Network Interface, or something like that. I think I need it set to wlan0 but it appears disconnected.

Anyone?

---

### Post by mat28590 on 2008-05-01
Jonas are your running a 64-bit version of Ubuntu? i don't know if that could make a difference. 

The problem i had with wireless first was that it couldn't detect channel 12, so i changed it to 6; thats when everything worked until the next reboot when it all went tits up.

---

### Post by Jonas Wakefield on 2008-05-07
I don't know what version it is but I'm pretty sure it's not channel I'm on, thanks for suggesting...btw I think I have 128 version but not to sure.

---

### Post by mat28590 on 2008-05-07
i reinstalled ubuntu n its all working...

---

### Post by sportman1280 on 2008-05-07
same issue here.  [http://ubuntuforums.org/showthread.php?t=783447](http://ubuntuforums.org/showthread.php?t=783447)

Could it be an issue with upgrading?  Because as far as i have tried on two different laptop... both were upgraded, but i still can't connect to that one router.  Works fine everywhere else...

---

### Post by sportman1280 on 2008-05-07
Bug report:
[https://bugs.launchpad.net/ubuntu/+bug/220445](https://bugs.launchpad.net/ubuntu/+bug/220445)

Please add to it.

---

