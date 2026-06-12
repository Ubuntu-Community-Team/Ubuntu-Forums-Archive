---
title: "Problem with zd1211rw driver"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by SnowTDM on 2008-04-29
Hello everybody,

I have an USB wireless card with chip Zydas 1211rw using module zd1211rw. It used to run perfectly in Ubuntu 7.10, but I've upgraded to 8.04 and it doesn't connect or show any wireless network. It also doesn't connect booting with desktop CD or upgrading from 7.10 to 8.04 without any CD.

But if I start 8.04 version with 7.10 kernel (2.6.22) card connects perfectly, including with WAP encryption. It also connect if I boot with 7.10 desktop CD.

I think it is a problem with driver or module zd1211rw in conjunction with new kernel.

Typing "dmesg | grep zd" I get:

[   58.667458] zd1211rw 2-2.4:1.0: eth0
[   58.667475] usbcore: registered new interface driver zd1211rw
[   67.326365] zd1211rw 2-2.4:1.0: firmware version 4605
[   67.366327] zd1211rw 2-2.4:1.0: zd1211 chip 0ace:1211 v4721 high 00-02-e3 RF2959_RF pa0 g----
[   68.365743] zd1211rw 2-2.4:1.0: error ioread32(CR_REG1): -110

Typing "lshw -C network" I get:

  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:02:e3:45:53:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

Typing "lsmod | grep zd" I get:

zd1211rw               64008  0
ieee80211softmac       34688  1 zd1211rw
ieee80211              38344  2 zd1211rw,ieee80211softmac
usbcore               169904  5 zd1211rw,usblp,ehci_hcd,ohci_hcd

Typing "lsusb" I get:

Bus 002 Device 004: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 002 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:7604 Hewlett-Packard Deskjet 3940
Bus 001 Device 001: ID 0000:0000  

¿Somebody could help me?

Thanks in advance

---

### Post by cbarros on 2008-04-30
Hi, I have the same problem. My desktop it's an AMD 64Bit. I just get a fresh install of hardy and the wireless card doesn't work. with Ubuntu 7.10 it works fine.

anybody knows what's the problem.?

Here is my dmesg output

[   25.368780] usb 2-2: reset high speed USB device using ehci_hcd and address 3
[   25.501664] zd1211rw 2-2:1.0: eth2
[   25.501673] usbcore: registered new interface driver zd1211rw
[   30.301333] zd1211rw 2-2:1.0: firmware version 4605
[   30.341295] zd1211rw 2-2:1.0: zd1211 chip 0ace:1211 v4330 high 00-02-e3 RF2959_RF pa0 g----
[   31.342636] zd1211rw 2-2:1.0: error ioread32(CR_REG1): -110
[   44.306726] ADDRCONF(NETDEV_UP): eth2: link is not ready

---

### Post by sebbar on 2008-05-02
> **SnowTDM said:**
> 
Bus 002 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]

The problem is the hub. Try to unplugged it and reboot system.

---

### Post by Sambo320 on 2008-05-02
I am using the belkin F5D7050 wireless USB adapter version 4000. The device uses the zydas 1211rw driver, but it is not working. I have read that the new kernel has screwed somethings up with this module and am wondering if people are having the same problem.

I guess I am wondering if the zd1211rw module has worked with kernels before this newest release?

---

### Post by Sambo320 on 2008-05-02
bumb

---

### Post by Sambo320 on 2008-05-02
The device does not even show up with lsusb.

---

### Post by Bastanteroma on 2008-05-03
For what it's worth, my zd1211rw chipset works fine in Gutsy and Hardy. I get similar responses to the commands you entered, except that I get no errors.

---

### Post by Sambo320 on 2008-05-03
Do you have the Belkin F5D7050 version 4000?

---

### Post by Paris Heng on 2008-05-03
Copy the firmware of zd1211rw into the existing zd1211 folder in the kernel. :lolflag:

---

### Post by cbarros on 2008-05-04
Hi, I had Solved this problem with ZD1211 based Wireless Stick on Hardy, but i don't like the way i solved this. I had to use ndiswrapper.

I think something was forgotten on the Hardy's kernel. This Adapter was working just fine on my old Gutsy, and without use ndiswrapper and windows driver.

well here is what i did:

