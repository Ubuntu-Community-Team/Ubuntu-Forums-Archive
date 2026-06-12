---
title: "inspiron 1501 with 1490 wifi card, and feisty 64bit version: how-to guide requested"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by loso on 2007-04-29
I tried get wifi working all day yesterday, and all in vain:(  I've attempted a ton of different how-to guides (that are all written for computers with slightly different specs than my own) and none have worked so far.  

Here are my specs:
dell inspiron 1501 with AMD turion 64 x2 processor
dell wireless 1490 card (802.11a/g), lscpi gives the following:
```

05:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```
The computer came with windows vista 32bit pre-installed (the dell website seems to care about that, I don't know why)

Has anyone gotten wifi working on these specs, and if so, how did you do it?

---

### Post by der_vegi on 2007-05-01
yeah, i've got the same notebook with the same card and right now, i'm surfing in the internet with it (WPA-encrypted).

using bcm43xx would be the nicest way as it is a native driver. it connects to my access point waaay faster than ndiswrapper but after a few seconds the ping goes to 4000ms and more. so that one is not usable (yet?).

but i got the card working with ndiswrapper using the firmware version  4.100.15.5. it sometimes takes a couple of tries to connect to my WPA-network and sometimes looeses the connection.
```
sudo modprobe -r ndiswrapper
```
and then```
sudo modprobe ndiswrapper
``` 
helps in this case.

here are the steps i would recommend:

1. download [the windows-driver]("http://ftp.us.dell.com/network/R151517.EXE") from dell.

2. install ndiswrapper

```
sudo apt-get install ndiswrapper-utils-1.9
```

3. unload bcm43xx
```
sudo modprobe -r bcm43xx
```

4. install unzip and - only if you want to identifiy the firmware-version - bcm43xx-fwcutter

5. go to the download directory and run
```
unzip R151517.EXE
```

6. go to the created subdirectory "DRIVER"
```
cd DRIVER
```

7. if you want to identify the firmware version run (not really neccessary)
```
bcm43xx-fwcutter -i bcmwl564.sys
```
the output should be
```
filename   :  bcmwl564.sys
  version    :  4.100.15.5
```

8. install the driver with
```
sudo ndiswrapper -i bcmwl5.inf
```

9. load the ndiswrapper module
```
sudo modprobe ndiswrapper
```

10. blacklist the bcm43xx
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

11. make the ndiswrapper load at boot time
```
sudo echo ndiswrapper >> /etc/modules
```

now you should see your wireless network by typing
```
iwlist eth1 scan
```

i hope that helped.
if someone has gotten the bcm43xx driver to work with this network card, please let me know

---

### Post by der_vegi on 2007-05-01
ha, good news! i am one of these guys annoying the support of hardware vendors who don't have linux drivers... *g

a few hours ago i have written an email to the dell support, complaining about the lack of linux drivers for their broadcom wireless cards. they have just told me, that "officially we do not support Linux OS systems yet, but that might change soon, some plans are already made. but i can't tell you a date yet."

maybe that's a reaction to the discussions on [http://www.dellideastorm.com]("http://www.dellideastorm.com")?

so one day we hopefully won't need these howtos any more, being able to download the dell driver over the ubuntu-repos?

---

### Post by loso on 2007-05-01
[http://news.bbc.co.uk/2/hi/business/6610901.stm](http://news.bbc.co.uk/2/hi/business/6610901.stm)

That day is comming soon.  Looks like Dell is going to sell inspirons preloaded with Ubuntu :) :)

---

### Post by der_vegi on 2007-05-01
Cool! But i hope they won't put Feisty on Dell notebooks before all those nasty bugs in the amd64 version got squeezed out... I already have problems explaining to my friends why my computer is crashing so often running Ubuntu and not Windows. :(

---

### Post by der_vegi on 2007-05-06
wooohhooo! i just downloaded the standalone version of bcm43xx from [ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2]("ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2"), installed it and now it works! ping is okay, connection speed as well...

---

### Post by loso on 2007-05-10
cool!  But how do you install it?

---

