---
title: "Dell Precision M60 - Wireless Configuration"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by dsgg10 on 2008-09-06
Hi all,

Newbie Question: Anyone know how to configure wireless on a Dell Precision M60 - Ubuntu 8.01 LTS

At the same time how can I tell what the system actually thinks is installed?

Cheers

Dave

---

### Post by pytheas22 on 2008-09-06
Please open a terminal (Applications>Accessories menu), run these commands and post the output here:
```

lspci -nn
lsusb
lshw -C Network
```

With that, we can figure out which chipset your card uses, and find instructions for installing it.  The name under which the card is sold is not a reliable way of knowing which drivers it needs etc.

---

### Post by dsgg10 on 2008-09-06
Thanks for the help - From this im pretty certain its the dreaded Broadcom 4306.

dave@ubuntu-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV36 [Quadro FX Go1000] [10de:034c] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
02:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
02:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)


dave@ubuntu-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


dave@ubuntu-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:16:bb:14
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:10:69:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by pytheas22 on 2008-09-06
Yes, you have Broadcom 4306, which is a bit of a pain.  Fortunately I have the same one in a laptop, though, and know that it should work with ndiswrapper if you install everything correctly (it also works with the bcm43xx driver, but the throughput rate and signal strength can be flaky, so I recommend trying ndiswrapper first).  Please try running this:
```

echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
echo 'ndiswrapper' | sudo tee -a /etc/modules
sudo apt-get install ndiswrapper*
wget http://burnthesorbonne.com/files/4320_drivers.tar.gz
tar -xzvf 4320_drivers.tar.gz
sudo ndiswrapper -i bcmwl5a.inf
```

Then reboot, after which things should work.  If not, please post the output of these commands:
```

uname -m
lshw -C Network
dmesg | grep -e ndis -e wlan
```

---

### Post by dsgg10 on 2008-09-06
It seems that blacklisting ssb removes the wireless support completely. I no longer have a Wireless Networks option under the network icon.

output from command attached

dave@ubuntu-laptop:~$ echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
dave@ubuntu-laptop:~$ echo 'blacklist b43legacy' | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43legacy
dave@ubuntu-laptop:~$ echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
blacklist ssb
dave@ubuntu-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
dave@ubuntu-laptop:~$ sudo ndiswrapper -i ~/drivers/bcm43/bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2


##################### AFTER REBOOT #######################

dave@ubuntu-laptop:~$ uname -m
i686
dave@ubuntu-laptop:~$ 
dave@ubuntu-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:16:bb:14
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e wlan
[   26.144372] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   26.195387] usbcore: registered new interface driver ndiswrapper

---

### Post by pytheas22 on 2008-09-06
> It seems that blacklisting ssb removes the wireless support completely. I no longer have a Wireless Networks option under the network icon.

That's ok; that's actually what you want, because you want ndiswrapper to drive the card instead of ssb (which doesn't really work even though it brings the card up).

For some reason, however, b43 is still preventing ndiswrapper from claiming the card.  Please run these commands and post the output so that we can figure out why b43 doesn't want to go away:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by dsgg10 on 2008-09-07
Thanks for the ongoing help...output attached - I also tried on eth0 but niether makes any difference

dave@ubuntu-laptop:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod ssb
dave@ubuntu-laptop:~$ sudo rmmod ndiswrapper
dave@ubuntu-laptop:~$ sudo modprobe ndiswrapper
dave@ubuntu-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
dave@ubuntu-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e wlan
[   67.581658] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   67.779896] usbcore: registered new interface driver ndiswrapper
[  425.436170] usbcore: deregistering interface driver ndiswrapper
[  133.579208] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  133.715448] ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) loaded
[  133.730293] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: f8d8c3e0
[  133.730309] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[  133.730505] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  133.730524] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  133.730567] ndiswrapper (mp_halt:259): device f77d6480 is not initialized - not halting
[  133.730575] ndiswrapper: device eth%d removed
[  133.730670] ndiswrapper: probe of 0000:02:03.0 failed with error -22
[  133.730842] usbcore: registered new interface driver ndiswrapper



##################### Also tried with eth0 #######################

dave@ubuntu-laptop:~$ sudo ifconfig eth0 up

dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e eth
[   21.399935] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0f:1f:16:bb:14
[   21.399959] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   21.399967] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[   23.870101] Driver 'sd' needs updating - please use bus_type methods
[   23.870633]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   67.581658] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   67.779896] usbcore: registered new interface driver ndiswrapper
[  315.535086] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  425.436170] usbcore: deregistering interface driver ndiswrapper
[  133.579208] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  133.715448] ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) loaded
[  133.730293] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: f8d8c3e0
[  133.730309] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[  133.730505] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  133.730524] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  133.730567] ndiswrapper (mp_halt:259): device f77d6480 is not initialized - not halting
[  133.730575] ndiswrapper: device eth%d removed
[  133.730670] ndiswrapper: probe of 0000:02:03.0 failed with error -22
[  133.730842] usbcore: registered new interface driver ndiswrapper

---

