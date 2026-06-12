---
title: "onboard network card fried?"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by olivine on 2008-07-06
There was a power outage due to a big thunderstorm last night, and now I have network problems. The computer was plugged into a surge protector (I wonder if damage can come through the LAN cable). 

Modem and cables work, and I didn't change anything in the system, so I *think* the onboard LAN is fried. A SMART LAN function in the BIOS detects a short (Pair7-8 status = short). The manual says that pairs7-8 are not needed for 100Mbps network, but it still doesn't sound too good.

My first question is: is there a way to run some checks to verify that the onboard LAN really is fried? The motherboard is a GA-G33-DS3R, the system is Gutsy Gibbon.

Second question: I have an old PCI ethernet card (Realtek RTL-8029). I plugged it in to try to get a network connection. I can't seem to get it to work. How can I check and/or install the right drivers for this card?

Thanks in advance for any help.

---

### Post by nixscripter on 2008-07-06
I don't know about diagnostics, but I can answer your second question.

I believe that the Realtek driver you want is in the mainline kernel. Ubuntu may even have compiled it. Try this: ```
modprobe 8390 ne2k-pci
``` And see if it shows up in **ifconfig**.

---

### Post by olivine on 2008-07-07
Thank you for your help. Typing "modprobe 8390 ne2k-pci" gives me:

```
eth1      Link encap:Ethernet  HWaddr 00:40:95:41:65:46  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:95ff:fe41:6546/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:44 txqueuelen:1000 
          RX bytes:5477192 (5.2 MB)  TX bytes:1403566 (1.3 MB)
          Interrupt:20 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:336 (336.0 b)  TX bytes:336 (336.0 b)

```

I'm not sure what it all means...

I should add that the realtek card doesn't work when I boot. If I type "sudo dhclient", then the net comes on (the lights on the modem seem to say it's only at 10MBs; not sure how to check that). The network works, but sometimes hangs after a while.

---

### Post by The incredible bulk on 2008-07-07
Don't worry about the lights on the modem. It's got a hardware limitation at 10mbps and really there's not much need to go over that for today's internet connections anyway.

About your adapter. My opinion is to have a large distrust of realtek cards, but I will try not to let that cloud my judgement.

It's been my experience that if you get as much traffic in and out as the previous screen shows you can NOT look for a software issue. It will be hardware, either your modem, your ethernet cable, or your ethernet card.

Since the data at this point seems to suggest that your card is working as it should I would try a quick swap out of your ethernet cable. Especially since you're getting a pin 7-8 error.

Also about the power surge you suspect. It's a very good thing to have a computer on a surge strip.. even better to have it on a UPS. But still surges CAN COME IN on the cable (coaxial) and then hit the modem next, and last stop would be the computer's nic..... Just a thought... it really could be your modem. Hate to confuse you.

---

