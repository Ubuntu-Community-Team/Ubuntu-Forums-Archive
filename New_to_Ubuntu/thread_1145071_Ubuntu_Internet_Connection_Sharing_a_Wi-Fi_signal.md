---
title: "Ubuntu Internet Connection Sharing a Wi-Fi signal"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by General-Gouda on 2009-05-01
I have an old Dell Latitude which I've recently loaded Ubuntu on.  The operating system is working nicely and I'd like to use it as my main OS on the laptop.  However, there is one thing that is holding me back currently.

My upstairs neighbor has been kind enough to let us use her wi-fi for free.  Our laptops connect with ease but I also have a desktop that uses the internet.  While in Windows I use Internet Connection Sharing to share the Wi-Fi signal.  I then plug the laptop directly into my Router as its internet source and it allows my desktop to connect to the internet easily.  

I'd love to be able to do this with Ubuntu so I can rid myself of WinXP on the laptop completely but the instruction sets I have seen so far only relate to sharing Eth0 instead of a Wi-Fi signal.  

Any suggestions?

---

### Post by zigga15 on 2009-05-01
sudo apt-get install wicd

Not sure what ur problem is to be honest. Check if your laptop drivers are working: google "linux compatibility {your comp name here}"

---

### Post by General-Gouda on 2009-05-01
> **zigga15 said:**
> sudo apt-get install wicd

Not sure what ur problem is to be honest. Check if your laptop drivers are working: google "linux compatibility {your comp name here}"

The OS is working fine.  Everything is being recognized and it runs nicely.  I just want to use the laptop's wi-fi connection to share the internet with other computers.  

I currently have a dual boot situation where Ubuntu and Windows are on the same small hard drive.  I'd much rather use ONLY Ubuntu instead of switching between the two OSs just to accomplish the internet sharing.

Thanks

---

### Post by zigga15 on 2009-05-01
Still not sure what you mean...

Basically an internet connection talks to your ISP (internet service provider).

If you want multiple computers to use this internet connection you need a "ROUTER" --- this basically splits up your internet connection and gives it to each computer.

---

### Post by caravel on 2009-05-01
> **General-Gouda said:**
> I have an old Dell Latitude which I've recently loaded Ubuntu on.  The operating system is working nicely and I'd like to use it as my main OS on the laptop.  However, there is one thing that is holding me back currently.

My upstairs neighbor has been kind enough to let us use her wi-fi for free.  Our laptops connect with ease but I also have a desktop that uses the internet.  While in Windows I use Internet Connection Sharing to share the Wi-Fi signal.  I then plug the laptop directly into my Router as its internet source and it allows my desktop to connect to the internet easily.  

I'd love to be able to do this with Ubuntu so I can rid myself of WinXP on the laptop completely but the instruction sets I have seen so far only relate to sharing Eth0 instead of a Wi-Fi signal.  

Any suggestions?
So the desktop does not have a wireless NIC but is plugged into a router?  You want to use the wireless NIC on the laptop as an AP?  If this is the case and it worked in windows then the issue is not wireless but how you've set up your LAN.

What is your router connected to, is it a standard wired router?  If you provide a basic breakdown of your network topology people will be better equipped to help you.

---

### Post by General-Gouda on 2009-05-01
> **zigga15 said:**
> Still not sure what you mean...

Basically an internet connection talks to your ISP (internet service provider).

If you want multiple computers to use this internet connection you need a "ROUTER" --- this basically splits up your internet connection and gives it to each computer.

Sorry if I'm not being clear.  :(

My neighbor lets us use her wi-fi router to access the internet.  We have 3 computers in our house.  2 laptops and a desktop.  We also have a Linksys wireless router.  My desktop does not have a Wi-Fi card.  It is connected to my Linksys router through an ethernet cable.  The router has no internet source plugged into it (no cable modem or DSL modem attached to it).  Both laptops connect to my neighbors wi-fi easily.  

To allow my desktop to connect to the internet I must connect to my neighbor's wi-fi using my laptop then route the connection through the laptop to the Linksys router using Window's Internet Connection Sharing capabilities.  Basically, it turns your laptop into a gateway which provides the Linksys router with an IP address and then it allows the internet connection to be utilized by the router (basically turns my laptop into a cable modem).  The internet connection is then routed through my laptop, to my Linksys router to my Desktop.  In the end my desktop has a network connection now and can access websites, play games, etc.

I would like to do this Internet Connection Sharing within Ubuntu so I don't have to boot into Windows XP each time I want to use my desktop.  

Hope that clears it up a bit.

Thanks,

Gouda

