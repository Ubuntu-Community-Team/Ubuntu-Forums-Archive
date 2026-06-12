---
title: "Installed wireless , disabled LAN :("
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by AfterForever on 2007-03-19
Hello all.
I (apparently) installed wireless drivers from this guide :
[http://doube.net/bcm4318.html](http://doube.net/bcm4318.html)
(Kubuntu 6.10)
The problem is that after rebooting, my ethernet card is not working !!! When I go to Control Center and Network Settings, I see the wireless device enabled and the ethernet disabled. When I press enable, it immidiately turns itself off. As a result I can't get online from Linux. I'm writing from windows right now.
Any ideas? :confused: 
Thanx in advance dudes.
A linux newbie.
PS. My network card is realtek rtl8169 8110 family gigabit ethernet NIC and it's fully supported and working (before all these :( )

---

### Post by DiverSpear on 2007-03-20
Hi!
First message on this forum!
I'm experiencing the exact same problem as you, and I may add that I have the exact same Ehternet controller from Realtek.
I'm on Ubuntu 6.10 with all updates, gfx driver - I think I installed the packages for SAMBA and NFS just before the problem occured.

All of a sudden one night, I couldn't connect to anything through LAN, but neither WAN.
I have had the Network Manager installed (for much easier access to various WAN's), but I uninstalled it, in case it was the problem, but no luck.

In properties the only connection I'm able to choose is 'lo', which I actually don't know what is.
- loopback!? 
Have the driver in some way 'de-loaded' itself or? The weird thing is, that it says that my LAN connection is set active in Networking - neither can I disable it. (perhaps the only difference to your problem)
Network Tools doesn't show any information on any connection besides the loopback -thing.

Really hope someone has a theory or better a solution to the problem

Thanks

/DiverSpear

---

### Post by chili555 on 2007-03-20
Please try: ```
sudo modprobe r8169
```Any complaints? Sometimes, I have seen 'modprobe' not work and 'insmod' work or vice-versa, so you may have to try both.

Afterwards, does: ```
ifconfig -a
```show eth0, your ethernet connection? If so, let's sudo gedit /etc/modules to add a new line:```
alias eth0 r8169
```

If not, post back and we'll get it.

---

### Post by DiverSpear on 2007-03-20
Thanks for your reply.

It seems that Ubuntu has fixed the problem. I booted and suddenly I was given a error message that listed possible cases to the error. I restarted X and everything seemed to be working out fine again - eth0 was localized and I was able to choose which unit I would use as connection link.

Weird.

Anyway hope you figure out the problem anyway - it might occur again.

/DiverSpear

---

