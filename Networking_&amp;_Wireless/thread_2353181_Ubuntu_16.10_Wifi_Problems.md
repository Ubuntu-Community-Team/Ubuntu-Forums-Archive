---
title: "Ubuntu 16.10 Wifi Problems"
date: 2017-02-19
forum: Networking &amp; Wireless
---

### Post by testclone on 2017-02-19
My laptop can connect to my home wifi, but when it is connected it might as well be not, packet-loss is always 60%-95%. My laptop can connect to other networks perfectly fine without the  aforementioned packet-loss.  I've been using the same kernel for a few months (without patches or updates) and I've never had a wifi problem. When I connect to my home internet instead with a wired connection it works fine as well (no packet-loss).


[LIST]
[*]I've tried loading into the maintained Ubuntu 16.10 kernel (4.8) but that doesn't work either.
[*]I've updated my laptop and fixed broken packages but that didn't fix the problem either.
[*]I've tried forgetting then re-entering my network but that doesn't work. (I have connected to the WiFi before without any packet loss; this started happening a few days ago).
[*]I also tried it with a Ubuntu 16.04 live disk (not 16.04.1 or with any updates) and it didn't work either still 90% packet loss.
[*]My mac and phone can connect to wifi without any problems.
[/LIST]
 
Distro: Ubuntu 16.10
Kenrel: 4.9 Generic & 4.8 Ubuntu maintained (I've also tried the rc8 4.10 kernel but the problem remained)
Wifi Card: RTL8188EE Wireless Network Adapter
Laptop: Toshiba Satellite C55-A
Modem Model: TG862G/CT

```
Iwconfig
``` output says I'm connected to my home wifi (still packet-loss) but says nothing for lo or enpsl0.

```
dmesg |grep -i firmware
```

```
[    0.503304] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.537191] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    2.505940] [drm] Found UVD firmware Version: 1.64 Family ID: 9
[    2.507986] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[   39.289438] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin

```
(this leads me to believe it might be a driver problem) (this also didn't happen with 4.10 kernel but the problem remained)

```
nmcli dev  
```

```
DEVICE  TYPE      STATE      CONNECTION         
enp1s0  ethernet  connected  Wired connection 1 
wlp5s0  wifi      connected  Auto WiFi  
lo      loopback  unmanaged  --

```
Recently installed or updated software:
```

Start-Date: 2017-02-16  07:04:43
Commandline: apt install oracle-java8-installer
Requested-By: gavin16 (1000)
Install: oracle-java8-set-default:amd64 (8u121-1~webupd8~0, automatic), oracle-java8-installer:amd64 (8u121-1~webupd8~0)
End-Date: 2017-02-16  07:08:05

Start-Date: 2017-02-16  07:12:00
Commandline: apt upgrade
Upgrade: libssh2-1:amd64 (1.7.0-1, 1.7.0-1ubuntu0.1), libgles2-mesa:amd64 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgles1-mesa:amd64 (17.1~git
1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), kpartx:amd64 (0.5.0+git1.656f8865-5ubuntu7.1, 0.5.0+git1.656f8865-5ubuntu7.2), libglapi-mesa:amd64 (17.1~git1702
141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libglapi-mesa:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libxatracker2:amd64 (17.1~git17
02141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), flashplugin-installer:amd64 (24.0.0.194ubuntu0.16.10.1, 24.0.0.221ubuntu0.16.10.1), libegl1-mesa:amd64 (17.1~git17
02141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libegl1-mesa:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), kpartx-boot:amd64 (0.5.0+git1.
656f8865-5ubuntu7.1, 0.5.0+git1.656f8865-5ubuntu7.2), libgbm1:amd64 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgbm1:i386 (17.1~git1702141930.92
4a8c~gd~y, 17.1~git1702160730.03f498~gd~y), gnome-calculator:amd64 (1:3.22.0-1ubuntu1, 1:3.22.2-1ubuntu0.1), libwayland-egl1-mesa:amd64 (17.1~git1702141930.924a8c~gd~y, 
17.1~git1702160730.03f498~gd~y), libwayland-egl1-mesa:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgl1-mesa-dri:amd64 (17.1~git1702141930.92
4a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgl1-mesa-dri:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libosmesa6:amd64 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libosmesa6:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgl1-mesa-glx:amd64 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgl1-mesa-glx:i386 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y), libgc1c2:amd64 (1:7.4.2-8, 1:7.4.2-8ubuntu0.1), mesa-vdpau-drivers:amd64 (17.1~git1702141930.924a8c~gd~y, 17.1~git1702160730.03f498~gd~y)
End-Date: 2017-02-16  07:14:01

Start-Date: 2017-02-18  22:21:00
Commandline: apt upgrade
Upgrade: libdns-export162:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libgles2-mesa:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libisccfg140:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libcups2:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libcups2:i386 (2.2.0-2, 2.2.0-2ubuntu0.1), unity-control-center-faces:amd64 (15.04.0+16.10.20161003.1-0ubuntu2, 15.04.0+16.10.20170214-0ubuntu1), gir1.2-gtk-3.0:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), libpci-dev:amd64 (1:3.3.1-1.1ubuntu4, 1:3.3.1-1.1ubuntu4.1), libgles1-mesa:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libgtk-3-common:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), libgtk-3-0:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), libgtk-3-0:i386 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), libglapi-mesa:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libglapi-mesa:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), snapd:amd64 (2.22.2+16.10, 2.22.3+16.10), bind9-host:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), snap-confine:amd64 (2.22.2+16.10, 2.22.3+16.10), dnsutils:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), gnome-software:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2, 3.20.1+git20170208.0.a34b091-0ubuntu1), libxatracker2:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libisc160:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libegl1-mesa:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libegl1-mesa:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), cups-server-common:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), cups-common:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), unity-control-center:amd64 (15.04.0+16.10.20161003.1-0ubuntu2, 15.04.0+16.10.20170214-0ubuntu1), libgbm1:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libgbm1:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), python-crypto:amd64 (2.6.1-6build1, 2.6.1-6ubuntu0.16.10.3), libisc-export160:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libgtk-3-bin:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), cups-ppdc:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), ubuntu-software:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2, 3.20.1+git20170208.0.a34b091-0ubuntu1), libcupsmime1:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), xserver-xorg-video-intel:amd64 (2:2.99.917+git1702110733.93942b~gd~y, 2:2.99.917+git1702161933.860c36~gd~y), libwayland-egl1-mesa:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libwayland-egl1-mesa:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), liblwres141:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libgail-3-0:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), libwebkit2gtk-4.0-37:amd64 (2.14.3-0ubuntu0.16.10.1, 2.14.5-0ubuntu0.16.10.1), libgl1-mesa-dri:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libgl1-mesa-dri:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libosmesa6:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libosmesa6:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libdns162:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), libgl1-mesa-glx:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libgl1-mesa-glx:i386 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), libunity-control-center1:amd64 (15.04.0+16.10.20161003.1-0ubuntu2, 15.04.0+16.10.20170214-0ubuntu1), python3-crypto:amd64 (2.6.1-6build1, 2.6.1-6ubuntu0.16.10.3), pciutils:amd64 (1:3.3.1-1.1ubuntu4, 1:3.3.1-1.1ubuntu4.1), libcupsppdc1:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), gir1.2-webkit2-4.0:amd64 (2.14.3-0ubuntu0.16.10.1, 2.14.5-0ubuntu0.16.10.1), libisccc140:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), cups-bsd:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), gtk-update-icon-cache:amd64 (3.20.9-1ubuntu2, 3.20.9-1ubuntu2.1), mesa-vdpau-drivers:amd64 (17.1~git1702160730.03f498~gd~y, 17.1~git1702180730.ad019b~gd~y), cups-core-drivers:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libbind9-140:amd64 (1:9.10.3.dfsg.P4-10.1ubuntu1.2, 1:9.10.3.dfsg.P4-10.1ubuntu1.3), cups-daemon:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libpci3:amd64 (1:3.3.1-1.1ubuntu4, 1:3.3.1-1.1ubuntu4.1), libcupsimage2:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), cups:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libcupscgi1:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), gnome-software-common:amd64 (3.20.1+git20161013.0.d77d6cf-0ubuntu2, 3.20.1+git20170208.0.a34b091-0ubuntu1), cups-client:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libjavascriptcoregtk-4.0-18:amd64 (2.14.3-0ubuntu0.16.10.1, 2.14.5-0ubuntu0.16.10.1), libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.3-0ubuntu0.16.10.1, 2.14.5-0ubuntu0.16.10.1), gir1.2-javascriptcoregtk-4.0:amd64 (2.14.3-0ubuntu0.16.10.1, 2.14.5-0ubuntu0.16.10.1)
End-Date: 2017-02-18  22:23:59
```

---

### Post by wildmanne39 on 2017-02-21
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

Please edit your post and break up that big block if text so it will be easier to read.
Thanks

---

### Post by testclone on 2017-02-22
I tried to make the post more readable; here's the script also.

---

### Post by wildmanne39 on 2017-02-23
First go into your router and take out the special characters and spaces in your network name, then change the channel in the router to 1 because there are several other networks using 6 and 11 then save the settings.

You have network manager and wicd installed you can only have one or the other or they conflict.

Go into network manager and change the settings to match the screenshots, it will increase speed and stability.

Now we need to set the correct country code for your router please do:
```
sudo iw reg set MX
sudo sed -i 's/^\(REGDOMAIN\)=.*$/&=MX/' /etc/default/crda
```
Reboot
Thanks

---

