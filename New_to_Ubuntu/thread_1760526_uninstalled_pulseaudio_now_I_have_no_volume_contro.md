---
title: "uninstalled pulseaudio now I have no volume control."
date: 2011-05-17
forum: New to Ubuntu
---

### Post by itguy1985 on 2011-05-17
Want one in the panel like I had before. Is there a way to accomplish this?

---

### Post by wildmanne39 on 2011-05-17
> **itguy1985 said:**
> Want one in the panel like I had before. Is there a way to accomplish this?

Hi, what ubuntu version are you running?:)

---

### Post by itguy1985 on 2011-05-17
> **wildmanne39 said:**
> Hi, what ubuntu version are you running?:)

Hello. Running 11.04. thanks

---

### Post by wildmanne39 on 2011-05-17
> **itguy1985 said:**
> Hello. Running 11.04. thanks

Hi, I need to ask are you logged in to unity or ubuuntu classic, and which one do you want to be logged into? Before I can tell you how to get it up there.

---

### Post by itguy1985 on 2011-05-17
> **wildmanne39 said:**
> Hi, I need to ask are you logged in to unity or ubuuntu classic, and which one do you want to be logged into? Before I can tell you how to get it up there.

I like gnome. I log into classic Ubuntu.

---

### Post by corrytonapple on 2011-05-17
Well, if you are using GNOME classic, then you should be able to do this:
On your top panel (The one with the time and application menus) right click.  Then you will see a list of widgets.  Click "Indicator Applet" and then "Add".  It should be there now.
Hopefully this should work, but if not, leave it to wildmanne39 :)

---

### Post by itguy1985 on 2011-05-17
> **corrytonapple said:**
> Well, if you are using GNOME classic, then you should be able to do this:
On your top panel (The one with the time and application menus) right click.  Then you will see a list of widgets.  Click "Indicator Applet" and then "Add".  It should be there now.
Hopefully this should work, but if not, leave it to wildmanne39 :)

Thanks for the help. Sorry, but that doesn't work once PA is removed.

---

### Post by beew on 2011-05-17
I got the volumn buttons back on Lucid following this thread
[http://ubuntuforums.org/showthread.php?p=10008815]("http://ubuntuforums.org/showthread.php?p=10008815") 

Don't know if it would work on 11.04 though.

Actually I ended up reinstalling pulseaudio because the sound quality was much better when it was installed and removing it didn't solve the problem I originally experienced (don't remember what it was. :p)  

I think there are some people on the forum who have had bad experience with pulseaudio in the past and/or still running something like Ubuntu 8.04 on ancient hardware. They are keen on recommending removing pulseaudio. But PA never gives me any problem since Lucid and removing it actually makes sound quality worse. So I would keep PA if I am running Ubuntu on anything less than 5 years old (The laptop where I have removed PA and reinstalled it is 6 years old)

---

### Post by wildmanne39 on 2011-05-17
> **itguy1985 said:**
> Thanks for the help. Sorry, but that doesn't work once PA is removed.

Hi, did the link the other user mention fix your problem, I can not get on to my computer tonight that has the right version of ubuntu on it so that I can check it out, I am on a laptop that I have not used in three years that barely works.

---

### Post by itguy1985 on 2011-05-18
Installed the package. I got this as an out put, so I know it installed the right version, and went smoothly. I can't figure out how to add it to the panel. I tried looking in the gnome applets, but it wasn't there.

  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnome-netstatus-applet deskbar-applet cpufrequtils
The following packages will be upgraded:
  gnome-applets
1 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 194 kB of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/dtl131/ppa/ubuntu/ natty/main gnome-applets i386 2.32.1.1-0ubuntu6~audiohacks1 [194 kB]
Fetched 194 kB in 1s (170 kB/s)        
(Reading database ... 132846 files and directories currently installed.)
Preparing to replace gnome-applets 2.32.1.1-0ubuntu5 (using .../gnome-applets_2.32.1.1-0ubuntu6~audiohacks1_i386.deb) ...
Unpacking replacement gnome-applets ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Setting up gnome-applets (2.32.1.1-0ubuntu6~audiohacks1) ...
```

---

### Post by wildmanne39 on 2011-05-18
> **itguy1985 said:**
> Installed the package. I got this as an out put, so I know it installed the right version, and went smoothly. I can't figure out how to add it to the panel. I tried looking in the gnome applets, but it wasn't there.

  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnome-netstatus-applet deskbar-applet cpufrequtils
The following packages will be upgraded:
  gnome-applets
1 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 194 kB of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/dtl131/ppa/ubuntu/ natty/main gnome-applets i386 2.32.1.1-0ubuntu6~audiohacks1 [194 kB]
Fetched 194 kB in 1s (170 kB/s)        
(Reading database ... 132846 files and directories currently installed.)
Preparing to replace gnome-applets 2.32.1.1-0ubuntu5 (using .../gnome-applets_2.32.1.1-0ubuntu6~audiohacks1_i386.deb) ...
Unpacking replacement gnome-applets ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Setting up gnome-applets (2.32.1.1-0ubuntu6~audiohacks1) ...
```
Hi when you move your mouse to the top of the screen and right click on the bar you can not add it that way?

