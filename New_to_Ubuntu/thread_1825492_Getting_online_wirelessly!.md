---
title: "Getting online wirelessly?!"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by varietas on 2011-08-15
Greetings, all!

I'm brand new to the world of Linux and I'm loving it so far... except for being able to connect wirelessly.

Here's my deal: I'm trying to get 11.04 to connect through a Ralink RT3090 Wireless 802.11n 1T/1R PCIe.

Enable Networking is checked under the network icon, but beneath that Enable Wireless is grayed out.  The indicator lights on my laptop tell me that wireless is enabled and the radio switch is on.

Please help me out!

Thanks :D

---

### Post by TeoBigusGeekus on 2011-08-15
Have you checked in the Hardware Drivers whether there is a proprietary drivers for your chip?
If there is one, connect your pc to your router with a udp cable, download them and install them.

---

### Post by varietas on 2011-08-15
running sudo lshw -C network gives me this

...driver=rt2800pci driverversion=2.6.38-10-generic-pae...

How do I know if this is proprietary or not?  If it is, will I need to use an NdisWrapper?

---

### Post by TeoBigusGeekus on 2011-08-15
Go to Administration>System>Hardware Drivers.
See if any drivers are listed there.

---

### Post by Bucky Ball on 2011-08-15
Welcome.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Third one on the list. Your card looks like it's up on this driver already though (you probably just have a setting wrong). Stay well away from Ndiswrapper. You shouldn't need it, 'specially for this card, and it is largely superseded.

Please give results of:

```
iwconfig
ifconfig
sudo lshw -C network
```*Full* result of the last one thanks. And as TeoBG mentioned, anything in System>Admin>Additional Drivers? ;)

---

### Post by varietas on 2011-08-15
I am using Unity, so I think the file path is a little different...

This is what I did:  Control Center>Hardware>Additional Drivers

The result I got lists only one proprietary driver (for a graphics card) that is already installed and running.  No other drivers were listed.

---

### Post by TeoBigusGeekus on 2011-08-15
Oh crap Unity...
...you did good never the less.
So, no proprietary drivers available for your card.
See Bucky Ball's post and post us the output of the commands he gave you.

---

### Post by Dan Again on 2011-08-15
I had a weird problem with wireless after doing a clean install of Natty. Tried a bunch of stuff and nothing worked. Finally I plugged my machine into a wired connection, ran all updates and installed all additional drivers and everything worked fine after that. Have you tried this?

---

### Post by Bucky Ball on 2011-08-15
> **Dan Again said:**
> ... I plugged my machine into a wired connection, ran all updates and installed all additional drivers and everything worked fine after that. Have you tried this?

? Exactly. ;)

But by the looks of it that card is up already on the wrong driver (not unusual) but perhaps not the greatest performance because of it. Post the output of the commands in my first post, please.

---

### Post by varietas on 2011-08-15
**iwconfig **gives me the following -

wlan0    IEEE 802.11bgn  ESSID:off/any
            Mode:Managed Access Point: Not-Associated  Tx-Power=20 dBm
            Retry Long limit:7  RTS thr:off  Fragment thr: off
            Power Management:off

**ifconfig** gives me -

wlan0    Link encap:Ethernet  HWaddr cc:af:78:40:6a:67
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 droped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

and **lshw -C network **gives me -

*-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0300.0
       logical name: wlan0
       version: 00
       serial: cc:af:78:40:6a:67
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic-pae firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:e0100000-e010ffff

---

### Post by varietas on 2011-08-15
I also haven't tried plugging into a wired connection just yet, as I don't have one readily available.

I would use the one here in the office, but the IT guys have been on the war-path lately.  Apparently using a personal device on the network will get you *fired*.

---

