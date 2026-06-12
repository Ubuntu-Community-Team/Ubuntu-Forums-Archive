---
title: "Can access internet but no local network resources on laptop via wifi"
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by blm14 on 2015-11-15
Never seen this happen before! I am using a relatively old dell laptop (N5030) running trusty with all packages up to date. I am posting this message from the laptop, so clearly internet is working.

here is the output of ifconfig:

```

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:ae:94:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70021 (70.0 KB)  TX bytes:70021 (70.0 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1b:b1:83:02:7c  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b1ff:fe83:27c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7728959 (7.7 MB)  TX bytes:737467 (737.4 KB)

```

contents of /etc/network/interfaces:

```

auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

```

output of netstat -r -n:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0

```

output of route:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         www.routerlogin 0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0

```

output of route -n:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

But if I try to ping the router:

```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
^C
--- 192.168.1.1 ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10003ms

```

or another machine on the LAN:

```

$ ping 192.168.1.14
PING 192.168.1.14 (192.168.1.14) 56(84) bytes of data.
From 192.168.1.13 icmp_seq=1 Destination Host Unreachable
From 192.168.1.13 icmp_seq=2 Destination Host Unreachable
From 192.168.1.13 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.14 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4022ms

```

I've tried to access 192.168.1.1 from safari on my iPad via wifi on the same wireless SID and was immediately presented with the login credentials screen, so the router is not outright blocking access from wifi clients. The router is a netgear R6220 with most up to date firmware.

Ideas?

---

