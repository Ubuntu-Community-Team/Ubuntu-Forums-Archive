---
title: "Temperamental flash in 64 bit Karmic"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by futureismo on 2009-11-27
Hi there,
My flash is highly temperamental, some times youtube will play fine, others the buttons such as play/pause will not be pressable and sometimes towards the end of the video it will disappear and be replaced by a grey box.
For some sites flash simply does not work.
[http://www.cambridgescp.com/ws2_tlc/vocab/ocrgcse/OCR_GCSE_Foundation_vocab.html](http://www.cambridgescp.com/ws2_tlc/vocab/ocrgcse/OCR_GCSE_Foundation_vocab.html)
On this flash based page I cannot click any of the buttons. In Opera I can click a button once but after that I have the same problem

I've done a search of the forums and have attempted the advice which seems to be in most posts about flash problems. I've used apt-get purge flashplugin-nonfree a number of times and there don't appear to be any conflicting packages installed (nspluginwrapper etc). I have also seen a post saying this is a well known problem and there are many HOWTOs to fix it, I am posting as I cannot find these and most other posts have slightly different problems.
However being a bit of noob any suggestions are helpful, I may have not done the previous steps correctly.

Thanks

---

### Post by futureismo on 2009-11-27
Very hasty addition. On trying to follow this guide [http://ubuntuforums.org/showthread.php?t=1332870](http://ubuntuforums.org/showthread.php?t=1332870) (tempted by the SOLVED thread title!) I am at the stage of all flash pages hanging for a few seconds and then white boxes appearing where the flash content should be. Flash is by far the most frustrating issue of my move to ubuntu! If only adobe could produce a simple linux flash plugin.

---

### Post by coffeecat on 2009-11-27
That thread is a bit odd. It keeps referring to /usr/lib64/mozilla/plugins/ but I don't have such a directory in my 64-bit system. Not even a /usr/lib64/mozilla. /usr/lib64 is only a symlink to /usr/lib anyway. Are you meant to create the folders? I don't know.

Anyway, this is what works for me. Make a folder ~/.mozilla/plugins and put the libflashplayer.so file in that. Of course, that only works for your user account, but since I am the only user of my machines, I'm content.

---

### Post by futureismo on 2009-11-27
> **coffeecat said:**
> That thread is a bit odd. It keeps referring to /usr/lib64/mozilla/plugins/ but I don't have such a directory in my 64-bit system. Not even a /usr/lib64/mozilla. /usr/lib64 is only a symlink to /usr/lib anyway. Are you meant to create the folders? I don't know.

Anyway, this is what works for me. Make a folder ~/.mozilla/plugins and put the libflashplayer.so file in that. Of course, that only works for your user account, but since I am the only user of my machines, I'm content.

Thanks for your reply although unfortunately that doesn't seem to work for me. I see your point about that thread as well, I reached the point of desperation where I would try anything posted! I think the Ubuntu website could do with a decent flash Installation /FAQ or perhaps a sticky on these forums dedicated to flash. It would make use for first timers like me a lot easier. 
Firefox is still hanging for a couple of seconds and then all flash objects become blank white space, any more suggestions?

---

### Post by futureismo on 2009-11-27
Well I never, I found a solution which has successfully got flash working! Using the .sh file blueridgedog posted in this thread has successfully sorted the problem.
[http://ubuntuforums.org/showthread.php?t=1333858](http://ubuntuforums.org/showthread.php?t=1333858)
Looking at the file I cannot for the life of me work out why that worked when I am fairly certain I had repeated all those steps before, I believe it may have been flash plugin installer which was loitering somewhere in my system or the lines. As at this point I had retraced some of my steps and reinstalled some of the packages in an attempt to see what would work so the output of the file read: 
```
The following packages will be REMOVED
  flashplugin-installer* flashplugin-nonfree* nspluginwrapper*
0 upgraded, 0 newly installed, 3 to remove and 9 not upgraded.

``` Or maybe this had the effect?
```
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```__
Whichever helped I'm now very happy.
Perhaps this or something similar could be posted somewhere official. Would certainly make things alot easier!

Thread will be marked as solved.

---

