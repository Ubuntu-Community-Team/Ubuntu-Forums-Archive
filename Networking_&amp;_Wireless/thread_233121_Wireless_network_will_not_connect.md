---
title: "Wireless network will not connect"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by nashattan on 2006-08-09
My friend is having a severe issue with her wireless networking.  namely, it doesn't connect.  So far we have tried ethernet, which does work, and lead me to believe that it was a driver issue.  We installed the ndiswrapper and ran if for her card (Broadcom BCM4310) and it says that the hardware is recognized, but it still will not connect to the internet when she goes to System > Administration > Networking and tries to set up the connection.  I have made sure we both have all the same settings and it works fine on my computer.  I am absolutely out of ideas.  Can anyone give me a hand with this?  What information do you need about her computer to help?

---

### Post by oyvindaa on 2006-08-09
There's a neat little program called wifi-radar.

```

sudo apt-get install wifi-radar

```

Quite easy to set up your wireless connection from there.
No guarantees though, but it worked flawlessly my end.

---

### Post by tonofclay on 2006-08-09
I used this guide to get my wireless internet up and running. I'm not sure if the ndiswrapper method or the bcm43xxcutter method works better, perhaps its different for each user, but here is the How To:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

---

### Post by nashattan on 2006-08-09
Hey, thanks!  I've already tried the Wifi-radar with no success on its own, but it looks like I need to use it with the firmware cutter anyway.  I'll give the cutter a shot tomorrow.  Looks promising.

---

### Post by oyvindaa on 2006-08-10
Good luck there mate, hope you sort it out.

---

