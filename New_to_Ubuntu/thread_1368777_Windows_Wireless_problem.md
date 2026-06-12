---
title: "Windows Wireless problem"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by bm14 on 2009-12-31
The other day i was messing with my network connections on windows(vista) trying to be able to hook my laptop up to my friends xbox so he could have live. It never worked, so i shut my computer off and started using linux again. I haven't used windows again until today. When i was on windows, i wasn't able to connect to my wireless network. I tried to diagnose and repair the problem, but none of the solutions work. The wireless does work when I am on ubuntu however. Also, if I am on windows and i plug an ethernet chord in i am able to get internet. Windows said I might have a problem with a network adapter or something. Is there a way to restore my network settings to how they were before i messed with them on vista? For the past 2 and a half hours I have been trying to fix this problem and I have gotten very frustrated so i logged onto Ubuntu to get help. I am not very good with computers, so please make your replies simple to understand.
Thanks in advance

---

### Post by Temposs on 2009-12-31
This problem you're having does not have anything to do with Ubuntu, I think. You might get more help posting in a Windows-oriented forum. Although, someone might be able to help here, as well.

---

### Post by gary0 on 2009-12-31
You could always run system restore in Windows and restore it to a date before you tweaked your network settings...

---

### Post by danastasio on 2009-12-31
we'd love to help... but this is a linux forum. Most of us are not savvy with windows :\

You can try this though
[http://forums.techguy.org/](http://forums.techguy.org/)

---

### Post by LuisGMarine on 2009-12-31
This is the 5th time I've heard someone say Ubuntu or Linux in general has jacked up their wireless on Windows.  There is no way that a default Ubuntu installation would mess with any of your files on windows.  So please don't jump the curve and blame Linux.

Best thing you can do is troubleshoot it like you would on windows if the point and click doesn't work.  Find out the manufacturer to your card, chipset etc ... and then hit google and try to find the "windows" drivers.  Download & install.

I'll look into this more, like I said you are the 5th person.  But as far as I know Ubuntu isn't hoping partitions to mess the other ones up.

---

### Post by danastasio on 2009-12-31
> **LuisGMarine said:**
> This is the 5th time I've heard someone say Ubuntu or Linux in general has jacked up their wireless on Windows.  There is no way that a default Ubuntu installation would mess with any of your files on windows.  So please don't jump the curve and blame Linux.

Best thing you can do is troubleshoot it like you would on windows if the point and click doesn't work.  Find out the manufacturer to your card, chipset etc ... and then hit google and try to find the "windows" drivers.  Download & install.

I'll look into this more, like I said you are the 5th person.  But as far as I know Ubuntu isn't hoping partitions to mess the other ones up.

He never said that Ubuntu messed with his windows settings, he said that HE messed with his windows settings.

> The other day i was messing with my network connections on windows(vista)

---

### Post by bm14 on 2009-12-31
I tried the system restore and it didn't help. However, now I can connect to my neighbor's wireless but not my own, which really confuses me, seeing as all our other computers can. Sorry for posting here i saw a few other windows oriented posts and figured it would be alright to ask here.

---

### Post by baltadt on 2009-12-31
> **bm14 said:**
> I tried the system restore and it didn't help. However, now I can connect to my neighbor's wireless but not my own, which really confuses me, seeing as all our other computers can. Sorry for posting here i saw a few other windows oriented posts and figured it would be alright to ask here.

open a command prompt and type ipconfig /f  I think that is the command to restart the adapter. My wife is having the same problem with her computer and I still haven't figured it out. If all else fails try to turn the power off on the router unplug it for 10 secs then plug back in and turn router back on. then try to connect again. Let me know if it works for you.

---

### Post by tad1073 on 2009-12-31
> **baltadt said:**
> open a command prompt and type ipconfig /f  I think that is the command to restart the adapter. My wife is having the same problem with her computer and I still haven't figured it out. If all else fails try to turn the power off on the router unplug it for 10 secs then plug back in and turn router back on. then try to connect again. Let me know if it works for you.

```
ipconfig /release
```

```
ipconfig /renew
```

---

### Post by tad1073 on 2009-12-31
> **bm14 said:**
> I tried the system restore and it didn't help. However, now I can connect to my neighbor's wireless but not my own, which really confuses me, seeing as all our other computers can. Sorry for posting here i saw a few other windows oriented posts and figured it would be alright to ask here.

reset your router

---

### Post by baltadt on 2009-12-31
ty tad1073.

---

