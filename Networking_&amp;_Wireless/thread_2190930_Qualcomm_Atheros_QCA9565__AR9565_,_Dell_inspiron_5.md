---
title: "Qualcomm Atheros QCA9565 / AR9565 , Dell inspiron 5537 wir&#1077;less problems"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by brick2 on 2013-11-30
I can not get my wirless to work at all, my hardware specs are bellow, if anyone could shed some light on this matter please.

[FONT=Arial][FONT=Arial]Dell Ispiron 5537
Ubuntu 12.04 LTS - 64 bit
Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

I am using Wicd etwork mannager.


[/FONT][/FONT]

---

### Post by varunendra on 2013-12-01
Firstly, if using wicd instead of the default Network Manager didn't work any better, I'd recommend to install Network Manager again -
```
sudo apt-get install network-manager-gnome
```
and purge wicd -
```
sudo apt-get purge wicd
```
..and reboot.

Then, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by kethella on 2013-12-05
I have the same problem. Every method posted in threads about similar problems did not work.
My output from wireless script:
```

*************** info trace ***************

***** uname -a *****

Linux kethella 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:16:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05eb]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8800M Series] [1002:6823]

***** lsusb *****

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:58c2 Realtek Semiconductor Corp. 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

ath9k                 133095  0 
mac80211              555272  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399752  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cfg80211              208382  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Automatyczne po&#322;&#261;czenie ethernetowe] ------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-i915-hsw.conf]
blacklist i915_hsw

***** modinfo *****

filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     2739A66454A502EC7DA66D6
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     1673D73171C827FC143E431
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 

filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     06D67ED7F5AB5AC7BD2B944
depends:        ath
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8C339DF4D303827C9304BB0
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****


****************** done ******************


```

---

### Post by varunendra on 2013-12-06
Welcome to the forums kethella !

The wireless card you have is pretty new in the market and the driver for it is still under development. The newer versions of the driver ath9k include support for the card, so you can try either upgrading your kernel or the whole OS, or try a backported driver instead.

If it is a fresh install (doesn't look like though, from the lsb_release vs kernel version), it is best to download 12.04.3 and do a fresh install. The point release 12.04.3 comes with kernel version 3.8 which supports your wireless card.

Else, you can try the latest backported driver on your current installation. Do the following if you decide to go with this option -

[indent]Before compiling the driver, make sure you have necessary support packages installed. To do so, open a terminal (Ctrl-Alt-T) and install/reinstall the following (while being connected to internet using your cable connection) -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Now download, compile and install the driver as follows -
1) Download the latest backported driver package from here - [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

2) Copy the downloaded tar.bz2 package to your Ubuntu Desktop > Right-click > Extract here.

3) Open a terminal and run the following commands one-by-one (if you are trying a version different than "3.13-rc2-1" change the name "backports-3.13-rc2-1" accordingly)-
```
cd Desktop/backports-3.13-rc2-1
make defconfig-ath9k
make
sudo make install
```

4) Reboot for the newer driver to take effect.[/indent]

..and let us know the result after trying this.

**PS:**
If you decide to do a fresh install of 12.04.3 or later, I recommend to download the ISO via torrent to ensure the integrity of the download, and do not forget to test it in Live mode first to make sure it works well with your hardware. Official link to torrent downloads : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by brick2 on 2013-12-06
```

*************** info trace ***************

***** uname -a *****

Linux whatever 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:16:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05e9]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]

***** lsusb *****

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 04f3:0034 Elan Microelectronics Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0c45:64ad Microdia 
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 004: ID 05d5:8001 Super Gate Technology Co., Ltd 
Bus 002 Device 005: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath3k                  12969  0 
bluetooth             212001  25 bnep,rfcomm,ath3k,btusb

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search Home

***** blacklist *****

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
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.5.0-44-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     5C844657111492DE4FF295C
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*
depends:        bluetooth
intree:         Y
vermagic:       3.5.0-44-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****


****************** done ******************
```

This is the output sorry for the late raplay.
Thank you for your time.

---

### Post by varunendra on 2013-12-06
No problem with the delay, I'm not very fast either. :)

You have exactly the same card and same kernel as kethella, hence my suggestions are also the same for you too.

