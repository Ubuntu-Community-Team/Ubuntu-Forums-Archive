---
title: "PLEASE Save me with TEW-424UB"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by daduNo1 on 2008-09-24
I did serch lot foinf lot also som say it work for me some say it's not working 

I am trying to make my TEW-424UB H/W:3.0R make work with Ubuntu I am able to see my usb WL addpeter under *sudo ndiswrapper -l* command i can see it listed as 
net8187b: driver installed 
device (0BDA:8189) present. 

under lsusb also i can see it's there under *iwconfig*

it says 

lo no wirless extention 
eth0 no wirless extention

I can no see wierless connection under network I don't know what's going on I try to follow so many diffrent thing nothing work it's pain..... 


PLEASE HELP ME I REALLY WANTS TO GO AWAY FROM MS WINDOWS

---

### Post by willca on 2008-09-25
Can you post what this gives..

sudo lspci | grep Ethernet

---

### Post by superprash2003 on 2008-09-25
also output of lshw -C network

---

### Post by daduNo1 on 2008-09-25
below is responce for both command thanks


~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1d:92:eb:5d:5a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=76.117.119.224 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
dushyant@Makadias:~$ sudo lspci | grep Ethernet
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)

---

### Post by daduNo1 on 2008-09-25
:lolflag: 
ha ha Man it's working It's /working //////i can not belive after sepending therr whole night /Now it's working with Netgear with in two min......yep it's working in two minute..... Just remove driver from wireless utility adn aadd for netgear and booooom it's working 

GO Ububtu......

BUT How I can scan wireless avelable netwrok in my area ????


Thanks,

---

### Post by willca on 2008-09-26
sudo iwlist wlan0 scan

or use the gui, network manager

---

### Post by daduNo1 on 2008-09-26
Thanks for your help this was big one but actully I had configured for specific netwrlok once i remove then i can see all but it seems like on Ubuntu is reading low signal compare to Window????

Again THANKS YOU for your help...

---

### Post by willca on 2008-09-26
that can true. mind you most desktop hardware are windows inclined in their code so its like that sometimes....but what the heck maybe things will start to change and manufacturers will open their drivers to Linux developers.

---

### Post by daduNo1 on 2008-09-26
:) 
Thanks Wikkca for you help

---

