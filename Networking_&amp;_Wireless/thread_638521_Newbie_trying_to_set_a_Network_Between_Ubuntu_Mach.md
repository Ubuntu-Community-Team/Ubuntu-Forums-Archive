---
title: "Newbie trying to set a Network Between Ubuntu Machine and XP machine (losing hope)"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by podness on 2007-12-12
Hello everyone here on Ubuntu forums, I have been looking for days now for a solution to my problem and I just can't seem to find any straight answers out there. I'm a newbie but I have some knowledge of how things work in Ubuntu and Unix in general.

My frustration is that on Windows XP OS, all I had to do to set up a network is just go to the wizard,
tell it that *this* is the main PC in the network from which other computers on the network connect through to the internet (Main PC1 is connected to the internet with PPPOE modem, it has 2 LAN cards. eth0 is for the internet connection and the eth1 is for the other Win XP machine on the netwrok) and tell the wizard on the other XP machine (The one that connects to the internet through the LAN, PC2 to PC1) that it connects to the internet through the network. And that's it, I would have both File Share and Internet Connection set in seconds.

But now I decided that I want something fresh to my machine, I decided to go for Ubuntu 7.10 gusty.
To connect my machine to the internet, really all I need to do is to type this very simple line in Terminal "sudo pppoeconf" and follow the short "Wizard". How ever I couldn't set a network. 

I don't know how the network thing works here at all.. I tried out to find any information about it in the Help documents of Ubuntu and best thing I could get is to deal out with some feature called "Network Manager", yet it doesn't say where this feature is nor its Terminal command, I have no idea where is that Network manager is however it IS installed on the system.

I tried the ifdown eth1 and ifup eth1 method which also was suggested but the results were negative. I just have no clue.. What I am trying to accomplice is this:

1. Set up a network between 2 computers (old fashion Wir[B]ed[/B), NOT wireless! Both machines have LAN cards)
2. Somehow tell the Ubuntu machine to allow the XP machine on the network to connection  to the internet from it 
3. Allow file share

Please help me guys, It would be very much appreciated! -- lol If I could I would even pay you, this thing really is destroying my experience with Ubuntu

(I won't get to the next issue with my ATI video card, failing to install the latest driver since the restricted drivers management shows me that it doesn't actually **use**(red light) my ATI video card accelerator; for now ><)

---

### Post by viking777 on 2007-12-12
If it is any consolation to you, when I first installed ubuntu it was about 6 months before I got networking to work right, and by that time I had made so many changes to so many files that I still don't know how I did it. Luckily networking isn't that important to me.

When it comes to networking I have had much better luck with Linux Mint where it just seems to work, I can't explain the difference because Mint is Ubuntu based anyway so should behave much the same.

You will just have to keep doing as I did and bash away at the literally thousands of posts on the subject both here and on the net as a whole until you find one that works for you, eventually you will get there. 

I know what you are going to say next, "It should just work" and you are right. It is one of my hobby horses with Linux that if less time was spent on worthless eye candy like Compiz, and more time was spent on things that really matter like networking, Linux as a whole would benefit.

---

### Post by schmildo on 2007-12-12
OK we'll leave the ATI stuff till last. (I had issues also, but got it going)

I like a good description, you've done well, I just wish we could draw pictures with this forum...

When you said you connect to the net using a pppoe modem do you mean that you use PPPoE inside your home network? or do you mean that your router uses PPPoE between itself and your internet service provider?

I know it might be a pain, but i'd suggest simplifying the situation first, by having the linux machine plugged directly into the router and ignoring the windows machine for a bit, it's important we know what works and what doesn't.

I'm currently trying to help a bloke out here: [http://ubuntuforums.org/showthread.php?t=634826](http://ubuntuforums.org/showthread.php?t=634826) with his connection, have a peek, I pretty much going to give you the same advice.

Once you have it working directly into the router then plug it back up teh way you want it, and change the default gateway to the windows machine's IP address and you should be ready.

