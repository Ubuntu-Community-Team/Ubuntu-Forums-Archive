---
title: "setting up home network... (problem with ip)"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by realmoonstruck on 2009-01-11
I am trying to set up a home network between my laptop and my pc both running Ubuntu.

i followed the instructions given by [mapes12]("http://ubuntuforums.org/member.php?u=472717") from...
[http://ubuntuforums.org/showthread.php?t=1031300&highlight=realmoonstruck&page=3](http://ubuntuforums.org/showthread.php?t=1031300&highlight=realmoonstruck&page=3)
and it worked fine when i connected with my friend's notebook

but now that I'm trying to connect with my own laptop it doesn't work anymore :confused:
well most probably because both of them have the same ip (I'm not sure though)


I think i need to assign a different ip to one of them.

so can u guys help me out with this?

---

### Post by lovelyvik293 on 2009-01-11
You can assign the ip address to any of the network interface just going to
preferences->network configuration.

---

### Post by realmoonstruck on 2009-01-11
my ip is 192.168.1.2

the output of **ifconfig** on my notebook is:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:7b:00:5e  
          inet6 addr: fe80::21e:ecff:fe7b:5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2700 (2.7 KB)  TX bytes:2178 (2.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102994 (102.9 KB)  TX bytes:102994 (102.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:92:13:5f  
          inet addr:[COLOR=Blue]**192.168.1.2**[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe92:135f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8079655 (8.0 MB)  TX bytes:1567103 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-92-13-5F-33-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```but i cant find this address anywhere in the network manager.
so what should i change?

will it be helpful if i post the output of **ifconfig** from mt pc too?

---

### Post by handydan918 on 2009-01-11
> **realmoonstruck said:**
> I am trying to set up a home network between my laptop and my pc both running Ubuntu.

i followed the instructions given by [mapes12]("http://ubuntuforums.org/member.php?u=472717") from...
[http://ubuntuforums.org/showthread.php?t=1031300&highlight=realmoonstruck&page=3](http://ubuntuforums.org/showthread.php?t=1031300&highlight=realmoonstruck&page=3)
and it worked fine when i connected with my friend's notebook

but now that I'm trying to connect with my own laptop it doesn't work anymore :confused:
well most probably because both of them have the same ip (I'm not sure though)


I think i need to assign a different ip to one of them.

so can u guys help me out with this?

Need a little more info about your network. Like what is it?
Cable/dsl? router? Wired/wireless? IOW, we know only what you tell us, which hasn't been much, so far.

---

### Post by realmoonstruck on 2009-01-11
here is the output **ifconfig** from my pc

```
eth0      Link encap:Ethernet  HWaddr 00:17:9a:78:26:d6  
          inet addr:[COLOR=Blue]**192.168.1.2**[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe78:26d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2483534 (2.4 MB)  TX bytes:419482 (419.4 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:314731 (314.7 KB)  TX bytes:314731 (314.7 KB)

```

---

### Post by realmoonstruck on 2009-01-11
my pc is hardwired to the modem. my notebook connects with a wireless connection.

Both are automatically configured by Ubuntu so I don't know much about the connections.

the modem i use is **SIEMENS *SL2_141* ADSL *MODEM***

---

### Post by handydan918 on 2009-01-11
From the notebook, give us the output of ```
lspci | grep -i net
```


And have a look [here]("http://www.indiabroadband.net/bsnl-broadband/7440-sl2_141-nokia-siemens-modem-wifi-configuration.html"), too.

---

### Post by realmoonstruck on 2009-01-11
> **handydan918 said:**
> From the notebook, give us the output of ```
lspci | grep -i net
```

```
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by stevoo on 2009-01-11
Dont give him all this problems. 

Do your 2 pcs get the same ip ? 
If yes restart your router. The router should be responsible or giving an ip to them .

After a restart of the router, you should most probably be ok !

---

### Post by realmoonstruck on 2009-01-11
I'm not using any router to connect the two computers.
I'm just using a simple crossover cable.

please go through the forum thread I posted earlier.
I'm using the ssh server as instructed.

---

### Post by realmoonstruck on 2009-01-11
I don't want to share the net connection.
I just want to facilitate** file sharing **among the two.

This is what i'm doing...
```
I guess what you want is file sharing between linux boxes - there is NO WINDOWS involved. This works for me:

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

     Code:
     sudo apt-get install openssh-server 
2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address

     Code:
     ifconfig 
this should give you an output just like this one

[SIZE=1]eth0 Link encap:Ethernet Hardware Adresse 00:13:77:04:cd:26
UP BROADCAST MULTICAST MTU:1500 Metrik:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Basisadresse:0x6000 Speicher:d2800000-d2820000

lo Link encap:Lokale Schleife
inet Adresse:127.0.0.1 Maske:255.0.0.0
inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
UP LOOPBACK RUNNING MTU:16436 Metrik:1
RX packets:992 errors:0 dropped:0 overruns:0 frame:0
TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:0
RX bytes:30392 (29.6 KB) TX bytes:30392 (29.6 KB)

wlan0 Link encap:Ethernet Hardware Adresse 00:13:02:0f:83:56
**inet Adresse:192.168.18.143** Bcast:192.168.18.255 Maske:255.255.255.0
inet6-Adresse: fe80::213:2ff:fe0f:8356/64 Gültigkeitsbereich:Verbindung
UP BROADCAST RUNNING MULTICAST MTU:1500 Metrik:1
RX packets:237037 errors:0 dropped:0 overruns:0 frame:0
TX packets:200628 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:208782489 (199.1 MB) TX bytes:22525126 (21.4 MB)

[SIZE=1]your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine so, in my case the address would be 192.168.18.143. [/SIZE][/SIZE][SIZE=2]
[/SIZE] 
3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine and away you go!
```as instructed by [mapes12]("http://ubuntuforums.org/member.php?u=472717")

---

### Post by realmoonstruck on 2009-01-11
Actually this works fine...
just that my notebook (or pc) just loads up an image of itself
as the server instead of loading the other computer as the server.

---

### Post by handydan918 on 2009-01-13
OK. Now that the forums are back up....
You DO have a router, not a modem. (Properly, a gateway...)
If you type 192.168.1.1 into a browser, you should get the interface for the router. If you poke around a bit, you can likely find a place where you can "reserve" an address for each device connected to the computer. It is probably best to have BOTH the lappy and the desktop fired up and connected during this process. 

What you want to achieve is a situation where on computer always gets assigned an ip (via dhcp) of 192.168.1.2, for example, and the other always get 192.168.1.3. This is better than static, because the lappy is still set up to look for dhcp, (desirable for cruising starbucks...) while the desktop and the lappy both have consistent ip addresses on your home network. 

Enjoy.

---

### Post by realmoonstruck on 2009-01-15
I didn't find any option to set the getway of the two comps separately.
this is the only place though where the ip was listed...

---

