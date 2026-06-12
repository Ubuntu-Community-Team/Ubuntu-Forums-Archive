---
title: "behind a router but not able to get online"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by geek_overlord on 2007-09-19
I recently installed Kubuntu 7.04 and I've had lots of trouble getting online. the details: The realtek chip on my mobo was recognized upon installation and the ip address was discovered. Since I connect through the router (which has dhcp enabled and handles the dns server) this seems odd. How can it know my ip address if I can't even ping yahoo,google etc?  In the gui I have a notification that a network cable is unplugged which I assume is due to the router issue. Can anyone shed some light on this? 

Oh btw my wife has no problem connecting with her windows laptop and the network cable worked just fine until I installed Kubuntu. I have not switched it out but I suppose I could if necessary.

---

### Post by noob12 on 2007-09-19
Can you post the output of these
```

route -n

cat /etc/resolv.conf

host www.google.com

```

Also post the result of pinging your router and an address outside (by IP, not name) like, for example this one that resolved from [www.yahoo.com](www.yahoo.com) in my area:
```

ping 209.131.36.158

```

If you can get outside but can't resolve hostnames, it suggests issues with your DNS servers, or the DNS proxy in your router.

---

### Post by geek_overlord on 2007-09-19
I'll try to get that info however I'm having trouble reading text files from kde in windows. I was told in another forum that I should just rename it .txt however that's not working. I'm downloading open office so I might be able to read docs from linux on my wife's windows machine. I'll post shortly.

---

### Post by noob12 on 2007-09-19
> **geek_overlord said:**
> I'll try to get that info however I'm having trouble reading text files from kde in windows. I was told in another forum that I should just rename it .txt however that's not working. I'm downloading open office so I might be able to read docs from linux on my wife's windows machine. I'll post shortly.

Use wordpad not notepad to see Unix-line termination properly in Windows

---

### Post by geek_overlord on 2007-09-19
I tried that as well. Same problem. I don't see the note/wordpad equivlent in kubuntu so I pasted the text to an open office document. Any suggestions?

---

### Post by noob12 on 2007-09-20
In KDE, I think it would be called kate, but you can post whatever you have, I'll try to read it.

---

### Post by geek_overlord on 2007-09-20
OMG as if it didn't take long enough to get this text into windows. Thanks for sticking with me through this. Here's the output of the commands you gave me:

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E                                                              xpress Gigabit Ethernet controller (rev 01)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 2305
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step                                                              ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-                                                               <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at ac00 [size=256]
        Region 2: Memory at fddff000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>

stormking@stormking-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
stormking@stormking-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
stormking@stormking-desktop:~$ cat /etc/resolv.conf
nameserver 4.2.2.1
nameserver 4.2.2.2
stormking@stormking-desktop:~$ host [www.google.com](www.google.com)
;; connection timed out; no servers could be reached
stormking@stormking-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.5.134 icmp_seq=2 Destination Host Unreachable
From 169.254.5.134 icmp_seq=3 Destination Host Unreachable
From 169.254.5.134 icmp_seq=4 Destination Host Unreachable
From 169.254.5.134 icmp_seq=6 Destination Host Unreachable
From 169.254.5.134 icmp_seq=7 Destination Host Unreachable
From 169.254.5.134 icmp_seq=8 Destination Host Unreachable
From 169.254.5.134 icmp_seq=10 Destination Host Unreachable
From 169.254.5.134 icmp_seq=11 Destination Host Unreachable
From 169.254.5.134 icmp_seq=12 Destination Host Unreachable
From 169.254.5.134 icmp_seq=14 Destination Host Unreachable
From 169.254.5.134 icmp_seq=15 Destination Host Unreachable
From 169.254.5.134 icmp_seq=16 Destination Host Unreachable
From 169.254.5.134 icmp_seq=18 Destination Host Unreachable
From 169.254.5.134 icmp_seq=19 Destination Host Unreachable
From 169.254.5.134 icmp_seq=20 Destination Host Unreachable
From 169.254.5.134 icmp_seq=22 Destination Host Unreachable
From 169.254.5.134 icmp_seq=23 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
413 packets transmitted, 0 received, +309 errors, 100% packet loss, time 412037ms
, pipe 3
stormking@stormking-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Hope it helps.

---

### Post by noob12 on 2007-09-20
So, actually you don't have an address assigned on that interface,  You did not get one assigned from the router, and you can't ping your router.   So you'll need to resolve those issues.

Let's start at the beginning.  First check that you have link detected on the ethernet card.
Type this command
```

sudo ethtool eth0

```
No need to post the whole thing.  Just look for the "Link detected:" line.  If it says "no", you have more fundamental issues.  If it says "yes", you should first try to configure an address manually and see if you can ping the router.

Use the **System | Administration | Network ** menu,  Click **Wired Connection**  and Properties.  Disable roaming mode if it is checked.  In the **Configuration** pulldown select "Static IP Address" and enter the ip address 192.168.1.50 subnet mask 255.255.255.0 and gateway address 192.168.1.1.  Hit OK and Close.

Now try pinging your router at 192.168.1.1.  I'm hoping you're right about the router address, because I based all of the address configuration on that.

---

### Post by geek_overlord on 2007-09-20
Sounds good. I can't do that right now as I'm on the way out the door to work. When I get in this afternoon I'll do that right away. Thanks again for sticking with me on this. BTW I think your name belies your skill. Maybe someone should change that for you.:)

---

### Post by noob12 on 2007-09-25
You can probably run with that manual configuration, but that was really just to see if you could get basic connectivity.  PM me if you need more help, as I'm no longer watching this thread.

---

