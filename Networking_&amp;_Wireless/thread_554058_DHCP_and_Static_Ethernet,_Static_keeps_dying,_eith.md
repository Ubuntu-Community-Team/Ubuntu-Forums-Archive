---
title: "DHCP and Static Ethernet, Static keeps dying, either card"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Phoenix on 2007-09-18
Greetings folks,

I'm running Kubuntu Feisty with kernel 2.6.20-16-generic and I'm having problems with my network (well, not really sure whether to describe it as a problem with the network or the network cards, as you'll see shortly.)

My network interfaces are as follows, lo, eth0 and eth1. /etc/network/interfaces also lists eth2 ath0 and wlan 0 for reasons I do not understand (I dont have wireless on here I'm sure of that).

Overview: my network has 10 static IP addresses, one of those addresses goes to the NAT Router which assigns all the internal IP addresses via DHCP, I will refer to those addresses as internal. Several of the machines also have public IP addresses I will refer to those as external.

All of the machines on the network have internal connections, (of the form 192.168.1.x), the ones that need public IPs also have external connections. The machine in question has an external connection (eth1) and an internal connection (eth0).

The problem is that the connection for eth1 has somehow been dying. All connectivity via the interface stops, I can't ping things that would normally be routed through that card (for the sake of discussion lets say that my 10 public IP addresses are in the range 1.2.3.x)

Network transfers seem to take down the interface in particular. I was trying to transfer a large file (19GB) over an NFS share to another machine that has an external address via the external address and whenever I attempt this the transfer stalls, dies and then I can't get the connection to work again, even with "sudo ifdown eth1 && sudo ifup eth1" or "sudo /etc/init.d/networking restart".

I really don't know what to make of this and I've tried switching which card is external or internal (trying to determine if its a hardware thing) and the problem just plagues the other card instead. I rely on a lot of file transfers from network file servers so this is causing me quite a problem :(.

ktorrent (which opens some torrents from network shares) also seems to cause the interface to die. It hasn't happened in the past hour (this is a multiple times per day type of thing)  but when it happens again I can post any information needed. I know that something gives a code 2 on exit when I try to bring the interface back up and if memory serves it has to do with avahi-autoipd.

Anyway, any help someone could give would be greatly appreciated.

---

### Post by fjames on 2007-09-19
I am having basicly the same problem.

I have installed the LAMP server 6.06 on 3 PC's. All different hardware. I have the same issue on all the servers. **Periodically the server appears to stop listening on all ports.** I can not find any malfunction. Sometimes ifconfig shows that the static IP has changed to an IP issued by DHCP. I followed the instructions to the letter when configuring for static.

/etc/network/interfaces

auto eth1
iface eth1 inet static
address 192.168.20.100
netmask 255.255.255.0
network 192.168.20.0
broadcast 192.168.20.0
gateway 192.168.20.1

I also changed the DNS (resolv.conf).

All seems perfect. Then it stops. Downing and brining eth1 backup fixes the problem.

Frank

---

### Post by fjames on 2007-09-19
I have done a little more troubleshooting.  If there is a DHCP server availaible then the static IP gets replaced by it. It seems to happen once and hour on ny system.  If you put it on a network with no DHCP available then the static IP doesn't change. Although I have it configured for static if DHCP is available it will use it.

Frank

---

### Post by Phoenix on 2007-09-19
Ah!
Well, my static isn't on a connection where a DHCP can be reached, so it just stops working period. ifconfig still shows me having the address and the interface being up, but it cant ping anything and all the connections to that interface stop working. Have you been able to figure out a solution under that set of circumstances?
I'm glad someone's responded, I'm going mad here, lol.

---

### Post by fjames on 2007-09-20
No.  I'm leaning toward the Intel Pro 100 driver not liking the second NIC.  It seems to behave if the second NIC is disabled. It dosen't seem to matter what brand you use for the second NIC. I'm still not 100% sure it's stabled.  Reguadless, I still need to find a solution. I need the scond MIC.

You would think a lot more people would have seen this probem.

Frank

---

### Post by Phoenix on 2007-09-21
I'm wondering if a lot of people are and maybe we're all assigning different causes to it?

For me its a driver that's worked pretty much...always...built in NIC in on an ASUS M2N-E Deluxe.

I'm wondering, would it be good to do 
ifup -vv eth1 > ifupError 
and then post the resulting file that it creates? 

Forgive me if this post seems utterly insipid, running on 4 hrs sleep.

---

### Post by fjames on 2007-09-22
I may not have figured out what was causing this problem but I may have found the cure at least for me.  I updated my installation. It downloaded 108MB of updates. I rebooted and have been running without a problem. :)

---

### Post by Ovlov on 2007-09-22
I think I have the same problem.  If I do anything that sends a significant amount of data out of the network; my connection dies and I have to reboot to get it back.  Things that I have done that have taken my network down:
  bittorrent both Azureus and KTorrent (if I limit my upstream to 6 KB it seems to mitigate the problem)
  VNCing through ssh into my KUbuntu box from non local internet connection
  Watching a show hosted on my KUbuntu box through SAMBA on another computer.

I never had any problems on this same hardware with 3 years of Gentoo doing the same things.

I seem to be up to date, so I don't think that that is the problem.

Ubuntu 2.6.20-16.31-generic

---

