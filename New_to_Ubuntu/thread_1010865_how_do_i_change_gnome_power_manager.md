---
title: "how do i change gnome power manager"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by chipppy on 2008-12-14
Hello I am a newbie
I have an older ASUS unit with a 2700+ mobile CPU that I have loaded Ubuntu 8.10 onto to start learning about linux
My problem is the computer is really slow. I tried playing 'supertuxkart' and the frame rate is so sloooooow eg 0.9fps.  I am assuming that it is a reduced CPU issue

I noticed reading through the help for Gnome Power Management that there should be a button to change the speed of the CPU when it is on battery.

I checked my preference screen and that button was not available. I read through the help again and it mentioned that the gconf policy keys may be disabled by the system admistrator and as such some options may be hidden.

I am a newbie to Linux and this whole command line bit. I started the 'terminal' and had a go a gconfd-2 but nothing happen. I logged in a root and tried again but still nothing.

I would like to get the CPU speed button onto Gnome Power Manager so that I can see what its setting are and see if this help me out but I dont have a clue how to do this.

Does anyone know where I can get a step by step to walk me through this process. 

I am at the 'how do I change directories' level so nothing to advanced please

Cheers
chipppy

---

### Post by Kobalt on 2008-12-14
Did you try to add the CPU frequency applet to one of your Gnome panels? Right click on your panel and select *Add to the panel...*
Select the CPU frequency scaling applet and add it where you want.

After this you may need to set it to run as root in order to control you CPU frequency. To do so, open a Terminal and enter the following command line :
```
sudo dpkg-reconfigure gnome-applets
```
It will ask you the CPU feq. applet should be run as root, select yes and you're done.

---

### Post by sdennie on 2008-12-14
This problem is probably not related to the CPU frequency governor.  Are you running compiz (Desktop effects).  If so, turn it off before trying to play a game.  Also, what are the specs of your machine (specifically graphics card and memory).  It's possible that your machine isn't powerful enough to play that game.

---

### Post by chipppy on 2008-12-14
Ok tried a couple of things here and had limited success.
Tried Kobalts idea and that gave me more information but didnt fix the issue.
With the applet running I can now see that my CPU is running in the ondemand mode and at min frequency.  The is 6 frequencies available 535mHz-equal steps upto-2.01GHz.  This is strange as the laptop is an ASUS L3000D with an AMD athlon XP-M 2700+ so the top speed should be 2.7GHz.
Anyway I set the CPU to Performance and the speed went to 2.01GHz and stayed there.  Ran 'Supertuxkart' again and still the same problem.  Set the CPU to ondemand and tried again and the SPU speed increased from 535MHz to 2.01GHz when I started 'Supertuxkart'.
So I think is probalby correct in that it is not a CPU speed issue, although there is the issue of only 2.01GHz and not the full 2.7GHz.
I found the System/Admistration/Hardware Drivers and ran that.  There is no propietary driver in use.  The laptop is an old one that I havent used in years and I am not sure what its specifications are other then those on the stickers.
Using the System/Admistration/ubuntu hardeware testing I found a SI7012 sound card that didnt make any soiund during the testing but works fine normally and plays music fine, screen resoultion is 1024X768 @60Hz, the video test looks good nothing strange happened and all the bars were there, the mouse works fine, [SiS] SiS9000PCI fast etherent(rev 90) works fine, internet works, and typing works.  Dont know if any of that helps but I thought it might give some insite

How do I search to see what hardware has been recongised by Ubuntu?

And also thatnks for tha help

Cheers
chipppy

---

### Post by chipppy on 2008-12-15
OK I am still doing more research and found something about AMD used to put speed numbers on it CPU that were the equilivant Intel speed and not the actual AMD speed. 
Following on from this I found out about entering the BIOS and looked into that.  The BIOS says that the CPU frequency is 1995MHZ so this might explain the 2.01GHZ issue.
I still havent been able to find out about how to see what Ubuntu recongises in the hardware stakes.
Anyone have an idea of how to see what hardware is in my Laptop.

Cheers
chipppy

---

### Post by Francewhoa on 2009-01-31
Same here with Ubuntu 8.04 and Toshiba A8 laptop. [This post]("http://ubuntuforums.org/showpost.php?p=6654274&postcount=8") worked for me.

---

