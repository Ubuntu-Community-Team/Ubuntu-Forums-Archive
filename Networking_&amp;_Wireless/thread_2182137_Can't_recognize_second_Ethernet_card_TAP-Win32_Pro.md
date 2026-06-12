---
title: "Can't recognize second Ethernet card TAP-Win32 Provider OAS"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by tommysmith2 on 2013-10-20
Hi, I'm running Win 7, and I tried to add one more Ethernet Card for testing in Virtualbox, I have old one (TAP-Win32 Provider OAS - I don't remember name of card but I see it in Device Manager), so I use it for testing. My trouble is Win 7 & Virtualbox recognize it, but when in Debian 7 / Ubuntu Server and Desktop 13.04/13.10 - it show that the eth DOWN, I had tried to ifup, and just plugin the second one, but it still don't auto get the ip from DHCP.

I don't know the problem by my old Card or from Ubuntu, if from my card, I'll buy new thing, but if from server, I hope can solve it. Thanks for any help :D

---

### Post by varunendra on 2013-10-22
Hello tommysmith2, and Welcome to the forums !

Have you checked if the card has a driver associated with it? Please show us the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
nm-tool
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by tommysmith2 on 2013-10-22
> **varunendra said:**
> Hello tommysmith2, and Welcome to the forums !

Have you checked if the card has a driver associated with it? Please show us the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
nm-tool
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.


Thanks Varunedra for your help :) This is sreenshot from virtualbox running Ubuntu Server 13.10 I had took, and the Code too:

```

**uname -mr**

3.11.0-12-generic x86_64

```

```

**lspci -nnk | grep -iA2 net**

00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet C
ontroller [8086:100e] (rev 02)
        Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
        Kernel driver in use: e1000
--
00:08.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet C
ontroller [8086:100e] (rev 02)
        Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
        Kernel driver in use: e1000

```

```

**ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 08:00:27:e5:97:24
          inet addr:192.168.10.32  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fee5:9724/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:257662 (257.6 KB)  TX bytes:8050 (8.0 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:d1:52:6a
          inet addr:192.168.10.36  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fed1:526a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1108949 (1.1 MB)  TX bytes:70617 (70.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

**cat /etc/network/interfaces**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

```

**nm-tool**

NetworkManager Tool

State: connected (global)

- Device: eth1 ------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unmanaged
  Default:           no
  HW Address:        08:00:27:D1:52:6A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on


- Device: eth0 ------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unmanaged
  Default:           no
  HW Address:        08:00:27:E5:97:24

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

