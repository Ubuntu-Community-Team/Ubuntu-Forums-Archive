---
title: "WUA-1340 will not work no matter what"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by disco22522 on 2013-12-06
```
Linux kali 3.7-trunk-amd64 #1 SMP Debian 3.7.2-0+kali8 x86_64 GNU/Linux
```
SAGER NP6370 W350ET Laptop
I have install the .inf file using ndiswrapper, BUT i get this error trying to finalize the setup 

```
root@kali:~# sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to  ...
sh: 1: Syntax error: end of file unexpected
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.
```

I've tried posting on Kali Forums but they won't even approve my post because they're nazi's or something.


I am on a laptop and would prefer using my onboard wireless... here is lspci

```
root@kali:~# lsusb
Bus 001 Device 004: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 005: ID 07d1:3c04 D-Link System WUA-1340
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 004 Device 003: ID 5986:0401 Acer, Inc 
```
```
root@kali:~# lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd4 (rev a1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
```
```
root@kali:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d9:9e:c7  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fed9:9ec7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72488948 (69.1 MiB)  TX bytes:5239186 (4.9 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3360 (3.2 KiB)  TX bytes:3360 (3.2 KiB)
```
```
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

But I google-fu and my skills have rendered and solution null. I would very much love to get away from ethernet and actually use my laptop to it's fullest extent under Linux.. If anyone can lend me a helping hand that would be absolutely beauitful of them.

---

### Post by disco22522 on 2013-12-06
I have been following this tutorial: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

I downloaded the dropbox file and ran "make" this is what is left:

```
root@kali:~/rtl# make
make -C /lib/modules/3.7-trunk-amd64/build M=/root/rtl modules
make[1]: Entering directory `/usr/src/linux-headers-3.7-trunk-amd64'
  CC [M]  /root/rtl/base.o
/root/rtl/base.c: In function ‘_rtl_init_mac80211’:
/root/rtl/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/root/rtl/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/root/rtl/base.c: In function ‘rtl_send_smps_action’:
/root/rtl/base.c:1432:16: error: ‘struct <anonymous>’ has no member named ‘sta’
make[4]: *** [/root/rtl/base.o] Error 1
make[3]: *** [_module_/root/rtl] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7-trunk-amd64'
make: *** [all] Error 2
```

---

### Post by disco22522 on 2013-12-06
I'm recieving this error.... and it won't let me probe, Module not found.
```
root@kali:~/rtl# make
make -C /lib/modules/3.7-trunk-amd64/build M=/root/rtl modules
make[1]: Entering directory `/usr/src/linux-headers-3.7-trunk-amd64'
  CC [M]  /root/rtl/base.o
