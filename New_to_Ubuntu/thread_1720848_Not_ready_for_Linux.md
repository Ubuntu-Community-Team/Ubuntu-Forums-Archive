---
title: "Not ready for Linux"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by hezbollama on 2011-04-03
I think I'm not ready to use Linux. I feel like I am between a beginner and an intermediate user; I need more than the basic email/music/movie/Facebook functionality of an OS, but I cannot understand even the basics of commands that Linux relies on. I bought a laptop for school from a local (and great) non-profit computer recycling store and it came preloaded with Ubuntu 10.10. After attempting to work with Ubuntu and continually getting frustrated I tried reformatting the hard drive with gParted and installing XP but it didn't work. The XP disk I used (which I have successfully installed on multiple computers) could not find a hard-drive in my computer. I then used DBAN to eradicate all information for a  clean start but had the same exact problem. I could, however, install Ubuntu 10.10 from the disk I made with the intention of duel booting XP and  Ubuntu. I found it odd that Ubuntu would take hold but XP would not. I've looked and looked but have yet to find information what can actually help me remove the partitions and prepare my hard-drive for a fresh install of XP. I still plan to duel boot Ubuntu along with XP, but I cannot tolerate Linux (which I see as my problem, not Linux's) at this time. With school to focus on I cannot afford to spend my time wrestling with Linux. I would greatly appreciate help with this task.

---

### Post by Paqman on 2011-04-03
> **hezbollama said:**
> I found it odd that Ubuntu would take hold but XP would not.

Early versions of XP could not install to SATA disks. If you've got a SATA hard drive and a really old XP disk then you'll need a disk with SATA drivers to do the install. Newer XP install images or old ones slipstreamed with SP2 (I think?) should be able to see your drive ok.

You may also be able to set your SATA drive to appear as an IDE one in your BIOS. That would allow you to get XP installed, then install the service packs and switch the drive back to SATA mode in BIOS.

---

### Post by earthpigg on 2011-04-03
hi,

if you've dbanned the hard drive, then it isn't possible that ubuntu is still preventing windows xp from loading.

check the bios settings. when you first turn it on, and it says 'press ___ to enter setup', do so and look around in there. see if there are multiple hard drives, and which is set as the primary.

also:

> The XP disk I used (which I have successfully installed on multiple computers) could not find a hard-drive in my computer. 

you've uninstalled the past XP installs prior to attempting the current one, right? else, that is copyright infringement.

---

### Post by dcsoldschool53 on 2011-04-03
**When you had reformatted your had drive did you do it with  fat32?**

---

### Post by t4thfavor on 2011-04-03
Im going to make a vote for the SATA driver floppy. XP needed them loaded from a floppy. It wasn't until Vista that you could load them from USB or CDROM.

---

### Post by madjr on 2011-04-03
> **hezbollama said:**
> I think I'm not ready to use Linux. I feel like I am between a beginner and an intermediate user; I need more than the basic email/music/movie/Facebook functionality of an OS, but I cannot understand even the basics of commands that Linux relies on. I bought a laptop for school from a local (and great) non-profit computer recycling store and it came preloaded with Ubuntu 10.10. After attempting to work with Ubuntu and continually getting frustrated I tried reformatting the hard drive with gParted and installing XP but it didn't work. The XP disk I used (which I have successfully installed on multiple computers) could not find a hard-drive in my computer. I then used DBAN to eradicate all information for a  clean start but had the same exact problem. I could, however, install Ubuntu 10.10 from the disk I made with the intention of duel booting XP and  Ubuntu. I found it odd that Ubuntu would take hold but XP would not. I've looked and looked but have yet to find information what can actually help me remove the partitions and prepare my hard-drive for a fresh install of XP. I still plan to duel boot Ubuntu along with XP, but I cannot tolerate Linux (which I see as my problem, not Linux's) at this time. With school to focus on I cannot afford to spend my time wrestling with Linux. I would greatly appreciate help with this task.