```

Ah, this is the result from my new NIC, I can't waiting so I had buy a new one, but it's still have some trouble => Server can see too NIC but can't "use" two NIC.

It's mean I had testing in Win 7, new NIC can running ok, I also had setting 2 NIC in VirtualBox with 2 "Bridged Adapter" for 2 NIC; the Server Ubuntu (Desktop - Server) / Debian/ Centos can see, and I can ping two IP setting with DHCP for 2 eth0 & eth1. However, when I tried to ifdown eth0/eth1 (The Ethernet I set for NIC Onboard), it's can ping to the Internet, but If I down the New NIC, so server can running the other onboard NIC :confused:

I also had testing just using the New NIC Bridged Adapter, it's can running ok, the problem just happend when I down the onboard NIC, I don't know why !?!

---

### Post by varunendra on 2013-10-22
Sorry I'm not sure I understand this part correctly -
> **tommysmith2 said:**
> However, when I tried to ifdown eth0/eth1 (The Ethernet I set for NIC Onboard), it's can ping to the Internet, but If I down the New NIC, so server can running the other onboard NIC :confused:

I also had testing just using the New NIC Bridged Adapter, it's can running ok, the problem just happend when I down the onboard NIC, I don't know why !?!
..so please confirm if this is what you mean to say -

[indent]**1)** You have got both your ethernet interfaces working by replacing the add-on card (the New one).

**2)** You have also successfully bridged them to the virtualbox virtual adapters.

**3)** The network, the Internet, and the bridging in virtualbox - **all work fine when both interfaces are "UP"**. So no problem so far.

**4)** The network and Internet keep working when you "Down" the add-on (the New one) NIC. So no problem even in that case..

[COLOR="#FF0000"]**5)** However, you can not access the internet as soon as you "Down" the onboard NIC ![/COLOR][/indent]

Please confirm if the above are correct or not. Please correct whichever is wrong.

If all the above assumptions are true, I believe the local network keeps working when the onboard NIC is disabled (only the internet stops working). Is this correct too?

If all of this is true, then I think I may have an easy solution for you, just post back the output of -
```
route -n
```

---

### Post by tommysmith2 on 2013-10-23
> **varunendra said:**
> 
Thanks you Varunendra, but when I tried several tens of testing, it's hack my mind @@

[INDENT]**1)** You have got both your ethernet interfaces working by replacing the add-on card (the New one).
**Yes, my new NIC working both on Win 7 and in Virtualbox (Ubuntu & Centos) with testing in both Adapter 1 &2.**

**2)** You have also successfully bridged them to the virtualbox virtual adapters.
**Yes, I choose "Bridged A****dapter" in Network** **in turn Adapter 1 & 2 and working fi****ne.**

**3)** The network, the Internet, and the bridging in virtualbox - **all work fine when both interfaces are "UP"**. So no problem so far.
**Yes, when Bridaged Adapter 1&2 with same New NIC or 1 New & 1 Old** **- All working fine (testing ping google.com) when they UP.**

**4)** The network and Internet keep working when you "Down" the add-on (the New one) NIC. So no problem even in that case..
**Yes and....Noop, this is hacking my mind @@ sometime they can ping, some time they can't when I tried DOWN them with many cases I had tested. I think this is mistake by Virtualbox, not NIC, I tried with 2 Adapter 1-2 : Same Old, Same New, Old-New, New-Old with Ubuntu and CentOS. However, the funny thing is sometime when I DOWN one NIC (whatever New or Old)****, they can ping but sometime they can't ping (unknow host) and they can different result with CentOS when I testing **](*,)

[COLOR=#FF0000]**5)** However, you can not access the internet as soon as you "Down" the onboard NIC ![/COLOR]
**Not really. The reason above ****^^**
[/INDENT]
 
If all the above assumptions are true, I believe the local network keeps working when the onboard NIC is disabled (only the internet stops working). Is this correct too?
**I had testing when take out the cable Onboard NIC - the Old one, the internet or network still working fine, I think it switch in New NIC.**

If all of this is true, then I think I may have an easy solution for you, just post back the output of -
```
route -n
```


**This is the result in Adapter 1 - Old , Adapter 2 - New:**

```

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

---

### Post by varunendra on 2013-10-23
Okay, so some things cleared up, and something new came out of the picture. Please confirm these -

[indent]**1)** You have only Windows running as "Host". All the other operating systems (Ubuntu/Centos/Debian etc.) you are talking about are "Guests" running inside Virtual Machines on virtualbox.

**2)** When you say "Up" or "Down" NIC, you mean the "Virtual" adapters "Inside" virtualbox, not the physical ones in your physical box.

**3)** There is No **Fixed** Pattern or Case about when they would work or when they won't, when "Any" one of them is down. Means - If you disable (down) eth0, the guest sometimes stays connected to Interned, sometimes not. Same when you disable eth1.

**4)** It Does Not matter which "Physical" NIC (or NICs) you have bridged eth0 and eth1 to. The above behaviour remains the same.[/indent]

I hope I am understanding your problem a little better this time. Earlier, I thought you were talking about "Host" OSes, not guests.

Please provide some more description on how you have bridged the virtualbox adapters, and post screenshots (cropped to make it small) showing the two adapters' settings as well. For example, my virtual adapter 1 is attached to "eth0" -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247190[/IMG]

And, IF I'm understanding correctly this time, you may have to keep a record of different cases when Internet does not work "in the Guest", and the output of "route -n" command corresponding to each case. I may need to look at them if a general approach doesn't work.

**PS:**
Reading and understanding [post=12819114]this post[/post] may help you understanding the routing table and its behaviour a little better, and may lead you to the solution you need.

---

### Post by tommysmith2 on 2013-10-24
> **varunendra said:**
> 

Thanks your link, I'm not read all yet, but it can help something more clearly :D[INDENT]**1)** You have only Windows running as "Host". All the other operating systems (Ubuntu/Centos/Debian etc.) you are talking about are "Guests" running inside Virtual Machines on virtualbox.

