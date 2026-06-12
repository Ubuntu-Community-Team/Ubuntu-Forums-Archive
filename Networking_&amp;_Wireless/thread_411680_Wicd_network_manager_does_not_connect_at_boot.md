---
title: "Wicd network manager does not connect at boot"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by scotty64 on 2007-04-17
I have replaced the standard network manager with WICD. I like the versatility of this application, but I could not find out how to set it up that the wired device is available automatically after booting. Whenever I start my machine I have to start WICD in order to get an IP on the wired device - not very comfortable.
Has anybody solved this problem?

---

### Post by chili555 on 2007-04-19
I like Wicd, too. My wireless interface is started on boot. I think the key is to be sure the word 'auto' with your relevant wireless interface appears in */etc/network/interfaces*. Here is a disguised version of mine:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

**auto eth1**
iface eth1 inet dhcp
wireless-essid myrouter1
wireless-key 096c7xxxxxxxxx4afe
```Also, while you are amending your file, you can safely eliminate all the other interface lines that you know you don't want or need. Don't touch, or even look at lo.

---

### Post by plinydogg on 2007-06-13
I took a look at this thread because I have to manually start Wicd everytime I boot as well. 

When I tried the suggestion solution, though, I found that I didn't even have an entry in /etc/network/interfaces for my wireless! I just have lo and eth0 but my wireless alias is wlan0. 

It took a lot of help from this forum to get my wireless network working and I messed with /etc/network/interfaces a number of times so I probably changed it, but I'm just wondering: 

If wlan0 isn't in my /etc/network/interfaces, then where is it? How does wlan0 work without it?

---

### Post by chili555 on 2007-06-14
wlan0 works without an entry if you installed Feisty and, by default, Network Manager took control of your network interfaces. If you removed NM and installed Wicd, there is no mechanism I know of for the interface stanzas to get added back in to *interfaces*. There is no reason you can't do it yourself. Just add with sudo gedit or sudo kate:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid myrouter1
wireless-key 096c7xxxxxxxxx4afe
```Your details will vary; adjust as needed.

---

### Post by dardack on 2007-06-14
You don't need to manually edit anything.  I have this done automatically for me (i had to remove NM cause my connection would drop all the time, i was doing manual connection for awhile until someone posted to one of my forum posts about WICD, which does everything automatically).  Now what version of WICD are you using, i'm using the 1.2.9 testing version (pretty stable for me).  So i don't know if it's different in 1.2.7.  But first once you run WICD, verify that under your ESSID options you have selected connect to this network automatically.  It is unchecked by default.  Also for the tray icon and such:

[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq) (wicd's home/faq) and in there you will find this  (the relevant part about boot is second sentence):

How can I get the tray icon to appear?
Hit alt-F2, and run “/opt/wicd/tray-edgy.py”. In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the “Startup Programs” tab, click the “New” button. Give it a name (”Wicd” works fine). For a command, enter “/opt/wicd/tray-edgy.py”. In KDE, run the following command from a terminal: “sudo ln -s /opt/wicd/tray-edgy.py ~/.kde/Autostart/tray-edgy.py”. Under either desktop environment, you can open the main window by right clicking the tray icon and choosing “Connect...” (or simply by left-clicking it if you are running version 1.2.8 or later). 

Hope this helps.  But i never had to manually edit anything after i uninstalled NM.  I just downloaded WCID 1.2.9 ran it and every time i boot it connects fine.

---

### Post by tdjones on 2008-02-16
I've been running into this very same problem. I've checked that the init script /etc/init.d/wicd is run when the machine boots and it certainly does.

When the script is run at startup through the boot sequence it fails to connect. Yet if I run the very same script manually with sudo after the machine has loaded it works every time.

But I noticed something peculiar. When comparing the log files from /opt/wicd/data/wicd.log after the machine boots with the log generated when I execute:
#/etc/init.d/wicd start   

When the prior is run it only detects 6 acesspoints which it lists the MAC's of. None of those MACS are a match to my home network.
With the latter call it detects 11 ap's, one of which is my router and successfully connects once it identifies that there is a related profile.

What could be causing this behavior? Signal Strength? Channel selection? any ideas are welcome.

---

