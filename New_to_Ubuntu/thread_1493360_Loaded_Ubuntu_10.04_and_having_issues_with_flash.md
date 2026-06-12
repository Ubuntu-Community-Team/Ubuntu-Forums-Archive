---
title: "Loaded Ubuntu 10.04 and having issues with flash"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by ali_williams on 2010-05-25
So I have tried some of the things I saw on the the forum already like removing flash and reinstalling it. I also loaded flash-aid on firefox, google chrome, and ran the following command sudo apt-get install ubuntu-restricted-extras

and I keep getting the same issue which is when i view a video on youtube or hulu i can not control the video so i can not turn up the volume, pause the video, or skip ahead to different parts in the video when I had this problem in the past I just reinstall flash and it worked but it doesnt seem to be the silver bullet this time so any ideas guys?

---

### Post by -humanaut- on 2010-05-25
Check synaptic and make sure the 64bit Flash Alpha version is removed from your system. Then reinstall with ubuntu-restricted-extras which will download and install the 32bit version with ndiswrappers. The 32bit & 64bit versions cannot co-exist together.

---

### Post by lovinglinux on 2010-05-25
> **-humanaut- said:**
> Check synaptic and make sure the 64bit Flash Alpha version is removed from your system. Then reinstall with ubuntu-restricted-extras which will download and install the 32bit version with ndiswrappers. The 32bit & 64bit versions cannot co-exist together.

FLASH-AID should take care of that, since it removes any conflicting plugins.

> **ali_williams said:**
> So I have tried some of the things I saw on the the forum already like removing flash and reinstalling it. I also loaded flash-aid on firefox, google chrome, and ran the following command sudo apt-get install ubuntu-restricted-extras

and I keep getting the same issue which is when i view a video on youtube or hulu i can not control the video so i can not turn up the volume, pause the video, or skip ahead to different parts in the video when I had this problem in the past I just reinstall flash and it worked but it doesnt seem to be the silver bullet this time so any ideas guys?

Those symptoms are common when you use the 32bit version of flash on a 64bit system. Load [FLASH-AID](http://flash-aid-extension.blogspot.com/) again. If it prompts for the 64bit beta version, then install it. Don't forget to restart Firefox after installing the new flash version and don't run "sudo apt-get install ubuntu-restricted-extras" after executing FLASH-AID, otherwise it will install the 32bit version again.

If that doesn't work, type this command and post the output here:

```
locate libflashplayer.so
```

---

### Post by celem on 2010-05-25
Ditto - 10.04 running 64-bit Firefox 3.6.3 e/w Shockwave Flash 10.0 r45 plays all flash that I throw at it except:
[http://media.celebritycruises.com/celebrity/content/swf/homepage/shell.swf?t=05252010%20081340]("http://media.celebritycruises.com/celebrity/content/swf/homepage/shell.swf?t=05252010%20081340")

This plays fine in Konqueror but crashes when the flash fully loads, just as it is about to play. I used FLASH-AID to verify no conflicts and the latest flash plugin but no joy.

---

### Post by lovinglinux on 2010-05-25
> **celem said:**
> Ditto - 10.04 running 64-bit Firefox 3.6.3 e/w Shockwave Flash 10.0 r45 plays all flash that I throw at it except:
[http://media.celebritycruises.com/celebrity/content/swf/homepage/shell.swf?t=05252010%20081340]("http://media.celebritycruises.com/celebrity/content/swf/homepage/shell.swf?t=05252010%20081340")

This plays fine in Konqueror but crashes when the flash fully loads, just as it is about to play. I used FLASH-AID to verify no conflicts and the latest flash plugin but no joy.

It works fine for me on Firefox 3.6.5pre 64bit with the latest beta plugin. Check if you have libmoon installed and remove it. This will prevent you from viewing Silverlight content.

---

### Post by ali_williams on 2010-05-26
> **lovinglinux said:**
> It works fine for me on Firefox 3.6.5pre 64bit with the latest beta plugin. Check if you have libmoon installed and remove it. This will prevent you from viewing Silverlight content.

dude that fixed it youtube but hulu doesnt work... argh!!!

---

### Post by lovinglinux on 2010-05-26
> **ali_williams said:**
> dude that fixed it youtube but hulu doesnt work... argh!!!

Hulu seems to have issues with the 64bit version. Anyway, I can't access Hulu here, but there are [plenty of threads about it](http://www.google.com/search?q=hulu+site%3Aubuntuforums.org).

---

### Post by celem on 2010-05-27
Guess what? I did a reboot and it now works. Go figure.

---

