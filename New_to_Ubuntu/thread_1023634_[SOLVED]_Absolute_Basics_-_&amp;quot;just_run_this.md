---
title: "[SOLVED] Absolute Basics - &amp;quot;just run this code&amp;quot; but how?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Sour Mash on 2008-12-28
As I blunder my way around xubuntu I find that I can't figure out the basics! Lot's of posts say "run this code" or "use this command" but I can't see an obvious place to actually type in these commands. There doesn't seem to be an equivalent of a "DOS box" but then I'm sure I'm not looking for the right thing and wouldn't recognise it if it was wearing a T shirt and shimmying across the screen :(

Please gently and deliberately point me in the right direction - thanks.

Current projects are

1. Get Wireless working (I see the network but it simply won't connect)
2. Change the screen resolution so that it fills the screen, none of the options in settings work.
3. Hand it over to my 12 year old to break

---

### Post by shifty_powers on 2008-12-28
it is called the terminal.

in xubuntu, [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

and read the whole site it will be a godsend, trust me...

---

### Post by 5BallJuggler on 2008-12-28
you need to open a package called "Terminal", it's under Applications - Accessories

you may need to type "sudu" at the start of the command line, you will then be asked for your system password.

then hey presto...

---

### Post by shifty_powers on 2008-12-28
close. the command is

```
sudo apt-get install thunderbird
```

as an example. it means super user do, and give you temporary admin access, known as root access. read psychocats, it will tell you a lot about it all...

---

### Post by Sour Mash on 2008-12-28
You lovely people you :P

I feel far more dangerous now ):P

Right, now to see if I can figure out the screen resolution thing.

---

### Post by 5BallJuggler on 2008-12-28
> **5BallJuggler said:**
> 
you may need to type "sudu" at the start of the command line, you will then be asked for your system password.


oops.... that was a typo i meant "sudo"

sorry

---

### Post by Sealbhach on 2008-12-28
You should be able to adjust screen resolution in System/Preferences/Screen Resolution.

For your wireless, please paste these commands in the terminal

```
lshw -C network
```

```
ifconfig
```

```
sudo dhclient wlan0
```


and copy and paste the results here. It may give us some clues...


.

---

### Post by Sour Mash on 2008-12-28
> **Sealbhach said:**
> You should be able to adjust screen resolution in System/Preferences/Screen Resolution.

[COLOR="SeaGreen"]My problem is not selecting the available settings it's that these settings are nowhere near where they should be. The monitor now has 800x600 but the screen is capable of showing 1024x768 - according to the documentation here 
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/portege_7140ct.pdf]("http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/portege_7140ct.pdf")
[/COLOR]

For your wireless, please paste these commands in the terminal

```
lshw -C network
```


```
ifconfig
```

```
sudo dhclient wlan0
```


and copy and paste the results here. It may give us some clues...


.

[COLOR="seagreen"]OK I'll do that, will have to get onto the subject machine to copyt and past the outputs [/COLOR]

---

### Post by Sour Mash on 2008-12-28
Here's the results of ```
lshw -C network
```

WARNING: you should run this program as super-user.
  *-generic DISABLED      
       description: IRDA interface
       product: FIR Port Type-DO
       vendor: Toshiba America Info Systems
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: irda0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list irda logical
       configuration: driver=donauboe latency=64 module=donauboe
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 6c
       serial: 00:00:39:c2:21:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.104 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:30:4f:24:b2:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+

Others follow

---

### Post by Sour Mash on 2008-12-28
Response to the command [PHP]ifconfig[/PHP]
eth0      Link encap:Ethernet  HWaddr 00:00:39:c2:21:24  
          inet addr:192.168.1.104  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fec2:2124/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2059614 (1.9 MB)  TX bytes:362709 (354.2 KB)
          Interrupt:11 Base address:0xcf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2000 (1.9 KB)  TX bytes:2000 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:30:4f:24:b2:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x1800 

More follows for the last command

---

### Post by Sour Mash on 2008-12-28
and finally, here's the response to ```
sudo dhclient wlan0
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:30:4f:24:b2:c1
Sending on   LPF/wlan0/00:30:4f:24:b2:c1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I hope all this means something to you :confused:

---

### Post by Sour Mash on 2008-12-28
Just a thought, should this now become a new thread with a better title?

---

