---
title: "Neeed Ubuntu help fast"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by tom24 on 2009-12-23
Hi all, I really want to get to know and use this fabulous looking operating system, but I am having problems. I have purchased an upgraded desktop with Ubuntu for my youngest lad(not sure what one yet). Ubuntu is the only operating system on the hard drive, as I was told a fresh install had been done.
 
My problem is that I have removed the EDUP wireless card from his old computer running XP, and where windows would normally just find and install the software, in Ubuntu, I do not know how to do it. I have the little cd with the drivers on, but cannot open them in Ubuntu obviously.
 
Can any one please help me to get his computer on the internet through help with installing the drivers needed for the EDUP wireless card to work with Ubuntu. I only have 1 day before he looks forward to a faster pc to play all his games.
 
Once I am on the internet on that pc I can slowly learn more, (I am on a friends pc at the moment).
 
Thanks in advance for any help offered, and a very Merry Christmas to all on the Ubuntu forums. Tom.

---

### Post by Geoff918 on 2009-12-23
You can plug in the card, and then run the following:

lscpi -v

will tell you what kind of hardware it is specifically.

There are hardware specific and networking and wireless specific forums, too. You may find some individuals with more experience with this specific issue there. :)

---

### Post by anewguy on 2009-12-23
Is this a PCI wireless card, or PCMCIA, or USB?

With the card in, please do the following and post back the results:

(1) click on applications/accessories/terminal

(2) type:

lspci <press enter>


Also post back whatever you know about the wireless card - make, model, etc., as this is very important in looking for drivers.

If you have the Windows CD with the wireless drivers on it, search that CD and see if you find files that have .sys or .inf extensions and if so post back the entire file name(s).  If worse comes to worse, we should be able to use those and a utility called ndiswrapper to get it going.

Also, check under system/administration/hardware drivers and see if a restricted driver shows for it.  If so, and if it's not enabled, try enabling it (don't know if it's going to want to download something then or not).

If possible, while doing this work, connect the PC directly to the wireless router via hard wire.

Thanks
Dave :)

---

### Post by tom24 on 2009-12-23
Thanks for the quick reply Geoff. Will try your advice, and stick around here to see what else pops up.

---

### Post by pizza-is-good on 2009-12-23
OK, once you put in the new wireless card, and if like you said nothing works, try the following things:

Go to System >> Administration >> Hardware drivers.
It should come up with a driver for that wireless card. Whether yes or no, try the following

On your top menu bar, right click on your network icon. Make sure that 'Enable Wireless' is checked.

Let us know how that goes.

~pizza

---

### Post by tom24 on 2009-12-23
Thanks ANEWGUY, will do that and get back in ten minutes or so

---

### Post by ubername on 2009-12-23
You could try looking through some of this:
[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=EDUP+wireless+card+&sa=Search&siteurl=crunchbang.org/ubuntu-search-engine/](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=EDUP+wireless+card+&sa=Search&siteurl=crunchbang.org/ubuntu-search-engine/)

but I have another concern. You say your son is looking forward to playing games on his faster PC. Unfortunately windows games do not just 'work' on Ubuntu - you will have to investigate wine :[http://www.winehq.org/](http://www.winehq.org/)


:)my 500th post:)

---

### Post by t0p on 2009-12-23
Fit the wireless card,  reboot, then click on the network manager icon (probably in the top right hand corner of the screen, looks like 2 computer monitors).  What happens?

You said that your son is looking forward to a faster pc to play games on.  Are you talking about the Ubuntu computer?  If so, check that his games will work on it.  Windows games will not usually run on Ubuntu - Ubuntu and Windows are completely different operating systems.  It would be a shame if you give him the machine on Christmas morning and his games won't work.

---

### Post by pizza-is-good on 2009-12-23
> **ubername said:**
> You could try looking through some of this:
[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=EDUP+wireless+card+&sa=Search&siteurl=crunchbang.org/ubuntu-search-engine/](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=EDUP+wireless+card+&sa=Search&siteurl=crunchbang.org/ubuntu-search-engine/)

