---
title: "Problem with static IP"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by Yves_Dawson on 2014-06-01
Hi,

I have a static IP problem with Ubuntu server 14.04.  If I set the IP with DHCP everything work fine but not with static.

Here's my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.103
    netmask 255.255.255.0
    gateway 192.168.1.1

After the bootup of the server if I look at ifconfig all I get is the loopback, nothing for eth0.

If I try to ifdown or ifup eth0 I get the following message:

/etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

If I set the ip manually with sudo ifconfig eth0 192.168.1.103 netmask 255.255.255.0 it work fine but naturally that change is temporary!

Any help is welcome,

Thanks

---

### Post by TheFu on 2014-06-01
Looks find to me, though missing the DNS settings is bad. dns-nameservers and  dns-search

I'd look for "ohs" instead of "zeros" in the file and verify that eth0 is actually recognized by the OS (see dmesg) - that is unlikely to be an issue based on the other things you've said.  

Also - how did you edit the file?  Could the EOL characters be wrong?

If the machine is portable, it might be easier to setup a "dhcp reservation" using the router to provide a static IP at home, but DHCP elsewhere.

I'm just throwing darts now ...

---

### Post by chili555 on 2014-06-01
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="#FF0000"]dns-nameservers 8.8.8.8 192.168.1.1[/COLOR]
```And try again:```
sudo ifdown eth0 && sudo ifup -v eth0
```Please note and post any errors.

---

### Post by Yves_Dawson on 2014-06-01
Chili555:

Added the dns line and same result:

[COLOR=#000000]/etc/network/interfaces:2: misplaced option[/COLOR]
[COLOR=#000000]ifdown: couldn't read interfaces file "/etc/network/interfaces"

[/COLOR]

---

### Post by chili555 on 2014-06-01
That implies that there is something wrong with the file, although it looks fine above. Do you mind if we have a peek?```
cat /etc/network/interfaces
```It isn't something like 1o instead of lo, is it? Or l0 instead of lo??

And how about permissions?```
ls -al /etc/network/interfaces
```Mine says:```
-rw-r--r-- 1 root root 82 Apr 16 12:04 /etc/network/interfaces
```

---

### Post by The Cog on 2014-06-01
It really looks like there's something screwy with the config file. It'll be a bit long, but can you (copy/paste) post the output of this command:
```
hd /etc/network/interfaces
```

---

### Post by Yves_Dawson on 2014-06-01
chili555:

cat /etc/network/interfaces returns:

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1

ls -al /etc/network/interfaces returns:

-rw-r--r-- 1 root root 368 Jun 1 14:01 /etc/network/interfaces


The Cog:

hd /etc/network/interfaces returns:
```

00000000  23 20 54 68 69 73 20 66  69 6c 65 20 64 65 73 63  |# This file desc|
00000010  72 69 62 65 73 20 74 68  65 20 6e 65 74 77 6f 72  |ribes the networ|
00000020  6b 20 69 6e 74 65 72 66  61 63 65 73 20 61 76 61  |k interfaces ava|
00000030  69 6c 61 62 6c 65 20 6f  6e 20 79 6f 75 72 20 73  |ilable on your s|
00000040  79 73 74 65 6d 0a 61 6e  64 20 68 6f 77 20 74 6f  |ystem.and how to|
00000050  20 61 63 74 69 76 61 74  65 20 74 68 65 6d 2e 20  | activate them. |
00000060  46 6f 72 20 6d 6f 72 65  20 69 6e 66 6f 72 6d 61  |For more informa|
00000070  74 69 6f 6e 2c 20 73 65  65 20 69 6e 74 65 72 66  |tion, see interf|
00000080  61 63 65 73 28 35 29 2e  0a 23 20 54 68 65 20 6c  |aces(5)..# The l|
00000090  6f 6f 70 62 61 63 6b 20  6e 65 74 77 6f 72 6b 20  |oopback network |
000000a0  69 6e 74 65 72 66 61 63  65 0a 61 75 74 6f 20 6c  |interface.auto l|
000000b0  6f 0a 69 66 61 63 65 20  6c 6f 20 69 6e 65 74 20  |o.iface lo inet |
000000c0  6c 6f 6f 70 62 61 63 6b  0a 0a 23 20 54 68 65 20  |loopback..# The |
000000d0  70 72 69 6d 61 72 79 20  6e 65 74 77 6f 72 6b 20  |primary network |
000000e0  69 6e 74 65 72 66 61 63  65 0a 61 75 74 6f 20 65  |interface.auto e|
000000f0  74 68 30 0a 69 66 61 63  65 20 65 74 68 30 20 69  |th0.iface eth0 i|
00000100  6e 65 74 20 73 74 61 74  69 63 0a 61 64 64 72 65  |net static.addre|
00000110  73 73 20 31 39 32 2e 31  36 38 2e 31 2e 31 30 33  |ss 192.168.1.103|
00000120  0a 6e 65 74 6d 61 73 6b  20 32 35 35 2e 32 35 35  |.netmask 255.255|
00000130  2e 32 35 35 2e 30 0a 67  61 74 65 77 61 79 20 31  |.255.0.gateway 1|
00000140  39 32 2e 31 36 38 2e 31  2e 31 0a 64 6e 73 2d 6e  |92.168.1.1.dns-n|
00000150  61 6d 65 73 65 72 76 65  72 73 20 38 2e 38 2e 38  |ameservers 8.8.8|
00000160  2e 38 20 31 39 32 2e 31  36 38 2e 31 2e 31 0a 0a  |.8 192.168.1.1..|
00000170

