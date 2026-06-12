---
title: "Internet connection disappeared..."
date: 2005-10-03
forum: Networking &amp; Wireless
---

### Post by Yorak on 2005-10-03
Just installed Ubuntu today. I set up a partition so I could dual boot with WinXP. After installation everything was working fine. Internet included. Then I shut down and went into WinXP to do something, shut down, went back to Ubuntu and I no longer had a connection. I'm at college, just connecting with ethernet that goes to a router. I just don't understand how it worked then but not after the second time I loaded it up. Any help would be greatly appreciated.

~ Yorak

---

### Post by cwaldbieser on 2005-10-03
[QUOTE=Yorak]Just installed Ubuntu today. I set up a partition so I could dual boot with WinXP. After installation everything was working fine. Internet included. Then I shut down and went into WinXP to do something, shut down, went back to Ubuntu and I no longer had a connection. I'm at college, just connecting with ethernet that goes to a router. I just don't understand how it worked then but not after the second time I loaded it up. Any help would be greatly appreciated.
~ Yorak[/QUOTE]
Try opening the terminal and typing
```

$ sudo dhclient

```
Does that connect you to the network again?

---

### Post by Yorak on 2005-10-03
Nope, all it says is a bunch of "Permission denied" and "Network is down". :???:

---

### Post by Yorak on 2005-10-03
Any ideas? A connection is sorta essential, ya know?

---

### Post by cwaldbieser on 2005-10-03
[QUOTE=Yorak]Any ideas? A connection is sorta essential, ya know?[/QUOTE]
Well, you could try to set up a static route.  Most routers use DHCP, though, so I'm surprised that dhclient didn't work.  Can you capture the errors and post them here?

In the meantime, since you have a dual boot, in the Windows console (cmd.exe), post the output of:
```

C:\>ipconfig
C:\>route print

```
That should give us the settings we need to get you running.

---

### Post by Mustard on 2005-10-03
I have an unconventional suggestion. :)

You could try shutting down, disconnecting the computer from the power, say by taking your power cord out of the back.  Leave for a minute, then come back and try Ubuntu again.  I've experienced something like this with a totally different type of hardware on dual boot machine, which inexplicably used to steal my usb ports from linux.

---

### Post by Yorak on 2005-10-04
Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : pct.edu
        IP Address. . . . . . . . . . . . : 10.100.27.14
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.100.27.1

C:\Documents and Settings\Yorak>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 50 56 c0 00 08 ...... VMware Virtual Ethernet Adapter for VMnet8
0x3 ...00 50 56 c0 00 01 ...... VMware Virtual Ethernet Adapter for VMnet1
0x4 ...00 12 3f d8 f6 9e ...... Broadcom 440x 10/100 Integrated Controller - P
ket Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      10.100.27.1    10.100.27.14       20
      10.100.27.0    255.255.255.0     10.100.27.14    10.100.27.14       20
     10.100.27.14  255.255.255.255        127.0.0.1       127.0.0.1       20
   10.255.255.255  255.255.255.255     10.100.27.14    10.100.27.14       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
     192.168.79.0    255.255.255.0     192.168.79.1    192.168.79.1       20
     192.168.79.1  255.255.255.255        127.0.0.1       127.0.0.1       20
   192.168.79.255  255.255.255.255     192.168.79.1    192.168.79.1       20
    192.168.254.0    255.255.255.0    192.168.254.1   192.168.254.1       20
    192.168.254.1  255.255.255.255        127.0.0.1       127.0.0.1       20
  192.168.254.255  255.255.255.255    192.168.254.1   192.168.254.1       20
        224.0.0.0        240.0.0.0     10.100.27.14    10.100.27.14       20
        224.0.0.0        240.0.0.0     192.168.79.1    192.168.79.1       20
        224.0.0.0        240.0.0.0    192.168.254.1   192.168.254.1       20
  255.255.255.255  255.255.255.255     10.100.27.14    10.100.27.14       1
  255.255.255.255  255.255.255.255     192.168.79.1    192.168.79.1       1
  255.255.255.255  255.255.255.255    192.168.254.1   192.168.254.1       1
Default Gateway:       10.100.27.1
===========================================================================
Persistent Routes:
  None

---

