---
title: "Screen Error: ???"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-06-16
Alright, I have had Ubuntu 10.04 installed for a few days now. I think that Ubuntu is really cool, And I am thinking about making a permanent switch. There is one thing stopping me doing so; a screen error.

System Specs:
[View it here.]("http://dageek247.cwahi.net/pages/hardware_info.html")
I got the HTML file from this code:
sudo lshw -html > ~/hardware_info.html && firefox  ~/hardware_info.html

My Problem:
Every time I leave the computer on with out messing with it, it goes into a repeat stage:
it shows some text that is way off center from the screen.
it shows bars on the screen.
it repeats.
Whenever the error occurs, the running programs still work, but I cannot change anything. the only way to get rid of it (that i know) is to press the power button on my computer. then it turns off normaly.
the error also shows whenever the screen res changes, I open up the screen saver 
client, or when I play specific games that change screen res.

any help?
also, is there a way to remove the screen saver from running, without going to System > Preferences > Screensaver? so that my computer doesnt stop working when i leave it alone to do something? like say, a terminal bit of code?

---

### Post by marshmallow1304 on 2010-06-16
I don't know about your main problem, but I can help with a couple other things.

1) If you experience that problem or any lockup, there there are safer methods than holding the power button.
[INDENT]a) First, you should try Ctrl+Alt+F1 to see if you can drop to the console, where you can log in and use
```
sudo shutdown -r now
```
or
```
sudo reboot
```
to reboot.

b) If that doesn't work, you can use the ["Magic" SysRq key]("http://lifehacker.com/298891/gently-restart-a-frozen-system").  Hold down Alt+SysRq and type r-e-i-s-u-b, waiting for hard drive activity to subside after each.[/INDENT]