First of Welcome. 

Second, dont worry we all been there.

linux can take some time (usually like a couple of weeks to get used to it). Is not your fault is just how the subconscious works, specially with the limited time in your hands.

Anyway, it looks like you still want to learn, but of course at your own rhythm (or when you get the time).

So i would advise getting at it slowly, check out some interesting stuff you can do, videos, follow some blogs, etc.

a good start would be:

[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

[http://www.webupd8.org/](http://www.webupd8.org/)

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)


and of course you can always ask almost anything on these forums, not just about linux or open source. :)

ps. you can do almost anything from a gui, not just the command line. But you have either option as you become more advanced. And remember that ubuntu is great for dual-booting, is always good idea to have more than one OS installed.

---

### Post by Hedgehog1 on 2011-04-03
> **hezbollama said:**
> ... After attempting to work with Ubuntu and continually getting frustrated I tried reformatting the hard drive with gParted and installing XP but it didn't work. The XP disk I used (which I have successfully installed on multiple computers) could not find a hard-drive in my computer. ...

hezbollama,

The XP install might be happiest with no partitions defined on the hard drive, and just have an MBR partition map (the only one Windows understands).

To See if this will get you rolling, please do this:


Please boot off the LiveCD/LiveUSB, select 'TRY'.

Run Gparted, and do this for the hard drive:

[img]http://img834.imageshack.us/img834/8480/gpartedpartitiontable.png[/img]

Gparted defaults to the **MBR** partition map - **that is the one you want**.

Press the 'check mark' button and make the change real.

**Don't add any partitions - let the XP install do that.**

If XP still will not install, please come back and we will look for other options to get you going.

***The Hedge***

:KS

p.s. I believe the issue you have had is that the the GPT type partition map was used for the Ubuntu only install, and the XP installer cannot make head-or-tails of that.

---

### Post by Hedgehog1 on 2011-04-03
> **t4thfavor said:**
> Im going to make a vote for the SATA driver floppy. XP needed them loaded from a floppy. It wasn't until Vista that you could load them from USB or CDROM.

The XP SP2 and XP SP3 CDs do install on SATA drives without a driver floppy, but I belive you are correct that the original XP disks needed the driver floppy.

That would be the next logical step to try if **hezbollama** finds that the GPT vs MBR partition map is not the issue. 

One way or another, **this many good minds** will get him where he wants to be.


***The Hedge***

:KS

---

### Post by wolfen69 on 2011-04-03
> **hezbollama said:**
> I need more than the basic email/music/movie/Facebook functionality of an OS, but I cannot understand even the basics of commands that Linux relies on.

So do I, and I never need commands. Can you give us an example of what you like to do on the computer?

---

### Post by grahammechanical on 2011-04-03
I agree with wolfen69. I went from Windows 98 four years ago to Ubuntu and I have never needed to use a command in order to use my computer. I did not need them in Windows and I have not needed them in Ubuntu. I think that Ubuntu is becoming the OS that lets you do things either way.

Regards.

---

### Post by hezbollama on 2011-04-03
The copy of XP I have works with SATA hard drives. It came with my previous laptop which I am just replaced.   

Yes, I believe it was formatted in Fat32. That was the only  option I recognized in the list. I thought I got rid of the partitions.  At least, that's what I was trying to do. I don't know if I did it right  though. I used GParted and the "create partition table" and got the  "windows cannot find a hard drive" message, just the same as when I  tried to get XP do do the partition itself.

As for having to use  commands for programs, I don't know how you download anything that is  not in the repository without having to use commands. And, for me at  least, nothing works the way it says it's supposed to. Inevitability I  find a "how to" for whatever program I'm trying to work with that is an  "easy" 5 step process of commands, the first of which doesn't work. It's  too frustrating for me to deal with. Some examples are getting podcasts  or radio stations to work with the default player that came packaged  with Ubuntu. If I wanted a different player I'm sure that would be even  more frustrating.  I tried downloading desktop themes for Emerald and  none of the themes work. They all say they are not valid themes. Again,  the only help I was able to find was a process of commands which don't  work for me.

