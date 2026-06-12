---
title: "Some Flash functionality not working"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by John.b.Goode on 2010-11-22
Hello,
Up until today, I've been using Ubuntu 10.04. I upgraded today because I've been having Flash issues, and I hoped that a semi-clean install would help, but it didn't. Here's a bit of background:
I print sheet-music off of a site called CCLI, which uses a Flash application to display, and allow manipulation of, the music before printing. Recently I lost the ability to use this application. I will get a loading screen, and then it will freeze there.
I tried re-installing Flash, and purging and then installing it, but to not avail. I tried installing flash on the live CD (actually USB key), and it worked there, but now that I've installed it on the hard drive, it once again doesn't work.
A very important fact here is that I didn't do an upgrade, but I did do a "dirty" install, where I kept my home directory the same, preserving settings that way. This leads me to believe that there is a setting that is messed up, but I have no idea where to begin trying to fix the problem. Any help would be appreciated. Peace!

---

### Post by bioterror on 2010-11-22
> **John.b.Goode said:**
> Hello,
Up until today, I've been using Ubuntu 10.04. I upgraded today because I've been having Flash issues, and I hoped that a semi-clean install would help, but it didn't. Here's a bit of background:
I print sheet-music off of a site called CCLI, which uses a Flash application to display, and allow manipulation of, the music before printing. Recently I lost the ability to use this application. I will get a loading screen, and then it will freeze there.
I tried re-installing Flash, and purging and then installing it, but to not avail. I tried installing flash on the live CD (actually USB key), and it worked there, but now that I've installed it on the hard drive, it once again doesn't work.
A very important fact here is that I didn't do an upgrade, but I did do a "dirty" install, where I kept my home directory the same, preserving settings that way. This leads me to believe that there is a setting that is messed up, but I have no idea where to begin trying to fix the problem. Any help would be appreciated. Peace!

On my laptop looks like this:
```

$ ls .adobe/
Flash_Player

```

So how about a little nice command like:
```
rm -rf ~/.adobe/
```

Might work, becouse that directory is just full of some random cache stuff, which may cause your problem.

---

### Post by John.b.Goode on 2010-11-22
Good thought, but unfortunately it didn't work.
My output when typing in ls .adobe/ is the same as yours.
Any other thoughts?

---

### Post by drdos2006 on 2010-11-22
Try installing Flash-Aid from the Firefox plugins.
I found it very useful after having all sorts of issues trying to resolve FlashPlayer 10 problems with a manual install.

regards

---

### Post by garvinrick4 on 2010-11-22
Lots of flash upgrades lately it seems. Some mirrors are not up to date so maybe
you have a flash upgrade coming in soon. Just a thought.

---

### Post by John.b.Goode on 2010-11-22
Thanks both of you. In my search for a solution I actually did stumble upon Flash Aid last night, but it didn't help.
Yes, I have thought of the possibility that the current update is not fully functional... but I don't think that can be it, because like I said, Flash worked on the Live USB key. Since I had to install Flash on the USB key at that time (two or three days ago) and this problem began a couple of weeks ago, I figure that it can't be the current update...
Any other ideas would be helpful. I really don't want to have to reinstall again...

---

### Post by John.b.Goode on 2010-11-22
Just had a brain blast. I tried running Firefox as root, and it worked! If nobody knows where I might be able to change permissions to permanently resolve the problem I can just run as root whenever I need the program... but, that being, said, any suggestions on which files/directories might have the wrong permissions would be appreciated.

---

### Post by cpmman on 2010-11-22
Check your permissions on ~/.mozilla

---

### Post by John.b.Goode on 2010-11-23
Just checked, and that's not it. I use both Firefox and Chrome, and the same problem exists for both, anyway.

---

