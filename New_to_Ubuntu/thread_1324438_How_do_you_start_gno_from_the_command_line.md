---
title: "How do you start gno from the command line?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Irishpolyglot on 2009-11-12
Sorry, that should be gnome in the title. i'm having troubles booting up as normal (separate thread in General Help) but when I select 'recovery mode' from grub then 'resume normal boot' I have access to log in by command line. Is there a command to start gnome from here?
Thanks

---

### Post by wojox on 2009-11-12
Try:

```
sudo service gdm start
```

Or

```
sudo service gnome-session start
```

---

### Post by philinux on 2009-11-12
> **Irishpolyglot said:**
> Sorry, that should be gnome in the title. i'm having troubles booting up as normal (separate thread in General Help) but when I select 'recovery mode' from grub then 'resume normal boot' I have access to log in by command line. Is there a command to start gnome from here?
Thanks


After you've logged in on the command line it's just this.
```
startx
```

There seems to be a bug in recovery mode as resume normal boot should do just that and not drop you to a shell.

---

### Post by Irishpolyglot on 2009-11-12
Thanks. When I run the first one it says
```
gdm start/running, process 2334
```
and then returns to the prompt. The second one gives:
```
gnome-session: unrecognized service
```
Any thoughts? :)

---

### Post by Irishpolyglot on 2009-11-12
> **philinux said:**
> After you've logged in on the command line it's just this.
```
startx
```

There seems to be a bug in recovery mode as resume normal boot should do just that and not drop you to a shell.

I tried that. I don't know how to copy the results to you because I'm writing from my iPhone. It includes some of the following after using config file xorg.conf:
> (EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.
Fatal server error:
no screens found
........
ddxSigGiveUp: Closing log
giving up.
Xinit: No such file or directory....
This is obviously related to a bigger problem that I've raised here: [http://ubuntuforums.org/showthread.php?t=1324329]("http://ubuntuforums.org/showthread.php?t=1324329")
But it would be great if I had to just edit the conf file or whatever, for more basic driver use, so I can at least access the GUI....
Thanks!!

---

### Post by philinux on 2009-11-12
From the recovery menu choose xfix.

---

### Post by Irishpolyglot on 2009-11-12
There is no xfix in the recovery menu, and running it from command line gives 'no command xfix found'

---

### Post by Irishpolyglot on 2009-11-13
I did some searching and others are having the same issue in Karmic - there is no longer an xfix option for some people. A bug has already been filed.
In the mean time I definitely need to scan and fix my hard drive. I dug out my old 9.04 installation CD and was reinstalling it, and in the last stage of installation it said that there was a problem with the CD or hard drive. I tried another CD (always have two... haven't burned 9.10 yet, not sure if that would make any difference) and it did the same thing. When I selected "scan disk for errors" option on the boot up CD list, it confirmed that there was an error.

That's all great, but how do I get rid of it?? xfix no longer exists and when I tried fsck it very sharply says "WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage" so I select no. How can I run this without mounting the filesystem?

What I really need to do now is run xfix or fsck with error correction enabled. How can I do this? I am accessing the system fine through my boot up CD. Thanks for any tips!!

---

### Post by philinux on 2009-11-13
You can run fsck to check you hard drive from the livecd as then your partitions are not mounted.

sudo fdisk -l

to show your partitions. Then fsck -v /dev/sd?? the partition you want to fix. It might report back that it's clean.

I would also check whats in /ect/X11/xorg.conf. You can in Karmic delete this file and it will use the vesa driver. So at least you should be able to get to a desktop then sort out the graphics driver.

---

### Post by Irishpolyglot on 2009-11-13
I deleted the xorg.conf and now my Ubuntu is back and running fine :)
I see the nvidia drivers have been disabled. I'm wondering if my system can run fine without them or if I'll be forced to find a solution to living with them.

---

### Post by philinux on 2009-11-13
> **Irishpolyglot said:**
> I deleted the xorg.conf and now my Ubuntu is back and running fine :)
I see the nvidia drivers have been disabled. I'm wondering if my system can run fine without them or if I'll be forced to find a solution to living with them.

Whats the graphics card?

---

### Post by Irishpolyglot on 2009-11-21
Sorry for the delayed response. I got the card working again as advised [in this forum]("http://ubuntuforums.org/showthread.php?t=1331701"), it was a GeForce 8M series.
Thanks for your help

---

