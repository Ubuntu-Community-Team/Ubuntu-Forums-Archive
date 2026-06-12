---
title: "Hello, I'm new and would like some advice."
date: 2009-11-29
forum: New to Ubuntu
---

### Post by big.d on 2009-11-29
First off, Hi Everyone. I'm big.d, and I'm brand new at this.

My Emachine (bought used) didn't have an XP disc with it, so when, for no apparent reason, my system files went corrupt, I decided that I should try Linux, and settled on Ubuntu. I ordered Karmic Koala and got my shiny new Ubuntu CD in the mail a few days ago.

So now I'm (kinda) up and running, but I don't really know where to go from here. I don't have an internet connection at home, so any programs I get are offline installers, and I'm really having a hard time getting things to run properly.

I have decided I'm going to reinstall Ubuntu, just to start completely fresh and do things right. Once I get that done, I'll take the machine to a friend's house who has broadband, and try to get everything I need to do done in one fell swoop.

My biggest question is this: What do I need most to get the most out of my Ubuntu system?

I want to try to run some windows games, so getting WINE running is important. I also need good programs to play my oversized music collection, burn CDs, backup DVDs, and just do what I want it to do. I also can't figure out how to install the Nvidia display drivers, even though I've read about 3 different tutorials on just that. 

My system is approximately as follows ( In what leading scientists are calling 'Ridiculously Stupid' I can't remember exactly what hardware I have.)

AMD 2400XP, I think!

768MB SDRAM

60GB HDD (My Main HDD)

10GB HDD (stores most of my music collection)

Geforce FX Fifty-Something

onboard sound & ethernet

Old Linksys 802.11b Wireless card (not currently used for anything)

*Is there a way for me to check all these in Ubuntu? Like, something analogous to 'System Information' in Windows XP?

It's a Dinosaur, I know, but the price was right. (And you should have seen the junker that it replaced!):lolflag:

---

### Post by roger_1960 on 2009-11-29
Hi

Go to Mainmenu>accessories>terminal and type
> lshw
which should list (ls) your hardware (hw).  Post the result to this forum and perhaps someone can help with nvidia drivers.

Otherwise, try Rhythmbox & Brasero.  Wine can be installed from the repositories when you are online.  Use "synaptic package panager" in mainmenu>system>administration and search for "wine" to find the right package.

---

### Post by t.rei on 2009-11-29
For a beginner the software center in the menu is actually a very good starting point.

Just browse it a little and install everything you find that might be usefull.

for a start you should install the package "ubuntu-restricted-extras" as soon as you have the internet connection. It is a meta-package - meaning it stands for several others - and will install lots of stuff that cannot be shipped with ubuntu for licencing issues, but its all free to use. Things like ms core fonts, flashplayer etc...

Some pretty decend guides that might be helpfull:
"10 things to do":
[http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing.html](http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing.html)
this also covers the medibuntu repositories. Very usefull stuff!

and partially redundant "13 things to do":
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

But basically you can just install anything that "seems like you might want to use or try it".

There is NOTHING more productive than a linux desktop once you have optimized it for your personal taste and preferences. The default is pretty good by now, too.

Have fun. :)

---

### Post by u.b.u.n.t.u on 2009-11-29
Welcome.

You may have lost XP but you gained a grand operating system. It is a bit buggy here and there but persevere.

Now to some of your questions. The initial install should basically have everything you need with two exceptions:

1. Windows like size games.
2. Working proprietary drivers.

Things like music, video, word processing, linux games all work brilliantly.

There are some good linux games you may want to check out now that you have a linux system.

What Windows games did you have in mind? Your rig is rather dated.

With the Nvidia driver you will need for 3d, check their site:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

You can also download via Ubuntu once you have a net connection.

Just be aware that there may be some issues with the Nvidia drivers not working at this time. So best to test such at the same time you have a net connection so if things go pear shaped you can return here and post for assistance.

If worst comes to worst start Ubuntu in recovery mode and at the command prompt type:

rm /etc/X11/xorg.conf

Then reboot. That will disable your Nvidia driver and revert to the default VESA driver so at least you can log in. Remember, this is a last resort only.

All the best.

---

### Post by big.d on 2009-11-29
As for Windows games, I'm gonna try to get Mechwarrior 3, KOTOR, Command & Conquer Generals, Starcraft, Dungeon Siege 2, and Starlancer running. Maybe some others as well. 

Eventually, I'll maybe get around to ordering a recovery disc for the machine and set up a dual-boot system.

What's the favored music player on Ubuntu? I always used Winamp for music and video on Windows, so something similar would be good. I got Songbird sort of working (have to run it's whatever you call in main file in terminal to start it) but I don't really like it's interface.

---

### Post by Plumtreed on 2009-11-29
System> administration> Update manager might be a good place to start....things might run better for you.

---

### Post by big.d on 2009-11-29
I'm hoping things will go more smoothly the second time around.

I'm doing some more reading, and I'm wondering about something.

If I want to do a fresh install, with an eye toward having a dual-boot system, how should I partition the 60GB drive. I've heard of making a /home partition for linux so the OS is separate from the rest of your Linux system. Should I set up 4 partitions? Something like one for Ubuntu, one for /home, one for XP, and one for shared space. Or is there a better way to do this?

---

### Post by u.b.u.n.t.u on 2009-11-29
> **big.d said:**
> What's the favored music player on Ubuntu?


This is a decent review of some audio players:

