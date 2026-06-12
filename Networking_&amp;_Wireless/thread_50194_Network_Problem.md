---
title: "Network Problem"
date: 2005-07-19
forum: Networking &amp; Wireless
---

### Post by elamison on 2005-07-19
I've just installed 5.04 and I have a strange network problem. The card (3COM EtherLink XL PCI) is recognized and works when I connect directly to the internet. However, when I connect to my D-Link DI-624 router it will not work. I can't reach (ping) it at all. Loopback works fine. I have the MAC address in the router and setup. I have tried it with filters off and as a DMZ. The cable is ok. here's the setup:

         address 10.10.10.23
         netmask 255.255.255.0
         network 10.10.10.0
         broadcast 10.10.10.255
         gateway 10.10.10.1

---

### Post by mad_scientist03 on 2005-07-19
I don't quite understand what's happening. I'm assuming you have some always-on internet connection of some sort (DSL? cable modem? ethernet?), and when your computer connects to that jack directly it works. What do you mean by "I can't reach (ping) it at all"? Are you trying to ping the router from your computer?

Connect the computer to the jack, then "sudo /etc/init.d/networking restart", and then "ifconfig". Post the output. Connect the router to the jack, the computer to the router, perform the same two commands, and post the output. Maybe we can start figuring things out from there.

---

### Post by elamison on 2005-07-19
Thanks, for helping. I have a broadband connection (RSAir). I have the router connected to the main line and Three computers on the router. A wireless Mac and a wired PC. Everything works fine. 

I tried connecting the Ubunto box directly to the internet and it works. I do the /etc/init.d/networking restart and it reconfigures and gives an [ok] and the internet connection works. 

I plug the box into the router, set up just like the other computers and run the /etc/init.d/networking restart and it gives the same [ok] but I can't get to the internet. I pinged the router (10.10.10.1) and the other computers on the network and it gives me a "destination host unreachable".

---

### Post by mad_scientist03 on 2005-07-19
Okay, after you have plugged your computer into the router and do the "sudo /etc/init.d networking restart" routine, type "ifconfig" in the terminal, and post the output. That will help determine what networking settings are being used.

Also, do you know what the (private) IP addresses of the wireless Mac and wired PC are?

---

### Post by elamison on 2005-07-19
Here's the ifconfig eth0 (without my mac address):

Link encap:Ethernet    HWaddr:[MY MAC ADDR]
inet addr:10.10.10.23    Bcast:10.10.10.255    Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST    MTU: 1500    Metric:1
RX packets:0    errors:338    dropped:0    overruns:0    frame:676
TX packets:90    errors:0    dropped:0    overruns:0    carrier:0
collisions:0    txqueuelen:1000
RX bytes:0 (0.0b)    TX bytes;5400 (5.2KiB)
Interrupt:11    Base address:0xe800

The router is at 10.10.10.1
Mac 10.10.10.20
PC 10.10.10.21

I also have a broadband phone at 10.10.10.22

I also did a netstat -rn:

Destination     Gateway    Genmask                Flags    MSS Window    irrt Iface
10.10.10.0     0.0.0.0       255.255.255.0        U          0        0          0    eth0
0.0.0.0         10.10.10.1   0.0.0.0                    UG        0        0          0    eth0

---

### Post by mad_scientist03 on 2005-07-19
Okay, good. It's a good sign that at least you're getting assigned an IP address that looks reasonable. Now, when you "ping 10.10.10.1" or "ping 10.10.10.21", what output are you getting?

---

### Post by elamison on 2005-07-19
I get a "Destination Host unreachable" and 100% packet loss. 

Also:

I also did a netsta -rn:

Destination    Gateway      Genmask           Flags   MSS   Window irrt Iface
10.10.10.0      0.0.0.0       255.255.255.0    U        0          0       0   eth0
0.0.0.0           10.10.10.1  0.0.0.0                UG      0          0       0 eth0

---

### Post by mad_scientist03 on 2005-07-19
So are the settings that you provided at the beginning of the thread present in the /etc/network/interfaces file and thus you're using a static IP arrangement, or are you receiving a DHCP lease from the router?

---

