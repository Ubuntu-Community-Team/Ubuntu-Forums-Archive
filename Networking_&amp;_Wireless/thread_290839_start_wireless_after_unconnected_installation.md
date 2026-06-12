---
title: "start wireless after unconnected installation"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by thegitksan on 2006-11-01
Good afternoon. I have an Acer 3613LCi with an 802.11 b/g wireless lan. Recently I installed Edgy using the Alternate disk, but did so at home, away from my office's wireless LAN. I installed it as a dual boot, with WinXP as the other OS.

In Windows XP, the wireless network is detected automatically, and I can connect to internet with zero problems. I do sometimes have to Connect to this network, but that is trivially easy.

Now I am faced with trying to make sense of setting up and connecting to the network/internet manually, after the basic installation is done.

At the time of installation, the install program tried to look for the network/internet, but I had to cancel, as I was not at office.

The wireless is recognising that a wireless card is there, and I tried to configure it. 

What on earth is an ESSID? Where do I get one? Why do I need a password to get one?

Is there an easy way to get Ubuntu to just do the work - find the network by itself, and then connect to it, the way Windows can?

I'm not dumb, I've been using PCs and even Linux, for years. Never had to configure for wireless, however, and this has me baffled. The documentation is really scanty here, just says click this, enter ESSID there. Tried reading through forum posts and everybody seems to be linux gods, coding all kinds of solutions (sudo this, then gtk the other thing and then compile all of it). I don't need to know how to build my OS from the ground up. I need a straightforward solution, stripped of all the geeky jargon.

BTW, I'm a GIS geek myself, have been for 15+ years.

Anyway. Hoping somebody out there knows how to do a simple wireless set up and can tell me.

Thanks!

---

### Post by Anisoropos on 2006-11-01
Dude relax... 

ESSID is the name of your network... 
Say u are home and u have a setup a wireless network under the name BARBIE then that's the name u should put there. the password is whatever password you have put to your network but I guess you haven't... Say you r at work now... network name KEN ... u need to switch to that network and if it needs a password then you have to ask your system administrator. In the case no password is used there might be a possibility of using MACaddress ... that is ...if you type ifconfig on a terminal u see something like this 
HWaddr: XX:XX:XX:XX:XX:XX

In that case your administator will have to put this address on the access list...

As for this question... 
...Is there an easy way to get Ubuntu to just do the work - find the network by itself, and then connect to it, the way Windows can?..

Who knows! If you are lucky and your wireless card is compatible then it shouls work out-of-the-box (e.g. my ASUS WL167g using ralink chipset) otherwise u might need to use ndswrapper for which I am not an expert...sorry.
Please bear in mind thought that I use UBUNTU Dapper and not Edgy and to be honest I don't know the differences...but in principle that's the answer... try it if it doesn't work try the forum again (but BE specific because believe not a lot of ppl will help in general questions)

Enjoy!
Ani

---

### Post by thegitksan on 2006-11-01
Hm. Okay, I understand better now. And thanks for the reply.

This network is an unsecured wireless. My work PC is wired into a local LAN, with a domain name. When I used the Windows, I didn't have to log on. Does Ubtuntu require a logon? 

I might try to re-install from scratch, this time with the laptop within wireless range. The installation software WAS searching for a network. I have a feeling that if I had let it do its thing while in range, I might have seen a fully functioning wireless set up. The OS definitely knows the wireless card is installed.

I know the MAC address bit too. I will try this before trying re-installing.

Thanks for your reply. And if it works, then perhaps I mgith enjoy.

---

### Post by matthewstory on 2006-11-01
you can handle this one of many ways man . . . network-manager, in the top right tray, will help you with this, you can select your WESSID from the drop down list that's there, and if there is no key,just keep it as ASCII and don't type anything in, select DHCP and hit OK, this should work.  If you want to change this to the default network Ubuntu connects to at startup, you'll have to tweak the /etc/network/interfaces file by hand . . . you can also use this to set up your connection, if you prefer:

sudo ifdown ath0

or whatever your wireless device is called.

to set up wireless in /etc/network/interfaces, the section will look like this:


auto ath0
iface ath0 inet dhcp
wireless-mode managed
wireless-essid <your network name>

then

sudo ifup ath0

hope this helps

---

### Post by thegitksan on 2006-11-06
Okay, I tried that. I was actually able to figure out the ESSID for our office access. Turns out it is linksys, the name of the makers of the USB wireless our office uses. Found the network manager at top right (thanks!) and went through that one too. We don't use a password (WEP)to logon. We do use DHCP. The whole thing seemed to be configuring the network, and then it still didn't work. 

I appreciate your taking the time to try stuff out. I will print off the sample instructions you typed above and see if that helps some.

Tried connecting the USB wireless from one of our office PCs and it did not recognise it. I think maybe our office setup is somewhat complex, in that we have both an intranet as well as an external internet access. We also have proxy walls.

I might try connecting up somewhere else, where I don't have all this extra stuff complicating things.

I don't actually need to connect to the intranet, just to get to the internet access.

Anyway, thanks for your kindness and suggestions. I'll keep whacking away at it until I figure something out.

---