[https://answers.launchpad.net/ubuntu/+question/31569](https://answers.launchpad.net/ubuntu/+question/31569)

i hope it may help someone.

if any body knows how to solve this with the linux native kernel or driver, let me know it please.

---

### Post by Sambo320 on 2008-05-04
> **cbarros said:**
> Hi, I had Solved this problem with ZD1211 based Wireless Stick on Hardy, but i don't like the way i solved this. I had to use ndiswrapper.

I think something was forgotten on the Hardy's kernel. This Adapter was working just fine on my old Gutsy, and without use ndiswrapper and windows driver.

well here is what i did:

[https://answers.launchpad.net/ubuntu/+question/31569](https://answers.launchpad.net/ubuntu/+question/31569)

i hope it may help someone.

if any body knows how to solve this with the linux native kernel or driver, let me know it please.

This did not work. Hardware: not present

---

### Post by SnowTDM on 2008-05-05
I've got same result: zd1211bu hardware not present

---

### Post by cbarros on 2008-05-05
Could you show us your dmesg output?  to see the hardware ID

maybe the windows driver i found does not have support for your sticks.

this is the hardware that driver supports.

[ZyDAS]
HARDWARE ID
------------
(0ACE:1211)
(0586:3401)
(0586:3402)
(0B3B:5630)
(0B3B:6630)
(0B3B:1630)
(129B:1666)
(0CDE:0009)
(0CDE:0011)
(079B:004A)
(6891:A727)
(1435:0711)
(0DF6:9071)
(07B8:6001)
(126F:A006)

---

### Post by SnowTDM on 2008-05-06
Our stick is the first of them

dmesg

[ 67.366327] zd1211rw 2-2.4:1.0: zd1211 chip 0ace:1211 v4721 high 00-02-e3 RF2959_RF pa0 g----

And  lsusb:

Bus 002 Device 004: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi

---

### Post by Sambo320 on 2008-05-06
I do not get anything from the device in lsusb... I want to cry...

---

### Post by SnowTDM on 2008-05-08
Sambo320,

Have you tried to connect the stick in another port?

---

### Post by Sambo320 on 2008-05-08
I tried every port. Nothing works.

---

### Post by cottoncloth on 2008-05-11
I have the Belkin F5D7050 v4 w/a new hardy install ... 

but in my case, device plugged in during boot always caused a kernel panic.  As long as I unplug before & during boot, it works fine.  Major PITA for a dual-boot machine.

Ndiswrapper method doesn't work for me either - hardware not present.

Anybody tried another kernel?

---

### Post by martin15s on 2008-05-11
had similar problems with this driver in 7.10 and 8.04 - gave up and bought an Edimax pcmcia card- not expensive -worked straight from the box in 8.04 worth every penny.

---

### Post by SnowTDM on 2008-05-14
Hello everybody,

I've solved the problem changing the stick from a hub port to a port connected directly to motherboard.

It seems a problem with the hub instead with the driver of the stick.

Thanks

---

### Post by preki on 2008-05-17
Cottoncloth,

I have the same problem, I have F5D7050 v4 and get kernel panic if the USB stick is plugged in while booting.  Weirdly, for about 2 weeks after upgrading from Gutsy to Hardy I didn't have this problem, then is suddenly started (maybe after routine updates)

Even when I plug it in after Gnome has started up then it sometimes takes a few attempts to connect to the network - it looks like it connects but I only have connectivity for a about 10 secs then can't even ping the router.  Usually after a 2-3 attempts it connects properly it then stays connected no problem.

It worked perfectly in Gutsy.  I'd just boot to the old kernel if only I could get nVidia drivers working on that one.

Anyone have any ideas how to stop the panic on boot?

---

### Post by preki on 2008-05-25
Cottoncloth and others,

It turned out the oops screen on boot for me was caused by conflicting hardware: the Belkin wireless USB and a USB hub built in to my monitor.

Unplugging one or the other leads to the latest (Hardy) kernel booting fine.  (Easy resolution for me is to leave the hub unplugged as I hardly used it anyway)

Perhaps this is the cause of the problem for others too ..?

---

### Post by SnowTDM on 2008-05-29
I've solved the problem starting Ubuntu without with the hub unplugged. If I start it with the hub connected I've to unplug and and plug again the wireless stick.

But the problem is there. It shouldn't be necessary to do those things. What is the forum to solve usb problems?

Best regards

---

### Post by SeePU on 2008-07-03
I installed Debian Testing/Lenny and had the same...uh, 'solution.'  I was having problems and after I read through this thread, I unplugged the usb cable to my Laser Printer and rebooted.   Upon the boot up of the OS, 'poof', I could scan for networks and connect.

Could it be a usb-oriented bug or usb conflict with the zd1211 driver/kernel (sync?)?  I have no idea.  

I am not sure how long I'll have this 'situation' but thanks for your comments, guys.

---

### Post by yosemite610 on 2008-07-04
FWIW, the only way I could get the ZyXEL G220v2 to work in Hardy was by turning off USB2.0:
```
sudo modprobe -r ehci_hcd
```
Then unplug the dongle, plug it back in and it would work.

I had read about problems with USB hubs and suggestions to plug directly into the motherboard USB ports. I was already plugged into a motherboard USB port (An ASUS P5B with 4 ports in back).

So, I tried plugging it into a PCI USB 4-port (5 with one internal?) hub and voila! It comes up all by its lonesome and I don't have to touch the ehci_hcd module so I have USB2.0 too.

---

### Post by trisweb on 2008-07-06
Same issue and same solution here - the device came up with the IOERR in dmesg when plugged in or modprobe'd, but works perfectly once my USB hub is unplugged.

Seems to me this is a driver issue with zd1211rw, but I could be wrong. It's a pain though, I sort of want to use my USB hub...

---