but I have another concern. You say your son is looking forward to playing games on his faster PC. Unfortunately windows games do not just 'work' on Ubuntu - you will have to investigate wine :[http://www.winehq.org/](http://www.winehq.org/)

Yeah, good point!

You could also try PlayOnLinux. It is a specific 'type' of WINE that is oriented towards games. Your Ubuntu software center has it. Or you could always ```
sudo apt-get install playonlinux
``` in your terminal.

---

### Post by Geoff918 on 2009-12-23
> **t0p said:**
> Fit the wireless card,  reboot, then click on the network manager icon (probably in the top right hand corner of the screen, looks like 2 computer monitors).  What happens?

You said that your son is looking forward to a faster pc to play games on.  Are you talking about the Ubuntu computer?  If so, check that his games will work on it.  Windows games will not usually run on Ubuntu - Ubuntu and Windows are completely different operating systems.  It would be a shame if you give him the machine on Christmas morning and his games won't work.

It's not that difficult to get things going with the use of the forums and google, though. And, in the end, his son will be richer because he'll *actually* understand computers having worked with Linux rather than just be able to point and click and read off some jargon stack dump in Windows. Am I right?

---

### Post by t0p on 2009-12-23
> **pizza-is-good said:**
> You could also try PlayOnLinux. It is a specific 'type' of WINE that is oriented towards games. Your Ubuntu software center has it. Or you could always ```
sudo apt-get install playonlinux
``` in your terminal.

**Applications > Accessories > Terminal**

---

### Post by howefield on 2009-12-23
> **Geoff918 said:**
> Am I right?

Probably not    ;)

He might just point and click with Ubuntu...

---

### Post by Geoff918 on 2009-12-23
> **howefield said:**
> Probably not    ;)

He might just point and click with Ubuntu...

Perhaps, but he stands a good chance of learning quite a bit about networking, security, and the like.

---

### Post by tom24 on 2009-12-23
I have just tried all the suggestions, and here is what I found.
 
Ispci:Command not found. Wired network Intel ethernet pro disconnected. Wireless networking is enabled in tick box.
In hardware: No proprietary drivers in use oin this system.

---

### Post by pizza-is-good on 2009-12-23
> **t0p said:**
> **Applications > Accessories > Terminal**

Yeah, sorry, I should have put that in there too.

Or Alt+F2 and type 'terminal'....

---

### Post by tom24 on 2009-12-23
I hope to get to know about the wine system. He wants to play sims 3

---

### Post by pizza-is-good on 2009-12-23
> **tom24 said:**
> I have just tried all the suggestions, and here is what I found.
 
Ispci:Command not found. Wired network Intel ethernet pro disconnected. Wireless networking is enabled in tick box.
In hardware: No proprietary drivers in use oin this system.

I think that he meant LSPCI, all in lowercase letters....

---

### Post by LowSky on 2009-12-23
> **tom24 said:**
> I have just tried all the suggestions, and here is what I found.
 
Ispci:Command not found. Wired network Intel ethernet pro disconnected. Wireless networking is enabled in tick box.
In hardware: No proprietary drivers in use oin this system.
the command is ```
lspci 
```as in LSPCI

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> I have just tried all the suggestions, and here is what I found.
 
Ispci:Command not found. Wired network Intel ethernet pro disconnected. Wireless networking is enabled in tick box.
In hardware: No proprietary drivers in use oin this system.

Time to get more aggressive:

Here are a few more commands to try:

sudo lsusb

and if that fails:

sudo lshw -html >> hardware.html

The first will list USB hardware. The second will list all hardware in use on the system and output it in a nice HTML file which you can click and scroll through.

If it's not listed there, the next question would be if the hardware itself is making contact. I assume you would have cold booted (turned the machine from off to on) after the physical installation of the machine, so it should be picking it up.

