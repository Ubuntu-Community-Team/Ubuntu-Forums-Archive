---
title: "b43 offline install"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by dracule on 2008-04-23
is there a way to install the b43 driver without internet? I dont have access to wired, but i can boot into windows and download any necessary drivers.

When I went to enable it on 8.04, it didnt give me any options of selecting my wl_something.o file, like it did on 7.10

No wizard at all came up on 8.04, except when i installed it (off the cd) it gave me an option of "fetch and extract".

So is there anyway to install it offline so i can configure the rest of my system?

---

### Post by dstew on 2008-04-23
I think the driver might already be installed. What is the output of```
ifconfig
iwconfig
sudo lshw -C network
```?

---

### Post by Patsoe on 2008-04-23
dstew: the driver is already installed but the firmware isn't.

You could download the b43-fwcutter deb package and bring it to your machine over USB (actually you might want to see if it isn't on the install disc, it probably is?). After installing that deb package, the command line instruction should be 'sudo b43-fwcutter -w "/lib/firmware" wl_something.o' (but check the man page to be sure!).

See also [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43)

---

### Post by dracule on 2008-04-23
ok, here is an update of everything:

```
sudo b43-fwcutter  -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

[sudo] password for phun: 

This file is recognised as:
  
ID         :  FW10
  
filename   :  wl_apsta.o
  
version    :  295.14
 
 MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3

Extracting b43legacy/ucode2.fw

Extracting b43legacy/ucode4.fw

Extracting b43legacy/ucode5.fw

Extracting b43legacy/ucode11.fw

Extracting b43legacy/pcm4.fw

Extracting b43legacy/pcm5.fw

Extracting b43legacy/a0g0bsinitvals2.fw

Extracting b43legacy/b0g0bsinitvals5.fw

Extracting b43legacy/a0g0initvals5.fw


Extracting b43legacy/a0g1bsinitvals5.fw

Extracting b43legacy/a0g0initvals2.fw

Extracting b43legacy/a0g1initvals5.fw

Extracting b43legacy/b0g0bsinitvals2.fw

Extracting b43legacy/b0g0initvals5.fw

Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw



```


I then modprobed b43
and restarted, and did these commands:


```
phun@ubuntu:~$ sudo lshw -C network
  
*-network               
       
description: Network controller
       
product: BCM94311MCG wlan mini-PCI
       
vendor: Broadcom Corporation
       
physical id: 0
       
bus info: pci@0000:01:00.0
       
version: 01
       
width: 32 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress bus_master cap_list
       
configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       

description: Wireless interface
       
physical id: 1
       
logical name: wlan0
       
serial: 00:14:a5:bd:4f:001
       
capabilities: ethernet physical wireless
       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g




```

```
phun@ubuntu:~$ ifconfig

eth0      
Link encap:Ethernet  
HWaddr 00:1d:72:423:ab:2132  
          
UP BROADCAST MULTICAST  MTU:1500  
Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:20 

lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
          
RX bytes:8400 (8.2 KB)  TX bytes:8400 (8.2 KB)



```
```
phun@ubuntu:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.

wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




```

still nothing...

[[IMG]http://img229.imageshack.us/img229/6388/screenshothardwaredriveld6.png[/IMG]](http://imageshack.us)


[[IMG]http://img116.imageshack.us/img116/7587/screenshotnetworksettinyc8.png[/IMG]](http://imageshack.us)

nothing shows up under wireless connections, when i click the network icon by the time either.

---

### Post by Patsoe on 2008-04-23
Are you sure the firmware has to go into that kernel-version-subdir?
On my system I found the b43 driver outputting errors on tty1 (get there via ctrl-alt-f1, apologies if I saying trivial things). It said it couldn't find the firmware, and it could finally find it when I put it straight in /lib/firmware (so you get a /lib/firmware/b43 directory).

(off-topic: in the end I still opted for the ndiswrapper driver)

---

### Post by dracule on 2008-04-23
> **Patsoe said:**
> Are you sure the firmware has to go into that kernel-version-subdir?
On my system I found the b43 driver outputting errors on tty1 (get there via ctrl-alt-f1, apologies if I saying trivial things). It said it couldn't find the firmware, and it could finally find it when I put it straight in /lib/firmware (so you get a /lib/firmware/b43 directory).

(off-topic: in the end I still opted for the ndiswrapper driver)

I tried ndiswrapper, but my my wireless disappeared altogether from the network menu, but ill try what you said above.

---

### Post by dracule on 2008-04-23
Update:
I extracted the firmware to my desktop, and then simply copied them into the directory. 

Now I dont get the "cannot find firware error" in tty1 like before

but there is still no wireless networks listed...

[[IMG]http://img74.imageshack.us/img74/7076/screenshotb43filebrowseeb5.png[/IMG]](http://imageshack.us)

[[IMG]http://img231.imageshack.us/img231/4880/screenshotvk4.png[/IMG]](http://imageshack.us)

---

### Post by Ayuthia on 2008-04-23
I think that Patsoe is correct about the location of the b43* folders in /lib/firmware.  Mine are not located in the kernel directories but right in /lib/firmware.  The other item is that it looks like the b43 drivers also need broadcom-wl-4.80.53.0.tar.bz2.  You should be able to get it from here: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

You will then need to do the following:
```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

```

This information was taken from /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh if you downloaded the b43-fwcutter from the hardy repositories.

---

### Post by Patsoe on 2008-04-23
Hm, well if it detects the firmware now, I wouldn't know what else to try...

Hate to come up with the ndiswrapper stuff again, since you've been through all that already, but did you see [this thread]("http://ubuntuforums.org/showthread.php?t=734003")?

---

### Post by dracule on 2008-04-23
> **Ayuthia said:**
> I think that Patsoe is correct about the location of the b43* folders in /lib/firmware.  Mine are not located in the kernel directories but right in /lib/firmware.  The other item is that it looks like the b43 drivers also need broadcom-wl-4.80.53.0.tar.bz2.  You should be able to get it from here: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

You will then need to do the following:
```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

```

This information was taken from /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh if you downloaded the b43-fwcutter from the hardy repositories.

Horray!

Im now posting this from Ubuntu thanks to you!

Problem solved. :guitar:

---

### Post by wazzoo on 2009-04-01
> **Ayuthia said:**
> I think that Patsoe is correct about the location of the b43* folders in /lib/firmware.  Mine are not located in the kernel directories but right in /lib/firmware.  The other item is that it looks like the b43 drivers also need broadcom-wl-4.80.53.0.tar.bz2.  You should be able to get it from here: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

You will then need to do the following:
```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

```

This information was taken from /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh if you downloaded the b43-fwcutter from the hardy repositories.

I joined these forums just to say thank you for this advice :D this works perfectly on my Amilo A1667G where everything else failed. Cheers!

---

### Post by mike892 on 2009-09-22
I just spent 4 or 5 hours trying to get wireless to work. Couldn't do it because my wired ethernet was broken. You are awesome man, i tried using opensuse and ubuntu. glad to see ubuntu worked thanks man.

---

### Post by yoshiki2 on 2009-11-21
I installed the deb package from this website [http://packages.ubuntu.com/karmic/i386/b43-fwcutter/download](http://packages.ubuntu.com/karmic/i386/b43-fwcutter/download), but it doesn't create any b43 folder.. Also when i try to copy the broadcom-wl-4.80.53.. into lib/firmware it doesn't allow me to copy anything.. any ideas?

> **Ayuthia said:**
> I think that Patsoe is correct about the location of the b43* folders in /lib/firmware.  Mine are not located in the kernel directories but right in /lib/firmware.  The other item is that it looks like the b43 drivers also need broadcom-wl-4.80.53.0.tar.bz2.  You should be able to get it from here: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

You will then need to do the following:
```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

```This information was taken from /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh if you downloaded the b43-fwcutter from the hardy repositories.

---

### Post by ivotkl on 2011-01-23
Comands entered:
ifconfig
iwconfig
sudo lshw -C network



Output shows:
root@ivan-lnv:/home/ivan# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

root@ivan-lnv:/home/ivan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@ivan-lnv:/home/ivan# sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f4500000-f4503fff
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:c8:ba:d7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb v3.04 latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:17 memory:f4600000-f460ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:2b:9c:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg





Do I need to use broadcom-wl-4.150.10.5.tar.bz2, broadcom-wl-4.80.53.0.tar.bz2, both or none (meaning a different one)? How do I do that?

Oh and BTW, I have no Eth0 after upgrading the system, not even booting up with the previous kernel, but I do have wirless and wired connection with XP.
I'm running Ubuntu Studio with Windows XP dual boot. Lenovo G550 with 4GB RAM. Model name is 2958J6Y.

Thank you so much for the help.
Greets.

---