```

To all:

It is not a question of having Os instead of zeros.  I checked it ;)

And btw, since I got this issue, I searched Internet and it seems a lot of people face this problem since Ubuntu 12.  Unfortunately, I still didn't found a solution that works for me. A few days before I installed another server with Ubuntu 10.04.4 32bits and made the exact same config and it worked fine. And before you ask for it, there's not IP conflict as the other server doesn't exist anymore ;)

And I don't see what could have gone wrong with the file as it's a fresh install.  I changed the configuration to static IP right after the install of the server and faced this issue immediately.

---

### Post by steeldriver on 2014-06-01
Your /etc/network/interfaces file appears to be missing a # (comment indicator) in the second line

```

# This file describes the network interfaces available on your system
[COLOR=#ff0000]**# **[/COLOR]and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by Yves_Dawson on 2014-06-01
steeldriver:

Wow!  What a stupid mistake!!!  You solved the problem!

What's weird is that for as far as I know I never touched that line so I can't explain why the comment indicator disappeared.

But thanks a lot for having seen it.

---

### Post by chili555 on 2014-06-02
> cat /etc/network/interfaces returns:

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1In fact, it returned a lot more; it returned the part that was faulty that would have helped us fix it.

---

### Post by TheFu on 2014-06-02
I would swap the order of the dns-nameservers too. Hitting the local one before the remote one should be faster.

---

### Post by chili555 on 2014-06-02
> **TheFu said:**
> I would swap the order of the dns-nameservers too. Hitting the local one before the remote one should be faster.And you can find out for sure with *namebench*: [https://code.google.com/p/namebench/](https://code.google.com/p/namebench/) It is in the repositories.

---

### Post by TheFu on 2014-06-02
Good point on the DNS speed stuff.

If your WAN connection is that fast, I'd agree.  My local DNS cache is 6-8x faster than anything on the internet.  Plus there are privacy concerns with DNS queries that many people don't consider.  8.8.8.8 is google - whether they need to know every DNS lookup or not is something every admin needs to decide for themselves. 

On my network, I let the router cache DNS, so there isn't any need for more than 1 to be in the list.  It isn't like the network will be up if the router isn't working anyway.  ;)

---

### Post by oldfred on 2014-06-02
Is .103 inside the DHCP reserved number range on router? Or in effect already used?

I had that issue and just have to use numbers outside the reserved range.

My new Comcast router seems to reserve all addresses and you can only set from router which address is fixed, and it did not work first try, and I have not tried again.

---

### Post by Yves_Dawson on 2014-06-03
Well I wasn't expecting this conversion to continue after the issue was solved ;)

TheFU:

In fact I will remove google's DNS and use the router's one (which uses a local one on my other server and my ISP's ones) and the server will also have a DNS server configured.

oldfred:

No problem with the IP, my router's DHCP is configured to allocate from 150 to 200.

Thanks to all of you for help and advises.

I have another thread which one person replied and with good advice too but I'd like a point of view from more people.  So if you have time to spare, you can look at this:

[http://ubuntuforums.org/showthread.php?t=2227430](http://ubuntuforums.org/showthread.php?t=2227430)

---

