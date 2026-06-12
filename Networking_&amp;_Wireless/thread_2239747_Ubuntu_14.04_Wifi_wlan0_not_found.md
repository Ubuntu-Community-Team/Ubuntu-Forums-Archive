---
title: "Ubuntu 14.04 Wifi wlan0 not found"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by Lingadharini_Viswa on 2014-08-15
Hi,
I upgraded to ubuntu 14.04 recently from 13.10
Wifi was working perfectly in 13.10, now after upgrading,the result of ifconfig is

```
#ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:23:5a:b9:04:9c  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:feb9:49c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1518363 (1.5 MB)  TX bytes:539926 (539.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166410 (166.4 KB)  TX bytes:166410 (166.4 KB)



```

Currently I am using ethernet cable for internet  connection, I am trying to use wifi. 

There used to be a wlan0. I cant find it. 
Help me.

---

### Post by chili555 on 2014-08-15
Tell us more:```
lspci -nn | grep 0280
lsusb
rfkill list all
```Thanks.

---

### Post by Lingadharini_Viswa on 2014-08-16
> **chili555 said:**
> Tell us more:```
lspci -nn | grep 0280
lsusb
rfkill list all
```Thanks.

[FONT=Ubuntu Mono][COLOR=#000000]Output list[/COLOR][/FONT]
```
 ~$lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

~$ lsusb
Bus 002 Device 002: ID 064e:c108 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Lingadharini_Viswa on 2014-08-16
Pls reply fast..

---

### Post by wildmanne39 on 2014-08-16
You need to be patient we are all volunteers here in different time zones, so it may take a while for him to reply.

---

### Post by chili555 on 2014-08-16
With a working ethernet or similar connection:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Reboot and tell us if it's now working.

---

### Post by Lingadharini_Viswa on 2014-08-17
I have installed it. Still doesnt work.

---

### Post by chili555 on 2014-08-17
> **Lingadharini_Viswa said:**
> I have installed it. Still doesnt work.We wonder if the logs hold a clue as to why not. Please run and post:```
rfkill list all
iwconfig
dmesg | grep -e wlan -e b43
```Thanks.

---

### Post by Lingadharini_Viswa on 2014-08-23
> **chili555 said:**
> We wonder if the logs hold a clue as to why not. Please run and post:```
rfkill list all
iwconfig
dmesg | grep -e wlan -e b43
```Thanks.


 rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no




 iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.




dmesg | grep -e wlan -e b43
[    2.563242] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: bab43694c655e6aee9fceadd34ffb05cf4363bc5'

---

### Post by chili555 on 2014-08-23
It looks like b43 didn't load automatically. Please try:```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```The first two may or may not result in errors or 'not found.' That's fine, just continue.

Any improvement?

---

### Post by Lingadharini_Viswa on 2014-08-26
> **chili555 said:**
> It looks like b43 didn't load automatically. Please try:```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```The first two may or may not result in errors or 'not found.' That's fine, just continue.

Any improvement?

$ sudo apt-get purge bcmwl-kernel-source


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,944 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 181285 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic


$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

$sudo modprobe b43


Ran everything. whats next?

---

### Post by Programmer135 on 2014-08-26
chilli555 You sir are a god.... I have a similear issue that I will use your procedure to fix.. thankyou
And to OP good luck, hopefully we get our problems fixxed :3

---

### Post by chili555 on 2014-08-26
> **Lingadharini_Viswa said:**
> Ran everything. whats next?Now does your wireless work? What does this tell us?```
lsmod | grep b43
dmesg | grep b43
```Thanks.

---

### Post by Lingadharini_Viswa on 2014-08-27
> **chili555 said:**
> Now does your wireless work? What does this tell us?```
lsmod | grep b43
dmesg | grep b43
```Thanks.


Thanks, got my wifi up and running.

The previous step worked liked charm. Thanks. 

Thank you so much. :)

):P):P

---

### Post by Treek on 2014-12-12
> **chili555 said:**
> Now does your wireless work? What does this tell us?```
lsmod | grep b43
dmesg | grep b43
```Thanks.

Hi! i have the same problem, and i typed this code (and every previous code posted here by you), but this code didnt show anything, and my problem isnt solved yet.
Can you help me? thanks.

---

### Post by chili555 on 2014-12-13
> **Treek said:**
> Hi! i have the same problem, and i typed this code (and every previous code posted here by you), but this code didnt show anything, and my problem isnt solved yet.
Can you help me? thanks.I'd rather you start your own new thread. Please include:```
lspci -nn | grep 0280
lsusb
rfkill list all
```Thanks.

---

### Post by vlad42 on 2015-08-27
it works! thank you so much!

kind regards
Bert van Riel

---

### Post by dofin on 2015-10-10
Hi,

I've had a similar problem and needed an extra [FONT=courier new]rfkill unblock wlan[/FONT] to get it working.
I've posted the details in [http://ubuntuforums.org/showthread.php?t=2298330](http://ubuntuforums.org/showthread.php?t=2298330)

Thanks for the pointer to rfkill, chili

---

### Post by kenneth20 on 2016-03-02
I will perform steps tonight ( I am at work) but I needed to bookmark this thread. I will let you know how it went

---

### Post by inckka on 2016-08-27
> **chili555 said:**
> It looks like b43 didn't load automatically. Please try:```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```The first two may or may not result in errors or 'not found.' That's fine, just continue.

Any improvement?


This worked like a charm. Thanks a lot for your time for solving this issue.

---

### Post by nikhilbhalwankar on 2017-07-06
> **Lingadharini_Viswa said:**
> $ sudo apt-get purge bcmwl-kernel-source


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,944 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 181285 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic


$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

$sudo modprobe b43


Ran everything. whats next?


I am facing the same problem. I just now visited official ubuntu help page. The additional software drivers tab has detected my hardware and is installing the driver for it. Do check this out.

[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html)

---

### Post by chili555 on 2017-07-06
> **nikhilbhalwankar said:**
> I am facing the same problem. I just now visited official ubuntu help page. The additional software drivers tab has detected my hardware and is installing the driver for it. Do check this out.

[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html)Please see and follow my post #16 above.

---

### Post by wildmanne39 on 2017-07-06
Old thread closed.

---

