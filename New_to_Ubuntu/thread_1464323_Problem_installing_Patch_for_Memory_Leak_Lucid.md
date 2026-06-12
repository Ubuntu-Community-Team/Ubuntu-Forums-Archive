---
title: "Problem installing Patch for Memory Leak Lucid"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by mikesol on 2010-04-28
Hello guys, 

I've installed Kubuntu 10.04 RC two days ago and how many of you know, there is a problem with a memory leak in Xorg server ([https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)).

In the wiki, they propose a patch from ppa:ubuntu-x-swat/x-updates. I need the patch for intel video card. Currently i have the 2.9.1 version of xserver-xorg-video-intel but the patch it's in the ppa like 2.9.0-1ubuntu2~xup~3. 

My problem it's Kubuntu uses Kpackagekit for install the updates and it just takes the lastest version of each package and i haven't found how to force a downgrade for the patch.

Thanks for any help.

Best Regards

---

### Post by Jon Monreal on 2010-04-29
You could try

```
apt-get install xserver-xorg-video-intel=2.9.0-1ubuntu2~xup~3
```

but if it's supposed to be fixed with today's release, I would just wait for that and then update. Wouldn't want to mess anything up in the process.

---

### Post by cuberts on 2010-04-29
> **mikesol said:**
> Hello guys, 

I've installed Kubuntu 10.04 RC two days ago and how many of you know, there is a problem with a memory leak in Xorg server ([https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)).

In the wiki, they propose a patch from ppa:ubuntu-x-swat/x-updates. I need the patch for intel video card. Currently i have the 2.9.1 version of xserver-xorg-video-intel but the patch it's in the ppa like 2.9.0-1ubuntu2~xup~3. 

My problem it's Kubuntu uses Kpackagekit for install the updates and it just takes the lastest version of each package and i haven't found how to force a downgrade for the patch.

Thanks for any help.

Best RegardsMaybe your memory is over loaded, and I cannot hold that OS anymore

---

