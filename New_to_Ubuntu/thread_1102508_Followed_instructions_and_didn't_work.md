---
title: "Followed instructions and didn't work"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-21
Ok I followed instructions on this thread

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and didn't work

I did this from "Getting the ALSA drivers from a *fresh* kernel"
since I couldn't find my driver for step 4 under General Help :s

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

and still didn't work I can only hear sound when it starts but no sound from anywhere else :(

on GNOME ALSA Mixer it shows C-Media CMI9880

I also did the aplay -l command on the terminal

leo@chick3ns-pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by lil_kid1333 on 2009-03-21
Can someone help...

tomorrow the last day to watch my online class lesson and obviously I can't hear it...

---

### Post by hansdown on 2009-03-21
Hi lil_kid1333.

I wish I had the knowledge to help, but that tutorial is almost three years old.

You need something that was written for 8.10.

Hoping this helps.

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

---

### Post by lil_kid1333 on 2009-03-21
Thanks I tried it but no luck still no sound :(

Imma give up... I think i'm just gonna reinstall ubuntu I really need my sound by tomorrow :'(

---

### Post by hansdown on 2009-03-21
Best of luck lil_kid1333.

My motto is, ' a fresh install fixes all."

I've done it too many times to count.

---

### Post by lil_kid1333 on 2009-03-21
yeah I know I would turn to that too when I used to have Windows but I don't want to do it cause I got SOOOOOOOOOOO much stuff on my PC..

Like songs, movies,etc but the most important things are some files for my school like projects and hw and I don't want to get rid of that but I really need my audio for my class >.<

---

### Post by hansdown on 2009-03-22
Booting into an older kernel may be a short term fix.

Actually, go to synaptic package manager.

Search for alsa base. If it is installed, the box will be shaded. If not, mark for installation, mark all upgrades, and install.

If it is installed, mark for complete removal, then reinstall.

---

### Post by lil_kid1333 on 2009-03-22
> **hansdown said:**
> Booting into an older kernel may be a short term fix.

Actually, go to synaptic package manager.

Search for alsa base. If it is installed, the box will be shaded. If not, mark for installation, mark all upgrades, and install.

If it is installed, mark for complete removal, then reinstall.

Ok I did it dude and nothing still no sound except before I restarted It, it said something bout sound properties was doing something and closing might lose data and I left it like that for a long time and tried restarting again and same message so I just restarted it and still no sound other than the beggining one :(

what the hell is wrong with my thing >.<

---

### Post by gandaran on 2009-03-22
> **lil_kid1333 said:**
> Ok I did it dude and nothing still no sound except before I restarted It, it said something bout sound properties was doing something and closing might lose data and I left it like that for a long time and tried restarting again and same message so I just restarted it and still no sound other than the beggining one :(

what the hell is wrong with my thing >.<
open the panel icon volume control, check if every sound option is enabled and at maximum value
and you may have to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)  if those fixes for alsa don't work.

---

### Post by lil_kid1333 on 2009-03-22
I tried it and nope it didn't work :(

I tried loading a previous kernel and didn't work... maybe I should try an older one... 

:(

---

### Post by kansasnoob on 2009-03-22
Did you run thru all the Intrepid specific steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

As Gandaran suggested?

---

### Post by lil_kid1333 on 2009-03-22
yeah this is the only part I didn't really understand

3. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a bug in Intrepid):

Code:

$ alsamixer -Dhw

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

4. Log out & back in for changes to take effect!

here's a pic

[http://img106.imageshack.us/img106/6278/screenshot1c.png](http://img106.imageshack.us/img106/6278/screenshot1c.png)



here result from doing the update part maybe I didn't add those lines it told me to edit on the file...

```
leo@chick3ns-pc:~$ sudo apt-get update && sudo apt-get dist-upgrade
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US    
Hit http://security.ubuntu.com intrepid-security Release.gpg        
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release             
Hit http://us.archive.ubuntu.com intrepid Release                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US        
Hit http://ppa.launchpad.net intrepid Release  
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://security.ubuntu.com intrepid-security/main Packages              
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/universe Packages   
Hit http://security.ubuntu.com intrepid-security/multiverse Packages 
Ign http://ppa.launchpad.net intrepid/main Packages                  
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Fetched 1B in 1s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by kansasnoob on 2009-03-22
Post the output from terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by lil_kid1333 on 2009-03-22
leo@chick3ns-pc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

---

### Post by kansasnoob on 2009-03-22
> **lil_kid1333 said:**
> leo@chick3ns-pc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

Ok, you have them added right:

> # PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

You still have no sound?

---

### Post by lil_kid1333 on 2009-03-22
No :(

But wait I did this when I loaded onto an older kernel could that be why?

---

### Post by lil_kid1333 on 2009-03-22
nevermind it ain't I tried loading onto the kernel I loaded into when I did the Pulse Audio thing and nothing.... :(

---

### Post by kansasnoob on 2009-03-22
Install gnome-alsamixer either from synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Look at mine:

[ATTACH]107298[/ATTACH]

[ATTACH]107299[/ATTACH]

Compare a little or post yours.

---

### Post by kansasnoob on 2009-03-22
Yes, you should be booting the most recent kernel!

---

### Post by lil_kid1333 on 2009-03-23
[http://img293.imageshack.us/img293/2936/screenshotf.png](http://img293.imageshack.us/img293/2936/screenshotf.png)

I did it and nothing im just going to restart it I guess =/ thanks guys for all your help

I was wondering, what's the folder where my bookmarks are saved on firefox? Imma back up some things

---

### Post by boof1988 on 2009-03-23
> **hansdown said:**
> Best of luck lil_kid1333.

My motto is, ' a fresh install fixes all."

I've done it too many times to count.

I know I'm kinda lame... but... this is the way I *fix* a lot of stuff.  It helps me learn what not to do.  And I guess I have learned alot during the many installations.  I just keep pushing the edge of the envelope.

---

### Post by lil_kid1333 on 2009-03-24
yeah I know that too from previous times that things have mest up...

anyways where's the folder with the firefox bookmarks?

---

### Post by boof1988 on 2009-03-24
> **lil_kid1333 said:**
> yeah I know that too from previous times that things have mest up...

anyways where's the folder with the firefox bookmarks?

I just usually make a backup of the Firefox bookmarks.  That way I can save the backup anywhere I want.

In Firefox, go to *Bookmarks >> Organize Bookmarks >> Import and Backup >> Backup* and then choose the place to save the bookmarks and click <*Save*>.

If this is not a feasible way for you to save your bookmarks, maybe someone else will have some more ideas.

HTH

---

### Post by markbuntu on 2009-03-24
Before you reinstall try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix you up go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by lil_kid1333 on 2009-03-25
> **markbuntu said:**
> Before you reinstall try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix you up go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

thanks but i re-installed already xD

omg I got sound!!!! :'D

thanks everyone for the help

---

