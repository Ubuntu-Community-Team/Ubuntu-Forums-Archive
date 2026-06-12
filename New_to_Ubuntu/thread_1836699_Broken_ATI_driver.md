---
title: "Broken ATI driver"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by SNIFFER_dog on 2011-08-31
Hi Ubuntu Community,

I have been trying to install a more current driver for my ATI GPU but I've managed to break the desktop completely and I can only log into 'tty1' when I boot up.

I followed this advice of the following youtube video but I fear there are no ATI Proprietry drivers for my VIAO laptop available and I must have picked the incorrect one.

[http://www.youtube.com/watch?v=KiSix41sR7s](http://www.youtube.com/watch?v=KiSix41sR7s)

I only got 3 folders not 4 and it basically isn't recognised.

When I:

lspci ¦ grep vga

it comes up with:

VGA Compatible Controller : ATI Technologies Inc Mobility Radeon X2300

Does anyone know what drivers I should be using and how to install them for 11.04 natty narwhal so I can make best use of my graphics card or is it simply too old.

Bear in mind I'm now only able to login at tty1 level

Thanks again

SNIFFY

---

### Post by SNIFFER_dog on 2011-08-31
It appears I've managed to get the ATI open source driver working. I followed the this link:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Which then took me here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

And that solved the problem.

I do seem to get some error messages when I boot up now that were not there before but at least I have a working unity again, I will investigate further. I'm still not convinced I have a smooth running system.

SNIFFY

---

### Post by Redblade20XX on 2011-08-31
If you want to try the proprietary drivers, take a look at this:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

- Red

---

### Post by Mark Phelps on 2011-08-31
The ATI restricted drivers only work with the new "HD" series of cards; they do NOT work with the older "X" series cards.

If you attempt to force an install of the restricted drivers, all you will do is trash your display and take on a LOT of work needed to remove the drivers -- and replace them with the same ones you already have running.

---

