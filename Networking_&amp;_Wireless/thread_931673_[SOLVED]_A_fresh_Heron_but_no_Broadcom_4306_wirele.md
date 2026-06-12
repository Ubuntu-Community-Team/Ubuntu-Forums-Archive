---
title: "[SOLVED] A fresh Heron but no Broadcom 4306 wireless"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2008-09-27
A new HD, a fresh HHeron install but afterwards no wireless connection to our home's router. It's little wonder that I generally prefer an Ethernet connection than using Wifi with Ubuntu. The hard drive on my wife's PC appears to be developing faults hence the fresh Ubuntu install on a new HD and this posting about no Broadcom 4306 based connection to our router.

Here iwconfig shows wlan0 whilst ifconfig doesn't show any reference to wlan0.

Please someone point us in the direction towards the solution of our wifi problem as to how to get a Broadcom 4306 chipset PCI card wifi working under Ubuntu.

---

### Post by Crafty Kisses on 2008-09-27
You may want to take a look at this thread > [http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy)

---

### Post by Handssolow on 2008-09-28
The good news is that I've got wifi back.  I spotted eventually that I'd made an error in the wirelessfix.sh file because module ssb was showing rather than module ndiswrapper when I looked at the terminal output of lshw -c network

The less than good news is that after every boot I have to keep manually entering our essid, wep key and channel. All the information is there in the Network Settings gui and in /etc/network/interfaces. I didn't add the last line in Step 3 because we use wep still rather than wpa.

Is there a missing applet?

How can I make the wifi setting load at boot?

---

### Post by Handssolow on 2008-09-28
Problem of wireless settings not been remembered solved after looking at-
 [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I wrote my wireless settings in the rc.local file as described.

Edit:
Unfortunately after moving on to work on some XP/Ubuntu dual hd dual boot issues, I returned to discover that the wifi connection to our router now isn't available after a reboot.

---

### Post by Handssolow on 2008-09-28
Surprisingly after a reboot
sudo iwlist scan
shows a neighbour's wifi router not ours!!!

However our settings are loaded giving a working link to our router after I run
sudo /etc/init.d/networking restart

I can also get wifi re-established after a reboot with the Network Settings gui. If I change a wireless setting in Properties to activate the "Changing Interface Configuration" first to an incorrect value then back to the correct value. 

Any suggestions what needs to be done to get our wifi automatically working after a reboot?

---

### Post by Handssolow on 2008-09-28
Reboots now come with a wifi connection to our router after I created a startup script as described below, though I'm not entirely happy about the error messages I read during boot and shutdown. Network Manager is throwing up bugs, my system appears not to like the old Broadcom bcmwl.inf driver and I seems to have not just wlan0 but wmaster0.

[http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

Not sure if I should leave the bugs as they are or try removing Network Manager in synaptic.

---

