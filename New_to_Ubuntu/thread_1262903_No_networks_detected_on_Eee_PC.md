---
title: "No networks detected on Eee PC"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by gallonallen on 2009-09-10
I installed netbook remix on my Asus Eee PC 1005HAB yesterday and I cannot connect to wired or wireless networks.  There are none detected to even attempt.  I have searched the forums but everyone else with similar problems seems to be on acer netbooks, or they cannot connect to wap protected networks.  Neither of these types of threads are helpful to me, so here is my new thread with yet another netbook that doesn't run linux 'out of box.'  Can someone help?
Thanks
-Sean

---

### Post by OffAxis on 2009-09-10
the wired card is different than the wireless card, so...

Is the wired card being detected?

Is the wireless card being detected?

```
ifconfig
```

will list the status of the wired card

```
iwconfig 
```

will do similarly for the wireless
(if you get any information from these commands then something is being detected. It may off, it may be unconfigured - but something is being recognized.)

For the wired card, the easiest thing to do is connect it and see if you get an IP off your DHCP server. If you need to forcibly restart it the command is
```
sudo /etc/init.d/networking restart
```

---

### Post by LewRockwell on 2009-09-11
[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks)

.

---

### Post by gallonallen on 2009-09-16
Thanks to everyone with help on this subject.  The individuals who replied gave me valuable information that lead me to a easy solution.  Others with the same problem should go to the thread linked below for the easiest to follow solutions.

[http://ubuntuforums.org/showthread.php?t=1200710](http://ubuntuforums.org/showthread.php?t=1200710)

thanks again

-GallonAllen

---

