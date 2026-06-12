---
title: "Dell D600 wireless trouble"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by elbarto_87 on 2008-09-22
Hi,
I have a dell D600 laptop which I have tried to install ubuntu on. On the startup screen, there is an error message regarding the b43 firmware for the wireless card and suggests I go to [http://linuxwireless.org](http://linuxwireless.org) to try an rectify the problem.

I have found this page [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) which I think has all the instructions I need, but I cannot connect my laptop to the internet to follow the instructions. I downloaded the files I needed and transfered them to the desktop of my laptop but then I got an allot of error messages when I used the "make" command detailed in the above link.

Is there anyway I can install what I need this way? What is the default location that programs etc download to when you use the "wget" command?

Thanks in advance,

Elbarto

Ps. the wireless card is a "Dell Wireless 1450 WLAN miniPCI Card" if anybody has any other suggestions?

---

### Post by shanix on 2008-09-22
Can we see the exact error message that you see when the system sytart up?
Also, one of the useful information to have here is the PCI ID for the device. Try the command below and paste the output.

$ lspci -vvnn | grep Wireless

---

### Post by superprash2003 on 2008-09-22
hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. connect via LAN to the internet and follow those steps

---

### Post by elbarto_87 on 2008-09-23
Thank you for the replies,

I tried ```
lspci -vvnn | grep Wireless
``` but there was no output

I tried to follow the site listed, but I didn't have any luck. There was quite a few steps to follow, maybe this isn't the easiest thing for a linux novice to be attempting. After trying the above dirrections, I no longer get an error on start up. I think this may be from blacklisting the b43 firmware?

Some more information regarding my wireless card.
```
$ lspci -n | grep 
'14e4:43'02:03.0 0280: 14e4:4324 (rev 03)
```

I wasn't sure exactly what step to follow on the website. There are multiple step 2's listed so maybe thats where I made an error. I used step f I think.

Do you know if these network cards will be better supported in the next release of ubuntu? 

Thank you

Elbarto

---

### Post by superprash2003 on 2008-09-23
follow the correct step according to the output you get

---

### Post by shanix on 2008-09-23
Install ndiswrapper and try the driver from the following locatieon:

[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

Or if you like, install ndisgtk is a GUI tool for ndiswrapper that might make things easier.

---

### Post by elbarto_87 on 2008-09-23
Thank you all once again for your help. I had a brainwave to pull the wireless card out of a broken Dell inspiron 6000 that I completely forgot about. My D600 is now fully functional with ubuntu so I am very happy :). I probably took the easy way out but I think it will have saved me some sanity.

Thank You

Elbarto

---

