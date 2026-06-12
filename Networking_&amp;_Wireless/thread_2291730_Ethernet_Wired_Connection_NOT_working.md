---
title: "Ethernet Wired Connection NOT working"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by swapnil9 on 2015-08-22
I installed Ubuntu 14.04 LTS as a dual boot on windows 7. I am able to connect Ubuntu to Wifi, however Ethernet Wired connections doesn't seem to be working. Also, eth0 doesn't show up on ifconfig -a. Any help on getting the wired connection sorted? 


swapnil@swapnil-Inspiron-N5110:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140454 (140.4 KB)  TX bytes:140454 (140.4 KB)

wlan0     Link encap:Ethernet  HWaddr cc:af:78:20:11:87  
          inet addr:192.168.43.26  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::ceaf:78ff:fe20:1187/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2324365 (2.3 MB)  TX bytes:450100 (450.1 KB)

---

### Post by chili555 on 2015-08-22
If you have no eth0, that suggests that the driver and hardware haven't matched up yet. Let's start by identifying the hardware; from a terminal:```
lspci -nn | grep 0200
```

---

### Post by swapnil9 on 2015-08-22
This is what I get:

> swapnil@swapnil-Inspiron-N5110:~$ lspci -nn | grep 0200
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
0b:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)



---

### Post by chili555 on 2015-08-22
> Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)This device is supposed to work with the driver r8169. Let's load it and see what happens:```
sudo modprobe r8169
```Any change?```
ifconfig
```Is it somehow blacklisted?```
cat /etc/modprobe.d/blacklist.conf
ls /etc/modprobe.d
```

---

### Post by swapnil9 on 2015-08-23
```
sudo modprobe r8169


```

This causes the wired connection to constantly make an attempt to connect, which eventually results in "Disconnected - you are offline" prompt.

```
ifconfig



