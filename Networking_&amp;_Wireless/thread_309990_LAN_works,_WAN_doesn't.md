---
title: "LAN works, WAN doesn't"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Forlornity on 2006-11-30
Hi There (First post WOO!) I've had the Edgy live disc running on my machine and installed from there (but had to un-install due to Vista not recognising itself, stupid windows) and in both cases I've had the exact same problems with networking:

The PC is connected to the network fine, I'm running a D-Link G604T and when I enter it's ip address (192.168.1.1) into the firefox address bar, the router's configuration pages appear. However, whenever I try to visit anywhere else it says: "Connecting to XXXXXXX.XXX" but never makes it. I can ping google just fine (my site never responds to pinging strangely enough) but it just cannot connect to the internet. 

Can anyone tell me what's wrong?

Thanks, Forlornity

---

### Post by aidanr on 2006-11-30
sounds like a dns problem
try going into 
system->administration->networking
hit the dns tab and see if there are any dns servers listed
if not then add the ip of your router

edit:// nm, shoulda read more carefully, if you can ping google then its probably not dns:rolleyes:

---

### Post by Forlornity on 2006-11-30
I'll try that the moment my alternate install is finished dloading, meanwhile, can anyone help me with the wireless on my other pc (an old Tiny running Xubuntu edgy) I've got a usb wireless stick in it and i've tried a number of methods for making it work (including ndiswrapper and the ZD1211 linux driver) but none of it has worked,  as you've probably guessed it's a ZyDas 1211 chipset manufactured by a german company called targa, it used the ZyDas drivers to run it on windows so I presume they should work with it anywhere else. If it has any effect, whenever I plug the stick in it's data/connect/action light flicks on for a moment then turns off again, it also turns on during boot.

Could you help me with this?

---

### Post by Forlornity on 2006-11-30
Any ideas from anyone?

---

### Post by Thumper322 on 2006-11-30
> **Forlornity said:**
> I'll try that the moment my alternate install is finished dloading, meanwhile, can anyone help me with the wireless on my other pc (an old Tiny running Xubuntu edgy) I've got a usb wireless stick in it and i've tried a number of methods for making it work (including ndiswrapper and the ZD1211 linux driver) but none of it has worked,  as you've probably guessed it's a ZyDas 1211 chipset manufactured by a german company called targa, it used the ZyDas drivers to run it on windows so I presume they should work with it anywhere else. If it has any effect, whenever I plug the stick in it's data/connect/action light flicks on for a moment then turns off again, it also turns on during boot.

Could you help me with this?

A quick check on a [Linux wireless card database]("http://linux-wless.passys.nl/") turned up [a driver for your card]("http://zd1211.ath.cx/"). You might have some luck poking through there. Scroll down to the *Installation* section.

---

