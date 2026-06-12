---
title: "newbie network help"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by 900donuts on 2007-01-06
i've got what i belive to be a unique network set up 

1. a CHEAP NO FUTURE 2.8Ghz celeron eMachine with 768MBs of ram that runs windows

2. a wonderful 1Ghz athlon costom job with 512MBs of ram that runs linux

3. a 5 port dumb ethernet hub 

4. 3 UTP cables 

5. and 3 network cards (1 in the windows and 2 in the linux)

can anyone provide me a little step by step on how to on how to make this work

i have no windows or linux networking experience and please keep all windows jokes seperate from your help 

thanks in advance

---

### Post by 900donuts on 2007-01-06
oh I almost forgot I had already tried just pluging everything in and hopeing for the best. the linux machine could acsess the internet but not the windows one it used a sbc browser and it couldn't log in

---

### Post by celem on 2007-01-06
You need to set up SAMBA in order to network between a Linux box and a Windows box. See the WiKi instructions at:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by celem on 2007-01-06
This may be more useful:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by 900donuts on 2007-01-06
ok the second link says Its best if i had a static ip how do I do that?:-k

---

### Post by celem on 2007-01-06
I guess that I don't understand your goal. I was answering about how to network the Windows box and Linux box so that you can access files/folders between machines. That is SAMBA's role. If, on the other hand, you are simply trying to get both machines to be able to access the internet, you don't need SAMBA.

You only mention a "5 port dumb ethernet hub" and don't mention a router. What is supplying the DHCP for your machines?

---

### Post by 900donuts on 2007-01-07
well my goal is to have them both access the internet at the same time (for example someone plays think tanks while someone else plays runescape) 

as for a router thats some thing i forgot to include the internet provider provided one

---

### Post by celem on 2007-01-07
You don't seem to have a Linux question since you initially stated "the linux machine could access the internet but not the windows one". Since the Linux box works fine your issue is with the Windows box and this forum won't be of value for you.

You ISP feeds the router. The router contains your DHCP server that supplies both of your computers with their IP addresses. Since the Linux box works, it means that the router, DHCP server, and ISP connection are all OK. Your Windows setup must be wrong. IN the Windows box make sure that you have DHCP correctly setup in the "Network Connections" in control panel. You'll need to go to BillGates for that info:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/hnw_wizard_overvieww.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/hnw_wizard_overvieww.mspx?mfr=true)

---

### Post by Koybe on 2007-01-07
How is physicaly plugged your network?

Is your ubuntu plugged one network in the router and the other in the hub or is your router directly connected to the hub and only one network car is used on your linux box?

---

### Post by 900donuts on 2007-01-08
my current network setup is that all the parts (router, win box, lin box) are pluged in to the hub seperately they do not go through the linux and this setup would be fine if it worked 

the people who use the windows are complaining that the internet is slower now and it takes several trys to load a web page

ive even noticed problems on my linux machine i get long connection failures when i play think tanks

could these prolems be remedied if i used the linux box as a gate way?

copuld they both use the internet at the same time?

---

### Post by celem on 2007-01-08
You don't mention if the router has multiple ports on it. If so, I would plug each computer into its own port on the router and reserve the hub for expansion. The simpler the setup the better it is.

You should isolate the source of your problem. Start by taking a PC, I'd use the Windows box since it is having the most difficulty, and directly connect it to the broadband connection and test it there, without any other equipment attached. If the problem remains, your ISP connection is the trouble.

---

### Post by 900donuts on 2007-01-08
the router or dsl modem or what ever it is has only one ethernet port

I asked a local highschool computer teacher for advice he said it might be (i not sure i remember everything) but it was something like the rout only has 1 ip adress so each computer has to wait their turn and that i should call the isp he said something like that i thing :-k

---

