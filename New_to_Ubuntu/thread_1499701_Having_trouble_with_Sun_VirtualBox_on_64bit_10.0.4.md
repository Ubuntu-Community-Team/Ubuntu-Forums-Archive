---
title: "Having trouble with Sun VirtualBox on 64bit 10.0.4"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by wombatvvv on 2010-06-02
Hi,

I know this isn't really the right forum, but the VirtualBox forums have an idiotic spam-protection field in their registration form that doesn't seem to accept the correct answer, so I can't register there.

Has anyone had any luck installing any Windows version with Virtual Box on 64bit Ubuntu?

I've tried Windows 7, Windows 7 64-bit and Windows XP.

Both Windows 7 version seem to hang on "Loading Windows Setup" (or something similar, just after you choose the language etc.)

Windows XP seems to be installing, but it's going incredibly slowly. The install process has dropped from "25 minutes remaining" to "18 minutes remaining" in the last hour. So it is moving, but at a very slow speed.

Anyone else had any luck or have any suggestions? I'm using the 64-bit version of VirtualBox.

Thanks

---

### Post by ..::| Dave89 |::.. on 2010-06-02
I don't know if this is related but I have a similar problem loading Ubuntu based distros in VirtualBox 3.2 on Lucid 64-bit, they just hang there on the boot screen. I've tried Xubuntu 10.04 64-bit, Ubuntu Lucid 64-bit, Ubuntu 9.04 and 9.10, both 32-bit.  Haven't got a spare Windows disc to try, but VirtualBox seems to load Puppy Linux, Windows 3.1 and openSUSE fine.

---

### Post by corncob on 2010-06-02
I don't seem to be having any problems but then I don't use it very much either.  I don't remember but I would have installed 64bit VB if it was available.  What I've been doing, rather than reinstalling XP and the applications every 6 months when I upgrade, is to merge the previous .VirtualBox folder into the new installation.  This came from 9.04 or earlier -- I save my home folder when I upgrade.  VB keeps prompting me to download an upgrade when I start it but I'm giving a presentation to the computer club next week and don't want to mess things up lol.

---

### Post by philinux on 2010-06-02
I'm using the VB for 64bit and have had no problems. I had Win7 rc running last year. It did take while to install as I remember the iso file was something like 4 gig. It took well over an hour. The performance also depends on the host pc specs.

Recently just got linux peppermint installed. I only used the default setup in VB.

---

### Post by wombatvvv on 2010-06-02
> **philinux said:**
> I'm using the VB for 64bit and have had no problems. I had Win7 rc running last year. It did take while to install as I remember the iso file was something like 4 gig. It took well over an hour. The performance also depends on the host pc specs.

Recently just got linux peppermint installed. I only used the default setup in VB.


The host specs should be more than adequete ... I just bought the laptop a couple of weeks ago. It's an i7 with 4GB ram, etc. all the good stuff.

Since my last post I'm down to "6 minutes remaining".

I wondering if it has something to do with the virtual HD options - I noticed there was a few choices there...

I just selected default for everything but bumped the ram up to 1GB. The main reason I need to run it is to run Photoshop. And if GIMP could open the latest PSD formats properly, I wouldn't even need that.

---

### Post by philinux on 2010-06-02
> **wombatvvv said:**
> The host specs should be more than adequete ... I just bought the laptop a couple of weeks ago. It's an i7 with 4GB ram, etc. all the good stuff.

Since my last post I'm down to "6 minutes remaining".

I wondering if it has something to do with the virtual HD options - I noticed there was a few choices there...

I just selected default for everything but bumped the ram up to 1GB. The main reason I need to run it is to run Photoshop. And if GIMP could open the latest PSD formats properly, I wouldn't even need that.

Well the default HD option is for it to dynamically expand so should be no problem there. Even the ram is just the starting ram and it will use more if it needs to. I reckon it just takes a while to install. You'll get a real feel for it once it's actually running the os. Win7 last year was very snappy even in the VB.

---

### Post by sandyd on 2010-06-02
I have a question, really. how did you install virtualbox?

---

### Post by VastOne on 2010-06-02
> **wombatvvv said:**
> Hi,

I know this isn't really the right forum, but the VirtualBox forums have an idiotic spam-protection field in their registration form that doesn't seem to accept the correct answer, so I can't register there.

Has anyone had any luck installing any Windows version with Virtual Box on 64bit Ubuntu?

I've tried Windows 7, Windows 7 64-bit and Windows XP.

Both Windows 7 version seem to hang on "Loading Windows Setup" (or something similar, just after you choose the language etc.)

Windows XP seems to be installing, but it's going incredibly slowly. The install process has dropped from "25 minutes remaining" to "18 minutes remaining" in the last hour. So it is moving, but at a very slow speed.

Anyone else had any luck or have any suggestions? I'm using the 64-bit version of VirtualBox.

Thanks

Running Win7 in V-Box on several Ubuntu 64 Lucid Machines with 0 issues.

---