### Post by Yorak on 2005-10-04
On another note I copied the errors onto a thumb drive but when I went to Windows the file on the drive was gone. Oh well, I have class now but will try back in 2 hours. Thanks for all the help though guys, I know you're trying your best. I've always been satisfied with Ubuntu forums. ;)

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=Yorak]On another note I copied the errors onto a thumb drive but when I went to Windows the file on the drive was gone. Oh well, I have class now but will try back in 2 hours. Thanks for all the help though guys, I know you're trying your best. I've always been satisfied with Ubuntu forums. ;)[/QUOTE]
The only thing I can think of is that you didn't unmount the drive before you unplugged it.  I've had that happen to me where data was not save because it is being buffered until you tell the drive you are going to unmount.

As far as your network problem, the following should set up a static IP and route for you:
```

$ sudo ifconfig eth0 10.100.27.14
$ sudo route add -net 10.100.27.0 netmask 255.255.255.0 dev eth0
$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.100.27.1

```
The first command brings up you NIC identified as eth0 with the IP address 10.100.27.14.
The second command adds an entry to the routing table that says, if the packet is destined for the 10.100.27/24 network, send it to my local NIC.
The last command adds an entry to your routing table that says, if the packet is destined for anywhere else, send it to my router at 10.100.27.1.

That's a temporary solution, but hopefully it makes it more convenient for you to be on the forums and Ubuntu at the same time.

If something doesn't work, note the error.  The commands "ifconfig" and "route" by themselves should show you what the current state of your NIC and the routing table look like.

---

### Post by Yorak on 2005-10-04
Didn't work, I got this:

