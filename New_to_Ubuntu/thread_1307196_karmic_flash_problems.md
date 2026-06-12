---
title: "karmic flash problems"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by itsbrad212 on 2009-10-30
Hey everybody. I recently installed karmic and so far, I'm pretty unhappy. Mostly because of the changes and all, and I guess I'll get used to it. But anyway, the reason I'm posting is because I can't get flash player installed. Can anybody help me?

---

### Post by Regenweald on 2009-10-30
Try System>>Administration>>Synaptic

Search 'flash'

check 'flashplugin-nonfree' for installation.

---

### Post by itsbrad212 on 2009-10-30
> **Regenweald said:**
> Try System>>Administration>>Synaptic

Search 'flash'

check 'flashplugin-nonfree' for installation.


it's not showing up :(

---

### Post by Xatolos on 2009-10-30
I found it with Applications -> Ubuntu Software Center, then downloaded Ubuntu Restricted Extras. Tried that?

---

### Post by itsbrad212 on 2009-10-30
> **Xatolos said:**
> I found it with Applications -> Ubuntu Software Center, then downloaded Ubuntu Restricted Extras. Tried that?

sorry im new to the whole software center thing. ive always used synaptic. so how exactly do u do that ? :D

---

### Post by RC1139 on 2009-10-30
try pasting this command into your terminal: sudo apt-get install adobe-flashplugin

---

### Post by itsbrad212 on 2009-10-31
> **RC1139 said:**
> try pasting this command into your terminal: sudo apt-get install adobe-flashplugin

output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

---

### Post by hotstovejer on 2009-10-31
> **itsbrad212 said:**
> output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

Please try this command:
```
sudo apt-get install ubuntu-restricted-extras
```
And let us know what the output is. 

You also may need to check your Software Sources. Do you know how to check that? Go into System, then Administration, and then Software Sources. Check all the boxes you can, and then click close. Let it update, and then try again!

Thanks!

---

### Post by itsbrad212 on 2009-10-31
> **hotstovejer said:**
> Please try this command:
```
sudo apt-get install ubuntu-restricted-extras
```And let us know what the output is. 

You also may need to check your Software Sources. Do you know how to check that? Go into System, then Administration, and then Software Sources. Check all the boxes you can, and then click close. Let it update, and then try again!

Thanks!


thanks for your help. I was about to add the sources when i realized i could just do:

```
sudo apt-get flash-player-nonfree
```

thanks anyway.

(O and sorry this post made me sound like a noob, I actually have used ubuntu for years, and i think the hardest part is getting started from a clean install :D)

---

### Post by itsbrad212 on 2009-10-31
> **itsbrad212 said:**
> thanks for your help. I was about to add the sources when i realized i could just do:

```
sudo apt-get flash-player-nonfree
```thanks anyway.

(O and sorry this post made me sound like a noob, I actually have used ubuntu for years, and i think the hardest part is getting started from a clean install :D)

whoops forgot to add the "install" in there :popcorn:

---

### Post by Xatolos on 2009-10-31
> **itsbrad212 said:**
> sorry im new to the whole software center thing. ive always used synaptic. so how exactly do u do that ? :D

Go to Applications -> Ubuntu Software Center (it's the bottom choice). It's an software list of Ubuntu approved software for you to install and use. Just type in what you are looking for in the top right Search box and it will bring up a list of options. Like when I type in Flash it offers me at the top the Ubuntu Restricted Extras, just double click (or click the arrow button when the option is highlighted) to receive a summery of the program with a possible picture of what it looks like. Near the bottom of the summery will be an Install button to click to install the software (or it will be a Remove button if it's already on your system.

Also on the left box is 2 different options, the Get Free Software (default selected) which I just described and then there is the Installed Software option which shows what is installed on your system, which shows the programs installed, but not the finer parts that are listed in the Synaptic Package Manager. When you are download/installing a new program a 3rd option will appear showing the list of things installing and to be downloaded and installed.

Hope that helps

---

### Post by Berk'n'Boni on 2009-10-31
> **hotstovejer said:**
> Please try this command:
```
sudo apt-get install ubuntu-restricted-extras
```And let us know what the output is. 

You also may need to check your Software Sources. Do you know how to check that? Go into System, then Administration, and then Software Sources. Check all the boxes you can, and then click close. Let it update, and then try again!

Thanks!

Thank you. Very much in fact. -  Never used Ubuntu before yesterday (trying the new release) and that little fix has just solved what has been bothering me since I went online.  All ads were a grey field with a circled arrow in them (yay!) but so were UPLOAD buttons on certain websites I use daily (boo!) and when clicked on they simply didn't work at all.  Spent most of today Googling trying to find a solution and kept hitting various walls.

Having joined the forums this was the first thing I found on RECENT threads.  Of course, reading through lots of the others during the day made me feel completely lost and reminded me about 'assumed terminology', f'rinstance to me 'Terminal' is where the trains finally stop...  I'd like to stick with this but at this stage really am a COMPLETE beginner and it's going to take me sometime to even get used to where to find things and the file structure.

But again, thank you for making this a less potentially miserable experience.

---

### Post by bronxbomberz41 on 2009-10-31
Hi,

I'm having an issue with this as well and I'm getting errors with the flash-nonfreebeta.  I tried the ubuntu restricted extras and here is the output i got.  It looks like it failed again.  I've tried this through synaptic as well with no luck.  This is getting a little frustrating.  Everytime there is a flash update or a release update i have issues with flash.  Why can't they just have this figured out?

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 160859 files and directories currently installed.)

Removing flashplugin-nonfreebeta ...

update-alternatives: error: no alternatives for iceape-flashplugin.

update-alternatives: error: no alternatives for iceape-flashplugin.

dpkg: error processing flashplugin-nonfreebeta (--remove):

 subprocess installed pre-removal script returned error exit status 2

postinst called with argument `abort-remove'

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 1

dpkg: libavcodec-extra-52: dependency problems, but removing anyway as you requested:

 mplayer depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 mencoder depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 vlc-nox depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 libquicktime1 depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

 mpd depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:

  Package libavcodec52 is not installed.

  Package libavcodec-extra-52 is to be removed.

Removing libavcodec-extra-52 ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 flashplugin-nonfreebeta
```

---

### Post by bronxbomberz41 on 2009-11-01
Anything?  No matter what I do to try and fix this it always errors on the flash nonfreebeta piece

---

### Post by bronxbomberz41 on 2009-11-04
I was able to fix it by using the following How To and removing the offending broken package from the file var/lib/dpkg/status

[http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/](http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/)

---

