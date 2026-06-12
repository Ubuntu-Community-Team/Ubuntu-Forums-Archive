---
title: "Ubuntu sees wifi network, but dont connect  14.04"
date: 2014-07-07
forum: Networking &amp; Wireless
---

### Post by ellliotcz97 on 2014-07-07
So, my problem is the following: I've just installed Ubuntu 14.04 on my MacBook, and i wanted to play around with it. So i started Firefox and then i recognized, that i have no connection. I tried to connect to my home WIFI network but without any sucess. I've very new to this… and i need some help.

My card is a Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01). Fortunately i have ethernet connection!

I hope you can help me :)

PS:. Sorry for my bad english

---

### Post by chili555 on 2014-07-07
Which driver is being used? From a terminal Ctrl+Alt+t please run and post:```
lsmod | grep -e wl -e brcm -e b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Did you check the sticky? [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by ellliotcz97 on 2014-07-07
> **chili555 said:**
> Which driver is being used? From a terminal Ctrl+Alt+t please run and post:```
lsmod | grep -e wl -e brcm -e b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Did you check the sticky? [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Thanks for your help :) 

Yes, i read the sticky and the problem is that my PCI ID is 14e4:4353 wich according to your chart is a special case. I've tried it, but it didn't work. 

Here's the output from:  lsmod | grep -e wl -e brcm -e b43
```
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl 
```

---

### Post by Bucky Ball on 2014-07-07
According to this page you are after the b43 driver for that card:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29)

There's the instructions for installing it. Looks like you are using the wl driver, which I'm not sure is right. Might be an idea to wait til chili555 confirms before going for it (or take your chances!). The wl driver may need to be blacklisted or removed prior to installing b43 and chili555 knows more of these things ... ;)

---

### Post by ellliotcz97 on 2014-07-07
Thanks for Reply! 

Ok, i'll wait for chili555 :D

---

### Post by Bucky Ball on 2014-07-07
According to that page:

> b43 - Open source driver

    For Chip ID BCM4306 (rev 03), BCM4309, BCM4311, BCM4312, BCM4318, BCM4322, BCM4331, **BCM43224** and BCM43225.

So, I would try - and this won't cause any irreparable damage incidentally, and might get it going - these two commands in a terminal, one after the other, hitting enter between each:

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```

You may need to reboot or wireless may pop up immediately. Any luck?

* Looks like chili555's online. Hopefully they'll jump on here and confirm this procedure. I'd give it a shot while you're waiting (and chili can help sort it out if it doesn't work! ;)).

---

### Post by ellliotcz97 on 2014-07-07
I've run the Code and rebooted the computer, but it didn't work :/

---

### Post by Bucky Ball on 2014-07-07
> **ellliotcz97 said:**
> I've run the Code and rebooted the computer, but it didn't work :/

I neglected to mention: You need to be online with an ethernet cable for this to work. Catch 22. Are you? If not either plug one in (makes things MUCH easier) or:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

You need the b43, not b43 legacy or any of the others.

---

### Post by ellliotcz97 on 2014-07-07
> **Bucky Ball said:**
> I neglected to mention: You need to be online with an ethernet cable for this to work. Catch 22. Are you? If not either plug one in (makes things MUCH easier) or:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

You need the b43, not b43 legacy or any of the others.

Yes, i'm online with an ethernet cable.

---

### Post by Bucky Ball on 2014-07-07
When you say it didn't work, please run those commands again and post exactly what the errors are from the terminal, if any.

---

### Post by ellliotcz97 on 2014-07-07
> **Bucky Ball said:**
> When you say it didn't work, please run those commands again and post exactly what the errors are from the terminal, if any.

```
 elliotcz97@elliot-MacBook-Linux:~$ sudo apt-get update
[sudo] password for elliotcz97: 
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                             
Hit http://archive.canonical.com trusty Release.gpg                        
Hit http://extras.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release
Hit http://extras.ubuntu.com trusty Release    
Ign http://archive.ubuntu.com trusty InRelease  
Hit http://archive.canonical.com trusty/partner Sources
Ign http://archive.ubuntu.com trusty-updates InRelease
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Ign http://archive.ubuntu.com trusty-backports InRelease
Ign http://archive.ubuntu.com trusty-security InRelease
Hit http://archive.ubuntu.com trusty Release.gpg
Hit http://archive.ubuntu.com trusty-updates Release.gpg
Hit http://archive.ubuntu.com trusty-backports Release.gpg
Hit http://archive.ubuntu.com trusty-security Release.gpg
Ign http://archive.canonical.com trusty/partner Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://archive.canonical.com trusty/partner Translation-en
Hit http://archive.ubuntu.com trusty Release   
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.canonical.com trusty/partner Translation-de                 
Ign http://extras.ubuntu.com trusty/main Translation-de              
Hit http://archive.ubuntu.com trusty-updates Release
Hit http://archive.ubuntu.com trusty-backports Release
Hit http://archive.ubuntu.com trusty-security Release
Hit http://archive.ubuntu.com trusty/universe Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/main Sources
Hit http://archive.ubuntu.com trusty/main amd64 Packages
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/main Translation-de
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-de
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-de
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-de
Hit http://archive.ubuntu.com trusty-updates/universe Sources
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://archive.ubuntu.com trusty-updates/restricted Sources
Hit http://archive.ubuntu.com trusty-updates/main Sources
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-backports/main Sources
Hit http://archive.ubuntu.com trusty-backports/restricted Sources
Hit http://archive.ubuntu.com trusty-backports/universe Sources
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Sources
Hit http://archive.ubuntu.com trusty-security/multiverse Sources
Hit http://archive.ubuntu.com trusty-security/restricted Sources
Hit http://archive.ubuntu.com trusty-security/main Sources
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/main Translation-de
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-de
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-de
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/universe Translation-de
Ign http://archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://archive.ubuntu.com trusty-backports/main Translation-de
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-de
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-de
Ign http://archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-backports/universe Translation-de
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US
Ign http://archive.ubuntu.com trusty-security/main Translation-de
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-de
Ign http://archive.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty-security/restricted Translation-de
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-security/universe Translation-de
Reading package lists... Done
elliotcz97@elliot-MacBook-Linux:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libcapi20-3:i386 libexif12:i386 libgd3:i386
  libgif4:i386 libglu1-mesa:i386 libgphoto2-6:i386 libgphoto2-port10:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libieee1284-3:i386
  libkrb5-26-heimdal:i386 liblcms2-2:i386 libldap-2.4-2:i386 libltdl7:i386
  libmpg123-0:i386 libosmesa6:i386 libp11-kit-gnome-keyring:i386
  libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvpx1:i386 libwind0-heimdal:i386 libxcomposite1:i386 libxcursor1:i386
  libxinerama1:i386 libxpm4:i386 libxrandr2:i386 linux-image-generic
  ocl-icd-libopencl1:i386 p11-kit-modules:i386 wine-gecko2.21:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