yorak@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D8:F6:9E
          inet addr:10.100.27.0  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed8:f69e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:85919 (83.9 KiB)  TX bytes:7948 (7.7 KiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:183560 (179.2 KiB)  TX bytes:183560 (179.2 KiB)

yorak@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7191
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:12:f0:93:8e:18
Sending on   LPF/eth1/00:12:f0:93:8e:18
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:12:3f:d8:f6:9e
Sending on   LPF/eth0/00:12:3f:d8:f6:9e
Sending on   Socket/fallback
receive_packet failed on sit0: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPACK from 10.100.27.3
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
/etc/dhcp3/dhclient-script: line 33: /etc/resolv.conf.dhclient-new: Permission denied
/etc/dhcp3/dhclient-script: line 41: /etc/resolv.conf.dhclient-new: Permission denied
/etc/dhcp3/dhclient-script: line 41: /etc/resolv.conf.dhclient-new: Permission denied
chown: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
chmod: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
mv: cannot stat `/etc/resolv.conf.dhclient-new': No such file or directory
bound to 10.100.27.14 -- renewal in 4503981 seconds.
yorak@ubuntu:~$

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=Yorak]Didn't work, I got this:
yorak@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D8:F6:9E
inet addr:10.100.27.0  Bcast:10.255.255.255  Mask:255.255.255.0
inet6 addr: fe80::212:3fff:fed8:f69e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:968 errors:0 dropped:0 overruns:0 frame:0
TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:85919 (83.9 KiB)  TX bytes:7948 (7.7 KiB)
Interrupt:18
lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:2077 errors:0 dropped:0 overruns:0 frame:0
TX packets:2077 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:183560 (179.2 KiB)  TX bytes:183560 (179.2 KiB)
yorak@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7191
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
sit0: unknown hardware address type 776
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:12:f0:93:8e:18
Sending on   LPF/eth1/00:12:f0:93:8e:18
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:12:3f:d8:f6:9e
Sending on   LPF/eth0/00:12:3f:d8:f6:9e
Sending on   Socket/fallback
receive_packet failed on sit0: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPACK from 10.100.27.3
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
/etc/dhcp3/dhclient-script: line 33: /etc/resolv.conf.dhclient-new: Permission denied
/etc/dhcp3/dhclient-script: line 41: /etc/resolv.conf.dhclient-new: Permission denied
/etc/dhcp3/dhclient-script: line 41: /etc/resolv.conf.dhclient-new: Permission denied
chown: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
chmod: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
mv: cannot stat `/etc/resolv.conf.dhclient-new': No such file or directory
bound to 10.100.27.14 -- renewal in 4503981 seconds.
yorak@ubuntu:~$[/QUOTE]
If you look at your output from "ifconfig", the part that says
```
inet addr:10.100.27.0
```
is showing that your NIC has been given address 10.100.27.0.  This is actually pretty strange, because the for most home networks the xxx.xxx.xxx.0 and xxx.xxx.xxx.255 addresses are reserved.

Your dhclient output is also a little wacky.  It looks like it has trouble creating or moving some file, but ultimately reports that it bound your NIC to address 10.100.27.14.  I take it that at that point another "ifconfig" confirms your NIC does not have that address.

Try posting the contents of your /etc/dhcp3/dhclient.conf config file.  Maybe there is something messed up in there.

You could also try explicitly identifying the interface you want to dynamically assign:
```

$ sudo ifdown eth0
$ sudo dhclient eth0

```

---

### Post by Yorak on 2005-10-06
Fixed it by fresh install, will make a new thread about my new problem, although it is much less important and I can live without. Thanks for all of your help.

---

### Post by aseitz on 2006-07-07
I too am getting the same problem, I attached to edgy and boom no more networking.

It seems dhclent is busted, I have the same exact errors as the OP.

I am running: Internet Consortium DCHP Client V3.0.4
I have tried:
- ifconfig eth0 down
- ifconfig eth0 up

And it gives me 
- SIOCSIFADDR: Permission denied
- SIOCSIFFLAGS: Permission denied
- SIOCSIFFLAGS: Permission denied

Did this package get updated recently or something? If so, can I downgrade it? And FYI, I am posting this on my seperate windows box, so I can not copy and paste error messages from linux. I would retype the entire screen, if it was required (I'm just hoping it's not necessary).

---

### Post by Hakunushi on 2006-11-30
okay im a linux user for 2 years now... i was always a slackware user... but since ubuntu dapper im a apt-get fan :mrgreen:

i work with computers on a company´s IT area and since i know linux i use it on the servers... using squid... samba... ldap and all that server stuff

among all these server stuff lies my webserver wich contains the site of the company i work for, and in chage of that and take the responsibilities for that XD

Happens that i´ve upgraded my dapper to edgyand soon my network stopped... okay since the company connection lies on a router all i had to do was to veryfy my lan configuration... but wenever i try to change it, it says "/etc/resolv.conf : permission denied" so i typed sudo nano /etc/resolv.conf, permission denied....sudo chmod 777 resolv.conf, permission denied.... sudo chmod +x... -x ... chown crap... what the reck... i´ve abilited root and tehn used su command... #chmod, nothing, chown, nothing, rm denied...
WTF?

then i used ls command, and noticed that among all blue, green and white file names resolv was in red... i dont know what that means... all i know is that i couldnt even delet it with supreme root user, couldnt even see its contents... im lucky that i had a g4u clone of my dapper server and in 30 mins i put my server online again... but i lost that precious time... and so my company... maybe some money too.... maybe edgy is unreliable... coz now here in the internet i see some ppl had the same problem... edgy is unsafe and buged maybe???

but i cant believe that edgy is buged... maybe i did something wrong... i dont even know what the red color means for ubuntu... i want to use edgy but first i gota know what happened ... and ifits a bug... 

thanks since now ^^

---

### Post by dmackenzie on 2008-06-06
I had the same problem. I reverted back to the old dhcp deb packages by installing them from the CD.

i.e.

cd /media/cdrom0/pool/main/d/dhcp3
dpkg -i *.deb

Hope this helps. Now to get my nvidia drivers working again :-)

---

### Post by dmackenzie on 2008-06-06
When I say, "the old dhcp deb packages" I mean the ones from the Ubuntu 7.10 CD.

---

### Post by Sylar_7 on 2008-06-06
try this:
in the BIOS setup, enable "Onboard Lan Boot ROM"

i was having that problem and it fixed mine

---

### Post by oscarjd74 on 2008-06-20
This seems like a similar problem that I had. I got the same permission denied messages. I've posted a solution that worked for me in this thread:
[http://ubuntuforums.org/showthread.php?t=543685](http://ubuntuforums.org/showthread.php?t=543685)

I'm guessing that dmackenzie's solution worked not because he reverted to an older version but because some permissions are reset when the package (old or new) is (re)installed.

Cheers,
Oscar

---

