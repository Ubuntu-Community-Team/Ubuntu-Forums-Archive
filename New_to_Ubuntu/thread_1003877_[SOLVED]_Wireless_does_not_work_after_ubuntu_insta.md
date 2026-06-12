---
title: "[SOLVED] Wireless does not work after ubuntu installation"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Art3mis on 2008-12-06
Hi everyone,

I installed Ubuntu on my Dell Inspiron 6000,
but the wireless dosen't work.


Can anyone help me get the wireless up and running.


----I installed ubuntu on entire disk, so no windooze or whatsoever on my machine

---

### Post by nhasian on 2008-12-06
first lets find out what network adaptor you have.  in a terminal type:

```
lshw -C network
```

---

### Post by Art3mis on 2008-12-06
It says

PCI (sysfs)  
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:eb:2f:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.65 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:1f:f0:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

---

### Post by will11 on 2008-12-06
hello. i have an acer aspire one preloaded with windows. i duel booted it with ubuntu 8.10 and it works great. the only problem is that it wont connect to the internet. i went up to find new drivers in ubentu and it found the wireless card. i activated it but still no internet. im new to linux and would love simple totorial on how to do this.
thanks.

---

### Post by nhasian on 2008-12-06
hmm wireless radio=off

does Fn-F2 to turn it on?  please also see if this thread helps:

[http://ubuntuforums.org/showthread.php?t=242418](http://ubuntuforums.org/showthread.php?t=242418)

---

### Post by Art3mis on 2008-12-06
Well, thats the point FN+F2 does not turn it on>

Do I have to install any drivers or somethhing?


Sorry dude, the link you gave me doesnt help at all

---

### Post by will11 on 2008-12-06
that didn't help me either, sorry.

---

### Post by nhasian on 2008-12-06
do you have the latest bios for your system?  I believe it is A09.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094")

---

### Post by will11 on 2008-12-06
well i do for the acer aspire one.

---

### Post by Art3mis on 2008-12-06
yes everything is up to date.


Please I need my wireless working

---

### Post by nhasian on 2008-12-06
will11, do you also have an Intel PRO/Wireless 2200BG Network Adaptor?

I found this thread too:

[https://bugs.launchpad.net/ubuntu/+bug/82444](https://bugs.launchpad.net/ubuntu/+bug/82444)

it seems the network adaptor is detected, but in an off state.  you may need to adjust some settings in the bios to enable it as described here:

[https://bugs.launchpad.net/ubuntu/+bug/82444/comments/5](https://bugs.launchpad.net/ubuntu/+bug/82444/comments/5)

---

### Post by wolfen69 on 2008-12-06
go to system>administration>hardware drivers and see if the driver is there.

---

### Post by will11 on 2008-12-06
i have a atheros AR507EG wireless adapter.

---

### Post by sportscrazed2 on 2008-12-06
> **wolfen69 said:**
> go to system>administration>hardware drivers and see if the driver is there.

thats what worked for me when my wireless card didn't work but to download the driver you will have to connect with ethernet

---

### Post by lovelyvik293 on 2008-12-06
For atheros just use the madwifi driver,The How-to for this is:-
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by will11 on 2008-12-06
anything more simple

---

### Post by WinterMadness on 2008-12-06
when you install ubuntu, you have to install the windows XP wireless driver to get wireless to work

get ndiswrapper, goto your manufacturers website and download the driver and wireless will work once you use ndiswrapper to install it

---

### Post by lovelyvik293 on 2008-12-06
check it out
[http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971)

---

### Post by nhasian on 2008-12-06
try following my instructions here:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)



> **will11 said:**
> i have a atheros AR507EG wireless adapter.

---

### Post by will11 on 2008-12-07
i dont understand it

---

### Post by nhasian on 2008-12-08
okay i'll try to make it easier.  

This is to make your atheros wifi adaptor function in Ubuntu 8.10:

make sure your connected to the internet with your ethernet adaptor until we get your wifi adaptor working.

open up a terminal by going to Applications/Accessories/Terminal

then enter the following to install the intrepid backports:

First enter this to make sure you have updated sources:

```
sudo apt-get update
```

then enter this to make sure you have ubuntu up to date:

```
sudo apt-get upgrade
```


Finally enter this to install the backports module:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

almost done!  your wifi adaptor probably wont work yet until you edit the blacklist file like this:

```
sudo gedit /etc/modprobe.d/blacklist
```

at the bottom of the document add the lines:

```
blacklist ath_pci
blacklist ath_hal
```

then save and reboot.  now see if your wifi adaptor works.

> **will11 said:**
> i dont understand it

---

### Post by will11 on 2008-12-08
thank you so much. it worked perfectly.
thanks again.

---

