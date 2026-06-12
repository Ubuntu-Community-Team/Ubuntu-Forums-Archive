---
title: "[SOLVED] problem seeing shared drive on XP machine"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Stolea on 2008-06-22
I can access my network by going:
Places > Network > Windows Network > IBMPEERS (my workgroup) > Office
When I double click on "Office" nothing shows up even though there are 4 shared drives. If I type "Office_D" after the smb://office/ in the location box it will show that drive and its directories with full read/write access.
Why can't I see the partitions when I double click on "Office"?

---

### Post by Stolea on 2008-06-22
Anyone? I am sure I am not alone with this problem?

---

### Post by timboe on 2008-06-22
> **Stolea said:**
> Anyone? I am sure I am not alone with this problem?

I have the exact same problem, this is more a workaround than a fix but when you put your share in manually and can see it add it as a bookmark.

---

### Post by Stolea on 2008-06-22
Thanks, its better than nothing.:)
I have tried to find anything at all on this problem, but can't seem to find any real answer, neither on how to fix it, or what causes this.

---

### Post by plewisfdx on 2008-06-22
I would suggest mounting it permanently:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

The guide needs to be changed in a few places if you're running hardy.  Replace any instances of "dmask=" with "dir_mode=" and "fmask=" with "file_mode=" then the numbers that follow need a leading 0.  So in the guide it says "dmask=755" change that to "dir_mode=0755".

Then it will be mounted locally forevermore.

I looked into your problem, but I didn't find a suitable answer. 

My guesses for fixing would be googling "samba browsing" and when I did that I found a program called "lisa" was needed, and maybe "fusesmb" but I'm not sure if thats old/bad info.

Automounting it on bootup is the way to go.

---

### Post by Stolea on 2008-06-23
Thanks, it worked a treat.
It took a bit of working out exactly what was meant, but all that command line work from way back when is slowly coming back. And what's more its fun to rediscover something long forgoten.
All I got to do now is work out how to share my /windows folder with XP (see my other post)
I am sure I'll get there :)

---

