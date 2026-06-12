---
title: "PPP dialer"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-16
From all of the good help of the forum and a little research I believe that my serial hardware modem (US Robotics courier 56K v.everything) does not require drivers, but the correct "**[COLOR=#ff0000]PPP[/COLOR]** **[COLOR=#ff0000]Dialer[/COLOR]**." What is a **[COLOR=#ff0000]PPP[/COLOR]** **[COLOR=#ff0000]dialer[/COLOR]** and how do I go about setting it up?
 
Thank you

---

### Post by Wobblybob on 2011-04-18
Hi try looking in the Synaptic Package Manager for gnome-ppp

> modem internet connection tool for the GNOME Desktop. GNOME PPP is an easy to use graphical dialup connection configuring
and dialing tool with system tray icon support.

---

### Post by grahammechanical on 2011-04-18
You will need to configure Gnome PPP with the phone number of your ISP and your ISP username and password. The speed you can set as 115200. COM will be /dev/ttyS0 (that is the number not the lower case letter). The Method should be PAP Authentication and the DNS is Dynamic. This worked for me when I was using a dial-up modem.

Regards.

---

### Post by Bartender on 2011-04-20
Synaptic Package Mgr. will not find gnome-ppp until you've gotten online and clicked the "Reload" button.  With a fresh install of Ubuntu and a PC that's never been online, Synaptic doesn't know what's what and will not find packages that you ask for.

Use pppconfig to get online, then ask Synaptic to Reload.  On dial-up this should take about an hour.  Then you can type in "gnome-ppp" and Synaptic will get the packages.

---

