---
title: "Now on ubuntu 11.04 and still havent managed to get my graphics working right!"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2011-05-10
Ok so I have posted a couple of threads on here about the problems with graphics on my PC.

Its a AMD 7750 64 bit powered machine, 4gb of mem, 1x500gb HD(which ubuntu runs off as it wouldnt install onto the windows drive) 1x160gb HD and now I am running 2x Radeon HD4670 graphics cards.

Windows 7 (32bit even though this machine is 64 bit due to install problems)is fine with the dual card setup and is working lovely however my 64bit ubuntu is having none of it.

I have run through various versions of ubuntu all with the same result of not being able to use the full graphics potential of this machine. I started with ubuntu 9.04, then 9.10,10.04LTS 64bit, 10.10 64bit and now I am running 11.04 with only minor improvement.

Basically the standard graphics drivers seem to now be working so it boots up without crashing everytime, but under the update manager it says there is an ATi graphics driver to install but when I click to install it I get a new window appear that says[I]:

 **'The package system is broken' 'If you are using third party repositories then disable them, since they are a common source of problems. Now run the following command in a terminal: apt-get install -f'**[/I]

[I][B]The following packages have unmet dependencies:

fglrx-amdcccle: Depends: fglrx but it is not installed
                Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.1 is installed
                Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.1 is installed[/B][/I]