My other assumption is that the IRQs and all are set by software means. It's been a lot of years since I've had to change jumpers. :)

---

### Post by pizza-is-good on 2009-12-23
> **tom24 said:**
> I hope to get to know about the wine system. He wants to play sims 3

playonlinux has something for sims 3. It says that it has some stability issues...

---

### Post by ubername on 2009-12-23
> **tom24 said:**
> I hope to get to know about the wine system. He wants to play sims 3


[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732)

He should be able to do that, then.

---

### Post by anewguy on 2009-12-23
However......let's try to work on 1 thing at a time.  You wanted to get wireless working.  Yes, the command I posted is "L" (lowercase) spci - it will list the PCI devices on your system.  Since this is a desktop, I'm going to assume it's PCI since you said "card".

Please follow my original post and post the information back here so we can go from there.  Remember - it's lspci (lowercase "L").  :)


Dave :)

---

### Post by tom24 on 2009-12-23
I have used the command lspci, and this is what it has foundm The wireless card has an EDUP set up dis, but in the found list is: Network Controller, Texas Instruments ACX 111 54mps Wireless interface. Not sure if that is the EDUP card. I have put our wireless ssid and security settings in to the network details, but still not connected, no screens as yet.

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> I have used the command lspci, and this is what it has foundm The wireless card has an EDUP set up dis, but in the found list is: Network Controller, Texas Instruments ACX 111 54mps Wireless interface. Not sure if that is the EDUP card. I have put our wireless ssid and security settings in to the network details, but still not connected, no screens as yet.

That should be it. You probably won't have any other wireless cards.

You might want to now try the Hardware drivers post info from above at this time.

EDIT:

Here's a link I found. Seems this hardware is less than open-source.

[http://sourceforge.net/projects/acx100/](http://sourceforge.net/projects/acx100/)

EDIT 2:

[http://elwoodicious.com/2006/08/22/ubuntu-and-texas-instruments-acx-111-chipset/](http://elwoodicious.com/2006/08/22/ubuntu-and-texas-instruments-acx-111-chipset/)

Seems this guy has a decent guide. And it links to a further link here at the forums for making the hardware work in Ubuntu. (Our forums are one of our great strengths.)

---

### Post by anewguy on 2009-12-23
So if you check in network manager it does show wireless networks available?

The card can/will show in lspci without necessarily actually working.  The OS can know about the card (such as shown in lspci) but not know how to work with the card (the driver).

If you do:

lspci -v <press enter>

What does it show under "modules" or "kernel modules" for the wireless card?

dave :)

EDIT:  Please also check the CD for the .inf and .sys files, as we could use ndiswrapper yet if needed.

---

### Post by Geoff918 on 2009-12-23
> **anewguy said:**
> So if you check in network manager it does show wireless networks available?

The card can/will show in lspci without necessarily actually working.  The OS can know about the card (such as shown in lspci) but not know how to work with the card (the driver).

If you do:

lspci -v <press enter>

What does it show under "modules" or "kernel modules" for the wireless card?

dave :)

EDIT:  Please also check the CD for the .inf and .sys files, as we could use ndiswrapper yet if needed.

Seems he'll be needing ndiswrapper and a driver from the CD or from the manufacturer's website.

It may also help then to post the output of the following command:

uname -a