[http://www.anewmorning.com/2008/05/21/10-best-linux-audio-players/](http://www.anewmorning.com/2008/05/21/10-best-linux-audio-players/)

---

### Post by big.d on 2009-11-29
Where are my manners?:-P:p:p

[SIZE=5]Thank you everyone, you are being most helpful![/SIZE]

---

### Post by manoriax on 2009-11-29
> **big.d said:**
> I'm hoping things will go more smoothly the second time around.

I'm doing some more reading, and I'm wondering about something.

If I want to do a fresh install, with an eye toward having a dual-boot system, how should I partition the 60GB drive. I've heard of making a /home partition for linux so the OS is separate from the rest of your Linux system. Should I set up 4 partitions? Something like one for Ubuntu, one for /home, one for XP, and one for shared space. Or is there a better way to do this?

To set up a linux system, there are at least two partitions needed. One for /home, which contains all your documents, music and applications data (e.g. settings etc.). The partition that is simply called / contains the system itself (means: kernel, programs, ...).

Depending on your RAM I would recommend another partition (swap) in the size of...2 GB should be enough I guess.

You should take those points into consideration when you set up your system.

Use the rest of the available disc space to set up Windows. Linux is able to access your Windows partiton so you do not need to create a shared partition I think.

Regards

---

### Post by big.d on 2009-11-29
@ manoriax: OK cool thank you.

I flipped thru the .pdf guide i just downloaded. it's very good.

---

### Post by candtalan on 2009-11-29
> **big.d said:**
> I don't have an internet connection at home

This is important because a lot of what people will suggest might expect an online connection. Stuff can be easy if an internet connection exists. Off line is ok but there are a few more things you will need to know.

Ubuntu and the like use so called 'Repositories' of programs - large on line libraries - containing a lot of stuff, typically say, 30GB, depending on the Ubuntu version.

There might be a way of making use of a program called apt on cd (aptoncd) to get stuff onto CD.
There may be other ways of making programs for installation to be transportable, perhaps others here can suggest approaches?

hth

---

### Post by Bartender on 2009-11-29
I've been dinking off and on with Linux (mostly Ubuntu) for about 5 years now behind a dial-up connection.
I've tried aptonCD, and Keryx.  Sad to say, I've found no substitute for a broadband connection.
Linux drove me to get a laptop so I could go into town and find some broadband.  
Maybe your friend will let you stop by a couple of times a month.

Before you go too much further, are you thinking of installing Windows?  Cause it sure makes life simpler to install Windows before installing Ubuntu.  You mentioned that you have no discs, but do you have the shiny 25-character COA sticker somewhere on the PC?  If so, all you need is somebody's XP disc, and probably some time at your friend's house to get drivers.

There's nothing illegal about using somebody else's XP CD.  A real true XP CD, by the way, don't try using someone's recovery disc.  There's nothing unique about the CD.  Microsoft stamped out millions of them.  The 25 character key on your COA sticker is what makes your copy unique (and legal in the eyes of MS).

If you are thinking about installing Windows, I'd suggest doing it now, then reinstall Ubuntu.  That would be better than using Ubuntu for several weeks or months, then deciding you do want XP back on there after all.

I'm a little concerned about the PC's original meltdown.  You said "no apparent reason" but there's always a reason and I'm wondering if the thermal paste has dried up, or the CMOS battery is almost dead, or the HDD is starting to fail, or maybe the power supply is going gunnysack on you?

---

### Post by ed-koala on 2009-11-29
big.d, some EXTREMELY important advice!!

Go to WineHQ web site and check out all the games you want to run, to see how compatible they are.  Running Windows games under Ubuntu is hit or miss, some may work flawlessly with Wine, some won't work at all.

Also, You can run Windows in VirtualBox, but that requires a Windows install CD to set up, and also may not run some things.  If all those games are vital for you, research first or else you may be sorry later!

Next, try a Live CD first.  This allows running Ubuntu and testing your system without losing your current Windows stuff.  I recommend starting with version 8.04, the most recent long tern service release as it is the most stable and least likely to cause problems for you. You can work on upgrading afterward.

Good luck and welcome to the wonderful world of Ubuntu!

---

### Post by big.d on 2009-11-29
@Bartender: If I could get a Windows CD, I may never have tried Ubuntu in the first place, actually. Nobody I know has one, they all lost theirs. 

So, I was going to order a replacement from Microsoft (you can get a new disc if you have a good Product Key) but when I actually got to looking at my PC case, the joker I bought it from peeled off the Microsoft sticker! So now I guess if I want XP I need to just get in touch w/ Emachines support and cough up a few bucks for a replacement. I would have done that already, however it hasn't been a concern since I don't really need the machine for anything other than playing my mp3 collection and letting my girlfriend play Dungeon Siege.:P

Also, it wasn't much of a 'meltdown'. I was getting more frequent lockups and having trouble with the machine, and with no internet or recovery disc, I just rode it out until one day i booted the machine and it told me that something-or-other system file directory was corrupt or missing. I messed with it for awhile, considered installing Win98 (which I do have a disc for) so it would play Starlancer, then remembered how much trouble it was to get 98 running back when it was actually supported.

So I unplugged the old beast and it sat for a month and a half. Then, just recently, the linux bug bit. I'd played around with Damn Small and Puppy on an older machine, (the IBM 533 Celeron that this replaced, what a piece of junk) and figured there would be some decent options for a desktop OS if I looked around. I settled on Ubuntu because it was hyped as the best choice for an end-user linux OS.

@ed-koala: too late for that. The HDD was useless anyway. I was fortunate to have backed up my important data to DVDs literally a week before the system went down, so I jumped into the deep end, reformatted and installed Karmic.

I'm gonna reformat again, create my partitions for Karmic and XP, install Karmic fresh, and head to my friend's house to get online. I figure I should be able to get everything I need in one day, so at least I'll have a useful PC at home.

And if the HDD dies, no worries. I'm not doing anything mission critical with it, and it would give me some incentive to upgrade to something contemporary.


Thanks for the advice, everyone. I'll keep you posted on how things progress.
big.d

---

