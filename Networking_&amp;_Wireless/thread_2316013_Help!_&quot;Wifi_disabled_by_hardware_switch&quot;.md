---
title: "Help! &quot;Wifi disabled by hardware switch&quot; on lenovo t430s"
date: 2016-03-04
forum: Networking &amp; Wireless
---

### Post by buttery-toast on 2016-03-04
Just bought this laptop so It's got a fresh install of ubuntu 15.10. I've been trying for hours to get wifi working.  Ive tried every solution I can find online and nothing has made any change at all. Even tried booting linux mint since it uses an older kernel and maybe has other changes to wifi drivers(?) but no difference. There's also theres no bluetooth but I'm not worried about that ATM.

Obviously tried the physical wifi switch, disabling kernel modules and god knows what else. I'm far from being a linux expert though.


Heres the output of $ rfkill list all

 > 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


 and $ sudo lshw -c Network

> $ sudo lshw -c Network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: 3c:97:0e:73:b9:c1
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:6080(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 34
       serial: 84:3a:4b:60:8b:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-16-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f1c00000-f1c01fff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:1.1
       logical name: enx000ec6817901
       serial: 00:0e:c6:81:79:01
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=192.168.2.219 link=yes multicast=yes port=MII speed=1Gbit/s



---

### Post by jeremy31 on 2016-03-04
Please post the result for ```
lsmod | grep ideapad
```

---

### Post by buttery-toast on 2016-03-04
the command doesn't display anything.

edit:  Figured out why, it's a thinkpad rather than an ideapad. :) 

here's the output of $ lsmod | grep thinkpad


> lsmod | grep thinkpadthinkpad_acpi 86016 1
nvram 16384 1 thinkpad_acpi
snd 81920 18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
video 40960 2 i915,thinkpad_acpi




---

### Post by jeremy31 on 2016-03-04
You may want to check out [https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T430s-Wireless-Switch-Issue/td-p/1447259](https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T430s-Wireless-Switch-Issue/td-p/1447259)

It could be ribbon cable issue with the switch

---

### Post by buttery-toast on 2016-03-04
Thanks, I'll try that. Really hope it's something that simple :D

---

### Post by jeremy31 on 2016-03-04
Me too since the ideapad-laptop module isn't being used.  If it used that module I could change the source code so that your model wouldn't have the hard block

---

### Post by buttery-toast on 2016-03-04
> **jeremy31 said:**
> You may want to check out [https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T430s-Wireless-Switch-Issue/td-p/1447259](https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T430s-Wireless-Switch-Issue/td-p/1447259)

It could be ribbon cable issue with the switch

oh my good god that actually fixed the wifi. I can not believe that was the problem! 

Thank you very much for your help :D

---

