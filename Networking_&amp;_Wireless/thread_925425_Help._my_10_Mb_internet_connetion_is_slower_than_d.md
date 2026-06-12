---
title: "Help. my 10 Mb internet connetion is slower than dial up?"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by lorderico on 2008-09-20
I have a 10 Mb internet connection to my house, but my linux computer goes incredibly slowly.  Half of the time it can't load at all (the physical connection is fine).  The other half I get about 1000 B/s.  These two modes switch every few seconds, making loading a page take forever.

My windows computers work fine with the internet.  I am connected to a Linksys WRT54G router, which connects to the cable modem.  This happens when I am in static, dhcp, and roaming mode.

When I do an sudo lshw, I get this for the network section: 

 *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:11:5b:c7:62:f1
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.105 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

Can anyone help me?
Thanks,
Eric

---

### Post by blastus on 2008-09-20
WRT54G should have no problem getting 10Mb/s (megabits) over the WAN. 

First you should verify the speed of your interface as connected to your router. ```
sudo ethtool eth0
``` The above should report 100Mb/s in your case.

With your wired connection set to use DHCP, check in Network Settings if it picked up the DNS which should be the IP address of your router (the default for WRT54G is 192.168.1.1)

Install traceroute ```
sudo apt-get install traceroute
``` and enter the command ```
traceroute google.com
``` On the first line it should show the IP address of your router. On the second line it should show your WAN IP (your Internet IP address.)

Goto [http://www.speedtest.net/](http://www.speedtest.net/) and measure your network connection speed under both Windows and Ubuntu. Is there a difference in what speedtest reports?

I know you probably don't, but if you have two network cards in your computer Ubuntu can get confused about routing.

Do you have DD-WRT installed on the router?

---

### Post by lorderico on 2008-09-20
sudo ethtool eth0:

It says I am running 100 Mb/s.

traceroute google.com:

 traceroute google.com
traceroute to google.com (64.233.167.99), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  1.553 ms  1.935 ms  2.383 ms
 2  * 10.131.64.1 (10.131.64.1)  15.352 ms  15.518 ms
 3  96.34.20.74 (96.34.20.74)  15.800 ms  19.796 ms  19.974 ms
 4  96.34.16.37 (96.34.16.37)  22.228 ms  22.459 ms *
 5  96.34.16.53 (96.34.16.53)  21.153 ms *  21.523 ms
 6  so-7-0-2.edge5.Chicago1.Level3.net (4.79.208.21)  26.221 ms  13.747 ms  16.968 ms
 7  ae-21-52.car1.Chicago1.Level3.net (4.68.101.34)  17.849 ms ae-21-56.car1.Chicago1.Level3.net (4.68.101.162)  17.522 ms ae-21-52.car1.Chicago1.Level3.net (4.68.101.34)  18.027 ms
 8  GOOGLE-INC.car1.Chicago1.Level3.net (4.79.208.18)  16.456 ms  20.748 ms  20.922 ms
 9  66.249.95.246 (66.249.95.246)  30.779 ms  30.525 ms  30.065 ms
10  72.14.238.90 (72.14.238.90)  25.533 ms 72.14.238.89 (72.14.238.89)  21.721 ms 72.14.238.90 (72.14.238.90)  25.704 ms
11  64.233.175.26 (64.233.175.26)  26.697 ms  27.184 ms 72.14.232.74 (72.14.232.74)  27.429 ms
12  py-in-f99.google.com (64.233.167.99)  17.132 ms  19.189 ms  16.909 ms

Not sure what to make of this the traceroute

Speedtest.net my computer: 385 kb/s
Speedtest.net windows computer: 10 mb/s

I do not have dd-wrt installed, should I install it?  Will it mess with any windows computers' internet?

Thanks for your help,
Eric

---

### Post by shredder12 on 2008-09-20
Hey i don't know whether it will work for you or not..
but it worked for me..
Just try to disable ipv6 and tell me whether you found any difference or not..
you may do that by following this link..

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

and if even that doesn't work..
you may try this one..

[http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804](http://www.howtogeek.com/forum/topic/extremely-slow-internet-in-ubuntu-804)

hope that helps you..

---

### Post by blastus on 2008-09-20
The fact that you are going through a router and the performance is significantly different between Windows and Ubuntu strongly suggests that there is something wrong with how Ubuntu works with the network card.

I found this article that might give you some info: [Ubuntu Wired Networking Woes? Read This Closely](http://www.lockergnome.com/linux/2007/11/27/ubuntu-wired-networking-woes-read-this-closely/) From the sounds of it it looks like the card you have might be a little difficult to setup in Ubuntu. 

If I had the same issue I would just go and get a $30 Linksys or Realtek PCI ethernet card cause it's not worth the hassle. Pretty much all network cards just work out of the box in Linux so I'm surprised about this one. There isn't any configuration or setting I know of in Linux that would drastically affect wired network performance. It sounds to me like the driver Ubuntu is using for your card is just bad.

I probably wouldn't install DD-WRT on your router if you haven't already because you can brick it if you are not careful. I have two WRT54GL routers but they are made for flashing with third party firmware (note the L in the model name stands for Linux.) I also have two WRT310N routers flashed with DD-WRT firmware.

---

### Post by lorderico on 2008-09-21
I put in a generic network card I happened to have around (nothing special, just something other than the onboard network card).  Now sudo lshw -C network returns this:

 *-network:0             
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 05
       serial: 00:50:8b:5c:c8:04
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.106 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:11:5b:c7:62:f1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

I now get 6.6 Mb/s on speed test, and everything loads faster.  However, that is still not up to what my other computers get (even my other linux computer).  I think that I will take the advice here and buy a good network card to see if that works.

Thanks for your help,
Eric

---

