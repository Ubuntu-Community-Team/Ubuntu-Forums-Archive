---
title: "ubuntu server ethernet connection not working"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by Sigurthor_Bjorgvin on 2015-09-26
Hello

I have a limited experience with ubuntu/unix but know my way around.
I have been trying to set up a ubuntu server 14.04 that i want to be able to ssh into inside and outside my local network. 
The issue right now is that i aint able to ping any ip or host except localhost.
Every time i try i get a error

```
connection: network is unreachable
```

and when i try to ping a domain i get this error

```
 ping: unknown host google.com
```

I spent about 6 hours surfing and trying to find a fix but i cant seem to be able to find it.
I have set the nameserver in the /etc/resolv.conf to 8.8.8.8
the file looks like this:

```
nameservers 8.8.8.8
nameservers 8.8.4.4
```

I set a static ip to the server 192.168.1.178 and i can see the server in my router with that ip.

i am able to ```
ping localhost
```.

when i do ```
netstat -nr
``` the table returned is

```
[COLOR=#111111][FONT=Consolas]Kernel IP routing table
[/FONT][/COLOR]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1       0.0.0.0            UG    0        0        0   eth0 
[COLOR=#111111][FONT=Consolas]192.168.1.0      0.0.0.0   255.255.255.0   U    0     0     0   eth0[/FONT][/COLOR] 
```

when i try to add to the route with the command ```
sudo route add default gw 192.168.1.1
``` i get the error ```
SIOCADDRT: network is unreachable
```

when i do cat ```
/etc/network/interfaces
``` i get this

```
auto lo
iface lo inet static

iface eth0 inet static
    address 192.168.1.178
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 192.168.1.1
    dns-search ManCaveDomain
```

when i do ```
sudo dhclient eth0
``` it hangs for a few minutes and returns nothing 

when i do ```
ifocnfig
``` i get

```
lo    Link encap: Local Loopback
       inet addr: 127.0.0.1 mask: 255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:65536 Metric: 1
       RX packets: 4 errors: 0 dropped: 0 overruns: 0 frame: 0
       TX packets: 4 errors: 0 dropped: 0 overruns: 0 carrier: 0
       collision: 0 txqueuelen: 0
       RX bytes: 336 (336.0 B) TX bytes:336 (336.0 B)
```

This issue is really getting to me and I cant seem to figure it out.

Can anyone here help me?
If you need any more information please post the command and i will post the output.

Thanks in advance

---

### Post by blitz2 on 2015-09-26
Is eth0 up? You can look up to syslog to make sure if a hw problem or not. (cat or nano /etc/log/syslog, /var/log/boot.log) 

Also you can check your hardware;
lshw -short

here is my ethernet inf;
eth0       network    82540EM Gigabit Ethernet Controller
eth1       network    82540EM Gigabit Ethernet Controller

If its ok than you can ping to gateway?

---

### Post by TheFu on 2015-09-26
Don't touch /etc/resolv.conf.  That has been maintained by the resolvconf package since 12.04.

Remove these lines from your interfaces file. They are deprecated.
```

    network 192.168.1.0
    broadcast 192.168.1.255
```

You are missing a 
```
auto eth0
```
stanza. Add it above the "static" line.

Manually adding an unneeded route is bad.
If you have a static IP setup - like it appears you do, don't use DHCP commands.

Please post the output from **sudo lshw -C network** so we can see some facts.

Thanks for using code tags - very helpful.  Please leave the command and the output together in 1 code block. We are used to reading this stuff together.

---