But...

If you windows machine really is using PPPoE between itself and the router, that will complicate things...

Regardless, the first thing we need to know more about is your PPPoE setup. LIke, have you had to go into windows and tell it that you are using PPPoE?

also have a look at that link i posted and run those commands and post the output here for us to read.

I'll post this and get you some info about the ATI stuff, hehe isn't linux fun! :) (The only reason I'm sticking with it is because I can't understand why other people bother with it, oh, and becase I couldn't install windows XP onto my USB stick after 4 of my harddrives died in some freak accident.)

---

### Post by schmildo on 2007-12-12
These two commands seemed to be thrown around alot with regard to people having issues with ATI drivers:

**tim@lister:~$** [COLOR="DarkSlateBlue"]fglrxinfo[/COLOR]
[COLOR="Sienna"]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)[/COLOR]

**tim@lister:~$** [COLOR="DarkSlateBlue"]glxinfo |grep direct[/COLOR]
[COLOR="Sienna"]Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)[/COLOR]

LOL, for some reason my direct rendering is off, I have no idea what that means, but I think that's bad, it's supposed to be on i'm told. But my fancy pancy desktop effects are working so I dunno.

I tried nearly everything to get my video drivers working properly, but I think this bit solved it all for me:

[COLOR="DarkSlateBlue"]aticonfig --initial --input=/etc/X11/xorg.conf[/COLOR]


My problem was when I ran fglxrinfo, i kept getting the mesa drivers appearing, and then I'd go change the xorg.conf file and then I'd reboot, and it'd change back again. But the aticonfig command seemed to do the trick.

Amazingly I have a green dot 'and' a tick. (I got the dot but not the tick when I did it)

Either way give us the output of those two commands and we'll have a look-see.

---

### Post by Sagadon on 2007-12-12
Quick question:  You have a network with an XP box and a Linux box.  Do you have a router?  A Hub?  A firewall?  If you're connecting NIC to NIC... you would need a special cable - a cross-over cable. Normally with the routers, the connection marked 'Internet' is interally crossed.

It sounds like you know enough about computers to have set this up right.  

As far as the network manager goes, I believe it is a daemon running that you can control through a few methods:
1) ifup / ifdown / /etc/init.d/networking
2) editing /etc/ files and running '/etc/init.d/networking restart'
3) Under System/Administration/Networking in the main menu there's a UI which edits /etc/ files for you

Here's the files I've seen referenced for editing:
  /etc/resolv.conf
  /etc/network/interfaces

I'm trying to solve my own problem, so I'm no expert, but hopefully someone with more knowledge will correct me!

---

### Post by viking777 on 2007-12-12
OK FWIW I will tell you how I setup my network in Hardy recently. I would stress from the outset that I am not a networking expert so I have no real idea which of these measures made the difference to my network, some of them may be completely unnecessary and I have absolutely no idea if they will make any difference to yours. In all probability they wont. 

1) Install Samba. Ubuntu doesn't install the full version of Samba by default, so go into synaptic, search for the package 'samba' then download and install it.

2)Using a root mode text editor, open the file /etc/samba/smb.conf (back it up first) and first look for the line :

# Change this to the workgroup/NT-domain name your Samba server will part of


In my file the workgroup name was present but commented out and the netbios name was not present at all.

it should look something like:

workgroup = mshome


netbios name = computername

Obviously the workgroup must be identical on all the networked machines and the netbios name must be individual for each machine.

Then go and look for a line like this:

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = smbpasswd

obey pam restrictions = no

On my file the passdb backend was set to something else and the 'pam restrictions' were set to yes so amend accordingly.

Finally go to the end of your file where the shared folders are defined (I am assuming that you have already selected some folders to share) and add a line similar to this at the end of the each network share:

hosts allow = 10.0.0.1, 10.0.0.2, 10.0.0.3 etc

Obviously you set this to correspond with the dns addresses that are pertinent to your network.

