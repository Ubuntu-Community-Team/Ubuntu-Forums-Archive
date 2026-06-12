---
title: "Networking 4 Noob"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by theRevMom on 2006-12-22
I'm a Linux Newbie Convert after 15+ years doing Windues.  I have a handle on Win Networks, cmd boxes, and even some troubleshooting, but I'm in the dark with Ubuntu.  Be gentle with me... I'm really green.

Here's my situation.  I have two Ubuntu boxes, two WinXP Pro boxes, and three wireless laptops (two Ubuntu, one Win2K).  All access the internet through a Linksys BEFW1154.  The Win boxes & Laptop can see one another, can share the printer from WinXP1.  

Here's what I need:  The Ubuntu machines to access the printer connected to WinXP1.  

My Fedora loving brother told me to get Samba.  I found how to install it through Applications/Add/Remove.  But, I can't figure out how to run it... heck... access it even.

I can ping all the Win machines from the Ubuntu box.  But I can't SEE the network... it does not come up in the Network list.  ](*,) 

I know this is really basic, but please help me out!

---

### Post by dbbolton on 2006-12-22
did you see stormbringer's howto on samba ?

---

### Post by dbbolton on 2006-12-22
found it :)

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

---

### Post by theRevMom on 2006-12-22
Yes.  And that's how green I am.  I got lost with "Open a terminal"... how?:-?

---

### Post by stupidkid on 2006-12-22
Applications -> Accessories -> Terminal

---

### Post by theRevMom on 2006-12-22
Okay, I found the terminal.  
I went through the steps in HOW TO: set up Samba peer t...
I still can't see the printer from the Ubuntu boxes.  

I went to system -- Administration -- Printing and set up the printer's name and location.  I installed the driver.  I tried to print a test page.  No response by the printer.  

2 hours later addendum:  The Windows units can't see the samba share either.  And the Ubuntu machines can't see the Windows network.  So nothing prints from the Ubuntu machines.

I'm sorry to be so very stupid.  I'm trying!  ](*,)

---

### Post by koenn on 2006-12-23
The printer is connected to a winXP machine, right ?
The winXP1 is sharing the printer, right ?

If you have an ordinary, default ubuntu installation, there's no nedd to add samba because the ubuntu system is not going to share anything. It just needs to be able to access awindows share, and that is included in a default setup. 

What happens if you go to
System:Administration:Printing and click Add New Printer ?
What did you choose for 'Printer Type' ?  
What did you put in as printer name ?

---

### Post by theRevMom on 2006-12-23
What happens if you go to
System:Administration:Printing and click Add New Printer ?
What did you choose for 'Printer Type' ?
What did you put in as printer name ?


I added the printer.  I choose Network printer  I put in the name of the printer at WinXP1.  I told it to print a test page.  The Ubuntu box says it is printing.  Nothing happens with the printer.  The Ubuntu box eventually says the printer is paused.  I think it's not finding the printer.

But, I think it's not finding the network.  It can't see any of the computers in the workgroup.

Suggestions?   ](*,)

---

### Post by koenn on 2006-12-23
> I choose Network printer
the default there is CUPS, you did change it to Widows (SMB), right ?

>  I put in the name of the printer at WinXP1
yep, that's what you're supposed to do. You did write correct values for hostname and printername there, right ? did it ask for username and password of an account on the xp machine ?

what workgroup are the xp machines in ? 

open a file browser (Places:Computer), type Ctrl + L ; you should get an address bar. type in the address bar ```
smb://name_of_workgroup
```
or ```
smb://name_of_xp_machine
```
what happens ?

and just to make sure you have network:
open a terminal and run these commands.
```
ifconfig
```
```
ping 127.0.0.1
```
post the output

---

### Post by theRevMom on 2006-12-23
[QUOTE=koenn;1923537]the default there is CUPS, you did change it to Widows (SMB), right ?
Yes.  I chose Windows (SMB)


what workgroup are the xp machines in ? 

Hermes

open a file browser (Places:Computer), type Ctrl + L ; you should get an address bar. type in the address bar ```
smb://name_of_workgroup
```
or ```
smb://name_of_xp_machine
```
what happens ?

Cannot find XP Machine or Hermes (workgroup)

Output of config and ping:

dan@dan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:2B:39:44:05
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:30:BD:B4:47:83
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:feb4:4783/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1273833 (1.2 MiB)  TX bytes:186977 (182.5 KiB)
          Interrupt:217 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8099 (7.9 KiB)  TX bytes:8099 (7.9 KiB)

dan@dan-desktop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=11 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=12 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=13 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=14 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=15 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=16 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=17 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=18 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=19 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=20 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=21 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=22 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=23 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=24 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=25 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=26 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=27 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=28 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=29 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=30 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=31 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=32 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_seq=33 ttl=64 time=0.046 ms
64 bytes from 127.0.0.1: icmp_seq=34 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=35 ttl=64 time=0.047 ms

--- 127.0.0.1 ping statistics ---
35 packets transmitted, 35 received, 0% packet loss, time 34025ms
rtt min/avg/max/mdev = 0.038/0.045/0.053/0.009 ms

---

### Post by theRevMom on 2006-12-23
](*,) ](*,) ](*,) ](*,) 

I'm giving up until after the holidays.  I'm too overwhelmed with other stuff.  
I read through this forum: [http://www.ubuntuforums.org/showthread.php?t=32190&page=4&highlight=print+to+Windows+printer](http://www.ubuntuforums.org/showthread.php?t=32190&page=4&highlight=print+to+Windows+printer)

But nothing there helped either.  Like tseliot there, I too am running Norton SystemWorks and the XP firewall on the XP machine connected to the printer.  I can't work any longer with it or my family will disown me.  

Thanks for your input. I'll be back in a few days.

---

### Post by koenn on 2006-12-23
You seem to have 2 network cards - one of which is without IP address
> eth0 Link encap:Ethernet HWaddr 00:40:2B:39:44:05
UP BROADCAST MULTICAST MTU:1500 Metric:1

eth1 Link encap:Ethernet HWaddr 00:30:BD:B4:47:83
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:bdff:feb4:4783/64 Scope:Link

shouldn't matter much unless you've plugged in the network cable in the wrong NIC. thought I'd mention it just in case. 

```
I too am running Norton SystemWorks and the XP firewall on the XP machine connected to the printer.
```
Firewalls are meant to block connections coming from other computers and that may well include your ubuntu machine attemting to connect to your XP. Turn XP firewall off (and disable Norton), then try again, either via the "Add Printer" procedure and / or the smb statements.

If the Firewall / Security is the culprit, at least you know where to start to solve the problem.

---