2) You can indeed prevent gnome-screensaver, which I assume you use (it's the default), from activating:
```
gnome-screensaver-command -i
```
will inhibit the screensaver while it (the command) is active.

---

### Post by DaGeek247 on 2010-06-16
> If you experience that problem or any lockup, there there are safer  methods than holding the power button.I don't HOLD down the power. I just press it once and the shutdown screen shows. then the computer powers down.

> You can indeed prevent gnome-screensaver, which I assume you use (it's  the default), from activating:Thanks, but when I installed Ubuntu I messed with the screen saver and switched it the spider one. (before the ever-present error showed) is there code to stop the spider screensaver?

> First, you should try Ctrl+Alt+F1 to see if you can drop to the console

No that didn't work. :-\

---

### Post by Zeike on 2010-06-16
> **DaGeek247 said:**
> Thanks, but when I installed Ubuntu I messed with the screen saver and switched it the spider one. (before the ever-present error showed) is there code to stop the spider screensaver?


Can you provide more information about this spider screensaver?

---

### Post by DaGeek247 on 2010-06-16
Um I didn't actualy download it, it is one of the preloaded spider screen savers. it is just a 3D spider that spins. (i think, i only got to see the first two seconds of it.)

---

### Post by Zeike on 2010-06-16
It sounds like you're still using gnome-screensaver.

It might help if you did disable it.  I know that I have experienced freezes using some of the screensavers included with gnome-screensaver, particularly the openGL ones (the ones prefaced with "GL", ex "GLCells")

---

### Post by DaGeek247 on 2010-06-16
marshmallow1304 said that the code only works when it is running. i=s there a way to put that code in .bat file (Or whatever the terminal files are called) and run every startup? also could i hide the running program so its like its not there? (visibility wise)

---

### Post by Zeike on 2010-06-16
If you go to System->Preferences->Startup Applications there should be an entry for the screensaver daemon.  Simply uncheck it.

---

### Post by DaGeek247 on 2010-06-16
> **Zeike said:**
> If you go to System->Preferences->Startup Applications there should be an entry for the screensaver daemon.  Simply uncheck it.
Although that would be nice, the Screen saver Deamon does not show up there.

---

### Post by marshmallow1304 on 2010-06-18
> **DaGeek247 said:**
> Although that would be nice, the Screen saver Deamon does not show up there.

How about unchecking the "Activate screensaver when computer is idle" box in Screensaver Preferences?

---

### Post by DaGeek247 on 2010-06-29
> **marshmallow1304 said:**
> How about unchecking the "Activate screensaver when computer is idle" box in Screensaver Preferences?

 I believe that to do that I would have to access System > Preferences > Screensaver.  So it wouldn't really work. Any other advice? 

I need a fix that will fix it. one that doesn't mess with the "side effects" of the problem. :mad: How do I fix it so that the error never shows up? I read some where that like 90% of the errors in Linux are from bad hardware drivers, not the OS itself. Can anyone help find a permanant work-around for this?

---

### Post by DaGeek247 on 2010-08-18
bump.

---

### Post by Zorgoth on 2010-08-18
So your screensaver crashes your computer even when set to "blank screen?"

Because your description sounded like a graphics driver bug, and graphics driver bugs can be caused by 3D spiders.

---

### Post by DaGeek247 on 2010-08-18
I can't set it to blank screen. it crashes when i open up the options window. I posted this a while ago, so I am agreeing with you when you say it has something to with the graphis card, one problem: i don't have one.

see?
[http://dageek247.cwahi.net/pages/hardware_info.html](http://dageek247.cwahi.net/pages/hardware_info.html)

---

### Post by Zorgoth on 2010-08-18
irq	:	0
memory	:	f8000000-fbffffff(prefetchable)
id:	
display
description: 	VGA compatible controller
product: 	82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	f0000000-f7ffffff(prefetchable)
memory	:	ffa80000-ffafffff

You have this here graphics card.

---

### Post by Zorgoth on 2010-08-18
This might work to disable your screensaver:

Alt-F2 gconf-editor

navigate to /apps/gnome-screensaver

Change the following keys (if they are not already like this):

theme should be 'screensavers-ubuntu_theme'
themes should be '[]'
mode should be 'blank-only'

of course they do not have quotes in them

---

### Post by DaGeek247 on 2010-08-18
Yep, they are all set like that, and i didn't have to make any changes.

---

### Post by Zorgoth on 2010-08-18
As for apps other than the screensaver doing this...

You can try to fix your graphics issues, but that is a *very* old computer and I wouldn't give you a high success chance.  Even the lowest-end computer you can buy now (excluding Atom-powered devices) will be a few times faster.  My laptop's processor is about 10 times faster.  The graphics are ancient and it is not surprising that it doesn't work well.  If you had a decent processor I'd say buy an AGP card, but you don't...

If you have $200 or more to spare, I would recommend building a new computer (If you have $400-500 or more you can buy it if you are too lazy) - you can likely use the case/fans on your current one.

---

### Post by Zorgoth on 2010-08-18
> **DaGeek247 said:**
> Yep, they are all set like that, and i didn't have to make any changes.

They are set like that and it tries to give you a spidery screensaver ?!  Or am I misunderstanding

---

### Post by DaGeek247 on 2010-08-18
I have to get off, but I will be on tomorrow with the full details. as a side note [this link]("http://forums.fedoraforum.org/showthread.php?t=249741") does pertain to my problems.

---

### Post by Zorgoth on 2010-08-19
How does that link pertain to your problems?  Did things work before you recovered that partition?  Is that partition still there?

---

### Post by DaGeek247 on 2010-08-19
Alright, now I will tell the full story on what happened. I have posted questions pertaining to the big problem, and that is one of the main ones. alright here goes.

I started out with windows, and it was all good. I installed ubuntu on the same hard drive and it was all good, except for the ever present screen error. Posts on this thread from June 26th and before were then posted. 

Then I installed WAMP on my windows system, and it caused enough problems for me to need to do a major system restore. It worked, but unfortunately, the game maker on my computer ran extremely slow. So much in fact that I decided to run it on Ubuntu. It didn't work because of the error, so I thought I could try fedora. I installed Fedora 13, and it worked out, after I figured out how to partition it correctly. Then, when I was running fedora, I realized that the game maker was on the Windows partition. (three OSes on one drive)

So I attempted to boot into Windows. It didn't work, and I made [this post]("http://forums.fedoraforum.org/showthread.php?t=249741") from the Fedora OS to try to fix it. Long story short (about the post) I managed to get the important data, and completely format the drive to a blank NTFS drive. Then, I attempted to reinstall windows, and I found out that the Windows CD was broke, so i attempted to make myself comfortable using just Ubuntu. That was when I posted the [control+alt+delete]("http://ubuntuforums.org/showthread.php?p=973937") equivalent post.

Then I decided to download a windows XP iso, and just use that. It took me awhile, but I manged to do it. I then put the CD in and rebooted the computer, just to find out that it was using the broken install CD in my other DVD drive, and not the one i made. That was a big bummer for me because, the windows install ruined grub, so i posted [this]("http://ubuntuforums.org/showthread.php?t=1555922"). I maneged to fix grub, and formet the NTFS drive.

So I am currently runnning a full install of Ubuntu with a empty NTFS partition, and I have a slipstreamed windows install CD that I have yet to test. Hopefully, this will answer the questions about the screensaver, the link in the post before this and maybe others.

---

### Post by DaGeek247 on 2010-08-20
It has been solved. I borrowed my brothers graphics card and it worked out. It runs my game maker really slow, so i going to ask my "geek" friend if he has any graphics cards. I hope it all works out.

---

