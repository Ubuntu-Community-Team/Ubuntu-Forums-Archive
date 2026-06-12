---
title: "Ubuntu 10.10 problems"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by anirudh215 on 2010-12-14
I have been using Linux before for quite some time and have also installed 10.04 on VirtualBox before but I have never installed for dual boot along side my Vista. I am still new to this, so please be patient.

First, I downloaded the official package from the website, the 10.10 desktop edition.
Second, I burnt the ISO on to a CD and rebooted with the CD inside.
Third, I chose the option 'Install Ubuntu alongside another OS'.
From here, many problems started cropping up.
#1 I have heard/read from many sources that the installation was supposed to be very quick, but mine was painfully slow. It took nearly an hour.
#2 It then said the recommended settings were to have a 2.6 GB space allotment, for which it showed a green tick, Some second option for which it showed a green tick, but the third one, the one that said internet connection needed showed a green tick for a minute or so then turned into a black cross. I proceeded with the installation but I kept getting an error message 'something wicked has happened'. This process went on for nearly half hour. After I clicked on the option 'skip', it went ahead and 'completed' the installation.
#3 Finally when I rebooted to Ubuntu, I could not connect to the internet. It says connected to 'auto eth1' sometimes, or not connected to anything sometimes.
#4 When I boot into Ubuntu, I get this message ' FATAL error. Could not load..'

What is going on? Could someone please help?

EDIT:
I have installed the same Ubuntu 10.10 on VirtualBox and it works like a charm. Why can't I set it up for dual boot??

---

### Post by low_rider on 2010-12-14
As for the ubuntu installing problems it would help if you could provide a little bit more information such as what exactly it is failing to load.  

As for the internet troubles you may be able to fix that without reinstalling.  Try using ifdown and ifup on eth1 to see if that connects you to the internet.  Also try looking at /etc/network/interfaces.  Oh and when it says you are connected to auto eth1, can you get on the internet?

---

### Post by anirudh215 on 2010-12-14
I've already tried using ifup eth1, but is of no use. What exactly does one look for in /etc/network/interfaces? When it says I am connected to auto eth1, I cannot connect to the internet.

All the packages that are supposed to downloaded from the net are not and thus I am given the error message that it has failed to load.

---

### Post by low_rider on 2010-12-14
From what it sounds like, this problem is kinda out of my league.  It may be best to try a full reinstall, but I don't really know enough about the problem to give you advice on what to do differently. If you still want to know more about /etc/network/interfaces, this is a good site to learn about what goes in there.

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

Sorry I couldn't be more of a help.

---

### Post by akand074 on 2010-12-14
Are you on a desktop or a laptop? Are you using a wired connection or a wireless connection? Any more information on the errors?

---

### Post by anirudh215 on 2010-12-15
I've tried re-installing twice now. Each time it has failed to load internet. There is a red exclamation mark over the internet sign. I am on a desktop. I have an Atheros L2 fast ethernet wired connection. This connection works fine on my Vista. When I try to ping google through one of their ips, I get no connection. I tried doing
sudo ifconfig ifup
sudo ifconfig eth0 up
but neither worked.

---

### Post by Hippytaff on 2010-12-15
What is the output of the followin commands
```

lspci | grep -i net

```
```

iwconfig

```
```

ifconfig

```
```

lshw -C Network

```
(might be a lower case n in the last command ie network, not on my ubunut box to check :-)

---

### Post by anirudh215 on 2010-12-15
lspci | grep -i net
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:13:74:00:5c:38  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:74ff:fe00:5c38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2362 (2.3 KB)  TX bytes:13634 (13.6 KB)
          Memory:bdec0000-bdf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

sudo lshw -C Network
[sudo] password for *****: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: a0
       serial: 00:13:74:00:5c:38
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=10.0.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:bdec0000-bdefffff memory:bdea0000-bdebffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:b800(size=256) memory:bddffc00-bddffcff memory:bdde0000-bddeffff

---

