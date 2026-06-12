---
title: "Netgear DG834G v4 router connects/drops out"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by hosssbosss on 2011-04-15
Hi all! I'm new to Ubuntu, and am just getting things set up, but I'm having a frustrating time with my router.
 After startup, it should auto connect to my Netgear (which is password protected), but for some reason prefers to connect to a neighbour's router instead. I have to manually select my own router by clicking on the wireless symbol up the top, although it doesn't usually connect unless I switch the router off then on again. If I do this, then it seems to connect ok, but only for a few minutes, then disconnects and switches back to my neighbours! If I try to connect again after the connection drops out, then it just sits there attempting to make a connection for a few mins, then stops.
Hopefully this is just a simple fix, and I'll be on my way - can anyone help me out please?!

Quentin

---

### Post by jtarin on 2011-04-15
It sounds as if neither router has been setup. You can access the router interface by typing.... [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1....in](http://192.168.1.1....in) the url bar of your browser. Is your computer hardwired to your router with a LAN cable? I don't understand how it accesses your neighbors router.

---

### Post by hosssbosss on 2011-04-15
I should mention that the re-connection is somewhat intermittent - I just attempted to connect after pulling the Netgear WG111v3 usb adapter out and plugging it back in, and it connected, although this has now failed and gone back to the neighbours once again. Pulling the usb, and switching the router on/off gives me temporary internet...

---

### Post by hosssbosss on 2011-04-15
Hi jtarin, thanks for your quick reply :)

My router is wireless, and my neighbours internet is unsecured, so that's how I can access it. I'll have a crack at throwing that into the url...

---

### Post by hosssbosss on 2011-04-15
The connection has timed out

      The server at 192.168.0.1 is taking too long to respond.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

This is what happens when I type those in - it just seems to time out, and nothing happens?

---

### Post by jtarin on 2011-04-16
Try pinging the addresses in a terminal. Also in a terminal issue the command ```
route -n
```and post results.
Doesn't your neighbor have enough bandwidth for you? :)

---

### Post by Paqman on 2011-04-16
You can stop your computer from connecting to your neighbour's router. Right click on the wifi icon, go into the settings for your neighbour's network and uncheck the "connect automatically".

---

### Post by Enigmapond on 2011-04-16
> **Paqman said:**
> You can stop your computer from connecting to your neighbour's router. Right click on the wifi icon, go into the settings for your neighbour's network and uncheck the "connect automatically".

Also when you right-click you will see "Edit Connections" Just remove any others but yours off the list.

---

