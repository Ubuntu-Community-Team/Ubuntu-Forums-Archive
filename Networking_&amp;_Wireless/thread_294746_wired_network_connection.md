---
title: "wired network connection"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by STREETURCHINE on 2006-11-07
hi i am trying to get my windows laptop to network with ubuntu 6.06 desktop 
i think i am part way there but i am now stuck so any help would be good.
i have included an output from "ifconfig -a"but being a noob i dont understand it. 

rex@Linux:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:E3:51:74
          inet addr:192.168.0.145  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fee3:5174/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18169676 (17.3 MiB)  TX bytes:3086351 (2.9 MiB)
          Interrupt:201 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:424 (424.0 b)  TX bytes:424 (424.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.110.1  Bcast:172.16.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.4.1  Bcast:172.16.4.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

rex@Linux:~$

i just dont seem to be able to get the computers to see each outher  ](*,)
 ps i am using a dlink DI 704up

---

### Post by kidders on 2006-11-07
Hi there,

So, both your PCs are connected to your router? Assuming your Ubuntu box is connected via eth0, how is your Windoze box connected, and what IP address does it get assigned?

If you can't at least ping one computer from the other, you may have a cabling problem, but there are a few other possibilities ... let us know!

---

### Post by STREETURCHINE on 2006-11-07
sorry im not sure how to get the info you want if you could help with the commands ,both windows and ubuntu (ubuntu is desktop) go through the router then through the skyedge modem.

---

### Post by kidders on 2006-11-07
Post the output of the following, as executed on your Windows box...

[LIST]
[*]ipconfig
[*]ping 192.168.0.145
[/LIST]

---

### Post by STREETURCHINE on 2006-11-07
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\rex>ipconfig

Windows IP Configuration


Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.161
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\rex>ping 192.168.0.145

Pinging 192.168.0.145 with 32 bytes of data:

Reply from 192.168.0.145: bytes=32 time<1ms TTL=64
Reply from 192.168.0.145: bytes=32 time<1ms TTL=64
Reply from 192.168.0.145: bytes=32 time<1ms TTL=64
Reply from 192.168.0.145: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.0.145:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Documents and Settings\rex>
this was done in windows through command promt

---

### Post by kidders on 2006-11-07
Hey again,

It looks as though your computers see each other just fine :-) What problems are you having, exactly? (I'm assuming, now that you have the Windoze box's IP, that you can ping it from the Ubuntu box too.)

---

### Post by STREETURCHINE on 2006-11-07
hi i am asuming the ip address of my ubuntu box is 192.168.0.161 so i typed into terminal (ping 192.168.0,161 )and it just kept pinging do i have to tell it how many time to ping ?it got to 107 so i stopped it.
 its just that i dont seem to be able to get to my shared files and i dont have write permission on the windows network on the ubuntu box.
   oops meant windoze box up there .
 
 it could be that i just dont know how to find them or i have not given them the same name,i just dont know

---

### Post by kidders on 2006-11-07
Yep... 192.168.0.161 is right, although since your internal addresses are probably DHCP-assigned, they might not be the same tomorrow!

So, it seems as though your only problem is with filesharing.

> i dont seem to be able to get to my shared files
I'm not sure about exactly what's happening there, but if you don't have write access to files on your Ubuntu box, you should first check whether you *should* have write access.

[LIST]
[*]The user you are connecting as (from Windows) needs write access to the files, as would a user you are mapping to, in the event you're connecting as a guest, or another "special" user. Doing something like **ls -l /path/to/wherever** will show you the current ownership/permissions for your share.
[*]Next, I would check the output of **mount**, to make sure the filesystem your share lives on is mounted in read/write mode.
[*]Finally, I would check my smb.conf, to make sure write access isn't being explicitly prevented, with **writable = no**, for instance.
[/LIST]

With any luck, one of these is your solution :-)

---

### Post by STREETURCHINE on 2006-11-07
I'm not sure about exactly what's happening there, but if you don't have write access to files on your Ubuntu box, you should first check whether you should have write access.

    * The user you are connecting as (from Windows) needs write access to the files, as would a user you are mapping to, in the event you're connecting as a guest, or another "special" user. Doing something like ls -l /path/to/wherever will show you the current ownership/permissions for your share.
    * Next, I would check the output of mount, to make sure the filesystem your share lives on is mounted in read/write mode.
    * Finally, I would check my smb.conf, to make sure write access isn't being explicitly prevented, with writable = no, for instance.


With any luck, one of these is your solution
Reply With Quote
 yes it may be but as i say i am a total noob and i have no idea how to do any of that,i am learning but being an old fart its not a quick process :-D  
 so if you could lead me through it it would be good .if not  thanks for your help at least i know they are seeing each outher\\:D/

---

### Post by kidders on 2006-11-07
Happy to help :-) PM me and I can walk you through it.

---

### Post by STREETURCHINE on 2006-11-09
well we have ubuntu sorted .i can see windows shares by typing in the ip address, but i still cant figure out how to get windows to see ubuntu.
it probably see's ubuntu i just dont know how to cnfig windows to find ubuntu  :-k

---

