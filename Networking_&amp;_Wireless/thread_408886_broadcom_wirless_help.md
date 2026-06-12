---
title: "broadcom wirless help"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by cessna_89702 on 2007-04-13
Hey im trying to configure my broadcom wireless chip and i have the 64 bit version of ubuntu 6.06

if i run ndiswrapper -l    I get back ```
zach@zach-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present

```

if i run ```
lspci | grep Broadcom\ Corporation
```   i get back ```
zach@zach-laptop:~$ lspci | grep Broadcom\ Corporation
0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

```

any tutorials for configuring this??

---

### Post by rjfioravanti on 2007-04-13
what happens when you do iwlist scan

---

### Post by cessna_89702 on 2007-04-13
zach@zach-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by rjfioravanti on 2007-04-13
Thats not good !

what procedure did you follow to install ndiwrapper

Did you execute the following command yet?

sudo ndiswrapper -m

---

### Post by stump138 on 2007-04-13
have you tried this one?

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by cessna_89702 on 2007-04-13
yes i have ran that command and i think the tutorial he posted is what i use (or one of them)

I would just use my wireless adapter that goes in the usb but that doesnt even get the detected on the 64 bit

---

### Post by caffienefree on 2007-04-13
The before mentioned guide uses fwcutter. If you prefer to use ndiswrapper, this guide will walk you through.

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by cessna_89702 on 2007-04-13
zach@zach-laptop:~$ sudo ndiswrapper -i /home/zach/Desktop/bcmlw5.inf
Installing bcmlw5
couldn't copy /home/zach/Desktop/bcmlw5.inf at /usr/sbin/ndiswrapper line 135.

---

### Post by cessna_89702 on 2007-04-13
so whats wrong?

---

### Post by caffienefree on 2007-04-14
You used the wrong name. It's bcmwl5.inf, not bcmlw5.inf
[B]ndiswrapper -l
ndiswrapper -e whateveryounamedthedriver
rmmod ndiswrapper
ndiswrapper -i /path/to/bcmwl5.inf
modprobe ndiswrapper
iwlist scanning[/B]

You need to make sure that you have bcmwl5.inf and bcmwl5.sys in the same place, and that you have 64-bit drivers, not 32-bit ones. Also, that you have the proper drivers for your device.

---

### Post by cessna_89702 on 2007-04-14
ndiswrapper -l says 
```
Installed ndis drivers:
bcmlw5  invalid driver!
bcmwl5          driver present
zach@zach-laptop:~$

```

thats the one that i want present right? Where would they be so I can delete the rest

---

### Post by cessna_89702 on 2007-04-14
ok now when i run ndiswrapper -l I get only the right driver

```
Installed ndis drivers:
bcmwl5          driver present

```


on ```
ndiswrapper -i /path/to/bcmwl5.inf
``` where would it be probably

---

### Post by cessna_89702 on 2007-04-14
Ok i did what you said and it said  its already installed. In my etc/ndiswrapper I have two files named   "bcmwl5.inf"     &   "bcmwl564.sys"

iwconfig is getting no wireless extensions 

I believe those are the 64 bit drivers but i will check later and also reboot to see if that will help.

any ideas as to what might be wrong though

---

### Post by cessna_89702 on 2007-04-14
ok so i got rid of those ones & insalled 64 bit but it still doesnt work

---

