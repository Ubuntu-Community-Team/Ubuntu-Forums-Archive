---
title: "connecting to wireless network"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by joe6966 on 2009-09-07
Hello members,
I installed Ubuntu 9.04 yesterday. It is on a partition of my laptop. I can't get it to connect to my wireless router.
The laptop running Vista does run on the network and I have no problems with the router.
While in Ubuntu, I clicked on the network icon in the upper right corner. It asked for a password. I think it wants the WPA encryption code that was used with Windows. I don't know how to get that. I don't remember it. I know it was long.
I tried the help/support link, and got the message to type in a terminal, sudo lshw -Cnetwork. I did that, and it asked for my password, which I have. The terminal window had a black blinking cursor, but would not allow any input.
Please help!
I have been using Windows 98, XP Pro, Vista 64 bit and Linux Debian 3.
I also went to the Linksys WRT54G2 V1 support page, but they have no support for Linux.

---

### Post by Temposs on 2009-09-07
If you don't know the WPA encryption code for your router, then you need to be able to plug in to the router with an ethernet cable. Then connect to the router administration.

---

### Post by ddrichardson on 2009-09-07
The stage of the help you refer to assumes a non-working wireless connection which you don't have.

If it's your router and you've lost the password, you can reset it to factory defaults and connect through NM.

[http://technicallyeasy.net/2008/01/how-to-reset-linksys-wrt54g-wireless/](http://technicallyeasy.net/2008/01/how-to-reset-linksys-wrt54g-wireless/)

---

### Post by accaflacca on 2009-09-07
You need to find your WPA password. Download Wireless key view on your Vista computer and use it to find your WPA password.Then WRITE IT DOWN IN SEVERAL PLACES SO YOU DONT LOSE IT AGAIN. Then enterit in Ubuntu and all should be well.

John Buck
:guitar:

---

### Post by Vaeil on 2009-09-07
As said above: You pretty much need your WPA key.

This is a bit like asking how you can access your bank account without your code. That very code is supposed to block people from access as long as they don't have it.

Connect to the router via cable, or another pc with access, and get (or change) the WPA key.

---

### Post by joe6966 on 2009-09-07
I downloaded WirelessKeyView, installed and ran it. It showed nothing.

---

### Post by ddrichardson on 2009-09-07
Again, if network manager is showing a connection available to your router but you don't know the password, then you can connect using an ethernet cable and find the password from your router's configuration page (its on the link I gave earlier).

Otherwise you can reset the router (also on that link).

---

### Post by joe6966 on 2009-09-08
Thanks all; it is running now. I had to reset router and reinstall.

---