### Post by Hippytaff on 2010-12-15
I don't know how old this documentation is, but it's guidance to install the driver you need for your wireless. [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)
Alternatively plug in an ethernet cable, do

```

sudo apt-get update

```
then go to System -> Administration -> Alternative Drivers, and select any recommended Atheros wireless device drivers.

---

### Post by anirudh215 on 2010-12-15
But I'm not running wireless. I'm running a wired connection. I tried out what you said anyway and it doesn't work.

---

### Post by hwychld on 2010-12-16
The result of your ifconfig command says the card is Up and is assigned an IP address.  When you boot into Vista, what is the IP address of the computer?  Do you have a router on your network?  Is it providing DHCP services?  

When you had Ubuntu working in Virtual Box was the VM ethernet adapter set up for NAT or in Bridged mode?

---

### Post by anirudh215 on 2010-12-17
What do I with it? Yes, I have a router. My modem is connected to my router.

I don't understand the rest of your message. What does 'providing DHCP service' mean? What is NAT or bridged mode?

---

### Post by hwychld on 2010-12-17
If you can edit you post you should remove the IP address that you posted, that looks like your external IP address (the address of your modem as seen by the rest of the internet).

Private IP addresses (like you would see between computers on your local network) start with these types of numbers:

10.xxx.xxx.xxx
172.16.xxx.xxx
192.168.0xx.xxx

For instance, the IP address that your Ubuntu machine is reporting: 10.0.0.3.  I would suspect, if this is a valid address, that your router is 10.0.0.1 (just  a guess).

DHCP stands for Dynamic Host Configuration Protocol.  It is used to assign IP addresses to devices when they join the network.  In most home networking situations this function is performed by the router or the modem if no router is present.  What I am trying to determine is if the IP address assigned to your Ubuntu machine is valid for your network.

It would help if you could boot Vista, open a command window (run-> cmd) and type ipconfig.  This should tell you the IP address of your Vista machine, which we know is working on your network.  I would guess it would be the same assigned to Ubuntu (the IP address will be correlated with the MAC address of the ethernet card which will be the same whether you boot Vista or Ubuntu).  At the very least I expect to see an IP address on the same subnet as the one Ubuntu is reporting 10.0.0.x.  If not, then we have an idea where to look for the problem.

As for the NAT vs. bridged don't worry too much about that.  When Virtual box is setup to use NAT your host OS (Vista) and your guest OS (Ubuntu) basically share the same IP address.  This is the default for Virtual Box.  If your Vista works, the guest will work too.  In bridged mode the guest OS (Ubuntu) appears as a individual machine on the network - even showing a different MAC address.  If for some reason your network is not providing a DHCP service (which would mean your Vista IP is statically assigned) then the guest Ubuntu might not have internet access just like your Ubuntu in dual boot configuration.  Again, I am just trying to determine if your network is providing DHCP and the IP address reported by Ubuntu is valid for your network.

Good luck.

---

### Post by anirudh215 on 2010-12-17
Um... I don't see any IP address here. I do see an IPv6 address, IPv4, subnet mask and default gateway, whatever these terms mean.

---

### Post by hwychld on 2010-12-17
If you run ipconfig in Windows, you should see something like below:

```


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\ipconfig

Windows IP Configuration

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . : domain.local
        IP Address. . . . . . . . . . . . : 192.168.6.26
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.6.1

Ethernet adapter VirtualBox Host-Only Network:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.56.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

```

I don't have access to a Vista machine at the moment, but I would expect the result to be about the same.

---

### Post by anirudh215 on 2010-12-18
Ok. Those numbers that show up as the IP address for you are called my IPv4 address. Done. So what now?
I found out I have an Atheros L2 Fast Ethernet 10/100Base-T Controller. Could that be causing problems? Now my iPhone does not work with the wifi either. It too detects the connection much like my ubuntu, but when I start any website, the loading bar keeps circling and returns an error after some time. The same is happening on my ubuntu when I start firefox. What could be wrong?

---

### Post by anirudh215 on 2010-12-18
UPDATE: I have tried installing Arch on this system, but it too doesn't connect to the net although it seems to detect a connection. What on Earth is going on? Nothing but my Vista seems to be able to use this internet. :(

