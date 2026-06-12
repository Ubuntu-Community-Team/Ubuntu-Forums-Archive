---
title: "Lost ALL network connections after Edgy Upgrade. Please Help."
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by maxvonseibold on 2006-11-07
Can anyone please help me. I (foolishly) upgraded my g4 powerbook from dapper to edgy the other night. 

After the upgrade the network seemed fine but when I rebooted I cannot connect to a single thing, even my router 
on 192.168.0.1 ... 

I have to say that I find networking extremely hard but I know I am runing DHCP and the network wizard thing says that this is running. 

I ran the following commands below and I am pretty certain that 'route' should show something but I have no idea what. 

Could anyone please offer me some advice. Surely if DHCP is up and running things should be fine..... ... . :( 


Thanks. 


Max. 



Output begins: 



max@orchard:~$ netstat -r
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
max@orchard:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:93:AE:33:DA
          inet6 addr: fe80::20d:93ff:feae:33da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2376 (2.3 KiB)  TX bytes:1836 (1.7 KiB)
          Interrupt:41 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

max@orchard:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
max@orchard:~$
max@orchard:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
max@orchard:~$

---

### Post by mitch.c on 2006-11-07
DHCP may be running on your network, but it sure doesn't look like eth0 has an IP address. Post contents of /etc/network/interfaces. For dhcp, it should look something like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
You'll need to make sure that dhcpcd or dhcp3-client is installed.

To update interface configuration do this:
```
$ sudo ifdown eth0
$ sudo <editor-of-your-choice> /etc/network/interfaces  # tweak as you wish
$ sudo ifup eth0
```

---

### Post by stream303 on 2006-11-13
> **maxvonseibold said:**
> 
max@orchard:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
max@orchard:~$

Aha.  No ISP nameserver's listed.  I'd be tempted to place the isp's primary and backup nameservers in your router setup page.

OR, you could force /etc/resolv.conf to contain those addresses (and stay that way!) with:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Let's see if this works...

---

### Post by mips on 2006-11-13
> **stream303 said:**
> Aha.  No ISP nameserver's listed.

Uhm, I think you are putting the cart in front of the horse here. He does not even have a IP(v4) Address yet !

---

### Post by stream303 on 2006-11-13
Ooops!  You are quite right - no cart or horse! :)

Looks like IPV6 addresses only?  I've never seen that before...

---

### Post by Iowan on 2006-11-13
I have an Edgy workstation that sometimes does/not get a DHCP address on bootup (but DOES get the ipv6 address).  Usually, a ```
dhclient
``` from a terminal will get it an address.  It's currently working - dunno if it was because I commented out all the other unused interfaces that seem to come default in Edgy's **/etc/network/interfaces** file.

---

### Post by stream303 on 2006-11-14
hmmm.. I was just looking through the **dhclient-script** file and noticed a sleep 1 statement in the PREINIT section.  I wonder if it's a timing issue that could be solved by a sleep 2 instruction?

I'm definitely not this low-level savvy, but it did pique my curiosity..

---

### Post by maxvonseibold on 2006-11-20
dhclient worked! 

Thankyou so much! 


Not sure if it will continue to when I reboot. Will find out soon......

---

