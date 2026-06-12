---
title: "Skype From Synaptic"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by lotusalive on 2010-09-20
Hello out there :)  

I was trying to get my Skype from Synaptic to work, but received this 

Error Msg when registering: 

> P2P connect failed. Please Check your Internet Connection.  

My connection is fine / working.

Suggestions on what else I might look at ? ?

Thank you all so much, in advance.

---

### Post by clive littlewood on 2010-09-20
Hi

I always go to the Skype download site and use the linux link.

This site will always be more up todate and is a simple .deb file.

I have this on 2 machines (10.04) and both work great.

Hope this helps

Clive

---

### Post by lotusalive on 2010-09-23
Thanks for the Reply Clive: 

I went to their site first, Before trying the Syn Pkg, but the Download on their site was for i386 Intrepid, not Jaunty, so GDebi or Archive Mgr would not install it !  I'll check my sign-up with them again, but Skype Intrepid i386 is still thrown in my Trash ! ](*,)](*,)](*,)](*,)

---

### Post by mastablasta on 2010-09-23
go here: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/)
 
Download .deb for ubuntu. it will work.

---

### Post by lotusalive on 2010-09-23
:KSty mastablaster: 
Uninstalled Skype from Syn Pkgs, INstalled Skype from their site, Gdebi worked, since I'd forgotten to uninstall the Syn Pkg, duh...  BUT, I'm STILL getting the Error Msg on my IP Connectivity:

> P2P Connect Failed

I'm more than a little lost here...  Am using using a Router from Netgear for 2 PC's...  Do I have to go to their site to enable P2P ?
Someone please direct me ?  Thanks mucho, in advance.:confused:

---

### Post by mastablasta on 2010-09-23
you probably have something blocked in router (perhaps router firewall?!). you will have to look in router manual on how to let skype connect through the router. Or you can just browse the router setting and see if there is any that would help you let specific prorgamme to go through...
 
I think if you are not using VNC you could (and porbably should) also open ports and also use uPNP on router.
 
edit: yah forgot to add that you should note that doing this will make you small network more vulnerable so you should have some firewall installed on your computer. linux has it on by default i believe, while if you have any Windows maschines in the network you can use one of the free ones such as Comodo or Zone Alarm.

---

### Post by lotusalive on 2010-09-23
ty mastablastA:KS:  cwazy stuff here...  After rebooting with Skype installed, I lost ALL internet connection !  Uninstalled Skype, reboot, still no connection, or access to Syn Pkg Mgr !  Scared: came in on Live Disk, STILL no internet !  Reconfigured Router at Netgear to 'Dynamic' instead of 'Static' IP... Have internet back... Going back to my Desktop Jaunty after this note...  (lol:confused:as to WHY this would happen.  Only thing I can think is that yesterday, trial & error beginner here, installed DHCP from Syn Pkgs, & didn't reboot 'til now...  don't know what I'm doing with it, just wanted to 'see,' as I MUST learn every single 'hard-way' there IS:guitar:  LOL, I guess...  If I get back into Syn Pkgs on my Desktop, should I uninstall 'DHCP' Main Pkg ?  (I think that's what I did, that could have affected my Internet Connection...)  Sorry for all this.

Will look at Firewalls you suggest, although almost all of what you said is way over my head, as I've never heard those terms before...  Haven't used a Firewall with Desktop access since my old Favorite Pkg began failing consistently...  (I have 'friends.')  Thanks a lot, if you can direct me further on this.  Going back to Desktop, I hope.:)

---

### Post by beew on 2010-09-23
I also install Skype from the repo, it is not recording apparently. Also, even though my setting is English, the echo help speaks a language that sounds like German or some Eastern European language, I wonder if anyone has the same experience.

---

### Post by beew on 2010-09-23
Just uninstalled skype from synaptic and installed the .deb package from skype. Still cannot hear my voice in echo-sound test and the guy (yes, it is a guy) in echo still doesn't speak English. Also, the version I installed from Synaptic is actually newer, I am invited to update.

---

### Post by mastablasta on 2010-09-23
> **beew said:**
> Just uninstalled skype from synaptic and installed the .deb package from skype. Still cannot hear my voice in echo-sound test and the guy (yes, it is a guy) in echo still doesn't speak English. Also, the version I installed from Synaptic is actually newer, I am invited to update.
 
what version? 2.1 beta is the latest.
 
Does the mic work in other porgrammes (e.g. sound recorder)?
what kind of output / input do you have set in your sound preferences?
 
> Haven't used a Firewall with Desktop access since my old Favorite Pkg began failing consistently... (I have 'friends.') Thanks a lot, if you can direct me further on this
 
if you only use Linux then you don't really need to mess with firewall i guess. someone else could tell you more here.
 
basically it's a protection wall and there is usually one on router. in order for a programe or computer to go through it you can open a port (doors). different programmes use different doors. so if skype has a closed incomming door or outgoing door then (maybe) it can't work propperly. i am also new to this :) all i know is sometimes you just need to open some doors for things to work.

---

### Post by beew on 2010-09-23
It is version 2.1.0.81 beta, I downloaded it from the skype link here. The one in synaptic is the same but a more recent built (I installed it from a ppa) I haven't got a chance to test the mic yet, I was planning to do that and post a thread here. 

But have you tried the echo sound test? Does the guy speak English? In the windows version it is a girl and she does speak English. In the Linux version a guy greets you with something like "Dobilidan"

