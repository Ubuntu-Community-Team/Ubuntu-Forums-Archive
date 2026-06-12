---
title: "Windows 7 RC installation"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by anchorschmidt on 2009-05-06
I downloaded the RC build of windows 7 and made a separate partition using gparted for it. 
However, when I start the installation, when the drivers are supposed to be loaded in the first step, it tells me that no drivers can be found. I first formatted the partition as a NTFS and then later as unformatted but it didn't work.

---

### Post by Happy_Man on 2009-05-06
And this has... what to do with linux?

---

### Post by anchorschmidt on 2009-05-06
Well I'm trying to dual boot with Ubuntu.

---

### Post by Happy_Man on 2009-05-07
Right, but your problem is that the Windows drivers aren't being picked up by the install disc... right? So, then, this is beyond the scope of this particular subforum. 

Try the Windows subforum.

---

### Post by Herber on 2009-05-07
If you are not opposed to a reinstall of Ubuntu, why not install The Win7 release candidate and then install ubuntu.  I find that the Grub boot mechanism is very good about selecting boot OS.

---

### Post by Niniel on 2009-05-07
The Absolute Beginners forums is for Ubuntu, Linux and Computers. 
So it's not totally wrong to ask this here. Somebody might know.
E.g. my guess would be that there's something wrong with the installation disk.

---

### Post by SunnyRabbiera on 2009-05-07
Well windows has never been that good at autodetect, it only seems that way because when you use that XP or Vista disk you got with your computer its always a tweaked version.
But a pure Vista/XP is much different, Vista is a little better but not by much.

---

### Post by theozzlives on 2009-05-07
Why don't you try a [VirtualBox]("http://www.virtualbox.org/") that's how I did the beta.

---

### Post by bodhi.zazen on 2009-05-07
> **Niniel said:**
> The Absolute Beginners forums is for Ubuntu, Linux and Computers. 
So it's not totally wrong to ask this here. Somebody might know.
E.g. my guess would be that there's something wrong with the installation disk.

Yes , that is true, especially as the community has grown.

We suggest directing Fedora ? => Fedora forums
Arch ? => Arch forums
Debian => Debian forums
Mint => Mint forums

and on ...

Yes, this question is probably best directed at Microsoft or a windows forum.

Just be polite about it is all (not that your post was rude .. ) ;)

---

### Post by SunnyRabbiera on 2009-05-07
> **bodhi.zazen said:**
> Yes , that is true, especially as the community has grown.

We suggest directing Fedora ? => Fedora forums
Arch ? => Arch forums
Debian => Debian forums
Mint => Mint forums

and on ...

Yes, this question is probably best directed at Microsoft or a windows forum.

Just be polite about it is all (not that your post was rude .. ) ;)

yes though windows forums are barely helpful, often the best place to get help with windows is to post in a linux forum...
As its a smarter crowd :D

---

### Post by gsxruk on 2009-05-07
Hi,

I just completed this dual boot recently and had some problems because my pc is getting a little old now.  Soon time for an upgrade :)

I don't know if this will be any help because the problem is not the same but it may work for you.

After writing the Windows 7 installation disc it would not boot from switch on.  I read somewhere about trying the following which worked for me (you need a Vista disc)

1. Boot from the Vista disc at switch on and when the first screen appears select the repair option.
2. When offered, select for a command prompt.
3. At this stage, switch the disc for the Windows 7 installation disc.
4. Browse to this disk e.g. D: or whatever your drive is.
5. Browse to the "sources" folder (important).
6. Run "setup".
7. The installation of Windows 7 will start from where the Vista one was and worked for me.  During installation I gave Windows about half the disc of which was partitioned and formatted during the installation.
8. Installed Jaunty on the rest of the drive and dual boots perfectly.

Hope this helps.

---

### Post by LowSky on 2009-05-07
Its funny, a week ago I get bashed for telling someone to use the correct forum or to call tech support and I got a warning from a Mod.

Today you guys tell this person  the same thing I do and no one has an issue... got to love Community based forums....


Lately a good amount of people are comming to this site and asking question that have nothing to do with Ubuntu or Linux in general.
Its not like I tell them to RTFM but even telling them to search google brings critizism fomr other members. Personally I love Ubuntu and these forums but with more and more (popularity) people posting help questions on non OS issues it gets rather annoying

anchorschmidt your issue is propbably an easy one. Windows 7 
tries to creat 2 partitions, because your Ubuntu OS may use 3 (if you have /, /home, swap), Windows is failing to install
[http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/](http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/)

---

### Post by Kegusa on 2009-05-07
Actually just finished installing W7RC as dual boot with ubuntu 9.04.
As expected it overwrote the grub boot so I loaded up the live cd and tinkered with grub there, coming over a little wierd thing. I'm not familiar with Vista and how it's made, but Win7 created a 100MB big partition for the booting of Windows so I had to make grub boot from that little partition instead of the partition that I installed Win 7 on..  (Discovered this while manually editing GRUB)

Anyone else had any experience with this before?

My thougth go to the "killswitch" implemented for march 2010 contained in that partition..


Oh, and to the OP - I had the same problem and just burned a new disc and it worked..

---

### Post by mark_vinton on 2009-05-07
I've run into the same issue.  I run 9.04 64 as my main OS (been with ubuntu since 6.06 or whatever it was) and have virtualbox 2.2.2 with an xp vm for my ipod touch usage, and thought it'd be fun to tinker with windows 7 64 rc.  However, it's done the exact same things to me.  I get to a point and it says a driver is missing- no install...  

To the original poster, i feel your pain, and to anyone complaining about it being in the wrong forum or whatever, just realize that if we're on this forum, we're probably all enthusiasts of some degree and it would be beneficial to help if we can.

---

### Post by anchorschmidt on 2009-05-09
Thanks for the help :). I posted here as I thought that someone might have had the same problem as I did and people here are generally more experienced with computers in general so now I'm going to try and burn a new disk and see if it works :)

---

