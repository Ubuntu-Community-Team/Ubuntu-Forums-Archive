---
title: "Flash not responding on some websites"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by N_L on 2009-12-28
I'm using 64 bit version of ubuntu 9.10 and I installed flash plugin for mozzila from ubuntu software center.

I can open some videos just fine but some aren't responsive for mouse click. Like on youtube i can't press pause, volume or anything but I can pause/play with space key.
And then I open different video and all works fine.

Anyone got clue what might be problem?

---

### Post by tom.swartz07 on 2009-12-28
**[COLOR="Red"]UPDATE: 05/02/10- I have added a complete script for this process. If you would like to use the script, please download it from my Launchpad account; [http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/download/head%3A/x64flashinstaller-20100502230034-ngskmemxsovq6oe9-9/x64%20Flash%20Installer](http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/download/head%3A/x64flashinstaller-20100502230034-ngskmemxsovq6oe9-9/x64%20Flash%20Installer)[/COLOR]**

Thats the bug associated with 64bit flash on Ubuntu.

Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players.

There is a really dead simple script that you could use to remove the offending programs, highlighted here: [http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)


Once everything is all removed, you could start fresh and get the official Flash plugin.


Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type ```
gksu nautilus /usr/lib/flashplugin-installer
```
This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type ```
gksu nautilus /usr/lib/mozilla/plugins
```
Paste the same file into this folder, again agreeing to overwrite the current version 

Theres a PPA if you want to use it to keep your flash updated
```
sudo add-apt-repository ppa:sevenmachines/flash 
```

If you are still having problems, update it with 
```
sudo apt-get update && sudo apt-get install flashplugin64-installer
```

---

### Post by tom.swartz07 on 2009-12-28
Also, if you middle click and left click at the same time, it works well too.
:popcorn::lolflag:

---

### Post by N_L on 2009-12-28
Thanks, gonna try it now.

And no middle click on my laptop :(

---

### Post by tom.swartz07 on 2009-12-28
> **N_L said:**
> Thanks, gonna try it now.

And no middle click on my laptop :(

Great! Let us know if it works and solves your problem!

PS- 'middle click' on a laptop is both left and right click at the same time, you could hold those down and tap the touchpad to click.
I was using that method until I hunted down this way to fix it.

---

### Post by N_L on 2009-12-28
It seems to be fixed, thanks!
But I had to remove flash I downloaded from ubuntu software center to get it to work, was giving me just white window with it still installed.

Also I can't seem to make middle mouse thing work correctly, if I somehow get it it still opens in main page(trying to open in new tab with middle click, and it opens+opens in same tab) but doesn't matter, glad flash works.
Thanks again ;)

---

### Post by Sef on 2009-12-28
Thank you Tom.   That has fixed the same problem for me.

---

### Post by tom.swartz07 on 2009-12-28
> **N_L said:**
> It seems to be fixed, thanks!
But I had to remove flash I downloaded from ubuntu software center to get it to work, was giving me just white window with it still installed.

Also I can't seem to make middle mouse thing work correctly, if I somehow get it it still opens in main page(trying to open in new tab with middle click, and it opens+opens in same tab) but doesn't matter, glad flash works.
Thanks again ;)

Great! Ill make a note that the old version of flash has to be un-installed first.


Happy Holidays!

---

### Post by Sef on 2009-12-28
> Great! Ill make a note that the old version of flash has to be un-installed first.


Happy Holidays!

I did not need to uninstall flash.  Just followed your directions. 

Happy Holidays to you and all.

---

### Post by hreikin on 2009-12-28
> **tom.swartz07 said:**
> long post

very helpful, got flash working again for me however i have 1 small problem :(

when watching videos on iplayer/youtube the sound is like 1 second behind the video, its nothing amazingly annoying but its noticeable :P

any help appreciated

---

### Post by Sef on 2009-12-28
**hreikin** > when watching videos on iplayer/youtube the sound is like 1 second behind the video, its nothing amazingly annoying but its noticeable Please start a new thread for that problem.  You may link here if you wish.  thank you.

---

### Post by psychlic on 2010-05-23
> **tom.swartz07 said:**
> **[COLOR="Red"]UPDATE: 05/02/10- I have added a complete script for this process. If you would like to use the script, please download it from my Launchpad account; [http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/download/head%3A/x64flashinstaller-20100502230034-ngskmemxsovq6oe9-9/x64%20Flash%20Installer](http://bazaar.launchpad.net/~tom-swartz07/%2Bjunk/main/download/head%3A/x64flashinstaller-20100502230034-ngskmemxsovq6oe9-9/x64%20Flash%20Installer)[/COLOR]**


Hey Tom

Just wanted to say thanks very much for posting the script.  I used it and it worked perfectly :guitar:

To anyone else having this problem I can vouch for Tom's script 100%.

Have a good one

psychlic

---