elliotcz97@elliot-MacBook-Linux:~$  
```

---

### Post by Bucky Ball on 2014-07-07
Try:

```
sudo modprobe b43
sudo echo b43 >> /etc/modules 
```

Reboot. Incidentally, pull the ethernet cable before reboot. Sometimes that prevents the wireless coming up.
___

The b43 driver seems to be installed. If the instructions above don't get the wireless up, try this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

... and add to the end of that file:

```
blacklist wl
```

Reboot.
___

If *that* doesn't work, could you please post the output of:

```
sudo lshw -C network
```

That will show us whether the card is using b43 or not.
___

Off the point here, but I think about now it would be a good idea to run these commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That will clean things up and bring all installed software up to date.

---

### Post by ellliotcz97 on 2014-07-07
> **Bucky Ball said:**
> Try:

```
sudo modprobe b43
```

Off the point here, but I think about now it would be a good idea to run these commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That will clean things up and bring all installed software up to date.

The b43 driver seems to be installed. After you've done the above, could you please post the output of:

```
sudo lshw -C network
```

That will show us whether the card is using it or not. You did reboot after installing the driver last time? Could be the wl driver is getting in the way and either needs to be removed or blacklisted.

ok, Done it! ```
 elliotcz97@elliot-MacBook-Linux:~$ sudo modprobe b43
[sudo] password for elliotcz97: 
elliotcz97@elliot-MacBook-Linux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: d4:9a:20:fa:77:ca
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.121 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 memory:d3386000-d3386fff ioport:21e0(size=8) memory:d3389000-d33890ff memory:d3389300-d338930f
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:d3100000-d3103fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 34:15:9e:8f:b7:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-30-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11abgn
elliotcz97@elliot-MacBook-Linux:~$ 


```

---

### Post by chili555 on 2014-07-07
Did you purge the *wl* driver?```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -r wl
dmesg | grep -e b43 -e brcm
```

---

### Post by ellliotcz97 on 2014-07-07
Thank you for helping me. It means a lot! :)

I ran the codes, but it does not work.

```


[sudo] password for elliotcz97: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: d4:9a:20:fa:77:ca
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.121 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 memory:d3386000-d3386fff ioport:21e0(size=8) memory:d3389000-d33890ff memory:d3389300-d338930f
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:d3100000-d3103fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 34:15:9e:8f:b7:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-30-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by ellliotcz97 on 2014-07-07
> **chili555 said:**
> Did you purge the *wl* driver?```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -r wl
dmesg | grep -e b43 -e brcm
```

Here's the output: ```
 sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 213435 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-30-generic
elliotcz97@elliot-MacBook-Linux:~$ sudo modprobe -r wl
modprobe: FATAL: Module wl not found.
elliotcz97@elliot-MacBook-Linux:~$ dmesg | grep -e b43 -e brcm
[   17.870155] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.870222] b43: probe of bcma0:0 failed with error -524
[   18.199027] brcmsmac bcma0:0: mfg 4bf core 812 rev 23 class 0 irq 19
[   21.535641] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   21.535705] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   39.948115] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   39.948120] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   66.323575] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   66.323582] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   95.909501] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   95.909512] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  128.027272] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  128.027291] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  131.493739] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  131.493751] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  177.306442] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  177.306450] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
elliotcz97@elliot-MacBook-Linux:~$ 

```

---

### Post by chili555 on 2014-07-07
> Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1That's what I love about dmesg! It often tells us what's wrong and then what to do to fix it. Let's hope it's accurate in this case. This will be a temporary fix; if it works we'll write a quick file to make it permanent.```
sudo modprobe -r brcmsmac
sudo modprobe -r b43
sudo modprobe b43 allhwsupport=1 
sudo modprobe brcmsmac
```How about now?

---

### Post by ellliotcz97 on 2014-07-07
Sadly it didn't work :/ ```
[sudo] password for elliotcz97: 
root@elliot-MacBook-Linux:~# sudo modprobe -r brcmsmac
root@elliot-MacBook-Linux:~# sudo modprobe -r b43
root@elliot-MacBook-Linux:~# sudo modprobe b43 allhwsupport=1 
root@elliot-MacBook-Linux:~# sudo modprobe brcmsmac
root@elliot-MacBook-Linux:~# 



```

---

### Post by chili555 on 2014-07-07
What does this tell us?```
dmesg | grep b43
iwconfig
sudo iwlist wlan0 scan
```I will be away for a couple of hours; see you later.

---

