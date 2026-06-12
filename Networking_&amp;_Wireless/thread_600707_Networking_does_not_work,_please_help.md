---
title: "Networking does not work, please help"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by WinterWeaver on 2007-11-02
Hi everyone,

KK, i've been using Ubuntu a little over a year now. and I always seem to have the same problem. Tried sooo many things and followed many threads... but nothing works.

ok... some info.
>> I'm running Gutsy.
>> I have Roaming Mode enabled in Network Manager and I can connect to the internet fine with this setting.
>> If I change from Roaming to DHCP or anything else, I cannot connect to the internet at all, and it seems as if I'm not even getting a IP.
>> Other PC's can see me on the network, but not access anything (but this does not bother me atm).
>> PROBLEM >> I cannot see anyone else if I open up Networking.
>> When I go; Places >> Connect to Server, and put in their IP's, It does not connect to them. I CAN ping them with success.

ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:32:C9:97  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe32:c997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74384165 (70.9 MB)  TX bytes:6487595 (6.1 MB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6172 (6.0 KB)  TX bytes:6172 (6.0 KB)

```

netstat -r:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.254   0.0.0.0         UG        0 0          0 eth0

```

need anything else?

---

### Post by Lambert on 2007-11-03
If you can ping them, get on internet, and other machines can connect to you then your network stack is working fine.

the question will be what kind of share are you trying to connect to? a windows share, nfs share, etc.... Sounds like you need to configure something to connect and authenticate with that machine.

---

### Post by WinterWeaver on 2007-11-04
Thanks for the reply :)

It's Windows and Mac shares which I'm trying to connect to.

Previously, on Feisty, I did not really configure anything. I just clicked 'Places >> Network' and from there I could connect to the shares and copy to/from them.

I already have Samba installed. I didn't configure a samba password, cause it's not necessary for others to access my shares. I just need to get onto their machines.

any ideas?

---

### Post by froy02 on 2007-11-04
I do not know why you have to remove roaming mode when it works better.  But here's a link that would guide you in setting up networking:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I could not make my nic see the internet either after I change it manually. but I never tried to reboot to see if that would work. 

Froy

---