So then I go into terminal and type 'sudo apt-get install -f' which gives me this:
[I]
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0 B/35.0 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 190694 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.840-0ubuntu4_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd[/B][/I][B]64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]
I have followed the ubuntu wiki page on trouble with graphics drivers and purging the system of them and starting again but something still seems to be up and I dont know what to look at next[B] :(
[/B]
If anyone knows of what I can do I would appreciate the help. I wanted Linux on my machine as a bit of a test for me to get it to work and beat windows, but I find myself banging my head against the wall!

---

### Post by Bugsy_malone 666 on 2011-05-11
I thought I would add to this that I cant seem to update anything through update manager currently, even if I unselect the ATi graphics update, it still keeps coming up with the package system is broken thing.

Any ideas on how to purge the system futher?

---

### Post by jramshu on 2011-05-11
This may solve some of the "7 not upgraded" part. Be warned, sometimes it will remove pulsaudio and may have to be reinstalled.
```
sudo apt-get update
sudo apt-get dist-upgrade
```Let us know what the output was.

Thanks

---

### Post by Bugsy_malone 666 on 2011-05-12
Well yesterday before I had read this post I decided to do something silly and do a fresh install.

When I say fresh install I mean that I started the ubuntu CD and chose to install 64bit linux again but keeping my files/settings.

I left that running while I was out lastnight, I figured it would get rid of everything and install what was needed, I even got updates downloaded as I went along. This resulted in a machine that now wont boot as such (as its got dual o/s it gets to the o/s select) as in if I select ubuntu, it just wont boot up fully, it just hangs.

Soooooo, later today I am going to set it installing again, this time I am going to install linux and set it to wipe all my settings and not download updates as it goes along. I get the feeling that the ATi drivers are what is causing the issues, as upon booting rather than a pure black screen the background is a dark purple, which I found to be a symptom of the ATi drivers.

If I can get it to boot normally I will try again with the updates and see if the package installer still reports broken stuff.

Then I will report back!

---

### Post by Bugsy_malone 666 on 2011-05-13
ok after hours of messing about lastnight I finally got ubuntu 11.04 to work on my machine. 

However there is still some sort of graphics driver issue!

Basically ubuntu is running in basic graphics mode and wont run unity because it needs graphics drivers, so I open the proprietary driver thing and download the driver linux says I need, problem is that one didnt work! Instead I ended up with a hanging screen when I booted up.

So then I thought maybe I can manually install the drivers that I downloaded from ati site. Previously I have just had a .run file which I have double clicked on and its loaded, not now as 11.04 doesnt seem to know what to run it with!

It's really annoying that I have a great spec PC that just wont work properly!

---

### Post by Goupit on 2011-05-20
> **Bugsy_malone 666 said:**
> 
So then I thought maybe I can manually install the drivers that I downloaded from ati site. Previously I have just had a .run file which I have double clicked on and its loaded, not now as 11.04 doesnt seem to know what to run it with!

Its been ages since i got in here. Hello ubuntu community.

Well Bugsy you can run the .run with sh <filename>.run but i would not suggest doing it. I did it a couple of days ago. When i first installed ubuntu i enabled my driver through Additional Drivers application. I found out after restarting that unity would not run after that. So what i did was run the script from ATI site. I noticed that now i had in System->Preferences menu, the ati ccc option twice for each mode. I deactivated the driver from additonal drivers and had it once. I tried to remove fxglr-amdccc from synaptics. Did it but i'm  stuck with amd ccc in menu. Now i'm looking for a way to remove everything cause i kind of liked unity. I tried updating i tried re-removing... nothing works. After trying to update i get the same messages with you.
I believe that the driver from ati's site is still somewhere in there causing problems. I don't want to re-install ubuntu.
Any ideas?

---

### Post by Bugsy_malone 666 on 2011-05-21
> **Goupit said:**
> Its been ages since i got in here. Hello ubuntu community.

Well Bugsy you can run the .run with sh <filename>.run but i would not suggest doing it. I did it a couple of days ago. When i first installed ubuntu i enabled my driver through Additional Drivers application. I found out after restarting that unity would not run after that. So what i did was run the script from ATI site. I noticed that now i had in System->Preferences menu, the ati ccc option twice for each mode. I deactivated the driver from additonal drivers and had it once. I tried to remove fxglr-amdccc from synaptics. Did it but i'm  stuck with amd ccc in menu. Now i'm looking for a way to remove everything cause i kind of liked unity. I tried updating i tried re-removing... nothing works. After trying to update i get the same messages with you.
I believe that the driver from ati's site is still somewhere in there causing problems. I don't want to re-install ubuntu.
Any ideas?

I have had a mixture of problems when using ATi drivers, but just cant get them to install, they make the machine hang/not boot.

What graphics card are you using?

I used the 'additional drivers' option first and that caused it to not boot, then switching back to conversion 'basic' linux shipped graphics drivers it works, but I dont get the fancy graphics and unity isnt even an option to try.

I have been able to run the ati downloaded drivers I got from their site, although previously on ubuntu 10.04lts/10.10 it would still give me the same result where I would have it hanging on start up and just not boot, the only way I could get it to boot was go back to the basic graphics thing again.

Its driving me crackers as I have a laptop with a 64mb ati graphics card (HP NC8000 laptop) running unity and another desktop with a radeon 9800pro running 10.10 (just havent booted it up to update to 11.04 unity yet) which has ati drivers installed fine!

---

### Post by Goupit on 2011-05-22
Well i faced a couple of boot failures as i remember. Unfortunately, i couldn't wait since i needed my system up and running for some projects, so i did a fresh install.

I have a radeon 4330 on my acer laptop. After reinstalling i enabled no graphics driver and i have unity working great. I don't know what's happening. But it would be great having the catalyst center and all with my ubuntu. I still haven't tried the HDMI output and see if it is working without having the additional driver. I'll post once i test it.

---

### Post by Goupit on 2011-05-24
There is no way i can explain the behavior of natty.
Here's what i have done in time order the last two days:

1. Installed 11.04:
   Worked except from the thing with the graphics card i mentioned above. I was working on a project using postgresql(newbie on it). Tried everything, postgresql server wasn't starting, so...
2. Reinstalled 11.04:
   Now here's the good stuff. Nothing works. No boot after grub, whatsoever. I only heard for once the tam-tam from the login screen, pressed enter, my password, I managed to log in and shut down with a blank screen.
3. Frustrated, I installed 9.10 karmic:
   Well ok that was the last working disto i had.
4. Updated to 10...:
   I still wanted postgresql. My setup was not what i was looking for, the setup in 11.04 was, so...
5. Installed 11.04:
   So last night after the installation ended i rebooted and loaded ubuntu fine. I had unity working but i was tired and shut my laptop down. So i went to bed being happy about my new fresh working installation that would be waiting for me in the morning.
Guess what... this is morning... and i'm posting through my windows firefox browser...!!!
What is going on????
#-o#-o#-o

---

### Post by Finnius on 2011-05-24
Hey,

11.04 still has bits and pieces that need ironing out...
It would save you a lot of headaches if you could just run 10.04 LTS.

> **Goupit said:**
> 
4. Updated to 10...:
   I still wanted postgresql. My setup was not what i was looking for, the setup in 11.04 was, so...

Why do you need 11.04 for the postgresql "setup" you want?

---

### Post by wildmanne39 on 2011-05-24
> **Bugsy_malone 666 said:**
> I have had a mixture of problems when using ATi drivers, but just cant get them to install, they make the machine hang/not boot.

What graphics card are you using?

I used the 'additional drivers' option first and that caused it to not boot, then switching back to conversion 'basic' linux shipped graphics drivers it works, but I dont get the fancy graphics and unity isnt even an option to try.

I have been able to run the ati downloaded drivers I got from their site, although previously on ubuntu 10.04lts/10.10 it would still give me the same result where I would have it hanging on start up and just not boot, the only way I could get it to boot was go back to the basic graphics thing again.

Its driving me crackers as I have a laptop with a 64mb ati graphics card (HP NC8000 laptop) running unity and another desktop with a radeon 9800pro running 10.10 (just havent booted it up to update to 11.04 unity yet) which has ati drivers installed fine!
Hi, part of the problem is when you download and install drivers from other sites they conflict with the ones you already have installed through additional drivers, if you know the names exactly you can remove them and the config files with this command. 
```
sudo apt-get --purge remove <package name>
```This command is without brackets.You say you did another install but when you keep your settings from the previous install you are just making matters worse.

---

### Post by Goupit on 2011-05-24
> **Finnius said:**
> 

Why do you need 11.04 for the postgresql "setup" you want?

Well the thing is that i want postgis for its geogrphy data type. When i installed postgis with postgresql in 11.04, i somehow had them.
When i installed them in 10 i only had geometry. As i mentioned i'm new to this. Also messing with packages and stuff is not something i'm strong at. I couldn't find something in this foroum about postgres setup, maybe i should open a thread. Have you got any suggestions?

Anyhow.
> **Finnius said:**
> 
11.04 still has bits and pieces that need ironing out...
It would save you a lot of headaches if you could just run 10.04 LTS.

You're right. Very unstable, at least won't do the work for my laptop. Also it seemed to me like it cought fire([http://ubuntuforums.org/showthread.php?t=1761022&highlight=natty+grub](http://ubuntuforums.org/showthread.php?t=1761022&highlight=natty+grub)). So i think ubuntu is not an option for my little friend.  I haven't returned home to sheck on my desktop. I left 5 days ago without checking out how that installation is working. I have there a nvidia graphics card. I'll post when i can.

---

### Post by Goupit on 2011-10-26
I knew i had forgoten something...
This thread!!!
Well my desktop is working great ever since i installed. Not enabled unity.
The problem with my laptop was-as i found out five months ago-the switchable graphics options provided by the mobo manufacturer.
Going so deep back then was not an option for me so still my acer has no ubuntu.

---

