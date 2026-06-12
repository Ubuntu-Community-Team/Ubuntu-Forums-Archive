---
title: "No internet connection, connected to the network though :/"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by franpa on 2008-11-26
Hello, I am connected to the network manually because Automatic mode tries to use the same IP as our other computer. I can connect to the network correctly by following the instructions @ [https://help.ubuntu.com/8.10/internet/C/networking-enable.html](https://help.ubuntu.com/8.10/internet/C/networking-enable.html) but trying to configure the Internet by following [https://help.ubuntu.com/8.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/8.10/internet/C/modems-adsl-pppoe.html) does not work :/

I assume I am meant to set up my Internet Services username and password somewhere before trying to configure for PPPoE? Yes I do use a PPPoE encapsulated ADSL 1 connection through Ethernet.


EDIT: I also can't set my network mask to 255.255.255.0 like it is under Windows XP :/

---

### Post by TFX360 on 2008-11-26
You're not making a lot of sense.

Give us the output from the following code.


Open a terminal

type:

```
sudo ifconfig eth0
```


Assuming you are using a network card and not connecting through ADSL directly.



Regards,


TFX

---

### Post by franpa on 2008-11-26
Well, I installed Ubuntu 8.10 and it finds my network device, The network adapter does not connect to the network because it tries to use the same IP as my other computer. Where do I go from here? right click the network icon in the top left and edit it to use a valid IP? doing that changes it to a "working connection" but it can't see my other computers and I still can't access the router or the internet :/

Since I do not have a actual working network, I can't provide the output of various commands that easily :S

---

### Post by TFX360 on 2008-11-26
> **franpa said:**
> Well, I installed Ubuntu 8.10 and it finds my network device, The network adapter does not connect to the network because it tries to use the same IP as my other computer. Where do I go from here? right click the network icon in the top left and edit it to use a valid IP? doing that changes it to a "working connection" but it can't see my other computers and I still can't access the router or the internet :/

Since I do not have a actual working network, I can't provide the output of various commands that easily :S

Give us the output whether it's working or not. We can/will see what goes wrong.

---

### Post by franpa on 2008-11-26
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:dd:cd:0b  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3070 (3.0 KB)  TX bytes:2935 (2.9 KB)

---

### Post by TFX360 on 2008-11-26
> **franpa said:**
> eth0      Link encap:Ethernet  HWaddr 00:1b:fc:dd:cd:0b  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3070 (3.0 KB)  TX bytes:2935 (2.9 KB)

Ouch, the network card is broadcasting/multicasting. DHCP is prolly misconfigured on you ADSL router. You connect via an ethernet cable from your router to your computer? If true then check the DHCP settings on your router.

---

### Post by franpa on 2008-11-26
Vista and XP work fine and I can't find any such setting in my router configuration :/

---

### Post by TFX360 on 2008-11-26
> **franpa said:**
> Vista and XP work fine and I can't find any such setting in my router configuration :/

What is the name of your router? Linksys? Draytek?

---

### Post by franpa on 2008-11-26
It is in my signature...

Netcomm nb1300+4 router, ADSL 1, PPPoE LLC Encapsulation
Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

---

### Post by forcumang on 2008-11-26
In your terminal, type **sudo nano /etc/network/interfaces** (you can also replace **nano** with **gedit**, **vim**, **emacs**, or other Ubuntu compatible editors if you prefer), in that file you should to set up a static interface and save it, google has many pages with the format. After reconfiguring your network interfaces, type **sudo /etc/init.d/networking restart**. It should reconfigure it with an output of '[OK]'. Next, type **ifconfig** to check and see if you are interfacing with eth0 (lan 0), if you can see your LAN IP and surf the internet, you're done. If you can't, I am sorry that I couldn't be of more help.

---

### Post by TFX360 on 2008-11-26
> **franpa said:**
> It is in my signature...

Netcomm nb1300+4 router, ADSL 1, PPPoE LLC Encapsulation
Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

Ah, setting an IP-address does not work?

Assuming you have a 192.168.1 network

Administration -> Network -> Connections -> Wired Connection -> Disable roaming mode -> 

IP address 192.168.1.10
Subnet mask 255.255.225.0
Gateway address 192.168.1.1 (Routers IP)

---

### Post by franpa on 2008-11-26
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1


This appears in the Syste Log Viewer when opening Mozilla Firefox.
unmanaged device found; state CONNECTED forced.



EDIT: there is no "Network" option under Administration either.
EDIT: ifconfig still reports UP BROADCAST RUNNING MULTICAST mode, but the rest looks correct according to [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by franpa on 2008-11-26
note: I can now access the router, so we are making progress :) internet still not working.

EDIT: what is pan0? it is a interface I have o_o

I have: eth0, lo and pan0


EDIT: I can ping 220.233.0.4 (My DNS address)
updater detected 15 updates, but can't download them...

according to [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) pppoeconf is only for direct adsl which is not what i have, i have a network card connecting my pc to the router via a ethernet cable.

---

### Post by franpa on 2008-11-26
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1

With this, I can access the network and my dads computer, I can also access the router and Ping [www.google.com](www.google.com). I can not download things from the internet or browse websites.

unrelated: the pan0 interface randomly disappeared after tinkering with it :/ when setting up pppoe connection as directed by Help, it adds the pan0 device.

---

### Post by TFX360 on 2008-11-26
> **franpa said:**
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1

With this, I can access the network and my dads computer, I can also access the router and Ping [www.google.com](www.google.com). I can not download things from the internet or browse websites.

unrelated: the pan0 interface randomly disappeared after tinkering with it :/ when setting up pppoe connection as directed by Help, it adds the pan0 device.

If you can ping google.com you should by all means be able to surf to it!

---

### Post by franpa on 2008-11-26
Firefox doesn't connect though, it is confusing >_< :confused:

---

### Post by TFX360 on 2008-11-26
Prolly a proxy setting gone bad in FireFox? (Edit -> Prefs)

---

### Post by franpa on 2008-11-26
I can...
Ping
Trace
access router
access network

I can not...
browse internet
download packages
download updates

I have tried correct DNS settings.

---

### Post by franpa on 2008-11-26
So how do I improve on the situation? do I have to just give up? I'm not really familiar with configuring and running Linux and can't seem to find anything on a situation like mine :/

---

### Post by TFX360 on 2008-11-27
Can you surf in your browser to 74.125.45.100? If so you have a DNS problem. Then they are incorrectly set in your router.

---

### Post by franpa on 2008-11-27
Ok, since my Windows computer still works, my router DNS settings are now manually configured. I also configured my DNS settings in Ubuntu ($ sudo gedit /etc/resolv.conf).

I can indeed access google directly by there IP, but still can not by there web address.

---

### Post by TFX360 on 2008-11-28
> **franpa said:**
> Ok, since my Windows computer still works, my router DNS settings are now manually configured. I also configured my DNS settings in Ubuntu ($ sudo gedit /etc/resolv.conf).

I can indeed access google directly by there IP, but still can not by there web address.

Could you post the contents again for:

```
sudo ifconfig
```


Thanks

---

### Post by franpa on 2008-11-29
can you provide the IP for these forums, so I can just copy/paste the results into the forums? (I can just save it a TXT file and transfer it over the network then paste it, if not)

---

### Post by TFX360 on 2008-11-29
```
duncan@duncan-laptop:~$ ping -c 5 www.ubuntuforums.org
PING www.ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=48 time=43.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=49 time=38.4 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=50 time=37.0 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=49 time=38.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=5 ttl=49 time=38.0 ms

```

---

### Post by ugm6hr on 2008-11-29
This may be an ipv6 issue.

Try this: [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by franpa on 2008-11-30
I asked on another forum and the internet now works great under Ubuntu :) here is the solution...

/etc/resolv.conf
make sure you have a entry prefixed with **nameserver** followed by your **routers IP address** (EG: nameserver 192.168.1.1). Then add your DNS settings.

---

