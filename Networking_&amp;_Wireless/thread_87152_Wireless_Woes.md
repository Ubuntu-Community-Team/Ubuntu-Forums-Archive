---
title: "Wireless Woes"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by IMELucky on 2005-11-07
I'm running Ubuntu Hoary Hedgehog on a HP-Compaq nc6230

I can connect to my home wireless network, but after a while my wireless will just stop working and I won't be able to reconnect without rebooting. (The admin-networking tool fails to reconnect to the network) In adittion, I'm a college student and when I try to connect to my school's unsecured wireless network, it won't work either. (Again, admin-networking doesn't work). Cable ethernet always works, so when I plug into a public access port I'm fine. I'm just having issues with wireless.

I should also mention that the admin networking tool can always see the access point, but it won't pick up signal or connect to the network.

Thanks to anybody who can help!

---

### Post by mips on 2005-11-07
What wireless card are you using ? Make and model please ?

---

### Post by IMELucky on 2005-11-07
According to lspci:
0000:02:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

Which use the following modules (lsmod)
ipw2200                66156  0
firmware_class          9728  1 ipw2200

---

### Post by Stelmate on 2005-11-10
For the school Wi-Fi point did you register your computer with your school? Most colleges use a access list with their wifi networks.
For your own personnel network how long are you able to connect before you get booted?  Does the internet acutally work while you are connected?  What kind of security are you using WEP or WAP? and finally are you using the command line or your x-windows system to setup your wifi at home?
and finally are you using a actualy linux driver for your wifi card or ndiswrapper?


[QUOTE=IMELucky]I'm running Ubuntu Hoary Hedgehog on a HP-Compaq nc6230

I can connect to my home wireless network, but after a while my wireless will just stop working and I won't be able to reconnect without rebooting. (The admin-networking tool fails to reconnect to the network) In adittion, I'm a college student and when I try to connect to my school's unsecured wireless network, it won't work either. (Again, admin-networking doesn't work). Cable ethernet always works, so when I plug into a public access port I'm fine. I'm just having issues with wireless.

I should also mention that the admin networking tool can always see the access point, but it won't pick up signal or connect to the network.

Thanks to anybody who can help![/QUOTE]

---

### Post by IMELucky on 2005-11-15
The school network is registered
My home network is variable and when it is connected it works great. Sometimes it will work for hours then quit, other times it will only work for about 10 minutes.
When it does stop working, it is impossible for me to get reconnected without rebooting the computer.
Generally, my home network tends to stop working the most often after the screen saver is deactivated (like hitting the mouse, or pressing the keyboard)
I'm using WEP, and I use the GUI tool to configure my network. 
Is there a command line way of configuring network? (iwconfig, but what command does Ubuntu use for dhcp?) 
I'm pretty sure that the driver I'm using is the actual linux driver and not an ndiswrapper

---

