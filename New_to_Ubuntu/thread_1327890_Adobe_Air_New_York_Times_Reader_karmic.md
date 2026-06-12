---
title: "Adobe Air New York Times Reader karmic"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-15
Ubuntupals:

My brother wants to use the Adobe Air reader to look at the New York Times. It supposedly runs in linux. We downloaded it from the Times website and attempted to install. Looks like it installed something, But nothing runs. Does anybody know if this works in Karmic 64 bit?

---

### Post by ArinSky on 2009-11-15
> **dndrich said:**
> Ubuntupals:

My brother wants to use the Adobe Air reader to look at the New York Times. It supposedly runs in linux. We downloaded it from the Times website and attempted to install. Looks like it installed something, But nothing runs. Does anybody know if this works in Karmic 64 bit?

;-; adobe air... it definitely can run on jaunty (sorry for the cry face, i have bad experiences with adobe air) though i just used wine, installed it on windows and copied it over.

i dual boot for versatility ^.~ windows = storage bin

---

### Post by Meskarune on 2009-11-15
have you installed air from synaptic?

---

### Post by dndrich on 2009-11-15
Didn't even know it was there. I'll try that.

---

### Post by Locke_99GS on 2009-11-16
Get Adobe Air from here: [http://get.adobe.com/air/](http://get.adobe.com/air/)

Add xattr to the file:
```

chmod +x AdobeAIRInstaller.bin

```

Run the installer:
```

sudo ./AdobeAIRInstaller.bin

```

After Air is installed, just double click on an air package to install it.

---

### Post by wilee-nilee on 2009-11-16
I installed the the reader on a 32bit all from the website air installed with NY times link.

---

### Post by dndrich on 2009-11-16
OK, I tried the above, but the Times reader does not install. Not sure what to do next. I installed Air, I think, at least it looks like it installed. But the Times Reader also tries to reinstall Air for some reason. Perhaps that is the problem?

---

### Post by wilee-nilee on 2009-11-16
Here is a link to some common questions about the time reader.
[http://www.nytimes.com/membercenter/faq/timesreader.html](http://www.nytimes.com/membercenter/faq/timesreader.html)

I just searched Google with times reader linux 64 bit so far what I have seen is that it should work, I wonder if it is the Adobe air that is the problem. So searching Google again with adobe air linux 64 bit I found this.
[http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

I would search around more but it appears that there isn't a 64 bit for Linux but the 32 bit can be installed but the question arises that will the time reader work with this set up and is this correct information.

---

### Post by dndrich on 2009-11-16
OK, well, this is useful. I seem to be able to get Air installed manually. The issue so far was using the New York Times download which tries to install automatically. But it looks like I can download the Times Reader package manually. So, when I get home later to my Karmic box I will try to install Air again manually, and then Times Reader package manually and see what happens.

---

### Post by dndrich on 2009-11-16
OK, I tried to do the instructions found here:

[http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

Now, these are for Jaunty, but apparently work in Karmic?

So, it appears to have installed Adobe Air, but when I try to install the package it fails. So, I ran the Adobe Air Application installer in terminal, and this is what I get:

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

Now, I pick the file to install, which is an air package, and it fails. The terminal quits also, so I can't see what happened. Thoughts?

---

### Post by Locke_99GS on 2009-11-19
It doesn't appear to like the 64bit install that I reckon you used. Try the 32bit version.

---

### Post by dndrich on 2009-11-19
In the words of Homer Simpson...duh oh! So that is what the 32 bit libraries were for! I'll try the 32 bit version and see if that flies.

---

### Post by dndrich on 2009-11-19
OK, as it turns out, there is no 64 bit version! I was using the 32 bit version all along. I can't make it run, sadly. Same output as before.

---

### Post by agolin on 2012-07-11
This isn't necessarily specifically relevant to 64 bit questions but if anyone is having trouble generally getting the download from the NYTimes site to work, follow the instructions on getting AIR set up here: 

[http://www.liberiangeek.net/2012/04/install-adobe-flash-reader-air-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-adobe-flash-reader-air-in-ubuntu-12-04-precise-pangolin/)

and then just download from Softpedia:

[http://linux.softpedia.com/get/Adobe-AIR-Apps/Internet-Tools/New-Your-Times-Reader-47857.shtml](http://linux.softpedia.com/get/Adobe-AIR-Apps/Internet-Tools/New-Your-Times-Reader-47857.shtml)

The Reader 2.0 application itself wasn't great for me, a little buggy and the fonts look like hell. The Chrome app is nicer and can easily be made into a chromeless Application Shortcut.

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

