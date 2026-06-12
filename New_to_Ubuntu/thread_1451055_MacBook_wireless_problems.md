---
title: "MacBook wireless problems"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by thehiddensherpa on 2010-04-09
I have a MacBook A1181 that I recently installed Ubuntu 9.10 on. Nothing I have tried has gotten the wireless internet to work. It won't show me the available network connections. It's as if AirPort Utility is off and I can't turn it on.

Network Tools gave me nothing.
Network Connections gave me nothing.
I tried installing madwifi, it said I needed subversion. It wouldn't let me install subversion.
I tried installing some driver for the AirPort Extreme and it gave me a 13: Permission Denied or something.

My first three days of ever using a command-line for anything have been spent trying to connect to a wireless network. Could somebody please point me in the right direction?

---

### Post by huygens on 2010-04-10
I do not know which revision of the MacBook is the A1181 that you are mentioning, however you should found what you are looking for here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
Check the corresponding link for your MacBook and Ubuntu release (if the Ubuntu release does not match, you can try picking up an older release).

---

### Post by alfu on 2010-12-28
My landlady's MacBook A1181 hard drive fried, and she had lost the install CD set.

On a whim I wondered if the Ubuntu 10.04 live CD (for 64 bit PC) would do anything in this machine, and to our amazement, EVERYTHING works (WiFi, yes!) except it doesn't seem to come back from 'suspend'.

Also, flash movies don't work because the flash driver needs to be downloaded (it is not provided with the live CD -- maybe on the install only CD?)

And this stupid machine (2007 vintage) has a one-button track pad!  You have to install an external USB mouse (it works too) to get right-click context menus.

Update 101229: Bought a USB Seagate 640GB drive at Office Depot for $60 (it was $10 cheaper than the 500GB BARE drive), hoping that it was a compatible SATA drive, in the event the MacBook would not be able to boot Ubuntu from an external drive.  Yup, even tho a Ubuntu 10.10 installed OK CD --> USB drive, the Mac would not boot from it (Hold down Option key right after startup sound).  Opened the USB case, and installed the drive inside the MacBook (undo the three screws holding in the battery compartment metal "L" bracket), then everything worked.  Suspend problem is fixed, altho the MacBook wants to come back from suspend only with hitting the power button, not a keyboard key.

Heat tip: the MacBook 2.1 is prone to cooking its HDDs over time, probably due to dust accumulating in its pathetic little air vents.  I tried cleaning them with a nozzle attached to a shop vac; time will tell.

---

### Post by VonSpyder on 2010-12-28
why are you using karmic? Ide imagine a later distro would solve this isuue.

---

