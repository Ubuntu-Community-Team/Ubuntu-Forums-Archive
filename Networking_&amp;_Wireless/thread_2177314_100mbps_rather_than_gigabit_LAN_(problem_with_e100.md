---
title: "100mbps rather than gigabit LAN (problem with e1000e)"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by julien-dal-col on 2013-09-28
Hi,

I have a **Dell optiplex 755** running Ubuntu 13.04.

The integrated NIC is "*Intel 82566DM Gigabit LAN*"

"*Connection Informations*" gives me:
 - "Driver:          e1000e"
 - "Speed:         100 Mb/s"

I guess there is a problem, It should say "1000Mb/s"... There is no 10/100 port in my whole LAN, only gigabit ones.

I don't know how to test wether my connection is actually limited to 100mbps or not...
I don't know how to fix this if the connection is endeed limited to 100mbps.

Any advice anyone?
Thank you very much in advance for your help.
Best,
-J-

---

### Post by praseodym on 2013-09-28
Also the switches (if any) and all cables support gigabit? Please show

```
sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by The Cog on 2013-09-28
```
lshw -C network
```
should give useful information too.

---

### Post by julien-dal-col on 2013-09-28
:)
Everything 100% gigabit...

user@ubuntu:~$ sudo ethtool eth0
[sudo] password for user: 
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes

_____________________________________

user@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=1.4-0 ip=192.168.xxx.xxx latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:febe0000-febfffff memory:febdb000-febdbfff ioport:ecc0(size=32)


Useful?

---

### Post by sanderj on 2013-09-28
The lshw output in line "configuration" says "speed=100Mbit/s". So there you have it.

My own output says: "speed=1Gbit/s"

So: check your cables and switch. Bad cables/connectors are a cause of throttling down to 100 or even 10 Mbps.

---

### Post by julien-dal-col on 2013-09-28
I did...  :S
The NIC is connected to a brand new Linksys WUMC710 and the Ethernet cable was bundled with it (it's written "Cat5E patch cable" on the cable)...

I get a gigabit connection with the same device (linksys) and the same cable plugged into a different machine (running Win7 pro x64)...

---

### Post by sanderj on 2013-09-28
Is there Windows on you Dell optiplex 755? If so: is gigabit working under Windows?

Furthermore, you could do this:

```
# List current settings
sudo ethtool eth0
# are 1000baseT link modes listed?

# at your own risk (if 1000baseT is listed !):
# Re-negotiate speed
sudo ethtool -r eth0
# Force speed manually to gigabit
sudo ethtool -s eth0 speed 1000
```

HTH

---

### Post by julien-dal-col on 2013-09-28
no windows on the optiplex :(

user@ubuntu:~$ sudo ethtool eth0
[sudo] password for user: 
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes



What is the risk of forcing gigabit transfer rate?

Tx
-J-

---

### Post by julien-dal-col on 2013-09-28
One more info:

When I installed 13.04 the network card would not work ("device not managed"). I solved this following this tread:
[http://www.techishare.com/linux/ubuntu-device-not-managed-problemsolved/](http://www.techishare.com/linux/ubuntu-device-not-managed-problemsolved/)

Could it be linked to my current problem?
Best,
-J-

---

### Post by praseodym on 2013-09-29
Check:
```

sudo ethtool -s eth0 speed 1000 duplex full
sudo ethtool eth0
```

---

### Post by julien-dal-col on 2013-09-29
> **praseodym said:**
> Check:
```

sudo ethtool -s eth0 speed 1000 duplex full

```

This killed my connection :(

```
user@ubuntu:~$ sudo ethtool -s eth0 speed 1000 duplex full
user@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: [COLOR=#ff0000]Unknown![/COLOR]
    Duplex: [COLOR=#ff0000]Unknown! (255)[/COLOR]
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: [COLOR=#ff0000]no[/COLOR]
user@ubuntu:~$ 
```

---

### Post by julien-dal-col on 2013-09-30
do you think something may be wrong with the driver?

---

### Post by praseodym on 2013-09-30
Maybe. Try to update it according to this:

[http://forum.ubuntuusers.de/topic/netzwerk-macht-probleme-unter-12/#post-5609442](http://forum.ubuntuusers.de/topic/netzwerk-macht-probleme-unter-12/#post-5609442)

The download link is there.

---

### Post by julien-dal-col on 2013-09-30
entschuldigungen sie bitte aber ich spreche nicht deutsch...
:s

---

### Post by julien-dal-col on 2013-09-30
OK, so after a quick German self-learning ;) I did the following:
Downloaded [http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/15817/eng/e1000e-2.5.4.tar.gz&lang=eng&Dwnldid=15817](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/15817/eng/e1000e-2.5.4.tar.gz&lang=eng&Dwnldid=15817)
from [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=15817](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=15817)

extracted the archive on the desktop.
Opened a terminal into the src directory of the downloaded folder
Ran the following:
make
sudo make install
sudo rmmod -f e1000e (this killed my connection)
sudo modprobe e1000e (this restored my connection)
sudo reboot

Result: no change :s

---

### Post by praseodym on 2013-09-30
Ok, lets check:
```

sudo ethtool eth0
dmesg | egrep 'eth0|e1'
ifconfig eth0
modinfo e1000e
```

---

### Post by julien-dal-col on 2013-10-01
1)
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes



2)
nothing displayed

3)
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.xxx.xxx  Bcast:192.168.xxx.xxx  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12745723 (12.7 MB)  TX bytes:186773342 (186.7 MB)
          Interrupt:21 Memory:febe0000-fec00000 


4)
filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.5.4-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     14FC0D45EE1DAA1B5E0DBBA
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           Node:[ROUTING] Node to allocate memory on, default -1 (array of int)
parm:           debug:Debug level (0=none,...,16=all) (int)


:S this is Chinese to me...

---

### Post by praseodym on 2013-10-01
Did you really check all components (cable, router plug, switch, if any, etc.)? Only if all of them support Gigabit, it will work.

"Link detected: no" may be a hint for that (see above)

---

### Post by julien-dal-col on 2013-10-01
I double and even tripled checked...

---

### Post by praseodym on 2013-10-01
Try to deactivate the auto-negotiation:

```
sudo ethtool -s eth0 speed 100 autoneg off
```
After that try it with 1000

---

### Post by julien-dal-col on 2013-10-03
> **praseodym said:**
> Try to deactivate the auto-negotiation:

```
sudo ethtool -s eth0 speed 100 autoneg off
```
After that try it with 1000

Didn't work... I still have to test this more thoroughly though...

However, I did the following:

 - Install win7pro x64 on the optiplex 755 -> I get 1000mbps using the same hardware

 - get a laptop configured with dual boot (WinXPsp3 & Ubuntu 12.04) -> 1000mbps on both OS... On ubuntu 12.04 the NIC driver was "tp3" not "e1000e" like for the optiplex 755

My best guess: e1000e is (a POS...) not working properly with my NIC
:s

---

### Post by julien-dal-col on 2013-10-04
is there any alternative to e1000e?

---

### Post by praseodym on 2013-10-04
Please check the product and vendor IDs:
```

lspci -nnk | grep -iA2 net
```

---

### Post by julien-dal-col on 2013-10-05
I installed:
XPEnology_DS3612xs_3211-repack-trantor-v1.2
on that hardware (dell optiplex 755).
It also uses e1000e as a NIC driver. Guess what? I get 100mbps connection.
It really seems something is wrong with e1000e

---

### Post by julien-dal-col on 2013-10-05
> **praseodym said:**
> Please check the product and vendor IDs:
```

lspci -nnk | grep -iA2 net
```

here you are:
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
    Subsystem: Dell OptiPlex 755 [1028:0211]
    Kernel driver in use: e1000e
```

---

### Post by julien-dal-col on 2013-10-06
.

---

### Post by julien-dal-col on 2013-10-07
is it useful in any way?

---

### Post by julien-dal-col on 2013-10-09
Does anyone has the same problem? From what I could find e1000e is VERY widespread... Tons of network adapters use this driver... How come it limits bandwidth to 100mbps only in my case?

---

### Post by julien-dal-col on 2013-10-09
I read this:
[http://lwn.net/Articles/278016/](http://lwn.net/Articles/278016/)
My NIC is not PCIe, it is onboard... maybe I should try to use e1000 rather than e1000e?
How can I do that?

---

### Post by julien-dal-col on 2013-10-16
anyone?

---

### Post by lazlo on 2013-10-22
Same here! I have a Lenovo Thinkpad X201T with a intel NIC (82577LM). It worked with 1000baseT before. Now I only get 100baseT. Before I had this problem but i could solve it by reconnecting, disabling and reenabling networking or use of mii-tool.

I'm using ubuntu 13.04 with the 3.8.0-32 kernel.

---

### Post by lazlo on 2013-10-22
Same here! I have a Lenovo Thinkpad X201T with a intel NIC (82577LM). It worked with 1000baseT before. Now I only get 100baseT. Before I had this problem but i could solve it by reconnecting, disabling and reenabling networking or use of mii-tool.

I'm using ubuntu 13.04 with the 3.8.0-32 kernel.

---

### Post by julien-dal-col on 2013-10-23
tx :)
Please keep me informed if you find a fix
Best,
-J-

---