### Post by Sour Mash on 2008-12-28
I'm really cooking now, solved my display issue with a thorough search of the forums and this ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by gn2 on 2008-12-28
Your ACX100 wireless chipset should "just work"...

Instead of using the Network icon in the panel, use the Network shortcut in the Applications or System menu (wherever it is, my memory of Xfce is a bit rusty) to create a connection.
Assign it a fixed I.P.
As far as I remember from my own ACX100 adapter that I used to have, it will not handle WPA, it's WEP only.
Also enter the I.P. of your DHCP server (router) in the relevant tab.

---

### Post by Sour Mash on 2008-12-28
Thanks for the reply, first things first, I can't see a non-secured option when setting up a connection. I don't use any security at the moment, I'm not in a "vulnerable" area and there are currently quite a few devices connecting from friends and family.

The options are 
[LIST]
[*]WEP key (hexadecimal)
[*]WEP key (ascii)
[*]WPA Personal
[*]WPA2 Personal
[/LIST]

There is something called "Enable roaming mode" at the top and when that's active then the security options are locked out - so is this the "use no security" option? If that's selected then no more options are available

---

### Post by shifty_powers on 2008-12-28
is it actually able to sacn for networks?

```
sudo iwlist scan
```

---

### Post by appi2012 on 2008-12-28
Roaming simply means that it will look for other networks, and not simply connect to a default one. When roaming is enabled, you can click on the network icon in your notifications area, and it will show you the available wireless networks. You can then click on the one you want, and enter the security password if needed. You can also create your own wireless network if you want. 

Hope that helps.

---

### Post by Sour Mash on 2008-12-28
> **shifty_powers said:**
> is it actually able to sacn for networks?

```
sudo iwlist scan
```

Here's the result - Mission Control is the network I'm aiming at

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:9E:D3:49:AD
                    ESSID:"TalkTalkc2f68"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=0/100  Signal level=29/100  Noise level=34/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:16:E3:12:9B:0C
                    ESSID:"BTVOYAGER2500V-0C"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=0/100  Signal level=29/100  Noise level=42/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:14:78:E4:86:3E
                    ESSID:"Mission Control"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/100  Signal level=100/100  Noise level=31/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:23:4D:11:CA:35
                    ESSID:"NYC"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/100  Signal level=1/100  Noise level=41/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:1B:2F:3C:C9:90
                    ESSID:"Wallace"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level=23/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:14:7F:2B:27:6A
                    ESSID:"SpeedTouchA149C7"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=7/100  Signal level=28/100  Noise level=21/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by Sour Mash on 2008-12-28
> **appi2012 said:**
> Roaming simply means that it will look for other networks, and not simply connect to a default one. When roaming is enabled, you can click on the network icon in your notifications area, and it will show you the available wireless networks. You can then click on the one you want, and enter the security password if needed. You can also create your own wireless network if you want. 

Hope that helps.

