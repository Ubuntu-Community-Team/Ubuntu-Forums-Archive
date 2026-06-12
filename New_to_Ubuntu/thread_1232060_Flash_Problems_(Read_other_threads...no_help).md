---
title: "Flash Problems (Read other threads...no help)"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by coronacolada on 2009-08-05
Okay, I've been working on this for days trying to use other threads and the problem is still not fixed. 

I've got jaunty and both Firefox 3.0.12 and Chromium. Flash is sketch with both of them. I did update from 9.0 r999 to 10.0 r32. First I uninstalled all flash anything and then reinstalled adobe-flashplugin and flashplugin-installer. No help. I took a chance with gnash and it didn't work so I uninstalled that also. 

Now I have both 9.0 and 10.0 installed, and neither work (I keep one disabled). If I have 9.0 enabled, I get a gray box with no content. If I have 10.0 enabled I don't even get a gray box. 

I have the same versions of ubuntu, firefox, and chromium on two other computers and Flash works fine on both of those. 

Any further suggestions? More info. from me? Be happy to help.

-tom

sic luceat lux

---

### Post by Dave.E on 2009-08-05
Thank you Tom!
worked perfectly!
I hope I learn some of these tricks myself before too long!
Cheers
Dave.

---

### Post by coronacolada on 2009-08-05
I wish these suggestions worked for me also! I've been wracking my brain on this for days.

---

### Post by Shig on 2009-08-05
Hi coronacolada

Which files doe you have in your firefox plugins directory?
It should be /usr/lib/firefox-<version>/plugins

Flash is working fine for me (Ubuntu 9.04 x86_64) and all I have is:
```
ls /usr/lib/firefox-3.0.13/plugins
libflashplayer.so
```If you could also provide anything related to shockwave or flash when you browse to ```
about:plugins
``` in firefox that would be helpful too.

---

### Post by coronacolada on 2009-08-05
I have just libflashplayer.so

And quote from about:plugins - 

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

thanks.

-tom

sic luceat lux

---

### Post by LunaticHiatus on 2009-08-05
It might just be easier to do a fresh install, with as much as you have been fiddling with flash. I wouldn't be surprised if you have a weird set up at this point. Then just go to youtube, find the deb package when it doesn't work and install it.

---

### Post by coronacolada on 2009-08-05
I performed a complete removal of Firefox and anything to do with Flash in Synaptic. Then manually deleted all instances of libflashplayer.so that were found in various hidden folders throughout the drive. Then did a complete reinstall of both. The problem persists, exactly as before. 

Although, to be honest, I never could get rid of Shockwave Flash 9.0 r999 - never found the file for it, and it's nowhere in Synaptic. I'm thinking there must be a conflict somehow involving that?

-tom

sic luceat lux

---

### Post by coronacolada on 2009-08-05
(not to mention all "firefox-flashplayer" and "mozilla-flashpler" files found in "alternatives" folders)

---

### Post by Shig on 2009-08-07
Try checking in ~/.firefox/plugins too - to see if any plugins are registered, but as you only have one listing in about:plugins it seems like you don't have any problems with conflicts, the flash plugin is all-inclusive in the libflashplayer.so file, so if you've only got one file, you've only got one version at work.

Try replacing the libflashplayer.so with the one from [this]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz") package, it is the latest version from Adobe. You can copy the libflashplayer.so into the firefox plugins directory, and then browse to about : plugins again, and it should show the new version.

Give it a try and let us know how you travel

---

### Post by missiledave on 2009-08-12
guys, i have tried everything in this thread and this is driving me absolutely up the wall.  this is the third version of ubuntu i have run (jaunty) and the first time i have ever had this problem.  i tried using konqueror with the same result.  flash content is just a grey square with a "play" symbol in it.  when clicked it blanks out to a white square and then just loads into infinity.  what can i do to help you guys help me? i would appreciate the hell out of it.


-edit 1-

ps youtube works fine for some reason...

---

### Post by Shig on 2009-08-14
Seems like you have an add-on installed that blocks flash, like flashblock.
Can you go to tools->add-ons and let us know which add-ons you have installed?

Should (by the sounds of it) just be as simple as uninstalling or upgrading the offending add-on.

---

### Post by missiledave on 2009-08-19
> **Shig said:**
> Seems like you have an add-on installed that blocks flash, like flashblock.
Can you go to tools->add-ons and let us know which add-ons you have installed?

Should (by the sounds of it) just be as simple as uninstalling or upgrading the offending add-on.


sure, i have


Default Plugin

Demo Print Plugin for unix\linux

DIVX Web Player

Quicktime Plug-In 7.2.0

Shockwave Flash

then i have two plugins disabled but installed

VLC Multimedia Plugin (compatible totem 2.26.1)

Windows Media Player Plugin 10 (compatible totem)

dont ask about the windows media player plugin i have no idea how that got there...

---

