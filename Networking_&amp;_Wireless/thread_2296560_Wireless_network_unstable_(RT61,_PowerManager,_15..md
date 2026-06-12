---
title: "Wireless network unstable (RT61, PowerManager, 15.04)"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by ashley16 on 2015-09-26
I turn on computer. Log in. Wireless connection drops after two minutes. Unable to reconnect. (Spinning wheel on NetworkManager GUI, then it gives up).

OR, sometimes, I log in, and wireless cannot connect at all.

My wireless worked fine in Fedora 21 but I wanted to install fglrx which on Fedora is not simple.

modinfo rt61pci
```
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.kolicense:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FE55283B9821614A74CA3E3
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

nmcli -v
```
nmcli tool, version 0.9.10.0
```

dpkg -s network-manager | grep 'Version'
```
Version: 0.9.10.0-4ubuntu15.3
```

Other computers (OS X / Win7) are able to connect to wireless. No problems.

I'm trying some solutions. First is checking power management.

iwconfig
```
wlan0     IEEE 802.11bg  ESSID:""            Mode:Managed  Frequency:2.412 GHz  Access Point: 4C:09:D4:D0:99:0C   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:381  Invalid misc:908   Missed beacon:0
```

If I do
sudo iwconfig wlan0 power off

But, it automatically turns power management back on after a short time. How do I disable it permanently?

BTW at the moment I am using wicd as a workaround but it is flaky.
 
I turn on wicd by killing NetworkManager like this
sudo pkill -9 NetworkManager

And then
wcid-gtk

Sometimes wicd gives me

```
[  544.767978] wlan0: aborting authentication with 4c:09:d4:d0:99:0c by local choice (Reason: 3=DEAUTH_LEAVING)
```

And also this message comes up

dmesg
```
rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 2
```

I'm really confused and only want to have a stable Internet connection which I already had on a different Linux flavour :(

---

### Post by ashley16 on 2015-09-27
I've installed Mint 17.2.

Kernel version is different (3.16.0-38) and NetworkManager version is different (0.9.8.8).

Wireless works perfectly.

I've subscribed to a bug on launchpad describing a similar problem.

I'm satisfied with Mint. I may go back to Ubuntu if I'm confident that NetworkManager and kernel 3.19 won't make my connection unusable.

---

