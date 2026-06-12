---
title: "Is it safe to upgrade to 11.04"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by itsols on 2011-05-16
My laptop: Dell Inspiron 1150 - 2.8GHz P4, 512RAM, 80GB HDD. Intel 855 graphics.

Current OS: 10.04; moved all the way from version 5, 7.x, 8.x and 10.04.

My question: Is it safe to hit the UPGRADE button on Update manager and install 11.04?

Reason for fear:

1. As it is I cannot run any UI animations.
2. Many games are pretty slow.
3. This is my development and official machine: running LAMP stack, C++, Pascal, Lazarus (very slow), Open Office, Gimp, InkScape, Skype, MonoDevelop (C#), etc.
4. The BIGGEST ISSUE: I have another PC with a similar config. Did the upgrade. Never booted. Lost all work on it. Then had to do a fresh installation.

So has anyone else done this upgrade and got sailing?

Thanks!

EDIT: This is also Dual boot with XP but it's hardly ever used

---

### Post by beew on 2011-05-16
Don't do it. The hardware sounds pretty weak for 11.04 and Natty is beta software based on countless testimonies on this forum. I cannot see what you have to gain by upgrading.

And if you must, I suggest a fresh install instead of upgrade.

---

### Post by wojox on 2011-05-16
Technically you would be updating to 10.10

Download a copy of Natty and burn it to a USB and try it out first.

---

### Post by itsols on 2011-05-16
Yup, I always had the feeling of uncertainty with the new upgrade. One of the key reasons I stuck to Ubuntu was the need for less resources. But I guess that story is a thing of the past.

Now about the pen-drive installation; Will it be writing any changes to the disk (even for a swap)? I don't want to mess up my current installation of Ubuntu. I don't mind losing Windows but my work is on Ubuntu.

Thanks!

---

### Post by NCLI on 2011-05-17
> **itsols said:**
> Yup, I always had the feeling of uncertainty with the new upgrade. One of the key reasons I stuck to Ubuntu was the need for less resources. But I guess that story is a thing of the past.

Now about the pen-drive installation; Will it be writing any changes to the disk (even for a swap)? I don't want to mess up my current installation of Ubuntu. I don't mind losing Windows but my work is on Ubuntu.

Thanks!

No, booting from a live usb or cd doesn't so much as touch your hdd. Also, while upgrading between releases could potentially ruin your install, it is very unlikely to destroy your data. You can always just boot from a live cd or usb, plug in an external hdd, and copy all of your data over there, even if your computer can't boot from the hdd after an upgrade.

---

### Post by itsols on 2011-05-17
Thank you all for your inputs.

An error on my part: I am NOT on 10.04. It's 10.10. And since this is not LTS, I'll have to move to whatever other version by April next year.

As for 'copying' my files over, it's easy said than done :)

I have loads of work including MySQL DB tables, saved passwords, etc. So I guess the usual 'backup before anything' rule applies here ;)

And I cannot forget the horrified moments the day I move to Ubuntu 8.04 - how it destroyed my settings and Gnome never started.

To add to my fear, I've just learnt that Unity requires a minimum of 1GB RAM. So I guess it's not too far before I say bye to my old laptop :)

Or maybe I'll use it as an in-house server - smiles...

Thanks again for all the feedback!

---

### Post by NCLI on 2011-05-17
> **itsols said:**
> Thank you all for your inputs.

An error on my part: I am NOT on 10.04. It's 10.10. And since this is not LTS, I'll have to move to whatever other version by April next year.

As for 'copying' my files over, it's easy said than done :)

I have loads of work including MySQL DB tables, saved passwords, etc. So I guess the usual 'backup before anything' rule applies here ;)

And I cannot forget the horrified moments the day I move to Ubuntu 8.04 - how it destroyed my settings and Gnome never started.

To add to my fear, I've just learnt that Unity requires a minimum of 1GB RAM. So I guess it's not too far before I say bye to my old laptop :)

Or maybe I'll use it as an in-house server - smiles...

Thanks again for all the feedback!

Unity 3D recommends 1GB of ram,  yes, but 11.04 has Ubuntu Classic as a low-power fallback and 11.10 will have Unity 2D.

