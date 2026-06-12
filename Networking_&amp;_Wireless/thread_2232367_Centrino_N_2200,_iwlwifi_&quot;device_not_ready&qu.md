---
title: "Centrino N 2200, iwlwifi &quot;device not ready&quot;"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by asgawer2 on 2014-07-01
I got my Thinkpad T430 two months ago and this is the second time I've had this issue. The first time I just did a wild copy/paste of every suggested solution, none of them worked. I took the opportunity to upgrade to Mint 17 (14.04/Trusty), but the problem was still there. I believe it worked again after a full dist-upgrade, but here I am again, all upgraded with the same problem. What happened both times is: The wifi works as expected. I shut down, come home from work, turn on the laptop and get "device not ready." I guess there is a software update that causes it, I don't see how I can have done any damage involuntarily. I don't have Windows or any physical switch. Fn+F5 works, the message goes from "device not ready" to "Wi-Fi is disabled."

```

########## wireless info START ##########

##### release #####

Distributor ID:    LinuxMint
Description:    Linux Mint 17 Qiana
Release:    17
Codename:    qiana

##### kernel #####

Linux xiaohaier 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwldvm                232285  0 
mac80211              626489  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

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
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.38
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

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

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
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

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     03CC0BBD2BE23C16DB062DC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
*snip lots of similar alias lines*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

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

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0891 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[  202.884632] iwlwifi 0000:03:00.0: Could not complete ALIVE transition: -5
[  202.885008] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
[  202.885069] iwlwifi 0000:03:00.0: Unable to initialize device.
[  202.886824] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  202.894320] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[  202.940598] iwlwifi 0000:03:00.0: Command COEX_PRIORITY_TABLE_CMD failed: FW Error
[  202.940608] iwlwifi 0000:03:00.0: Could not complete ALIVE transition: -5
[  202.940982] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
[  202.941071] iwlwifi 0000:03:00.0: Unable to initialize device.
[  202.941537] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
*snip similar lines*
[  224.656063] iwlwifi 0000:03:00.0: Command COEX_PRIORITY_TABLE_CMD failed: FW Error
[  224.656073] iwlwifi 0000:03:00.0: Could not complete ALIVE transition: -5
[  224.656451] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
[  224.656540] iwlwifi 0000:03:00.0: Unable to initialize device.
[  224.656947] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  224.664449] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
 [COLOR=#000000]########## wireless info END ############[/COLOR]
```

---

### Post by asgawer2 on 2014-07-02
One more piece of possibly useful information: I think I upgraded the *linux-firmware* package before the reboot. I postponed upgrading it for a while because I suspected it was the source of my troubles the last time, but I eventually upgraded. Not 100% that't the culprit, but I believe* /lib/firmware/iwlwifi-2000-6.ucode *is not on good terms with the hardware.

---

### Post by chili555 on 2014-07-02
Let's start by seeing:```
ls -al /lib/firmware | grep 2000-6.ucode
```We'll see if the file exists, has the proper permissions, size, etc.

My linux-firmware is up to date and I get:> -rw-r--r--  1 root root  695876 Jun 12 11:48 iwlwifi-2000-6.ucode

---

### Post by asgawer2 on 2014-07-02
```
 ls -al /lib/firmware | grep 2000-6.ucode
-rw-r--r--  1 root root  695876 Jul  2 20:23 iwlwifi-2000-6.ucode