[B]Yes, I'm running Win 7 for "Host", and other Linux OS for "Guest" in Virtualbox
Ah, one extend question :D I see Virtualbox have funtion copy/paste switch Host vs Guest, but even I had checked it, I'm still can't copy code between them, so I had using putty to ssh for copy/paste code, I don't know I had missing something not check yet !?![/B]

**2)** When you say "Up" or "Down" NIC, you mean the "Virtual" adapters "Inside" virtualbox, not the physical ones in your physical box.

**Yes, I just using ifdown and ifup inside Linux Virutalbox, not in real NIC cable in Host.**

**3)** There is No **Fixed** Pattern or Case about when they would work or when they won't, when "Any" one of them is down. Means - If you disable (down) eth0, the guest sometimes stays connected to Interned, sometimes not. Same when you disable eth1.

[B]Oh, it's really not, after I read your topic, I know why "sometime" happend :D When I Down an eth0(1) and it's "sometime" cut off network because I Down the eth0 bridged with reach gateway when I checked in route -n. 

But the crazy is when I restart (init 6) Ubuntu, it's still have same route configurations, it's mean don't change the eth (ex: eth0) reach with gateway, but if I "restart" (init 0), shutdown and turn on Ubuntu, it change the eth (become eth1) connect with gateway and make me thing "sometime" it's crazy cauze I don't realize it's different between restart and shutdown @@[/B]


**4)** It Does Not matter which "Physical" NIC (or NICs) you have bridged eth0 and eth1 to. The above behaviour remains the same.

Yes, when I change NICs in Adapter 1&2, it's still have same situation with above.
[/INDENT]

[ATTACH=CONFIG]247206[/ATTACH][ATTACH=CONFIG]247207[/ATTACH]


** So the Myth is just I don't understand why the eth connect gateway different in "restart" and "shutdown" =]]**

---

### Post by varunendra on 2013-10-24
> **tommysmith2 said:**
> I see Virtualbox have funtion copy/paste switch Host vs Guest, but even I had checked it, I'm still can't copy code between them, so I had using putty to ssh for copy/paste code, I don't know I had missing something not check yet !?!
Generally, you just have to install "Guest Additions" *(Devices > "Install Guest Additions.." from the menu of a running virtual machine)* within the guest OS to get that functionality. It is like installing the drivers for the 'virtual hardware' the virtual machine provides. You should also know that it allows only copy-pasting of "Text" between host and guest, not objects. For object sharing, you can create a "Shared Folder" between host and guest, which also requires the Guest Additions to be installed. If this doesn't answer your above question, or you are having problem installing Guest Additions, you should ask your question in a different thread under [Virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308") section.

> when I restart (init 6) Ubuntu, it's still have same route configurations, it's mean don't change the eth (ex: eth0) reach with gateway, but if I "restart" (init 0), shutdown and turn on Ubuntu, it change the eth (become eth1) connect with gateway and make me thing "sometime" it's crazy cauze I don't realize it's different between restart and shutdown @@
To be honest, I am not sure either, maybe it is the 'DHCP cache' thing. But you can always use "route add default gw <gateway IP>" command to manually add a gateway route using whichever interface is left up. Or you can use manual IP/gateway assignment to both interfaces. I *think* that automatically takes care of it.

As a last and ugliest resort, you can create a script to automatically take care of it depending upon whichever interface is left. If you need help with that, I would need the output of route -n for all the cases to make sure the script is perfect.

---

### Post by tommysmith2 on 2013-10-25
Cool, it's working to add gateway for second eth when down the interface that reach the gateway.

Ah, actually, when I know sometime I can't ping by down an interface which reached gateway, I think it normally, jut up it. However, when I think what happen if that interface really down or crash in the reality, so the other interface remain will not auto replace the broken one and auto reach the gateway ?

The route -n it's same above :

