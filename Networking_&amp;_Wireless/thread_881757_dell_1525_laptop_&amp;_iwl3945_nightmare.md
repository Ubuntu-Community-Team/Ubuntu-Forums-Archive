---
title: "dell 1525 laptop &amp; iwl3945 nightmare"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Ichido on 2008-08-06
My 2 Dell Inspirons 1525n, with Hardy and the 3945 Wireless Mini-Card, Wireless worked great until a week ago when I did the usual Updates.
Now I have two laptops without Wifi!
I suspect the "Updates" Killed both of my laptop's wifi

output from "dmesg | tail" from one of my 2 laptops:

[ 70.924157] sky2 eth1: enabling interface
[ 70.930385] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 73.048413] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 73.048555] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 73.049623] iwl3945: Radio disabled by HW RF Kill switch
[ 73.049741] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 86.438315] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 86.438458] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[ 86.439560] iwl3945: Radio disabled by HW RF Kill switch
[ 86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

What is a "Kill Switch"?
How do I "Un-Kill" my Wifi?
Can I "Un-Update"?

I just tried code:
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

No text Output.
Even Rebooted (a habit from my Windoze Days).
Still no Wifi, Wifi Light or Internet Connection/Signal.

JUST got another Dell 1525n Laptop (laptop #3) with Ubuntu 7.10.
I will test everything but I will NOT UPDATE Anything !!!
I love Linux and Ubuntu but I hate the Updates that Kill:(

---

### Post by moogleking on 2008-08-06
Hi,

I have a dell laptop using iwl3945 as well and it didn't work out of the box with Hardy Heron updates.

But doing the following helped me:

enable hardy backports via System > Admin > Software Sources > Updates

then in terminal:

sudo apt-get install linux-backports-modules-hardy-generic 

reboot

that managed to get my wireless working, though I still have a problem with speed: [http://ubuntuforums.org/showthread.php?t=881685](http://ubuntuforums.org/showthread.php?t=881685)

---

### Post by superprash2003 on 2008-08-06
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by pytheas22 on 2008-08-06
> try this [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

Thanks for the suggestion superprash2003, but that page only addresses wireless cards with Broadcom chipsets.  The original poster here has an Intel card.

@Ichido:

Are you sure there's no switch on the laptops to turn your wireless on?  Usually it's a key combination, like function-F2.  Sometimes it's also a separate physical switch that you flip on or off.  Also check your BIOS to ensure that everything for your wireless card is turned on.

That said, I understand that everything was working perfectly before, so I agree that it's probably an issue with a bug in the updates.  Try the hardy-backports repository as suggested above.  If that doesn't help, we can do some research and see if anything turns up.

---

### Post by Ichido on 2008-08-06
I just received my "Replacement" Dell 1525n Laptop.
This one now comes with Ubuntu 8.04 LTS and everything including Wifi works!
I think that I will NEVER Update again :(

Now if I just can get my wife's 1525 Wifi working.

---

### Post by pytheas22 on 2008-08-06
Which chipset exactly does your wife use?  In other words, what is the:
```

lspci -nn
```

output on her machine?

---

### Post by Ichido on 2008-08-07
lspci -nn:
Intel Corp PRO/Wireless 3945ABG Network Connection [8086-4222] (Rev 02).

---

### Post by Ichido on 2008-08-07
> **Ichido said:**
> I just received my "Replacement" Dell 1525n Laptop.
This one now comes with Ubuntu 8.04 LTS and everything including Wifi works!
I think that I will NEVER Update again :(

Now if I just can get my wife's 1525 Wifi working.

I Updated ONLY the Security Updates and now my SOUNDs, DVDs and CDs do not work:confused:
Is anyone TESTING this Before it gets into the Updates or is it just me and my Dells?

---

### Post by Ichido on 2008-08-07
I finished the 900+ updates and Wifi now works, but NOT in Roaming Mode.
Had to Disable the 14 Language Updates to get Firefox running.
I'm still working on it.

---

### Post by bachisanerd on 2008-08-07
I'm having a similar problem, but I've got an HP dv8000 series laptop, also with the 3945ABG chipset.  I previously had Feisty installed, and the card worked without trouble, but now the wireless button above the keyboard has no effect.  From what I can tell, the system is finding the card and the driver (I believe) has been loaded, but the card is not working.  dmesg tells me that the radio kill switch is on.  The only switch is the button, and that doesn't do anything.

I'm now running Ubuntu Studio 8.04.1.

---

### Post by Ichido on 2008-08-08
> **bachisanerd said:**
> I'm having a similar problem, but I've got an HP dv8000 series laptop, also with the 3945ABG chipset.  I previously had Feisty installed, and the card worked without trouble, but now the wireless button above the keyboard has no effect.  From what I can tell, the system is finding the card and the driver (I believe) has been loaded, but the card is not working.  dmesg tells me that the radio kill switch is on.  The only switch is the button, and that doesn't do anything.

I'm now running Ubuntu Studio 8.04.1.

Contact HP or their Forums to find out What and Where the Kill Switch is.

---

### Post by Ichido on 2008-08-10
System> Administration> Network Settings> Wireless Connection.
'Roaming Mode' Still Not Working.
Using Ubuntu 8.04, nm-applet 0.6.6.

---

### Post by pytheas22 on 2008-08-10
> I'm having a similar problem, but I've got an HP dv8000 series laptop, also with the 3945ABG chipset. I previously had Feisty installed, and the card worked without trouble, but now the wireless button above the keyboard has no effect. From what I can tell, the system is finding the card and the driver (I believe) has been loaded, but the card is not working. dmesg tells me that the radio kill switch is on. The only switch is the button, and that doesn't do anything.

Does:
```

sudo ifconfig eth1 up
```

(replace 'eth1' with 'wlan0' if that doesn't work)

do anything?  If not, what does 'dmesg | grep -e iwl -e eth -e wlan' tell you?
```

System> Administration> Network Settings> Wireless Connection.
'Roaming Mode' Still Not Working.
Using Ubuntu 8.04, nm-applet 0.6.6. 
```

You could try using [wicd]("http://wicd.sourceforge.net"), which sometimes does a better job than NM.  It will effectively allow you to roam from network to network.

---

### Post by Ichido on 2008-08-10
[QUOTE=pytheas22;5560591]Does:
```

sudo ifconfig eth1 up
```

This caused No Change.

  If not, what does 'dmesg | grep -e iwl -e eth -e wlan' tell you?

my@dell-desktop:~$ dmesg | grep -e iwl -e eth -e wlan0
[   13.162382] Driver 'sd' needs updating - please use bus_type methods
[   13.697342] Driver 'sr' needs updating - please use bus_type methods
[   24.307154] sky2 eth0: addr mac
[   24.502311] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   24.502315] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   24.502498] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   24.621202] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   25.508043] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   25.510901] Registered led device: iwl-phy0:RX
[   25.510916] Registered led device: iwl-phy0:TX
[   26.907989] wlan0: Initial auth_alg=0
[   26.907995] wlan0: authenticate with AP "MAC"
[   26.909101] wlan0: RX authentication from "MAC" (alg=0 transaction=2 status=0)
[   26.909106] wlan0: authenticated
[   26.909110] wlan0: associate with AP "MAC"
[   26.909983] wlan0: RX AssocResp from "MAC" (capab=0x421 status=0 aid=1)
[   26.909987] wlan0: associated
[   31.341504] sky2 eth0: enabling interface
[   31.347748] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.154035] wlan0: no IPv6 routers present
[  145.029182] sky2 eth0: disabling interface
[  145.059373] Registered led device: iwl-phy0:RX
[  145.059403] Registered led device: iwl-phy0:TX
[  145.063096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.074658] sky2 eth0: enabling interface
[  145.079317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  145.828894] sky2 eth0: disabling interface
[  145.864743] Registered led device: iwl-phy0:RX
[  145.864776] Registered led device: iwl-phy0:TX
[  145.868660] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.885484] sky2 eth0: enabling interface
[  145.891724] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  160.308434] Registered led device: iwl-phy0:RX
[  160.308452] Registered led device: iwl-phy0:TX
[  160.311971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  160.314766] wlan0: Initial auth_alg=0
[  160.314770] wlan0: authenticate with AP "MAC"
[  160.316867] wlan0: RX authentication from "MAC" (alg=0 transaction=2 status=0)
[  160.316871] wlan0: authenticated
[  160.316873] wlan0: associate with AP "MAC"
[  160.320506] wlan0: RX AssocResp from "MAC" (capab=0x421 status=0 aid=1)
[  160.320514] wlan0: associated
[  160.321931] sky2 eth0: disabling interface
[  160.327522] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  160.339924] sky2 eth0: enabling interface
[  160.344406] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  160.364987] sky2 eth0: disabling interface
[  160.378037] sky2 eth0: enabling interface
[  160.382479] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  163.131331] sky2 eth0: disabling interface
[  163.153815] sky2 eth0: enabling interface
[  163.158304] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  167.823158] wlan0: no IPv6 routers present
dave@dell-desktop:~$ 

