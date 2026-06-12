---
title: "Ubuntu power management"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Delawaredave on 2009-02-19
Love Ubuntu.  Unfortuantely I have had zero luck the power management - hibernating, etc. 

Sony Vaio model:  PCV-R526DS

I install updates.  Any idea what to do next ?

Before someone said to do below - it worked for awhile - but not any more.

sudo apt-get install startupmanager
Then go to System > Administration > StartUp-Manager
where it says
Default OS to
Click on the drop down arrow and change it to
Ubuntu 8.04, kernel 2.6.24-16-generic

---

### Post by Pollox on 2009-02-20
> **Delawaredave said:**
> Unfortuantely I have had zero luck the power management - hibernating, etc.

What exactly is the issue?  Just hibernating not working, or hibernate and suspend, or broader power management issues?

---

### Post by Delawaredave on 2009-02-20
Weird - both suspend and hibernate don't work.  Occasionally they will work - I've been trying to understand the conditions when/why it works.

But usually for suspend or hiberate, either the monitor hangs on way down, or monitor won't start on way back up, or system won't shut down.  Sometimes, but rarely, I get an error - I'll post if I can find.

Is either suspend or hibernate generally more reliable than other ?

Anything I can do ?  This computer is in a location where we often "turn on for a couple minutes, use, then turn off" -so suspend or hibernate is needed.

Thanks !

---

### Post by Pollox on 2009-02-20
> **Delawaredave said:**
> Weird - both suspend and hibernate don't work.  Occasionally they will work - I've been trying to understand the conditions when/why it works.

But usually for suspend or hiberate, either the monitor hangs on way down, or monitor won't start on way back up, or system won't shut down.  Sometimes, but rarely, I get an error - I'll post if I can find.

Is either suspend or hibernate generally more reliable than other ?

Anything I can do ?  This computer is in a location where we often "turn on for a couple minutes, use, then turn off" -so suspend or hibernate is needed.

Thanks !

Personally, I found suspend to be more reliable (and it might be easier to fix), although hibernate usually works well too if you have enough swap and it's set up correctly.  You might want to check out this post: [http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890) for help figuring out your issue, although it might be overly complicated and/or outdated.  Sorry I couldn't help you more on this, as I'm no expert on the issue, only someone who's had problems with hibernate before.  Hopefully the details you posted are enough for someone more knowledgeable to solve the problem when they read this.  If you can really pinpoint what exactly it does when it tries to suspend or hibernate, you might even get lucky with a web search and find someone who had the same problem before.

---

### Post by Delawaredave on 2009-02-21
> **Pollox said:**
>  [http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)

Thanks. Above is way over my head.

Ubuntu is so great in most ways - but so incredibly clumbsy for installing programs -I can't figure out TAR GZ, all that stuff.

So I found "tuxonice" - thought that would help my hibernate problems - forget it - you need a degree in computer science to install it,

I love this line at [http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon]("http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon") ***"I hope you know the essential packages like gcc, make, bzip2 or gunzip, fakeroot, wget, kernel-package required for compilation. There are two ways to build this"***

Is there any way a "normal user" can install this ?  Thanks !

---

### Post by wangsuda on 2009-02-21
> **Delawaredave said:**
> Love Ubuntu.  Unfortuantely I have had zero luck the power management - hibernating, etc. 

Sony Vaio model:  PCV-R526DS

I install updates.  Any idea what to do next ?

Before someone said to do below - it worked for awhile - but not any more.

sudo apt-get install startupmanager
Then go to System > Administration > StartUp-Manager
where it says
Default OS to
Click on the drop down arrow and change it to
Ubuntu 8.04, kernel 2.6.24-16-generic

Have you tried the built-in power management? Go to System>Preferences>Power Management and set your parameters.

---

### Post by Delawaredave on 2009-02-21
> **wangsuda said:**
> Have you tried the built-in power management? Go to System>Preferences>Power Management and set your parameters.

Thanks but above just defines defaults when you press button and idle time.  Was already set to go to hibernate when pressing button. I tried also suspend - no better.  Thanks !

---

### Post by Pollox on 2009-02-21
> **Delawaredave said:**
> Thanks. Above is way over my head.

Ubuntu is so great in most ways - but so incredibly clumbsy for installing programs -I can't figure out TAR GZ, all that stuff.

