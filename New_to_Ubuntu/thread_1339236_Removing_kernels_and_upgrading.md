---
title: "Removing kernels and upgrading"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by mydisguise09 on 2009-11-27
kernels:
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04.3 LTS, memtest86+
that's what appears when I press 'Esc' near the start up of the computer

how do I go about removing these and installing, what is it ubunto 9.0.1 or whatever? I don not understand computer talk/jargon so if you could dumb it down please and go step by step that would be appreciated :)

---

### Post by Norm24 on 2009-11-27
Kernals can be removed through sysnaptic.

System>Administration>Synaptic Package Manager

After entering your password go the top right of the window and in quick search type:
```
Linux Image Generic
```

All installed kernals will be listed.Remove the ones you don't want.Good policy to keep the last working kernal in case the newest has issues.

---

### Post by Norm24 on 2009-11-27
I didn't even see the last line in your post.Having not seen it my 1st post is kinda useless,disregard it.Though you can still remove old kernals by following what I posted.

Gonna need more info.Is 8.04 the only OS on your computer?Are you dual booting with a version of Windows?Is there any important files/info you need to save?

If you wish to have the latest version of Ubuntu(9.10),a clean install would probably be best.There are others here who can explain in much simpler terms what's best for you once some more info about your system is given.

---

### Post by BDNiner on 2009-11-27
You can either upgrade your OS to 9.10 using the Update Manager then launch Symantec and remove the old kernels or you can download a new install CD for 9.10, backup your data and perform a clean install. 

I you go the upgrade route you may have to upgrade to 8.10 then 9.04 then 9.10. I am not sure if you can upgrade directly to 9.10 from 8.04.

---

### Post by MiCK.ca on 2009-11-27
word of advise. this may not apply to everyone who "upgrades" but it happened to me. The jump from 9.04 to 9.10 installs a new version/update for gnome. sometimes that upgrade brings problems with your settings. I suggest a new/ fresh install.

according to the Ubuntu upgrade site, you are advised to upgrade version to version...i.e. 8.04 to 8.10 to 9.04 etc. because of packages changes and version changes it is not wise to jump 8.04 to 9.10. If you do, you **WILL** have problems.

---

### Post by Norm24 on 2009-11-27
> **BDNiner said:**
>  

I you go the upgrade route you may have to upgrade to 8.10 then 9.04 then 9.10. I am not sure if you can upgrade directly to 9.10 from 8.04.

You would be correct.You can't do a direct upgrade.

What MiCK.ca suggested is the best route.

But some more info would be helpful before preceeding.

---

### Post by ChrisNZ on 2010-02-06
[COLOR="Black"][COLOR="DarkOrchid"]THis issues is so common that there must be a tip and tricks help file some[/COLOR]where?[/COLOR]

---

### Post by ChrisNZ on 2010-02-06
> **ChrisNZ said:**
> [COLOR="Black"][COLOR="DarkOrchid"]THis issues is so common that there must be a tip and tricks help file some[/COLOR]where?[/COLOR]

has anyone noticede that the message screen is "greyed out and does not actually show what you are typing till you show in "preview"??!

---

