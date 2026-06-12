---
title: "edgy and rt73"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by littlespy on 2006-10-28
I have a belkin wireless usb device based on the rt73 chipset.  In dapper I used the cd that came with the device and ndiswrapper and it worked flawlessly.

Now in edgy it seems that they've included rt2x00 which is fine, excpet that it doesn't work.  It detects my device and creates wmaster0 and wlan0.  In the drop-down menu in gnome network manager it doesn't list and ESSID's so I just type in what mine is called and still it doesn't work.

I also tried ndiswrapper and the version of ndiswrapper in edgy won't even detect my device.  I know for a fact that the ndiswrapper module is loaded properly and the proper aliases in /etc/modprobe.d are set.  I've also blacklisted the rt73usb driver when I'm trying to use ndiswrapper so it doesn't interfere.

The next thing I tried was the driver from the ralink website, I've heard of people having success for it.  When I went to compile it, I guess it's a 32-bit driver because it won't compile on my amd64 system.  I may try to reinstall edgy with the i386 and see if I can get it to work then.  Any suggestions appreciateed.

I'm sure a lot of people are having the same problem as me, I hope someone can help.

---

### Post by littlespy on 2006-10-28
bump

---

### Post by JAwuku on 2006-11-01
I'm having the same problem here. I'm running Kubuntu Edgy (64-bit), and I use a Sitecom WL-113 USB wireless device.

The kernel recognizes it, and loads the rt73usb driver.

But I cannot get it to connect to the Internet, despite putting in the config details in the KDE Control Centre. I had no problem in Dapper 64-bit (I compiled the Ralink driver following the Ubuntu wiki).

I am considering to downgrade back to Dapper, and run my Edgy apps in a 32-bit chroot environment.

 One thing, littlespy, that I think may help is if you use the 64-bit Ralink Windows drivers from [www.ralinktech.com](www.ralinktech.com), this may work better with ndiswrapper. I haven't yet figured out how to use ndiswrapper, as I have not got it to work in the past.

cheers

---

### Post by oo00oo on 2006-11-04
This is the exact problem I have. I have to unload the rt73usb driver which Ubuntu loads but it doesnt actually work and load the rt73 drivers which work perfectly.

My card is a DWL-G122 V.C1 and that rt73 drivers work perfectly, but they are only 32bit ones, not too sure about the 64bit ones!

I just need a way to load the rt73 drivers automatically now as I  have to load them through terminal every reboot! 

Any help appreciated...

---

### Post by oo00oo on 2006-11-04
BTW. JAwuku - my ralink drivers worked in 6.06 then upgraded to 6.10 (edgy) and it was then that my wireless broke!

Just recompile the ralink drivers under the new kernel as you did before (because you have to) then unload the ubuntu driver

in terminal run:
modprobe -r rt73usb

then reload the freshly compiled rt73 driver (just read the readme in the file when you download it for compile instructions)

insmod rt73.ko

and it will work perfectly as in dapper! Good luck

---

### Post by splint-84 on 2006-11-07
I'm having the same problems as everybody else and following the help on the forum I have been able to compile and load the drivers from ralink... But... 

Does anyone else find that the drivers are quite slow?

If I bot into windows I can load google.com in maybe 2 secs where it easily takes 6-8 secs in ubuntu... I want to use ubuntu so I really wanna fix this! Have anyone else got this problem?

---

### Post by FrodoB on 2006-11-09
There have been some forum messages stating that ip6 is causing this. It does not sound like an rt73 issue to me. I am using one without problems.

---

### Post by defconoii on 2007-08-01
you can get the latest rt73 drivers here [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