So I found "tuxonice" - thought that would help my hibernate problems - forget it - you need a degree in computer science to install it,

I love this line at [http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon]("http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon") ***"I hope you know the essential packages like gcc, make, bzip2 or gunzip, fakeroot, wget, kernel-package required for compilation. There are two ways to build this"***

Is there any way a "normal user" can install this ?  Thanks !

It looks like you can just install "tuxonice-userui" from Synaptic, and it will automatically mark the necessary dependencies (neither of which are called "tuxonice", but I think it's the thing you're looking for).  So you could try that.  Ubuntu is great for installing programs provided someone made a .deb file for them (i.e. the huge list of programs you can find from Synaptic).  tar.gz files are just compressed files like .zip in Windows.  You can just right click on them and click "Extract here" should you for some reason need to do so in the future.  Usually if you're installing a program in that way, there's a README file in the thing you extract that gives specific instructions.

---

### Post by Delawaredave on 2009-02-21
> **Pollox said:**
> It looks like you can just install "tuxonice-userui" from Synaptic, and it will automatically mark the necessary dependencies (neither of which are called "tuxonice"

Thanks.  I can't get past above.  Is this explained in English anywhere ?
Googled "tuxonice-userui" -and got below hits - but I don't know what I am staring at.

I downloaded a file called tuxonice-userui_0.7.2+clean.orig.tar.gz -- does that help ? What do I do with it ?

Thanks !

[http://packages.gentoo.org/package/sys-apps/tuxonice-userui]("http://packages.gentoo.org/package/sys-apps/tuxonice-userui")
[https://launchpad.net/ubuntu/hardy/+source/tuxonice-userui/0.7.2+clean-3]("https://launchpad.net/ubuntu/hardy/+source/tuxonice-userui/0.7.2+clean-3")

---

### Post by presence1960 on 2009-02-21
> **Delawaredave said:**
> Thanks.  I can't get past above.  Is this explained in English anywhere ?
Googled "tuxonice-userui" -and got below hits - but I don't know what I am staring at.

I downloaded a file called tuxonice-userui_0.7.2+clean.orig.tar.gz -- does that help ? What do I do with it ?

Thanks !

[http://packages.gentoo.org/package/sys-apps/tuxonice-userui]("http://packages.gentoo.org/package/sys-apps/tuxonice-userui")
[https://launchpad.net/ubuntu/hardy/+source/tuxonice-userui/0.7.2+clean-3]("https://launchpad.net/ubuntu/hardy/+source/tuxonice-userui/0.7.2+clean-3")

Dave, use Synaptic Package manager to install. Synaptic package Manager is just what you are looking for. Open Synaptic Package manager and click search. Search for tuxonice, when it finds tuxonice tick the box next to it and choose mark for installation. When complete click apply up top. just a few mouse clicks and it will be installed.

---

### Post by 3rdalbum on 2009-02-21
> **presence1960 said:**
> Dave, use Synaptic Package manager to install. Synaptic package Manager is just what you are looking for. Open Synaptic Package manager and click search. Search for tuxonice, when it finds tuxonice tick the box next to it and choose mark for installation. When complete click apply up top. just a few mouse clicks and it will be installed.

Always look in Synaptic Package Manager first. It's the Linux way of installing software.

---

### Post by presence1960 on 2009-02-21
> **3rdalbum said:**
> Always look in Synaptic Package Manager first. It's the Linux way of installing software.

+1 

Dave was making a mountain of a molehill. If he would have checked the repositories first in Synaptic he would have had tuxonice installed with no problems. But like the rest of us he will live and learn. That's all part of the learning process.

---

### Post by Delawaredave on 2009-02-26
Think I figure out - noticed I had Google gadgets and search installed - I uninstalled those and things seem to be working better.

So my "didn't make any changes since install" wasn't exactly correct....

Thanks for everyone's help !!!

---

### Post by wangsuda on 2009-02-26
> **Delawaredave said:**
> Think I figure out - noticed I had Google gadgets and search installed - I uninstalled those and things seem to be working better.

So my "didn't make any changes since install" wasn't exactly correct....

Thanks for everyone's help !!!Thanks for keeping us updated. Now we know more of what to look for when we repartition.

---