(We're getting closer!)

---

### Post by tom24 on 2009-12-23
Kernel in lspci -v: Showing the texas instruments wireless interface. Subsystem Z-com. Under capabilities:acess denied

---

### Post by tom24 on 2009-12-23
Uname -a command:
LINUX USER DESKTOP 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14.04.26 UTC 2009 i686GNU/Linux

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> Kernel in lspci -v: Showing the texas instruments wireless interface. Subsystem Z-com. Under capabilities:acess denied

Ah, yes. Group error. Now trying to remember how to do this in Ubuntu.

Unfortunately, I'm away from my actual system.

I think, System -> Administration -> Users and Groups

You will need to add wireless capacity to the root user and your user. Might be called wl

If anyone has more specific information, or can correct me, please do.

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> Uname -a command:
LINUX USER DESKTOP 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14.04.26 UTC 2009 i686GNU/Linux

You're running 32-bit. Good to know for when we install the appropriate driver(s). Thanks! :)

---

### Post by Geoff918 on 2009-12-23
Another way to take this is a complete reinstall. As long as you have a flash drive or a disc burner and a blank CD somewhere you can always start from scratch. That's one of the great things about Ubuntu and Linux in general--it's free and open-source. :)

You don't need to call MIcrosoft and have them re-approve your install. (Been there, done that. Which is part of why I use Linux-based systems now--and security is the clincher).

---

### Post by tom24 on 2009-12-23
Thanks, just done the root user wireless connection enable, and rebooting to see if that works. Have been offered access to a usb with 9.10 on it to reinstall if neccesary. Is that advisable if nothing elase works?.

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> Thanks, just done the root user wireless connection enable, and rebooting to see if that works. Have been offered access to a usb with 9.10 on it to reinstall if neccesary. Is that advisable if nothing elase works?.

It may not be necessary. But seeing as it seems a fresh install already, you wouldn't be losing any information that you've added.

It's just a thought because while Linux is pretty easy to administer. Rather than getting into config files all over the place the original install may be able to just set it up and run out of the box.

At the least it may be a good thing to use that to boot into a "LiveCD" session by selecting "[Start Ubuntu With No Change To My System]" If the hardware is detected and works from there, that's definitely the easiest way to get it done. Based on what I've read regarding your hardware it may not quite have the drivers to do what it needs, anyway. Worth a shot, anyway.

---

### Post by tom24 on 2009-12-23
Thanks to all of you for all your help. I am off to work soon, so might not get the time to constantly check posts, so in the meantime, can anyone advise on the best (and most reasonably priced) wireless cards to use with Ubuntu, thanks again, Tom.

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> Thanks to all of you for all your help. I am off to work soon, so might not get the time to constantly check posts, so in the meantime, can anyone advise on the best (and most reasonably priced) wireless cards to use with Ubuntu, thanks again, Tom.

You should be fine with that card. It just might take a small amount of tweaking. We can get you through if you'd like.

---

### Post by tom24 on 2009-12-23
By the way, in the brief hour I have been looking at this system, they can shove Windows/xp/vista etc where the sun don't shine.

---

### Post by tom24 on 2009-12-23
Would appreciate it, thanks

---

### Post by anewguy on 2009-12-23
To prepare for using ndiswrapper, put your LiveCD in the drive, then "explore" it using "places".  You want to navigate to the /pool/main/n (or maybe it's /main/pool/n -> don't remember off the top of my head).  There you will find 2 folders - 1 for ndiswrapper and 1 for ndisgtk.  Go to each of these folders and click the files there to install them.

This will install ndiswrapper, a tool that allows using Windows wireless drivers in Linux, and ndisgtk, a GUI'd front-end to ndiswrapper to make things easy to do.

Please also let us know:  

(1) Again, any files on the CD of .inf or .sys type.  Usually the manufacturers place these things in a folder called "drivers".

(2) Did you install 32-bit (e.g. "normal") Ubuntu, or did you install the 64-bit version?

While I can't promise we can get it working, I am not a novice at setting up the drivers for wireless, so we *should* be able to get it working.

Dave :)

---

### Post by anewguy on 2009-12-23
> **Geoff918 said:**
> Seems he'll be needing ndiswrapper and a driver from the CD or from the manufacturer's website.

Please see my posts??????

Dave :)

---

### Post by Geoff918 on 2009-12-23
> **tom24 said:**
> Would appreciate it, thanks

