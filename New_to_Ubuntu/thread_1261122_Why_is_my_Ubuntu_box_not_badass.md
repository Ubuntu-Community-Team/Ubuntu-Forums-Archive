---
title: "Why is my Ubuntu box not badass?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by rslee on 2009-09-08
A few weeks ago I installed Ubuntu 9.04 on a new PC and shelved my 4-year-old Vaio running XP Pro.  I hadn't used Linux since the 90's, so I was really impressed with the look and feel of Gnome and the overall user-friendliness of Ubuntu.

However, within a week or two the system started feeling slow.  It now behaves like a system I would diagnose as low on resources, and yet this is a brand-spanking-new Core 2 Duo with 3GB of RAM.

The type of behavior I'm talking about is:
* Everything is sloooow- opening menus, applications, the Gnome Do dialog and new windows, ALT-TAB graphics, typing text and highlighting text (in Firefox textboxes), switching tabs in Firefox
* A few times a day, FF greys itself out for 15-30 seconds and becomes unresponsive
* I've had gedit crash a couple of times, seemingly because I pasted text twice quickly (less than 1MB)
* Copying a 700MB file to my thumb drive takes 10-15 minutes (yes, minutes)

90% of my time on Ubuntu is spent in Firefox and gedit, so the slowness and instability of those two apps is a source of constant frustration.

Yes, I have 25 tabs open in Firefox, but they're the same 25 I had open in Firefox on XP.  And I have 50% more RAM now, not to mention a better processor and emptier disk (I assume it's faster but haven't checked).  

What gives?  Is there a list of, say, Everything Extraneous You Should Uninstall After Installing Ubuntu?

I can deal with the small challenges and disappointments of moving to Linux (such as spending hours getting a basic device working or losing Evernote and some key functionality of my HP printer), but if it's not fast and not stable, what's the point?

I wanted to start using VirtualBox to do some testing in Windows, but I'm afraid to add any more load to the system, for fear it will become unusable.

I think I must have something very misconfigured, or else I just bought some faulty hardware, because this just can't be right!  How do I go about waking up a sleepy Jackalope?

Thanks!

---

### Post by Simian Man on 2009-09-08
What graphics card do you have?  Did you install the restricted drivers?  Are you running the 32 or 64 bit version?  Are you running compiz (desktop effects)?

---

### Post by MysticGold04 on 2009-09-08
Just a shot in the dark, but you might have a bad memory chip.  reboot and hit ESC when grub is starting and run the memory test.  

Also, you might double check your cmos/bios settings and reset them to the default to see if that helps.  

I have noticed that the current version of Firefox has a bug or something as it hangs sometimes on my laptop (Vista) but that could also be the OS.

---

### Post by LowSky on 2009-09-08
Well I hate to tell you this but It probably you and not Ubuntu.
What happens is that people new to the OS get all happy that they have such a lightweight OS and go install crazy, using poor instructions that eventually end up in slow downs and system breakage.

dont worry it happens to most of us. By the time you do your 3-4 install things will fall in line.... 

But lets see if its a simple fix

open a terminal and type ```
top
``` hit CTRL+C to end the process and copy and paste the data here. Please be running you normal daily stuff, dont cheat, so 25 tabs open in firefox,  a 1MB gedit file, the works...
What have you installed besides the Operating System.

* FF greying out can be the result of flash, are you using 32 or 64 bit Ubuntu, if 64 bit, lets get you the right driver, and no it isn't he one from the repos.. if not using 64bit, why its the future of OSes, and it will use your CPU and RAM better.

* gedit crash.. never heard of that, What the hell are you pasting, and even 512kb is alot of info al at once for any wordpad like program

* Linux (not just Ubuntu) has isues with Flash drives. I myself have tried to fix the issue to no avail. It seems anyone involved in driver creation doesn't realize that people might need to transfer a 100MB+ file. Oddly things work fine on new installs most times, but once you update the Kernel things go to Hell.

---

### Post by Paqman on 2009-09-08
> **MysticGold04 said:**
> Just a shot in the dark, but you might have a bad memory chip.  reboot and hit ESC when grub is starting and run the memory test.  


Just a note on this: it won't actually halt at any point. Just let it run for a few hours.

It does sound like it could be hardware though. You shouldn't be seeing poor performance on a new machine, but faulty components are highly likely to fail early.

---

### Post by rslee on 2009-09-08
@Simian Man, I'm running 64-bit Jaunty. Graphics card, Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I don't see any restricted drivers to enable, but I can't tell if there's something I need to do first (e.g. download).

I didn't think I was using compiz, but a compiz.real process showed up when I ran top (see below).

@MysticGold04 Don't want to reboot right now; will respond later.  I haven't updated the BIOS.

