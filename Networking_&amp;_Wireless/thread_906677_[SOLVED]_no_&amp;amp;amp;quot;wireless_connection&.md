---
title: "[SOLVED] no &amp;amp;amp;quot;wireless connection&amp;amp;amp;quot; option in manual configuration"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by jimmgunnz on 2008-08-31
okay... backstory.

so i already know that my wireless card is a nightmare.  it's the 4311 broadcom guy.  every time i get b43 installed, through the fw_cutter method, my system locks up directly after login.  so, i needed to do a modprobe -r b43 from a failsafe terminal to get my system back up and it lets me back in.  

however, in all of my attempts, i definitely used modprobe -r broadcom, and i think it uninstalled my wireless card.  so, there is no recognition, and there is a lack of a "wireless connection" option in my network manager.

basically i am at like square -1 in my wireless setup.  if anyone wants to help me at least establish my wireless card detection, that would be amazing.  i'll start another thread about actually getting wireless after i can establish detection.

i'll post any output upon interest.... thanks in advance, and apologies if this is ABT or if this is in a lot of other threads!!

---

### Post by jimmgunnz on 2008-08-31
ps...
 sudo pccardctl ident
Socket 0:
  no product info available

yikes, huh??

---

### Post by jimmgunnz on 2008-08-31
alright... i tried installing ndiswrapper and did get the "wireless connection" option, but when i restarted, my system locks up again... right after login.  the system starts then freezes, almost looks like it wants to show an error message (it almost looks like a negative of the american flag, weird).  but does absolutely nothing.

so, i needed to go to failsafe terminal again, go modprobe -r ndiswrapper to get myself back in, then removed ndiswrapper promptly.

am i just doomed here??  it's really seeming kind of grim.  i don't understand why it keeps locking up... only when it's networking.  even if i have an ethernet cable plugged in when the system is starting up... it locks.  networking makes it lock...

any ideas at all??  or just one of those buggy 8.04 situations with the broadcom cards?

---

### Post by vishalrao on 2008-08-31
if you're using ndiswrapper have you added the following lines to /etc/modprobe.d/blacklist file?

blacklist ssb
blacklist b43
blacklist b43legacy

you might even need to provide a kernel boot option such as "nolapic" which you can add to /boot/grub/menu.lst where you see the line for KOPT - dont uncomment it, just add nolapic to the list and see if that helps...

PS: it helps if you post details such as your laptop model and output of dmesg/lspci etc...

---

### Post by jimmgunnz on 2008-08-31
hi... thanks... i do have the blacklist file, with those entries.  and at this point i've uninstalled ndiswrapper, so i'm starting from scratch.  sorry, i'm never sure what type of output to provide, so i just let people ask for something specific..

i see the KOPT reference you were making.... so i just add nolapic at the end of each of those lines like below??  sorry if i'm moronical...

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro nolapic
##      kopt_2_6_8=root=/dev/hdc1 ro nolapic
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro nolapic
# kopt=root=UUID=d5805dd5-279d-4ed7-88ba-77b3f62bf0dc ro nolapic


also... no file or directory was found for dmesg, but...

lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

does any of that help at all??  what other kind of output can i provide??  thanks again for the help!

---

### Post by jimmgunnz on 2008-09-01
interesting.  so... i've got ndiswrapper working right now.  writing this message wirelessly in fact.  however, as soon as i restart, i KNOW i will have an issue with my system locking up..... but at least i have it working now!!

lshw -C network:
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ba:60:bf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:dd:7b:57
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,11/02/2005, 4.10.4 ip=192.168.1.101 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by jimmgunnz on 2008-09-01
yep, i called it.  i restarted and my system locked up.

BUT....

i now have a method down.  and my wireless is working.  with ndiswrapper.

since my system keeps locking up, i need to disable ndiswrapper before logging in.  so, i go to a failsafe terminal and enter 
        sudo modprobe -r ndiswrapper
and then go and log in as normal.  once logged in safely, i re-enable ndiswrapper.  

then i need to go to my manual configuration.  i saved the settings for my own home network, as well as the settings for "roaming" mode.  i need to toggle between roaming and my home network, then it works.

the most ridiculous resolution ever, but i now have working wireless.  i just need to figure out how to make this a smoother transition!

weird huh??

---

### Post by jimmgunnz on 2008-09-01
yupp!!  it's official.  i have wireless.  i need to go through all of those steps i mentioned above, but it really does work, each time.  there's got to be an easier cleaner way though, doesn't there??  

or should i just count my lucky stars that i am able to achieve wireless at all??  i dunno... but wireless stories and adventures are fun?!

---

