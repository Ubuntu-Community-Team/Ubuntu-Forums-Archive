---
title: "DNS resolution problems"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by irregardlessly on 2008-03-11
Hi everyone,

I am pretty new to Ubuntu so please bear with me. 

I just recently moved.  At my old place I had my cable modem hooked into my Linksys WRT54G router, and my laptop hooked into the router.  Everything worked fine.

At my new place however I tried the same thing with my new router.  Everything works fine in Win XP (I am dual booting Win XP and Ubuntu 7.10).  However, in Ubuntu I don't get name resolution.  That is, if I type in Google's IP address in FireFox I get Google, but if I type in [www.google.com](www.google.com) it times out.  Same with all other applications like mail, pidgin, PING, etc.

My router is at 192.168.1.2 and is set for DHCP.  My laptop private IP is 192.168.1.101 via the DHCP.

Here is some more info:

jon@jon-laptop:~$ ifconfig eth0
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:13:21:B7  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe13:21b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1725 (1.6 KB)  TX bytes:5635 (5.5 KB)
          Interrupt:18 Base address:0x1800 

```


jon@jon-laptop:~$ cat /etc/resolv.conf
```

search cmts.eph.ptd.net
nameserver 216.144.187.199
nameserver 207.44.96.129
nameserver 216.144.187.71

```

Note that the info above looks to match what my router must have automatically received from my cable modem.  I tried statically setting other DNS server IPs (Verizon's, OpenDNS) in my router and in the network config window.  It did not make any difference.  My router has it's own PING test.  I was able to ping [www.google.com](www.google.com) from there, so it seems like the router is fine, I just have not set up Ubuntu properly to do DNS through it or something.

Any help would be greatly appreciated.  Let me know if you need more info.  Thanks!

[Edit:]
I forgot to mention, when I googled this some stuff came up about IPV6 causing a similar problem.  I tried disabling IPV6 in FireFox in about:config and restarting FireFox but that did not help.

---

### Post by SpaceTeddy on 2008-03-11
have you tried removing everything from the resolv.conf and just adding your router as the dns ?

so, you would place the entries
> nameserver 192.168.1.2
as the only name in the resolv.conf

---

### Post by irregardlessly on 2008-03-11
Hi SpaceTeddy,

Thank you for the suggestion.  I tried this but it did not have any affect.

---

### Post by SpaceTeddy on 2008-03-11
can you acctually query any of the dns server ? like, what does the command
```
nslookup www.google.de 192.168.1.2
```
say ?

---

### Post by irregardlessly on 2008-03-11
Looks like no.  I tried a bunch of variations and they all timed out.  

```

jon@jon-laptop:~$ nslookup www.google.de 192.168.1.2
;; connection timed out; no servers could be reached

jon@jon-laptop:~$ nslookup www.google.com 192.168.1.2
;; connection timed out; no servers could be reached

jon@jon-laptop:~$ nslookup www.google.com 4.2.2.1
;; connection timed out; no servers could be reached

jon@jon-laptop:~$ nslookup www.google.com 208.67.222.222
;; connection timed out; no servers could be reached

jon@jon-laptop:~$ nslookup www.google.com 216.144.187.199
;; connection timed out; no servers could be reached