@LowSky: I agree about going install-crazy with a new machine.  My Windows machines suffered the same punishment and are none the worse for it.  But (in my experience) Ubuntu doesn't have the ocean of sketchy shareware toys Windows does, that tend to lead you down that path.  I don't think I've gone overboard with this install of Ubuntu.

Top:

```
top - 12:38:44 up 6 days,  3:45,  2 users,  load average: 0.24, 0.18, 0.19
Mem:   2026368k total,  2008040k used,    18328k free,     6424k buffers
Swap:  5935976k total,  2434904k used,  3501072k free,   181148k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                           
 5019 leer      20   0 1623m 758m  14m S   10 38.3 766:59.02 firefox                           
 3106 root      20   0  711m 139m  12m S    1  7.0 102:36.05 Xorg                              
 3887 leer      20   0 70312 1984 1004 S    0  0.1   0:26.01 npviewer.bin                      
11767 leer      20   0  161m  24m 4200 S    0  1.2  27:29.78 skype                             
 5536 leer      20   0  200m  10m 5236 R    0  0.5   0:11.76 gnome-terminal                    
20485 leer      20   0  257m  21m 5632 S    0  1.1   0:00.84 jockey-gtk                        
 3405 leer      20   0  260m 7888 4376 S    0  0.4   0:06.74 kded4                             
 3411 leer      20   0  261m 6532 3592 S    0  0.3   0:03.54 kwalletd                          
 3720 leer      20   0  786m  21m 6980 S    0  1.1   1:16.43 pidgin                            
 3904 leer      20   0  240m 4760 1764 S    0  0.2  11:45.11 compiz.real                       
   21 root      15  -5     0    0    0 S    0  0.0   0:24.60 ata/0                             
 3046 root      20   0 28484  304  232 S    0  0.0   0:02.99 hald-addon-stor                   
 3047 root      20   0 28484  312  236 S    0  0.0   0:42.46 hald-addon-stor                   
 3905 leer      20   0  332m  15m 5520 S    0  0.8   3:02.68 gnome-panel                       
 5763 root      20   0  434m  18m 5308 S    0  0.9   1:00.60 gedit                             
    1 root      20   0  4104  140   60 S    0  0.0   0:00.73 init                              
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                          
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/0                       
```I'm not doing much text processing these days, but when I did, I would regularly manipulate 50-100MB files in UltraEdit.  The app itself might slow down noticeably with files that size (during scroll mainly), but I don't remember Windows being too affected.  A 1MB text file is not big, and gedit isn't WordPad, thank goodness. :)  The amount of text I pasted before the crash was probably more on the order of 100K.

