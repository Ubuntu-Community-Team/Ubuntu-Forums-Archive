---
title: "mozilla firefox is too slow when flash games are played"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-21
whenever i try to play some flash games in facebook ,the firefox seems to be very very slow(in ubuntu 8.1).. i have winXP installed in my system, i use firefox there too, there in winxp firefox works really well.. its very fast.. but here in ubutu i have real serious issues with firefox... can somebody please help me on this..
this is the version am using

Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

---

### Post by fooman on 2009-01-21
try the flash plugin for 64 bit.  first,  go to synaptic and uninstall any flash/gnash stuff that is already installed.  then go here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

scroll down and click the "download 64 bit plugin for linux"

after it downloads,  right click on the file and choose "extract here".  that will extract a single file..."libflashplayer.so"

open home folder and in the toolbar, click "view" and put a check next to "showhidden files"..... copy the "libflashplayer.so" to /home/<user name>/.mozilla/plugins"

see if thats any better.

---

### Post by computermacgyver on 2009-01-21
What version of Flash do you have installed? Type "about:plugins" into Firefox to find out. 

I have had some issues with Flash 10, although the previous version was working fine. There is also a build of firefox (swiftfox, [http://getswiftfox.com/](http://getswiftfox.com/) ) that is optimized for linux. This helped me recduce lag too.

---

### Post by chethankrish on 2009-01-21
> **computermacgyver said:**
> What version of Flash do you have installed? Type "about:plugins" into Firefox to find out. 

I have had some issues with Flash 10, although the previous version was working fine. There is also a build of firefox (swiftfox, [http://getswiftfox.com/](http://getswiftfox.com/) ) that is optimized for linux. This helped me recduce lag too.

where can i find the installed flash version ?

---

### Post by fooman on 2009-01-21
go to system > administration > synaptic package manager

click the "search" button and type "flash"

you should see the choices for flash...right click on any that are installed and choose "mark for removal".  click "apply" in the toolbar.  then search for "gnash" and do the same if any of those are installed.

---

### Post by computermacgyver on 2009-01-21
sorry the smile got in the way of my post. Type
```

about:plugins

```
into the url bar in Firefox. (You can also check the package manager as suggested, but this will simply tell you what is installed, not what Firefox is configured to use)

To others working on this thread, please see: 
[http://ubuntuforums.org/showthread.php?t=1046206](http://ubuntuforums.org/showthread.php?t=1046206)
For more on the same issue.

---

### Post by chethankrish on 2009-01-21
> **fooman said:**
> try the flash plugin for 64 bit.  first,  go to synaptic and uninstall any flash/gnash stuff that is already installed.  then go here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

scroll down and click the "download 64 bit plugin for linux"

after it downloads,  right click on the file and choose "extract here".  that will extract a single file..."libflashplayer.so"

open home folder and in the toolbar, click "view" and put a check next to "showhidden files"..... copy the "libflashplayer.so" to /home/<user name>/.mozilla/plugins"

see if thats any better.

 i did all that you said, but in  /home/krsna/.mozilla  there is no folder or file called plugins.. you are asking me to copy the downloaded file to this location.. but plugins does not seem to exist..

---

### Post by fooman on 2009-01-21
create it.

right click in an empty space in " /home/krsna/.mozilla" and choose "create folder"...name it "plugins" (no quotes of course).

then copy the file to that folder.

hope that helps.

---

### Post by chethankrish on 2009-01-21
> **fooman said:**
> create it.

right click in an empty space in " /home/krsna/.mozilla" and choose "create folder"...name it "plugins" (no quotes of course).

then copy the file to that folder.

hope that helps.

i created a new folder named plugins and copied the downloaded file there.. i restarted firefox.. now when i try to open any flash games, my firefox is freezing.. it stops responding for a while or so.. i tried this some 4 times and all the four time the same thing happened.. firefox stopped responding for a whle(say some 15seconds).. and the flash games are also not getting opened.. can you please help me now..

---

### Post by fooman on 2009-01-21
what video card are you using and ...do you have your video card drivers installed/enabled?  if not....

go to system > administration > hardware drivers

if there are video drivers listed,  enable them.

btw...it is simple to undo what we did with flash (though it should not be the problem).  just go to the plugins folder,  right click on the file and choose "move to trash".  then you can reinstall the synaptic version.

---

### Post by chethankrish on 2009-01-21
> **fooman said:**
> what video card are you using and ...do you have your video card drivers installed/enabled?  if not....

go to system > administration > hardware drivers

if there are video drivers listed,  enable them.

btw...it is simple to undo what we did with flash (though it should not be the problem).  just go to the plugins folder,  right click on the file and choose "move to trash".  then you can reinstall the synaptic version.

i have nvidia 1GB graphics card.. the drivers are enabled.. i checked the same in system > administration > hardware drivers

i deleted the folder which we had created.. now what do i do?

---

### Post by fooman on 2009-01-21
open synaptic,  search for and install "ubuntu-restricted-extras"

see if that helps.

---

### Post by temporary11 on 2009-01-21
**Use flash v9 instead of v10 is the best solution for me**
try this:
**1**- uninstall all current flash plugin for firefox
**2**- install manually flash v10 from tar.gz
**3**- use sudo to copy libflashplayer.so OF FLASH V9 to /usr/lib/firefox-3.0.5/plugins (OVERWRITE libflashplayer.so of flash v10 of course)
I'm noob here, I don't know why I can't directly install flash v9

[B]flash v9 download here: [http://www.filewatcher.com/m/install_flash_player_9_linux.tar.gz.2608602.0.0.html](http://www.filewatcher.com/m/install_flash_player_9_linux.tar.gz.2608602.0.0.html)
flash v10 tar.gz file can be downloaded from adobe site[/B]
(link from a user of ubuntuforums.org, I don't remember)

hope this help

*edit: the tar.gz flash v9 from mediafire is not complete, use link edited above*

---

### Post by computermacgyver on 2009-01-21
> **computermacgyver said:**
> 
I have had some issues with Flash 10, although the previous version was working fine. 

> **temporary11 said:**
> Use flash v9 instead of v10 is the best solution for me


Yes, I would definitely try version 9 instead of 10. It works much better for me too. If you have a 64-bit architecture, just make sure you grab the 64-bit version.

---

