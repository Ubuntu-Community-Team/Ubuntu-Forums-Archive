---
title: "No wireless anymore no matter which card"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by supremedalek on 2008-05-29
I have a Dell Latitude D600 running ubuntu 7.10. Originally it came with a Broadcom minipci card whose performance was a bit on the bleah side: it worked but was slow both to connect and to transfer. Also, sometimes it would disconnect if I did not keep doing something like pinging nonstop. I replaced it with an Atheros card and it worked like a champ. Also, I had a Prism2 usb card and sometimes used both at the same time, namely to check if a given wireless AP I set up would work with different brands. Later on I was playing with kismet on the prism2 card without a hitch. 

One day it stopped working. By that I mean first the prism card is reported by dmesg to be there but I cannot put it to work. Second, even though I can see the atheros card through ifconfig or iwconfig, it will report there are no available networks out there.  And when I try to manually connect to, say, my home network it will fail.

```
raub@monaco:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth3      radio off  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
vmnet8    no wireless extensions.
 
vmnet1    no wireless extensions.
 
raub@monaco:~$
raub@monaco:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:e0:85:c7
       width: 64 bits
       clock: 66MHz                                                             
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5702-v2.25 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:48:39:5d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
raub@monaco:~$
raub@monaco:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)                                                                              
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
raub@monaco:~$         
raub@monaco:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      radio off  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

raub@monaco:~$                                                                                   
raub@monaco:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      No scan results

vmnet8    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

raub@monaco:~$                                        
```

I also tried putting back the broadcom card and even an intel minipci card I had doing nothing and no cookie. What else should I check?

---

### Post by supremedalek on 2008-05-29
Out of the blue I decided to try my ancient Orinoco gold card. It worked. So, out of 3 minipci cards, 1 usb wireless thingie, and one pcmcia card, all of different chipsets, one works in this machine.

---

### Post by wdaniels on 2008-05-29
> **supremedalek said:**
> ath0      radio off

That won't help for starters - assuming it's not just an oversight, have you changed anything to do with the power management on this laptop recently (i.e. ACPI)?

---

### Post by supremedalek on 2008-05-31
> **wdaniels said:**
> That won't help for starters - assuming it's not just an oversight, have you changed anything to do with the power management on this laptop recently (i.e. ACPI)?

You know, your suggestion helped a lot.  As you suspected, the wireless was off for whatever reason. I too was confused for the reason -- I have not touched the power management in the laptop for quite a while -- so then decided to check what was happening on the bios. While there I turned the wireless on. I do not know why that happened but at least now I have wireless; I am using it right now to send this. Now, if I just could find out who is wifi0 I would be golden.  


Thanks for the help!

---