As for my Flash player, I found this ([http://ubuntuforums.org/showthread.php?t=996674](http://ubuntuforums.org/showthread.php?t=996674)) just before starting this thread, but since I didn't have any  of the packages installed that they say to uninstall, I figured that an official release had come out and that I was using it already.  Should I install via the page mentioned in that thread?

@Paqman, I should run Grub for a few hours?  Overnight then... will that find a motherboard problem as well?

To all, many thanks for your help!

---

### Post by Bucky Ball on 2009-09-08
System->Admin->Synaptic Package Manager. Search for and install 'ubuntu-restricted-extras' (and 'ubuntu-restricted-modules' but not sure if that is needed in 9.04). 

Add the Medibuntu repository to your software sources following this guide. It will install flash and a bunch of other things:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Open a terminal and paste:

```
sudo apt-get update
```then

```
sudo apt-get upgrade
```

---

### Post by alejaaandro on 2009-09-08
to check for restricted drivers go to 
Administration->Hardware drivers.. if you have some hardware that might need extra drivers, you will be informed there

---

### Post by wobin77 on 2009-09-08
Just don't install the ATI ones... They can flush anything away. Did it, so i know... 
--> HD 3850

---

### Post by LowSky on 2009-09-08
you really need a reboot, 6 days up time is great but after installing software like flash and such a reboot will make things run smoother.

Afor 64bit flash follow this
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

the ubuntu-restricted-extras command will not install 64bit flash, only the 32bit version... no one mentions that.. the 64bit is technically a Alpha software but runs great, very few issues.


Also it says your running KDE and Gnome at the same time? You have 2 users running two different environments ... that is what is taking up cache and resources, turn one off.

---

### Post by Paqman on 2009-09-08
> **rslee said:**
> 
@Paqman, I should run Grub for a few hours?  Overnight then... will that find a motherboard problem as well?


The option you want from Grub is called Memtest86, and it just tests memory.

You said you're using Intel integrated graphics on Jaunty though, that could be some or all of your problem. Intel really messed up their graphics drivers for Jaunty. Until Karmic comes out at the end of next month you don't really have a simple solution besides stepping back to Intrepid, or disabling all effects. Go to System > Prefs > Appearance > Visual Effects and make sure you've got it set to "none".

---

### Post by LowSky on 2009-09-08
> **wobin77 said:**
> Just don't install the ATI ones... They can flush anything away. Did it, so i know... 
--> HD 3850

He has Intel graphics... why for whatever reason would he install ATI drivers????

---

### Post by LowSky on 2009-09-08
> **Paqman said:**
>  Until Karmic comes out at the end of next month you don't really have a simple solution besides stepping back to Intrepid, or disabling all effects. Go to System > Prefs > Appearance > Visual Effects and make sure you've got it set to "none".

OR use the Karmic driver in Jaunty... (I will say this isn't the best thing to do, but if its required)
[http://packages.ubuntu.com/karmic/xserver-xorg-video-intel](http://packages.ubuntu.com/karmic/xserver-xorg-video-intel)

---

### Post by Paqman on 2009-09-08
> **LowSky said:**
> OR use the Karmic driver in Jaunty... (I will say this isn't the best thing to do, but if its required)
[http://packages.ubuntu.com/karmic/xserver-xorg-video-intel](http://packages.ubuntu.com/karmic/xserver-xorg-video-intel)

I haven't tried it, but it could be a hassle to sort out the dependencies, and thus not entirely newb friendly.

---

### Post by ugm6hr on 2009-09-08
> **rslee said:**
> 
Top:

```
top - 12:38:44 up 6 days,  3:45,  2 users,  load average: 0.24, 0.18, 0.19
Mem:   2026368k total,  2008040k used,    18328k free,     6424k buffers
Swap:  5935976k total,  2434904k used,  3501072k free,   181148k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                           
 5019 leer      20   0 1623m 758m  14m S   10 38.3 766:59.02 firefox                           
 3106 root      20   0  711m 139m  12m S    1  7.0 102:36.05 Xorg                              

```

The problem here is Firefox.  38% of MEM used, with 2GB RAM (did you say you have 3GB?) and 6GB swap, of which almost half is in use.

Xorg is using a little more  than expected, but FF is clearly the problem.

As for why?  Don't know.  Your 25+ tabs may be the issue (I never use more than about 10). but I am not sure.  Perhaps worth trying FF-3.5 and rebooting to see if it is any more efficient.

```
sudo apt-get install firefox-3.5
```

It appears as Shiretoko in your menu (but is actually FF 3.5).

EDIT: Not sure if I have missed something, but it appears FF has been running on CPU for longer than FF....

---

### Post by tgalati4 on 2009-09-08
Could be the fsync bug.  Try shutting down firefox and see how the rest of the system responds.  FF's sqlite database is trying to fsync it's state with 25 tabs open while the rest of Ubuntu is trying to do the same, resulting in laggy performance.

If FF 3.5.2 doesn't fix it, then try running FF in RAM:

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

Some detail on fsync:

[http://www.mail-archive.com/sqlite-users@sqlite.org/msg34254.html](http://www.mail-archive.com/sqlite-users@sqlite.org/msg34254.html)

---

### Post by running_rabbit07 on 2009-09-08
> **LowSky said:**
> the ubuntu-restricted-extras command will not install 64bit flash, only the 32bit version... no one mentions that.. the 64bit is technically a Alpha software but runs great, very few issues.

Off subject. Will this problem with Ubuntu-restricted-extras be fixed for 64-bit flash in Karmic or Lusty?

---

### Post by lykwydchykyn on 2009-09-08
Check this out:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

A must-try for anyone having performance problems with Intel in Jaunty.  Helped out my laptop a good deal.

---

### Post by LowSky on 2009-09-08
> **running_rabbit07 said:**
> Off subject. Will this problem with Ubuntu-restricted-extras be fixed for 64-bit flash in Karmic or Lusty?


It's not really a problem, the 64bit version has never been out before, so for the longest time we 64bit guys had to run the 32bit version.
Once Adobe finalizes the 64bit version then the next subsequent version of Ubuntu will have the update. same as always...

---

### Post by wobin77 on 2009-09-08
> **LowSky said:**
> He has Intel graphics... why for whatever reason would he install ATI drivers????

Yeah, sorry... misread his post (failed to see the 'intel' -word).

---

### Post by oldos2er on 2009-09-08
> **running_rabbit07 said:**
> Off subject. Will this problem with Ubuntu-restricted-extras be fixed for 64-bit flash in Karmic or Lusty?

 As long as 64-bit flash remains alpha, there most likely won't be a fix.

---

### Post by rslee on 2009-09-08
OK, here's an update:

@Bucky Ball: ubuntu-restricted-extras and dependencies were already installed.  I followed the rest of your instructions, verifying at the end that Medibuntu was in fact available and selected as a source in Synaptic.  But the upgrade didn't do anything interesting:

```
The following packages will be upgraded:
  google-chrome-unstable language-pack-en language-pack-gnome-en
```Should ubuntu-restricted-extras make restricted drivers available?  I'm puzzled as to why none are available in Hardware Drivers.

@alejaaandro: No drivers showing at the moment.

@LowSky:

Flash- Followed instructions; my current installed version of the Flash plugin is 10.0 r22.  When I went to download Firefox 3.5, it recommended a critical update to Flash, version 10.0 r32, which I don't  see a 64-bit version of.  Should I go back to 32-bit for security reasons?

KDE- Do you say that because of the kded4 process above?  Not sure how this happened; could it be because I installed some KDE icons? I definitely want to resolve that!

@Paqman: I set the desktop effects to None.

@ugm6hr: I did say 3GB; I was wrong!  I have 2GB.  It doesn't change my expectations, really, since I've never had more than 2GB on any machine.  But I'll buy another 2, I think, to feed my 25 tabs.  (I'm spoiled by the TabGroups Manager plugin.)

@tgalati4: I upgraded FF to 3.5.

I'll try @lykwydchykyn's suggestion when I'm feeling like less of a noob (though Karmic will probably be out by then), but for now my system is responding a lot faster, mainly due to the Flash upgrade and turning visual effects completely off, I think.  Can't wait to see how it runs when I actually reboot! ;)  Thanks again...

---

### Post by LowSky on 2009-09-08
KDE icons, Like What?

Like I said beofre there is no 64bit verison of Flash availible fro Ubuntu's repos. You need to follow my link from before.
The one Ubuntu installs is the 32bit version

TabGroups Manager plugin...hmmm might be your memory leak

alejaaandro mentioned drivers for video, but you dont need any, intel has no restricted proprietary drivers, they are completly open. And they stink under 9.04, 9.10 (karmac) supposedly work much better.

and _**reboot **_or at least log off and then back in. It take a minute tops!!! You need to clear your cache of all the processes you ran, especially if you did any kernel upgrades.

---

### Post by Bucky Ball on 2009-09-09
For Medibuntu follow the instruction here, NOT Synaptics. :

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

... as I suggested. I would uninstall whatever you have installed of Medibuntu with Synaptics unless you like what it has added. I think you probably installed the desktop and some apps perhaps. Don't know, never used it. Only ever installed the repo. Don't forget to add the GPG key which is at the bottom of the codes.

---

### Post by tgalati4 on 2009-09-09
Although I haven't tried it, I have heard that FF 3.5.x can run from ram disk as well.

---

### Post by tolean_dj on 2009-09-11
I was too not too thankful of my Ubuntu for a period just before a few days ago when I found a trick that speed-ed up my jaunty a lot :)
I'm running 32 bit and the trick was CPU scaling setting. You can easily change it by right clicking on a panel and adding the "CPU Frequency Scaling Monitor", then just click it and select the "Performance" option. It work very good for me and I can say now I'm happy :D

Just one mention, if ubuntu we'll use actively the swap it will be lagging anyway. A way to reduce swapping is setting it to a lower percentage just right here [http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html](http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html)

Hoping this will help you. Have a nice day!

---

### Post by relay_man on 2009-09-11
I believe ugm6hr has it right.
Unload at least half of those tabs.
Any time you're using that much swap it's going to take a while.
(even with a 10,000 rpm disc,  which you probably don't have)

Get an NVidia vid card with some memory on the card. An 8600GT or better would help alot.
The on-board Intel graphics will use ram when it needs it.
In your case I'm sure it's "borrowing" quite a bit.

---

### Post by markbuntu on 2009-09-11
firefox and flash both have some small memory leaks which will pile up after a few days and start to slow things down so closing firefox every once in a while is a good idea. 25 tabs??? really...

A reboot after installing packages will also clean stuff up a lot and free up resources.

There was also a few issues with the intel drivers in the kernel for Jaunty which you can read about here

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by tolean_dj on 2009-09-12
Just an add

A nice ideea would be to install "Flash Block" plugin in firefox, wich replace each flash object with a button, what consume much less than the flash itself, so unnecessary flash objects will not eat so much needed memory... 

... just as an add, not the base ideea...
;)

---

### Post by twright on 2009-09-12
> **rslee said:**
> How do I go about waking up a sleepy Jackalope?
Well you might find some relief in waiting for a Kickass Koala - the next version of Ubuntu will have a lot of cool performance improvements and if you do a fresh install that will clean out any junk left over. The system is not normally at all slow, on my eeepc with 1GB ram, integrated intel graphics and an atom processor even with 20-50ish tabs, image editors and media programs all open it runs perfectly snappily.

---

