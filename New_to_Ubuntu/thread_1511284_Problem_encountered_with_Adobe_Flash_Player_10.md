---
title: "Problem encountered with Adobe Flash Player 10"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by JohnFDay on 2010-06-16
I'm running Ubuntu 10.04 LTS on an old DELL Desktop.  It installed fine, and I downloaded the latest Adobe Flash Player 10. It seemed to install A-OK but now it won't let me get any Ubuntu updates and it says that the Adobe Flash Player needs to be uninstalled and then re-installed. However, I can't get it to uninstall.

Any idea what to do about this problem?  

I'm pretty much at my wits' end trying to solve this one.  

Any help will be appreciated!

Thanks in advance.
John F. Day

---

### Post by Cavsfan on 2010-06-16
Try this site. It worked for me.

_[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)_

(Pay no attention to the fact it says 64bit it is only 32 bit as that is all Adobe is offing right now)

---

### Post by Cavsfan on 2010-06-16
Test it on YouTube and if you find that the pause, stop, volume, full screen and other buttons 
do not work, here is the solution:

_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

 I only had to perform step 3 of the above workaround to get my flash to work perfectly.

---

### Post by Cavsfan on 2010-06-16
If there is any confusion about the steps, here are the commands:

Download the file to your desktop by clicking on the link above where it says "here"

Then enter in a terminal:

```
cd Desktop
tar xvzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

cd
mkdir -p .mozilla/plugins

mv Desktop/libflashplayer.so .mozilla/plugins 

Then restart firefox. Go to about:plugins to see if it&#8217;s enabled:
```
It should say:
**[SIZE=1]Shockwave Flash[/SIZE]**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version:   Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-06-19
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Cavsfan on 2010-06-20
> **lovinglinux said:**
> Install [FLASH-AID]("http://flash-aid-extension.blogspot.com") extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR=Sienna]**Flash Optimization**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

You da man!

---

### Post by JohnFDay on 2010-06-25
To everyone who replied to my message:    Thanks boatloads!  I tried everything that was offered, with zero success.  I unloaded 10.04, then re-installed it.  For some reason, this time it worked okay.  I can't explain why....all I know is the problem is now gone.

Again, thanks to all!

Oh, one more thing....How do I put an official "end" to this thread so nobody wastes his/her time answering???

---

### Post by Cavsfan on 2010-06-25
> **JohnFDay said:**
> To everyone who replied to my message:    Thanks boatloads!  I tried everything that was offered, with zero success.  I unloaded 10.04, then re-installed it.  For some reason, this time it worked okay.  I can't explain why....all I know is the problem is now gone.

Again, thanks to all!

Oh, one more thing....How do I put an official "end" to this thread so nobody wastes his/her time answering???

You are very welcome! There are a lot of helpful people on this forum.

To solve this thread, just click on [COLOR=Red]Thread Tools[/COLOR] at the top right and then at the bottom of the list it should 
say [COLOR=Red]Mark this thread as Solved[/COLOR]

---