---

### Post by mister_p_1998 on 2009-05-01
He wants to use his Wifi -enabled laptop to share the internet via wired network cards. you need a switch-box to plug in the wired machines, and your laptop into, then need to setup your laptop as a proxy. Not sure how to do this on Ubuntu, but I did this years ago in XP with a program called AnalogX. you run it on the Internet enabled machine, and you put the ip of your internet connection (on the wired machines) to the ip of your laptop, therefore your wired network machines connect to the internet via your laptops connection.


This might help:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Steve

---

### Post by General-Gouda on 2009-05-01
> **mister_p_1998 said:**
> He wants to use his Wifi -enabled laptop to share the internet via wired network cards. you need a switch-box to plug in the wired machines, and your laptop into, then need to setup your laptop as a proxy. Not sure how to do this on Ubuntu, but I did this years ago in XP with a program called AnalogX. you run it on the Internet enabled machine, and you put the ip of your internet connection (on the wired machines) to the ip of your laptop, therefore your wired network machines connect to the internet via your laptops connection.


This might help:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Steve

I've seen that before but I don't know if that applies to wireless connections.  EthX seems to only refer to ethernet NICs.  Let's say your wireless network connection is named "BobsWireless" can it be substituted for "EthX"?

---

### Post by Andrew Steyn on 2009-05-05
I know exactly what the op wants.  

Let me try and explain, because I would love to know as well.

In Windows you have to go to you network connections.  There you see all your network connections.  Usually Local Connection and Wireless Connection and so on.  If you connect to the internet using your wireless adapter, you can simply right click on that adapter and click on "allow other users on your network to connect to the internet through this  connection".  

In my case, my laptop uses it wireless adapter to connect to the internet.  I am using a wired adapter to connect to a desktop PC from my laptop.  What needs to happen now is for my desktop to be able to connect to the internet through my laptop.  

That is as clear as I can make it.

I do not have a router or anything, because the wireless network that my laptop connects to is a hotspot in my appartment building.  So the only way for me to connect to the internet using my desktop is through the laptop.

Please shed some light on this.  Thanks alot for the help so far!

---

### Post by Andrew Steyn on 2009-05-05
I have been searching high and low for 45 minutes and all I can find are threads telling me to get a router... I KNOW this can be done without a router.  Maybe I should not have wiped out my Windows after all.

LoL

---

### Post by rbc on 2009-05-05
I have not tried this and have no idea how old this document is, but if anyone gives it a go, please post back with the results
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Andrew Steyn on 2009-05-05
OK I figured it out!!!

Here is what you do:

1)  Go to the terminal and type:

sudo get-apt install firestarter

2)  Once it has installed, exit the terminal

3)  Go to "Applications" > "Internet" > "Firestarter"

4)  When you first open Firestarter, it provides you with a"Wizard".

5)  Select your device that connects to the internet (in my case wlan0)

6)  Check the box where it says "IP address is assigned via DHCP"

7)  Click next

8)  Choose the wired network adapter which is in your PC/laptop and check the box that says "enable internet connection sharing"

9)  Save settings and start firewall

AND NOW:

Make the wired network adapter's IP settings as follows:

IP:  192.168.0.1
Netmask:  255.255.255.0

leave the "gateway" open.

Save your settings.

AND THEN:

Right-click on the Wireless Connection icon and go to "Connection Information".  Here you must find the Primary and Secondary DNS addresses... write them down. 

Go to your PC that you want to share the internet connection with and do the following:

1)  Make it's wired network adapter's IP settings as follows:

IP:  192.168.0.2
Netmask:  255.255.255.0
Gateway:  192.168.0.1

Now type in the Primary and Secondary addresses you wrote down earlier.

TADA!!!

Tested this on Xbox 360 as well as Desktop PC - Have fun.

---

### Post by General-Gouda on 2009-05-06
I'll have to try this when I get home.  Just one question.  When you say:

> AND NOW:

Make the wired network adapter's IP settings as follows:

IP:  192.168.0.1
Netmask:  255.255.255.0

leave the "gateway" open.

Save your settings.

Where are these actions performed?

Thanks!!

---

### Post by Andrew Steyn on 2009-05-07
> **General-Gouda said:**
> I'll have to try this when I get home.  Just one question.  When you say:



Where are these actions performed?

Thanks!!

Thats the easy part.

Go to:

System > Preferences > Network Connections

There you will be taken to your network adapter's setup.  Click on eth0 and then click on "Edit".

There you must click on the tab "IPv4 Settings"  Set it to manual and enter the addresses I set out into the empty spaces.

---

