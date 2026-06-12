---
title: "USB WIFI not fully recognized Ubuntu 18.04"
date: 2019-09-24
forum: Networking &amp; Wireless
---

### Post by callapa1 on 2019-09-24
Hello.

So I got the TPLINK TL823N V2 and after some struggling I managed to make it work but there's still some information missing that makes me doubt. Also when I set the device in monitor mode (with airmon-ng) it can actually do it but my laptop gets troubles when I try to quit monitor mode.

when I use lsusb it shows:

> 
Bus 001 Device 002: ID 8087:8000 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 2357:0109  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


with the device 004: ID 2537:0109 missing. I'm not sure what that means but I guess it has no controller.

also when I use iwconfig:

> wlx503eaa229777  IEEE 802.11bgn  ESSID:"bib-gast"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 6E:3B:6B:19:63:9F   
          Bit Rate:300 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/100  Signal level=-68 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


wlp7s0    IEEE 802.11  ESSID:"bib-gast"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 6E:3B:6B:19:63:9F   
          Bit Rate=60 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:315   Missed beacon:0

which means the device catches internet. I double-checked it by putting my internal wifi to monitor mode and connecting to a network from the usb and it works.

there's also many differences between both wifi devices when I use lshw -C network:

>   *-network                 
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 83
       serial: a0:88:69:86:8a:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-29-generic firmware=17.948900127.0 ip=172.20.5.217 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:48 memory:b3700000-b3701fff


  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:2
       logical name: wlx503eaa229777
       serial: 50:3e:aa:22:97:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192eu ip=172.20.5.56 multicast=yes wireless=IEEE 802.11bgn

ALSO, when I use airmon-ng I get:

> 

[TABLE="width: 500"]
[TR]
[TD]PHY[/TD]
[TD]Interface[/TD]
[TD]Driver[/TD]
[TD]Chipset[/TD]
[/TR]
[TR]
[TD]phy0[/TD]
[TD]wlp7s0[/TD]
[TD]iwlwifi[/TD]
[TD]Intel Corporation Wireless 3160 (rev 83)[/TD]
[/TR]
[TR]
[TD]phy1[/TD]
[TD]wlx503eaa229777[/TD]
[TD]???????[/TD]
[TD][/TD]
[/TR]
[/TABLE]







driver says '??' and Chipset is empty

Finally, when I try to quit monitor mode by using airmon-ng stop wlan0mon , I get this message:

> 
##USING Y##

Found phy1 with no interfaces assigned, would you like to assign one to it? [y/n] y



 ERROR adding monitor mode interface: command failed: Device or resource busy (-16)


PHY    Interface    Driver        Chipset




ethtool failed...
Only mac80211 devices on kernel 2.6.33 or higher are officially supported by airmon-ng.

##USING N##

Found phy1 with no interfaces assigned, would you like to assign one to it? [y/n] n
PHY phy1 will remain lost.


PHY    Interface    Driver        Chipset




ethtool failed...
Only mac80211 devices on kernel 2.6.33 or higher are officially supported by airmon-ng.







this won't let me use my device again. If I try to set my pci wifi device on monitor mode I can do it, but when I try to quit monitor mode, the same message will be displayed, even if I'm working on the other device, which will force me to reboot.

thanks in advance

---