---

### Post by itguy1985 on 2011-05-18
> **wildmanne39 said:**
> Hi when you move your mouse to the top of the screen and right click on the bar you can not add it that way?

No

---

### Post by itguy1985 on 2011-05-20
bump

---

### Post by corrytonapple on 2011-05-20
Go to:
[https://launchpad.net/gmixer](https://launchpad.net/gmixer)
and download gmixer.  Then, extract it to your home folder and run the script in the folder "gmixer-1.3.tar.gz" to install.  The script should be setup.py.  
Try that and Good Luck

---

### Post by itguy1985 on 2011-05-25
I've gotten so desperate I've reinstalled pulse and I still can't get a volume control on my task bar.  I added indicator applet complete, and every thing shows up but the volume control. WTF?

---

### Post by beew on 2011-05-25
Did you install the package pavucontrol?

---

### Post by Paqman on 2011-05-25
Why did you uninstall Pulseaudio? It's a pretty important part of the system.

---

### Post by corrytonapple on 2011-05-25
What happened when you installed GMixer?

---

### Post by itguy1985 on 2011-05-25
I was afraid to try it, because it wasn't a .deb. How will I uninstall it if it doesn't work. Will I have to manually update it?

---

### Post by itguy1985 on 2011-05-25
> **Paqman said:**
> Why did you uninstall Pulseaudio? It's a pretty important part of the system.
 
I had sound problems with some emulators I enjoy using. One of them (pSX) won't even start if PA is installed.

---

### Post by itguy1985 on 2011-05-25
> **beew said:**
> Did you install the package pavucontrol?

Just installed it, nothing. Deleted indicator from panel and re-added it, nothing. Logged out logged back in, nothing, Restarted the computer, nothing. I'm stumped.

---

### Post by 5149.5 on 2011-05-25
> **itguy1985 said:**
> Just installed it, nothing. Deleted indicator from panel and re-added it, nothing. Logged out logged back in, nothing, Restarted the computer, nothing. I'm stumped.

I have the same issue. I spent two days fiddling with pulseaudio. The next day sound had quit. There is no way that sound should be so difficult. I put pulse audio in the dumpster where it belongs. Alsa does everything I need with lower resource demands and no configuration problems. If I need a volume control, I just run alsamixer from the command line but that usually doesn't happen.

---

### Post by Paqman on 2011-05-26
> **itguy1985 said:**
> I had sound problems with some emulators I enjoy using. One of them (pSX) won't even start if PA is installed.

I'd be inclined to either:
[LIST]
[*]Find a better emulator
[*]Install the emulator into an older or stripped down version in a VM. Although this depends on what kind of graphics performance you need.
[/LIST]

Ripping big chunks out of your main system just to get one program working seems a bit drastic.

---

### Post by 3rdalbum on 2011-05-26
> **beew said:**
> 
Actually I ended up reinstalling pulseaudio because the sound quality was much better when it was installed and removing it didn't solve the problem I originally experienced (don't remember what it was. :p)

Removing Pulseaudio **never** solves any problems as far as I know, it's just that people have this reflex action that makes them automatically suggest removing Pulseaudio whenever you say you have sound problems :-)

---

### Post by itguy1985 on 2011-05-26
> **3rdalbum said:**
> Removing Pulseaudio **never** solves any problems as far as I know, it's just that people have this reflex action that makes them automatically suggest removing Pulseaudio whenever you say you have sound problems :-)
It did solve the problem. I just don't have a volume control. Now that I reinstalled PA pSX won't start again.

---

### Post by 5149.5 on 2011-05-26
I didn't even have a problem with another app. I just developed an extreme dislike for pulse audio after messing with it for two days. I only wanted some sound. It didn't need to be as complicated as installing a database or a web server. and then it just stopped working for unknown reasons. That was the last straw.

---

### Post by 5149.5 on 2011-05-26
There is even a [howto ]("http://goo.gl/sTfdN")for fixing pulseaudio problems and the fix is to just remove it.

---

### Post by Paqman on 2011-05-27
> **itguy1985 said:**
> It did solve the problem. I just don't have a volume control. Now that I reinstalled PA pSX won't start again.

If fixing one problem just creates another, i'd venture you're not making much progress. What you really want is an emulator that isn't broken on up-to-date versions of Linux.

---

### Post by itguy1985 on 2011-05-27
> **Paqman said:**
> If fixing one problem just creates another, i'd venture you're not making much progress. What you really want is an emulator that isn't broken on up-to-date versions of Linux.

Is there any that aren't broken? Epsxe has the same problem.

---

