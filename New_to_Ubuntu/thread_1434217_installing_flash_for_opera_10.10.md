---
title: "installing flash for opera 10.10"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by samMD on 2010-03-20
i attempted to install a .deb file from adobe site to install the flash plugin for opera 10.10, but it didnt work and youtube still tells me to get flash player.

any help on this?

---

### Post by werecatomega on 2010-03-20
have you tried installing the flash plugin from the ubuntu software center?

---

### Post by The Real Dave on 2010-03-20
According to [Adobe's site]("http://www.adobe.com/products/flashplayer/systemreqs/#os"), Flash 10 for Linux isn't compatible with Opera. You might wanna search the software centre for "Flash" and see what crops up. I think also that the latest beta version of Flash supports Opera, but I could be wrong.

Sorry I can't help more :(

---

### Post by 3rdalbum on 2010-03-20
Flash 10 is definitely compatible with Opera. But you need to tell Opera to use it; I can't remember what I had to do. I think it might be under Tools > Advanced > Blocked Content possibly, it might literally "block" Flash movies by default.

---

### Post by samMD on 2010-03-20
ok thanks i will check it out and let you guys know


*UPDATE*: I can hear the video running on youtube in opera but there is no video, in place of the video is the list of results from the previous page

---

### Post by samMD on 2010-03-22
bump, i even downloaded the 10.51 RC for deb  i can hear video on youtube but cant see it but on other video sites flash doesnt work like on MSNBC i go into preferences and see opera detects all the plugins available and is in the correct folder so whats going on?

---

### Post by mkvnmtr on 2010-03-22
You will find that if you use the repositories for things you will have a lot more luck. I just tried my Opera and You Tube flash works just fine. I installed Opera after I had downloades flash from the synaptic package manager for Firefox and Seamonkey. Opera found and used that flash with no problems.
Normally it is a bad idea not to check the packagemanager first when you need a program. They do a lot of work to set up a safe and reliable system to download software and scrounging of the internet will quite often foul up your system,

---

### Post by stinkeye on 2010-03-22
Check your plugin path in tools > preferences > advanced > content > plugin options

I set it to use the /usr/lib/adobe-flashplugin folder
so I know it's only picking up adobe flash

---

### Post by TBABill on 2010-03-22
Worst case, just purge your current Flash install you attempted, then just sudo apt-get install flashplugin-nonfree. 64-bit is different, but I didn't see any mention of you having a 64-bit Ubuntu. Easiest way is to just open software center, search for flash and install....or just install the Ubuntu extras non-free (not sure that's the exact name, but it's something similar).

---

### Post by samMD on 2010-03-22
I solved the issue: "O Menu"--->"settings"--> "preferences"-------> "advanced"----> "content"--> "plug-in options"-----> "change path" 

make sure the only boxed that is checked is for the directoy:  /usr/lib/plugin-installer

opera can now play ALL sites!! :popcorn::popcorn::D

P.S this can also work for the new 10.51 RC for linux :) which you can download here: [http://my.opera.com/desktopteam/blog/2010/03/20/new-opera-unix-packages-arrive-deb-rpm-tar]("http://my.opera.com/desktopteam/blog/2010/03/20/new-opera-unix-packages-arrive-deb-rpm-tar")

---