### Post by dustinmarlowe56 on 2010-06-02
> **carlee said:**
> I have a question, really. how did you install virtualbox?


the best way that i have seen is to install in from the virtual box website (omg yes you aren't using repos for once.) 

of course i say this because i have been hearing about the VB in the repos being not up to date or something like that, but it could be fixed by now.

---

### Post by wombatvvv on 2010-06-02
> **carlee said:**
> I have a question, really. how did you install virtualbox?

I just downloaded it from the Sun VirtualBox website and ran the script. It installed in it's own isntaller program thingy. I dunno, I've very new to Linux, but it was very easy.



Anyhooo....



I just couldn't get Win7 going at all. Last night I tried again and it just hung on that "Loading Setup" screen for about 2 hours.

I did however install Windows XP - but it's very strange: the install took AGES. Well over 2 hours - probably close to 3 hours. However, once it's installed it FLIES. How is this possible?? I installed PhotoShop and Flash (CS3 - 32 bit), and Photoshop _literally_ loads in 3 seconds, I'm not exaggerating at all. Flash loads in about 2 seconds. The blue splash screen barely has time to flash up. I've never seen Photoshop ever load so fast. Is the Virtual Box storing an old state in memory or something? I just can't get over it. I'm even using the default VirtualBox settings with 3D and 2D disabled!

I have the PhotoShop CS5 64bit trial on my Windows 7 partition (non-virtual), it takes over a minute to load, as does Flash.

Another question - with 2D or 3D enabled, VirtualBox seems to often crash when switching between fullscreen mode. Any advice?

---

### Post by wombatvvv on 2010-06-02
> **VastOne said:**
> Running Win7 in V-Box on several Ubuntu 64 Lucid Machines with 0 issues.

Can you remember it taking a looooong time to install? As I mentioned in my above post, I got XP going, but it took all night to install it.

---

### Post by wombatvvv on 2010-06-02
I just wanted to bump this to the next page...

> **wombatvvv said:**
> I just downloaded it from the Sun VirtualBox website and ran the script. It installed in it's own isntaller program thingy. I dunno, I've very new to Linux, but it was very easy.



Anyhooo....



I just couldn't get Win7 going at all. Last night I tried again and it just hung on that "Loading Setup" screen for about 2 hours.

I did however install Windows XP - but it's very strange: the install took AGES. Well over 2 hours - probably close to 3 hours. However, once it's installed it FLIES. How is this possible?? I installed PhotoShop and Flash (CS3 - 32 bit), and Photoshop _literally_ loads in 3 seconds, I'm not exaggerating at all. Flash loads in about 2 seconds. The blue splash screen barely has time to flash up. I've never seen Photoshop ever load so fast. Is the Virtual Box storing an old state in memory or something? I just can't get over it. I'm even using the default VirtualBox settings with 3D and 2D disabled!

I have the PhotoShop CS5 64bit trial on my Windows 7 partition (non-virtual), it takes over a minute to load, as does Flash.

Another question - with 2D or 3D enabled, VirtualBox seems to often crash when switching between fullscreen mode. Any advice?

---

### Post by blur xc on 2010-06-02
I didn't install a windows guest in vbox, but I already had a VM that I created in an older version of vbox, in 32bit 9.04, that now that I've upgraded to 64bit 10.04 it runs in it just fine.  I have a different problem with VBox 3.2 in 64bit 10.04 though- don't know if it's related-  [http://ubuntuforums.org/showthread.php?t=1499866](http://ubuntuforums.org/showthread.php?t=1499866)

It doesn't seem to affect the guest os, but the host comes to a crawl.

BM

---

### Post by sandyd on 2010-06-03
> **wombatvvv said:**
> I just downloaded it from the Sun VirtualBox website and ran the script. It installed in it's own isntaller program thingy. I dunno, I've very new to Linux, but it was very easy.



Anyhooo....



I just couldn't get Win7 going at all. Last night I tried again and it just hung on that "Loading Setup" screen for about 2 hours.

I did however install Windows XP - but it's very strange: the install took AGES. Well over 2 hours - probably close to 3 hours. However, once it's installed it FLIES. How is this possible?? I installed PhotoShop and Flash (CS3 - 32 bit), and Photoshop _literally_ loads in 3 seconds, I'm not exaggerating at all. Flash loads in about 2 seconds. The blue splash screen barely has time to flash up. I've never seen Photoshop ever load so fast. Is the Virtual Box storing an old state in memory or something? I just can't get over it. I'm even using the default VirtualBox settings with 3D and 2D disabled!

I have the PhotoShop CS5 64bit trial on my Windows 7 partition (non-virtual), it takes over a minute to load, as does Flash.

Another question - with 2D or 3D enabled, VirtualBox seems to often crash when switching between fullscreen mode. Any advice?

i know how to install virtualbox :) , I just wanted to see wether you were installing it from the repos or the site. speaking of which, have you tried virtualbox beta? oh !nd good night everyone... ill spend the rest of today playing cod's museum level at veteran difficulty.... hopefully ill get through the first bell press

---

