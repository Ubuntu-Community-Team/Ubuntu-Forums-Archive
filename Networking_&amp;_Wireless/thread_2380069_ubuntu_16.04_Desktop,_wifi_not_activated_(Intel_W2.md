---
title: "ubuntu 16.04 Desktop, wifi not activated (Intel W2200 centrio )"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by ekung on 2017-12-12
Dear all:

  a Lenono Ideapad Y580 latop computer,  with dual boot OS ( win 10 & ubuntu 16.04 LTS desktop)
The wifi worked under win 10, while ubuntu 16.04 LTS not.
(  Ubuntu 16.04 LTS Desktop ,  wifi is not activated. ) 


iwconfig : 
  enp2s0  no wireless extension
  lo          no wireless extension

lspci -n:
 03:00.0  0280:  8086:0891 (rev C4)

lspci :
03:00.0   Network controller: Intel Corporation Centrino Wireless-N 2200 ( rev C4)

how to solve it ?  If not, is it possible use a wifi bridge to output RJ45  and cable-connects to the laptop?

Thanks

---

### Post by chili555 on 2017-12-12
Please open a terminal and run these commands. Then post the results:```
rfkill list all
uname -r
modinfo iwlwifi | grep 0891
```

---

### Post by ekung on 2017-12-12
rfkill list all
>    (nothing shown)

uname -r
> 4.13.0-17-generic

modinfo iwlwifi | grep 0891
> libkmod: ERROR ../libkmod/libkmod.c:514 lookup_builtin_file: could not open builtin  file '/lib/modules/4.13.0-17-generic/modules.builtin.bin' 
modinfo:  ERROR module iwlwifi not found

---

### Post by ekung on 2017-12-13
[COLOR=#000000][I] sudo modprobe ipw2200

[/I][/COLOR]*-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 08
       serial: dc:0e:a1:f3:fa:d7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.65.221 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d3600000-d363ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d3501fff

---

### Post by ekung on 2017-12-13
[COLOR=#000000][I]ls -al /lib/firmware | grep ipw 

[/I][/COLOR]-rw-r--r--  1 root root  209190 11&#26376; 10 04:30 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 11&#26376; 10 04:30 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 11&#26376; 10 04:30 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 11&#26376; 10 04:30 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 11&#26376; 10 04:30 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 11&#26376; 10 04:30 ipw2200-sniffer.fw

---

### Post by chili555 on 2017-12-13
> sudo modprobe ipw2200Your wireless device is not the old, old ipw2200 ABG device. It is the much newer 2200N device. It's driver is iwlwifi as shown in the modalias:```
chili@T440p:~$ modinfo iwlwifi | grep 0891
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]0891[/COLOR]sv*sd00004222bc*sc*i*

```The module doesn't load and drive your device because:> > libkmod: ERROR ../libkmod/libkmod.c:514 lookup_builtin_file: could not open builtin file '/lib/modules/4.13.0-17-generic/modules.builtin.bin' 
modinfo: ERROR module iwlwifi not found

There is evidently a flaw or glitch in your install.

Now we could try to find out where the modules.builtin.bin file is and why it's missing or why it lacks the correct permissions, etc., etc., but it is far easier to simply reinstall your current linux-image:

```
sudo apt-get install --reinstall linux-image-`uname -r`
```Reboot and your wireless should hopefully be fixed. 

If not, then:```
sudo apt-get update && sudo apt-get -y dist-upgrade
```Hopefully, it will offer and install a newer (flaw- and glitch-free) kernel version.

Reboot and your wireless should hopefully be fixed.

---

### Post by ekung on 2017-12-13
it still the same 
$iwconfig
lo         no wireless extensions.
enp2s0 no wireless extensions.

---

### Post by chili555 on 2017-12-13
> it still the same Which step did you try? Both? When you did the second step, was a newer kernel version installed? Did you reboot? Is the error the same?```
uname -r
sudo modprobe iwlwifi
```Please try to give us complete details so we have some clues as to what happened so we may help you better.

---

### Post by ekung on 2017-12-18
I do those 2 steps below and reboot. 


sudo apt-get install --reinstall linux-image-`uname -r`
sudo apt-get update && sudo apt-get -y dist-upgrade


I cannot login as a infinite loop does. 

 ( Finally, I try Ubuntu Kylin 17.04 Simplified Chinese ver.  It supports wifi auto startup and all seems OK)

---

