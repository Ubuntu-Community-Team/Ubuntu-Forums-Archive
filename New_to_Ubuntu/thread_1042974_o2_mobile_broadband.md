---
title: "o2 mobile broadband"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by engineerlee on 2009-01-18
Hi all,

I am a real newbie to Umbuntu and have started to figure a few things out but I am after some help before parting with hard earned cash.
I would like to buy a pay and go mobile broadband package (most probably O2) but want to be certain I can install and use it as O2 dont support Umbutu.
Any help and information would be greatly appreciated.

Many thanks in advance

---

### Post by gsocker on 2009-01-18
This can be done. The main problem is making sure that the hardware you buy is supported under Linux.
If it is,the main obstacle then is getting the necessary settings to make a connection. If you are using 8.10, NetworkManager may already have them builtin. If you are running 8.04, you can either upgrade NetworkManager or use one of the various PPP front-end rograms(gnome-ppp,wvdial) to connect. 
This article might help:
[http://www.techradar.com/news/mobile-computing/get-mobile-broadband-on-your-linux-laptop-486813](http://www.techradar.com/news/mobile-computing/get-mobile-broadband-on-your-linux-laptop-486813)

---

### Post by steeleyuk on 2009-01-18
I've got one. Its fairly easy to get working though there are some little bugs you might encounter.

First, Network-Manager 0.7 is easiest to set it up with, its installed by default but I know some people prefer Wicd, Wifi-Radar, etc.

Once, you plug the device in, give it a few seconds and it appears in the list. You might need to set a couple of options to get it working:

Number: *99#
APN: m-bb.o2.co.uk
PAP authentication only

Now for a couple of problems. I've installed lots of updates since Intrepid came out so not 100% sure if this applies but there was a problem where the device had to be plugged in while the computer booted for it to be detected. If you plugged it in mid-session, the machine wouldn't load the module for the device.

Second problem, again not 100% sure on this. On Windows you install the software and it allegedly brings up a landing page for you to topup. I've yet to see this work in Linux so you'll need to topup the device before you go out with it.

As for the device itself, the box says its a Huawei E160 however Linux detects it as an E220. There are quite a few different models of these and some work better by default than others.

Edit: One more point. This device DOES work under 64-bit.

Edit 2: I've just tested it. The device is now detected mid-session, whether that was an official update or not I don't know.

Edit 3: Final point. There is (was) a problem with the version of Network-Manager that came with Intrepid. It wouldn't display certain settings even though they had been applied. For example, you could tick a checkbox, close the window, then reopen and it would show the checkbox as unticked. Not a major hassle but it can be if you're trying to troubleshoot these devices. I'd recommend updating to the latest Network-Manager [from the Launchpad PPA]("https://launchpad.net/~network-manager/+archive"). However, this is unsupported and could break some other networking part (though I haven't had any problems).

---

### Post by ludwigs on 2009-02-17
Hi there,

O2 pay as you go with Huawai E160 works straight out of the box for my 
Linux xxx 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux system (Ubuntu 8.10)

I made use of NetworkManager Applet 0.7.0 and applied login data taken from Mac OSX pdf sheet (USB Modem E160 Mac Installation & Configuration Guide.pdf), see also steeleyuk's posting.

This is fabulous!

PS You might also have a look at 'iftop' for easily checking on the traffic.

Cheers,
LS

---

### Post by cfc7763 on 2009-02-17
ive got orange mobile broadband using an option icon 225 dongle any tips on getting that to work? Im pulling my hair out. Im running a hi-grade laptop with dual boot vista or ubuntu and can search my vista hard drive whils in ubuntu can i possible do something with that? it recognises my dongle as a drive for about a minute it says autoplay isnt working and if i browse my orange dongle the applications come up as blue diamonds HELP:o

---

### Post by pjti on 2009-02-20
> **cfc7763 said:**
> ive got orange mobile broadband using an option icon 225 dongle any tips on getting that to work? Im pulling my hair out. Im running a hi-grade laptop with dual boot vista or ubuntu and can search my vista hard drive whils in ubuntu can i possible do something with that? it recognises my dongle as a drive for about a minute it says autoplay isnt working and if i browse my orange dongle the applications come up as blue diamonds HELP:o


For the Icon 225 on Orange visit this site , worked for me.
[http://www.linuxhorizon.ro/icon225.html]("http://www.linuxhorizon.ro/icon225.html")

I do have to run a terminal command to get it to connect, if you get this far and get stuck send me a message, I have other links on my laptop back home (Spain next week)


Oh and am currently using O2 PAYG on 8.04 no probs if anyone wants help.

Patrick

---

### Post by pjti on 2009-02-20
> **engineerlee said:**
> Hi all,

I am a real newbie to Umbuntu and have started to figure a few things out but I am after some help before parting with hard earned cash.
I would like to buy a pay and go mobile broadband package (most probably O2) but want to be certain I can install and use it as O2 dont support Umbutu.
Any help and information would be greatly appreciated.

Many thanks in advance

I have just got it running on HP2133 with 8.04 installed, it was a bit confusing at first but having checked the syslog I could see the modem was recognised. BUT I could not get KPPP or my older version of Network Manager to find it.

I installed GnomePPP and it found the modem almost straight away,I am able to connect very easily now.

Usr = m-bb.o2.co.uk
PWD = password

Number = *99***1#    

Thats it easy as that.

---

### Post by ropey2011 on 2011-01-31
Hello all, I am new to Ubuntu a recent convert but LOVE it far more than the Mac 

and Windows systems I am used to working with. Sorry to jump in here but i could 

really do with some help please.

Just installed Ubuntu 10.10 on my old PC and have an 02 PAYG dongle for broadband 

access. The dongle works fine on my Windows 7 laptop but having problems on my 

PC. 

When I put the dongle in the USB port it goes green then flashes a blue light as 

if trying to aquire. 

I set up the connection wizard using the presets for the 02 PAYG dongle and it 

does indeed try to connect - least ways I get the green rotating icon to indicate 

that something is trying to happen. 

However the dongle just sits and flashes blue for well over 5 minutes without 

getting a steady blue light. 

What if anything do i need to change to get it work in the wizard prefs Or could 

it be that the dongle is simply not acquiring a signal being close to the floor. 

The PC tower is on the floor and the USB is on the back. 

Any help advise or sage wisdom will be REALLY useful. 

Thanks guys. 

ropey.

---

