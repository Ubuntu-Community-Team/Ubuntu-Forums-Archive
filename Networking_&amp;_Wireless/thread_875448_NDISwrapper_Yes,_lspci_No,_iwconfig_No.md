---
title: "NDISwrapper Yes, lspci No, iwconfig No"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by davedave on 2008-07-30
Hi all,

I'm having a little bit of problems getting WiFi to work on my new ASUS M51VA-AS045G. I know it works, as it is fine with the Vista installation.

Anyways, on to the troubleshooting.

The ASUS WiFi driver was downloaded from [_here_]("http://dlcdnet.asus.com/pub/ASUS/nb/Drivers/WLAN/WiFi_Intel_VT_080626.zip").

I have installed NDISwrapper 1.53 from source
**ndiswrapper -v**
> utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko
version:        1.53
vermagic:       2.6.24-19-generic SMP mod_unload 586

The driver/device seems to be installed OK
**ndiswrapper -l**
> netw5v32 : driver installed
	device (8086:4232) present

I have created a script to disable modules SSB and B43
**cat /etc/init.d/wirelessfix.sh**
> #!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44


Now for the bits that don't really make sense or line up with anybody else's experience.

**ndiswrapper -m** seems to have written the following file
**cat /etc/modprobe.d/ndiswrapper**
> alias wlan0 ndiswrapper

iwconfig does not detect a wireless device
**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

lspci does not list the wireless card correctly
**lspci**
> 06:00.0 Network controller: Intel Corporation Unknown device 4232

Does anyone know why NDISwrapper thinks that the driver is installed and the device is present, yet lspci does not recognise the card and iwconfig does not recognise a wireless device?

Any help is greatly appreciated!

Cheers,
Dave

---

### Post by cdtech on 2008-07-30
I added these to my /etc/modprobe.d/blacklist file:

# everything to do with wireless
blacklist b44
blacklist ipv6
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist agpgart

I tried to use the wirelessfix.sh script and found that even after a reboot I had to re run the script for it to work. Now, since I've added the modules to the blacklist, after a reboot my ndiswrapper works.

This may not work for you but it's worth a try......

---

### Post by davedave on 2008-07-30
I tried those blacklistings and also stopped the wirelessfix.sh script from running.

Even after modprobing the ndiswrapper, I still get the same problems

> davidw@Laphroaig:~$ **lsmod | grep b4**
davidw@Laphroaig:~$ **lsmod | grep ssb**
davidw@Laphroaig:~$ **lsmod | grep ndiswrapper**
ndiswrapper           193436  0 
usbcore               146028  8 ndiswrapper,hci_usb,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
davidw@Laphroaig:~$ **cat /etc/modprobe.d/ndiswrapper**
alias wlan0 ndiswrapper
davidw@Laphroaig:~$ **lspci | grep Network**
06:00.0 Network controller: Intel Corporation Unknown device 4232
davidw@Laphroaig:~$ **ndiswrapper -l**
netw5v32 : driver installed
	device (8086:4232) present
davidw@Laphroaig:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

Thanks for the help anyway!

---

### Post by superprash2003 on 2008-07-30
i remember having a similar issue once.. ndiswrapper said it was present but it wasnt quite there.. but a reboot worked for me

---

### Post by davedave on 2008-07-30
Thanks, though I have already tried that windows approach ;)

---

### Post by cdtech on 2008-07-31
What do you get with the output of:
lshw -C network

---

### Post by davedave on 2008-07-31
> **cdtech said:**
> What do you get with the output of:
lshw -C network

**sudo lshw -C network**
>   *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:2a:b4:1b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.5.1.44 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

### Post by cdtech on 2008-07-31
Your "logical name: eth0" is incorrect. I'm looking through my notes......

---

### Post by davedave on 2008-07-31
That's on the LAN NIC though

---

### Post by cdtech on 2008-07-31
Ok, go to /etc/udev/rules.d and edit the file "70-persistent-net.rules":
sudo gedit /etc/udev/rules.d/70-persistent-net.rules