```

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

---

### Post by varunendra on 2013-10-26
If you want the second interface to automatically take over the route to the gateway in case when the first one crashes, just assign manual IP and gateway to both. I tested that here with manually assigned IPs in virtualbox, and it works the same way.

Although I don't see why it shouldn't happen with DHCP assigned IPs as well. Maybe the DHCP offers the gateway to both, but the system only 'Takes' it for the primary one.

---

### Post by tommysmith2 on 2013-10-26
How to assign Gateway for both NICs !?! Cuz when I add the gw IP in route add, it's just said that IP already have, I'm only add it when the NIC reach the gw down and make gw IP lost.

---

### Post by varunendra on 2013-10-26
If using desktop environment, you can save the manual settings in the network manager. If using a GUI-less (server) system, the place to save them is /etc/network/interfaces file (see [this wiki page]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing") and scroll down to "Static IP Address" section)

---

### Post by tommysmith2 on 2013-10-27
Oh, I tested add gw for NIC in :

+ route add default gw 10.0.0.1 eth0[1] - and I check both NIC reached gw, but after that I can't ping, maybe it's make something conflict !!!

+ After that, I tried add static IP with same gw for both NICs, but in route -n, it's still just one eth reach gateway and if I down an IP reach gw, it's not auto switch for the second one. I think if a server "live" and running continuous, if an NIC down and restat server, Ubuntu will realize and auto configuration gateway for the second, but we can't restart a server to solve it huh !?!

---

### Post by varunendra on 2013-10-27
Can't say about server, but in the default GUI here, it happens pretty smoothly. Maybe Network Manager is taking care of it.

Also, regarding this -
> I check both NIC reached gw, but after that I can't ping, maybe it's make something conflict
Not a conflict, maybe the route was lost. You can always check the effective routing table with "route -n". Perhaps there are certain 'Server-specific' ways to check and configure that, but I'm not familiar with any others.

For any substantial help or advice on the problems you are having, it would be best if you also post the "route -n" output pertaining to each problem case.

---

### Post by tommysmith2 on 2013-10-28
Hi thanks, at least I know what happen with both NICs and solve it manually :D but what about the scripts you said before? it's automatically "take care" - it's mean auto add the gw for the second whichever the first left?

---

### Post by varunendra on 2013-10-28
> **tommysmith2 said:**
> but what about the scripts you said before? it's automatically "take care" - it's mean auto add the gw for the second whichever the first left?

Yup, I can still do that. But in the same post and same line I also said that I need to see the "route -n" output for each possible case (which shouldn't be more than 3-4 tables) to make sure it can handle all the possibilities. :)

There are people with much more complex setups and they can handle these situations quite easily. So either this should have been an automatic process or there must be some configuration stuff to handle this in a better way.

I just don't know those "better ways", so willing to do that via script, which is crude, but will get the job done.

---

### Post by tommysmith2 on 2013-10-28
Yah, I also said that just have 2 case happen:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

If I restart, so nothing change, but If I shutdown server and turn it on so the NIC reach gw will change such as in below :

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

Maybe in the future will more complex, but now it just...simple like that :D

---

### Post by varunendra on 2013-10-28
These are definitely the outputs from when both the interfaces are up and internet works. I need to see the 'problem cases', to determine what all may go wrong when you disable one of them.

I can guess the situations, but 1) I want to confirm, and 2) Don't want to spend time on unnecessary assumptions.

---

### Post by tommysmith2 on 2013-10-28
Oh, sorry, maybe I'm not sure I understand clearly the problem case, If it's like I guess, so this is the simulator of case when I'm down the NICs:

**1/ Down the eth0 reach gateway:**

```

root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@vpn:~# ifdown eth0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/08:00:27:e5:97:24
Sending on   LPF/eth0/08:00:27:e5:97:24
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.10.1 port 67 (xid=0x13b0a176)
root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@vpn:~# ping google.com
ping: unknown host google.com

```


**2/ Down the eth1 don't reach gateway:**

```

root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@vpn:~# ifdown eth1
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/08:00:27:d1:52:6a
Sending on   LPF/eth1/08:00:27:d1:52:6a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.10.1 port 67 (xid=0x7a991c93)

root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
root@vpn:~# ping google.com
PING google.com (113.171.253.251) 56(84) bytes of data.
64 bytes from localhost (113.171.253.251): icmp_seq=2 ttl=57 time=127 ms
^X64 bytes from localhost (113.171.253.251): icmp_seq=4 ttl=57 time=165 ms

