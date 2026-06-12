---
title: "Installing Flash 10"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by ovid9 on 2009-12-12
Ok, I don't know why this is so hard, but its fighting me.  Big surprise.  I'm trying to upgrade to flash 10.  

First, I ran:
> sudo apt-get remove flashplugin-nonfree

Then, I downloaded Flash 10 and ran the installer.

However, when i got to about:plugins, it shows as flash 9 and it won't work on sites requiring flash player 10.

What have I missed here?

Oh, I have shut down FF while doing that and since rebooted.

Thanks.

---

### Post by jwh400 on 2009-12-12
I have always downloaded the .deb file from Adobe then used the GDebi Package Installer to install. 
I've had no problems so far.

---

### Post by Norm24 on 2009-12-12
Run update manager.The latest updates include it.

---

### Post by ovid9 on 2009-12-12
Thanks.   I have run update manager.  It shows it installed.  But my Firefox still shows Flash 9.  Which I don't understand cause I removed that when i removed the flash-nonfree thing.  

So, I show 10 installed in synaptic, but my Firefox still shows 9.06.

---

### Post by Norm24 on 2009-12-12
> **ovid9 said:**
> Thanks.   I have run update manager.  It shows it installed.  But my Firefox still shows Flash 9.  Which I don't understand cause I removed that when i removed the flash-nonfree thing.  

So, I show 10 installed in synaptic, but my Firefox still shows 9.06.

That is odd.My FF shows 10.0 r42.

But I did find this thread:
[http://ubuntuforums.org/showthread.php?t=1349360&highlight=flash+plugin](http://ubuntuforums.org/showthread.php?t=1349360&highlight=flash+plugin)

---

### Post by mcdjork on 2009-12-12
Make sure there is no libflashplayer.so in your ~/.mozilla/plugins directory. Maybe the older version is there. Also check your /usr/lib/firefox/plugins directory. If it's there, just delete the file.

---

### Post by ovid9 on 2009-12-12
Ah hah!  

Ok, I was doing too many things at once.  I was also getting FF3.5.  Well, in 3.5 its Flash 10.  

So, I think I'm all set now.  I'm not exactly sure how I got the steps crossed, but I now have FF3.5 with Flash 10.  

Thank you all so much!

---

