---
title: "problems with network"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by theugleymonkey on 2008-04-26
ok here is the problem i am trying to get my unbuntu computer to my pc for internet through ethernet.  My pc computer is hooked up to a wireless network i cant run any cables to my router.  so i was wondering if i can hook up my ubuntu computer to my vista pc and get internet like that. i have been trying this for about a day and i still cant get it to work.  I remember that one time i was able to hook up my wifi laptop to a xbox360 for internet and it work. I have no clue if this is the same concept. please help.  thanks

---

### Post by superprash2003 on 2008-04-26
yea.. there is something called ICS(Internet Connection Sharing) in windows vista.. you need to enable that.. and your windows vista machine should have 2 LAN cards. [http://windowshelp.microsoft.com/Windows/en-US/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx](http://windowshelp.microsoft.com/Windows/en-US/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx)

---

### Post by wilsonmuse on 2008-04-26
To hookup two computers directly you will need a crossover cable, not a standard Ethernet cable. I'm not sure how to share internet in Vista though...

---

### Post by theugleymonkey on 2008-04-26
I enabled ics but it still dose not work

---

### Post by theugleymonkey on 2008-04-26
can anyone help

---

### Post by kgriff on 2008-04-27
Are you using the crossover cable that was mentioned?  You will have to either have a crossover cable or a network hub between the two computers in order for them to talk.

---

### Post by superprash2003 on 2008-04-27
first make sure that the vista and the ubuntu machine get an ip.. and let us know if they can ping each other

---

### Post by theugleymonkey on 2008-04-27
Im sorry im a noob at this. Ok i will pick up the crossover cable today at radioshack and how do i give ubuntu an ip or ware and wich ip do i give it.

---

### Post by superprash2003 on 2008-04-27
go to your windows vista pc and type ipconfig and post results here.. then go to the ubuntu terminal and type ifconfig and post results here.. then it is possible to find out what ip vista and ubuntu is getting

---

### Post by theugleymonkey on 2008-04-27
Ok i have the crossover cable now I did the ipconfig and ifconfig and i got 

this for vista

Windows IP Configuration


Ethernet adapter Local Area Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::e52e:44b4:9a90:3914%9
   IPv4 Address. . . . . . . . . . . : 192.168.1.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::9966:ae50:ec5d:b73e%8
   Autoconfiguration IPv4 Address. . : 169.254.183.62
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection 5:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::2ca4:8edf:e37e:4963%17
   IPv4 Address. . . . . . . . . . . : 192.168.85.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection 6:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::b5b0:ccf7:550c:93b4%19
   IPv4 Address. . . . . . . . . . . : 192.168.245.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Ethernet adapter Hamachi:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 5.205.63.94
   Subnet Mask . . . . . . . . . . . : 255.0.0.0
   Default Gateway . . . . . . . . . : 5.0.0.1

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 13:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 14:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 15:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2002:5cd:3f5e::5cd:3f5e
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301

Tunnel adapter Local Area Connection* 16:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :



An i got this for ubuntu

eth0    link encap:Ethernet HWaddr 00:0d:87:12:c3:17
        inet6 addr: fe80::20d:87ff:fe12:c317/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:4462 errors:0 dropped:0 overruns:0 frame:0
        TX packets:4 errors: dropped:0 overruns:0 Carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:312212 (304.8 kb)TX bytes:328 (320.0 B)
        Interrupt:16 Base adress:0xe800

lo      Link encap:local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128scope:Host
        Up LOOPBACK RUNNING MTU:16436 Metric:1 
        RX Packets:1388 errors:0 dropped:0 overruns:0 frame:0
        TX Packets:1388 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:72064 (20.3 KB)  TX bytes:72064 (70.3 KB)

---

### Post by theugleymonkey on 2008-04-27
so can anyone help

---

### Post by superprash2003 on 2008-04-27
from your windows vist ipconfig it doesnt look like you have ICS enabled. usually if you have ICS enabled one of those adapters would get an ip address 192.168.0.1 .. which doesnt seem to occur...

---

### Post by theugleymonkey on 2008-04-28
ok well i just ran it again today enabled everything and that ip that you said still didnt show.

---

### Post by theugleymonkey on 2008-04-29
any one

---

### Post by jerome1232 on 2008-04-29
[http://www.annoyances.org/exec/show/ics_xp]("http://www.annoyances.org/exec/show/ics_xp") does this help? first result I got from google, you might want to research ICS as much as you can, this is really a Windows question. All I know (think) is ICS turns the windows computer into a router (am I correct on this?), which can present problems 'cuz your going to have 2 routers on the same network, which takes some special setup steps which I haven't personally messed with so I don't know what you need to do to get that working.

sorry that was xp I think  you mentioned you are using Vista...
[http://windowshelp.microsoft.com/Windows/en-US/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx]("http://windowshelp.microsoft.com/Windows/en-US/help/bfd3bd31-82f0-4b9c-9cde-fb92bc2b14771033.mspx")

---