Any other ideas?

---

### Post by ikt on 2011-04-03
> **hezbollama said:**
> After attempting to work with Ubuntu and continually getting frustrated I tried reformatting the hard drive with gParted and installing XP but it didn't work. 

You said you have trouble using Ubuntu but then tried to do something a more experienced user would do?

> **hezbollama said:**
> As for having to use  commands for programs, I don't know how you download anything that is  not in the repository without having to use commands.

Why do you have to download things outside of the repo?

> **hezbollama said:**
> 
If I wanted a different player I'm sure that would be even  more frustrating.  I tried downloading desktop themes for Emerald and  none of the themes work. Any other ideas?

Ask for help with what you need help with, not help getting around things you need help with.

> **hezbollama said:**
> Some examples are getting podcasts  or radio stations to work with the default player that came packaged  with Ubuntu.

What problem were you having? Did you have the right codecs installed?

> **hezbollama said:**
> I tried downloading desktop themes for Emerald and  none of the themes work. They all say they are not valid themes.

Emerald themes haven't been used for a while now.

Here are some theme's you might like, which are easy to install.

[http://www.bisigi-project.org/?page_id=6&lang=en](http://www.bisigi-project.org/?page_id=6&lang=en)

How to install: (from the page) 
[http://www.bisigi-project.org/?page_id=8&lang=en](http://www.bisigi-project.org/?page_id=8&lang=en)

1. sudo add-apt-repository ppa:bisigi/ppa && sudo apt-get update
2. sudo apt-get install bisigi-themes

then right click on your desktop, and choose change desktop, and the theme's should be there.

3. easy!

---

### Post by Timmer1240 on 2011-04-03
I went from windows xp to Linux and never missed a beat any questions or problems I just googled or asked in this forum and got good answers.I did duel boot but pretty much forgot about the windows partition rather quickly hope you can work out your problem and get it duel booted and learn at your own pace!I dont hardly have to use the terminal for much either I dont think you really need to unless your running it as a server or something like that.

---

### Post by techunit on 2011-04-03
> **ikt said:**
> You said you have trouble using Ubuntu but then tried to do something a more experienced user would do?



Why do you have to download things outside of the repo?



Ask for help with what you need help with, not help getting around things you need help with.



What problem were you having? Did you have the right codecs installed?



Emerald themes haven't been used for a while now.
This user isn't ready to commit to linux. He is fully capable of learning he just doesn't seem to want to. The problem your having with the Win XP disk could have something to do with the fact thats its OEM and not supposed to be used with anything but the computer it came with. It is also quite illegal to do otherwise with it. Linux is a fun and exciting OS to work with especially Ubuntu but if your not willing to ask questions then your really not going to have alot of fun.

---

### Post by ikt on 2011-04-03
> **techunit said:**
> This user isn't ready to commit to linux. He is fully capable of learning he just doesn't seem to want to.

I think it's just because they are attacking ubuntu's problem as if Ubuntu is Windows.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If hezbollama is willing, they will find their basic problems will be very easy to fix, you just need to attack them in the right way.

---

### Post by Paqman on 2011-04-03
> **hezbollama said:**
> 
As for having to use  commands for programs, I don't know how you download anything that is  not in the repository without having to use commands.

The only stuff from outside the repos i'd normally bother installing would be stuff that has a .deb file available, or can be got from a PPA. You'd only have to use the command line to install something if you were messing about with tarballs and/or compiling from source, which is almost never necessary.

The repos are so big and Ubuntu is so widely supported that you should be able to use the package manager to get anything you need.

---

### Post by bodhi.zazen on 2011-04-03
> **techunit said:**
> This user isn't ready to commit to linux. He is fully capable of learning he just doesn't seem to want to. 

I agree, Ubuntu / Linux is not for everyone. Rather the attempting to push Ubuntu on the OP , please try to solve the problem.

Perhaps the OP would then be willing to dual boot or run Ubuntu in Virtualbox, who knows ?

@hezbollama :

It seems your windows install disk does not have the proper drivers. Unfortunately this is a common problem and it may be difficult to identify and download the drivers you need.

I would suggest you try taking the PC to a local repair shop, they may be willing to give you some fast advice. Otherwise you are going to need to google search to see if you can find the windows drivers you need.

You may also have better success if you post to a Windows forum.

If you decide to go with Ubuntu, it would be easy to install. If you install Ubuntu and have a problem, I would start a new thread.

---

### Post by Learning Linux 2011 on 2011-04-04
> **hezbollama said:**
> I think I'm not ready to use Linux. I feel like I am between a beginner and an intermediate user; I need more than the basic email/music/movie/Facebook functionality of an OS, but I cannot understand even the basics of commands that Linux relies on. I bought a laptop for school from a local (and great) non-profit computer recycling store and it came preloaded with Ubuntu 10.10. After attempting to work with Ubuntu and continually getting frustrated I tried reformatting the hard drive with gParted and installing XP but it didn't work. The XP disk I used (which I have successfully installed on multiple computers) could not find a hard-drive in my computer. I then used DBAN to eradicate all information for a  clean start but had the same exact problem. I could, however, install Ubuntu 10.10 from the disk I made with the intention of duel booting XP and  Ubuntu. I found it odd that Ubuntu would take hold but XP would not. I've looked and looked but have yet to find information what can actually help me remove the partitions and prepare my hard-drive for a fresh install of XP. I still plan to duel boot Ubuntu along with XP, but I cannot tolerate Linux (which I see as my problem, not Linux's) at this time. With school to focus on I cannot afford to spend my time wrestling with Linux. I would greatly appreciate help with this task.

I purchased Acronis True Image a long time ago.  It has a program that *completely *wipes the hard drive, including any boot info.  It might be worthwhile for you to buy it.

I have heard that this also works:
[http://www.dban.org/download](http://www.dban.org/download)

Or this:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by wojox on 2011-04-04
> **Learning Linux 2011 said:**
> I purchased Acronis True Image a long time ago.  It has a program that *completely *wipes the hard drive, including any boot info.  It might be worthwhile for you to buy it.

DBAN overwrites the MBR as well.

---

### Post by zsazso on 2011-04-04
Just my 2cents, but I'm 47 years old, never touched a computer till about 4 years ago. I wasn't ready either (for xp, win 7, ubuntu, or anything else). I'm still learning something about all of them. You're never too old to learn. Also, by the way, command line stuff is really hard to understand for beginners, and experienced alike. Nobody just understands that kind of stuff. It has to be explained to everyone, at one time or another. If you want to know something, just ask. It really is as simple as that, and you're in the right place to start. The people in this community are SO helpful. 
 P.S. I prefer GUI over command line, and almost never have to use CLI, thanks to the folks here.

---

### Post by srs5694 on 2011-04-04
First, some background to help anybody unfamiliar with the issues  understand what's being discussed in the below quote: Until recently, most PCs have used  the Master Boot Record (MBR) partitioning system, aka "MS-DOS  partitions," "BIOS partitions," or various other terms. Some PCs,  including recent Macintoshes, now use the GUID Partition Table (GPT)  system instead. These are two different ways to define partitions. The  32-bit version of Windows XP can't understand GPT, but recent versions  of Ubuntu can. Ubuntu doesn't use GPT by default on most computers,  though.

> **Hedgehog1 said:**
> I believe the issue you have had is that the the GPT type partition map was used for the Ubuntu only install, and the XP installer cannot make head-or-tails of that.

I don't believe this is the case, for three reasons:


[list]
[*]The OP didn't mention GPT being in use, and Ubuntu doesn't use GPT by default. Therefore, it's unlikely that the disk was ever partitioned using GPT, although I can't say this with certainty.
[*]GPT includes a protective MBR that's designed to signal to GPT-unaware utilities that the disk is in use. Thus, the 32-bit Windows installer, when shown a GPT disk, should see the disk but report that it's got a single partition. I've just tested this, and it works as I expected. I've also seen reports on this forum from people who've installed in this way (it can create problems down the line because some GPT data remain behind, which can confuse some partitioning tools). In other words, if the disk *did* originally use GPT, that shouldn't prevent Windows from installing on the disk.
[*]The OP reported that the disk had been wiped using DBAN. Unless this process went badly awry, it would result in the destruction of all partitioning information, both GPT and MBR.
[/list]


Thus, I can say with a high degree of confidence that GPT is *not* an issue here.

The symptoms being reported are usually the result of missing drivers, as others have suggested. Note that Windows' ability to "see SATA disks" is *not* universal; different disk controllers require different drivers, and Windows XP is old enough that its installation disc might not have drivers for whatever hardware is in the computer. Try checking the manufacturer's Web site for drivers, or use hardware identification/diagnostic software to learn what disk controller chipset the computer uses and look for drivers for it.

The suggestion that the installer being used might be tied to specific hardware other than the hardware being used is another valid possibility. If so, that version of Windows just won't install; the OP will need to buy a retail version of Windows rather than an OEM version.

It's also possible that adjusting a BIOS option relating to the hard disk might fix the problem. In particular, look for anything relating to AHCI mode and fiddle with it.

---

### Post by Hedgehog1 on 2011-04-04
> **srs5694 said:**
> GUID Partition Table (GPT)...


I don't believe this is the case, for three reasons:


[list]
[*]The OP didn't mention GPT being in use, and Ubuntu doesn't use GPT by default. Therefore, it's unlikely that the disk was ever partitioned using GPT, although I can't say this with certainty.
[*]GPT includes a protective MBR that's designed to signal to GPT-unaware utilities that the disk is in use. Thus, the 32-bit Windows installer, when shown a GPT disk, should see the disk but report that it's got a single partition. I've just tested this, and it works as I expected. I've also seen reports on this forum from people who've installed in this way (it can create problems down the line because some GPT data remain behind, which can confuse some partitioning tools). In other words, if the disk *did* originally use GPT, that shouldn't prevent Windows from installing on the disk.
[*]The OP reported that the disk had been wiped using DBAN. Unless this process went badly awry, it would result in the destruction of all partitioning information, both GPT and MBR.
[/list]


Thus, I can say with a high degree of confidence that GPT is *not* an issue here.

Well dog gone, it was *SUCH* a great (if wild) theory, too.  However, your logic is impeccable.  Thanks for your detailed explanation **srs5694**!  I continue to learn every day...

  

***The Hedge***

:KS

---

### Post by madjr on 2011-04-04
> **hezbollama said:**
> The copy of XP I have works with SATA hard drives. It came with my previous laptop which I am just replaced.   

Yes, I believe it was formatted in Fat32. That was the only  option I recognized in the list. I thought I got rid of the partitions.  At least, that's what I was trying to do. I don't know if I did it right  though. I used GParted and the "create partition table" and got the  "windows cannot find a hard drive" message, just the same as when I  tried to get XP do do the partition itself.

As for having to use  commands for programs, I don't know how you download anything that is  not in the repository without having to use commands. And, for me at  least, nothing works the way it says it's supposed to. Inevitability I  find a "how to" for whatever program I'm trying to work with that is an  "easy" 5 step process of commands, the first of which doesn't work. It's  too frustrating for me to deal with. Some examples are getting podcasts  or radio stations to work with the default player that came packaged  with Ubuntu. If I wanted a different player I'm sure that would be even  more frustrating.  I tried downloading desktop themes for Emerald and  none of the themes work. They all say they are not valid themes. Again,  the only help I was able to find was a process of commands which don't  work for me.

Any other ideas?

Hey hezbollama,

i think this will help you:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

this is an easy visual guide, that will tell you everything you need about ubuntu. It's written by one of our forum moderators.

am pretty sure you'll solve almost all doubts, after checking it a bit :)

also, you might find these useful:

[http://www.youtube.com/watch?v=16Ocb8oNhM8](http://www.youtube.com/watch?v=16Ocb8oNhM8)

[http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/](http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/)

[http://news.softpedia.com/news/Ubuntu-10-10-Desktop-Customization-Guide-186408.shtml](http://news.softpedia.com/news/Ubuntu-10-10-Desktop-Customization-Guide-186408.shtml)

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1158-top-things-to-do-after-installing-ubuntu-1010-marevick-meerkat](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1158-top-things-to-do-after-installing-ubuntu-1010-marevick-meerkat)

---

### Post by hezbollama on 2011-04-05
Thanks to everyone who responded, and especially for the links. They were helpful (some more than others :)  ). I think I'm going to stick with Ubuntu for awhile. The basics work, and I can build up to more advanced things. One problem I was having was not realizing my idea of "advanced" on Linux was different than Windows or Mac. I also realized that I was still thinking in "Windows operator" mode. I'm sure I'll be posting questions to these forums again. Thanks again.

---

### Post by Javelin Dan on 2011-04-05
[COLOR=black][FONT=Arial]I'm going to give you advice that no one else will - newbie to newbie. First of all, don't give up on Linux. It's a remarkable system with many possibilities, even for newbs. But you have to remember that it was originally designed by and for "software engineer" types who have little time or tolerance for non-geeks. I have spent MANY hours trying to solve the (seemingly) simplest of problems only to fail miserably time and time again. While well intentioned, most of the advice given in these forums assumes a certain amount of basic knowledge about Linux that many of us just don't have. If you want to see one of these forum threads go dead as a doornail, just keep pleading that you don't understand something. Your "angels" will then go hover over top of someone else who has some basic knowledge of Linux, or at least some well established computer skills. This is not a slap at anyone - it's just how it is. I've also noticed that many responders fixate on one isolated aspect of your question and then bat the arguments back and forth like a tennis ball without ever addressing your major concerns. Additionally, I'm wondering if your current laptop has enough resources to run both XP and Ubuntu - both are pretty hungry apps. It might, but my old Dell did not.[/FONT][/COLOR]
[COLOR=black][FONT=Arial]    [/FONT][/COLOR]
[COLOR=black][FONT=Arial]    So, I'm going to give you some hard-earned advice...[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]1.)  Try multiple distros on for size. Try to stay with one that is lightweight (doesn't use a lot of resources) and something that will keep you in a primarily desktop environment. This will give you the closest thing possible to the "Windows experience". Pick one you like due to feel and ease of use. Some I would recommend checking out are Lubuntu 10.10, Puppy Linux 5.2, and Antix 8.5. Of these, Antix is by far the most hardy. It will take a lickin' and keep on tickin". If you lock it up (done that many times on my old Dell laptop), you will be able to do a hard shut down-power off and restart without screwing anything up. I can't say that for the other distros. However, Antix is not the most user friendly to a newbie. I REALLY like the looks of Lubuntu so far, but have found synaptic package manager (the app to download and apply software) to be a bit buggy. Neither Lubuntu or Puppy properly configured the sound card on my Compaq Presario laptop, but Antix did.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]2.) If you purchase any hardware peripherals (wireless modems, Mp3's, printers, etc.) make *_absolutely sure_* that they not only work with Linux, but the specific distro you are using. What works with one Linux flavor doesn't always work with another and trying to properly configure a non-working piece of hardware in Linux practically requires an engineering degree. I found this out the hard way when I purchased a wireless dongle said to have[/FONT][/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR][COLOR=black][FONT=Arial]worked with Linux. I spent evenings and weekends for over 6 weeks and never was able to make it work. I then surrendered and bought another new one (made by SMC) that was reported to work with Mepis (the parent distro of Antix) and it worked right out of the box – plug-n-play! It’s OK to try an existing piece if you’ve already got it, but don’t give up chunks of your life trying to reinvent the wheel.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]3.) Read, read, read! Bury your nose in all the online manuals (there’s usually one for each OS), wikis, tutorials and forums that you can. Knowledge is power, and I’ve had too little of it as of late. A couple of books that I would recommend are “Beginning Ubuntu Linux” by Keir Thomas & Jaime Sicam (remember, differences from one Linux distro to another are small), and "Linux for Dummies” by Richard Blum. These certainly won’t get you out of every scrape you’ll get into, but the knowledge you will squeeze out of them will be invaluable. You can find either of these used on Amazon for about $12 (US). [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]4.) Don’t get discouraged! I know all too well Linux can be very frustrating at times (well – most of the time!), but when you actually do accomplish something, you feel like “Rocky” running to the top of the steps. Best of luck, and keep fighting![/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]

