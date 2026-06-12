---
title: "Networking with Firewire"
date: 2005-08-29
forum: Networking &amp; Wireless
---

### Post by kleptonin on 2005-08-29
Hello, I have just installed Hoary Hedgehog 5.04 and have come across a problem. We have a two-PC network, which until recently used Ethernet with a crossover cable. I recently switched from using Ethernet to using a 6-to-6 pin Firewire crossover cable. This setup works fine in Windows XP. However, Ubuntu does not seem to recognise a network connection present. There is no physical networking device present, as I have disabled my onboard LAN chipset, leaving just the PCI Firewire card. It does however see the Firewire card.

Is there any way of establishing a network connection between Ubuntu and Windows using only Firewire?

Thanks.

---

### Post by pmjdebruijn on 2005-08-29
Hi,

You need to load the 'eth1394' kernel module, like this:

```
sudo modprobe eth1394
```

Then if it works, you can add it to your '/etc/modules' file, to be loaded automatically at boot.

Regards,
Pascal de Bruijn

---

### Post by kleptonin on 2005-08-29
This did the trick! I'm posting this reply from inside Ubuntu.

Many thanks!

---

### Post by vtec on 2005-08-29
Just wondering, but why use FW over Ethernet??

---

### Post by kleptonin on 2005-09-01
It lets me transfer files between the computers at up to 400Mbps. I hope.

---

### Post by pmjdebruijn on 2005-09-02
Hi,

Well, 400Mbps will probably be hard to attain... But it should be way faster then 100BaseT...

But when used a lot, I'd recommend getting an el'cheapo GigE network card. Realtek 8169s32 cards are going for 15 euro's these days...

Regards,
Pascal de Bruijn

---

### Post by The Keeper on 2005-10-17
I am also a firewire network user. However, I was not able to get it to work by adding the eth1394 module to /etc/modules. FireWire network connection is available and I can manually assign IP-address and subnet, just like I did under WinXP. I can even see that the two computers are sending and receiving some packets. However, I cannot even get ping through from either PC.

It is quite unfortunate if this requires recompiling the kernel, as then I will be without automatic kernel updates...
Please, anyone know how to get this to work without kernel recompile?

This was an older thread about the subject, even though I did install 5.10 rather than 5.04, I thought this would be more proper way to approach.

---

### Post by samat on 2007-08-21
Good day!
 Same thing - I do 
```
modeprobe eth13944
```
- there is ethX for firewire card and I assign everything I need but only the thing i see is "dropped" count getting more in ifconfig out:
```
eth2      Link encap:UNSPEC  HWaddr 00-02-3F-99-29-51-0C-0C-00-00-00-00-00-00-00-00  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:422 overruns:0 frame:0
          TX packets:198 errors:3 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:21670 (21.1 KiB)

```
ping:
```
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
From 10.0.0.1 icmp_seq=1 Destination Host Unreachable
From 10.0.0.1 icmp_seq=2 Destination Host Unreachable
From 10.0.0.1 icmp_seq=3 Destination Host Unreachable
```

Any ideas, please...

---

### Post by efil vasers on 2007-12-08
I'm having the same problem as samat.
The device appears and I can assign it an IP/netmask, but it can't reach other computers.
I've been trying this with 3 computers (all running Gutsy) and they all have the same problem.

---

### Post by samat on 2007-12-09
> **efil vasers said:**
> I'm having the same problem as samat.
The device appears and I can assign it an IP/netmask, but it can't reach other computers.
I've been trying this with 3 computers (all running Gutsy) and they all have the same problem.

I found that problem can be solved only by recompiling kernel with built-in fire-wire support. It was impossible to get networking via firewire using kernel modules at the time it tried to (a few months ago)... :(
Maybe with Gutsy 7.10 situation has been changed, I don't know...
(post information about your investigations here, if you'll find it, please)

---

