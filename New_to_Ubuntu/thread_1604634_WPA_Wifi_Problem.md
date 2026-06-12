---
title: "WPA Wifi Problem"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ?#Yhf%*&amp; on 2010-10-24
Hi everyone...

I am running Ubuntu 10.04 LTS on an iBook G3. I also have a wifi network with the WPA standard. Every time I try to connect, I enter the password, it tries for about a minute, then asks for the password again. Sometimes it asks for my kechain too. :?

P.S. My wifi was working fine (with the same setup) on my previous Mac OS X installation :confused:

---

### Post by cariboo on 2010-10-25
We need to know what make/model wireless device you system has, can you paste the outputs of:

```
lspci
```

and

```
sudo lshw -C networking
```

in your next post.

---

### Post by ?#Yhf%*&amp; on 2010-10-25
Output of lspci:

```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun GEM)
```


There was no output for sudo lshw -C networking, I assumed you meant to say sudo lshw -C network, and here are the results of that:

```
  *-network               
       description: Ethernet interface
       product: UniNorth/Pangea GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:03:93:1e:37:46
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:19:59:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```

Hopefully the forums can help me now. :)

---

### Post by I Am Noob on 2010-10-25
Hey Corbin052198,

I know i'm not using a Mac (currently using a Windows desktop for Ubuntu 10.10) but i had a WiFi issue when installing Ubuntu, then after some trouble I decided to try a fresh install with my desktop hooked up to my router... This meant that Ubuntu could download extra drivers otherwise not available (some for WiFi) during the installation process and afterwards my WiFi worked fine.

It just depends on weather you're in a situation where you can afford to do a complete re-install!?

Hope this may have been of some use :D

---

### Post by anewguy on 2010-10-25
It does show it is using the orinoco driver, so I'm not sure if there is some updated driver or not.  What you may want to try:

- if possible:

hard wire a connection to your router
in a terminal:  sudo apt-get update

- check in System/Administration/Hardware Drivers (I *think* that's what it's called - I'm in Windows right now) and see if there is a driver listed - if so, be sure to enable it.

Also, sometimes once you've made an error, network manager can be a little bit of a pain because it will try to use an existing definition.  I would go into network manager, delete the current definition for your network, then manually set up the connection in network manager - being sure to get your WPA type correct, the correct password/passphrase (I don't remember right now, but it may also want to know if it's a 64 or 128 bit key).

Dave ;)

---

### Post by ?#Yhf%*&amp; on 2010-10-25
> **anewguy said:**
> It does show it is using the orinoco driver, so I'm not sure if there is some updated driver or not.  What you may want to try:

- if possible:

hard wire a connection to your router
in a terminal:  sudo apt-get update

- check in System/Administration/Hardware Drivers (I *think* that's what it's called - I'm in Windows right now) and see if there is a driver listed - if so, be sure to enable it.

Also, sometimes once you've made an error, network manager can be a little bit of a pain because it will try to use an existing definition.  I would go into network manager, delete the current definition for your network, then manually set up the connection in network manager - being sure to get your WPA type correct, the correct password/passphrase (I don't remember right now, but it may also want to know if it's a 64 or 128 bit key).

Dave ;)

Thanks! Would it work if I shared my Wifi connection with Ubuntu over Ethernet? I am running Mac OS X 10.4.11 on my iMac G5 and I know you can do that.

---

### Post by anewguy on 2010-10-25
I have to tell you I really don't know.  I've actually never shared an internet connection in my life - always had separate connections.  I hope someone can chime in on that and help you more.

In the mean time, any luck with the suggestions?

Dave ;)

---

### Post by ?#Yhf%*&amp; on 2010-10-26
> **anewguy said:**
> I have to tell you I really don't know.  I've actually never shared an internet connection in my life - always had separate connections.  I hope someone can chime in on that and help you more.

In the mean time, any luck with the suggestions?

Dave ;)

I have not had much time to myself lately, and I have only tried once. Since the FireWire showed up as a Internet connection, I tried to share it with FireWire. Did not work. I think the FireWire is broken on the iBook. Next I am going to try Ethernet.

If that doesn't work, I'm probably going to set up a guest (WEP) wifi to use for a couple days to get my system some software and upgrade to Ubuntu 10.10.

---

### Post by anewguy on 2010-10-26
Don't remember if I asked - has this PC ever connected over the same network?  If not, perhaps you have MAC filtering on in the router and need to add the PC's MAC to the router list.

Dave ;)

---

### Post by ?#Yhf%*&amp; on 2010-10-31
I thought I would give a general update:

I have updated to Ubuntu 10.10 with no success regarding the WPA network.

And that's pretty much it :(

Now I have another question. I read about IPv6 is enabled by defult in Ubuntu. I wonder if that could be the trouble. I am using a Time Capsule to generate my WPA network. Can someone show me how to disable IPv6?

---

### Post by ?#Yhf%*&amp; on 2010-11-04
I was doing some work on my iBook in the kitchen, which is right below the wifi base station. OpenOffice freezed, so I had to restart my computer. I set my iBook to automaticly try to connect to my WPA wifi network even though it did not work before. It connected! I suppose it was just my distance from my base station. I watched in glee as macrumors.com loaded in Firefox :D

Thanks everyone for your replies. ;)

---