That does explain the roaming thing, I've found the available networks list. I still can't connect to any though :-(

Thanks

---

### Post by Sealbhach on 2008-12-28
It looks like your router is not assigning your computer an IP address (I assume wired connection works fine?).

Try to ping the router, it should do it with this

```
ping -c 5 192.168.0.1
```

or

```
ping -c 5 192.168.1.1
```

Just see if you get a response. It would be a good idea to look at the documentation that came with it to make sure you have the correct WEP or whatever settings you had.

also, try to ping an external site, see if you can get anything:

```
ping -c 5 132.185.240.21
```

and

```
ping -c 5 bbc.co.uk
```


.

---

### Post by Sour Mash on 2008-12-28
Pardon my ignorance but I don't understand this - laptop is connected to the router via a wire at the moment, all works OK. Other laptops and PDAs connect wirelessly to the router OK (Ubuntu, Windows XP and Windows Mobile).

If I try and connect wirelessly it fails so how can I ping it wirelessly or am I missing something?

If I ping it now, wired, then I get

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4010ms

I am confuddled :confused:

---

### Post by gn2 on 2008-12-28
Some routers are normally 192.168.1.1
Which would explain getting nothing back from pinging 192.168.0.1

---

### Post by MenZa on 2008-12-28
You'll want to run them in the terminal, which can be found in Applications &#8594; Accessories &#8594; Terminal.

For your other issues, feel free to create a thread for each of them. That's your best bet on how to get an answer.

---

### Post by Sour Mash on 2008-12-28
> **gn2 said:**
> Some routers are normally 192.168.1.1
Which would explain getting nothing back from pinging 192.168.0.1

I'm in your hands here as my knowledge of these things is scant.

I opened a fresh ping and this is what I got

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.648 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.626 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.646 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.621 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.644 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.621/0.637/0.648/0.011 ms

---

### Post by Sealbhach on 2008-12-28
> **Sour Mash said:**
> 
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.644 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.621/0.637/0.648/0.011 ms

OK, so it's talking to the router and the router is talking back - assuming that's done wirelessly?

If so, that means you don't have any really big problems, it's just a matter of getting the right settings in your network configuration. 

Are you using xubuntu 8.10 or 8.04? There's a newer network manager in 8.10 that maybe will handle the connection process better.

Yeah, and it might be better to start a new thread about this.

.

---

### Post by 73ckn797 on 2008-12-28
> **Sour Mash said:**
> Pardon my ignorance but I don't understand this - laptop is connected to the router via a wire at the moment, all works OK. Other laptops and PDAs connect wirelessly to the router OK (Ubuntu, Windows XP and Windows Mobile).

If I try and connect wirelessly it fails so how can I ping it wirelessly or am I missing something?

If I ping it now, wired, then I get

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4010ms

I am confuddled :confused:

I will assume that when you are trying to connect wirelessly that you have selected that from the icon at the top right side? or wherever it may be in Xubuntu. Could be that you have not told it to connect to a wireless conenction. 

I will also assume that you know to set security through the router.

---

### Post by sofasurfer on 2008-12-28
For generally learning how to may Linux do stuff try this... [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

Tons of basic knowledge that you need and its written for beginners.

---

### Post by Sour Mash on 2008-12-29
Guys, I'm all confused now. The machine is connected via a wired connection so when I do this ping thing then surely all that's doing is using the wired connection to ping the router, ie testing a connection we know is working.
If it won't connect wirelessly then how can I ping the router?

When I disconnect the cable and click on the connections icon in the top right I can choose my network but all that happens is that it tries but can't connect.

Once I know what I'm doing with this ping thing then I'll starts a fresh thread.

Thanks for your interest so far :-)

Oh and how would I upgrade xubuntu? I've run all the updates etc but I don't know how to move up a version.

---

### Post by Sour Mash on 2008-12-29
I figured out the update thing - well that's a lie, I figured out that the forum search is pretty good and more useful at finding answers than any other forum search I've used. I also found that the release names bear an uncanny resemblance to Dilbert project names - Intrepid Ibex here we come :-)

---

### Post by Sealbhach on 2008-12-29
> **Sour Mash said:**
> I also found that the release names bear an uncanny resemblance to Dilbert project names - Intrepid Ibex here we come :-)

Oh, OK, so you're going to install Intrepid Ibex? That's got a brand new Network Manager which is a lot better at handling connections - it fixed my wireless problems whereas the previous version didn't. Well, see how you get on with that and if you still have problems start a new thread.

The ping thing is just to eliminate possibilities really, it's difficult to narrow down the area where the fault is. Often you can ping even though it appears that the network is not working.

Good luck!

.

---

### Post by theozzlives on 2008-12-29
I noticed that your wireless is 802.11b, if you're using a wireless   access point that is only capable of 802.11g then that may be it.

---

### Post by Sour Mash on 2008-12-29
Thanks guys, the update is going OK - I left it running whilst I was out, it has about 30 mins left :-) I'll post back here on how it went, just to close this chapter and then I'll start a new thread for any further issues.

I'm really impressed with this place and the help I'm getting - thank you all :KS

---

### Post by Sour Mash on 2008-12-29
Ahhhhh!!! It's all gone wrong! I have a blank screen, a blinking cursor that I can't type at and the Caps Lock light is flashing. 
Pushing keys does nothing, not even the PrtSc button helps thing time. I'm crushed.

I'll start a new thread now.

---

### Post by Sour Mash on 2009-01-02
I know I marked this close but let me put some proper closure on it - the uipdate screwed my system and I have to reinstall 8.04 to get it to respond again. I "solved" the WiFi issue by changing the WiFi card to a 3Com one I had and it worked fine.
I've started other threads for separate issues.

---