---

### Post by mastablasta on 2010-09-23
that's some slavic version then :-) maybe there is some setting in preferences you can change. i dont' think Skype comes in too many languages... i know there is a german one. try fiddle arround with preferences a bit.
 
you also get this if you try to find skype in google by typing in "skype for linux"?!
 
it should be english and i also think it's a woman...

---

### Post by lotusalive on 2010-09-23
Welp, I seem to have lost my Jaunty installation...  I went back into my Desktop, Syn Pkg Mgr actually worked, but Internet Connection STILL did not !  How weird is that ?  On the 2nd re-opening of Syn Pkg Mgr, it was then no longer connected to the internet for repos therefore, not operable !  AND, I cannot access the Netgear Site from my Browser, with Error on Browser: 

> Firefox cannot find server start.ubuntu.com:confused:

I WAS installing servers from the Universe Pkgs. Could I have contracted something unwanted ?  Will someone help me understand WHY I might have lost this installation ? Or PERHAPS reboot it from GRUB somehow ? :confused:

If I'm just stuck, I'd like to know what I did 'overnight' !  It then looks like I'll have to reinstall anew, after one good operable year !  What a drag to lose all the time & s/w I've installed.  Guess I'll upgrade to Karmic, at this point, if that's the case.

P.S. Funny ha,ha, Off Topic: I personally always try to integrate 'both' sexes into my being, spiritually speaking :)

---

### Post by lotusalive on 2010-09-23
Yikes, Tell me this, will you folks ?  Live Disk won't login to Facebook, with Error Msg:

> Firefox can't find the server at login.facebook.com

When I attempt login from my Gmail for Facebook, I get Error Msg

> Service Unavailable - DNS failure
The server is temporarily unable to service your request. Please try again later.

Reference #11.256f1160.1285273585.1e8d3d2b 

What does THAT mean ? ? ?  (I can login to YouTube from Live Disk, & Google is just fine, & so are OTHER Facebook Pages !  It's just MY page at Facebook that I can't access !  LOL !  (struck a high-note, i guess...)

---

### Post by lotusalive on 2010-09-23
If anyone is noticing this Thread, I have removed my Netgear Router, now in direct connection to Modem.  My Jaunty Desktop is STILL inoperable.  Last night [COLOR="DarkOrchid"]**I removed the Syn Pkg 'dhcp-3 server' (as nothing warned me it was NECESSARY to my System, & I thought I'd installed it as a 'trial & error' s/w like I often do...)**[/COLOR], & when I rebooted for the downloaded Skype Pkg Install, I lost Internet Connectivity 'server' on my Desktop, then this morning the Live Disk Internet Connectivity also failed on the Router !

**[COLOR="DarkOrchid"]Is there any program on my Desktop that might help me save my System ?[/COLOR]**  

The Desktop is ALSO telling me that it refuses to recognize ALL 3 of my USB's as vfat, not supported by my System, which has never happened with this installation before now.

Error msgs from Syn Pkg Mgr when I attempt to utilize any repo is basically, Failed to find archive.ubuntu.

---

### Post by mastablasta on 2010-09-24
it seems you managed to somehow corrupt the system?!
 
Also you can't just remove the router and connect directly. usually you need to give your MAC address to ISP (internet service provider). as you usually connect with a password and username to the network.
 
btw you are using cable to connect, right?

---

### Post by lotusalive on 2010-09-24
Yep, corrupted System SOMEHOW.  Am direct from Live Disk to Modem, removed Router for now.  Confusion over installing dchp-3 for SERVERS. I thot it was a higher Version of dchp-client, & stupidly removed dchp-client, that will not now reinstall.  USBs working, saved everything except Films.

> lightening@lightening-desktop:~$ sudo su
[sudo] password for lightening: 
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
root@lightening-desktop:/home/lightening# sudo apt-get install dhcp-client --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dhcp-client
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.1kB of archives.
After this operation, 57.3kB of additional disk space will be used.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe dhcp-client 3.1.1-5ubuntu8.2
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/d/dhcp3/dhcp-client_3.1.1-5ubuntu8.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/d/dhcp3/dhcp-client_3.1.1-5ubuntu8.2_all.deb)  Could not resolve 'security.ubuntu.com'
root@lightening-desktop:/home/lightening# 


I also cannot install packagekit-backend-apt.  Don't know why it wasn't installed in the first place, & I did not remove it.

I'm booting in with Jaunty-19-Generic (Recovery Mode).  Does it matter if I remember which exact repo I was using ?  (It's one of 4, US, Canonical, Duke, or Davis.):confused:  I'd like to save my sytem, if it's possible.:confused:

---

### Post by lotusalive on 2010-09-24
Don't worry about me, Mastablasta, Desktop Environment helped me with this, all I have to do is Manually Set IP, Subnet, Gateway, & DNS Servers. Will try to get ISP to help me have all the addresses.  Thanks a lot.  I set P2P manually this morning, so that should clear me for Skype use. Thanks 
again !:KS

---

### Post by lotusalive on 2010-10-11
Installed Frostwire from Debian Apps, to do the P2P connection.  Will probably work, when I get Adobe Flash to work again...  The new update for Adobe Flash 10.1 in Synaptics,is not working for SOUND !  Neither is the flashplayer.nonfree installer !  :confused:  Use an upgrade Alsa Script ? ? (Found that thread.)  Should I upgrade to Karmic because of this ?

---

