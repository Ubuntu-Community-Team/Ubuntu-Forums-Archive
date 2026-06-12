---
title: "can't see wireless card in 8.1"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by tiffanystardust on 2008-11-22
i have a vostro a860. wireless works fine in vista. i installed ubuntu 8.1 earlier, i'm using dell windows wireless driver which it says is fine, but it can't see the wireless card. any ideas please?

p.s. the a860 has fn + f11 to switch wireless on/off in windows, this works for bluetooth in ubuntu, and the switch is set to be for both so i'm guessing this means it's switched on? it doesn't work either way...hmm

---

### Post by Joe2Shoe on 2008-11-22
Go to System/Administration/Hardware Drivers and see if your wifi card's drivers are listed there.
If so, click on the driver listed, then click the 'activate' button below.
Reboot if necessary.
Good luck,
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
If that doesn't work, update the repositories.
I had the same problem, but this worked for me.

You must enable all the repositories to be able to download the needed drivers for your system:

Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

---

### Post by tiffanystardust on 2008-11-22
hi thanks...

 i tried that, but still no joy...the driver doesn't show up in system/admin/hardware drivers...

the atheros support is supposed to be deactivated, right?

---

### Post by Joe2Shoe on 2008-11-22
it has to be ACTIVATED!

---

### Post by tiffanystardust on 2008-11-22
er...yeah, if atheros support is activated it doesn't work.

if i install the driver from dell, it says installed, hardware not present ( in console:

ndiswrapper -l   gives   bcmwl6 : driver installed  but does not show hardware present

umm...this is my first day, can you tell?!! sorry....

---

### Post by Joe2Shoe on 2008-11-22
[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

---

### Post by tiffanystardust on 2008-11-22
already tried that!!

it says driver installed, hardware not present:


tiffany@tiffany-laptop:~$ lspci
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

tiffany@tiffany-laptop:~$ lspci -n
0c:00.0 0280: 168c:001c (rev 01)


tiffany@tiffany-laptop:~$ ndiswrapper -l
bcmwl6 : driver installed

but surely it should relate this to the wireless adapter at this point?

and the network configuration tool? it says its installed but ndiswrapper says unable to find network configuration tool

i know these are prob dumb questions, but i don't know any better yet!!

---

### Post by Joe2Shoe on 2008-11-22
tif,
It took me one YEAR to get my Broadcom BCM4306 rev. 02 wifi card to work!
So, don't feel alone.
I'll keep trying to find a fix for you.
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
> **Joe2Shoe said:**
> [https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

tif, did you install the right .inf file here?
It's the one that came with Windows on your system.

---

### Post by tiffanystardust on 2008-11-22
i tried the one off the dell website, just found another one and now it says hardware present so fingers crossed... hahaha :-)

meantime, i found this...but its for kde not gnome....any ideas? 
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

i'll catch up one day...heh!

THANKS!!! by the way..

tif x

---

### Post by Olivier2371 on 2008-11-22
Hi tiffanystardust,

You might to check the following to links.

[http://linuxwireless.org/en/users/Drivers/ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k")

[http://linuxwireless.org/en/users/Drivers/ath5k]("http://linuxwireless.org/en/users/Drivers/ath5k")

I hope this will clarified your situation.

---