### Post by dsgg10 on 2008-09-07
Also just to note so that in post #4 where you said

sudo apt-get install ndiswrapper*
wget [http://burnthesorbonne.com/files/4320_drivers.tar.gz](http://burnthesorbonne.com/files/4320_drivers.tar.gz)
tar -xzvf 4320_drivers.tar.gz

so 

I downloaded the file manually from windoze - unzipped and untared and put  the files into ~/drivers/bcm43

then did

sudo ndiswrapper -i /home/dave/drivers/bcm43/bcmwl5a.inf


same with the ndiswrapper I downloaded the .deb package to usb pen and run them from there

I trust this is correct??

---

### Post by pytheas22 on 2008-09-07
hmmm, ndiswrapper doesn't like the Windows driver that you installed:
> 
[ 133.730293] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: f8d8c3e0
[ 133.730309] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[ 133.730505] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[ 133.730524] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)

In that same file containing the Windows drivers that you unpacked, there is a second .inf called just bcmwl5.inf.  You should try removing the currently installed driver and replacing it with bcmwl5.  You can remove bcmwl5a.inf with:
```

sudo ndiswrapper -r bcmwl5a
```

Then install bcmwl5.inf with:
```

sudo ndiswrapper -i /home/dave/drivers/bcm43/bcmwl5.inf
```

Please do that, then reboot and post again the output of:
```

sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

Let me know if using the other .inf file changes anything.

---

### Post by dsgg10 on 2008-09-07
once again thanks for continued help...output below...still no wireless in network manager.

dave@ubuntu-laptop:~$ sudo modprobe ndiswrapper
dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e wlan
[   26.353403] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   26.400918] usbcore: registered new interface driver ndiswrapper
dave@ubuntu-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

---

### Post by pytheas22 on 2008-09-07
Please reboot, then post the output of:
```

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
```

As I said, the 4306 can be a bit of a pain, but we'll get there...

---

### Post by dsgg10 on 2008-09-08
Thanks I really appreciate your help and patience...

dave@ubuntu-laptop:~$ sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
dave@ubuntu-laptop:~$ sudo modprobe ndiswrapper
dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e wlan
[   64.241340] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   64.455346] usbcore: registered new interface driver ndiswrapper
[  489.395230] usbcore: deregistering interface driver ndiswrapper
[  490.971147] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  147.307982] usbcore: registered new interface driver ndiswrapper

---

### Post by pytheas22 on 2008-09-08
Strange, ndiswrapper still doesn't appear to be bringing up the interface.  Could you please reboot again and post the output of:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmob b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
lshw -C Network
iwlist scan
dmesg | grep -e ndis -e wlan
```

Sorry to make you type so much, but that should help figure out what's wrong.

---

### Post by dsgg10 on 2008-09-08
No problem, hope this helps...thanks again

dave@ubuntu-laptop:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
dave@ubuntu-laptop:~$ sudo rmmod ssb
dave@ubuntu-laptop:~$ sudo rmmod ndiswrapper
dave@ubuntu-laptop:~$ sudo modprobe ndiswrapper
dave@ubuntu-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
dave@ubuntu-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:16:bb:14
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.11 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=32
dave@ubuntu-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

dave@ubuntu-laptop:~$ dmesg | grep -e ndis -e wlan
[   25.751257] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   25.807075] usbcore: registered new interface driver ndiswrapper
[  165.784272] usbcore: deregistering interface driver ndiswrapper
[   49.775085] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   49.783277] usbcore: registered new interface driver ndiswrapper

---

### Post by pytheas22 on 2008-09-08
Oddly, ndiswrapper doesn't seem to want to claim the device with the bcmwl5.inf driver installed, even though ndiswrapper thinks that that's the right driver for your card.  Let's try installing a different Windows driver by running (make sure you are plugged in via the ethernet connection first):
```

sudo apt-get remove --purge ndiswrapper*
sudo apt-get install ndiswrapper* cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Now reboot.  If after rebooting the wireless still won't work, please post the output of:

```
sudo rmmod ssb
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
lshw -C Network
dmesg | grep -e ndis -e wlan
```

If this still yields strange behavior, I have one more Windows driver to try; if even that doesn't work, we can give up on ndiswrapper and use bcm43xx instead.  But this should work, provided ndiswrapper behaves the way it's supposed to.

---

### Post by dsgg10 on 2008-09-08
You are an absolute STAR!!!!!!!

We are now firing on gas - thank you a million times.

Thanks again for sticking with me and leading me through this one! (Apart from wireless config) ubuntu rocks!!

---

### Post by pytheas22 on 2008-09-08
I'm glad we finally found the right Windows driver...sometimes ndiswrapper can be a pain because you have to keep on trying different versions of the Windows drivers until you hit the right one.

Does it still work after a reboot?  You may need to write a script to manually remove some modules after each restart of your computer before ndiswrapper will work, so let me if you have trouble with the wireless after rebooting.  Otherwise, enjoy Ubuntu!

---

### Post by dsgg10 on 2008-09-08
Nope all fine after reboot - again much thanks Cheers

---

