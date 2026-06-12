---
title: "Networking problems in Linux"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by larainzlo07 on 2008-09-09
I am running a dual boot machine with windows and linux. If I boot up into windows I get internet access just fine but in linux I get nothing. In the past it was working but ever since yesterday it has stopped. I tried reinstalling to see if that would help but nothing.

When I type in ifconfig it shows eth0. Any ideas as to what might be causing this?

---

### Post by Legend28469 on 2008-09-09
I've had that problem too, here what you do if your running on a lan maybe wireless too,

as far as i know my computer doesn't automatically hook me up to the internet on ubuntu, only windows

Goto SYSTEM > ADMINISTRATION > NETWORK
and unlock it by clicking the unlock button
and typing in your password...

then choose wired connection

make sure properties are set to "Enable Roaming Mode"

Then you can close those windows...

next

right click in the upper right corner on the 2 computers make sure "Enable Networking" is checked

then you left click it.. and select Wired Network

and after a few seconds.... Boom :popcorn:

---

### Post by larainzlo07 on 2008-09-09
K I will try that to see if that works. Hopefully it does because this is annoying. I don't understand why it worked in the past and now it doesnt.

---

### Post by larainzlo07 on 2008-09-09
No that didn't work. I tried using my other ethernet port on my computer to see if that one worked and it didnt. I tried using a different cable and that didnt work.

---

### Post by Legend28469 on 2008-09-09
Hmm... sorry.. .i thought that would work

---

### Post by larainzlo07 on 2008-09-09
Has anyone else had this problem?

---

### Post by Iowan on 2008-09-09
I haven't had the problem... 
yet,but...
post results of **ifconfig** and contents of **/etc/network/interfaces**.

BTW, if you hack a cracker, that probably makes you covered in crumbs.

---

### Post by Legend28469 on 2008-09-09
> **Iowan said:**
> 
BTW, if you hack a cracker, that probably makes you covered in crumbs.

Exactly... :lolflag:

---

### Post by larainzlo07 on 2008-09-09
OK i will get that ASAP

---

### Post by larainzlo07 on 2008-09-09
Here is the ifconfig info:

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:29:d7:13  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe29:d713/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:650 (650.0 B)  TX bytes:5568 (5.4 KB)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94700 (92.4 KB)  TX bytes:94700 (92.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0d:fa:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-0D-FA-74-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Here is the etc/network/interfaces info: 

auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0

auto eth1

---

### Post by Iowan on 2008-09-09
OK, I'm confused... Why does **ifconfig** show eth0 with address 192.168.1.3, and **/etc/network/interfaces** shows eth1 with that address?
Try  editing **/etc/network/interfaces**  (I like **sudo nano** - you might prefer **gksudo gedit**) Change eth1 to eth0 (both in the **iface** line and the **auto** line), save file, and restart networking with **/etc/init.d/networking restart**.

---

### Post by larainzlo07 on 2008-09-09
Tried that and still nothing

---

### Post by hawksbill on 2008-09-09
Are you trying to connect through your wireless network or your lan? You stated that everything was fine yesterday but not working today. Does that mean your windows station isn't connecting either? If this is the case did you reboot the modem and router? I know it may seem like overkill but I always like to start with the simplest things first then work my way up.

---

### Post by larainzlo07 on 2008-09-09
No in windows I can connect to the internet just fine. I have tried restarting the router and reconfiguring it but all of the settings that I had in my router before didn't cause problems because the internet in linux worked with it configured that way.

---

### Post by cariboo on 2008-09-09
Get rid of this:

```
iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0

auto eth1 

```

In /etc/network/interfaces and change it to:

```
auto eth0
iface eth0 inet dhcp
```

then restart networking in a terminal type:

```
sudo /etc/init.d/networking restart
```

Your network should work the way it did before it stopped

Jim

---

### Post by larainzlo07 on 2008-09-09
This is what my /etc/network/interfaces file looks like now.

```
auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Restarted the service and nothing.

---

### Post by larainzlo07 on 2008-09-10
This still isnt working for me. Can anyone help?

---

