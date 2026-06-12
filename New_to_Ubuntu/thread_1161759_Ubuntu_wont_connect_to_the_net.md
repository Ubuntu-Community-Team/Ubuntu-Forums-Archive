---
title: "Ubuntu wont connect to the net"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by pmasters123 on 2009-05-17
Hi All,

I have downloaded ubuntu 9.04 and tried it runnung off the cd so i dont have to install it, but it wont connect to the internet i have tried many of the ideas on the net but to no avail, i am no computer wiz so any info will need to be simple please. if anyone can help me that would be great i really dont want to go back to windows xp.

i am on pipex with a usb modem it all connects fine in windows 

thanks Paul

---

### Post by diablo75 on 2009-05-17
> **pmasters123 said:**
> Hi All,
i am on pipex with a usb modem it all connects fine in windows 

thanks Paul

I'm not familiar with Pipex, but the modem itself should also support an Ethernet connection.  Check to see if there is an Ethernet port available and use an Ethernet cable instead of a USB to attach your computer to it.  If you don't have a cable, you should be able to pick one up from Wal-mart for about ten dollars.

That's what I would do, anyway...

---

### Post by lkraemer on 2009-05-17
If you have a Wired LAN connection, use Synaptic to install Gnome-PPP,
and configure it.  It may take a bit of trial and error, to get your
configuration correct, but it should work.

Another method would be to try wvdial and see if it will connect.

If you want to try wvdial first, there are some good guides posted
on the forum.  This should get you going.  Once wvdial works
Gnome-PPP will be easy.


See:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Post #4

I assume pipex is your Dialup ISP.

lkraemer

---

### Post by Bölvaður on 2009-05-17
> **lkraemer said:**
> If you have a Wired LAN connection, use Synaptic to install Gnome-PPP,
and configure it.  It may take a bit of trial and error, to get your
configuration correct, but it should work.

Another method would be to try wvdial and see if it will connect.

If you want to try wvdial first, there are some good guides posted
on the forum.  This should get you going.  Once wvdial works
Gnome-PPP will be easy.


See:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Post #4

I assume pipex is your Dialup ISP.

lkraemer


That looks like an annoying thing to do every time you turn on the computer as it doesnt save any data on the live cd.

---

### Post by Knowle on 2009-05-17
Hey pmasters,

I'm definitly no expert as I just installed and starting using Ubuntu myself this morning but I had the same trouble using the LiveCD. I was however able to ping out from terminal so you might want to check that and see it if works. Just another way to check that you have connectivity even if you can't pull a webpage. You can also do as I did and try out Wubi, it will install Ubuntu for you(dual boot were you can either boot into Ubuntu/WinXP or what have you) and easily uninstall it through Add and Remove programs if it still doesn't work.

Applications > Accessories > Terminal, type "ping google.com" without quotes and press enter. You can let it fill 4-5 lines then hit Ctrl+C that will stop it. Should give you something like this:
```
knowle@ubuntu:~$ ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=43 time=36.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=43 time=35.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=6 ttl=43 time=34.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=10 ttl=43 time=35.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=11 ttl=43 time=34.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=15 ttl=43 time=35.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=16 ttl=43 time=36.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=20 ttl=43 time=34.7 ms
^C
--- google.com ping statistics ---
20 packets transmitted, 8 received, 60% packet loss, time 19081ms
rtt min/avg/max/mdev = 34.499/35.407/36.456/0.753 ms
knowle@ubuntu:~$ 
```

---

### Post by mapes12 on 2009-05-17
Hi Paul

Are you trying to connect using a dialup modem or do you have Broadband? USB modems can be tricky sometimes. If you have a Broadband router then try connecting using an ethernet cable as previously advised.

Post the output to ```
ifconfig
```

---

