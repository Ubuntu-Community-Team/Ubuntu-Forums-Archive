---
title: "Ununtu 7.04 - no internet"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by ericsaxalto on 2007-08-29
I installed Ubuntu 7.04 on Monday night and I cannot figure out how to get the networking to work.  I keep getting a message saying "Firefox cannot find server".  I have entered the IP address of the wireless connection in my home, but still nothing is working - even without using the wireless.  Any thoughts?  I'm using a Gateway MT6705 laptop.

---

### Post by kevdog on 2007-08-29
You probably need to install a wireless driver.

Do you have a wired connection on the computer??

Can you post the following:
lspci -nn
lshw -C network

---

### Post by ericsaxalto on 2007-08-29
Kevdog,

Thanks for the suggestions.  I posted the two suggestions and they registered in the terminal, but it didn't change anything.  It recognizes a wireless card, but I have no idea how to find the drivers necessary if that's the problem.  I checked the Networking Tools under System and Administrator and the Network Device is set to "loopeback Interface".  Is that correct or do I need to set it to Wireless Interface?  When I selected Wireless InterfaceIt did not register any of the information at the bottom of that icon.  I'm open to suggestions if you have any.  Thanks again!

---

### Post by kevdog on 2007-08-29
> I posted the two suggestions

Those werent suggestions, I wanted you to post the output of those two commands here so I can figure out the chipset of your wireless card.

---

