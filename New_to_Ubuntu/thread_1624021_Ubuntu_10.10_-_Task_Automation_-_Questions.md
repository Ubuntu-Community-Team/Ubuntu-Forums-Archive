---
title: "Ubuntu 10.10 - Task Automation - Questions"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Dark7man on 2010-11-17
Hey everyone!  First off I'm a complete noob to linux! I've played around with various live CD's before and tried installing a few distros before but due to hardware issues I decided to leave things a little longer... I'm now using Ubuntu 10.10 on my HP dv6 1340sa laptop and dual booting with Windows 7 (Both OS 64bit)

I had, which seems a well known issue with the Broadcom BCM4312 WLAN chip but that's all sorted now after a 4 days of playing around and 3 Fresh installs of Ubuntu later! #-o lol

**[COLOR="Navy"]My question..[/COLOR]** I'd like to try some automated task software (not sure thats the right term-hey I'm a noob to this :))

I'd like to basically - have an application.. click record - click around for example... change my sound output from my laptop speakers to my HDMI port... and configure my screen to switch of the laptop screen and use my HDTV instead.. And when all the messing around is done... hit Stop Recording.. and be able to save the file as some kind of executable or script that runs.. with a nice shortcut that I can place on my panel or desktop...
I have a few other ideas I want to use it for... so basically I can have it set to automate opening GShutdown and start the countdown...turn down the volume a bit etc... and suggestions as to what software I'm looking for would be greatly appreciated! :)

I posted on one of the bug threads by the way how I got my WLAN card work no prob btw incase anyone still has this issue.  Search google or the board something like "BCM4312" and "Dark7man" might bring it up... Be near the bottom some where! :)

Thanks in advance!
Cant wait to get more familiar with Ubuntu - its already been 5days since I logged into Windoze... and think it could stay that way... loving the freedom of Ubuntu! :guitar:

Regards
~Dark

---

### Post by Dark7man on 2010-11-17
I've read the post by peterrudin " [ubuntu] Automation software - suggestions wanted "  but it seems his aim is different from mine!  Still looking...

---

### Post by realzippy on 2010-11-17
Welcome to UF !

And then you would create a starter which runs all that recorded mouse/keyboard commands?
Do not know about such an app;others will.
But that idea has a taste of ugly workaround,most things you want to be done could be run with a command(s) on the shell,triggered by starter on your Desktop.
E.g. *xrandr* has all the options for switching laptop panel/HDTV,or twinview aso...
Gshutdown only is a GUI for the *shutdown* command,which also
has bunch of options...
What exactly do you want to do ?

---

### Post by Dark7man on 2010-11-17
I think its best if I explain my goal to begin with... I'm lying in bed... watching a movie or whatever... I would like that in one click or execution that it would setup GTimer for a set amound of time... EXAMPLE:
1 icon for "Shutdown in 30mins"
1 icon for "Shutdown in 1Hour" etc. etc

But if I ever come across another task I'd like automated... I could almost start recording.. and say for example... send a few daily emails or check for updates etc... hit "stop recording" and then have this 'script' saved on the desktop for future use...

I have been reading around today and some guys have gave me a little advice on reading up on BASHScripting and Shell Scripts.. like You have also suggested. I think this is a place where I should start... going to need to learn myself anyway.. I was just asking incase there has already been something like this made by someone who has wanted similar things.  I appreciate Your speedy reply.. :) You think I'm heading in the right direction?

---

### Post by realzippy on 2010-11-17
For the shutdown command you need "sudo"  and your password.
You can change* this,[open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal"),type:

```
sudo chmod +s /sbin/shutdown
```

Now you can shutdown without password e.g. in 30 minutes

```
shutdown +30 -h
```
Create a starter:
rightclick Desktop,create Launcher
Command:
   *shutdown +30 -h*    
(or:
   *shutdown* +1 -h
 for a quick test)

Type: 
application

otherwise a terminal pops up.
Name it what you want.

**note that then everbody (e.g. multiuser machine) can shutdown your machine,a disadvantage/security lack.Theoretically...*

---

### Post by Dark7man on 2010-11-18
> **realzippy said:**
> For the shutdown command you need "sudo"  and your password.
You can change* this,[open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal"),type:

```
sudo chmod +s /sbin/shutdown
```

No you can shutdown without password e.g. in 30 minutes

```
shutdown +30 -h
```
Create a starter:
rightclick Desktop,create Launcher
Command:
   *shutdown +30 -h*    
(or:
   *shutdown* +1 -h
 for a quick test)

Type: 
application

otherwise a terminal pops up.
Name it what you want.

**note that then everbody (e.g. multiuser machine) can shutdown your machine,a disadvantage/security lack.Theoretically...*

HOLY SMOKE DUDE! =D>  \\:D/  :D

Sorry about the delayed reply! I'm just getting online 1st time today and got a ton to catch up on!  From what I've seen... You've made my day..It looks perfect, just what I'm after... I want to play and build on this idea with a few things!

I've got a few pointers and tips from another guy on learning how to make scripts and learn about BASH commands and the rest of it! I'm a complete noob! Linux ROCKS though, I wish I'd got on board sooner! Love the Freedom - its the future! :guitar: 

I will post back with an update amigo - Seriously appreciate You help! :)
~TS

---

