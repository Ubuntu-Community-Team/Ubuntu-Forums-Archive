---
title: "I can't connect to a wireless network starting with 172.168.*.*"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by mod187 on 2007-02-14
I am running Edgy gnome.

I got my wireless working using this tutorial 
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

I can connect to several networks with no problem. The only problem I have is when I try to connect to a network with the gateway address of 172.168.1.1

I can connect when I plug the Ethernet cable in, but not wireless. I even tried to set a static IP, and it still failed. 

The connection is an unsecured hotspot at a condo I work at. It's set up to be free wireless for guests and owners. I can boot to XP and it will work, just not ubuntu.

Any ideas?

Thanks,

Matt

---

### Post by chili555 on 2007-02-14
Yes. I have the idea that the gateway is really *192.168.1.1*. Please check and try again.

---

### Post by mod187 on 2007-02-14
> chili555           	Yes. I have the idea that the gateway is really 192.168.1.1. Please check and try again.

I wish it was! The gateway is in fact 172.168.1.1

Matt

---

### Post by chili555 on 2007-02-14
From man route:

> route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
              adds a route to the network 192.56.76.x via "eth0". The Class  C
              netmask modifier is not really necessary here because 192.* is a
              Class C IP address. The word "dev" can be omitted here.


A little Googling suggests 172.xxx is a Class *B* address and that its Netmask may be 255.255.0.0.

So, I might try:

```
route add -net 172.168.1.1 netmask 255.255.0.0 <your_wireless_interface>
```

And then bring up your interface the usual way. Interesting problem, actually.

---

### Post by netztier on 2007-02-14
> **mod187 said:**
> 
The connection is an unsecured hotspot at a condo I work at. It's set up to be free wireless for guests and owners. I can boot to XP and it will work, just not ubuntu.


Hit that WLAN's admin a bit with over the head with a large trout. ;-)

**172.168.0.0 /16** belongs to AOL, and must therefore never be used for private IP networks.

```
[COLOR="DarkGreen"][FONT="Courier New"]marc@cube:~$ whois 172.168.0.0

OrgName:    America Online
OrgID:      AOL
Address:    22000 AOL Way
City:       Dulles
StateProv:  VA
PostalCode: 20166
Country:    US

NetRange:   172.128.0.0 - 172.191.255.255
CIDR:       172.128.0.0/10
NetName:    AOL-172BLK
NetHandle:  NET-172-128-0-0-1
Parent:     NET-172-0-0-0-0
NetType:    Direct Allocation
NameServer: DAHA-01.NS.AOL.COM
NameServer: DAHA-02.NS.AOL.COM
NameServer: DAHA-07.NS.AOL.COM
Comment:    ADDRESSES WITHIN THIS BLOCK ARE NON-PORTABLE
RegDate:    2000-03-24
Updated:    2003-08-08
[/FONT][/COLOR]
```

Proper addressing for private internetworks is defined in [RFC1918]("ftp://ftp.rfc-editor.org/in-notes/rfc1918.txt") resp. [BCP005 ]("ftp://ftp.rfc-editor.org/in-notes/bcp/bcp5.txt"). In a nutshell, they basically define this:

> ```
[COLOR="Navy"][FONT="Courier New"]3. Private Address Space

   The Internet Assigned Numbers Authority (IANA) has reserved the
   following three blocks of the IP address space for private internets:

     10.0.0.0        -   10.255.255.255  (10/8 prefix)
     172.16.0.0      -   172.31.255.255  (172.16/12 prefix)
     192.168.0.0     -   192.168.255.255 (192.168/16 prefix)

   We will refer to the first block as "24-bit block", the second as
   "20-bit block", and to the third as "16-bit" block. Note that (in
   pre-CIDR notation) the first block is nothing but a single class A
   network number, while the second block is a set of 16 contiguous
   class B network numbers, and third block is a set of 256 contiguous
   class C network numbers.
```
[/FONT][/COLOR]


Something seems to be wrong in the configuration of that network. I'd check that subnet addresses, subnet masks and default gateway settings match everywhere, and that the DHCP server is properly configured to dole out correct addressing, subnet mask, default gateway and DNS information to the clients.

best regards

Marc

---

