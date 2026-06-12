---
title: "Network Manager configures both eth0 and wlan0"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by dwhitney67 on 2009-03-01
Last weekend I was having trouble getting my wireless working; it was working fantastically for over two years, then it just stopped working.  In my efforts to resuscitate the wireless, I decided to upgrade the OS from 8.04 to 8.10.

Now the wireless is working (btw, I also had to install new drivers), but the curious thing is that when I am connected to the wired-network, the NetworkManager not only configures my system's eth0 interface, but periodically it also attempts to configure the wlan0 interface... and sometimes it succeeds!  Thus the system has two active interfaces.

When I switch to wireless only, then of course the NetworkManager obliges by terminating the eth0 interface.  Then wlan0 is still active or becomes active, but operates at a pathetic 1 Mb/s rate.

Is there a simple explanation for all this, or should I just consider waxing the system?

It was incredulous that the wireless stopped working out of the blue when the system had 8.04.  I was not doing anything to the system (at the time I was using my Fedora 9 system, of which 99% of the time is at my fingertips).  When I took a look at the 8.04 system, the wireless interface was no longer active, nor was there the ability to view any wireless access points in my apartment complex (normally there are over 10).  The wireless chip-set was enabled, but no WAPs were visible.

Btw, the system has the following chip set:
```

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by Xiong Chiamiov on 2009-03-02
*Something* causes your wireless to stop functioning; it's just not obvious what it is.  The most common reason is a kernel upgrade.

If wlan0 wasn't up, you can bring it up with ifconfig.

NetworkManager will always manage all of your interfaces (at least, I don't know how to make it not), but it shouldn't be trying to connect wirelessly if you have a good wired connection.  Is it connecting to a saved wireless network, or just one at random?

---

### Post by dwhitney67 on 2009-03-02
> **Xiong Chiamiov said:**
> ...

NetworkManager will always manage all of your interfaces (at least, I don't know how to make it not), but it shouldn't be trying to connect wirelessly if you have a good wired connection.  Is it connecting to a saved wireless network, or just one at random?

For whatever reason, the NM does indeed connect to my WAP when the system has a good wired connection.  It is bizarre.  (See attached image).

I wish 1) I could get NM to stop connecting to the WAP when I have a connection via the wired port, and 2) that I could achieve greater download speeds via the wireless port.  Right now the wireless port achieves about 1 Mb/s, whereas my system which is next to the Ubuntu system, achieves 11 Mb/s.

---

