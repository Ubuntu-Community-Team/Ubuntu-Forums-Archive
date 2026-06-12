---
title: "DHCP after resuming from suspend - 8.10"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by cob on 2008-10-26
I just upgraded to Intrepid Ibex, and now every time I resume from suspend, I have no network connection.  Layer 2 is established (802.11 via b43legacy, BCM4306), but it's not making a DHCP request after the resume.  An /etc/init.d/networking restart quickly resolves the problem, but I don't want to have to do it after every suspend.  Anyone else having this problem?

---

### Post by tomjooonas on 2008-10-30
I do have same problem, I have Atheros 802.11 wireless LAN card. After suspend I can´t get wlan connection. How do you restart network manager?

---

### Post by cob on 2008-10-31
```
sudo /etc/init.d/networking restart
```

This is for layer 3, dependent upon your wireless adapter already having layer 2 established.

I think I'm going back to Hardy, not only has this problem cropped up, but my video acceleration is gone.

---

### Post by klearvue on 2008-10-31
Just updated to 8.10 - wireless unable to obtain IP address via DHCP  AT ALL.

(not too big a problem at home - I just switched it to static but it's not a solution for many places where DHCP is a must)

---

### Post by cob on 2008-10-31
Strangely, the Network Manager seems to be completely misaligned with my configuration.  It reports no connections are active, yet my wireless card is up and connected to the AP, and I've got an IP, and am able to surf.  After a fresh reboot, the Network Manager icon is absent, and is restored after a suspend/resume, but reports the aforementioned.

---

### Post by sygard on 2008-10-31
> **tomjooonas said:**
> I do have same problem, I have Atheros 802.11 wireless LAN card. After suspend I can´t get wlan connection. How do you restart network manager?

I think 8.10 supports restart of network manager through init.d
```

sudo /etc/init.d/NetworkManager restart

```

I'm facing the same problem as you regarding DHCP request through any of my ehternet devices. I have to manually force a dhcp request for my network to work.

```

sudo dhclient eth0

```

/sygard.

---

### Post by tomjooonas on 2008-10-31
Restarting network manager didn`t work. But when I restarted Atheros Wlan-card`s driver it start to work. So my problem wasn`t network manager. 

Thanks for help to everyone!!

---

### Post by PinkFloyd102489 on 2008-10-31
I have the same problem here. It's a Dell 1505 ABGN mini-PCI card with a bcm4328 chipset. When resuming from standby, Network Manager says it's "disabled". Doing /etc/init.d/NetworkManager restart kills off the applet and starts it again, reenabling my connection. It takes about 10 seconds after Network Manager restarts for DHCP to grab an IP address.

Once again, this is only after resuming from standby.

---

### Post by cob on 2008-11-07
Re-installed 8.10 from scratch, and this issue is solved.

---

### Post by robgig1088 on 2009-01-14
Thanks, PinkFloyd.  That worked perfectly.  I have no idea why I didn't try that before.  I tried everything else.  Oh well, at least I can fix it now!! :D

---

### Post by danmarycap on 2009-03-11
Has anyone discovered an actual fix?  I have the same problem on my Dell Mini9 running Intrepid.  Wireless works fine until I suspend, and on resume...no wireless connection.  Go to Terminal, run sudo dhclient, switch back to Firefox and everything works.

That's a hassle...and while I've got no prob issuing sudo commands, I don't want my wife and daughter to have to do that.

Seeing lots of variations on the same theme posted throughout this forum, but no permanent fixes.  Anyone...?

-Dan

---

### Post by danmarycap on 2009-03-13
I've posted a solution here: [http://ubuntuforums.org/showthread.php?p=6883391](http://ubuntuforums.org/showthread.php?p=6883391)

---

