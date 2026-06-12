---
title: "share dsl (speedtouch usb) with a XP box"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by FFighter on 2007-05-28
Hello all!

This is my first post in this forum as you might see. I'm using Ubuntu (Feisty) for a few days and I'm loving the experience so far, both in terms of fun and learning. 

However, I've been breaking my head on how to share my adsl connection with my sister's XP (SP2) machine. When I had XP, I used the native XP internet connection sharing.

My modem isn't a router and I don't have a router or hub either. I've got a speedtouch usb (Alcatel) modem. It was already pretty hard to set it up to work under ubuntu, but I learned a lot in the process :)

I strictly followed this tutorial: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) but couldn't make it to work... :(

Here's the output of my ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:CE:ED:C2  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fece:edc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28857 errors:1 dropped:0 overruns:0 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2740565 (2.6 MiB)  TX bytes:68262 (66.6 KiB)
          Interrupt:18 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:26:54:13:3B:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16372 (15.9 KiB)  TX bytes:7508 (7.3 KiB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:783705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:783705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52680890 (50.2 MiB)  TX bytes:52680890 (50.2 MiB)

nas0      Link encap:Ethernet  HWaddr 00:90:D0:2E:B9:A2  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:d0ff:fe2e:b9a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152638 errors:167543 dropped:0 overruns:167543 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83134124 (79.2 MiB)  TX bytes:18388156 (17.5 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:201.2.243.61  P-t-P:200.138.242.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:157391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:81874330 (78.0 MiB)  TX bytes:24477380 (23.3 MiB)



```

eth0 is the card which is connected to the XP box.

After executing all the steps on the article I mentioned, I couldn't get my ubuntu box to ping XP neither XP to ping ubuntu. 

After trying to redo the tutorial many times without success, I thought I would install dhcp and try again. Here's the contents of my dhcpd.conf:

```

# dhcpd.conf 
# Dynamic DNS updates disabled.  (Note, this does not affect things like dyndns.org) 
# ddns-update-style none; 
 
# Lease times, in seconds 
default-lease-time 600; 
max-lease-time 7200; 
 
# Subnet definition.
subnet 192.168.0.0 netmask 255.255.255.0 { 
        # Range to configure via DHCP 
        range 192.168.0.11 192.168.0.254; 
 
        # This is the authoritative DHCP server for this network. 
        authoritative; 
 
        # IP address of the router. 
        option routers 192.168.0.20;
 
        # IP addresses of the DNS servers (ISP; see /etc/resolv.conf) 
        option domain-name-servers 192.168.0.20;
}

```

The dhcp assigned 192.168.0.50 to the XP machine.

And here comes an interesting thing: When I try to ping the XP machine (192.168.0.50), I get the following output:

```

root@marcelo-desktop:/home/marcelo# ping 192.168.0.50
PING 192.168.0.50 (192.168.0.50) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable
From 192.168.0.1 icmp_seq=4 Destination Host Unreachable

```

Why is it trying to ping 192.168.0.1?

Trying to ping 192.168.0.20 from the XP machine doesn't work either.

If someone could help me, I would be grateful.

Marcelo.

---

### Post by FFighter on 2007-05-29
Anyone? I really need some help here... :(

---

### Post by FFighter on 2007-05-29
Please, let me know if you need more informations about my system!

---

### Post by StevenHarper on 2007-06-04
Hi I have made  Speedtouvh Manager to Make Speedtouch modems work 

you can get it from here

[https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

and if you need any help post here 

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Steve

---