---

### Post by hwychld on 2010-12-18
So what IPV4 address is your Vista reporting?  We know that one seems to work so I am trying to compare it with the IP address of the Ubuntu machine.

---

### Post by anirudh215 on 2010-12-18
192.168.1.2 This is different from the Ubuntu IP which you said was 10.0.0.3

---

### Post by hwychld on 2010-12-18
Yes it is, which is why it is not working.

In Vista we need to determine if it got that IP address by DHCP or if it is statically assigned.  Unfortunately, I know squat about Vista.

In XP the steps would be Start->Control Panel, select network connections, highlight the Local Area Connection and choose properties.

Once the properties window comes up scroll down to the bottom of the list and choose Internet Protocol(TCP/IP) and click the properties button.  If it says "Obtain IP Address Automatically" then something on your network is providing the DHCP service.  If it says "Use the following IP address" with the 192.168.1.2 listed, then you will have to statically assign an IP address to Ubuntu.

---

### Post by anirudh215 on 2010-12-19
It says obtain an IP automatically. What do I do now?

---

### Post by hwychld on 2010-12-19
Go to System->Preferences->Network Connections

Select the Auto Eth0 and select edit.  Select the ipv4 tab and make sure DHCP is set.

As a temporary workaround until we figure out what is going on you can use this edit box to manually assign the same IP as your Vista box uses.  Select manual, select add address, type in your address with the mask of 255.255.255.0 and the gateway the IP of the router.  See if your network connection works then.

---

### Post by anirudh215 on 2010-12-20
Nope. That doesn't work. I still can't connect to the net but the error message pops up sooner, if that's of any comfort.

---

### Post by jrdk on 2010-12-26
> **Hippytaff said:**
> I don't know how old this documentation is, but it's guidance to install the driver you need for your wireless. [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)
Alternatively plug in an ethernet cable, do

```

sudo apt-get update

```
then go to System -> Administration -> Alternative Drivers, and select any recommended Atheros wireless device drivers.

I'm running Ubuntu 10.10 64-bit, Fedora 14 64-bit and Win 7 64-bit on a Dell XPS M1530, and I also can't seem to get my Wired Connection working while on Ubuntu, but I can get wired and wireless in Win 7.

After I did, su - root, to get into root.
I type:

```

 lspci | grep -i net

```

 09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller(rev 12) 0b:00.0 Network controller: Broadcom Corp: BCM4312 802.11b/g LP-PHY ( rev 01 )

after typing:
```
 
sudo iwconfig

```

   lo no wireless extensions

   eth0 no wireless extensions

   wlan0 IEEE 802.11bg ESSID off/any

after typing 
```

sudo ifconfig:

```

   eth0 Link encap:Ethernet HWaddr 00:23:ae:0f:a3:fe
        inet6 addr: fe80::223:aeff:fe0f:a3fe/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU 1500 Metric: 1......

   lo Link encap: Local Loopback
      inet addr:127.0.0.1 Mask: 225.0.0.0.......... and so on 


   and my wanl0 Ethernet HWaddr 00:23:4e:6d:4c:6e


I try doing sudo apt-get update and I get a lot of errors involving:

 Could not resolve 'security.ubuntu.com'
 Could not resolve 'ppa.launchpad.net
 Could not resolve 'us.archive.ubuntu.com'
 Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick](http://security.ubuntu.com/ubuntu/dists/maverick)... and so on


I plug in my ethernet cable, wait, and it says there's no network connection. The ethernet cable is coming from my router which is coming from my modem. I can get ethernet on my Vista desktop.  

and one more token of information:

I type while in root: 
```

  lspci -n | grep 14e4

```

and find this: 0b:00.0 0280: 14e4 4315( rev 01 )
Dell 1395 <- my device ID

which I got from here:  

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
    

The website above suggests building a module, but I'm unable to because apt-get update will not work. Have any possible ideas?:)
I appreciate any feedback

---