NOTE "MAC"= my MAC Address.

---

### Post by pytheas22 on 2008-08-10
@Ichido,

Unfortunately I don't see anything in your dmesg output that explains why roaming mode won't work.  Mostly I wanted to see bachisanerd's dmesg, because I thought that might be useful.

I'm guessing that your roaming mode won't work because Network Manager is doing something wrong.  You may want to try using [wicd]("http://wicd.sourceforge.net") instead, which offers all the functionality of NM, but tends to work better in many cases.

---

### Post by jasonkirk2006 on 2008-09-06
> **pytheas22 said:**
>  
Unfortunately I don't see anything in your dmesg output that explains why roaming mode won't work.

I have a Dell with 3945. I'm also having the same difficulties. With the default installation of Hardy, one can see the dmesg output compaining about either "MAC is in deep sleep" or "insufficient output power" or even "microcode error". After kernel updates, dmesg output does not show anything useful. But ifconfig -a shows (at least in my case) that the MAC address of the wireless interface is ff:ff:ff:ff:ff. From that point, it never wakes up - be it rmmod or disable_hw_scan.

Now i tested Interpid, and in the current situation dmesg output is something like this:

```
$ dmesg | grep 3945
[   13.369736] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.369824] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   13.369949] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
[   13.370031] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.370120] iwl3945 0000:0b:00.0: setting latency timer to 64
[   13.370140] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
**[   13.377263] iwl3945: Error: saturation power is -1, less than minimum expected 40**
**[   13.377348] iwl3945: Invalid power index**
**[   13.377417] iwl3945: initializing regulatory failed: -5**
**[   13.378741] iwl3945 0000:0b:00.0: PCI INT A disabled**
[B][   13.378816] iwl3945: probe of 0000:0b:00.0 failed with error -5

```[/B]