---

### Post by bodhi.zazen on 2011-04-05
FYI, most hardware is not necessarily distro dependent, but rather kernel dependent.

---

### Post by Ariakkas on 2011-04-05
you didn't sit down in front of windows on the first day and suddenly become a power users through osmosis. it took time, Linux does things differently, and for good reason...its not windows. If Linux did things the windows way, it would be windows. 

Baby steps, problems pop up, pick one you want to solve, and Google it. when you get it, move on to the next one. I've never spent more than an hour or two trying to get something to work, and those are usually on things that most people don't have to worry about, such as wired internet tether for my iPhone, or multitouch support for a touch screen netbook.

and getting this stuff to work is half the fun for me, if everything worked out of the box, i would become bored very quickly and move on to a broken distro just so i had something to do. It actually makes the OS yours, and not just the same copy that everyone else has, it doesnt EXACTLY what you need, and nothing more.

---

### Post by madjr on 2011-04-05
@Javelin Dan

your advise is good, but things have gotten a Lot easier since 2009 and hell lot easier since 2007 when i started.

linux just gets better and better every 6 months.

i can honestly say that a ton of stuff is easier to do on linux than on other OSs, without mentioning that linux is the most secure and lowest maintenance OS i know and is only going to get better :popcorn:

---

### Post by Old *ix Geek on 2011-04-05
> **hezbollama said:**
> I think I'm not ready to use Linux. I feel like I am between a beginner and an intermediate user; I need more than the basic email/music/movie/Facebook functionality of an OS, but I cannot understand even the basics of commands that Linux relies on.I'm baffled. :confused: My mother--who is over 80--uses Kubuntu day in and day out. She made the switch, cold turkey, from 20 years of using windoze, and needed *NO* help. No instruction, no tutoring, no hand holding. I just wiped her drive, installed Kubuntu, added tons of programs I knew she'd like and want to try, and said "here you go!" She intuitively went straight to the KDE menu button, clicked it, started scrolling through the programs, and started using them. So, yeah...I'm just a bit stumped as to why you're finding Linux so foreign and so challenging. My mother is the least computer savvy person I know, and she has ZERO problems using Kubuntu.
> I tried reformatting the hard drive with gParted and installing XP but it didn't work. The XP disk I used (**[color="red"]which I have successfully installed on multiple computers[/color]**) could not find a hard-drive in my computer.Um...isn't that illegal?
> I then used DBAN to eradicate all information for a  clean start but had the same exact problem. I could, however, install Ubuntu 10.10 from the disk I made with the intention of duel booting XP and  Ubuntu. I found it odd that Ubuntu would take hold but XP would not.Shhhhhh...it's all part of a huge sinister plot for *Ubuntu to overtake the world!

---

