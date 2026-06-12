---
title: "Cant seem to get a new DHCP release"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by sickdude on 2005-10-11
ok i have a problem and its here since this morning, yesterday i was browsing te web like any other. but when i booted the computer this morning i could not get on the web. so i browsed trough the forum but i cant seem to find the awnser.

anyway i think its because dhclient3 doenst give me a new ip number, i booted up windooowz and it works fine and i get a different ip number. from other topics i read that there where a few command to run to check if everything is ok. here is the output

```
root@megatron:/home/sickdude # dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:0b:6a:d1:33:2e
Sending on   LPF/eth0/00:0b:6a:d1:33:2e
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 145.116.11.254
bound to 145.116.8.52 -- renewal in 206874 seconds.

root@megatron:/home/sickdude # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:D1:33:2E
          inet addr:145.116.8.52  Bcast:145.116.11.255  Mask:255.255.252.0
          inet6 addr: fe80::20b:6aff:fed1:332e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:721626 (704.7 KiB)  TX bytes:12664 (12.3 KiB)
          Interrupt:23 Base address:0xd800

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:113131 (110.4 KiB)  TX bytes:113131 (110.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::145.116.8.52/96 Scope:Compat
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@megatron:/home/sickdude # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
145.116.8.0     *               255.255.252.0   U     0      0        0 eth0
default         145.116.11.254  0.0.0.0         UG    0      0        0 eth0
root@megatron:/home/sickdude # ping google.com
ping: unknown host google.com
root@megatron:/home/sickdude #

```

---

### Post by mlomker on 2005-10-11
Looks like you have an IP address but there's something wrong with the DNS server entries that your DHCP server is dishing out.  Take a look at the /etc/resolv.conf file and see if the DNS server addresses are correct.  You can check what you are getting in windows by opening a command prompt and typing **ipconfig /all**.

---

### Post by sickdude on 2005-10-11
C:\Documents and Settings\sickdude>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : metalmini
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : dekey.nl

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : dekey.nl
        Description . . . . . . . . . . . : VIA Compatable Fast Ethernet Adapter

        Physical Address. . . . . . . . . : 00-0B-6A-D1-33-2E
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 145.116.9.187
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . : 145.116.11.254
        DHCP Server . . . . . . . . . . . : 145.116.11.254
        DNS Servers . . . . . . . . . . . : 192.87.106.106
                                            192.87.36.36
        Lease Obtained. . . . . . . . . . : Tuesday, October 11, 2005 3:32:14 PM

        Lease Expires . . . . . . . . . . : Sunday, October 16, 2005 3:31:14 PM

C:\Documents and Settings\sickdude>


resolv.conf 
search dekey.nl
nameserver 192.87.106.106
nameserver 192.87.36.36

this looks fine to me 

when ubuntu is booting it wants to sync with ntp.ubuntu...... this gets the error no name resolution

this might help or not...

anyway i hope that we can figure this out very fast because i dont want to boot windows anymore

---

### Post by mlomker on 2005-10-11
> this looks fine to me 


I agree, it all looks fine.  What isn't working again?  

Do any of these work?

```

ping 145.116.11.254
ping 209.98.65.50
ping www.mpr.org

```

---

### Post by sickdude on 2005-10-12
it looks so strange, packets are filterd, this sucks big time. all i want is another IP number so i can get back on the web :(

sickdude@megatron:~$ ping 145.116.11.254
PING 145.116.11.254 (145.116.11.254) 56(84) bytes of data.
From 145.116.11.254 icmp_seq=1 Packet filtered
From 145.116.11.254 icmp_seq=3 Packet filtered
From 145.116.11.254 icmp_seq=4 Packet filtered
From 145.116.11.254 icmp_seq=5 Packet filtered
 
--- 145.116.11.254 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4000ms
 
sickdude@megatron:~$ ping 209.98.65.50
PING 209.98.65.50 (209.98.65.50) 56(84) bytes of data.
From 145.116.11.254 icmp_seq=1 Packet filtered
From 145.116.11.254 icmp_seq=2 Packet filtered
From 145.116.11.254 icmp_seq=3 Packet filtered
 
--- 209.98.65.50 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
 
sickdude@megatron:~$ ping [www.mpr.org](www.mpr.org)
ping: unknown host [www.mpr.org](www.mpr.org)
sickdude@megatron:~$

---

### Post by mlomker on 2005-10-12
> sickdude@megatron:~$ ping 145.116.11.254
PING 145.116.11.254 (145.116.11.254) 56(84) bytes of data.
From 145.116.11.254 icmp_seq=1 Packet filtered


This wouldn't work if you didn't have an IP address.  The 'filtered' part means that you are being blocked by a firewall.  Are you running Firestarter on your machine?  Try shutting it off.

---

### Post by sickdude on 2005-10-12
i dont have any firewall utils installed on my system so i dont know who the hell is blocking me

---

### Post by sickdude on 2005-10-12
nmap scan gives me this 

(The 65533 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh

but this shouldt block me from getting a other ip or letting me surf the web

---

### Post by mlomker on 2005-10-12
> i dont have any firewall utils installed on my system so i dont know who the hell is blocking me

If you can ping the same number from Windows then it might be your Internet provider.  They don't require you to log into a web page or run an application to access your connection. do they?

---

### Post by sickdude on 2005-10-12
no this connection is open all the way, only smtp is blocked but thats all really

and this happend over night, i turned of the computer with a internet connection. but when i got out of bed i turned on the computer and there was no internet. so this is so strange

---

### Post by sickdude on 2005-10-12
ok i got it back up again

wanna know how??

i changed networkcard this is pretty crappy because i have a new mobo with a networkcard onboard and this one seems to be very wierd maybe a bug in the nic or in the kernel i dont know maybe you know??

---

### Post by mlomker on 2005-10-12
> in the kernel i dont know maybe you know??

Kernel updates can cause problems, so you might be on to something.

---

### Post by sickdude on 2005-10-12
[QUOTE=mlomker]Kernel updates can cause problems, so you might be on to something.[/QUOTE]

well i did a apt-get upgrade and there was a kernel update so i think that is the biatch in this problem.

so whats next? file a report in bugzilla?

---

