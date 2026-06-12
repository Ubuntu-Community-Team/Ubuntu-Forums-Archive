---
title: "installing software off a cd-rom"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Drifting Cowboy on 2010-01-26
Okay, this is my first day of having Ubuntu. In fact, previous to today I have never had anything except Windows aside from running games off floppy disks (the actual floppy ones) in MSDOS years ago. Which I hardly remember doing, anyways. When my version of XP on this computer crashed with rootkits and worms, a tech suggested putting a form of Linux on here explaining to me how much better it was.

So, to my point, I have been on here for the past 7 and a half hours trying to install the router I bought for this computer a couple weeks ago. I was never informed that Ubuntu does not run .exe files until I sat down and tried to run this. So, through all of my google-ing today, all I could find was something telling me to get wine. So I got this activated, and when I run the Setup Assistant using wine it will now bring up the home screen for this. However, once I click anything in the home screen it completely terminates the program.

Everything else I can find for installing programs on Ubuntu, is for installing actual Linux programs available in the add/remove manager, or whatever. Is there any way for me to install this .exe file to setup my network, or am I just going to have to wipe this off and go back to Windows? Any help would be GREATLY appreciated, because after 7 hours of google-ing I am pretty frustrated with this OS at the moment, but not ready to give up on it.

Thanks in advance to any who reply with help.

---

### Post by tom.swartz07 on 2010-01-26
> **Drifting Cowboy said:**
> Okay, this is my first day of having Ubuntu. In fact, previous to today I have never had anything except Windows aside from running games off floppy disks (the actual floppy ones) in MSDOS years ago. Which I hardly remember doing, anyways. When my version of XP on this computer crashed with rootkits and worms, a tech suggested putting a form of Linux on here explaining to me how much better it was.

So, to my point, I have been on here for the past 7 and a half hours trying to install the router I bought for this computer a couple weeks ago. I was never informed that Ubuntu does not run .exe files until I sat down and tried to run this. So, through all of my google-ing today, all I could find was something telling me to get wine. So I got this activated, and when I run the Setup Assistant using wine it will now bring up the home screen for this. However, once I click anything in the home screen it completely terminates the program.

Everything else I can find for installing programs on Ubuntu, is for installing actual Linux programs available in the add/remove manager, or whatever. Is there any way for me to install this .exe file to setup my network, or am I just going to have to wipe this off and go back to Windows? Any help would be GREATLY appreciated, because after 7 hours of google-ing I am pretty frustrated with this OS at the moment, but not ready to give up on it.

Thanks in advance to any who reply with help.

What kind of router is it? 99.9% of them are just plug-and-play, you could edit the settings from a browser.


Heres what I say. Plug in the router, hook it directly to your computer, open a browser and navigate to 192.168.1.1 or 192.168.2.1 and see if the setup page appears


Hope this helps!

---

### Post by tom.swartz07 on 2010-01-26
Let us know what happens- I will certainly try to help!

---

### Post by drzoo2 on 2010-01-27
To answer your question Linux does not natively run a .exe. An exe is a program that was compiled for windows containing system calls strictly for that OS. Wine is a layer that can sit between the exe and Linux to try and translate those calls. While Wine does exist, you should reside the fact that your new Ubuntu system is not windows. If your planning on sticking it out realize that you can no longer go to your local Walmart and pick up a copy of anything to run on it. That said usually there are alternate programs that will do the job. Once you get used to Linux you will find just about any software you used in Windows has an equivalent in Linux. Not all has a replacement but for the typical user skies the limit.

As far as your router, like stated above. I have yet to see a router that doesn't have a web interface. Even when using Windows myself there has never been a reason to use the disk that comes with them. I think they include them just because most people expect some sort of software to install. Something like a router has to be OS independent. The routers documentation should have the default name, password and IP. 

Honestly if it requires software to be ran I would return it. Even if I was strictly a Windows user. It just isn't required.

z

---

### Post by 3rdalbum on 2010-01-27
When I tried to set up someone else's router on their Windows computer, I ran into trouble with the software that was to be used. I called the ISP's help desk, and the first thing they told me was to toss away the setup CD and just use the router's web-based configuration tool.

The address differs from router to router, but when you connect your Ethernet cable to the router your Ubuntu's network manager will connect. Network Manager is one of the little icons on your top panel, toward the right hand side of the panel. Right-click on it and choose "Connection Information". The Ip address given under "Default Route" is the address of your router. Put it into your web browser, like so:

