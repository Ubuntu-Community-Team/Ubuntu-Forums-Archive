---
title: "[Lubuntu] Wifi not working"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by alex1984 on 2014-09-22
Hi guys, I got an Acer Aspire One AO751h.

It's a very weak machine and I found that the only distro that runs decently is Lubuntu.

Unfortunately, I got a disastrous problem with it, it doesn't recognize ANY wireless. Internet only works through Ethernet cable.
Wireless seems to be totally absent from the network menu, it doesn't pick up ANY signal at all and doesn't include "wireless" among the various options, just "Ethernet".
Any ideas on how it could be fixed ?

Keep in mind that im a linux newbie ;)

---

### Post by slickymaster on 2014-09-22
*Moved to the ***Networking & Wireless*** sub-forum.*

Please follow the link below for downloading a script and running it. Then post its output, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by alex1984 on 2014-09-22
Thanks for the help!


Ok, first of all I noticed that while the OS loads, an error message briefly appears that goes roughly like this:
"Error: you must go to *some very long web address with words like wireless and kernel* to download the correct...."

it's very fast and I couldn't read it fully.

Anyway, here's the  report:
```

########## wireless info START ##########

Report from: 22 Sep 2014 15:13 CEST +0200

Booted last: 22 Sep 2014 15:02 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0244]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   356470  0 
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  1 acer_wmi
video                  18903  2 acer_wmi,gma500_gfx
ssb                    51854  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe28:5397/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12187041 (12.1 MB)  TX bytes:672836 (672.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
    DNS:             62.101.93.101
    DNS:             83.103.25.250

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   16.605845] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   16.648358] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   17.257901] b43 ssb0:0: Direct firmware load failed with error -2
[   17.257916] b43 ssb0:0: Falling back to user helper
[   17.260893] b43 ssb0:0: Direct firmware load failed with error -2
[   17.260907] b43 ssb0:0: Falling back to user helper
[   17.402773] b43 ssb0:0: Direct firmware load failed with error -2
[   17.402785] b43 ssb0:0: Falling back to user helper
[   17.416907] b43 ssb0:0: Direct firmware load failed with error -2
[   17.416921] b43 ssb0:0: Falling back to user helper
[   17.423807] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   17.424535] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   17.425241] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############


```

Should I run the scrip or not?

---

### Post by praseodym on 2014-09-22
You need this firmware file:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by alex1984 on 2014-09-22
> **praseodym said:**
> You need this firmware file:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

Thank you gentlemen, it works now! :p

---

### Post by Mike_Walsh on 2014-09-22
Just out of curiosity, had you RIGHT-clicked the Network Applet....or just left-clicked?

The normal one-piece menu in Ubuntu, has been split into 2 smaller menus in Lubuntu. Thw 'wi-fi' options are on the smaller right-click menu.

In my case, they don't show anyway.....not unless I plug my wi-fi adapter in. THEN they will appear.

Most of the time, I use Ethernet.....much faster.

Regards,

Mike.

---

### Post by alex1984 on 2014-09-22
> **Mike_Walsh said:**
> Just out of curiosity, had you RIGHT-clicked the Network Applet....or just left-clicked?

The normal one-piece menu in Ubuntu, has been split into 2 smaller menus in Lubuntu. Thw 'wi-fi' options are on the smaller right-click menu.

In my case, they don't show anyway.....not unless I plug my wi-fi adapter in. THEN they will appear.

Most of the time, I use Ethernet.....much faster.

Regards,

Mike.

I tried both left and right and it showed the wired connection only.

---

### Post by Mike_Walsh on 2014-09-22
Probably sounds crazy when I tell you I sometimes use a wireless adapter on a desktop, doesn't it?
It's because I have an ancient Dell Inspiron 'lappie'.....13 years old! It will NOT work with a wifi adapter; and I've tried several over the years.

So it's Ethernet or nothing; and if I want both machines online at the same time, it's Ethernet in the Dell, and wifi on the PC...

Fortunately, my TP-Link TL-WN725N works with this machine AND the entire 'buntu 'family'.....with NO problems. (At least, it does since the 3.13-0.33 kernel update, back in July...)

I only asked, because it took ME a little bit by surprise when I first found out there WERE two menus!


Regards,

Mike.

---

### Post by varunendra on 2014-09-24
Welcome to the forums alex1984!

Please mark the thread as **[SOLVED]** now that it is (using "**Thread Tools**" link above the top post). It helps other by indicating that the thread contains a possible solution to the problem mentioned in the title.

Oh, and just for the future, make sure NOT to install the proprietary driver that the "Additional Drivers" program may suggest/offer. The current one that praseodym got working is better for your card. :)

> **Mike_Walsh said:**
> ..I have an ancient Dell Inspiron 'lappie'.....13 years old! It will NOT work with a wifi adapter; and I've tried several over the years.
Wow! I wonder if modern hardware can keep working that long. :p

But 13 years old probably means USB 1.1 ports, which itself is a dead-end for most (perhaps 'All') USB wifi dongles. As far as I understand, USB wifi adapters can't work at anything below USB 2. Whether this laptop has one, can be checked with the output of "lsusb"; or better - "lsusb -t" when the device(s) is/are connected to the port(s).

---

### Post by Mike_Walsh on 2014-09-24
Hi, varun.

No; it DOES have USB 2.0 ports, but for some crazy, crazy reason, I've never been able to make a wifi adapter work on it; ve-e-ery mystifying. However, it's only a basic backup machine in case the desktop ( a **10 **yr-old Compaq Presario!) should decide to go wrong, so.....I don't tend to worry too much about it; the Presario occupies most of my time, as it's my main workhorse. It's got the old single-core Athlon 64 (one of the best of the single-core CPUs, in my humble opinion.)

I've yet to find anything that it won't do; and I've thrown plenty at it, believe me. At this moment (I'm in Zorin as I write this), it's got GIMP open in one workspace, Skype open in another ( a mate is sending me quite a large file from over 'the Pond'), and I'm listening to streaming radio in a third.....with nary a hiccup (and the CPU load is currently about 55% )..! Perhaps I've just got a good one; but if I'd tried this in XP, she would have been struggling!

Regards,

Mike.

BTW; if you ever get a chance to look at one, you'll find that the older Dell laptops were built like tanks! They might have used some very strange hardware combinations over the years, but in those days they DID build them to last. (I only replaced the battery pack for the first time 2 years ago....)

---

### Post by alex1984 on 2014-09-25
> **varunendra said:**
> Welcome to the forums alex1984!

Please mark the thread as **[SOLVED]** now that it is (using "**Thread Tools**" link above the top post). It helps other by indicating that the thread contains a possible solution to the problem mentioned in the title.



Done, thank you.

---