You've got it. We'll be here when you get back. (Perhaps not I, but someone. I'll keep an eye on it. I'm on the other side of the pond, so the time difference may be ever so slightly tricky).

---

### Post by anewguy on 2009-12-23
If needed, we can also try one of the drivers on this link (including Linux ones):

[http://www.modem-help.co.uk/TI/chipset.families/ACX111-11abg-WLAN-Controller.html?drivers=1](http://www.modem-help.co.uk/TI/chipset.families/ACX111-11abg-WLAN-Controller.html?drivers=1)

But for now, I'd also like one other little piece of information about the card when you can:

do:

lspci <press enter>

again, and copy back the entire line for your wireless card (need everything on that line - the manufacturer id and product id, etc.)

We can work on the ndiswrapper stuff when you want to.  I'm also in the states, but I'm usually up *real* late so I'll check back to you then.

Dave :)

---

### Post by tom24 on 2009-12-24
lspci:
O5:04.0 Network Controller. Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by tom24 on 2009-12-24
Bumping this as still need help

---

### Post by Barriehie on 2009-12-24
> **tom24 said:**
> Bumping this as still need help

Here for moral support :)   I'm sure these people will get  you going!

Barrie

---

### Post by tom24 on 2009-12-24
Thanks Barrie, really want to get my head around this system.

---

### Post by Barriehie on 2009-12-24
> **tom24 said:**
> Thanks Barrie, really want to get my head around this system.

You will and it'll be a good thing!

Barrie

---

### Post by anewguy on 2009-12-24
Sorry not to get back to you sooner!  We are having a huge snow storm and I've been out doing the driveway and sidewalk, and since I have a bad back I needed to lay down for a while.

Can you tell me the contents of the driver CD?  If you have already loaded ndiswrapper and ndisgtk as mentioned in my previous post, we shouldn't be that far away as soon as I see what's on your driver CD.

Thanks!

Dave :)

---

### Post by tom24 on 2009-12-24
Thanks for all your help, and as it's soon Christmas day here , Merry Christmas. On the EDUP cd are,amongst a few others, these files:
 
FwRad16bin, Fwrad17bin, fwrad19bin. t1130_9x.sys, tii30_XP.sys. TNET1130.INF
Cant see any others, but I am sure the N files were there earlier

---

### Post by anewguy on 2009-12-24
Okay, here's what I'd like you to do:

(1) copy any .sys and .inf files from the CD to your Ubuntu desktop

(2) start ndisgtk  -I honestly don't remember if there's a menu entry - you can just open a terminal window again and type:

sudo ndisgtk <press enter>

This will start up ndisgtk - the Gui'd front end to ndiswrapper.  When it starts up you would select "Install New Driver".  It will then come up with a window asking you to select the "Inf" file - point this to the .inf file from the driver CD that you put on your desktop.

It should install everything then, and *hopefully* blacklist anything that needs to be blacklisted.

Although not necessary, I would at this point restart my PC.  After it starts up check the network manager on your top bar and see if wireless networks are detected.  I saw a few comments about the ACX111 and not getting full speed with some drivers, but I think using the drivers that came on the CD should avoid that.

Give that all a try, then let me know how things went and we can try to debug if needed.

Again, sorry so late!

Dave :)

---

### Post by tom24 on 2009-12-24
I have tried that, but it takes the commands, but no further action. Wireless card still not seen in top tray. Thank you very much for trying. It's very late here, and bed calls so will have another go over the next few days. Thanks again and goodnight/day.

---

### Post by anewguy on 2009-12-24
I'm so sorry I wasn't able to get back to you earlier so we could have had this thing licked!

I hope you have a great holiday!

Dave :)

---

### Post by anewguy on 2009-12-25
When you feel like trying some more again, please do the following and then post the output back here:

In a terminal window:

sudo ndiswrapper -l <press enter) That's a lower case "L" - stands for list.

Did ndisgtk give you any error messages or warnings when you tried adding the driver?


Dave :)

---