```

Sr, If I misunderstand something :)

---

### Post by varunendra on 2013-10-28
No it's okay.

From the above examples, the first one is when _Internet stops working_ (after disabling eth0), thus it is a problem case.

In the second one, internet keeps working, so _not a problem case_.

You also said that *sometimes*, internet stops working even when eth1 is disabled. I assume the routing table in that (problem) case would be same as the first one (after disabling eth1), only eth0 and eth1 are mutually replaced.

In my test VM here (using Network Manager), the first one looks exactly the same as yours after disabling eth0 (only one line remains with no gateway). But within 2-4 seconds, a new line containing the gateway is generated automatically (probably Network Manager does it, since I've saved the gateway for both interfaces).

So, can you test the same thing and confirm if it gets auto generated or not if you wait a few seconds?

Also, in post #13, you mentioned -
>  route add default gw 10.0.0.1 eth0[1] - and I check both NIC reached gw, but after that I can't ping, maybe it's make something conflict !!!
I need to see the 'conflict' or whatever it is. Just show me the routing table (output of route -n) before and after you do above.

---

### Post by tommysmith2 on 2013-10-29
Yah, I had waiting long time after down an NICs but it's not auto reach the gw for the second NIC. Oh, maybe Virtualbox act different with VM and even it's also different in the real world @@

This is the result before and after I add the gw manual for the NIC don't reach the gw, it's make the internet corrupted. 

```

root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@vpn:~# ping google.com
PING google.com (113.171.253.244) 56(84) bytes of data.
64 bytes from localhost (113.171.253.244): icmp_seq=1 ttl=59 time=227 ms
^Z
[2]+  Stopped                 ping google.com

root@vpn:~# route add default gw 192.168.10.1 eth1

root@vpn:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@vpn:~# ping google.com
ping: unknown host google.com

```

---

### Post by varunendra on 2013-10-30
Okay, let's consider your post #19 again.

In the first case, when eth0 is disabled, there remains only one route. What we need to do in that case is to add the default route again.
This can be automatically done by the script I am posting below.

But what if you (or the script) add the gateway to eth1, and then eth0 is brought up again?? Check the routing table again and see the sequence of the routes. In an ideal situation -
[list]
[*]There should be only one line with the gateway defined
[*]The first route (ideally 2nd line) to the network or the gateway should be using the SAME interface as the default (gateway) route at the top.
[/list]

The rest of the routes will be fine, whatever their sequence is. If the above condition is not met, THERE WILL BE PROBLEM when eth0 is brought up again (or eth1 if that was the default interface during startup).

Copy-paste the following code in a text file, and save it into your Home as "autoroute.sh" -
```
#!/bin/bash

# Script to disable an interface and update the default route
# Usage : autoroute.sh [eth0|eth1] [down]

GATEWAY=$(route -n | awk 'NR==3 {print $2}')
IFACE_DEFAULT=$(route -n | awk 'NR==3 {print $8}')

if [ "$1" = "$IFACE_DEFAULT" ]; then
	if [ "$2" = "down" ]; then
		sudo ifdown "$1"
		sleep 2
		sudo route add default gw $GATEWAY
	fi
fi
```

After saving it, make it executable -
```
chmod +x autoroute.sh
```

This is how you have to use it -

* To disable eth0 -
```
./autoroute.sh eth0 down
```

* To disable eth1 -
```
./autoroute.sh eth1 down
```

* To enable them again, use the normal ifup command.

What it does is -
It records the default interface and gateway before doing anything.
It checks if the interface (eth0 or eth1) you are going to disable (down) is the default interface (the one used for gateway).
If yes, it disables it > waits for 2 seconds > adds the gateway again to the leftover interface.

What it can't handle is if enabling the interface again also brings up the gateway route originally associated with it, and it becomes a problem. I don't know if it will happen.

Test it and see if it does. Report back with the problematic routing table (multiple ones if there are more than one problematic tables) and we can modify the script to address the problem.

---

### Post by tommysmith2 on 2013-11-02
Thanks your script and so sorry, two days ago, I'm quite so busy that can't testing the scripts. Uhm, now I tested it but it have error that show below:

```

root@ubuntu:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

root@ubuntu:~# nano autoroute.sh
root@ubuntu:~# chmod +x autoroute.sh
root@ubuntu:~# ./autoroute.sh eth0 down
**-bash: ./autoroute.sh: \bin\bash: bad interpreter: No such file or directory**

root@ubuntu:~# ls
autoroute.sh