### Post by blm14 on 2015-11-15
I have already tried ufw disable and that didnt change anything :( wifi is set to DHCP from NetworkManager

---

### Post by Hadaka on 2015-11-15
hi < since you are using network manager to manage your network
you cannot use both.... your...

/etc/network/interfaces file..
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

needs to be edited to look like this...
```
auto lo
iface lo inet loopback
```

---

### Post by blm14 on 2015-11-15
OK made that change, rebooted laptop, and I still cannot access 192.168.1.1 from a web browser, or ping it, or access any other LAN resources. 

route and route -n have the same output as well

---

### Post by Hadaka on 2015-11-15
please post the output of..
```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
```
thanks

---

### Post by blm14 on 2015-11-15
lspci:

```

09:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Dell Device [1028:04a6]
	Kernel driver in use: atl1c
0c:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card [185f:30af]
	Kernel driver in use: ath9k

```

/etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo 
iface lo inet loopback

```

---

### Post by blm14 on 2015-11-15
going to update from 3.13.0-61 kernel to 3.13.0-68 kernel to see if that makes any difference. EDIT: nope. Same problem :(

---

### Post by Hadaka on 2015-11-15
Hi please do ..
```
sudo modprobe -r atl1c
sudo modprobe atl1c
```
did that activate eth0 ?
please also post..
```
uname -r
lsb_release -a
```
also try disabeling the wifi, boot and test the wired connection

---

### Post by blm14 on 2015-11-15
Confused - I am not using wired currently, just wifi. Should I try to modprobe out ath9k?

uname:
```

Linux homewarez 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

lsb_release
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

```


I will try wired shortly...

---

### Post by blm14 on 2015-11-15
Disabled wifi, plugged in ethernet and got an IP address immediately. Didn't need to modprobe anything.

I am on wired connection now and I can access 192.168.1.1 from web browser and ping the gateway. So it seems to be something specifically with wireless.

---

### Post by Hadaka on 2015-11-15
hi, set your ipv4 and ipv6 like the attached and see if that clears it.
[ATTACH=CONFIG]265590[/ATTACH][ATTACH=CONFIG]265591[/ATTACH]
be sure to save the changes and boot

---

### Post by blm14 on 2015-11-15
OK so made those changes and rebooted. warez_2ghz is the name of the wireless SID that I am using. After reboot, settings are:

[IMG]http://i.imgur.com/SmlVXSP.png[/IMG]

[IMG]http://i.imgur.com/nH4OVBL.png[/IMG]

And still cannot ping or connect to 192.168.1.1 from web browser

---

### Post by Hadaka on 2015-11-15
now im confused..by "ping from browser" are you putting in 192.168.1.1 in the browser?
if so...that should put you into the routers log in page.  ctrl/alt/t  a terminal is where a 
ping should be sent from. see what happens when you try to ping its own ip.. please do...
```
ping -c4 192.168.1.13
and  ping -c4 192.168.1.1
```
the wireless seems to be working and attaching to the net as you are posting to ubuntu forums.

---

### Post by blm14 on 2015-11-15
sorry if I was unclear. Should have said

"Still cannot access my router's web interface at 192.168.1.1 or ping 192.168.1.1 from command line"

First ping:

```

$ ping -c4 192.168.1.13
PING 192.168.1.13 (192.168.1.13) 56(84) bytes of data.
64 bytes from 192.168.1.13: icmp_seq=1 ttl=64 time=0.059 ms
64 bytes from 192.168.1.13: icmp_seq=2 ttl=64 time=0.058 ms
64 bytes from 192.168.1.13: icmp_seq=3 ttl=64 time=0.056 ms
64 bytes from 192.168.1.13: icmp_seq=4 ttl=64 time=0.057 ms


--- 192.168.1.13 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.056/0.057/0.059/0.007 ms

```

second ping:

```

$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms

```

And yes I am accessing the internet despite the fact that there appears to be no route to 192.168.1.1. Weird right!?

---

### Post by Hadaka on 2015-11-15
indeed it is weird, all your other devices can ping the router
the wired end of that computer can ping and attach. the wireless
card can access the net via the router, the only thing i can think of
is some odd port forwarding via mac address in the router or some
type of mac address blocking but only on cmp...pinging. check any
rules and accepts or rejects you may have written, also, while it doesnt
seem logical because it is infact working, power everything down, remove
the battery and reseat the wireless card. pretty simple to do on a dell.
other that that, you can try running the wireless scrip and see if anything
shows up which i doubt. try some of those things and do some research
on your ufw blockings.
thanks.

---

### Post by blm14 on 2015-11-15
here is a ping from another machine that is connected via ethernet:

```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.263 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.239 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.227 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=4.39 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=17.2 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.250 ms
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4997ms
rtt min/avg/max/mdev = 0.227/3.765/17.216/6.203 ms

```

There are no port forwards set up in the router. I tried turning off ufw on the laptop and the problem remained! Re-seating the wifi card seems a bit extreme but I will try it later this week maybe.

---

### Post by blm14 on 2015-11-15
This is even stranger - I happen to have a realtek mini USB wifi adapter (similar to this one: [https://www.vilros.com/raspberry-pi/wifi-adapter.html](https://www.vilros.com/raspberry-pi/wifi-adapter.html))

If I plug that in and connect to my wireless SID via that one it STILL doesn't let me ping the router or connect to it via a browser. So it doesn't appear to be something with the wifi card because using another one doesn't resolve the issue.

---

### Post by chili555 on 2015-11-16
I am a little puzzled by this:> output of route:

Code:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default        [COLOR="#FF0000"] [www.routerlogin](www.routerlogin)[/COLOR] 0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0Asa comparison, my working wireless says:```
chili@T410:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default        [COLOR="#FF0000"] 192.168.1.1[/COLOR]     0.0.0.0         UG    600    0        0 wlp3s0
link-local      *               255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp3s0

```I'd like to see:```
traceroute www.ubuntu.com
```Mine reads:```
traceroute to www.ubuntu.com (91.189.89.118), 30 hops max, 60 byte packets
 1  [COLOR="#FF0000"]192.168.1.1[/COLOR] (192.168.1.1)  1.962 ms  3.408 ms  3.866 ms
 2  adsl-74-235-172-1.clt.bellsouth.net (74.235.172.1)  19.756 ms  19.947 ms  20.116 ms
 3  70.159.208.135 (70.159.208.135)  20.374 ms  22.423 ms  25.123 ms
 4  12.82.93.229 (12.82.93.229)  28.511 ms  32.048 ms  35.812 ms
 5  12.122.154.162 (12.122.154.162)  48.633 ms  52.352 ms  52.408 ms
 6  cr2.attga.ip.att.net (12.122.30.82)  54.422 ms  25.283 ms  25.356 ms
<snip>
```A very interesting problems you all have cooked up!

---

### Post by blm14 on 2015-11-17
```

$ traceroute www.ubuntu.com
traceroute to www.ubuntu.com (91.189.89.115), 30 hops max, 60 byte packets
 1  www.routerlogin.com (192.168.1.1)  10.067 ms  9.979 ms  9.986 ms
 2  * * *
 3  tge-0-10-0-22.nycmnywi01h.nyc.rr.com (68.173.208.153)  24.533 ms  24.476 ms  25.044 ms
 4  agg116.nyclnyrg01r.nyc.rr.com (68.173.198.48)  27.263 ms  27.243 ms  27.200 ms
 5  bu-ether19.nwrknjmd67w-bcr00.tbone.rr.com (66.109.6.78)  27.168 ms  27.126 ms  27.115 ms
 6  0.ae1.pr0.nyc30.tbone.rr.com (66.109.6.161)  27.071 ms 0.ae0.pr0.nyc30.tbone.rr.com (66.109.6.159)  15.424 ms  15.404 ms
 7  207.239.16.193 (207.239.16.193)  15.350 ms  44.352 ms 207.239.16.25 (207.239.16.25)  14.329 ms
 8  ae1d0.mcr1.nyc-ny.us.xo.net (216.156.1.9)  43.835 ms  71.540 ms  41.493 ms
 9  vb1010.rar3.nyc-ny.us.xo.net (216.156.0.17)  69.845 ms  56.005 ms  69.771 ms
10  ae0d0.cir1.london2-eng.uk.xo.net (207.88.13.201)  134.022 ms  138.577 ms  113.056 ms
11  * * *
12  ae1-core1.thnor.uk.as6908.net (62.149.50.214)  157.796 ms  157.777 ms  162.000 ms
13  ae1-core0.gsld2.uk.as6908.net (62.149.50.33)  150.401 ms  136.645 ms *
14  canonical-gw.datahop.net (78.41.155.186)  135.110 ms  116.274 ms  116.173 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

:-/

---

### Post by Hadaka on 2015-11-17
Hi, big THANK YOU to chili555 !

Seems your netgear router is blocking the pings with it's "routerlogin" active.

 i googled [www.routerlogin.com]("http://www.routerlogin.com") and the fix is there, I tried to go to that
web site but the server was not found, You may have to do the ole toothpick
in the hole routine. This is the first time i have seen this one..its a Netgear thing.

try here ->[http://kb.netgear.com/app/answers/detail/a_id/61/~/how-to-disable-netgear-configuration-assistant-%28welcome-screen-%2F-hijack-screen%29%3F](http://kb.netgear.com/app/answers/detail/a_id/61/~/how-to-disable-netgear-configuration-assistant-%28welcome-screen-%2F-hijack-screen%29%3F)
#Starting at line 3

Please let us know the results.
thanks.

---

### Post by blm14 on 2015-11-17
Will try when I get home tonight!

---

### Post by blm14 on 2015-11-17
The page **[www.routerlogin.com/CA_HiddenPage.htm](www.routerlogin.com/CA_HiddenPage.htm) doesn't exist :(**

---

### Post by Hadaka on 2015-11-18
Hi,I could not access it either,Netgear must have removed the link.
there is a small hole on your router,this is the reset button.Power the router down
push a toothpick or some small item in the hole,hold down the reset button through the hole
power back on the router while still pushing down the button for 20 seconds,this should reset
your router and allow access. This Netgear feature only effects the wireless ,so you can try to
access the routers configuration with a wired access and turn off the wireless log on app. Prior
to the reset method.Changes to the router are best done from a wired connection anyway.This
must be a very old router,you might want to consider replacing it.
keep us updated please.
thanks.

---

### Post by blm14 on 2015-11-18
actually it's a brand new router that I just purchased... Maybe I will just switch to a different one

---

### Post by Hadaka on 2015-11-18
ok, and GOOD NEWS ! I found a link that works,
[http://routerloginnet.us/](http://routerloginnet.us/)
you get actual live help..lower left on screen..the live help
person i got couldnt help me without knowing the model number.
so..you can provide that and hopefully clear the routerlogin app.
I would suggest first trying to access the router with the wired connection
and see if you can turn off the wireless routerlogin feature.
keep us posted

---

### Post by blm14 on 2015-11-19
just a quick update - I haven't yet tried routerloginnet.us because the chat is currently offline, but I did chat with netgear support and was told they do not support linux clients (!!!!!!!!!!!!!!!)

Needless to say I had some strong language to that. I will try routerloginnet tonight when live chat is available.

But keep in mind, linux peeps, if you tell netgear you need help with linux they will tell you that you are SOL. Very poor support policy IMO

---

### Post by tripp98 on 2015-11-19
some routers do not allow access from wireless clients.  you may want to look up the model and see if this is one of them. 

Its just a router.  doesnt matter the client.

---

### Post by blm14 on 2015-11-19
I can access 192.168.1.1 from my iPad through wireless, so that's not it

plus it's not just the router I can't access - I can't access samba shares and other local network resources that I _can_ access from the ipad and other wired clients AND a different laptop running windows

---

### Post by Hadaka on 2015-11-19
you can access all of that with the wire connection from that machine
and you proved clearly that that machine routes wireless to routerlogin

output of route:

 	Code:
 	Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         [www.routerlogin](www.routerlogin) 0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0

so the issue is between the machine and the router, I ask you again, can you...did you
try turning off the router login by logging into the router from that machine..on the wired connection??????

---

### Post by blm14 on 2015-11-20
I am connected to the router via ethernet from another machine right now. There doesn't seem to be a place to disable the router login. That hidden page doesn't exist on my model and I've looked everywhere in settings and don't see a place to do it.

---

### Post by Hadaka on 2015-11-20
Is there a reason you cant access the router with a wired connection from the machine
that the wireless is being blocked by routerlogin ? The only other suggestion would be to
do the online live help and see if they can talk you through it, because it is blocking your
wireless ability to access the router admin pages,tis a quirky netgear security feature.
beyond that i have no further suggestions.
good luck to you.

---

### Post by blm14 on 2015-11-20
The whole point of a laptop is mobility, no? :) If I am using this machine in another room on another floor it's impractical to connect via ethernet.

Live help told me they don't support linux. Like I said I can access the routerlogin pages from wifi on other devices, and I cannot access other local machines via samba shares on this laptop but not I can via the iPad. So the router isn't blocking ALL access to local lan resources because I can access they via wireless from other devices.

---

### Post by blm14 on 2015-11-20
well for reasons that elude me, doing a factory reset on the router seems to have fixed it. I didnt change any settings, just did the reset-button-for-10-seconds-with-a-paperclip on the router, put my wireless SID and password back to my preferred values, rebooted the laptop, and now route -n shows 192.168.1.1 as the gateway and I can ping 192.168.1.1 and access my samba shares. Bizarre, but thanks for all the help!

---

### Post by Hadaka on 2015-11-20
I understand the mobility part,but i suspect that is your only linux machine
ipad and the others were not. anyway glad the reset fixed your problem
please take the time to log back in to your post and click tools..upper right
and mark SOLVED
thanks.

---

