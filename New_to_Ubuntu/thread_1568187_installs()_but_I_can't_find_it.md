---
title: "installs(?) but I can't find it"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by critin on 2010-09-04
I've used Wubi before with no problems, and want to add it to Windows XP inside Windows.  I've tried to install Wubi for two days and finally it says it installed and needed to restart.  Upon restarting, there is no place to open it.  

I searched and found three (small) entries for Wubi in local/temp files.  Two entered today and one of a couple years ago.
Ubuntu 10.04.1-rev 190 shows in Add/Remove control.

I've followed instructions but it just won't install properly.

2 GB Ram  XP Home

Yesterdsy it found remnants of formerly installed Wubi and I deleted all I could find.  This install seemed to be clean, but I did find a small older entry inside the local/temp file.  Could that be the issue?

Thanks for any suggestions,
critin

---

### Post by garvinrick4 on 2010-09-04
> **critin said:**
> I've used Wubi before with no problems, and want to add it to Windows XP inside Windows.  I've tried to install Wubi for two days and finally it says it installed and needed to restart.  Upon restarting, there is no place to open it.  

I searched and found three (small) entries for Wubi in local/temp files.  Two entered today and one of a couple years ago.
Ubuntu 10.04.1-rev 190 shows in Add/Remove control.

I've followed instructions but it just won't install properly.

2 GB Ram  XP Home

Yesterdsy it found remnants of formerly installed Wubi and I deleted all I could find.  This install seemed to be clean, but I did find a small older entry inside the local/temp file.  Could that be the issue?
Thanks for any suggestions,
critinWhat version are you trying to install? Oh I see 10.04 Should be in C: drive right next to Users in its own folder. And be a choice as boot.

---

### Post by critin on 2010-09-04
<<Should be in C: drive right next to Users in its own folder. And be a choice as boot.>>

Thanks,

The folder is inside C: and holds the stuff to install, but I  can't do it.  The items are on unreadable pages, there are no  instructions.

It is not listed next to the Users because it hasn't actually finished installing.

Other suggestions?  

Wubi is supposed to auto install Ubuntu for the user. it isn't.  

critin

---

### Post by garvinrick4 on 2010-09-04
> **critin said:**
> <<Should be in C: drive right next to Users in its own folder. And be a choice as boot.>>

Thanks,

The folder is inside C: and holds the stuff to install, but I  can't do it.  The items are on unreadable pages, there are no  instructions.

It is not listed next to the Users because it hasn't actually finished installing.

Other suggestions?  

Wubi is supposed to auto install Ubuntu for the user. it isn't.  

critin It is suppose to be installed from the cd you made. The folder is nothing to be looked into at all. Only if you want to uninstall completely should be an uninstall if you click on folder. 
How it is suppose to go:
Put in cd then click on WUBI:
Tell it how much space to use up to 30 gig.
Give it your user name and password:
Click install
And that is it, when through with install suppose to have a selection when you reboot to choose Windows or Ubuntu.

---

### Post by critin on 2010-09-05
The wubi I used a few years ago included the OS so that I only had to use Wubi to install ubuntu.  The one I used today and yesterday apparently are using the 64 bit, when I have 32 bits.  I've been trying to research issues, and am looking for earlier versions of wubi with earlier ubuntu that gives me the choice of 32 bits.  This one doesn't allow me to choose.  That is probably the problem, but it's frustrating to not be able to find what I need.

I can't make a cd which is why I'm trying to get wubi to work--it was so easy when I used it a few years ago.  The wubi pages say it still works the same way, but I can't use the 64 bit version.

Thanks for responding, I appreciate it.

---

### Post by bcbc on 2010-09-05
Download the .iso version you want, place it in the same folder as [wubi.exe]("http://wubi-installer.org/") and run it. Then it will use the one you selected. 

Make sure that the .iso is the same release as wubi.exe (10.04.1 is current) as not all flavours of ubuntu are at 10.04.1 (e.g. netbook-edition, xubunt etc). These will not work with the current wubi.exe .

---