[http://192.168.0.1](http://192.168.0.1)

You'll be asked for your router's username and password - it's usually username of "admin" and password of "admin". Otherwise, check with the router's manual.

---

### Post by egalvan on 2010-01-27
If the router is fairly new (less than four years, say),
it will have the router address, log-in name and password on a label...
almost always located on the bottom.

Some wireless routers even have an encryption key on the label...


Note... for security reasons, the first thhing you should do is change the log-in name and password.
If wi-fi, change the encryption key.

---

### Post by Drifting Cowboy on 2010-01-27
Thanks for the help guys. I went to bed after I made this post last night because my eyes just couldn't take the computer anymore, but as soon as my class is over with this morning I'm going to jump back on and try setting it up off the web.
 
The router I bought is a Belkin N150. There was really no instruction manual with it, just a piece of paper showing the path to hook the router inline with your modem and computer. This is the first time I've tried to set up a network, but since I now on a desktop, laptop, and PS3 I've been getting tired of dragging my modem around the house.
 
But once again, thanks for the help and I will let you guys know what happens when I get home and try this out.

---

### Post by Drifting Cowboy on 2010-01-27
Well, I just called the support number to find out the web location because internet searches turned out obsolete. After speaking with some guy from India I was informed that Belkin does not support Linux because no one there has heard of Linux. (Don't you love talking to someone half way around the world for tech support that you can barely understand) So I don't know.... I guess a word of advice for everyone here is don't buy a Belkin router.

---

### Post by J V on 2010-01-27
Just because the tech support guy is an idiot (and he is, 30% of india uses linux according to an article I read a while back) doesn't mean he can't help you, explain in very simple words that you need the IP for the router...

---

### Post by egalvan on 2010-01-27
> **Drifting Cowboy said:**
> Well, I just called the support number to find out the web location because internet searches turned out obsolete. After speaking with some guy from India I was informed that Belkin does not support Linux because no one there has heard of Linux. (Don't you love talking to someone half way around the world for tech support that you can barely understand) So I don't know.... I guess a word of advice for everyone here is don't buy a Belkin router.

BIG OOPS on my part....SORRY!!!
I always insert the part about...

`**[COLOR="Red"]Don´t tell tech support you are using Linux !![/COLOR]**`

Just tell them you are using Firefox under XP.
Ask them for the router web page address
should be something like...
192.168.0.1
192.168.0.255
192.168.1.1
192.168.1.255
192.168.2.1
etc....

I dug up these pages on the Belkin site...
give them a try....

[http://en-us-support.belkin.com/app/answers/detail/a_id/470/q/routers](http://en-us-support.belkin.com/app/answers/detail/a_id/470/q/routers)

[http://en-us-support.belkin.com/app/answers/detail/a_id/30/q/routers](http://en-us-support.belkin.com/app/answers/detail/a_id/30/q/routers)


DON`T GIVE UP!!
THERE IS NO ACTUAL, REAL REQUIREMENT TO USE MICROSOFT PRODUCTS TO ACCESS ANY STANDARDS-COMPLIANT ROUTER, OR THE INTERNET.
OTHER THAN A DESIRE ON MICROSOFT´S PART TO BE A REQUIREMENT.

---

### Post by tom.swartz07 on 2010-01-27
We have a belkin here. Since its plugged from the modem to the router, the ip is 192.168.2.1

If you just have it plugged right into your connection, it should be ----.1.1

Easiest way ive found is to look at the computer's ip- network connection information- and just pick the first of the set-

Say you look and your computer's ip is 192.168.5.6; the router should be 192.168.5.1

I have a screenie here just in case you need it

Good luck!

---

### Post by Jerry N on 2010-01-27
*"THERE IS NO ACTUAL, REAL REQUIREMENT TO USE MICROSOFT PRODUCTS TO ACCESS ANY STANDARDS-COMPLIANT ROUTER, ...."*

Actually I have run into routers (including mine) that require Internet Explorer to access some of the setup functions, including some of the wireless functions.  Firefox works for MOST things but not all.  The only useful thing on most of the disks that come with routers is the manual.  

Jerry

---

### Post by Drifting Cowboy on 2010-01-27
Just got it set up without removing Ubuntu. THANKS to everyone for the helpful advice. I have no problems using alternate programs to Windows, but I had to get this router I just bought two weeks ago set-up.

I guess people in India really DON'T know what they're talking about :-s Who would have figured?

Anyways, thanks again to everyone.

---

### Post by tom.swartz07 on 2010-01-27
> **Drifting Cowboy said:**
> Just got it set up without removing Ubuntu. THANKS to everyone for the helpful advice. I have no problems using alternate programs to Windows, but I had to get this router I just bought two weeks ago set-up.

I guess people in India really DON'T know what they're talking about :-s Who would have figured?

Anyways, thanks again to everyone.

Sure thing! Im glad you got it all sorted out! :D


Who needs tech support 10,000 miles away when you have us just a few clicks away?! :guitar::wink:

---

