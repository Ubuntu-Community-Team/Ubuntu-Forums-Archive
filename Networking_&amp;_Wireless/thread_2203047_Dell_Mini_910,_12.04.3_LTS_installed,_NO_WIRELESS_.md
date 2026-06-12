---
title: "Dell Mini 910, 12.04.3 LTS installed, NO WIRELESS ability"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by joewx on 2014-02-01
Hello,

Laptop
Dell Mini 910 Inspirion
Wireless card: Wireless 802.11g Mini Card 

I have just done a complete install of 12.03.3 LTS.  It had been running the obsolete 9.04 Jaunty Jackope April 2009. 
Install went fine with the exception I have NO Wireless capability. The wireless icon is empty, Enable networking is checked, hotspot is good.
Switching WIFI on and off has no effect.  
Wireless worked fine until upgrade.

Ran command iwconfig.  Received message 

lo-no wireless extensions
eth0- no wireless extensions.

Ran comand nm-tool. Received message

State: asleep
Device: eth0
Type: Wired
Driver: r8169
State: unmanaged
Default: no
HW Address: 00:21:70:D7:EB:CC

Capabilities:
Carrier Detect: yes
WIred Properties Carrier: Off

I am new to Ubuntu. Please help.

Thanks.

---

### Post by chili555 on 2014-02-01
Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by joewx on 2014-02-01
> **chili555 said:**
> Please run and post:```
lspci -nn | grep 0280
```Thanks.

Ran lspci - nn | grep 0280

Results:
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] {rev 01}

---

### Post by praseodym on 2014-02-01
You need the missing firmware for the low-power chipset:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by chili555 on 2014-02-01
> **joewx said:**
> 
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] {rev 01}Please get a temporary wired ethernet connection and do:```
firmware-b43-lpphy-installer
```And after it has finished its processes:```
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet and tell us if it is working.

---

### Post by joewx on 2014-02-01
Not to try your patience, but I only have wireless connectivity.  I am using my standard laptop to talk with you.  How do I set up a temporary for the Mini which has no INTERNET?

Sorry.

Joe

---

### Post by chili555 on 2014-02-01
> **joewx said:**
> Not to try your patience, but I only have wireless connectivity.  I am using my standard laptop to talk with you.  How do I set up a temporary for the Mini which has no INTERNET?

Sorry.

JoeDownload the file referenced on any other computer:> [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) Transfer it on a USB stick or similar and drag it to your desktop. Then do:```
cd ~/Desktop
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe -r b43 && sudo modprobe b43
```

Try my patience?? If you saw me struggling with my first Linux computer in 2001 compiling HPNA, you'd see patience.

---

### Post by joewx on 2014-02-01
Chili
I am posting this with the Dell Mini which now has WIRELESS with MANY Thanks to you.  I really appreciate it.  

Are you in Berlin GE?

Joe

---

### Post by chili555 on 2014-02-01
Awesome! Glad it's working.

I am not in Berlin. Please check my location to the right. Are you buying the beer if I stop in Berlin?

---

### Post by praseodym on 2014-02-01
I live in Berlin.

Berlin, Germany ;)

Coming over for a beer?

---

### Post by chili555 on 2014-02-01
> **praseodym said:**
> I live in Berlin.

Berlin, Germany ;)

Coming over for a beer?I have no plans to do so, but I like to have a couple of free beers lined up wherever I go!

---

