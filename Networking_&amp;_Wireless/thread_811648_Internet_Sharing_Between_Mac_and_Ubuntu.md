---
title: "Internet Sharing Between Mac and Ubuntu"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by gheremond@gmail.com on 2008-05-29
My problem is rather complicated, so I will take the time to explain it as best as I can

I have a MacBook Pro running Mac OS X 10.4.11 (Tiger). I have recently built an ubuntu system, aimed to be used as a cluster (if I ever make it work properly), consisting of 2 nodes, a primary one with a hard disk and dvd drive and a diskless one with no storage or boot disks attached (thin client). Both are based on the ASUS P5N-MX motherboard (with onboard 10/100Mb LAN cards) and have an Intel E2180 processor. They are connected to each other using a D-link 5-port gigabit switch, but since the LAN cards are 10/100, that is the highest speed available in the network. I also connect my MacBook Pro to the same switch, using the built-in ethernet card.

My intention is to make the diskless node boot through PXE over the LAN network (that is another story, with it own series of problems). To do so, I configured the head node as a dhcp server, so that the slave node can be assigned automatically an IP from it at startup. The head node itself has a static IP address. When I connect the MacBook, I choose in the Network Preferences (TCP/IP pane) to configure using dhcp. The MacBook then is assigned automatically an IP address from the head node (I can see the static IP of the head node as the router IP in the TCP/IP pane).

I have also installed samba on the head node and added the correct accounts to connect to/from the MacBook. On the Mac side, in the Sharing Preferences, I have activated Personal File Sharing, Windows Sharing (samba) Personal Web Sharing and Remote Login. With this configuration I am now able to:

-see the MacBook from the head node side and vice-versa,
-ping the MacBook from the head node and vice-versa,
-exchange files between the shared folders on the two systems,
-access data on a portable USB Western Digital hard disk attached to the head node from the MacBook side.

So far so good, as far as LAN networking using the ethernet switch is concerned. I have to mention that the head node (ubuntu) is not connected to the outside world (there is no router or adsl connected to the gigabit switch).

Now comes the tricky part.

I use a 3G USB modem to connect to the internet from my MacBook. It is the crappy Huawei E170, with crappy Mac OS X support and non-existent ubuntu support (as far as I can tell). Needless to say, I have had no luck trying to use it on the head node under ubuntu, the system did not recognise it and I couldn't find any drivers. So I thought I could do the following: Since the local ethernet network seems to be working, why not try sharing the internet connection from the mac side with the head node? So I went to the Sharing Preferences and on the Internet Pane, I started using internet sharing, choosing Share you connection from: HUAWEI Mobila  To computers using: Built-in Ethernet. Firewall is inactive. But although the LAN network continues to run fine and the MacBook can also access the internet, I cannot do the same from the ubuntu head node. I tried to ping from ubuntu external addresses with no success.

Things that should be mentioned:

-On the ubuntu node, in the Netwok Tools, I get proper readings in the Devices Pane once I choose the eth0 device, but once I hit "Configure", an error message appear saying the interface does not exist. Other than that, all other readings (IP address, MAC address, Interface Statistics) are O.K. All other tests (Ping, Finger, Port Scan) also work fine.

-Again on the ubuntu Network Settings, I have assigned a static IP address for the Wired connection and a subnet Mask, but no Gateway address and no DNS servers (since it is not supposed to be connected to the internet this way). I tried to enter the address of the router the MacBook gets when it is connected to the internet as a gateway, but it didn't make any difference.

-On the mac side, weird things also happen. I cannot use Internet Connect to make the call from the 3G modem and get a connection. Instead, I have to use a crappy custom software that came with it to make the connection. As a result, in the Network Port Configurations Pane, the configurations HUAWEIMobile appears, but it is ghosted. Still, the same entry appears on the internet sharing Pane, and there it is selectable as a connection source.

Any thoughts?

---

### Post by cyberdork33 on 2008-05-29
Wow. Long post with lots of info.

> **gheremond@gmail.com said:**
> -Again on the ubuntu Network Settings, I have assigned a static IP address for the Wired connection and a subnet Mask, but no Gateway address and no DNS servers (since it is not supposed to be connected to the internet this way). I tried to enter the address of the router the MacBook gets when it is connected to the internet as a gateway, but it didn't make any difference.
I think you need to use the MacBook as your Gateway since it is "serving" the internet to the LAN. I may be wrong though. 

Although you do have a MacBook, Your problem seems to be more general Networking related, so I am going to request this thread is moved to that forum, and you should be able to get much more help as this forum is really more focused on supporting running Ubuntu on Mac Hardware.

---

### Post by bapoumba on 2008-05-29
> **cyberdork33 said:**
> 
Although you do have a MacBook, Your problem seems to be more general Networking related, so I am going to request this thread is moved to that forum, and you should be able to get much more help as this forum is really more focused on supporting running Ubuntu on Mac Hardware.
Thanks, so moved :)

---

