---
title: "Still overwhelmed newb.. blank screen"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by magnoliasouth on 2009-02-20
I'm back again ([old post]("http://ubuntuforums.org/showthread.php?t=1058901"))! Sorry about this.

Okay, I did a search and I did find a thread ([here]("http://ubuntuforums.org/showthread.php?t=1068910")) that described my problem.

Just to remind everyone, the computer we're installing Ubuntu on is a wiped computer with no OS.

I followed the [burn]("https://help.ubuntu.com/community/BurningIsoHowto") and the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") instructions to the letter. All went okay.

I tried running the install CD (8.10 desktop i386) and we first checked the CD integrity. It passed. I then ran it in the "Play around" kind of mode (I can't remember what the option was called) and I got the blank screen issue.

I shrugged that off, but did worry about it. 

We decided to run the install CD anyway. All seemed to go okay, it said we needed to reboot, so we did.

Then, the blank screen was back.

We tried recovery mode, that didn't help.
We tried one that "fixes hardware" (I can't remember that option either) and that didn't help.
We tried logging in under GNOME, that didn't help.

I searched the forum and came up with that post I mentioned above. I cannot find a way to download 8.4.

I'm so frustrated and disappointed. Any direction anyone can give me would be appreciated.

---

### Post by rhcm123 on 2009-02-20
Would you post your system specs (anyting you can garnish from the stickers on the outside, looking up model numbers, etc would be helpful) and specify exactly what you want to do?

EDIT: I just finished reading through the other thread. It sounds like the desktops you bought may not have the power to support ubuntu. I would suggest xubuntu to at least get an OS on.

EDIT2: Just trying to cut down on posts. I think there might have been an error running the graphical install. Try the alternate install CD instead.

---

### Post by magnoliasouth on 2009-02-20
> **rhcm123 said:**
> would you post your system specs and specify exactly what you want to do?

Pentium 4 
2400 Mhz
768 MB RAM
40 G hard drive
IBM NetVista
Machine Type 8307
Model 42U
MFG Date 212
Product ID 830741U

That is, sadly, everything written on the machine from top to bottom, except the serial number. lol!

---

### Post by rhcm123 on 2009-02-20
Yes, those are the specs i wanted. I should of said that i really only needed the ammount of RAM, the processor make, speed and model. SORRY :). You have well over the minimum ammount needed to run ubuntu. Hard Drive is tiny, but that's not really an issue for the moment.

I have a sneaking suspuscion your computer can't handle the graphic installers. In that case you will have to use the alternate install disks. Instead of using the nice graphical installer it uses a more simple text based installer. Still very easy to use.

There are several things you can do:
1. Download the Ubuntu alternate 8.04 CD from: [here]("http://ubuntu.media.mit.edu/ubuntu-releases/hardy/ubuntu-8.04.2-alternate-i386.iso"). 
2. Xubuntu. A much ligheter-on-the resources ubunutu, it uses xfce instead of GNOME. Download the 8.04 alternate disk from:[here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/xubuntu-8.04.1-alternate-i386.iso")
3. Install a server edition of ubuntu (comes with a few server extras and NO GUI) and then install the GUI from the command line. i can walk you through this if you want.

---

### Post by magnoliasouth on 2009-02-20
> **rhcm123 said:**
> There are several things you can do:
1. Download the Ubuntu alternate 8.04 CD from: [here]("http://ubuntu.media.mit.edu/ubuntu-releases/hardy/ubuntu-8.04.2-alternate-i386.iso"). 
2. Xubuntu. A much ligheter-on-the resources ubunutu, it uses xfce instead of GNOME. Download the 8.04 alternate disk from:[here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/xubuntu-8.04.1-alternate-i386.iso")
3. Install a server edition of ubuntu (comes with a few server extras and NO GUI) and then install the GUI from the command line. i can walk you through this if you want.Okay. Number 3 sounds Greek to me. I've no idea what a server edition is.

A question about number 2: Can I run Wine and more specifically World of Warcraft on this? (The main use for this computer is strictly for one user to log onto WoW. We don't need a new gaming computer, just have access every now and then.)

What do you think is our best and most easy for newbs option?

---

### Post by Mercury_Alpha on 2009-02-20
> **magnoliasouth said:**
> Okay. Number 3 sounds Greek to me. I've no idea what a server edition is.

Surf over to [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") and click on the "Server Edition" tab ;)

---

### Post by magnoliasouth on 2009-02-20
> **Mercury_Alpha said:**
> Surf over to [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") and click on the "Server Edition" tab ;)Thanks, but I still have no clue what that means. :(

---

### Post by OffAxis on 2009-02-20
after you get the server edition installed the graphical desktop is just a 
```

sudo apt-get install ubuntu-desktop
```

or (for xfce based desktop):

```
sudo apt-get install xubuntu-desktop
```

or (for kde 4.1):

```
sudo apt-get install kubuntu-desktop
```

Those will install the respective desktop along with the 'desktop applications' (stuff you probably want).

---

### Post by OffAxis on 2009-02-20
> **magnoliasouth said:**
> Thanks, but I still have no clue what that means. :(

That's just where you can download another version of ubuntu. You can also get (yet another version) here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by soxs on 2009-02-20
Just donwload the installer for servers. It will have all features the normal edition has, except graphical installer, but it will give you a general gui after installing (like gnome or kde, whatever you select)

---

### Post by rhcm123 on 2009-02-20
> **magnoliasouth said:**
> Okay. Number 3 sounds Greek to me. I've no idea what a server edition is.

A question about number 2: Can I run Wine and more specifically World of Warcraft on this? (The main use for this computer is strictly for one user to log onto WoW. We don't need a new gaming computer, just have access every now and then.)

What do you think is our best and most easy for newbs option?

I loled when i read the words wine and world of warcraft in the same sentance. Wine can't do that. Sorry to be blunt, but no, it can't. I cant even get minesweeper running! That, my friend, is windoz's domain... and why i keep it around.

Edit: The easiest way would actually be to get the Ubuntu alternate install (as you have the power :) ) and run that to get ubuntu going

> **soxs said:**
> Just donwload the installer for servers. It will have all features the normal edition has, except graphical installer, but it will give you a general gui after installing (like gnome or kde, whatever you select)
assuming you install one

---

### Post by anewguy on 2009-02-20
The server editions are leaner versions of the operating system, particularly geared for running a server - a computer that holds files, perhaps printers, cd drives, etc., that are then accessed across a network from another computer.  Server editions do not include any form of GUI'd environment, so it would be command line based, not window based.  For what you want to do, you will need a version that will run windowed (not Microsoft, just not the command line).

For that reason, and given the problems you are having, I would follow the previous advice and try the alternate CD first.  It does not use a true graphical interface to do the installation, so it may work around your problem.  

My suspicion, however, is that you need a video driver in order for xwindows to work and not show a black screen.

In that regard, please try the following and post the results back here for us to check:

(1) boot up until you get the black screen

(2) press ctrl/alt and F1.  This will open a non-GUI command line window, commonly called a terminal window in Linux.

(3) log on using your normal username and password

(4) type:

lspci <press enter>  This will list all of the known PCI hardware on your system.  If your video is PCI based, the card/type will show in this output for us.

lshw -C video <press enter>  This will also list just the video hardware on your system.

Copy the output from both, then post that back here for us to work with, and we'll go from there.

Dave :)

EDIT:  You can run WOW in Linux - whether it needs wine or not I don't know - but there is another Ubuntu forum (gaming??) where the success/failure/things you have to do are discussed.  We just need to get your GUI'd environment working first.

---

### Post by Mercury_Alpha on 2009-02-20
> **rhcm123 said:**
> I loled when i read the words wine and world of warcraft in the same sentance. Wine can't do that. Sorry to be blunt, but no, it can't.

Wine runs WoW just fine, in my experience. You may have to do some additional fiddling with the in-game graphical settings, but it's perfectly doable.

---

### Post by Therion on 2009-02-20
Something to at least try.

EDIT:  Nevermind... OP is using Intrepid.

---

### Post by SunnyRabbiera on 2009-02-20
why are we suggesting a server disk all of the sudden?

---

### Post by magnoliasouth on 2009-02-20
> **rhcm123 said:**
> I loled when i read the words wine and world of warcraft in the same sentance. Wine can't do that. Sorry to be blunt, but no, it can't.Really? I was going by [this page]("https://help.ubuntu.com/community/WorldofWarcraft") that says:
[INDENT][I]Wine is a free open source implementation of the proprietary Win32 API, and attempts to enable Windows applications and games to run on Unix-like operating systems.

World of Warcraft can also be played under Ubuntu by using the Wine based CrossOver Games, Cedega and PlayOnLinux.[/I] [/INDENT]So you're saying it won't?

---

### Post by rhcm123 on 2009-02-20
> **magnoliasouth said:**
> Really? I was going by [this page]("https://help.ubuntu.com/community/WorldofWarcraft") that says:
[INDENT][I]Wine is a free open source implementation of the proprietary Win32 API, and attempts to enable Windows applications and games to run on Unix-like operating systems.

World of Warcraft can also be played under Ubuntu by using the Wine based CrossOver Games, Cedega and PlayOnLinux.[/I] [/INDENT]So you're saying it won't?


Well, atleast mine wont... it won't even play Age of Empires II. Otherwise i would have killed windows a long long time ago.


EDIT:
Oh, your talking about Cedega! That's different. That's WINE-based, it's not actually WINE. It's another package geared for gaming.

EDIT2:
> **SunnyRabbiera said:**
> why are we suggesting a server disk all of the sudden?
Cause i mentioned that she can install the server os then install the GUI from the command line.

---

### Post by Therion on 2009-02-20
One of several "How To's" on the forums specifically about getting WoW up and running under Wine:

[http://ubuntuforums.org/showthread.php?t=1067936&highlight=World+Warcraft](http://ubuntuforums.org/showthread.php?t=1067936&highlight=World+Warcraft)

I dual-booted when I was still gaming, but to each their own.

---

### Post by rhcm123 on 2009-02-20
> **Therion said:**
> One of several "How To's" on the forums specifically about getting WoW up and running under Wine:

[http://ubuntuforums.org/showthread.php?t=1067936&highlight=World+Warcraft](http://ubuntuforums.org/showthread.php?t=1067936&highlight=World+Warcraft)

Shoulden't we be worried about getting linux working first? :) :KS

---

### Post by magnoliasouth on 2009-02-20
> **anewguy said:**
> The server editions are leaner versions of the operating system, particularly geared for running a server - a computer that holds files, perhaps printers, cd drives, etc., that are then accessed across a network from another computer.If this is the case, then this is not what I am looking for.

I want it to be a computer, plain and simple. It is not going to be accessed by another computer and I'm not entirely sure how this conclusion came to be. I only asked what a server edition was, I wasn't interested in it at all. I'm trying to figure out what edition would suit our needs.

All I want to do is install Ubuntu on a wiped clean computer that has no OS at all. I tried to install, but as in my OP I had problems. 

This computer will be used as a computer, but the primary function will be for my husband to play WoW with our kids online. It won't need to be a high quality gaming computer, but we just want to be sure that this one particular thing can be done.

Hopefully this clarifies things.

---

### Post by Therion on 2009-02-20
> **rhcm123 said:**
> Shoulden't we be worried about getting linux working first? :) :KS
Probably.

---

### Post by rhcm123 on 2009-02-20
> **magnoliasouth said:**
> If this is the case, then this is not what I am looking for.

I want it to be a computer, plain and simple. It is not going to be accessed by another computer and I'm not entirely sure how this conclusion came to be. I only asked what a server edition was, I wasn't interested in it at all. I'm trying to figure out what edition would suit our needs.

All I want to do is install Ubuntu on a wiped clean computer that has no OS at all. I tried to install, but as in my OP I had problems. 

This computer will be used as a computer, but the primary function will be for my husband to play WoW with our kids online. It won't need to be a high quality gaming computer, but we just want to be sure that this one particular thing can be done.

Hopefully this clarifies things.

Well you can use the server OS to get a desktop by installing a >1000 MB virtual package, but let's not worry about that. Try the alternate install CD first. Then we can worry about getting your wine on (i just read that again and loled) :)

---

### Post by Mercury_Alpha on 2009-02-20
> **magnoliasouth said:**
> Really? I was going by [this page]("https://help.ubuntu.com/community/WorldofWarcraft") that says:
[INDENT][I]Wine is a free open source implementation of the proprietary Win32 API, and attempts to enable Windows applications and games to run on Unix-like operating systems.

World of Warcraft can also be played under Ubuntu by using the Wine based CrossOver Games, Cedega and PlayOnLinux.[/I] [/INDENT]So you're saying it won't?

Oh, it works. Like I said, it usually takes some fiddling, but I've done far hairier things in Linux than this.

---

### Post by rhcm123 on 2009-02-20
> **Mercury_Alpha said:**
> Oh, it works. Like I said, it usually takes some fiddling, but I've done far hairier things in Linux than this.

nice screenshot! :) KDE?

---

### Post by magnoliasouth on 2009-02-20
> **rhcm123 said:**
> Well you can use the server OS to get a desktop by installing a >1000 MB virtual package, but let's not worry about that. Try the alternate install CD first. Then we can worry about getting your wine on (i just read that again and loled) :)That is funny. I just read it to my husband and he got a kick too.

Okay, thanks on the alternate. That's what I'm downloading now. Do I burn like the other one? I used Infrarecorder. I burn it as an image too?

Sorry if I sound dense, but my head is aching from trying to follow this. :oops:

---

### Post by Mercury_Alpha on 2009-02-20
> **rhcm123 said:**
> nice screenshot! :) KDE?

Thanks :) It's actually Gnome -- I just removed the top panel and moved a few things that were up there to the bottom panel. The button on the far right is basically a kicker for Gnome. At this point, it actually looks a lot more like the Windows task bar than either Gnome or KDE :(

---

### Post by rhcm123 on 2009-02-20
> **magnoliasouth said:**
> That is funny. I just read it to my husband and he got a kick too.

Okay, thanks on the alternate. That's what I'm downloading now. Do I burn like the other one? I used Infrarecorder. I burn it as an image too?

Sorry if I sound dense, but my head is aching from trying to follow this. :oops:

Sorry about giving you a headache. :( Drink some caffeine, that opens blood vessles and typically relives my headaches (that's why it's in excederin.)
Yes, just burn the alternate like the regular CD, then drop it in and follow the prompts. 

It looks A LOT different than the LiveCD (there is no liveCD and this disk will only INSTALL ubuntu) but it is still very easy to use.  Post back if you have problems.

> **Mercury_Alpha said:**
> Thanks :) It's actually Gnome -- I just removed the top panel and moved a few things that were up there to the bottom panel. The button on the far right is basically a kicker for Gnome. At this point, it actually looks a lot more like the Windows task bar than either Gnome or KDE :(

I need a new computer :). Thanks for the ideas... i might wanna play around with KDE later though... who knows :)

---

### Post by anewguy on 2009-02-20
Given the computer specs, you will probably still get the black screen.  If you do, follow my previous post and type the commands and copy the output here for us.  I still suspect you are going to need a video driver.

Dave :)

---

### Post by magnoliasouth on 2009-02-20
Yeehaw!!! I'm in Ubuntu business. We've got it up and running and I LOVE it! We've already installed flash to get youtube working. ;)

Now we're off to figure out the WoW thing.

Thanks so much to everyone for the help. You've been a Godsend! :KS

---

### Post by Mercury_Alpha on 2009-02-20
The first thing I would recommend doing is adding the Wine beta repository. The version of Wine that comes with Ubuntu is fairly old, and every Wine update seems to include a fix for WoW.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by rhcm123 on 2009-02-20
> **magnoliasouth said:**
> Yeehaw!!! I'm in Ubuntu business. We've got it up and running and I LOVE it! We've already installed flash to get youtube working. ;)

Now we're off to figure out the WoW thing.

Thanks so much to everyone for the help. You've been a Godsend! :KS

It's how we roll.:D

I think sombody posted a link to a guide in this thread about getting wow up and running.. Might have been the poster above me

---

