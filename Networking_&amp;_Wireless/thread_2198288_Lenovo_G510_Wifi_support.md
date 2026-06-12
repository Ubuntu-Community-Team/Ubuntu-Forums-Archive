---
title: "Lenovo G510 Wifi support ?"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by tankarakesh.38 on 2014-01-08
Hello Ubuntu,
Recently I bought Lenovo g510(4th Gen I3, 4GB RAM,500 GB HDD, 2 GB Graphic Card,Win 8). I wish to install Ubuntu. In case if I install it, will my laptop's wifi works fine ? 
Please help me.

---

### Post by The Spectre on 2014-01-08
The best way to find out is to download Ubuntu and Boot into it using DVD or USB and select Try Ubuntu to see if the WiFi works...

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

[IMG]http://assets.ubuntu.com/sites/ubuntu/647/u/img/download/desktop-install-1.png[/IMG]

---

### Post by praseodym on 2014-01-08
And once tried Ubuntu like this, open a terminal with CTRl+ALT+T and show the output of
```

lspci -nnk | grep -iA2 net
rfkill list
```
Is the laptop using (U)EFI secure boot?

---

### Post by tankarakesh.38 on 2014-01-08
Thanks for your replies,
Till now I didn't install ubuntu. In case if wi-fi supports then only I will install ubuntu. 
Please confirm whether my laptop supports wi-fi in ubuntu.

---

### Post by praseodym on 2014-01-09
With these outputs we can say "yes" (there is no "no" ;) ) Did you try the Live-CD?

---

### Post by tom49 on 2014-01-23
I also just bought a Lenovo G510 (Intel Core i7 4700MQ, 2,4GHz, 4GB RAM,  HYBRID 1TB 5400RPM SSHD(8G), AMD Mars XT8750 (2GB)) and want to install  Ubuntu 12.04 64bit.
Wifi is not working out of the box for my live usb stick.
Ubuntu  recognize that a driver is missing and opens a window "Additional  Drivers" and tells that I have a  broadcom sta wireless driver. Also the  commands from praseodym tell me that I have a broadcom and nothing is  blocked.
Anyway when I click "Activate" to activate the driver I see  short a status bar and than "Sorry, installation of this driver failed".

When  I look at the named logfile (jockey.log) I see an "[FONT=courier new]Error! Bad return  status for module build on kernel: 3.8.0-29-generic (x86_64)[/FONT]". 

```

ERROR (dkms apport): kernel package linux-headers-3.8.0-29-generic is not supported
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs is disabled since running on read-only media
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

2014-01-23 19:26:12,152 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
2014-01-23 19:26:12,152 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2014-01-23 19:26:12,231 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

From there  I got pointed to make.log but I can't interpret what is meant there.
```

DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.8.0-29-generic (x86_64)
Thu Jan 23 19:26:08 UTC 2014
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function 'wl_cfg80211_join_ibss':
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: error: 'struct cfg80211_ibss_params' has no member named 'channel'
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: (near initialization for 'wl_cfg80211_ops.scan') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: (near initialization for 'wl_cfg80211_ops.set_tx_power') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: (near initialization for 'wl_cfg80211_ops.get_tx_power') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function 'wl_update_bss_info':
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: error: 'struct cfg80211_bss' has no member named 'information_elements'
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: error: 'struct cfg80211_bss' has no member named 'len_information_elements'
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'

```

What could I do to get WIFI running?

---

### Post by tom49 on 2014-01-23
Got it solved. I just executed: 
sudo apt-get install bcmwl-kernel-source

I found this in that link: [http://askubuntu.com/questions/334268/ubuntu-13-04-does-not-recognize-wireless-adapter-14e44365](http://askubuntu.com/questions/334268/ubuntu-13-04-does-not-recognize-wireless-adapter-14e44365)

---

### Post by tankarakesh.38 on 2014-02-07
I was stuck at black screen (command mode) where I was asked to log in(command mode only not UI mode) user credentials after successful, I am unable to find out UI. I tried different commands (Searched through AskUbuntu) but till now i didn't find out any solution to my problem. I previously installed ubuntu successfully in my dell. As i bought new [COLOR=#000000]Lenovo g510(4th Gen I3, 4GB RAM,500 GB HDD, 2 GB Graphic Card(Radeon),Win 8), I am unable to install.  While installing wifi drivers on working fine. After successful installation, Only black screen was appearing. I moved with[/COLOR] ubuntu-13.10-desktop-amd64.iso. [COLOR=#000000]Please help me out.[/COLOR]

---

### Post by varunendra on 2014-02-07
Check this thread out to see how to use "nomodeset" and other boot options : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If the "nomodeset" option lets you boot into normal GUI, check "Additional Drivers" program (while being connected to internet via cable) to see if it offers you any proprietary drivers. If yes, install it and reboot.

Your current problem (black screen) is not related to wifi, so if the above suggestion doesn't work for you, try starting a different thread in "Multimedia & Video" or "Hardware" section of the forums to solve that problem first.

Although we can work separately on your wifi issue if the 'nomodeset' option gives you a usable interface.

---

### Post by Scooby-2 on 2014-06-11
> **tom49 said:**
> I also just bought a Lenovo G510 (Intel Core i7 4700MQ, 2,4GHz, 4GB RAM,  HYBRID 1TB 5400RPM SSHD(8G), AMD Mars XT8750 (2GB)) and want to install  Ubuntu 12.04 64bit.
Wifi is not working out of the box for my live usb stick.
Ubuntu  recognize that a driver is missing and opens a window "Additional  Drivers" and tells that I have a  broadcom sta wireless driver. Also the  commands from praseodym tell me that I have a broadcom and nothing is  blocked.
Anyway when I click "Activate" to activate the driver I see  short a status bar and than "Sorry, installation of this driver failed".

When  I look at the named logfile (jockey.log) I see an "[FONT=courier new]Error! Bad return  status for module build on kernel: 3.8.0-29-generic (x86_64)[/FONT]". 

```