And Interpid uses an updated iwl3945 module as seen below:

```
$ modinfo iwl3945
filename:       /lib/modules/2.6.27-2-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
**version:        1.2.26ks**
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     5C079549ABD48E07B20F3C7
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        mac80211,led-class,cfg80211,rfkill
vermagic:       2.6.27-2-generic SMP mod_unload modversions 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

```

It seems the problem will not be solved even in the next Ubuntu version (neither in other distros).

---

### Post by pytheas22 on 2008-09-06
Jasonkirk,

Yes, this seems to be a bug with the iwl3945 driver that's still unresolved, so unless it gets fixed in the next months, it will probably remain present in Intrepid, unfortunately.  There's a [bug report]("http://intellinuxwireless.org/bugzilla/show_bug.cgi?format=multiple&id=1651") that says that for some users, adding the noapic option to the grub boot menu solves the problem.  Try doing that (if you don't know how to edit grub, let me know).

This [Ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203329") also suggests some workarounds that you might want to try, although unfortunately there seems to be no concrete solution that works for everyone.

Your other option, of course, is to use ndiswrapper to drive your card instead of iwl3945.

---

### Post by jasonkirk2006 on 2008-09-06
Thank you, pytheas22.

I've been working on this issue for weeks! I've tried almost all the workarounds mentioned here and there, but as you said, no one was a real soltion.

I'm happy that someone confirmed that the problem is infact the driver, iwl3945 - not the kernel. At least i will not try to upgrade my kernel to latest versions from now on :)

I also had problems with the ndiswrapper, which resulted in some kernel panic messages or unbootable OS somehow.

Hope it will be solved before final release of Interpid!

---

### Post by pytheas22 on 2008-09-06
> I'm happy that someone confirmed that the problem is infact the driver, iwl3945 - not the kernel. At least i will not try to upgrade my kernel to latest versions from now on 

Actually, the iwl3945 driver is essentially part of the kernel (it's included in the mac80211 wireless stack, which has been merged into the kernel tree for I think the last year or so; see [http://linuxwireless.org/](http://linuxwireless.org/) for more information), so upgrading to a newer kernel could solve the problem, because it would give you a more recent release of the iwl3945 driver.  Once the iwl3945 developers fix the bugs, the fix should automatically be merged into the kernel (I know this can all be confusing if you're not familiar with the kernel development policies or the mac80211 wireless stack, and really you don't need to understand any of it as long as you know that upgrading the kernel could help to fix iwl3945 eventually.)

You might also want to try adding adding the noapci option to your boot menu, as mentioned above; that may fix the problem now.

---