After you have done all that you reboot, find that your network still doesn't work and start cursing me:lolflag:

Then you reinstall the backup smb.conf file and start again.

Good luck.

---

### Post by podness on 2007-12-20
First of all thank you for all your replies! I'm sorry It took me a long time to post a reply, I had been busy for awhile.. But I did read everything you posted.

Okay..let's first answer the questions:

on Ubuntu, my internet worked like magic. The PPPoE modem is connected to my Ubuntu machine, the PPPoE modem is connected to the LAN plug, eth0 (the onboard LAN card). Last time I posted here, I was surfing from my Ubuntu machine.

Before I decided to try out linux, I had both machines running win XP. I had my network set fine. I could connect from my current machine to the internet and the other machine on my network (connected to the second LAN connection, the actually LAN CARD on my current machine, eth1 - as I said before, old fashion WIRED connection and NOT the Wireless) in the living room.  Here is a diagram:

[IMG]http://img249.imageshack.us/img249/4365/diagramru1.gif[/IMG]

But now that my internet connection here on Linux is fine, how do I get the other XP machine on the network to connect to the internet? I have little knowledge about it and I only could make it work before when I was running XP on the main (current) PC by using Windows Xp's "Home Network Wizard". 

When people use definitions like "gateway ip / mask address/DNS/etc." it confuses me because I know very little on what which means, however I can assure you that if was explained I would get it fast since I understand the world of computers (I also googled for information but fail to find the "right definition" to actually google for)

However I decided to try out the Mint Linux 4.0 that was "recommended" by viking777 here. It seems that Mint Linux (Ubuntu Based - latest version based on Ubuntu 7.10) really has it all together. I didn't have to do anything just to find out I can access files on the living room's computer, without needing to install my network. 

Right now at the moment I am using the Mint Linux instead of Ubuntu. It is obvious right now that the network is working and functioning just fine between the XP machine and the Mint (Ubuntu) machine. However I still have no clue how do I set the internet on the other network machine to work . The XP machine shows that there is a "problem" with the connection of the network (the yellow triangle with the "!" mark on it -- This shows in the windows machine) however, I can still access files through my Mint machine to the XP machine and do whatever I wish on the other machine.


So there are only 2 questions left:

1. Why am I shown the yellow triangle on the XP machine? I tried to click the option "Fix connection" but it failed

2. Now that there is a network up and running, how do I make the XP machine be able to surf the internet?

P.S -- It also seems that the video card is good and working when I use the ready-to-use "Envy" software on Mint OS to just automatically download & install the latest stable driver to my machine for my ATI video card.

I'm also looking for a good firewall that's easy to maintain. I think I'll go for the firestar firewall, however I wonder if there are any other (better) options out there.

Thank you all very much!

---

### Post by trobbins on 2007-12-20
*1. Why am I shown the yellow triangle on the XP machine? I tried to click the option "Fix connection" but it failed*

Yellow triangle "limited or no connectivity" means your NIC has a physical (wired) connection but does not have a logical (TCP/IP) connection.  You have two choices here.  You can install a dhcp server on your Ubuntu box and it will give your Windows PC an IP.  The other option is to statically set an IP, dns masq, and default gateway on your Windows and Ubuntu box.


2. Now that there is a network up and running, how do I make the XP machine be able to surf the internet?

Short answer is routing. In windows this is called "Internet Connection Sharing" or ICS.  I don't know how Ubuntu addresses this in an easy-to-use way.  Does anyone else?  I personally use a 1.44 megabyte linux distribution (BrazilFW) running on a pentium 75mhz with two NICs as my router.  I connect my modem to it, and then the other nic to a switch, with all my other PCs.

---

### Post by spiderbatdad on 2007-12-20
have you seen this:[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by trobbins on 2007-12-20
This thread looks very promosing for setting up internet connection sharing on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

It's not a fancy GUI, but looks like it works.

---