---

### Post by jtarin on 2011-05-17
> **itsols said:**
> My laptop: Dell Inspiron 1150 - 2.8GHz P4, 512RAM, 80GB HDD. Intel 855 graphics.

Current OS: 10.04; moved all the way from version 5, 7.x, 8.x and 10.04.

My question: Is it safe to hit the UPGRADE button on Update manager and install 11.04?

Reason for fear:

1. As it is I cannot run any UI animations.
2. Many games are pretty slow.
3. This is my development and official machine: running LAMP stack, C++, Pascal, Lazarus (very slow), Open Office, Gimp, InkScape, Skype, MonoDevelop (C#), etc.
4. The BIGGEST ISSUE: I have another PC with a similar config. Did the upgrade. Never booted. Lost all work on it. Then had to do a fresh installation.

So has anyone else done this upgrade and got sailing?

Thanks!

EDIT: This is also Dual boot with XP but it's hardly ever usedI cannot believe after what you have experienced and quite possibly seen in posts on the boards.......you would even ask are you crazy????..........SURE DO IT!!!!!!!GO FOR IT!!!!!! **[SIZE="3"]BUT BACKUP FIRST!!!![/SIZE]**:P

---

### Post by itsols on 2011-05-17
jtarin, you make a lot of sense - I should just dive in... But I thought I'd first learn what experiences others have with the upgrades, as opposed to a fresh install. After all, if a fresh install fails, you just re-install the older version or ditch the machine. But Upgrades are different... My TWO key concerns now are:

1. Will my hardware support 11.04? This is why I look forward to the experiences of the community.

2. The reason I go for upgrades rather than fresh installations, is to allow for least interruptions and continuity of work. If it weren't for these, I'd jump in for an install.

Thanks again for sharing your thoughts...

---

### Post by wildmanne39 on 2011-05-17
> **itsols said:**
> jtarin, you make a lot of sense - I should just dive in... But I thought I'd first learn what experiences others have with the upgrades, as opposed to a fresh install. After all, if a fresh install fails, you just re-install the older version or ditch the machine. But Upgrades are different... My TWO key concerns now are:

1. Will my hardware support 11.04? This is why I look forward to the experiences of the community.

2. The reason I go for upgrades rather than fresh installations, is to allow for least interruptions and continuity of work. If it weren't for these, I'd jump in for an install.

Thanks again for sharing your thoughts...
Hi, just make sure you do not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all.

---

### Post by mastablasta on 2011-05-17
hmm for production maschines LTS is recomended. 10.10 and upragdes are only needed for fun and if your hardware is not supported in lower version and it is supported better in new verison of the OS.
 
heh i knwo people that are still on 9.10 as uprading/reinstall would ause too many issues.
 
i mean if it works for what they need it, then why not??
 
otherwise form 10.04 it is possible to upgrade to 10.10 and later to 12.04LTS
form 10.10 you can only upgrade to 11.04. well the rest you know...

---

### Post by itsols on 2011-05-17
mastablasta, I fully agree with you. In fact until last October/November I only used LTS versions all the way from 5,7,8 and 10.04.

My laptop's hard disk crashed and I really didn't pay attention to 10.10 not being LTS.

My bigger fear is this... I don't mind just using my current version. But at the rate security updates and patches keep being released, I don't think I'd want to risk using the OS without updates. So the moment updates for this version stop, I have to somehow either upgrade or get a new machine.

Anyway, your thoughts are well appreciated.

---

### Post by Zill on 2011-05-17
> **mastablasta said:**
> ...i mean if it works for what they need it, then why not??...
The voice of sanity. ;-)

Unless you actually *need* to upgrade to a later release then why do it?

10.10 is [supported]("https://wiki.ubuntu.com/Releases") until April 2012, which is when 12.04 LTS is [scheduled]("https://wiki.ubuntu.com/PReleaseSchedule") to be released.

If your system works reliably then don't fix it :-)

Top-tip:  *Always* test your hardware with a Live CD *before* installing and don't even think about upgrading without having all your data backed-up!

---

