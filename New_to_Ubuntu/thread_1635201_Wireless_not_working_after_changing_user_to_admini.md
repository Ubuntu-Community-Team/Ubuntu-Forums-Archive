---
title: "Wireless not working after changing user to administrator status"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Vot Musik on 2010-12-01
Hi all,

I've been using Ubuntu 10.10 Netbook Remix on my Samsung NC10 with no problems for a month or so now, but my wireless internet has suddenly cut out.  None of the other computers in the household using the same network (running Windows) have experienced any problems.

I suspect that this came about after I changed my status in 'Users and Groups' to 'Administrator' last night, having seen that it was set to 'custom'.  I've also tried connecting to a wired router and other wireless networks, but no dice.  In addition, I changed 'password' for my user account to 'don't ask for' from 'asked on login'.  It's possible that these things have nothing to do with it, but it looks like fairly straightforward cause and effect.

I've had a look around to see if anyone has encountered the same problem, but nothing is available on this.

Please help!

Vot Musik

---

### Post by Trandre on 2010-12-01
I have a solution that worked for me here : [http://ubuntuforums.org/showthread.php?t=1634113](http://ubuntuforums.org/showthread.php?t=1634113) last post

---

### Post by Vot Musik on 2010-12-02
Hi Trandre,

Thanks for getting back to me.  That option is already enabled.  The readout from the command  

```
lshw -c network
```

mentioned in the thread is:


> *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:7d:be:f7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-23-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:24:54:12:80:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
       resources: irq:42 memory:f0200000-f0203fff ioport:2000(size=256)


---

### Post by plucky on 2010-12-02
Login as original Administrator

Open **System > Preferences > Network Connections > Wireless Tab** and select edit your wireless connection.At the bottom of the page,tick the box that says "Available to all users".

You might have to reboot,but you could try logging out and logging in as the new user and then see if the network is available to you.

Good Luck

---

### Post by Vot Musik on 2010-12-02
Hi Plucky,

The 'available to all users' box is already ticked for my wireless network.  I created a second user, an administrator, but the second user can't even see the wireless icon in the system tray, depite the fact that he has permission to connect to wireless networks.  Both have all boxes ticked in the 'user privileges' section of User Settings.

---

### Post by Vot Musik on 2010-12-02
Update - wired internet now working, autoeth0.

---

### Post by Vot Musik on 2010-12-04
Any ideas? I've read a few fixes that involve downloading additional drivers, but if it worked before I played with the user settings, that shouldn't be necessary - right?

---

### Post by Vot Musik on 2010-12-05
Thanks, plucky and Trandre. :)

Problem solved - it seemed like a waste of time, but my only option was to reformat. :roll: God knows why it happened, but here's hoping it won't happen again.

---

