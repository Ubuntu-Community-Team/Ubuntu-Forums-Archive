---
title: "ndiswrapper: module verification failed: signature and/or  required key missing - tai"
date: 2015-09-20
forum: Networking &amp; Wireless
---

### Post by Dean_Witcraft on 2015-09-20
A few minutes after I made this post, the WiFi disconnected and Ubuntu doesn't seem to be seeing the WiFi any more. My purpose is now to get help making it work.

I installed 
Netgear N-300/ WNA3100 USB Adapter for Ubuntu 14.04
I have some indications that it failed, but somehow it's working. 
I'd like to understand what the failure messages at the bottom of this post mean:


I'm new to Ubuntu (and to administering my own Linux environment).


lsusb
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]


$ sudo apt-get install ndisgtk ndiswrapper-dkms linux-headers-generic build-essential


$ cd Downloads
$ ll
Sep 19 14:44 2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
Jun  7  2011 Broadcom_bcm43xx_USB_32_64bit_v2/
Sep 19 15:02 ndisgtk_0.8.5-1ubuntu1_amd64.deb


$ sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
couldn't find install section "BCM43XXN32" -
installation may be incomplete


$ sudo modprobe -v ndiswrapper
insmod /lib/modules/3.19.0-28-generic/updates/dkms/ndiswrapper.ko 
$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
$ dmesg | grep ndis
[ 3235.656932] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[ 3235.660636] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 3235.750980] usbcore: registered new interface driver ndiswrapper

---

### Post by Dean_Witcraft on 2015-09-20
Well, it worked for a while and then failed. I'm back to using wired for this post. A little more information
$ dmesg | grep ndis
[   11.944812] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   11.945859] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   14.669723] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   15.684331] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   15.684337] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   15.684343] ndiswrapper (mp_halt:254): device ffff8800ba3c38c0 is not initialized - not halting
[   15.684345] ndiswrapper: device eth%d removed
[   15.684407] ndiswrapper: probe of 1-3:1.0 failed with error -22
[   15.684447] usbcore: registered new interface driver ndiswrapper

---

### Post by jeremy31 on 2015-09-20
What does ```
ndiswrapper -l
``` Have to say as the module verification failed is a normal thing

---

### Post by Dean_Witcraft on 2015-09-20
$ ndiswrapper -l
bcmn43xx64 : driver installed
device (0846:9020) present

---

### Post by Dean_Witcraft on 2015-09-20
That's a good thing :-) Thanks. I also understand what tainted kernal means now: [http://unix.stackexchange.com/questions/118116/linux-what-is-a-tainted-kernel](http://unix.stackexchange.com/questions/118116/linux-what-is-a-tainted-kernel)
but there are other ugly looking things in the console messages.
HOWEVER, the WiFi is working again. :-p

---

### Post by jeremy31 on 2015-09-20
I wouldn't expect it to work for very long as I had the same card and mailed it to chili555.  See his post [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

---

### Post by mheizer on 2015-11-29
I'm trying to get the WNDA3100 to work on lubuntu 14.04.  I've tried pretty much everything I can find in the posts.  ndiswrapper is installed along with the utilities.  bcmn43xx32.inf installed.  When I run iwconfig I get this I get this

iwconfig
enp1s8    no wireless extensions.

lo        no wireless extensions.

enxe091f53fbe91  IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



and 
dmesg | grep ndis
[  372.157341] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  372.161173] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  372.647138] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  372.921283] usbcore: registered new interface driver ndiswrapper
[  373.303038] ndiswrapper 1-3:1.0 enxe091f53fbe91: renamed from wlan0
[  373.309881] ndiswrapper: interface renamed to 'enxe091f53fbe91'


Any ideas?

---