### Post by elamison on 2005-07-19
Yes, those are the settings in the /etc/network/interfaces file and I'm using a static IP. Although I tried DHCP and that didn't work either.

---

### Post by gruepig on 2005-07-19
[QUOTE=elamison]
UP BROADCAST RUNNING MULTICAST    MTU: 1500    Metric:1
RX packets:0    errors:338    dropped:0    overruns:0    frame:676
TX packets:90    errors:0    dropped:0    overruns:0    carrier:0
collisions:0    txqueuelen:1000
RX bytes:0 (0.0b)    TX bytes;5400 (5.2KiB)
[/QUOTE]

The received errors (338) looks atypical.  Is that number increasing?  If so, check /var/log/dmesg and /var/log/syslog for messages.

Also, you said using DHCP didn't work.  Do you mean you received a DHCP lease (IP address, netmask, etc.), but couldn't ping anything?  Or that you didn't receive a DHCP lease at all?

Finally (perhaps not the problem but easy enough to check) try using a different ethernet cable and/or different port on the router.

---

### Post by elamison on 2005-07-19
I'll have to wait until morning to check /var/log/dmesg, but i think the errors are increasing. 

With DHCP I couldn't get a lease. It would time out trying. I've tried 3 cables and all the ports on the router.

Thanks again fot the help, I'll check the dmesg in the morning.

---

### Post by skyboy on 2005-07-20
can you post your /etc/network/interfaces

i had similar troubles and find out it was a mapping problem, especially if you have several network cards.

---

### Post by elamison on 2005-07-20
I just have one card. here's the /etc/network/interfaces:

#The loopback interface
auto lo
iface lo inet loopback

#primary network interface
iface eth0 inet static
    address 10.10.10.23
    netmask 255.255.255.0
    network 10.10.10.0
    broadcast 10.10.10.255
    gateway 10.10.10.1
auto eth0

There's also some hotpluggable stuff commented out.

---

### Post by skyboy on 2005-07-20
try adding before #the primary network interface, in the hotplug "stuff" :)

mapping hotplug
script grep
map eth0

also remove "auto eth0"

---

### Post by elamison on 2005-07-20
OK, I tried that. Still the same results.

---

### Post by skyboy on 2005-07-20
just to be sure, you don't have any firewall ?

type iptables -L -v and paste the result here

---

### Post by elamison on 2005-07-20
I had done a flush of iptables before. iptables -L -v showed INPUT FORWARD and OUTPUT all empty.

I can't find anything wrong with the configuration especially since it works with a direct connection. I had the same card running with windows connected to the same router also.

---

### Post by skyboy on 2005-07-21
Have you tried using some other class of addresses ? like C class instead of your A class.
I'm not sure about if it is standard to have A class in simple network.
try using C class,  192.0.0.0 	till 223.255.255.255

---

### Post by PhilippWollermann on 2005-07-21
I guess that your network card doesn't work correctly with the router. These errors suggest, that there is some hardware not working. :) If it isn't a problem with the cable, I'd try a different network card. I also had a problem like this, when I connected my PC with a Netgear GA302T Gigabit network card to an old 3Com 10 MBit Hub - it simply didn't work.

If you can't get another network card, you could try to put a switch (or a hub) between the router and your PC.. I know, this seems like a strange solution, but it should work. ;)

Philipp

---

### Post by elamison on 2005-07-21
I tried switching to the 192.168.0.0 range. I also tried resetting the router to factory defaults and reinstalling Ubuntu. The strange thing is that I've used this card (win xp) with this router and it worked.

---

### Post by skyboy on 2005-07-21
mysterie of computers ... :D
sorry mate, the weapons are to heavy now, can't fight anymore. 
Try with another network card, just to test, and report it here, i'm curious :)

---

### Post by elamison on 2005-07-21
I have one I can try tomorrow. I'll let you know what happens. Thanks for your help.

---

### Post by elamison on 2005-07-22
That's it. I put in a Linksys card and booted up. It recognized it instantly and it works with the router. Must of been something that my D-link router didn't like with the 3Com card. Thanks for all the help.

---

### Post by skyboy on 2005-07-22
Well, I'm really happy for you. Now we finally know what was wrong. But I would be very interested to know why this incompatibility happened! Mystery of computers ??? :)

---

