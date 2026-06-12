---
title: "Wireless goes on and off"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by rocklee on 2008-08-17
I'm using a Dell M1530 with the Intel 3945ABG wireless card.

While I couldn't get the Intel drivers to work, I resorted to using ndiwrapper which works.

Now Ubuntu will work sometimes, but when I reboot again wireless would not work.  However, after rebooting in Windows and getting into Ubuntu the wireless will work again.

I can't seem to access the wireless settings in Ubuntu when it fails.

I feel that Windows is doing something right when managing my wireless but Ubuntu seems to only detect my ethernet card and not the wireless.

Has anyone encounter this problem before?

Thanks.

---

### Post by rocklee on 2008-08-17
Ok so I installed WICD and installed the backport for hardy :

sudo apt-get install linux-backports-modules-hardy-generic

I can see a list of wireless networks to connect to, but still no dice.

I boot back into Vista and wireless works, boot back into Ubuntu and that will work.  Ubuntu won't work if I reboot it again.

---

### Post by rocklee on 2008-08-17
Ok so now Ubuntu doesn't work at all.

It lists all the wireless networks including the one that I am trying to connect to but nothing.  All the settings are the same as I have in Vista.

Any clues someone?  I'd really like to get this working as I've been rebooting the computer a lot.

---