```


```
swapnil@swapnil-Inspiron-N5110:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 78:2b:cb:ec:10:da  
          inet6 addr: fe80::7a2b:cbff:feec:10da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1986 errors:0 dropped:2 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:203466 (203.4 KB)  TX bytes:13037 (13.0 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13457 (13.4 KB)  TX bytes:13457 (13.4 KB)


wlan0     Link encap:Ethernet  HWaddr cc:af:78:20:11:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

eth0 does show up now. However, the connection is NOT established.


```
cat /etc/modprobe.d/blacklist.conf



```

```
swapnil@swapnil-Inspiron-N5110:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8169



```



```
ls /etc/modprobe.d


[CODE]swapnil@swapnil-Inspiron-N5110:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         fbdev-blacklist.conf
blacklist-ath_pci.conf      blacklist-oss.conf           forcedeth.conf
blacklist.conf              blacklist-rare-network.conf  iwlwifi.conf
blacklist-firewire.conf     blacklist-watchdog.conf      mlx4.conf
blacklist-framebuffer.conf  dkms.conf                    vmwgfx-fbdev.conf



```

[/CODE]

---

### Post by Hadaka on 2015-08-23
hi your wifi driver **r8169** is currently in the blacklist file... Let's fix that

```
#swapnil@swapnil-Inspiron-N5110:~$ cat /etc/modprobe.d/blacklist.conf
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist [COLOR=#ff0000]r8169[/COLOR]
```
Please open a terminal and copy and paste..
```
sudo sed -i '/^blacklist r8169/ d' /etc/modprobe.d/blacklist.conf
```
boot then do,,
```
sudo modprobe r8169
```
thanks.

---

### Post by swapnil9 on 2015-08-23
Hi,

I unlisted r8169 from the blacklist and rebooted. Further I added the module r8169 with

```
sudo modprobe r8169
```

However, the wired connection just makes an attempt to connect and **fails**.

Any further help?

---

### Post by Hadaka on 2015-08-23
Hi, lets verify it was deleted..
please do and post..
```
cat /etc/modprobe.d/blacklist.conf | grep "blacklist"
```

thanks

---

### Post by swapnil9 on 2015-08-23
On doing this:
```
cat /etc/modprobe.d/blacklist.conf | grep "blacklist"


```

The blacklist generated is:

```
swapnil@swapnil-Inspiron-N5110:~$ cat /etc/modprobe.d/blacklist.conf | grep "blacklist"blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac



```

---

### Post by chili555 on 2015-08-23
Please do:```
sudo ethtool -s eth0 autoneg off
```Also, please substitute another known good cable, unless, of course, you are dual-booting with Windows and you know it works. 

Also, let's have a look at:```
cat /etc/modprobe.d/dkms.conf
```

---

### Post by swapnil9 on 2015-08-23
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ethtool -s eth0 autoneg off[/FONT][/COLOR]
```

Did this, but the wired network continued trying to connect and fail.

Yes, I am dual booting with windows and know for sure the cable works. 

On:
```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/modprobe.d/dkms.conf[/FONT][/COLOR]
```

I get the following o/p:
```
~$ cat /etc/modprobe.d/dkms.conf# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
```

---

### Post by chili555 on 2015-08-23
Please do:```
sudo apt-get install r8168-dkms
```After it installs, reboot.

If you have no other internet connectivity, download the package here: [https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

You will also need its dependency dkms: [http://packages.ubuntu.com/trusty/dkms](http://packages.ubuntu.com/trusty/dkms)

Transfer them on a USB stick or similar to your desktop. Then:```
cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```Reboot and tell us if it's now working.

---

### Post by swapnil9 on 2015-08-23
Unfortunately, no. It's not working. I did all the above mentioned steps, managed to install successfully. 

```
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo dpkg -i dkms*.deb(Reading database ... 164696 files and directories currently installed.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) over (2.2.0.3-1.1ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
r8168-dkms-8.040.00/src/
r8168-dkms-8.040.00/src/Makefile
r8168-dkms-8.040.00/src/r8168_asf.c
r8168-dkms-8.040.00/src/Makefile_linux24x
r8168-dkms-8.040.00/src/r8168_asf.h
r8168-dkms-8.040.00/src/r8168_dash.h
r8168-dkms-8.040.00/src/r8168_n.c
r8168-dkms-8.040.00/src/rtltool.h
r8168-dkms-8.040.00/Makefile
r8168-dkms-8.040.00/dkms.conf
r8168-dkms-8.040.00/
r8168-dkms-8.040.00/README
r8168-dkms-8.040.00/src/rtl_eeprom.h
r8168-dkms-8.040.00/autorun.sh
r8168-dkms-8.040.00/src/rtltool.c
r8168-dkms-8.040.00/src/rtl_eeprom.c
r8168-dkms-8.040.00/src/r8168.h
r8168-dkms-8.040.00/src/r8168_realwow.h
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo dkms add -m r8168-dkms -v 8.040.00


Creating symlink /var/lib/dkms/r8168-dkms/8.040.00/source ->
                 /usr/src/r8168-dkms-8.040.00


DKMS: add completed.
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo dkms build -m r8168-dkms -v 8.040.00


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all............
cleaning build area....


DKMS: build completed.
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo dkms install -m r8168-dkms -v 8.040.00


r8168:
Running module version sanity check.


Good news! Module version 8.040.00-NAPI for r8168.ko
exactly matches what is already found in kernel 3.19.0-25-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod.......


DKMS: install completed.
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo depmod -a
swapnil@swapnil-Inspiron-N5110:~/Desktop$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
swapnil@swapnil-Inspiron-N5110:~/Desktop$ echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169



```

However, I noticed that eth0 was not showing up on ifconfig.

```
~$ ifconfig -alo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140454 (140.4 KB)  TX bytes:140454 (140.4 KB)


wlan0     Link encap:Ethernet  HWaddr cc:af:78:20:11:87  
          inet addr:192.168.43.26  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::ceaf:78ff:fe20:1187/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2324365 (2.3 MB)  TX bytes:450100 (450.1 KB)
```

---

### Post by praseodym on 2015-08-23
Is the driver loaded?
```

sudo modprobe -rfv r8169 r8168
sudo modprobe -v r8168
lsmod
ifconfig -a
dkms status
```

---

### Post by swapnil9 on 2015-08-24
Hi,

Just wanted to say a big thanks to Chili555, Praseodym, Hadaka for their support and guidance. 

I removed both r8168/9 and started from scratch. 
```
rmmod r8168
```

```
rmmod r8169
```

Installed r8168 and dkms package. The link for downloading r8168 and dkms package is the same as provided by Chili555 in the thread.

```
cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 

```

 Made sure that the module is loaded. Booted.

```
sudo modprobe r8168
```

That did the trick. Got my ethernet up and running. 

Cheers :)

---