### Post by itsols on 2011-05-17
Thanks Zill... Wait... Oh no!!! There's no LTS this year??!!@!#

So I guess it's back to 10.04 LTS or wait till April/May next year!

Tanks again folks!

---

### Post by norville05 on 2011-05-17
11.04 will also recognize if you cannot run Unity and put you into Classic mode and tell you to do this from now on.  It is always worth attempting (on a flash drive).

---

### Post by cmcanulty on 2011-05-17
One related question. If I go to 11.04 with gnome classic will I be able to save or redo all me panel icons? I have a ton and love getting to everything IO use with one click which is certainly a big mess in Unity.

---

### Post by beew on 2011-05-17
> **mastablasta said:**
> hmm for production maschines LTS is recomended. 10.10 and upragdes are only needed for fun and if your hardware is not supported in lower version and it is supported better in new verison of the OS.


That depends. 10.10 is not LTS but I find it more stable, less buggy and faster than 10.04 (which is very good too) I use it on my production machine. 

So I don't go by the simple criterion of whether a release is LTS or not. Quality of releases differs. Instead I do a full install of a new release on an external hard drive and do extensive testing and then I will decide whether to update the OS (always clean install, I don't do "upgrade")

I have tested 11.04 extensively this way too (and still am testing). My conclusion is that it would actually be a downgrade comparing to 10.10. But in any case this is not a real decision for me because I don't need to upgrade, 10.10 is as close to perfect for me as possible and it is only 6 months old. I keep my softwares up to date with ppas so why switch? 

I think a big mistake for many people is to schedule their OS update/upgrade based on Ubuntu's release cycle. It is insane to overhaul and reinstall your OS every 6 months unless there is a compelling reason to. That there is a newer release is not a compelling reason.

---

### Post by Bapun007 on 2011-05-17
If your system works then stick with LTS verson like me .

---

### Post by beew on 2011-05-17
> **norville05 said:**
> 11.04 will also recognize if you cannot run Unity and put you into Classic mode and tell you to do this from now on.  It is always worth attempting (on a flash drive).

Like I said 10.10 is good and it outperforms 10.04 for all the machines I have tested on.

---

### Post by Joliea on 2011-05-18
So seems most people are agains't upgrading to 11.04. I did and i am already finding bugs.

1. on some levels its hanging. can't explain further since it happened a while back and i can't recall exactly what happened.
2. some apps (i use destroytwitter) hangs sometimes. its annoying

when i remember some i will update. one thing i know is that, for me, i like change and this new one is nice. i just have to get used to going left for the panel instead of below. can be boring especially when you're right handed! anyway!

my 5 cents.

---

### Post by itsols on 2011-05-18
Joliea, your input was super useful! This is the kind of stuff I wanted to hear. 

Now putting all the responses together, I have ONE thought - I'll not upgrade to 11.04. I'd rather wait for the end of cycle in April :)

And since you mentioned it, I just HATE the thought of the LEFT PANEL. I want all my items to be readable at a glance. If for example, I use GEdit for LAMP development. I use multiple editors with each one having multiple tabs and 'sessions'. I need to see them spread out and readable. So for me the fancy Unity interface is a no go.

Maybe for a light user with just a couple of apps open, the left panel is good.

To me, the left panel or whatever it's called, looks like the unsuccessful (IMO) dock from apple. Once again, it's 'cute' and 'flashy' but not productive in the least. Gnome stays!

Now, I don't want to make this a debate, I just highlighted your points. This is really out of context :)

---

### Post by Joliea on 2011-05-19
Yes itsols.

There is a lot of borrowing from Apple. Like they've made the top panel to look like apple, where the menu bar is accessible there too, by hovering your mouse over it.

Again, the left panel needs some getting used to, how to manipulate it to fit your needs. Took me a while to know how to move the icons around to an arrangement I'm comfortable with. I had to un-pin an icon and re-pin it to the position I want it to go. And yes, I am a light user so not many icons there. I tried making the panel go below but didn't know how.

I do like the new look though. Its quite different and thus needs a patient heart. I just hope they fix the bugs here and there.

Something else the new Natty doesn't have is a "show desktop" button for minimizing and maximizing all open windows at once.

---

