---
title: "Trying to get Ralink RT2800usb to work"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by menth1979 on 2014-08-08
I just bought a similar adapter 0df6:0078. Where do you got the information about the chipset?

After some failure, I tried to get it to work with ndiswrapper. I installed the drivers on wine and I found out this file, RT2870.inf, so I supposed that the chipset is some kind of RT2800 flavour. Anyway, modprobing rt2800usb isn't working. Echoing the id and the vendor to /sys/usb/drivers/rt2800usb/new_id, as I found on many guides, doesn't work. Ndiswrapping loads the driver, finds the adapter but fails when modprobing ndiswrapper module with some obscure errors. Tried on Win XP, works flawlessly.

Also, the chipset firmware, with lsusb -v, is labeled "Ralink" not "Realtek".

---

### Post by coffeecat on 2014-08-08
The thread you posted to was about a Realtek chipset so it was not relevant to your situation with a Ralink. I've moved your post to its own thread and given it a suitable title.

These days, ndiswrapper is a last resort of desperation in most cases. I would hope a problem with a Ralink card would be easier to fix. I suggest you post the output of the wireless script as in this sticky post below and someone with Ralink experience may be able to help you.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by menth1979 on 2014-08-08
Ok, now I'm getting completely confused.
I always thought that the vendor id and product id were an unambiguous key for the chipset. Is it possible that my 0df6:0078 is a Ralink 2800 while yours is a Realtek?

---

### Post by coffeecat on 2014-08-08
> **menth1979 said:**
> Ok, now I'm getting completely confused.

So was I, but I think I've sorted it out now! :)

> **menth1979 said:**
> I always thought that the vendor id and product id were an unambiguous key for the chipset. 

That's my understanding too, but the OP of the thread you posted to - [http://ubuntuforums.org/showthread.php?t=2236540](http://ubuntuforums.org/showthread.php?t=2236540) - appears to have muddled things. Their dmesg output shows that the 0df6:0078 device is a Ralink, but they seem to have concluded that their wireless device is a Realtek and put Realtek RTL8192SU in their thread title. I have no idea why. I'll post to that thread and try to get things clarified, but in the meantime you are much better off with your own thread, particularly as the title to the other one is misleading.

I suggest you run the wireless script so that those who take an interest in wireless issues can help you without the distraction of the confusion in the other thread.

> **menth1979 said:**
> Is it possible that my 0df6:0078 is a Ralink 2800 while yours is a Realtek?

I presume you are addressing the OP of the other thread, but they are unlikely to see your post. 

Good luck with getting this fixed.

---

### Post by menth1979 on 2014-08-08
Bad and good news.

Good news: the adapter now works.
Bad news: it's working on a Raspberry Pi, with Raspbian.

First I modprobed rt2800usb.
Then I echoed 0df6 0078 (vendor and product id, got from lsusb) to new_id in the drivers folder.
Then I manually started wpa_supplicant.

> 
modprobe rt2800usb
echo "0df6 0078" > /sys/bus/usb/drivers/rt2800usb/new_id
wpa_supplicant -i wlanX -c /etc/wpa_supplicant/wpa_supplicant.conf


If it works on the RPi it's good because I can use one of the adapters I use on them that works on my computer. But I don't want to be selfish and I will still try to make it working on my main PC.
Now I wonder:
- how to make the modprobing, echoing and wpa_supplicanting at boot
- why the SAME trick isn't working on x86 systems

As this trick is not working on Ubuntu or similar distros like Linux Mint I am reticent to mark this thread as [SOLVED].

---

### Post by Hadaka on 2014-08-08
Hi,to determine your chip set and for more info 
plug your usb wifi rt2800usb in and do and post
```
lsusb
```
that should show your pci-id for that card.
then do.
```
modinfo rt2800usb | grep YOUR_PCI-ID
```
I did this with the only usable numbers you have in your post and got,
```
modinfo rt2800usb | grep 0078
```
output
```
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
```
does not match your numbers,
to see ALL the possibilities for rt2800usb...do
```
modinfo rt2800usb
```

---