ERROR (dkms apport): kernel package linux-headers-3.8.0-29-generic is not supported
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs is disabled since running on read-only media
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

2014-01-23 19:26:12,152 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
2014-01-23 19:26:12,152 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2014-01-23 19:26:12,231 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

From there  I got pointed to make.log but I can't interpret what is meant there.
```

DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.8.0-29-generic (x86_64)
Thu Jan 23 19:26:08 UTC 2014
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function 'wl_cfg80211_join_ibss':
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: error: 'struct cfg80211_ibss_params' has no member named 'channel'
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: (near initialization for 'wl_cfg80211_ops.scan') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: (near initialization for 'wl_cfg80211_ops.set_tx_power') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: (near initialization for 'wl_cfg80211_ops.get_tx_power') [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function 'wl_update_bss_info':
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: error: 'struct cfg80211_bss' has no member named 'information_elements'
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: error: 'struct cfg80211_bss' has no member named 'len_information_elements'
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'

```

What could I do to get WIFI running?

I have the exact same machine as you, WiFi works out of the box. However it looks like your setup thinks the wireless adaptor is a Broadcom - it should be a Qualcomm Atheros. What hardware does it detect? Mine is as follows:

```
lshw -C network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 40:f0:2f:e6:a4:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b9500000-b957ffff memory:9ff00000-9ff0ffff
 *-network
       description: Ethernet interface
       product: QCA8172 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 20:1a:06:99:c3:8d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=10.247.144.51 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:48 memory:b9400000-b943ffff ioport:3000(size=128)


```

I am also running Ubuntu 12.04LTS with kernel 3.11.0-23-generic. Why are you using 3.8.0-29-generic?

---

### Post by varunendra on 2014-06-11
> **Scooby-2 said:**
> I have the exact same machine....I am also running Ubuntu 12.04LTS with kernel 3.11.0-23-generic. Why are you using 3.8.0-29-generic?
They already got it solved -
> **tom49 said:**
> Got it solved. I just executed: 
sudo apt-get install bcmwl-kernel-source

I found this in that link: [http://askubuntu.com/questions/334268/ubuntu-13-04-does-not-recognize-wireless-adapter-14e44365](http://askubuntu.com/questions/334268/ubuntu-13-04-does-not-recognize-wireless-adapter-14e44365)

---

### Post by tom49 on 2014-06-12
Right, I got it solved.

@Scooby: Thanks anyway, this is the output, my wireless is shown as broadcom here.

```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 34:23:87:ea:ad:6f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:b9500000-b9507fff
  *-network
       description: Ethernet interface
       product: QCA8172 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 20:1a:06:93:dc:98
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt

```

Why I used this kernel? No idea just downloaded the 12.04 LTS, meanwhile I installed 13.04 after I crashed my system while trying to get the  3d card running. Also didn'nt work at 13.04. If you have an easy to follow way to get it done, please let me know.

---

### Post by pazuzuthewise on 2014-09-19
I also have a Lenovo G510 with Broadcom wireless chip. I've got it working under Ubuntu 14.04 by installing manually (from the terminal) the bcmwl-kernel-source* package and its prerequisites. They are present on the live iso image (so that they can be installed even without a working internet connection), under the following directories (and this is the order I've installed them in):

<mount point of the live iso image>/pool/main/d/dkms/dkms*.deb


<mount point of the live iso image>/pool/main/f/fakeroot/libfakeroot*.deb


<mount point of the live iso image>/pool/main/f/fakeroot/fakeroot*.deb


<mount point of the live iso image>/pool/restricted/b/bcmwl/bcmwl-kernel-source*.deb

---

### Post by tom49 on 2014-09-20
Hello [**[COLOR=#000000]pazuzuthewise[/COLOR]**]("http://ubuntuforums.org/member.php?u=966221").
I know the forum topic is an other one.
In 14.04 did you got the graphic card running? I tried to get it running on 13.04 and 13.10 but both times crashed my system after trying dozens of commands and different kinds to get it running.

Cheers
Tim

---

### Post by varunendra on 2014-09-23
> **tom49 said:**
> I know the forum topic is an other one.....

That's why you should ask your question in a different thread, in a relevant section (Hardware or Multimedia) with a relevant title, to get proper support. If you don't get satisfactory answers that way, and want some particular user(s) to participate in your thread, you can always choose to PM them to take a look at your thread.

Be aware that not everyone likes to be PM'd for support though.

Oh, and make sure your question is about a supported version, not 13.04 or 13.10, as both have reached their 'End Of Life', means are no more supported. At least have a Live DVD/USB of a supported version (12.04.5 or 14.04.1) ready for the tests, and try to limit your questions to that.

---