```

I have also downloaded and compared with the one from [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm), and the files are identical. The late timestamp is because I tried renaming other *.ucodes, but I gave up and renamed the original again.

---

### Post by chili555 on 2014-07-02
Waaaa! Why do they give all the hard ones to old Chili?! 

I have Googled this extensively. One of the steps I'd be tempted to try is to use the older firmware, however, I can't find it anywhere.

Another thing that is tempting is to see what parameters, if any, you have in iwlwifi.conf. If you haven't any, I'd try 'options iwlwifi bt_coex_active=N.' If, on the other hand, the parameter is already there, I'd check to see if it is malformed and correct it. I might also try removing it altogether to see if it changes anything.

Next, I'd compile the latest backports-3.16-rc1-1 package and see if it changes the errors.

Finally, grasping at straws and trying any and everything that is the least bit possible, I'd check the hardware to see if the card is correctly seated and the antenna wires are firmly connected.

That's it! That's all I've got!

You seem pretty adept, but if you need specific steps to do any of this, post back and I'll be happy to help.

---

### Post by jeremy31 on 2014-07-02
I will try to help Chili on this one since you are using LM 17.  I would start by using mint-update(Update Manager), click view and select Linux Kernel.  This should show you a few kernels available and the option to install them below.  Select install on the version with the highest version number, mine shows 3.13.0-29 as the most recent.  I am not sure, but I don't think any changes are made on the intel ucodes without them changing the version number.. and it seems that 2000-6 is the one that has been around since the 3.2 kernel but for whatever reason it fails to load as your dmesg log should read something about loading firmware version 18.168.6.1 and then selecting a rate control algorithm

---

### Post by chili555 on 2014-07-02
> mine shows 3.13.0-29 as the most recent.Indeed. That's why I suggested he compile backports-3.16-xx. It provides, not the firmware, but a possibly newer iwlwifi driver in case this is a driver vs. ucode problem. It's hard to tell, since the version for newer and older is stated in *modinfo* as 'in tree:'.

Quite a number of the Google hits for the dmesg errors involve Intel devices in the 2xxx series.

---

### Post by asgawer2 on 2014-07-03
Thanks a lot to both for help!

I did a fresh install (just because), but that didn't help either. Hardware problem? So I don't have the latest linux-firmware package.

```
ls -al /lib/firmware/iwlwifi-200*
-rw-r--r-- 1 root root 695876 Mar  5 22:45 /lib/firmware/iwlwifi-2000-6.ucode
```



```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

Deleting it didn't solve the problem, neither did *options iwlwifi bt_coex_active=N. *(I didn't look for any other changes caused by those two actions.)

> **chili555 said:**
>  I'd compile the latest backports-3.16-rc1-1 package and see if it changes the errors.

Yes, I've been looking around and that seemed like an option. But this

> **jeremy31 said:**
> Select install on the version with the highest version number, mine shows 3.13.0-29 as the most recent.

seemed to be slightly faster, so I did that first :)

And ... great success with 3.13.0-29-generic.

My current *linux-firmware* package is 1.127, I don't know if the newest version, 1.127.4, caused all this. (Yes, I have amd64.)

The changelog says:

> linux-firmware (1.127.4) trusty; urgency=medium

  * Remove amd64-microcode for licensing reasons.
    The amd64 microcode is not suitable for packaging in main since
    the license does not allow modification or disassembly. Install
    the multiverse package amd64-microcode instead which also contains
    initramfs hooks.
    -LP: #1181145



So I had 1.127 and 3.13.0-24 at some point before the fresh install and the wifi worked perfectly fine. Same versions after the fresh install and wifi didn't work at all :?

>  [COLOR=#000000]I'd check the hardware to see if the card is correctly seated and the antenna wires are firmly connected.[/COLOR][COLOR=#000000]

Yes, I was pretty close to this. Talked myself out of it since the wifi was perfectly stable both times until the software upgrade and subsequent reboot. [/COLOR]

---

### Post by chili555 on 2014-07-03
This > great success with 3.13.0-29-generic....and the marking [SOLVED] suggests you are all set. Is that the case?

---

### Post by asgawer2 on 2014-07-03
> **chili555 said:**
> This ...and the marking [SOLVED] suggests you are all set. Is that the case?

Yes. I don't fully understand what the problem was or exactly how/why it was solved, but the wifi is working now. Very useful help in this thread, thanks again!

---

