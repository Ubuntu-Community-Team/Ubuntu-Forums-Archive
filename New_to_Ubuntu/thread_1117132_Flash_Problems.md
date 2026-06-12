---
title: "Flash Problems"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by guy_ho on 2009-04-05
I'm running Ubuntu 8.10 and Firefox 3.0.8 on a 64-bit machine. A few weeks ago I did an automatic update, and since then I get blank boxes when using Myspace music player (although I can still hear the music, strangely) and on some sites (e.g. [here]("http://www.asos.com/Men/Clearance/Cat/pgehtml.aspx?cid=3936")). 

I've followed the suggested installation instructions on a lot of different threads to no avail, and would appreciate some help, so please ask me for any details regarding my installation.

Thanks,


Guy

---

### Post by gandaran on 2009-04-05
32-bits or 64-bits ubuntu?

---

### Post by guy_ho on 2009-04-05
My computer's 64-bit, so I tried following the Flash 64-bit installation suggestions, but then I just checked the 'lsb_release -a' and it came back with 'i686', so I guess the Ubuntu installation is i686.

---

### Post by gandaran on 2009-04-05
i686 is 32-bit, try reinstall the flash package, sometimes this works, which one is installed, flashplugin-nonfree or adobe-flashplugin?
and make sure you don't have any open source flash installed like gnash or swfdec and the 64-bits adobe flash.

---

### Post by guy_ho on 2009-04-05
I've currently got flashplugin-nonfree, and I've uninstalled and then re-installed it numerous times while trying different solutions. I don't have gnash or swfdec, and when I put 'flash 64' into Synaptic, the only thing that comes up is 'xserver-xorg-video-apm'.

---

### Post by guy_ho on 2009-04-06
Bump to the top, help appreciated.

---

### Post by metallicamike on 2009-04-06
[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

---

### Post by gandaran on 2009-04-06
post the full output of this code, type in firefox url bar
**about: plugins** (without spaces)
and type this in terminal
**locate libflash**

---

### Post by guy_ho on 2009-04-06
> **metallicamike said:**
> [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

For this one -

sudo apt-get install ia32-libs nspluginwrapper

I got this -

E: Couldn't find package ia32-libs


And for the next part I got - 

guy@guy-desktop:~$ wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
--2009-04-06 21:32:59--  [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
Resolving download.macromedia.com... 88.221.179.191
Connecting to download.macromedia.com|88.221.179.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-04-06 21:33:00 ERROR 404: Not Found.

---

### Post by guy_ho on 2009-04-06
I followed the steps 1 and 1.1 of the myscience link, so all my Flash stuff is long gone.

---

### Post by gandaran on 2009-04-06
> sudo apt-get install ia32-libs nspluginwrapper
the link is for installing flash on 64-bits system, you don't need nspluginwrapper for 32-bits, be-careful about installing a lot of crap, thats why many times flash doesn't work!

---

### Post by guy_ho on 2009-04-06
Ok, so if I've no Flash stuff at all any more what's the best approach from here?

---

### Post by gandaran on 2009-04-06
> **guy_ho said:**
> Ok, so if I've no Flash stuff at all any more what's the best approach from here?
if you system is already fully updated run **sudo apt-get update** then install the flashplugin-nonfree (sudo apt-get install flashplugin-nonfree)  and post the output of the code in firefox url bar after installing flash, test it in firefox first.
```
about:plugins
```

---

### Post by guy_ho on 2009-04-06
Ok, here's what I get in relation to Flash at my aboutplugins page -

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by gandaran on 2009-04-06
> **guy_ho said:**
> Ok, here's what I get in relation to Flash at my aboutplugins page -

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
okay then, still no work? I would still prefer to look into the full plugins output not just the adobe flash.
post also the output of typing in terminal **locate libflash**

---

### Post by guy_ho on 2009-04-06
Myspace music player worked once just then when I tested it, but when I closed the tab and opened the page up again, it was blank.

Here's what happens when I search for plugins -

guy@guy-desktop:~$ locate libflash
/home/guy/.local/share/Trash/files/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
/home/guy/.local/share/Trash/files/libflashplayer-10.2.0.22.87.linux-x86_64.so.tar.gz
/home/guy/.local/share/Trash/files/libflashplayer.so
/home/guy/.local/share/Trash/files/install_flash_player_10_linux/libflashplayer.so
/home/guy/.local/share/Trash/info/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz.trashinfo
/home/guy/.local/share/Trash/info/libflashplayer-10.2.0.22.87.linux-x86_64.so.tar.gz.trashinfo
/home/guy/.local/share/Trash/info/libflashplayer.so.trashinfo
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/libflashsupport.so

---

### Post by gandaran on 2009-04-06
> /usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
get rid of this flashplugin-nonfre-extrasound package, you don't need it!
> /usr/lib/mozilla/plugins/libflashplayer.so
delete this libflashplayer.so file in /usr/lib/mozilla/plugins, this is flash plugin you installed manually, you don't need a double adobe flash install, reinstall the flashplugin-nonfree after deleting this file and restart firefox, it may still not work but I will be back here tomorrow to help.
one question, do you have the flashblock addon installed?

---

### Post by guy_ho on 2009-04-07
I turned off Flashblock (been using it for years) and now all is well. Thanks!

---