/root/rtl/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/root/rtl/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/root/rtl/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/root/rtl/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/root/rtl/base.c:1432:16: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;sta&#8217;
make[4]: *** [/root/rtl/base.o] Error 1
make[3]: *** [_module_/root/rtl] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7-trunk-amd64'
make: *** [all] Error 2
```

I have started [THIS]("http://ubuntuforums.org/showthread.php?t=2192226") thread to avoid reviving this old one.

---

### Post by disco22522 on 2013-12-06
```
Linux kali 3.7-trunk-amd64 #1 SMP Debian 3.7.2-0+kali8 x86_64 GNU/Linux
```
SAGER NP6370 W350ET Laptop
I have install the .inf file using ndiswrapper, BUT i get this error trying to finalize the setup 

```
root@kali:~# sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to  ...
sh: 1: Syntax error: end of file unexpected
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.
```

I've tried posting on Kali Forums but they won't even approve my post because they're nazi's or something.


I am on a laptop and would prefer using my onboard wireless... here is lspci

```
root@kali:~# lsusb
Bus 001 Device 004: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 005: ID 07d1:3c04 D-Link System WUA-1340
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 004 Device 003: ID 5986:0401 Acer, Inc 
```
```
root@kali:~# lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd4 (rev a1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
```
```
root@kali:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d9:9e:c7  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fed9:9ec7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72488948 (69.1 MiB)  TX bytes:5239186 (4.9 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3360 (3.2 KiB)  TX bytes:3360 (3.2 KiB)
```
```
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

But I google-fu and my skills have rendered and solution null. I would  very much love to get away from ethernet and actually use my laptop to  it's fullest extent under Linux.. If anyone can lend me a helping hand  that would be absolutely beauitful of them.

I have been following this tutorial: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

I downloaded the dropbox file and ran "make" this is what is left:

```
root@kali:~/rtl# make
make -C /lib/modules/3.7-trunk-amd64/build M=/root/rtl modules
make[1]: Entering directory `/usr/src/linux-headers-3.7-trunk-amd64'
  CC [M]  /root/rtl/base.o
/root/rtl/base.c: In function ‘_rtl_init_mac80211’:
/root/rtl/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/root/rtl/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/root/rtl/base.c: In function ‘rtl_send_smps_action’:
/root/rtl/base.c:1432:16: error: ‘struct <anonymous>’ has no member named ‘sta’
make[4]: *** [/root/rtl/base.o] Error 1
make[3]: *** [_module_/root/rtl] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7-trunk-amd64'
make: *** [all] Error 2
```

I've also been following the old Realtek 8723 thread but I'm still running into walls - I simply cannot get this to work at all. Neither the Realtrek 8723 or the WUA-1340. Any help would be greatly appreciated, as I would very much love to have wireless capability back.

---

### Post by chili555 on 2013-12-06
I don't know much about Kali, but I have a few comments. Why do you tthink this is an rtl8723ae device?> 07d1:3c04 D-Link System WUA-1340I think its driver is rt73usb:```
$ modinfo rt73usb | grep 3C04
alias:          usb:v[COLOR="#FF0000"]07D1[/COLOR]p[COLOR="#FF0000"]3C04[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```Is rt73usb not on your system? Before you turn yourself inside out compiling the wrong driver, let's see about the right driver.> I've tried posting on Kali Forums but they won't even approve my post because they're nazi's or something.Actually, I doubt there is anyone over there that knows; this is pretty arcane stuff.

As for your google-foo, search Google for the device ID 07d1:3c04 and you'll see: [https://wiki.debian.org/WiFi/rt73](https://wiki.debian.org/WiFi/rt73) and this: [http://cateee.net/lkddb/web-lkddb/RT73USB.html](http://cateee.net/lkddb/web-lkddb/RT73USB.html)

---

### Post by disco22522 on 2013-12-06
I've actually followed that first link and it got me nowhere. Nothing is showing up in WICD.  thank you for the quick reply Chili.

---

### Post by chili555 on 2013-12-06
First, is rt73usb present in your system?```
sudo modprobe rt73usb
```If it isn't there, you will get an error, of course. Second, does the driver cover your exact device?```
modinfo rt73usb | grep 3C04
```Do you need but lack firmware?```
dmesg | grep rt73
```Is a wireless interface created?```
iwconfig
```

---

### Post by disco22522 on 2013-12-06
```
root@kali:~# sudo modprobe rt73usb
ERROR: could not insert 'rt73usb': Invalid argument
```

This isn't making any sense to me... As I literally just installed that component.

I do not think this is a Realtek device, I'm simply using the WUA-1340 since I could not get that work (which is my onboard and I would prefer to get that working, then I would not need WUA-1340)


After some more searching, I ran into someone having an issue with their Realtrek 8723. Although, I'm getting errors that I do not understand.....

```
root@kali:~# wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz
--2013-12-06 16:04:10--  http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
Resolving dl.dropbox.com (dl.dropbox.com)... 23.21.195.168
Connecting to dl.dropbox.com (dl.dropbox.com)|23.21.195.168|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz [following]
--2013-12-06 16:04:10--  http://dl.dropboxusercontent.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.252.164
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.252.164|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8997390 (8.6M) [application/octet-stream]
Saving to: `STDOUT'

100%[======================================>] 8,997,390    183K/s   in 47s     

2013-12-06 16:04:59 (185 KB/s) - written to stdout [8997390/8997390]

root@kali:~# cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
root@kali:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.7-trunk-amd64/build M=/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.7-trunk-amd64'
  CC [M]  /root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:16: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;sta&#8217;
make[4]: *** [/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[3]: *** [_module_/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7-trunk-amd64'
make: *** [all] Error 2
root@kali:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# sudo make install
make -C /lib/modules/3.7-trunk-amd64/build M=/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.7-trunk-amd64'
  CC [M]  /root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:16: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;sta&#8217;
make[4]: *** [/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[3]: *** [_module_/root/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7-trunk-amd64'
make: *** [all] Error 2


```

---

### Post by chili555 on 2013-12-06
So you are trying to get the internal 8723 working and *NOT* the WUA-1340 which is the title of your thread?? I may be confused... Please clarify and let's stick to one and one only task. > rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012This is not going to work - ever - on a 3.7 kernel. The solution, if that's what we're working on now, is elsewhere.

---

### Post by disco22522 on 2013-12-06
```
root@kali:/home# sudo modprobe rt73usb
ERROR: could not insert 'rt73usb': Invalid argument
root@kali:/home# apt-get update && apt-get install firmware-ralink
Hit http://security.kali.org kali/updates Release.gpg
Hit http://http.kali.org kali Release.gpg
Hit http://security.kali.org kali/updates Release
Hit http://http.kali.org kali Release           
Hit http://security.kali.org kali/updates/main amd64 Packages
Hit http://http.kali.org kali/main Sources
Hit http://security.kali.org kali/updates/contrib amd64 Packages
Hit http://http.kali.org kali/non-free Sources 
Hit http://security.kali.org kali/updates/non-free amd64 Packages
Hit http://http.kali.org kali/contrib Sources  
Hit http://security.kali.org kali/updates/main i386 Packages
Hit http://http.kali.org kali/main amd64 Packages
Hit http://security.kali.org kali/updates/contrib i386 Packages
Hit http://http.kali.org kali/non-free amd64 Packages
Hit http://security.kali.org kali/updates/non-free i386 Packages
Hit http://http.kali.org kali/contrib amd64 Packages
Hit http://http.kali.org kali/main i386 Packages
Hit http://http.kali.org kali/non-free i386 Packages
Hit http://http.kali.org kali/contrib i386 Packages
Ign http://security.kali.org kali/updates/contrib Translation-en_US
Ign http://security.kali.org kali/updates/contrib Translation-en
Ign http://security.kali.org kali/updates/main Translation-en_US
Ign http://security.kali.org kali/updates/main Translation-en
Ign http://security.kali.org kali/updates/non-free Translation-en_US
Ign http://security.kali.org kali/updates/non-free Translation-en
Ign http://http.kali.org kali/contrib Translation-en_US
Ign http://http.kali.org kali/contrib Translation-en
Ign http://http.kali.org kali/main Translation-en_US
Ign http://http.kali.org kali/main Translation-en
Ign http://http.kali.org kali/non-free Translation-en_US
Ign http://http.kali.org kali/non-free Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-ralink is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.


```

Why is it behaving this way???

---

### Post by chili555 on 2013-12-06
> **disco22522 said:**
> 

Why is it behaving this way???Because firmware-ralink is not a Kali package; it's a Debian package. Installing the firmware is useless without the driver anyway.

What are we doing here; the internal or the USB? I really am too old to run off in twelve directions at once.

---

### Post by Iowan on 2013-12-06
Threads merged. 
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.

---

### Post by disco22522 on 2013-12-06
Sorry, Internal. Realtek 8723.

---

### Post by chili555 on 2013-12-06
I suggest you download this package to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/backports-3.12-1
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8723ae
```Note and post any errors; warnings are OK. If you get a notice about signing, it may safely be ignored.

---

### Post by disco22522 on 2013-12-06
Okay everything ran great except "sudo modprobe rtl8723ae" that command seems to do nothing.. But I rebooted after sudo make install and that did fine.

So now what, good sir?

---

### Post by chili555 on 2013-12-06
> **disco22522 said:**
> Okay everything ran great except "sudo modprobe rtl8723ae" that command seems to do nothing.. But I rebooted after sudo make install and that did fine.

So now what, good sir?Now let's do some diagnostics:```
lsmod | grep rtl
dmesg | grep rtl
iwconfig
```Please be sure the USB is safely in your shirt pocket so we only have one wireless device to troubleshoot.

---

### Post by disco22522 on 2013-12-06
```
root@kali:~# lsmod | grep rtl
rtl8723ae             131529  0 
rtl_pci                30318  1 rtl8723ae
rtlwifi                66948  2 rtl_pci,rtl8723ae
mac80211              402780  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              384270  2 mac80211,rtlwifi
compat                 17227  4 cfg80211,mac80211,rtlwifi,rtl8723ae
root@kali:~# dmesg | grep rtl
[    7.210302] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    7.251727] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    7.251957] rtlwifi: wireless switch is on
[   11.897159] r8169 0000:04:00.2: firmware: agent loaded rtl_nic/rtl8411-1.fw into memory
[ 4217.987768] (NULL device *): firmware: agent loaded rtlwifi/rtl8723fw_B.bin into memory
[ 4219.744815] rtlwifi: wireless switch is on
root@kali:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on