Look for the line:
```
# PCI device 0x14e4:0x4311 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:73:b5:7e:d1", ATTRS{type
}=="1", NAME="**wlan0**"
```

Yours will probably have the eth0 listed, just change that to wlan0

---

### Post by cdtech on 2008-07-31
> **davedave said:**
> That's on the LAN NIC though

Your correct. I just had a brain thing then. Try my last post and see what you have listed for the "PCI device 0x14e4:0x4311 (ndiswrapper)"

---

### Post by davedave on 2008-07-31
I only have one entry, and that's for the realtek LAN NIC.
I don't actually have one that mentions (ndiswrapper)

> # PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:15:2a:b4:1b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

---

### Post by cdtech on 2008-07-31
What do you get with "ifconfig -a"

---

### Post by davedave on 2008-07-31
No sign of it at all

> eth0      Link encap:Ethernet  HWaddr 00:22:15:2a:b4:1b  
          inet addr:10.5.1.44  Bcast:10.5.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161288 errors:0 dropped:1371506772 overruns:0 frame:0
          TX packets:49698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121899901 (116.2 MB)  TX bytes:4117945 (3.9 MB)
          Interrupt:217 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6900 (6.7 KB)  TX bytes:6900 (6.7 KB)

---

### Post by cdtech on 2008-07-31
It's really starting to sound like a driver issue. Did you try ifup wlan0 (i'm really just throwing stuff out there now).

---

### Post by davedave on 2008-07-31
I do agree, but that won't be proven until it's fixed :(

I booted up in Vista to find the exact driver version, which was the one I was using (I had previously tried every one for that model of computer and this was the only one that **ndiswrapper -l** returned "device present" for). It's a Intel WiFi Link 5100 v12.0.0.73

I just looked around the net and found the XP version (not sure if it's actually different) and it has the exact same results.

**ndiswrapper -l**
> [NOPARSE]netw5x32 : driver installed
	device (8086:4232) present[/NOPARSE]

I also read someone had some dodgy characters inside their driver .inf file, but I had no better luck after running dos2unix on the file.

This sort of points the finger at the driver, but I'm guessing anything stopping ndiswrapper to run correctly would also cause something similar.

**tail -f /var/log/messages; sudo modprobe -r ndiswrapper; sudo modprobe ndiswrapper**
> [NOPARSE]Jul 31 17:38:38 Laphroaig kernel: [ 1129.422640] usbcore: deregistering interface driver ndiswrapper
Jul 31 17:38:38 Laphroaig kernel: [ 1129.423039] ndiswrapper (ntoskernel_exit:2671): object f7517220(2) was not freed, freeing it now
Jul 31 17:38:38 Laphroaig kernel: [ 1129.448992] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Jul 31 17:38:38 Laphroaig loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netw5x32 
Jul 31 17:38:38 Laphroaig kernel: [ 1129.473545] usbcore: registered new interface driver ndiswrapper[/NOPARSE]

Thanks again for your help cdtech, greatly appreciated!

---

### Post by davedave on 2008-07-31
Looking through the list of supported card on the ndiswrapper wiki, it doesn't appear that the card is supported at all :(

I might use the SVN version of ndiswrapper and update and recompile weekly. When it does become supported, I'll post a comment here.

Thanks for your help people!

---

### Post by yaojun8885 on 2008-08-12
> **davedave said:**
> Looking through the list of supported card on the ndiswrapper wiki, it doesn't appear that the card is supported at all :(

I might use the SVN version of ndiswrapper and update and recompile weekly. When it does become supported, I'll post a comment here.

Thanks for your help people!

I have the same problem.
Waiting for your good news.

---

### Post by davedave on 2008-08-12
Also watch [this thread](http://ubuntuforums.org/showthread.php?p=5563828)

If I get time this weekend, I'll retry recompiling the kernel and post my results.

---