### Post by menth1979 on 2014-08-08
Thanks, the problem is that, even if the dongle uses the rt2800usb driver, the system does not recognize it. I think that happens because it's a new product (the other thread is only a week old).
That's the reason because the wireless interface popped up (only on the RPi at the moment) after I echoed the ids in new_id. This seems to be the place where system associates drivers with the hardware.
It was frustrating but anyway I learned a lot of things.

I wonder if it's possible (for a not-very-savvy guy like me) to recompile the module adding this new id. I worked this problem around putting the modprobe and the echo commands into /etc/rc.local.

---

### Post by menth1979 on 2014-08-09
I did the wireless thing. Here are the results.
```


########## wireless info START ##########

Report from: 09 Aug 2014 02:22 CEST +0200

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux 3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

MATE

##### lspci #####

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Intel Corporation Device [8086:d613]
    Kernel driver in use: r8169

```

Nothing strange here, it's my ethernet card.

```

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 004 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 005 Device 002: ID 07b3:040b Plustek, Inc. 
Bus 003 Device 002: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 001 Device 008: ID 0df6:0078 Sitecom Europe B.V. 

```

Adapter is last.

```

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

ndiswrapper           282672  0 


```

I wonder why ndiswrapper is in this list. Maybe I changed somenthing on some obscure configuration file following some guide I found. It is not loaded at boot, it loads when the dongle is inserted. 
Anyway, I always rmmod it before testing.

```

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:eff:fe09:2509/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1275910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1245191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1149066577 (1.1 GB)  TX bytes:822905138 (822.9 MB)
          Interrupt:43 

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

grep: /etc/resolv.conf: No such file or directory

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

nl80211 not found.

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #####

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos #####

[ndiswrapper]
filename:       /lib/modules/3.2.0-67-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.57
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     16E68407AAA1EA699FBCA10
depends:        
vermagic:       3.2.0-67-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #####

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules #####

lp
rtc

coretemp
w83627ehf

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
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
blacklist amd76x_edac

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0cf3:0x9271 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x2001:0x3308 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x050d:0x7050 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# USB device 0x1737:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"

# USB device 0x0bda:0x8178 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan4"

# USB device 0x0bda:0x8178 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan5"

# USB device 0x0df6:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan6"

# USB device 0x0df6:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan7"

# USB device 0x0df6:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan8"

# USB device 0x0df6:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan9"

# USB device 0x0df6:0x0078 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan10"

##### dmesg #####

[   18.612792] intel_rng: don't want to disable this in firmware setup, and if
[43674.322086] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)

########## wireless info END ############

```

The trick that revived the dongle on the Raspberry Pi is not working on this machine. I don't think that ARM modules are better than the Intel ones, I think that I messed up something in the system. For example: I upgraded the firmware file with a new one I found on Mediatek (the company which acquired Ralink) site. I kept the old one.

---

### Post by varunendra on 2014-08-11
> **menth1979 said:**
> I wonder if it's possible (for a not-very-savvy guy like me) to recompile the module adding this new id.

The obvious place to add the id is "rt2800usb.c" file of the source code package (I just tried it on the backports-3.15.1-1). But adding the id manually there and compiling doesn't seem to reflect the id in the compiled module.

I may try to figure out why when and if found time for it, but I doubt it'll work anyway. I'm curious due to it working in Raspberry Pi, but getting time to do the research is a huge problem for me nowadays.

I hope someone may shed some light on why the change in the rt2800usb.c file doesn't reflect in the compiled module, and how to make it work. It may be a nice discovery for this device.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature. Forum mod lisati just did it for you, but you should know how to do it yourself.

---

### Post by FroggleWoggle on 2014-08-14
Please see [my post]("http://ubuntuforums.org/showthread.php?t=2236540&p=13098452#post13098452") in the original thread. I got it to work!

---

### Post by varunendra on 2014-08-14
Interesting! The OP already mentioned that the same trick didn't work for them. I guess it is the device "Unplug > Replug" cycle that is the critical part of the workaround.

But if it works, it can be made automatic by adding the echo command (along with "modprobe rt2800usb" also) to **/etc/rc.local** file, so that one doesn't have to plug the device twice.

---

