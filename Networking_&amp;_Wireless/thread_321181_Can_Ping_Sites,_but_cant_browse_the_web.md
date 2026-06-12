---
title: "Can Ping Sites, but cant browse the web"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Nothing.Face on 2006-12-18
I Installed ubuntu 6.06 recently, and i cant seem to get onto the web.
I can ping pretty much any website i please. but i cant get on any of them except google. i have no clue what im doing and some help would be appreciated. 
thanks.

---

### Post by signius on 2006-12-18
What do you have for your DNS settings and where are you getting your address's from ?

Are you getting all your IP information from a DHCP server or are you using statics ?

---

### Post by Nothing.Face on 2006-12-18
well i tried DHCP first and then static, using all my info from windows.
and they do the same thing. i can ping anyone on my network and any site.
and for my DNS i am using the one from my windows connection. and now i thought that the problem might be that im on a network through a dsl router. i tried it directly from the modem to my comp, same thing. im not sure if it should make a difference anyways.

---

### Post by hal10000 on 2006-12-18
If you can ping, but don't get a connection in your browser, then it's almost sure a nameserver-problem. Look into [COLOR="Red"]/etc/resolv.conf[/COLOR] and if there is not the same as in your windows system edit it by hand, e.g.
```

nameserver 111.222.333.444

``` Of course you have to fill in the ip-address of your provider.

---

### Post by Nothing.Face on 2006-12-18
ok. i tried opening /etc/resolv.conf thought console, but it told me i dont have persmission. so i found it in my system files. and it said the same thing as my default gateway,DHCP, and DNS server for windows. 10.255.252.1

---

### Post by hal10000 on 2006-12-18
You don't have read-permission to /etc/resolv.conf???????
You must have read-permission to that file, because programs running under your user-id (like forefox or other browsers) have to read this file.

So do: [COLOR="Red"]sudo chmod a+r /etc/resolv.conf[/COLOR]
Hope that fixes your problem.

---

### Post by Nothing.Face on 2006-12-18
well i can read it. but not in the terminal. and i can open it in text editor, but i cant save any changes.
well ill go try what you say now and post my results.

---

### Post by Nothing.Face on 2006-12-18
I did what you said, heres a screen of what happened.

[http://i20.photobucket.com/albums/b249/twisted_clown_2250/SCREENSHOT.jpg](http://i20.photobucket.com/albums/b249/twisted_clown_2250/SCREENSHOT.jpg)

---

### Post by dbott67 on 2006-12-18
What is the output of:
```
dbott@thedrake:~$ ls -all /etc/resolv.conf
-rw-r--r-- 1 root root 23 2006-12-15 23:44 /etc/resolv.conf

```

My resolv.conf file just contains the IP of my D-Link router:
```
dbott@thedrake:~$ cat /etc/resolv.conf
nameserver 192.168.1.1

```

Most routers have the capability to forward DNS requests to the ISP DNS servers.  You just need to make sure that the feature is enabled and the router is configured correctly (if you've got other computers on the network or a multi-boot system that work correctly, then chances are the router settings are okay).  See [this post]("http://www.ubuntuforums.org/showpost.php?p=1903456&postcount=5") to verify your router DNS settings.

As for the problem with DNS, can your please describe your network topology (i.e. Ubuntu connected via ethernet to D-Link router connected to DSL modem).  Is the 10.255.252.1 device a router of some sort?

Also, can you please post the output of the following commands:

```
cat /etc/network/interfaces 
```

Here's mine as an example:

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

-Dave

---

### Post by k1001001 on 2006-12-19
I had a similar problem once with being able to ping sites, but not access them. The problem was my DSL router is a piece of junk and is not compatible with IPv6. I don't know what IPv6 is, but it kept me from accessing sites in Firefox and also kept me from connecting to Gaim. It may have also blocked other services such as Frostwire, but I did not try. If this is the case though, then you probably need to disable IPv6.

Try the following:
1. Open Terminal.
2. Type: ```
sudo gedit /etc/modprobe.d/blacklist
```
3. At the end of the file, add this line: ```
blacklist ipv6
```
4. This will get Firefox to work, but not Gaim. To get Gaim and other internet services working, read the "Editing the /etc/dhcp3/dhclient.conf" section at [this]("http://www.ubuntuforums.org/showthread.php?t=282034") thread.

Only do the steps above though if no internet services are working for you though. It doesn't hurt to disable IPv6 I suppose, but I'm not for certain this is the problem you are having, so I don't want to offer useless advice and say that will fix your problem. Just try it and see what happens.

By the way, I don't know if you are new to Ubuntu, but I was looking at your screenshot of your terminal. If you ever type in a command and it comes back "Permission Denied," then just enter the command again with "sudo" in front of it. The "su" part of sudo stands for **S**uper **U**ser, which tells the computer you know what you are doing. It's kind of dumb, but I guess it keeps absolute idiots from going in and messing up their system configuration files. [Here]("http://xkcd.com/comics/sandwich.png")'s a good comic that reminds me of that though.

---

### Post by vorsia on 2006-12-20
Right on k1001001!

Turns out my router is also of low quality and your solution turned a pos router into an almost bearable router!

---

### Post by handy on 2006-12-20
> **Nothing.Face said:**
> I Installed ubuntu 6.06 recently, and i cant seem to get onto the web.
I can ping pretty much any website i please. but i cant get on any of them except google. i have no clue what im doing and some help would be appreciated. 
thanks.

It looks like an IPv6 problem here too.

Have a [**_look at this how-to_**]("http://ubuntuforums.org/showthread.php?t=282034") for a couple of internet fixes.

---

