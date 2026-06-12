---
title: "Internet connection"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by tommy2k10 on 2010-04-14
I have just installed Ubuntu Desktop 9.10 on my test machine, which also includes Windows XP, Vista and 7.  
However hard I try, I cannot get it to the connect to the internet!  When I go to Hardware Devices it can't find any!  However, when I open a Terminal and type sudo lshw -C network (I found this command through a Help site) it comes up with information about the wireless adapter!
It is an Atheros AR5000.
I try to go through Network in Applications, but I can't seem to access it there.
I have set a BT Home Hub as a wireless access point, as my main computer doesn't have a wireless card but my test one does.
Why can't I connect?

---

### Post by Paqman on 2010-04-14
Can you connect by plugging straight into the router and try Hardware Drivers again?

---

### Post by stoogiebuncho on 2010-04-14
Paqman is right - you probably need to download the driver for your wireless card, so you need to connect to the internet through a wired connection in order to do that.

So plug it into your router or modem, and go back to the Hardware Devices and see if the driver shows up.  If it doesn't, restart the computer and look again.

---

### Post by tsp_2177 on 2010-04-14
i agree with them and wow i would love to see the Grub bootup page i bet there are like 50 different options on that thing with all the different OS you have on that computer lol

---

### Post by anewguy on 2010-04-14
Please also post back the output of lspci so we can see the exact chipset the adapter is using.

thanks
Dave ;)

---

### Post by tommy2k10 on 2010-04-15
I've plugged the ethernet cable in and still no luck!
I have been to Network Connections, and under Wired, auto eth-0 looks fine, as I use dns automatically and assign an ip address automatically.
I did an lsmod from a Terminal window, and it listed the adapter.
Attached is a screenshot of lspci.

---

### Post by anewguy on 2010-04-15
You'll want to use the madwifi drivers to get your wireless to work.

Dave ;)

---

### Post by Easy Limits on 2010-04-15
Have done all of your updates?  The Atheros driver should be in the latest kernel in 9.10.

---

### Post by anewguy on 2010-04-16
We should have you post the complete output of lshw -C network - this will allow us to see what driver, if any, is loaded for the adapter.

Dave ;)

---

### Post by tommy2k10 on 2010-04-22
Here is the output of lshw -C network

---

