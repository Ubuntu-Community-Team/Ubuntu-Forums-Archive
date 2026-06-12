---
title: "not recognising wireless card and can not find in lists"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by simonfoley on 2007-03-04
I am a first time installer of Ubuntu and I am having a real uphill struggle with my wireless card. My laptop has the following Wireless Lan Card

NetVision IEEE 802.11b
Wireless LAN CardBus Card

I have looked everywhere for whether this device is supported but it seems that this quite a rare card and therefore it is hard to find information.

I can not even get Ubuntu to recognise that I have the card plugged in.

I have done a search at [https://help.ubuntu.com/community/Wi...ingGuide#check](https://help.ubuntu.com/community/Wi...ingGuide#check)
and it is not recognised at all. I also followed the guide and had a go at each of the stages.

I tried google and got nothing of help. I have Ubuntu 6.10 installed and everything else seems to be working fine.

Any ideas of the stages I should go through? As maybe is a BUS problem.

I tried to run lspci -v | grep subordinate

and got the information that I should maybe add

pci=assign-busses

to my kernel boot line?

I am not so linux minded and do not know how to do this or even if I am heading in the correct direction.

However, I am not even convinced that this could be problem. Any ideas of this card?

Simon

---

### Post by simonfoley on 2007-03-05
Anyone?  Should NDIS Wrapper work even though the pc does not recognise the card?

S

---

### Post by simonfoley on 2007-03-05
[I]00:00.0 Host bridge: ALi Corporation M1621 (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:13.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)[/I]

When I run lspci this is what I get.  No sign of the card at all.  Interestingly, I have a D-Link ethernet card in now and it working perfectly.  The only bum note is that I am sat next to the phone and wireless router in the hall way :confused:

If I run

ifconfig I get

[I]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
[/I]

---

### Post by simonfoley on 2007-03-06
Anyone?

---

### Post by FIONEX on 2007-03-06
I'm assuming that's an old laptop if it has the wireless B class card.  If it has a windows driver, then the NDIS wrapper should make it work once it is detected.  BTW, just because it's not in PCI, that doesn't mean it's not detected.  It could be built onto the motherboard.  You will probably get more help in the hardware forum.

---

