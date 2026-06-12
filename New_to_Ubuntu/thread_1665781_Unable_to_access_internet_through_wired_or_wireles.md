---
title: "Unable to access internet through wired or wireless connection"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by RadBrad63 on 2011-01-12
I have a Dell Inspiron 1520 that I bounced Vista off of and replaced with Ubuntu 10.04 last Spring.  I was able to access the wired internet and was looking forward to getting the wireless portion running as well.  Recently a friend offered to help and downloaded the driver for my Broadcom 4311 wireless, played around with some of the settings and now I'm unable to access internet through my NIC or wireless card.
I consider myself reasonably computer proficient (although new to the Linux OS environment) and have been searching through the various threads for nearly 3 days in hopes of finding a solution.  As far as I can tell from the terminal the computer is recognizing my cards.  My network manager showed "disabled" although I'm able to access the GUI from my network, where I have checked "Enable Networking", "Enable Wireless" and "Enable Notifications".  For some reason the "Connection Information" cannot be clicked on.
After 3 days I could ramble on about what I've done, etc. but I'm sure someone here will probably have just a few astute questions that I may answer and be able to solve the problem.  Please help.  My wife finally agreed to take that plunge away from Windows to Linux, but she really wants the internet working on her laptop.  Thanks in advance for your feedback!

---

### Post by Pedroriel on 2011-01-12
Sorry to be obvious, but have you power cycled your modem. (turn it off for 30 seconds)Doing this can help a lot of the time, as if all your network stuff is enabled, your router/modem should find it. This is the beginners fix! After that, check out your modem settings. As depending on your modem, you can log into it direct and fix settings.

---

### Post by SuaSwe on 2011-01-12
Hi RadBrad63!

What is the output of:

```

ifconfig -a

```

? 

If you know the IP address of your router, can you ping it?

---

