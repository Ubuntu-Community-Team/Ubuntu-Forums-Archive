---
title: "Bluetooth on Ubuntu 14.04 works inconsistently"
date: 2016-06-26
forum: Networking &amp; Wireless
---

### Post by duce_85 on 2016-06-26
```
~$ rfkill list 0: phy0: Wireless LAN Soft blocked: no Hard blocked: no
```
I have a lenovo T60. It seemed bluetooth would only work in certain kernels on certain days and sometimes it would not at all. In system settings, The Bluetooth is disabled by default and I cannot change it. It does not even recognize bluetooth at all. And I keep banging my head against the wall with all the suggestions from using Blueman to Bluesz and nothing seems to work.. And the odd thing is it could start back working at anywhere from next startup to a month from now. 

```
:~$ rfkill list 
0: phy0: Wireless LAN Soft blocked: no 
Hard blocked: no

 :~$ lspci -knn | grep Net -A2; lsusb

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation Device [8086:1010]
    Kernel driver i use: iwl3945
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1130:1704 Tenx Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by jeremy31 on 2016-06-26
I think you have most people stumped on this one as I would expect to see an Intel device in the lsusb results for it to have bluetooth capabilities unless it is a USB dongle that has port problems

---

### Post by him610 on 2016-06-27
@Jeremy31, 
FWIW, I have two different intel wireless/bluetooth cards in separate laptops. They will not show up in the results of *lsusb* as they are not on a USB bus. 
One of the bluetooth devices works (the older one), the newer one does not, both are on LSB 14.04 - go figure. 

I seldom use bluetooth, but the post by duce_85 piqued my interest. I will spend some more time trying to understand why one works and the other doesn't, and maybe, we can figure something out. :)

Added
## The one that works - 
Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver: iwl4965 
Cub Linux Kernel: 4.2.0-34-generic x86_64 (64 bit) Desktop: Openbox 3.5.2 Distro: Ubuntu 14.04 trusty

```
$ lsmod | grep blue
bluetooth             512000  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel
```

Uses Blueman Device Manager 1.23

So far I have paired/connected a Sansui HM1700 headset, Altec Lansing H20 speaker, and MotoX XT1058 phone


## The one that does NOT work -
Intel Centrino Advanced-N 6235 driver: iwlwifi 
Kernel: 3.13.0-91-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty


```
$ lsmod | grep blue
bluetooth             391136  11 bnep,btusb,rfcomm 
``` 
Note: btbcm, btintel are missing. I loaded btusb from terminal using* sudo apt*.  Not available to install - btbcm, btintel 

Blueman Manager 2.0.1(?)

# Don't know how to fix it, but will post updates as progress, or lack of progress, is made.

---

### Post by duce_85 on 2016-07-02
I am thinking its a Lenovo issue, most likely in the Bios. because I am not the only one with this issue and most of them go unsolved.

> **him610 said:**
> @Jeremy31, 
FWIW, I have two different intel wireless/bluetooth cards in separate laptops. They will not show up in the results of *lsusb* as they are not on a USB bus. 
One of the bluetooth devices works (the older one), the newer one does not, both are on LSB 14.04 - go figure. 

I seldom use bluetooth, but the post by duce_85 piqued my interest. I will spend some more time trying to understand why one works and the other doesn't, and maybe, we can figure something out. :)

Added
## The one that works - 
Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver: iwl4965 
Cub Linux Kernel: 4.2.0-34-generic x86_64 (64 bit) Desktop: Openbox 3.5.2 Distro: Ubuntu 14.04 trusty

```
$ lsmod | grep blue
bluetooth             512000  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel
```

Uses Blueman Device Manager 1.23

So far I have paired/connected a Sansui HM1700 headset, Altec Lansing H20 speaker, and MotoX XT1058 phone


## The one that does NOT work -
Intel Centrino Advanced-N 6235 driver: iwlwifi 
Kernel: 3.13.0-91-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty


```
$ lsmod | grep blue
bluetooth             391136  11 bnep,btusb,rfcomm 
``` 
Note: btbcm, btintel are missing. I loaded btusb from terminal using* sudo apt*.  Not available to install - btbcm, btintel 

Blueman Manager 2.0.1(?)

# Don't know how to fix it, but will post updates as progress, or lack of progress, is made.
This is what happens when I put it in.. and on the Bios bluetooth is enabled
charles@charles-ThinkPad-T60:~$ lsmod | grep blue
charles@charles-ThinkPad-T60:~$

---