```


WOAH wlan0 APPEARS! WE DID SOMETHING!!!!!!! PROGRESSS!!! MY GOD!

---

### Post by chili555 on 2013-12-06
> **disco22522 said:**
> WOAH wlan0 APPEARS! WE DID SOMETHING!!!!!!! PROGRESSS!!! MY GOD!Does it scan?```
sudo iwlist wlan0 scan
```What does this tell us?```
rfkill list all
```

---

### Post by disco22522 on 2013-12-06
```
root@kali:~# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

root@kali:~# rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@kali:~# 


```

---

### Post by chili555 on 2013-12-06
> Hard blocked: yesIn this context, 'hard' means hardware; that is, a hardware switch or key combination, Fn+F4 for example. Flip the switch and you'll be all set.

---

### Post by disco22522 on 2013-12-06
Thank you so much Chili555, I'd kiss you. 

I've actually am a secret follower, as I've read many of your posts lurking..

Seriously, thank you very much I really do appreciate the help, so much!

---

### Post by chili555 on 2013-12-06
I'm glad it's working! When you install a later kernel version, you will need to recompile the driver after you reboot into the later kernel:```
cd Desktop/backports-3.12-1
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8723ae
```Please retain the files and these instructions for that time.

Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Have fun!

---

### Post by disco22522 on 2013-12-06
Actually - one more thing - WICD is not obtaining an IP address and thus not connecting to the network. Any ideas? 

Fixed - Don't use WICD.

---

