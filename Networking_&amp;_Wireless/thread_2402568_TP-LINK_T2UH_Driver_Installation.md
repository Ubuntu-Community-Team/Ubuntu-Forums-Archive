---
title: "TP-LINK T2UH Driver Installation"
date: 2018-10-01
forum: Networking &amp; Wireless
---

### Post by komrat on 2018-10-01
Hi!
I've recently bought TP-LINK T2UH and I'm struggling with installing proper driver in order to make it work. I've followed this: 
[https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.22-beta](https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.22-beta) and this [https://ubuntuforums.org/showthread.php?t=2339960](https://ubuntuforums.org/showthread.php?t=2339960)
but I ended up installing wrong driver -> 4.3.20. When I try to uninstall my current driver (4.3.20) by entering these commands: 
```

[COLOR=#24292E][FONT=SFMono-Regular]# DRV_NAME=rtl8812AU
# DRV_VERSION=4.3.20[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]
[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]# sudo dkms remove ${DRV_NAME}/${DRV_VERSION} --all[/FONT][/COLOR][SIZE=1] 
[/SIZE]
```
I get this:
```

Error! There are no instances of module: rtl8812AU
4.3.20 located in the DKMS tree.

```
I also tried entering driver's location ->
```
 cd ~/Downloads/rtl8812AU-driver-4.3.20 
``` and running ```
 # sudo make uninstall 
``` and I get 
```

rm -f /lib/modules/4.15.0-34-generic/kernel/drivers/net/wireless//8812au.ko
/sbin/depmod -a 4.15.0-34-generic

```
Running ```
# sudo modprobe 8812au
``` followed by ```
# dmesg | grep 8812
``` makes this pop up: 
```
8812au: loading out-of-tree module taints kernel.
8812au: module verification failed: signature and/or required key missing - tainting kernel
RTL871X: rtl8812au v4.3.20_16317.20160108
usbcore: registered new interface driver rtl8812au

```
Ubuntu version is up to date.
The other driver is installed, but it seems not to be used. Is there possibility of selecting the correct driver (4.3.22-beta)? 
I have no idea what to do since I'm new to ubuntu. I would really appreciate tips on how to make it work properly.

---

### Post by chili555 on 2018-10-01
Please run and post:```
lsusb

```Thanks.

---

### Post by komrat on 2018-10-02
```
Bus 002 Device 004: ID 046d:c245 Logitech, Inc. G400 Optical Mouse
Bus 002 Device 003: ID 148f:761a Ralink Technology, Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 05ac:024f Apple, Inc. 
Bus 003 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I believe that "Bus 002 Device 003: ID 148f:761a Ralink Technology, Corp. " is what we're looking for.

---

### Post by chili555 on 2018-10-02
> I believe that "Bus 002 Device 003: ID 148f:761a Ralink Technology, Corp. " is what we're looking for.Correct. 

Just for the benefit of you and the searchers, this device comes, so far, in two versions. This v2 is not an rtl8812au device. Let's google its usb.id and find out what it actually is. The first listing is the always reliable WikiDevi: [https://wikidevi.com/wiki/TP-LINK_Archer_T2U](https://wikidevi.com/wiki/TP-LINK_Archer_T2U)

> Probable Linux driver
mt7610u_sta
Ahhhh! The always tricky, never straightforward mt7610u! 

This driver has a difficult history with later Linux kernels, for example, here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u) You might be interested in my post #18.

However, post #4 here claims that it is now working! [https://ubuntuforums.org/showthread.php?t=2375919](https://ubuntuforums.org/showthread.php?t=2375919) We shall soon find out!!!

With a working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:```
sudo apt update
sudo apt install git
git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo make installfw
sudo insmod mt7610u.ko
```Before we proceed with further needed steps, tell us if a wireless interface is created:```
iwconfig
```And if you can connect, pull web pages, etc., without difficulty.

---

### Post by komrat on 2018-10-02
After running "make" I get:
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-34-generic/build M=/home/komrat/mt7610u modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-34-generic'
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"

```
and so on... 
```
Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/komrat/mt7610u/mt7610u.mod.o
  LD [M]  /home/komrat/mt7610u/mt7610u.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-34-generic'

```After "sudo make installfw":
```
cp -n firmware/* /lib/firmware

```And then:
```
sudo insmod mt7610u.ko
insmod: ERROR: could not insert module mt7610u.ko: Unknown symbol in module

```
iwconfig shows that there are no wireless extensions:
```
enp3s0    no wireless extensions.


lo        no wireless extensions.

```

EDIT:
So I've installed libelf-dev and now after running "make" I get:
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-34-generic/build M=/home/komrat/mt7610u modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-34-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-34-generic'
```
but the rest stays the same.

---

### Post by chili555 on 2018-10-02
After installing libelf-dev, I recommend that you sweep out all the remnants of the first faulty build and start fresh:```
cd mt7610u
[COLOR="#FF0000"]make clean[/COLOR]
make
sudo insmod mt7610u.ko
```Now does the error still appear?

---

### Post by komrat on 2018-10-03
Now it is changed to:
```
insmod: ERROR: could not insert module mt7610u.ko: Invalid module format
```

---

### Post by chili555 on 2018-10-03
> make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-[COLOR="#FF0000"]34[/COLOR]-generic'Is that the running kernel in your system?```
uname -r
```Is that the latest kernel you have installed?```
ls /boot
```

---

### Post by komrat on 2018-10-03
Thank you for your answers but I've decided to return this WiFi adapter to the store and buy fully compatible adapter. Could you recommend me any?

---

### Post by chili555 on 2018-10-03
I suggest that you check here: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by reilg on 2019-03-22
Ugh.. 2019 and I still didn't do enough research about this product. 
Now I'm stuck with it =(

I followed this thread and I can see the adapter when I do **iwconfig**
```
wlan0     Ralink STA

enp1s0    no wireless extensions.


wlx503eaa53f077  IEEE 802.11bgn  ESSID:"---"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 0C:80:63:CD:28:39
          Bit Rate:150 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=87/100  Signal level=96/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.
```

But it cannot seem to detect any wifi networks.

I do want to note that I have a _TP Link Wireless N Nano USB_ connected as well. I got the AC600 because I wanted to connect to my router at 5GHz.
I was so happy with the Nano USB that I didn't even think to check on the AC600 :(

@chilli555 - Any chance you know what else I can do?

---

### Post by praseodym on 2019-03-22
Uninstall it and try this one

[https://ubuntuforums.org/showthread.php?t=2408678&page=2&p=13825311#post13825311](https://ubuntuforums.org/showthread.php?t=2408678&page=2&p=13825311#post13825311)

---

### Post by chili555 on 2019-03-22
> **reilg said:**
> <snip>

I do want to note that I have a _TP Link Wireless N Nano USB_ connected as well. I got the AC600 because I wanted to connect to my router at 5GHz.
I was so happy with the Nano USB that I didn't even think to check on the AC600 :(

@chilli555 - Any chance you know what else I can do?The most difficult problem we struggle with is trying to simultaneously troubleshoot two USB wireless devices when, in fact, there is also apparrently a working internal device.

It it possible to select just one of these three and we'll pour all our efforts into it? Which?

---