```

---

### Post by irregardlessly on 2008-03-11
Not sure if this helps, but I seem to have the same problem if I connect directly to the cable modem.  I also tried at my parents' house (they have DSL) and I get the same problem when connecting directly to their DSL modem.

---

### Post by irregardlessly on 2008-03-12
Anyone else have any other ideas?  I have been using Ubuntu for over a year now, but if I can't get this to work I will have to go back to windows.  :(

---

### Post by SpaceTeddy on 2008-03-12
strange, i did not see your post... anyways - timeout is no good. Timeout means that your computers acctually sends something, but does not receive an answer to it. 

can you please try if you can acctually ping any of the servers that do not answer. Just a test if this is a pure dns problem, or something broader that might not be dns, but network related.

these two servers answered my pings - so should they for you if this is a dns problem
```
ping -c 4 4.2.2.1
ping -c 4 208.67.222.222
```

---

### Post by irregardlessly on 2008-03-12
Yes, I was able to ping them and received replies.  

This is very confusing to me.  I thought about trying to use some packet sniffer or something and actually look at the DNS packets except that 
1. I wouldn't really know what I was looking at 
2. I don't really know how to set up the sniffer.  I tried wireshark before but couldn't get it to capture anything.
3. I can't grab any packages with synaptic because of this very problem.

Please let me know if you have any more ideas.  Thanks again for your help on this issue.

---

### Post by SpaceTeddy on 2008-03-12
on the off chance that something is misconfigured in your paket filter... can you please post the output of the follow commands ?

```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
sudo iptables -L -vnx --table mangle
```

this is probably way too much, but i figure it is safer to have too much information than too little... 

as for a paket sniffer - i would use tcpdump in that case. fast and no hassles. But you would need to install it via synaptic... if it is not installed, that is

---

### Post by Warprunner on 2008-03-12
> **irregardlessly said:**
> Yes, I was able to ping them and received replies.  

This is very confusing to me.  I thought about trying to use some packet sniffer or something and actually look at the DNS packets except that 
1. I wouldn't really know what I was looking at 
2. I don't really know how to set up the sniffer.  I tried wireshark before but couldn't get it to capture anything.
3. I can't grab any packages with synaptic because of this very problem.

Please let me know if you have any more ideas.  Thanks again for your help on this issue.

Forgive me for backing things up....

1st check to make sure your using DHCP to get your address and your DNS's. You can change the DNS's in the router.

From what your saying ...by not being able to do much at the different locations...sounds like you have a static IP address and don't have DNS's listed. So make sure your using DHCP to auto get an address. It should give you your DNS as well.

SYSTEM> ----Administration> ----Network> go to your connection and then go to Properties. Check Roaming Mode Enabled.

Just a thought.

---

### Post by irregardlessly on 2008-03-12
> **SpaceTeddy said:**
> on the off chance that something is misconfigured in your paket filter... can you please post the output of the follow commands ?

```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
sudo iptables -L -vnx --table mangle
```

this is probably way too much, but i figure it is safer to have too much information than too little... 

as for a paket sniffer - i would use tcpdump in that case. fast and no hassles. But you would need to install it via synaptic... if it is not installed, that is

OH!  I think you are on to something.  I need to reboot in Ubuntu to check, but I think this might be it.  I tried using Lokkit like 9 months ago.  It is some linux "firewall".   I had turned it off but it is possible that it left some stuff behind and didn't clean up right.  If I recall it does something with iptables.  (I don't really know what iptables are but I remember them in the description of the app).  I'll be back with the results in a moment...

---

### Post by irregardlessly on 2008-03-12
That worked!!!  Results from first iptables command are below.  Now I don't know exactly what that means, but I do see lokkit added some record here which was blocking some UDP requests.  Perhaps it was hardwired to my old DNS server or something?  So I ran Lokkit again and turned everything off again and now everything works.

Anyhow, thanks so much!  Awesome!

```
Chain INPUT (policy ACCEPT 1471 packets, 395286 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    1631   425990 RH-Lokkit-0-50-INPUT  0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 RH-Lokkit-0-50-INPUT  0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 1771 packets, 141214 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain RH-Lokkit-0-50-INPUT (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       2     1152 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp spts:67:68 dpts:67:68 
       0        0 ACCEPT     udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp spts:67:68 dpts:67:68 
       0        0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     udp  --  *      *       68.87.64.146         0.0.0.0/0           udp spt:53 
       0        0 ACCEPT     udp  --  *      *       68.87.75.194         0.0.0.0/0           udp spt:53 
       0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 reject-with icmp-port-unreachable 
     158    29552 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp reject-with icmp-port-unreachable 
```

---

### Post by SpaceTeddy on 2008-03-12
>       0        0 ACCEPT     udp  --  *      *       68.87.64.146         0.0.0.0/0           udp spt:53 
       0        0 ACCEPT     udp  --  *      *       68.87.75.194         0.0.0.0/0           udp spt:53 

these two lines allow incoming udp pakets from the specified ip addresses. i guess those are your old dns servers.

>        0        0 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 reject-with icmp-port-unreachable 
     158    29552 REJECT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp reject-with icmp-port-unreachable

and these two drop anything that has not been accepted beforehand - i.e. any outgoing paket that was not specificially allow got dropped there - tcp and udp. 

This also explains why you could ping the servers - icmp did not get dropped anywhere :)

---

### Post by irregardlessly on 2008-03-12
It is also ironic because when I installed lokkit I was only trying to protect myself from inbound traffic, not limit outbound traffic.  I was worried about when I am on the road and not behind a router.  Oh well.  Thanks again.

---

