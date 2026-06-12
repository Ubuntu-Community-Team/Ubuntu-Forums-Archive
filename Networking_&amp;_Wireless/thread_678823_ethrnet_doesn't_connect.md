---
title: "ethrnet doesn't connect"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by pfabrikant on 2008-01-26
hey guys,
i updated to xubuntu 7.10  a week ago, and then i suddenley  lost my  connection to the internet. I am connected through wires to the ethernet connection  (using a  thompson router), and everything worked fine until i updated. then i started getting "server not found" notices in the firefox browser. my rooomate's  internet connection works as usual (she has windows), which means the router works fine ( no ?).  I tried to go through the 'networking connection' options but i really don't understand much.  It looks like nothing changed from before the upgrade. 
i looked through the "how to's" and through the troubleshooting guides but there seems to be nothing there about a wired ethernet connection problem...  
any help would be great
thanks a lot !

---

### Post by Anvilfolk on 2008-01-26
Hi :)

Do you know your ethernet card's interface? It might be something along the lines off eth0 or eth1. If you don't know, you can see the ones you have through the network manager or by having a look at /etc/network/interfaces, which I suggest you post here.

In any case, try doing
```
sudo ifup <ethernet_interface>
```

if it says the interface is already up, run the same command, but with "ifdown" instead of ifup. If it's a normal wired connection, it should get you a new IP... otherwise, I dunno. Try checking your cable, maybe?

Good luck.

---

### Post by Iowan on 2008-01-26
**ifconfig** is another terminal command that will give information about your connections.

---

### Post by pfabrikant on 2008-01-26
the ethernet interface is eth0. i tried the ' ifup'  command and it did claim that the interface is configuered. then i tried the ifdown command and this is what i've got:

> pfabrikant@ubuntu:~$ sudo ifup eth0
[sudo] password for pfabrikant:
ifup: interface eth0 already configured
pfabrikant@ubuntu:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0a:e4:35:36:75
Sending on   LPF/eth0/00:0a:e4:35:36:75
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

 
anyone has a clue to what it means ???
sorry, i am a complete newbie...
thanks again

---

### Post by pfabrikant on 2008-01-26
i tried the ifconfig, and here is the outcome:

> pfabrikant@ubuntu:~$ sudo ifconfig eth0
[sudo] password for pfabrikant:
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:35:36:75  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:309705 (302.4 KB)  TX bytes:1152 (1.1 KB)

what does it mean ? where might be the problem ?

---

### Post by schiznik on 2008-01-26
you need to run "sudo ifup eth0" again. 

ifup and ifdown start and stop your network interface respectively - you've stopped it, now it needs starting again. 

post the output of ifup if you still have problems

---

### Post by pfabrikant on 2008-01-26
ok, 
i typed 'sudo ifup eth0' again, and this is what i've got:
> pfabrikant@ubuntu:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:0a:e4:35:36:75
Sending on   LPF/eth0/00:0a:e4:35:36:75
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted



???

---

### Post by Anvilfolk on 2008-01-26
Well, those are pretty weird problems. My guess is that there's something wrong with your drivers. Those errors aren't standard ones, like being unable to connect. They seem problems with Ubuntu communicating with your network card.

Speaking of which, what's your network card?

Run ```
lspci | grep -i eth
```, which should get you a line about your ethernet card. From that, maybe we can figure out what drivers you need and are using.

---

### Post by pfabrikant on 2008-01-26
thanks for helping !
the grep command didn't work (there was just a blank line beneath the command)
the lspci gave:
[QUOTE][pfabrikant@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

/QUOTE]

why did xubuntu stopped communicating with my network card just because of an update ?
 thanks again

---

### Post by darkworld on 2008-01-26
Hey guys, just as an add on to this thread.

 I just built a new pc and it had integrated ethernet, nivivida graphics etc and I included a wifi card. My old pc ran feisty off of broad band Ethernet via cable modem.

I was fortunate that I managed to jump on somebody else'sMCP51 Ethernet wifi router, someone in my street. I managed to load up gusty gibbon updates, get sound working, get nividia drivers loaded and working and was moving onto my router set up next but I would test my ethernet port first. 

When I connected to my integrated Ethernet on new board it was no go. (MCP51 Ethernet)

Ive been trying all sorts of things, not an expert but not a complete novice, then I tried trawling the net for help for over an hour.

Then I hit this thread and did > ifup eth0 and bang there it was! it just started working! 

Somebody please explain! 

many thanks! :)

---

### Post by schiznik on 2008-01-26
> **pfabrikant said:**
> pfabrikant@ubuntu:~$ sudo ifup eth0
>There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5

Thats your problem right there - a stale pid file, probably caused by something restarting during the updates.

run the below:
```
sudo ifdown eth0
sudo rm /var/run/dhclient.eth0.pid
sudo ifup eth0
```

Which should stop the eth interface, clear out the pid (process ID) file, and hopefully start the interface up again.

---

### Post by Anvilfolk on 2008-01-26
Hi, Chiz!

I get those all the time, and they don't seem to affect the ability to connect. I'm still betting on the driver problem ;) In any case, I hope that solves the problem, let us know!

I haven't got a lot of time, but what I'd do if that doesn't work is find what drivers suit your ethernet card, which you can see from this line:
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

I ran a quick search on google with
linux drivers 82801DB PRO/100 VE

And quite a few sites popped up. I'd try figuring out what driver packages you need. You'll probably find instructions on how to set them up. Try searching here on the forums too, you might get lucky. In any case, if there are no instructions, just tell us what the driver is (or the page you found some relevant info at) and we'll try to give you a hand.

I'd also try to google those error messages you get while running the ifup command, along with your card, and all that stuff!

Sorry I don't have any more time, good luck!

---

