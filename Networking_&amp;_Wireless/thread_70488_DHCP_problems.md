---
title: "DHCP problems"
date: 2005-09-30
forum: Networking &amp; Wireless
---

### Post by SomeoneStupid on 2005-09-30
Hello everyone.. I've recently installed Ubuntu, and I think it's been working great... except for the networking.  I can't seem to connect to my router, and we're using a DHCP set up at home.  A friend of mine told me to do this:

$ ipconfig
$ ping 192.168.0.1 (router's ip)

this is what I got:
> 
nawaf@192:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:25:B3:E9
          inet6 addr: fe80::208:a1ff:fe25:b3e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:6876 (6.7 KiB)
          Interrupt:17 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272894 (266.4 KiB)  TX bytes:272894 (266.4 KiB)

nawaf@192:~$ ping 192.168.0.1
connect: Network is unreachable


Any help would be much appreciated..

---

### Post by davidknibb on 2005-09-30
Assuming you are running Breezy(the menus are slightly different for Warty, but you'll find it - have you gone to System>Administration>Networking and looked to see if eth0 is configured ??

If not ,then select it, click 'properites', tick 'enable this connection' and it should work.

If it isn't this then come back to the forum.

David

---

### Post by davidknibb on 2005-09-30
I forgot to add that when configuring make sure that you set DCHP in the configuration.  I think that Static is set be default.  (This might even be your problem?)
David

---

### Post by SomeoneStupid on 2005-09-30
[QUOTE=davidknibb]Assuming you are running Breezy(the menus are slightly different for Warty, but you'll find it - have you gone to System>Administration>Networking and looked to see if eth0 is configured ??
If not ,then select it, click 'properites', tick 'enable this connection' and it should work.
If it isn't this then come back to the forum.
David[/QUOTE]

It is configured and enabled.. that's why I'm so frustrated.. :???: 

Oh, and yes, it is set to DHCP..

---

### Post by [pl]ice on 2005-09-30
hey, post /etc/network/interfaces
and post exactly what ping says etc...
it should work :) eth0 is normally no problem... 
try ping form router, there is an option.

---

### Post by SomeoneStupid on 2005-09-30
[QUOTE='[pl]ice']hey, post /etc/network/interfaces
and post exactly what ping says etc...
it should work :) eth0 is normally no problem... 
try ping form router, there is an option.[/QUOTE]
interfaces:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0
ping:
> 




nawaf@192:~$ ping 192.168.0.1
connect: Network is unreachable
nawaf@192:~$
nawaf@192:~$


---

### Post by xmastree on 2005-09-30
Mine:
```
eth0       Link encap:Ethernet  HWaddr 00:0C:6E:C0:E1:4E
        inet addr:192.168.232.214  Bcast:192.168.255.255  Mask:255.255.224.0
        inet6 addr: fe80::20c:6eff:fec0:e14e/64 Scope:Link
```Yours:
```
eth0 Link encap:Ethernet HWaddr 00:08:A1:25:B3:E9
inet6 addr: fe80::208:a1ff:fe25:b3e9/64 Scope:Link
```

See the difference? Yours isn't being assigned an ip address.

Are you sure the cable's good?

---

### Post by SomeoneStupid on 2005-09-30
[QUOTE=xmastree]Are you sure the cable's good?[/QUOTE]

Well.. I'm sure that it worked on windows.. I doubt it could atrophy within this small a timeframe (around 8 hours ago..)

---

### Post by [pl]ice on 2005-09-30
gateway 192.168.1.1
netmask 255.255.255.0

add these two, at the end, 
then ifdown eth0 , ifup eth0

it couldn't find the path to the router, that what i think.
(correct gateway for urs)

---

### Post by SomeoneStupid on 2005-09-30
It didn't work.. aaand Networking won't open up for me either.. :???:

---

### Post by MAZDA on 2005-10-23
Hello to all !

I have the same problem with Breezy Badger like the starter of this Thread also.

I have installed Ubuntu Hoary on my PC and this version has absolutley no problems with the Network.
I had the possibility to surf on the Internet without any Problems after the Installations of Hoary.

Now i have make a dist-upgrade like the most of the Ubuntu Useres and for my surprise i can no more conect to the Internet and for that no more download some ubuntu packages with apt-get.

Something was overwriten by the upgrading process.

After a lot of searching here on the Forum i have found that this Problem exist since Ubuntu was first released.
[http://ubuntuforums.org/archive/index.php/t-21188.html](http://ubuntuforums.org/archive/index.php/t-21188.html) 
People how have used Warty and have try to upgrade to Hoary has the Same problems like People how have Hoary installed and have make a dist-upgrade to Breezy Badger.

In one of this Thread it is described to use the command route to find if it all works.
[http://www.ubuntuforums.org/showthread.php?t=20529](http://www.ubuntuforums.org/showthread.php?t=20529) 

After typing the command
"route -n" in my Console i became the following unexpected result.

> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface 

Normally the result of this Command should look like this here
> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.1.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 10.1.1.1 0.0.0.0 UG 0 0 0 eth0

It looks like i don't have a kernel IP routing table.

The command Ping does give also very unexpected results.

If i ping to my Locale adress 127.1.1.1 then it function all right.
I don't see any Errors displayed.

if i ping my ADSL-Router which have as adress "192.168.1.1"
with the following command 
"ping 192.168.1.1"
then i became the Error "Network is unreachable".

I would ask the Profis here in this Forum what is the best medicine for this Probleme in Breezy Badger.

Thanks in andvance for your help !

---

### Post by bixin on 2005-10-26
My problem is similar to the original problem. I have Hoary and it is on a desktop running exclusively. I don't know what happened as 2 days ago the connection was perfectly fine. However, i do have family visiting whe are used to other OS so I don't know if they just started going at stuff or what. But  I have been looking around these forums all night and on google. I have no IDEA what is up. I have checked most things and my problem is that the DHCP doesn't assign me an IP address. The isp is up and running or I wouldn't even be writing this, so I know there is nothing wrong with the service. I have a Soyo motherboard and it has an onboard Ethernet card and I also have a seperate card. both are recognized but no internet connections. I cannot ping anything at all it comes up network not available or ends with DHCP no offers. SO needless to say im at my wits end. I don't know whats wrong. I tried my live CD no dice it won't go past the begining screen. Any help is greatly appreciated, if you need more info say the word.

thanks

---

### Post by MAZDA on 2005-10-26
Here is maybe a good Solution for your Problem.

[http://ubuntuforums.org/showthread.php?t=80920](http://ubuntuforums.org/showthread.php?t=80920)

I have my Problem with my Internet acess now solved.

I need only now the information like other people how to make this solution
permanent in Ubuntu Breezy Badger.

Breezy Badger use from my side of view somehow a not very well developed and tested package called "ifupdown" for activating the Internet Acces.

This package is probably the thing which make the biggest Network Problems at the Moment in Ubuntu Breezy Badger.

I see at the Booting of Breezy Badger how this Package is loaded but the result is for my surprise not very sucefull in compare if you type the same things manualy in the Console.

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ifupdown](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ifupdown)

---

### Post by bixin on 2005-10-26
Well my connection is up and running. Not sure how just yet but i am working on some things. What I did tonight was, I did as instructed in this thread

[http://ubuntuforums.org/showthread.php?t=502:](http://ubuntuforums.org/showthread.php?t=502:)

at this point both ethernet cards were on and recognized.  I couldn't ping my own router nor anything else. SO I thought well maybe i will disable my onboard lan and use the card. I shut down disabled and rebooted. Just the old card was showing. I went to System>Administration>Networking. Saw eth0 was not activated so i hit activate. Well it took a century but never activated the connection so i just closed them both and opened a root terminal. and typed

ifdown eth0

ifdown: interface eth0 not configured

ifup eth0
Internet systems consortium dhcp client v3.0.1
blah blah blah legal stuff

listening on LPF/eth0/00:02:2a:c1:92
Sendeing on LPF/eth0/00:02:2a:c1:92
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
mv: overwrite '/etc/resolv.conf', overriding mode 0644? y (i have no idea what this means and still don't im going to search to find out so i said yes)
mv: cannot move '/etc/resolv.conf.dhclient-new' to '/etc/resolv.conf' :Operation not permitted
bound to 192.168.1.101 --renewal in 82842 seconds

well its done internet connection up and running I haven't rebooted yet so i don't know how long or its it set. I have done other things so i have to go over my notes but this is the only thing i have done with any kind of results.  SO yeah im off to see how i (and Ubuntu forums) fixed my problem or put a bandaid on it.

---

