---
title: "Broadcom BCM43228 no WiFi, no ethernet"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by germo969 on 2018-08-08
After sudo apt-get update last week and restart I lost WiFi, tried to fix through Ethernet:
```
sudo apt-get update
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-sources
sudo apt-get install --reinstall linux-headers-generic
``` 

Did not had WiFi when I first installed Xubuntu 16.04 2-years ago, then all I needed was bcmwl-kernel-sources. Now I also lost Ethernet as well, I can see the home network, but it keeps connecting forever, but never connects.

So currently my Xubuntu 16.04 has no internet connection. On dual-boot Windows Ethernet and WiFi works perfectly. I removed bcmwl-kernel-sources and manually built from dpkg with needed dependencies. As other dependencies version were (2.23-0ubuntu10) I used same.

I read these, but could not fix myself:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

```
bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb
libc6-dev_2.23-0ubuntu10_amd64.deb
libc6_2.23-0ubuntu10_amd64.deb
linux-headers-generic_4.4.0.130.136_amd64.deb
``` 

This neither helped. I am a Linux rookie and using Ubuntu is always ongoing use, learn and study project for me. So a fix and hopefully an explanation what is wrong and why would be helpful.
Would appreciate both fixes- WiFi and Ethernet. Will post useful information that should provide the current state of my machine.

***lspci -nnk | grep -e 0200 -e 0280 -A2***
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
            DeviceName:  Onboard LAN
            Subsystem: Dell 82579LM Gigabit Network Connection [1028:0535]
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
            Subsystem: Dell BCM43228 802.11a/b/g/n [1028:0014]
            Kernel modules: bcma
```
**uname -r**
```
4.15.0-29-generic'
```[B]
dpkg --print-architecture [/B]
```
amd64
```

**ifconfig**
```
eno1      Link encap:Ethernet  HWaddr f0:1f:af:42:f1:32  
          inet6 addr: fe80::4606:47b7:5a20:2446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:37337 (37.3 KB)
          Interrupt:20 Memory:f7e00000-f7e20000
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1174704 (1.1 MB)  TX bytes:1174704 (1.1 MB)
```

**iwconfig**
```
eno1      no wireless extensions.
 
lo        no wireless extensions.
```

**sudo lshw -C network**
  ```
*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: f0:1f:af:42:f1:32
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:f7e00000-f7e1ffff memory:f7e39000-f7e39fff ioport:f080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d03fff
```

**/etc/network/interfaces**
```
  GNU nano 2.5.3                      File: /etc/network/interfaces                                                  
 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

**/etc/NetworkManager/NetworkManager.conf**
```
[main]plugins=ifupdown,keyfile,ofono
dns=dnsmasq
 
[ifupdown]
managed=true
```

[B]/etc/modprobe.d/blacklist.conf
[/B] - these should be related to connection and Broadcom

```
#replaced by b43 and ssb.#blacklist bcm43xx
```

---

### Post by jeremy31 on 2018-08-08
What is the result from terminal for ```
mokutil --sb-state 
```

---

### Post by germo969 on 2018-08-08
Failed to read SecureBoot

**Edit**
- working on wireless script

**2nd Edit**
All I am getting back from the wireless script is
```
########## wireless info START ##########
```
I run it in terminal ./wireless-info, sudo or no sudo, output is equally void of info

---

### Post by jeremy31 on 2018-08-08
Download [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb) and get it on your Desktop in Ubuntu, then in terminal
```
cd Desktop
sudo dpkg -i bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb
```
Reboot and see if wifi works

---

### Post by germo969 on 2018-08-08
sudo dpkg -ibcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb
```
(Reading database... 326093 files and directories currently installed.)
Preparing to unpackbcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Removing all DKMSModules
Done.
Unpackingbcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) over(6.30.223.141+bdcom-0ubuntu2) ...
Setting upbcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading newbcmwl-6.30.223.271+bdcom DKMS files...
Building only for4.15.0-29-generic
Building forarchitecture x86_64
Building initialmodule for 4.15.0-29-generic
Done.

wl:
Running moduleversion sanity check.
 - Original module
   - No originalmodule exists within this kernel
 - Installation
   - Installing to/lib/modules/4.15.0-29-generic/updates/dkms/

depmod....

DKMS: installcompleted.
update-initramfs:deferring update (trigger activated)
Processing triggersfor initramfs-tools (0.122ubuntu8.11) ...
update-initramfs:Generating /boot/initrd.img-4.15.0-29-generic
W: Possible missingfirmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missingfirmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915

```

Wifi works now, thank you [COLOR=#000000]jeremy31.[/COLOR] Also if it isn´t too much can you explain what was wrong? I mean I installed ```
[COLOR=#000000][FONT=&amp]bcmwl-kernel-source_6.30.223.**141**+bdcom-0ubuntu**2**_amd64.deb[/FONT][/COLOR]
``` but you send me ```
[COLOR=#000000][FONT=&amp]bcmwl-kernel-source_6.30.223.**271**+bdcom-0ubuntu**4**_amd64.deb[/FONT][/COLOR]
``` which is latest version. Now I see I installed older version, which used to be for 14.04 Trusty. So I should have looked for latest or [16.04 version]("https://packages.ubuntu.com/xenial/admin/bcmwl-kernel-source"). 

Ethernet is still broken -  If possible to offer any solutions I would like to get that fixed as well. Well keep this unresolved for time being.

---

### Post by crisaborn on 2018-08-08
[COLOR=#111111][FONT=Ubuntu]I can't view any wifi networks after upgrading to 16.04 from 14.04. [/FONT][/COLOR]

---

### Post by wildmanne39 on 2018-08-08
Hello crisaborn, please start your own thread instead of asking for help in another users thread.

Thanks

---

### Post by ravensm on 2018-08-08
i dont know if it helps you or not, but i had to manually enter my dns servers. which i got from a working windows os with said internet. once that happened, i was able to surf the net. before that it was kinda connected but wasnt able to access the web

---

