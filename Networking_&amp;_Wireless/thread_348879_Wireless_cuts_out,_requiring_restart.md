---
title: "Wireless cuts out, requiring restart"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by taosaur on 2007-01-29
I have a Linksys Speedbooster card (bcm4318 chip) running the bcm43xx driver via [these instructions]("http://ubuntuforums.org/showthread.php?t=185174"), in Edgy.  It works great for about 30 minutes at a stretch, and then suddenly it's Server Not Found in Firefox, Cannot Retrieve Files from Package Manager, etc.

According to WiFi Radar, I'm still connected to the network, and switching networks doesn't help, nor restarting any of the programs; I have to restart the computer every time.  I've had this happen on two different networks in different locations.  Any ideas on what's happening and/or how to fix it?

---

### Post by seventynine on 2007-01-30
I'm having the same issue. It just cuts out and does not give any error messages.

i tried the command "lshw" but the output there is the same, before and after...

using: belkin's 802.11g broadcom 4306 chipset via the bcm43xx driver

 > *-network:1
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: d
             bus info: pci@00:0d.0
             logical name: eth1
             version: 03
             serial: 00:11:50:1b:e0:2c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx ip=192.168.1.7 multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:cefea000-cefebfff irq:11

---

### Post by mikerduffy on 2007-01-30
I've been having this problem since day one of my wifi usage in kubuntu 6.10.  If anyone has any clues, please post them!

**EDIT: ** More info:

I'm using the 64-bit Broadcom wireless drivers (BCMWL564), with the firmware extracted.
I'm using the Gnome Network Manager (nm-applet), on KDE.
My computer is ~3.5ft (1m) from the router.
I do not have this problem in Windows.

---

### Post by seventynine on 2007-01-30
(as an alternative to restarting the computer) Here's something that works:
> 
 sudo /etc/init.d/networking restart

And here's something that DOESNT work:
> 
sudo ifconfig eth1 down
sudo ifconfig eth1 up

 (eth1 is my device's "logical name" seen by typing command "lshw", your device's logical name may vary)

---

### Post by mikerduffy on 2007-01-30
> **seventynine said:**
> (as an alternative to restarting the computer) Here's something that works:


And here's something that DOESNT work:


 (eth1 is my device's "logical name" seen by typing command "lshw", your device's logical name may vary)

I've noticed that if I right-click on the system tray icon for nm-applet, and disable the connection, then reconnect, it has a success rate of ~25%.

---

### Post by seventynine on 2007-01-30
Try this, it doesn't address the problem, but it still gives 100% connection uptime on my machine:
[B]
1) Rightclick the taskbar/panel and select "Add to panel"[/B]

(A window of custom applications will pop up)

**2) Select the app "Weather Report" and hit the "Add" button**

(now you will have the weather info on your panel)

**3) Rightclick on the weather icon and select "Preferences"**

(this will open the prefs for weather report)
[B]
4) Set it to update every 10 mins (default is 30)[/B]

Now, your connection should never go down. My guess is that for some reason DCHP gets timed out - which this setup prevents. I dont know the underlying reasons of this issue but the setup works. Perhaps someone more knowledgeble will know what's happening.

---

### Post by mikerduffy on 2007-01-30
> **seventynine said:**
> Try this, it doesn't address the problem, but it still gives 100% connection uptime on my machine:
[B]
1) Rightclick the taskbar/panel and select "Add to panel"[/B]

(A window of custom applications will pop up)

**2) Select the app "Weather Report" and hit the "Add" button**

(now you will have the weather info on your panel)

**3) Rightclick on the weather icon and select "Preferences"**

(this will open the prefs for weather report)
[B]
4) Set it to update every 10 mins (default is 30)[/B]

Now, your connection should never go down. My guess is that for some reason DCHP gets timed out - which this setup prevents. I dont know the underlying reasons of this issue but the setup works. Perhaps someone more knowledgeble will know what's happening.

Very interesting.

---

### Post by taosaur on 2007-01-31
Thanks for the responses.  I'm giving the weather report fix a try.  Also, thanks for letting me know about the Add to Taskbar command :D  

Yes, I'm a n00b.

---

### Post by seventynine on 2007-02-02
update: the weather applet trick works sometimes and sometimes it doesnt..............

i dun understand how does "sudo /etc/init.d/networking restart" fix the problem, if only temporarily?

---

