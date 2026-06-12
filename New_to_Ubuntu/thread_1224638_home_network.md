---
title: "home network"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by necromonger on 2009-07-27
how do i config. my home network?

---

### Post by lisati on 2009-07-27
Are you looking to share files between your computer? If so, one way of configuring things is described here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by bodhi.zazen on 2009-07-27
Most home networks use routers and most routers you plug into the wall and plug in your desktops / servers / or laptops => viola you have home network.

What is it you are wanting to do ?

---

### Post by Iowan on 2009-07-27
Here's a tutorial:
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html")

---

### Post by necromonger on 2009-07-27
my network is wireless

---

### Post by jonobr on 2009-07-27
Hey  necromonger
You dont have to ask your question in the form of a haiku.

Try providing a bit more information on your setup.
Your not charged by the word.....

---

### Post by Iowan on 2009-07-27
Maybe [this]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") one?

---

### Post by necromonger on 2009-07-27
sorry about my haiku here are my specks xps 410 2 gig of ram e6400 cor 2 duo wusb54g ver 4 dual dvd burners 965 chipset ati x1300 pro 256 meg of memory and i guess that is about it.

---

### Post by jonobr on 2009-07-27
Thanks, but could you give more information on what your setup is,

what devices have you got, how are you connecting up your network, or how do you intend to connect it up.

Are you using static IP addresses or dynamic,
do you take a look at the link Iowan provided?

---

### Post by necromonger on 2009-07-27
i am uesing a wusb54g ver 4 to connect to the internet an to my local network

---

### Post by mapes12 on 2009-07-28
What jonobr means is tell us what boxes you are trying to connect. For example:

How many windows machines?
How many Ubu machines?
Are any of them dual boot?
What types of files are you looking to share on the network?
Do you have a printer on the network and what is it connected to?
Are they all wifi enabled or are some connected via ethernet?
What routers, switches or hubs do you have?

Stuff like that. There are different solutions for different network requirements.

---

### Post by AndyCee on 2009-07-28
> **necromonger said:**
> i am uesing a wusb54g ver 4 to connect to the internet an to my local network

Sorry about all the clarification requests - but you have a wireless 54g router/modem, and would like to connect a computer/laptop running Ubuntu to the internet, yes?

Have you previously had a network set up?

If you have a wireless card in your computer and it's switched on, click the two computer icons in the top-right of the screen and see if your network name is there.

If you haven't previously set up a network, post the brand and model of the router as a start.

---

### Post by bodhi.zazen on 2009-07-28
I am sorry, but we need more information.

It seems your problem is with wireless. What is your exact router (make an model) and what wireless card (make and model).

So :

1. Does Ubuntu recognize your wireless cards ? Can you see wireless networks in Network Manager ?

2. What wireless protocols are you using ? WEP, WPA ?  I usually suggest you turn wireless security off, establish a connection, then work through WEP and finally to WPA.

Tell what you have done or what how-to you are following.

---

### Post by necromonger on 2009-07-28
my neighbor has the router it is a wrt54g running hyper wert. security is off all other computers are windows.network name is mshome.i just cant figure out how to set up a network to see the other computers on the net work.i am sorry for causing all this trouble.

---

### Post by necromonger on 2009-07-28
bump

---

### Post by AndyCee on 2009-07-29
_GUI:_
Can you see the two screens at the top-right corner? What is in the menu when you click on that? If the network card is working and your neighbour's network is in range then "mshome" should appear there. Click on that and you're connected to the network. If you can get this far we're on the home stretch.

_Terminal:_
If the GUI method isn't working, do this for us and it might give us an idea what's going on.

Type these into terminal and copy the output to a post:
```
sudo ifconfig wlan0
```
```
sudo lshw -C network
```

and if you don't get errors:
```
sudo iwlist wlan0
```

I realise this might look like gibberish, but we need to start somewhere.

<Not meaning to criticize, but you haven't even told us if you already have a wireless network card in your laptop/desktop>

---

### Post by necromonger on 2009-07-29
here is something greg@greg-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:16:76:b6:bc:6d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-0 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:5a:9c:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:8a:de:00:e7:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
greg@greg-desktop:~$ sudo iwlist wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
i connect to the internet just fine with my wusb54g but i can't connect to my wireless network on on the windows machines on the wireless network.

---

### Post by LewRockwell on 2009-07-29
> **necromonger said:**
> here is something 

greg@greg-desktop:~$ sudo lshw -C network

  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:5a:9c:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bg

i connect to the internet just fine with my wusb54g but i can't connect to my wireless network on on the windows machines on the wireless network.

since your internet access is fine you are definitely connected correctly to your neighbor's wireless router

regarding interacting between other devices on the LAN, there are various settings required for each separate unit(such as file sharing permissions)

also, for reference purposes, some LAN routing devices may restrict LAN inter-connectivity(depending on the requirements and system administration)

.

---

### Post by mapes12 on 2009-07-30
> **necromonger said:**
> my neighbor has the router it is a wrt54g running hyper wert. security is off all other computers are windows.network name is mshome.i just cant figure out how to set up a network to see the other computers on the net work.i am sorry for causing all this trouble.You need to install Samba support to connect your Ubu box to see windoze machines. Here are some detailed HowTo's:

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

[http://ubuntuforums.org/showthread.php?t=202605&highlight=networking+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=networking+windows)

There will be other guides out there. Search for Samba and / or networking with linux windows, or similar.

> i am sorry for causing all this troubleNo trouble at all. If you need more help just post back. There are many people here more than happy to help out.

---