### Post by hosssbosss on 2011-04-17
bash: [http://192.168.0.1:](http://192.168.0.1:) No such file or directory

Ok...this is what happens when I put the router's address into the terminal. Not ideal I'm guessing!

And when I punch in route -n this is what comes up...

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

I have changed the neighbours routers so that they don't auto connect, but this doesn't make any difference as far as my own is concerned...and I kinda need theirs as a temporary source of internet access haha! Not sure on their bandwidth!

---

### Post by jtarin on 2011-04-17
> **hosssbosss said:**
> bash: [http://192.168.0.1:](http://192.168.0.1:) No such file or directory
The command to enter is ```
ping 192.168.0.1
```or ```
ping 192.168.1.1
```this is to see if the destination is reachable.

Also post the results of the command when connected to your router only```
ifconfig
```

---

### Post by hosssbosss on 2011-04-18
qball@qball-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.91 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.94 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=5.06 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=4.06 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=2.93 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=64 time=1.69 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=64 time=1.81 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=64 time=2.31 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=64 time=1.68 ms
64 bytes from 192.168.0.1: icmp_req=10 ttl=64 time=1.95 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=64 time=1.92 ms
64 bytes from 192.168.0.1: icmp_req=12 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=14 ttl=64 time=1.81 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=64 time=2.05 ms
64 bytes from 192.168.0.1: icmp_req=16 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=17 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=18 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=19 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=20 ttl=64 time=1.81 ms
64 bytes from 192.168.0.1: icmp_req=21 ttl=64 time=2.05 ms
64 bytes from 192.168.0.1: icmp_req=22 ttl=64 time=2.56 ms
64 bytes from 192.168.0.1: icmp_req=23 ttl=64 time=1.30 ms
64 bytes from 192.168.0.1: icmp_req=25 ttl=64 time=1.25 ms
64 bytes from 192.168.0.1: icmp_req=26 ttl=64 time=2.05 ms
64 bytes from 192.168.0.1: icmp_req=27 ttl=64 time=1.93 ms
64 bytes from 192.168.0.1: icmp_req=28 ttl=64 time=1.93 ms

It seems to just keep scrolling up with more and more of the same after pinging that one.

Whereas the second just comes up with this.

qball@qball-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

...and ifconfig spits out this...

qball@qball-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:1d:21:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:cd:ed:55  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fecd:ed55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2011077 (2.0 MB)  TX bytes:548867 (548.8 KB)

---

### Post by hosssbosss on 2011-04-18
Oh and all that was done whilst connected to my own router...

---

### Post by jtarin on 2011-04-18
Open "Network Connections" if you have your wireless connection configured click on it and choose "edit".In "Device Mac Address" type ```
00:1b:2f:cd:ed:55 
```and close. Let me know the results.

---

### Post by hosssbosss on 2011-04-19
Hi jtarin,

Well so far it looks like you have the midas touch! This morning before work I did what you last instructed, and thought I would leave the pc on all day, and when I got home it was still connected - happy days so far!:p

Thanks so much for your help with this, although I don't want to count my chickens just yet...

Just curious, what exactly did that last command do?

---

### Post by jtarin on 2011-04-19
> **hosssbosss said:**
> Hi jtarin,

Well so far it looks like you have the midas touch! This morning before work I did what you last instructed, and thought I would leave the pc on all day, and when I got home it was still connected - happy days so far!:p

Thanks so much for your help with this, although I don't want to count my chickens just yet...

Just curious, what exactly did that last command do?Do you mean ```
ifconfig ????
``` [Here's a link.]("http://en.wikipedia.org/wiki/Ifconfig") The last one in the configuration is your wireless connection device. I had you enter the MAC address (also known as the Hardware Address) of your wireless point.Every one is unique so now your network connection will only connect to a point that has that address. If you should change connections then you will need to discover your new identifier. The same solution can be applied to ethernet cards as they have unique identifiers also. I don't use wireless but there is another tool that is used for wireless similar to "ifconfig"....it's called "iwconfig". You can read more [here.]("http://en.wikipedia.org/wiki/Wireless_tools_for_Linux") You still need to get into your router and configure its security if thats important to you.

---

### Post by hosssbosss on 2011-04-25
Hi again jtarin,

Sorry if you've been wondering where I was (easter holiday), but better late than never I guess! 

When I returned and fired the pc up, I noticed that I had the same problem I was having before. I ended up running through the same procedure you helped me do, and it's running ok at the moment. Does it make sense to you that it would return to it's old tricks once more? I was away for a few days, so the pc wasn't switched on for that time obviously.

---

### Post by jtarin on 2011-04-25
It depends on how you have it connect when it first boots. What did you change to get it working again?

---

### Post by hosssbosss on 2011-04-25
Well, initially I tried turning the router off/on, but to no avail, so after that, I ran through the same steps you led me through to get it working previously. Didn't actually change anything as such...

---

### Post by jtarin on 2011-04-25
So all settings were the same?

---

### Post by hosssbosss on 2011-04-25
Yes I believe so - I wasn't going to mess with the formula that worked in the past! Hopefully this one sticks!! Strange that it wouldn't connect you think?

---

### Post by jtarin on 2011-04-25
Try setting your router as the default gateway....according to your info above its address is 192.168.0.3. [Here's a link on how to do that.]("http://www.cyberciti.biz/faq/howto-debian-ubutnu-set-default-gateway-ipaddress/"). You don't have to use "Vi" you can just issue the command "gksudo" and the Gnome gedit will open and make your way to the file as root and edit.

---

### Post by hosssbosss on 2011-04-25
Ok I'll give that a go tomoz - I have to go for now. Thanks again for your help:)
I'll let you know how I go!

---

