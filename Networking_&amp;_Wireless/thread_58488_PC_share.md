---
title: "PC share"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by pwaustin on 2005-08-20
I am trying to connect to the internet via my NIC connected to a XP computer which is connected to a ADSL connection.  I have a dual boot with 2000 and can share the internet connection fine in 2000.  But in Kubuntu, I cannot even ping the XP computer and it cannot ping mine.  I figure that when they can connect to each other, the internet will work.  

Here is my ifconfig output,

```
 
eth0
Link encap:Ehthernet  HWaddr 00:02:3F:B4:CB:69
inet addr:192.168.0.31 Bcast:192.168.0.255  Mask:255.255.255.0
inet6 addr: fe80::202:3fff:feb4:cb69/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
RX packets:20 errors:0 dropped:0  overruns:0  frame:0
TX packets:56 errors:0 dropped:0  overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3492 (3.4 KiB)  TX bytes:5890 (5.7 KiB)
Interrupt:17 Base address:0x4000

lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets: 8  errors:0  dropped:0  overruns:0  frame:0
TX packets:8  errors:0  dropped:0  overruns:0  carrier:0
collisions:0 txqueuelen:0
RX bytes:788 (788.0.b)  TX bytes:788 (788.0.b)

```

and the route output

```

Kernal IP routing table
Destination           Gateway         Genmask      Flags      Metric     Ref   Use Iface
192.168.0.0            *              255.255.255.0    U            0            0        0   eth0
default                192.168.0.1       0.0.0.0          UG          0            0        0   eth0

```

I'm new at this so any help is much appreciated!

---

### Post by heimo on 2005-08-20
Is your XPs IP-address (on the inside, LAN, interface) 192.168.0.1? Do you connect with crossover cable? Are the green ACT leds on both network cards (and possiblle switch) lit?

---

### Post by pwaustin on 2005-08-20
Hi,

Yes, XP's IP address is 192.168.0.1.
Yes, I connect with a crossover cable.
Yes, both green lights are lit.

---

### Post by heimo on 2005-08-20
Wel... not many clues to follow. On the dualboot Windows side, you can ping the XP? (No firewalls blocking?) And are you using same IP addresses on both Windows and Ubuntu on that dualboot computer?

Well... this is a very long shot, but if you have no other ideas.. try disabling ipv6 (link is to Warty forum but applies to Hoary as well):
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

If that doesn't help: if this is available for install (on CD or otherwise):
[http://packages.ubuntu.com/hoary/net/nmap](http://packages.ubuntu.com/hoary/net/nmap)

Type:
 ```
sudo apt-get install nmap
sudo nmap 192.168.0.1

``` 
What do you get?

---

### Post by pwaustin on 2005-08-21
Thanks, I disabled the ipv6, but still nothing when I ping the XP computer.  How would I go about installing nmap?  I can download it and then put it on an external hard drive, but how do I tell ubuntu to install it?

Also, could there maybe be a problem with my NIC and linux?  I have a Realtek rtl8139 and have read that these should be okay with linux.  

Or maybe there is some network setting that I don't have right?  Because I have also tried connecting directly with my modem through the NIC (eth0) which didn't work, so I then tried through my USB port (eth1) and ran pppoeconfig for each of these connections, but it couldn't configure it.  So I am wondering if there is someway to check if there is some other problem?

Thanks again for your help, hopefully I'll get this working...

---

### Post by heimo on 2005-08-21
Looks like a dead end, what could be wrong? Can you install ethreal [http://www.ethereal.com/](http://www.ethereal.com/) on your XP, put it running (listening on the network card your Ubuntu box is connected), and ping from Ubuntu - and then on XP. You can forget that nmap if it's not on install CD (not worth the trouble).

---

### Post by pwaustin on 2005-08-21
ok, installed ethereal and did as you said. I ran a capture and pinged the XP computer and then pinged from the XP computer.  So what do I do now?  What am I looking for?

---

### Post by heimo on 2005-08-21
[QUOTE=pwaustin]ok, installed ethereal and did as you said. I ran a capture and pinged the XP computer and then pinged from the XP computer. So what do I do now? What am I looking for?[/QUOTE]

Packets from the other computer. You should see data going to two directions - back and forth, ping-pong. No? It's mysterious, if it's not happening. Am I forgetting something? Do you see NIC leds blinking when pinging?


 ```
lsmod | grep 8139

```  8139too, 8139cp?

---

### Post by pwaustin on 2005-08-21
yeah, the lights blink when I ping.

Here is what I got from lsmod | grep 8139

```

8139cp           19200  0
8139too          24320  0
mii                   4736  2 8139cp,8139too

```

---

### Post by heimo on 2005-08-21
Run dmesg | less just after boot and search relevant lines. Pay attention to IRQs and lines with eth, 8139 and so on. You could try to toggle BIOS settings for P'n'P OS (if it's enabled, disable). :-/ :-\ You could also attach /etc/network/interfaces file and output of cat /proc/interrupts.

---

### Post by pwaustin on 2005-08-21
Ok, change of events here.  I went into Samba and changed the Security Level to Share, and now the XP computer can see my computer in My Network Places. I can also see the XP computer in Konqueror.  Neither computer can ping each other though and when I click on my computer from the XP, it says that my computer is not accessible and I might not have permissions to see it.  Is there somewhere in Samba to set permissions?  Is there some default firewall that I don't know about that could be blocking this?

---

