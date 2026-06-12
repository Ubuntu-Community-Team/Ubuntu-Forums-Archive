---
title: "Options for installing on a shared computer?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by TheGrimSqueaker on 2008-12-31
I burned a Ubuntu Live CD today, and I've been playing around with the system a bit. So far, I really like it, and I'm considering going all the way and installing it for real. I just have one problem: I share the computer with the rest of my family, and they would be, shall we say, *less than happy* to discover that I had changed the default operating system, God forbid overwritten it entirely. (I can't blame them; I would be pissed off too. But our current OS (Windows XP) sucks balls, and it would be nice to at least have some other options.)

I know that I can either partition the hard drive & set up a dual boot, or install to an external drive & manually boot from that. But this is my first time doing something like this, so I'm not sure which would be better. (I don't want to wing it, and risk screwing the computer up) 

Can someone please help me? :confused:

-Grim

(PS: For reference, if I were to go with the external drive, I would be installing to a 500 GB USB hard drive. For a dual boot setup, I would use the computer's internal drive, which currently has 103 GB of free space (Out of 127 GB). Also, sorry if I used the wrong terms for anything in this post, or if my question was completely stupid. ^^; Like I said, I'm just getting started with this sort fo thing, so please be patient towards my n00b-ishness)

Edit: Thank you so much for all the responses. I'll give Wubi a try, and if I need any help I'll post back here.

---

### Post by Paqman on 2008-12-31
First of all: do you have the permission of the computer's owner to install a new OS?

If they say no, that's the answer. Sorry.

However, you might want to let them know that installing Ubuntu is very, very low risk. Use the Wubi install method and you won't even need to do any potentially risky disk partitioning.

If they do let you go ahead, **back up everything** before proceeding.

---

### Post by abn91c on 2008-12-31
install using the wubi option

---

### Post by wkuace on 2008-12-31
i'm new to linux too, and i also share my laptop alot with my family. I thought about a duel boot after playing with the live cd. If you have High speed internet and a decent computer I suggest Wubi i'm using it. Wubi basically installs ubuntu in windows but when you start your computer you choose to boot into windows or ubuntu. I don't know if it works with XP but it works well with Vista and i'm loving it. wubi will take about 30 min to install even with highspeed but its the simplest way to set up a duel boot. I did it and i hardly know what i'm doing :lolflag: the best part is if you don't like it boot into windows and delete like any other program its that simple. Good luck!

ps by default wubi will cause windows to boot after 10 sec on the boot menu

---

### Post by Michael.Godawski on 2008-12-31
Back up first.

Ask for permission. Back up.

Try Wubi first. If you like it, set up a dual boot.


[LIST]
[*][http://godawski.oxyhost.com/switch.html](http://godawski.oxyhost.com/switch.html)
[/LIST]
Before installing Ubuntu for real on the drive consult us, asking every question you want, so that there are no doubts. :D And all will be fine.

---

### Post by NightwishFan on 2008-12-31
I think Wubi is a good option for a trial period. If no one relies on a Windows Centric app, or if they all work in Wine. Try wubi for a week or so, and if everyone is happy ask if you can go full Ubuntu or a dual-boot. (Which is easier than it sounds)

Please ask if you need any more advice although I will be here only for half an hour.

---

### Post by TheGrimSqueaker on 2008-12-31
I checked before making the thread, and my dad's fine with it, so permission isn't a problem. 

I haven't heard of Wubi before, but I'm sort of relieved. I didn't really want to risk messing around with that sort of thing. XD 

I'm backing up now, but it looks like it's going to take a while. Could you tell me what to do when it's finished?

---

### Post by NightwishFan on 2008-12-31
For Wubi: Simply insert the CD while in Windows, and when the popup comes up, choose Install Inside Windows.

If your games are supported in wine and you do not rely on Microsoft products, I advise you go with the full install. The main downside is you will quickly grow bored with the stability of the new system. :D

To see if games work in wine:

[http://appdb.winehq.org/](http://appdb.winehq.org/)


Feel free to drop me a line, and any of the other fine people on this forum will be glad to help. Hope it all works out fine!

---

### Post by Paqman on 2008-12-31
> **TheGrimSqueaker said:**
> 
I'm backing up now, but it looks like it's going to take a while. Could you tell me what to do when it's finished?

Double-check your backup. Make sure it's got everything in there (easiest way is to image the whole disk)

Then just pop your LiveCD in while in Windows, when it autoruns click on the option to install from within Windows. Give Ubuntu about 20GB or more, pick your favourite desktop environment then go make a cup of tea. By the time you've drunk it you should have a nice dual-boot system.

---

### Post by abn91c on 2008-12-31
get wubi from here [http://wubi-installer.org/](http://wubi-installer.org/)
also when you insert the cd in windows you can select "Install inside Windows" option.
Make sure you defrag windows first and avoid hard reboots when starting wubi

---

### Post by wkuace on 2008-12-31
google wubi and install the app i think its about a meg. the run it you can choose ubuntu kubuntu,or a couple others if you've used the ubuntu live cd i suggest you choose ubuntu, i chose to use 8 gb in the option that in set to 15 gb the popup menu said 8 was "comfortable" and i left it in the c drive. for my computer. it will use you windows log in as a screen name. then you have to set a password and hit ok. Wubi will download about 700 mb of files so it will take along time (around 30+ min) then you have to restart and it will go to a bootloader where you can select ubuntu. choose it and it will continue the install (another 5-10 min) then you will log in.

ps if it freezes during the black ubuntu load screen restart the computer and when the progress bar starts push control+alt+f2. Found that one out the hard way :)

pps it maybe different in xp i used vista and it was pretty easy

---

### Post by TheGrimSqueaker on 2008-12-31
Thanks, Paqman! Hopefully, I'll be able to get it up and working before the end of 2008~

---

### Post by Keen101 on 2008-12-31
If it were me, i'd carefully unplug the internal hard drive, and boot the live-Cd and install to an external drive. Pretty easy, and won't risk messing up windows. Then just set BIOS to boot from USB before the other drive.

other than that you could try WUBI or VirtualBox.

---

