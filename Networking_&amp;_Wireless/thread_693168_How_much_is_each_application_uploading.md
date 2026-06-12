---
title: "How much is each application uploading?"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Levander on 2008-02-10
gnome-system-monitor says my computer is uploading a lot right now. What's the easiest way to tell how much each program is uploading?

---

### Post by jetsam on 2008-02-10
Nethogs does this.  It doesn't collect stats afaik, but it tells you what's happening in the moment-- how much each process is sending or receiving.  

It's in the universe repository.  

Install with:
```
sudo apt-get install nethogs
```

Run with:
```
sudo nethogs
```

---

### Post by Levander on 2008-02-10
Neat little program.

My problem with it is that I'm using virtualbox and virtualization to run Windows XP.  As is common in virtualizaton environments, I'm using a bridge that divides all traffic between my machine's eth0 and the tap0 for XP to use inside it's vm.  Linux doesn't have ip addresses for either eth0 or tap0.  

I can't attach nethogs to either eth0 or tap0 because they don't have ip addresses.  When I attach it to the bridge (device named bridge0) I'm apparently only getting the network traffic for eth0, and it's ignoring tap0 - so I have no idea how much network traffic is being put out by XP.

Well, at least I know the problem is in XP.  But, it would be nice to see this information explicily and not just something I've surmised by the absense of being able to see the problem anywhere else...

Is there another way to view network traffic, program by program, in Gutsy?

E.g., I'm thinking I should be able to see that the program virtualbox (the name of the virtualization program) is using a lot of network traffic.  Which I know it is, I just can't see it in nethogs (my guess for why is in the problems listed above).  I want to see how much traffic the virtualbox program is using.

---

### Post by jetsam on 2008-02-10
> Is there another way to view network traffic, program by program, in Gutsy?

I don't know of one personally, but there likely is...  

Bridged networking I know almost nothing about.  I have VirtualBox working in NAT mode, and nethogs works pretty much like you'd expect it to-- it shows VirtualBox as a single process and reports its network usage.    

does 
```
sudo nethogs tap0
```
work?  You can specify a device interface by name.

Added:  oops just read your last post more closely.  I'm stumped...  Maybe someone else here, or the Virtualization forum...

---

### Post by Levander on 2008-02-10
When I try that, I get this:

```

levander@louis:~$ sudo nethogs tap0
ioctl failed while establishing local IP
levander@louis:~$ 

```

I think it's because there's no IPv4 address for tap0.  The output of 'ip addr':

```

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever
3: tap0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 500
    link/ether 00:ff:7c:6b:57:42 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::2ff:7cff:fe6b:5742/64 scope link 
       valid_lft forever preferred_lft forever
4: bridge0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc noqueue 
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.63/24 brd 192.168.0.255 scope global bridge0
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever

```

Do you have an IPv4 address for your tap0?

---

### Post by jetsam on 2008-02-10
No, no...  I don't even have a tap0.  Sorry I confused you.  It works for me with VirtualBox using NAT networking, not bridged...  I was speculating that specifying the interface might work for you.  Then I saw that you'd already tried that...

I was just looking at iptraf.  It's another network monitor, that _may_ do better with the bridged interfaces.  It doesn't break things down by process, but since all you really want is confirmation that the vbox interface is busy, you might try it out.

I'm not sure if it's installed by default, but it's in the main repository.  You can run it with **sudo iptraf**, then try "general interface statistics."

---