### Post by dbott67 on 2006-11-30
Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
route -n
```

Is the problem just with Firefox?  Can you download packages from the repositories?  Can you use your e-mail/gaim/ftp/ssh/whatever client?

If the problem is just in Firefox, some people have reported problems with IPv6. You can disable IPV6 in Firefox by putting **about:config**
in the url bar. In the filter bar, type **ipv6**. Once found, doubleclick the search result to change the boolean value from false to true. Restart Firefox.

-Dave

---

### Post by stream303 on 2006-12-01
> **Forlornity said:**
> The PC is connected to the network fine, I'm running a D-Link G604T and when I enter it's ip address (192.168.1.1) into the firefox address bar, the router's configuration pages appear. However, whenever I try to visit anywhere else it says: "Connecting to XXXXXXX.XXX" but never makes it. I can ping google just fine (my site never responds to pinging strangely enough) but it just cannot connect to the internet.

Common situation.  I wrote up a quickie howto that might get your wan back.

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

I'd first try putting your isp's dns primary and backup nameservers into your routers setup page.

If you don't have access to the router, you can edit one line of a file as root (ie, sudo nano) (/etc/dhcp3/dhclient.conf) and reboot.  Write down those isp primary and backup dns addresses from the windows boxes and see if the howto above helps...

---

### Post by dbott67 on 2006-12-01
The only problem I have with stream303's solution is that we still don't know the cause.  I have read a number of similar threads where this solution has worked, but the thing that escapes me is *[COLOR="Red"]why is it happening?[/COLOR]*

I've been running Ubuntu (Warty, Hoary, Breezy, Dapper & Edgy, along with XP and OSX on the same network) and have never had to mess around with my DNS settings.  Granted, the router must be correctly configured, but the DNS forwarder in the router should "just work".

I've got a D-Link DI-614+ at home, but I've used Ubuntu at work (where DHCP & DNS are provided by Win2003) and not had problems.

Knowing which applications cannot resolve names would be the first step.  For example, many people note that they can ping via IP address & FQDN (i.e. [www.google.com)](www.google.com)), but the browser won't resolve.  What happens with applications like Synaptic (or apt-get), GAIM (or other IM clients), Evolution/TBird, etc?  Do they function properly?  Is the problem just with Firefox and related to IPv6?

**My suggestion would be this (assuming you can get online):**

1. Download 'traceroute' from Synaptic
```
sudo apt-get install traceroute
```
The default program (tracepath) always seems to fail outside of my router.

2. Ensure that your DNS is set to the IP of your router (i.e. 192.168.1.1 or similar):
```
dbott@edgy:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
```

3. Run a traceroute to google.com
```
dbott@edgy:~$ traceroute www.google.com
traceroute: Warning: www.google.com has multiple addresses; using 72.14.205.99
traceroute to www.l.google.com (72.14.205.99), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.893 ms  0.566 ms  3.471 ms
 2  abc.ip.execulink.net (209.183.xxx.yyy)  15.172 ms  13.987 ms  15.476 ms
 3  i.core1.ip.execulink.net (209.183.xxx.zzz)  19.776 ms  16.956 ms  15.494 ms
 4  142.46.4.109 (142.46.4.109)  15.460 ms  15.044 ms  15.278 ms
 5  142.46.128.9 (142.46.128.9)  16.954 ms  16.137 ms  16.219 ms
 6  142.46.128.5 (142.46.128.5)  15.381 ms  16.571 ms  24.573 ms
 7  gw-google.torontointernetxchange.net (198.32.245.6)  17.610 ms  15.690 ms  21.614 ms
 8  66.249.94.96 (66.249.94.96)  22.124 ms  20.777 ms 66.249.94.92 (66.249.94.92)  24.258 ms
 9  72.14.232.66 (72.14.232.66)  16.887 ms 72.14.236.138 (72.14.236.138)  17.560 ms 72.14.232.62 (72.14.232.62)  26.418 ms
10  qb-in-f99.google.com (72.14.205.99)  19.277 ms  20.249 ms  16.978 ms
```

Notice that tracepath is resolving some IP addresses.

FYI, using tracepath returns this:
```
dbott@edgy:~$ tracepath www.google.com
 1:  192.168.1.106 (192.168.1.106)                          0.256ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2   1.104ms
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500
```

The only time I could see changing your DNS servers on the router would be if your ISPs DNS server's are slow (or not working).  You might also need to change them on the local machine from time-to-time to troubleshoot/test/whatever, without affecting everyone else on the network.

Again, I'm not suggesting that stream303's solution won't work --- I'd just like to know why it's not performing as it should.  There are many people (like me) that have similar setups and do not experience this problem.

The main differences would be:
1. Make/model of router
2. Firmware version on router *[COLOR="Red"](this could be the issue for many.  Just updating the firmware may cure issues).[/COLOR]*
3. ISP (and their respective capabilities/competence levels with respect to setting up DNS/DHCP/routing/etc for their customers).

The most common element among these threads is IPv6 support in Firefox.  I have never disabled it on my computers, but it may be because I've updated my router's firmware.

Post whatever info you can because I'd like to find out if the problem is with Firefox, IPv6, DNS or your router.

Thanks,
Dave

---

### Post by nautilus on 2007-04-15
many cheap routers break under the wrath of ipv6.

integrated dns servers in them, more often than not, simply don't understand AAAA records.

instead of returning a big ol' "?" they take a crap and force you to cripple your system into an ancient networking protocol, IPv4.

*sigh.*

---