```

If the command "./autoroute.sh eth0 down" working, so the eth0 will down and 2 seconds later the script will auto add gw default for leftover NIC (eth1) right ? But what about the autoroute.sh eth1 down ?

---

### Post by varunendra on 2013-11-02
> **tommysmith2 said:**
> ```
**-bash: ./autoroute.sh: [COLOR="#FF0000"]\[/COLOR]bin[COLOR="#FF0000"]\[/COLOR]bash: bad interpreter: No such file or directory**
```
Sorry, messed up the slashes. Please correct them, they are forward slashes, not backslash.

> If the command "./autoroute.sh eth0 down" working, so the eth0 will down and 2 seconds later the script will auto add gw default for leftover NIC (eth1) right ? But what about the autoroute.sh eth1 down ?
Will work the same way IF eth1 is used for DEFAULT route (mutually replace eth0 and eth1 in your above routing table, and you'll get the scenario).

If you use it in the scenario exactly same as above, it will do nothing, because there is nothing in that case that needs to be done by a script. It would be easier to just use the simple "sudo ifdown eth1" command.

But if you need the script to handle both situations, just add an "else" part to cover that. So it will become like this -
```
#!/bin/bash

# Script to disable an interface and update the default route
# Usage : autoroute.sh [eth0|eth1] [down]

GATEWAY=$(route -n | awk 'NR==3 {print $2}')
IFACE_DEFAULT=$(route -n | awk 'NR==3 {print $8}')

if [ "$1" = "$IFACE_DEFAULT" ]; then
	if [ "$2" = "down" ]; then
		sudo ifdown "$1"
		sleep 2
		sudo route add default gw $GATEWAY
	[B]else
		sudo ifdown "$1"[/B]
	fi
fi
```

Now you don't have to check which one is default interface, the script will take care of it. If the one you are disabling is the default one, the IF part will work and gateway will be added 2 sec. later. If it is the non-default one, the simple "ifdown" will be performed with no additional steps.

---

### Post by tommysmith2 on 2013-11-05
Thanks, it's working, if I'm using "./autoroute.sh eth0 down" so the eth1 will auto reach the gw :)

However, I wonder that why it's not working when I'm using "ifdown eth0" ? Moreover, do you think in the real world, when we don't use the command line to down NICs but the NICs or Cable broken and losing the connection, so the script will auto work ?

---

### Post by varunendra on 2013-11-05
> **tommysmith2 said:**
> However, I wonder that why it's not working when I'm using "ifdown eth0" ?
I would expect it to work automatically. But as I have almost no experience with Linux server setups, I can't explain what may be wrong with the default setup, or if it is indeed the default behaviour in server setups.

> Moreover, do you think in the real world, when we don't use the command line to down NICs but the NICs or Cable broken and losing the connection, so the script will auto work ?
Scripts located in **/etc/network/ifup.d** and **/etc/network/ifdown.d** directories are supposed to execute automatically as soon as an ifup/down event occurs. I didn't mention it because I never tried it before, and I currently am a bit short of time to do experiments.

You may try a few variations of the script, and putting it in those directories yourself if you understand its basics. The script in its current form won't work because it needs two arguments (interface, and "down") to be supplied by the user. It should be self contained (needing no input from user) to work automatically.

Take a look at the existing scripts in those directories and you may get an idea of how to proceed.

Also take a look at this post, which mentions a similar alternative : [http://ubuntuforums.org/showthread.php?t=2102559&p=12452203#post12452203](http://ubuntuforums.org/showthread.php?t=2102559&p=12452203#post12452203)

The poster of the above post, Cheesehead, seems to have good experience with server setups and such automation scripts. He may be much better help for your queries about why it isn't happening automatically and how to automate it.

---

### Post by tommysmith2 on 2013-11-05
I'll try to testing it in the real world when I have change :D Anyway, thanks for your help so much, and actually I'm not new here, but my old nick tommysmith had gone from forum hacked, and I always like this forum cuz have many guys so enthusiasm like you, it' make me love open source with the spirit for learning and sharing :)

---

### Post by varunendra on 2013-11-06
> **tommysmith2 said:**
> I'll try to testing it in the real world when I have change :D Anyway, thanks for your help so much, and actually I'm not new here, but my old nick tommysmith had gone from forum hacked, and I always like this forum cuz have many guys so enthusiasm like you, it' make me love open source with the spirit for learning and sharing :)

It's a pleasure to be able to help with something. :)

If you think the original problem is solved, please mark the thread as such, using the "**Thread Tools**" link above the top post. It is itself a way of helping others by indicating that the thread contains a possible solution to the topic. :)

---