Just try what I suggested to kethella in my previous post.

---

### Post by brick2 on 2013-12-06
The drivers you recommended seam to function, my wireless is up and running, I 'll mark the post as solved soon, but if I could just ask you before I do.
 Can I use wicd network manager instead as I have had some problems with gnome network manager in the past, when I do the upgrades, it somehow breaks him, there were some suggestion that I should black list  some components which are  related to the gnome network manager in order to prevent it from breaking.  
 This was on my old laptop, but if you could shed some light on the matter, if not o well I thank you for your time and effort the post will be marked as solved tomorrow or in a couple of hours, depends how you look at it.

---

### Post by varunendra on 2013-12-06
Glad to know it works. :)

> **brick2 said:**
> Can I use wicd network manager instead as I have had some problems with gnome network manager in the past
Sure you can. If it is working better than NM, or if you are having problems with NM, there is no reason why you shouldn't try an alternative connection manager, and Wicd has a good reputation as an alternative to NM.

I haven't seen Network Manager break any packages or other functionality, and am not aware of any serious bug about it. So I would be interested to know the details of the problem you were having, and possibly help/advise if I could. Although based on my personal experience, I think it might have been something abnormal with your previous installation and this one shouldn't cause such any issues. But again, there is no reason why you can't use Wicd instead if you trust it more.

---

### Post by brick2 on 2013-12-06
Thx for all your help. This is an amazing forum!

---

### Post by varunendra on 2013-12-06
You're most welcome ! :)
> **brick2 said:**
> This is an amazing forum!
Indeed !

I hope the solution works for kethella too, as well as others who may find this thread later, facing the same situation.

---

### Post by zeusrock1 on 2013-12-07
Thanks Varun, your post solved my wireless problems on my Dell Inspiron 15, 3521!  I have the same wireless card and did a fresh install (12.04) using the iso from the dell/ubuntu approved devices page.  Just need to explore if my fan is running correctly, seems to run more than is needed.

---

### Post by varunendra on 2013-12-07
I'm so pleased to hear that. Thank you for the feedback. :)
It helps us offering a solution with more confidence next time, or improve it if required.

---

### Post by kethella on 2013-12-09
My wireless is working now. Thanks for the help, Varun.

---

### Post by varunendra on 2013-12-09
No problem. Hope you'll enjoy Ubuntu and the forums too ! :)

---

### Post by Conrad_Landicho on 2014-02-13
Hello, Varun,
I'm having the same problem on a new DELL Inspiron 15R/5537, and I've already installed  Ubuntu 12.04.3.   I already ran the wireless-script, but the output is way too big ... how can I display it here? 
Please advice.   Thanks in advance for your help ...

Regards,
-Conrad

---

### Post by Mk147 on 2014-03-29
[B]hey varu,

thanx so much for your help, my wifi is working fine now:D, this is what happened (reference to anyone will read this)
[/B][TABLE="class: outer_border, width: 500"]
[TR]
[TD]Now download, compile and install the driver as follows -
1) Download the latest backported driver package from here - [http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/%7Emcgrof/rel-html/backports/")

2) Copy the downloaded tar.bz2 package to your Ubuntu Desktop > Right-click > Extract here.

3) Open a terminal and run the following commands one-by-one (if you are  trying a version different than "3.13-rc2-1" change the name  "backports-3.13-rc2-1" accordingly)-
 	Code:
 	cd Desktop/backports-3.13-rc2-1
make defconfig-ath9k
make
sudo make install 
4) Reboot for the newer driver to take effect.
[/TD]
[/TR]
[/TABLE]
[B]
thanx again;)

[/B]

---

### Post by varunendra on 2014-03-30
You're welcome Mk147! :)

---

### Post by Anny_Hsu on 2014-05-31
Hi Varun, I tried your method, get the new driver but the wireless still doesn't work and keep popping up to ask for password. 
The following is the result of wirless-info Any suggestion? Thanks!

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux AnnyHsu-Inspiron-5437 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 005: ID 04f3:003d Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:64af Microdia 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 05ac:12a8 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 eth1
172.20.10.0     0.0.0.0         255.255.255.240 U     1      0        0 eth1

##### resolv.conf #####