### Post by celem on 2007-01-08
It sounds like you just have a broadband modem and your "hub" is a switch. You need a router supporting DHCP for IP assignment. Do yourself a favor and get a router. See: [http://www.dlink.com/products/?pid=478](http://www.dlink.com/products/?pid=478)

---

### Post by repins on 2007-01-09
just a suggestion here, but if you can get your hands on a old machine with two nic's, you could set up smoothwall on it and use it as a router (if im understanding what your needs are), and by old computer i mean it can run on a 486 machine. [http://www.smoothwall.org/about/](http://www.smoothwall.org/about/)


|modem|---->|smoothwall|---->|5 port hub|----->|pc's|

---

### Post by 900donuts on 2007-01-10
i don't understand WHY CAN"T I JUST PLUG THE WIN BOX IN TO THE SPARE NIC ON MY LINUX MACHINE CANT MY LINUX MACHINE SHARE THE INTERNET CONNECTION ????](*,) 

I do have a spare pentium lyeing around but i dont have enough nics

and as for the hub the box says its a hub its as big as a hub which is not very big and the way the network is working i have no reason to think other wise

---

### Post by celem on 2007-01-10
You can try "squid". read:

[http://www.linuxheadquarters.com/howto/networking/squid.shtml](http://www.linuxheadquarters.com/howto/networking/squid.shtml)
[http://www.linuxforums.org/forum/linux-networking/44597-how-share-internet-connection.html](http://www.linuxforums.org/forum/linux-networking/44597-how-share-internet-connection.html)
[http://www.trustix.org/forum/archive/index.php/t-161.html](http://www.trustix.org/forum/archive/index.php/t-161.html)

try sudo apt-get install squid

---

### Post by 900donuts on 2007-01-10
ok ill give squid a shot is there anything else i should know like problems people have had or mabey some made for ubuntu easy to understand how to's?

---

### Post by repins on 2007-01-10
> **900donuts said:**
> i don't understand WHY CAN"T I JUST PLUG THE WIN BOX IN TO THE SPARE NIC ON MY LINUX MACHINE CANT MY LINUX MACHINE SHARE THE INTERNET CONNECTION ????](*,) 

I do have a spare pentium lyeing around but i dont have enough nics

and as for the hub the box says its a hub its as big as a hub which is not very big and the way the network is working i have no reason to think other wise


I think this is what you are looking for, hope it helps. [http://rob.pectol.com/content/view/3/58/](http://rob.pectol.com/content/view/3/58/)

---

### Post by 900donuts on 2007-01-11
ok if squid doesn't work ill try that but i haven't had a chance to try anything yet because the win box has been occupied and every thinks that ill break it if it comes in contact with linux(just a joke only one person thinks that:D )
but i was wandering if a ps2 could be tossed into this mix(some games have on line play). will it work?

---

### Post by konungursvia on 2007-01-11
> **celem said:**
> You need to set up SAMBA in order to network between a Linux box and a Windows box. See the WiKi instructions at:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Hmm. Well I just set up Dapper on my Acer, so I have 2 lin boxes both on cable from the same router (wireless I'll set up later). Do I need to use samba to network the two computers? So far there isn't anything obviously similar to Network Neighbourhood that I see. How do I access the other computer's drives from this one?

---

### Post by 900donuts on 2007-01-11
well first if you did not have more beans and if this was somewhere else i would scream thread hijacker

and second i think samba is just for linux<-->windows file shareing but i did not go with smba because im worried about connection shareing

---

### Post by repins on 2007-01-12
> **900donuts said:**
> ok if squid doesn't work ill try that but i haven't had a chance to try anything yet because the win box has been occupied and every thinks that ill break it if it comes in contact with linux(just a joke only one person thinks that:D )
but i was wandering if a ps2 could be tossed into this mix(some games have on line play). will it work?


yes, the ps2 should work (i have never personaly set it up though), because it is running that first linux box as a router, but that is why i was trying to suggest the other way, its just  safe practice to not be web surfing and such on the box that is the gateway for your other machines.

---

### Post by 900donuts on 2007-01-12
thats a problem looks like im going to have to buy another nic and make that old pentium do the work is there a version of ubuntu light wieght enough for 200mhz, 64mb of ram, no floppy, and a 500mb hard disk?

---

### Post by repins on 2007-01-13
> **900donuts said:**
> thats a problem looks like im going to have to buy another nic and make that old pentium do the work is there a version of ubuntu light wieght enough for 200mhz, 64mb of ram, no floppy, and a 500mb hard disk?

The way i suggested would not be ubuntu at all, it would be smoothwall, which is a NAT router (so there wont be a web browser or anything), with tonnes of features and add on. But i notice an issue.

Minimum System Requirements For SW Ex 2.0:

    * 64MB RAM (recommend)
    * 150MHz CPU or better (I had mine running off 75 MHz)
    * 1Gb Hard Drive Space
    * 2 10/100 Network Interface Cards (NIC)
    * CDROM Drive
    * Monitor (only needed to install)
    * Any Video Card
    * Any Keyboard and Mouse


With the floppy you only need it for the install, so you can swap it out of one of the other systems, same with the cd (although cd is not needed, you can do a network install). And yes ps2, xbox, ETC, anything will run behind this with the proper ports being forwarded.

---

### Post by 900donuts on 2007-01-13
first the pentiums mobo can not work with floppy that part of the board is damaged or something (in a past life it was driven in to the ground)

second i've so far had poor luck with burning any thing but ubuntu disks

---

### Post by repins on 2007-01-14
Ok, i found exactly what you need "firestarter" [http://www.fs-security.com/](http://www.fs-security.com/) , and it's very easy to setup.

**sudo apt-get firestarter**

or download from synaptic package manager.

It will have you go through a wizard, setting up eth0 for your internet connection, and eth1 as a dhcp server.  let me know if this helps at all.

---

### Post by 900donuts on 2007-01-20
so this will allow me to have both computers use the net at the sametime (both playing online multiplayer games?) no extra hardware needed?

---

### Post by repins on 2007-01-21
> **900donuts said:**
> so this will allow me to have both computers use the net at the sametime (both playing online multiplayer games?) no extra hardware needed?


That is correct.

---

