---
title: "firefox/youtube problem"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by jbird999 on 2010-02-03
Hello, I just installed Ubuntu on my Laptop and it came with Firefox. After a long browsing of forums I installed my flash plugins so I could view Youtube videos. Problem is, when I get on a video, I can view the video but after a certain amount of time I can't hit play, pause, or even go on another video without having to refresh the page. Everything else works fine which is why I couldn't find a thread with anything matching this and frankly I do not know if it is a Youtube or a Firefox problem.
 
Please can someone enlighten me?

---

### Post by semi_fiction on 2010-02-03
How did you install the plugin? You might try removing it and installing the ubuntu-restricted-extras package using synaptic.

---

### Post by jbird999 on 2010-02-03
> **semi_fiction said:**
> How did you install the plugin? You might try removing it and installing the ubuntu-restricted-extras package using synaptic.
 I believe it was a sudo command in terminal, saw it here on the forums. All I know is when I put it in it worked.
 
How would I go about removing it?

---

### Post by semi_fiction on 2010-02-03
Crap, nevermind, the youtube thing is happening to me too now! Does anyone know what's up?

EDIT: Are you using 32 or 64 bit? This might help if you're running 64 bit, I'm about to try it and I'll let you know if it works: [http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/)

---

### Post by samantha_ on 2010-02-03
more people seem to be having this on 64-bit systems, but, many have reported that it also works for non-64 bit systems....
try this...

Hit ALT+F2 and enter```

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```
add the following line BEFORE the last line of text
```
export GDK_NATIVE_WINDOWS=1
```
Save.
Restart any applications using flash

EDIT: Try tom.swartz07's instructions first!

---

### Post by tom.swartz07 on 2010-02-03
> **semi_fiction said:**
> Crap, nevermind, the youtube thing is happening to me too now! Does anyone know what's up?

EDIT: Are you using 32 or 64 bit? This might help if you're running 64 bit, I'm about to try it and I'll let you know if it works: [http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/)

Thats the bug associated with 64bit flash on Ubuntu.

**Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players.**

Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type
```
gksu nautilus /usr/lib/flashplugin-installer
```
This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type
```
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

### Post by semi_fiction on 2010-02-03
Thanks Tom, worked like a charm!

---

### Post by tom.swartz07 on 2010-02-03
> **semi_fiction said:**
> Thanks Tom, worked like a charm!

Sweet Deal! Glad to help!

---

### Post by jbird999 on 2010-02-04
Thank you Tom, worked perfectly.

---