nameserver 172.20.10.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR17:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    resnetx:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    MegNet:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    WIN-UOHVR7HHC93-98800: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    JOSH:            Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 11 Mb/s, Strength 22
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    HP-Print-D8-Deskjet 3510 series: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12
    resnetx:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    resnetx:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise

- Device: eth1  [&#26377;&#32218;&#32178;&#36335;&#36899;&#32218; 1] -----------------------------------------
  Type:              Wired
  Driver:            ipheth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.10.5
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1

    DNS:             172.20.10.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR17"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007aa03826e6
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00094E4554474541523137
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010AA0E08D0B5BFC3F823CCC71ABB1A5B641021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d01a27e48
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000053aefc197
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000099de76783d
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b9567cadd
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ec2a761e8
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004cee24180
                    Extra: Last beacon: 340ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000099d5dc4180
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000126ade4180
                    Extra: Last beacon: 912ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040807
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c69f8c1c11
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e0a36917f
                    Extra: Last beacon: 380ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010c5b4ac180
                    Extra: Last beacon: 380ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"resnetx"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d0b5f8180
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 00077265736E657478
                    IE: Unknown: 01088C1298A4B048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040807

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### lsmod #####

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath3k                  13318  0 
bluetooth             395423  23 bnep,ath3k,btusb,rfcomm
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626511  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211

##### modinfo #####

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BAF225EEB618908380B28DA
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    9.047055] ath9k 0000:06:00.0: enabling device (0000 -> 0002)
[    9.047244] ath: phy0: Set BT/WLAN RX diversity capability
[    9.053917] ath: phy0: Enable LNA combining
[    9.055031] ath: EEPROM regdomain: 0x60
[    9.055031] ath: EEPROM indicates we should expect a direct regpair map
[    9.055032] ath: Country alpha2 being used: 00
[    9.055033] ath: Regpair used: 0x60
[   16.100865] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.104135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.291698] wlan0: authenticate with <MAC address removed>
[   51.311388] wlan0: send auth to <MAC address removed> (try 1/3)
[   51.315866] wlan0: authenticated
[   51.322663] wlan0: associate with <MAC address removed> (try 1/3)
[   51.329832] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[   51.329882] wlan0: associated
[   51.329894] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.333861] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   66.291645] wlan0: authenticate with <MAC address removed>
[   66.311693] wlan0: send auth to <MAC address removed> (try 1/3)
[   66.313852] wlan0: authenticated
[   66.314803] wlan0: associate with <MAC address removed> (try 1/3)
[   66.319486] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[   66.319533] wlan0: associated
[   68.326392] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   85.467863] wlan0: authenticate with <MAC address removed>
[   85.487337] wlan0: send auth to <MAC address removed> (try 1/3)
[   85.489237] wlan0: authenticated
[   85.490552] wlan0: associate with <MAC address removed> (try 1/3)
[   85.505768] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[   85.505850] wlan0: associated
[   87.511292] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  119.771578] wlan0: authenticate with <MAC address removed>
[  119.791310] wlan0: send auth to <MAC address removed> (try 1/3)
[  119.795906] wlan0: authenticated
[  119.798291] wlan0: associate with <MAC address removed> (try 1/3)
[  119.804980] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[  119.805023] wlan0: associated
[  121.810543] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  584.656069] wlan0: authenticate with <MAC address removed>
[  584.675015] wlan0: send auth to <MAC address removed> (try 1/3)
[  584.677808] wlan0: authenticated
[  584.678076] wlan0: associate with <MAC address removed> (try 1/3)
[  584.683640] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[  584.683689] wlan0: associated
[  586.700366] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  891.732889] wlan0: authenticate with <MAC address removed>
[  891.752066] wlan0: send auth to <MAC address removed> (try 1/3)
[  891.754078] wlan0: authenticated
[  891.755177] wlan0: associate with <MAC address removed> (try 1/3)
[  891.760181] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[  891.760225] wlan0: associated
[  893.771579] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

########## wireless info END ############

```

---

### Post by praseodym on 2014-05-31
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by varunendra on 2014-05-31
My first suggestion would be same as what praseodym suggested above.

If it doesn't help, please follow the instructions in the following post to download and run a new (experimental) version of wireless_script, and post back its report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

