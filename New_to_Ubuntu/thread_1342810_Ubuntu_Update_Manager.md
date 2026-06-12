---
title: "Ubuntu Update Manager"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Spright on 2009-12-01
Hi all,

I'm a beginner and I'm confused about the automatic updates that pop every week or so in Ubuntu.

Should I really install everything on the list?

What about updates for elements that I never use? I never use BlueTooth or Evolution; should I bother updating these every time? And is there a way to stop receiving updates for those particular tools?

Now and then a new Linux kernel comes. Does Ubuntu really change its whole kernel every few weeks?

Some updates say in the Description stuff like "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed." What should a humble beginnerlike me do with this confusing information? 

Thanks,

Me.

---

### Post by mkvnmtr on 2009-12-01
I install every update that comes up and have never had a problem. I even have backports enabled. That being said I normally uninstall all apps that I do not use such as bluetooth and Evolution. I do see threads where the poster is saying that the update borked their system but I am never sure if it is really operator problems or something with their specific system.

---

### Post by Bunnybugs on 2009-12-01
> **Spright said:**
> Hi all,

I'm a beginner and I'm confused about the automatic updates that pop every week or so in Ubuntu.

Should I really install everything on the list?

What about updates for elements that I never use? I never use BlueTooth or Evolution; should I bother updating these every time? And is there a way to stop receiving updates for those particular tools?

Now and then a new Linux kernel comes. Does Ubuntu really change its whole kernel every few weeks?

Some updates say in the Description stuff like "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed." What should a humble beginnerlike me do with this confusing information? 

Thanks,

Me.

Just install the updates... You can delete Evolution from your system with the 'Ubuntu Software Center' (Applications>Ubuntu Software Center). Just search for Evolution, Double click it, and press 'Remove'

You can do this with everything you don't use, BUT, some of these stuff could be usefull, so be carefull... Removing it now, and installing it back later is to much work for the same effect

---

### Post by Bunnybugs on 2009-12-01
> **mkvnmtr said:**
> I install every update that comes up and have never had a problem. I even have backports enabled. That being said I normally uninstall all apps that I do not use such as bluetooth and Evolution. I do see threads where the poster is saying that the update borked their system but I am never sure if it is really operator problems or something with their specific system.

Well, I guess that those people are Windoze users:P Windows doesn't make problems ith closing the update-app... but Ubuntu needs to be opened while updating... Just don't shut down during your update, etc, etc... Windoze remembers what the update was, and the state of the progress... from that on, they just keep on installing them... Ubuntu works different!

---

### Post by ukripper on 2009-12-01
ubuntu follows repository model. Please read this for more info - [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Besides it is not recommended to install anything outside ubuntu repos as it may be security risk or will likely to break your system during updates, unless if you really need that package and it is not in ubuntu repos you should always look for ppa [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) first. However, this is still not recommended secure way but it won't break your system on updates.

---

### Post by howefield on 2009-12-01
> **Spright said:**
> Should I really install everything on the list?

I'd say install the lot, given that the vast majority of the updates will be high risk bug fixes or security fixes. There aren't many program version updates as such, bar a few exceptions like Firefox.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by 3rdalbum on 2009-12-01
If they weren't meant to be installed, they wouldn't be pushed out to you. You might as well just install all of them. If you don't use Bluetooth or Evolution you can opt not to install those, but you might as well install them; it's safer.

Ubuntu does change its kernel version whenever there's a reason to. Why be so surprised; all operating systems push out kernel updates, and it's not really much different to getting a new version of Nautilus or Firefox, except that you have to reboot.

The confusing information you speak of is not really meant for your eyes. Don't worry about it. The "linux-generic" package makes sure that you get kernel updates; the package itself doesn't contain anything, but it has the latest kernel listed as a dependency. End result: When Ubuntu pushes out a new kernel, they push out a new version of linux-generic that says "I need the latest kernel", which ensures that the latest kernel gets installed without overwriting the old kernel.

Still confused? Don't worry about it, it doesn't matter from an end-user standpoint.

---

### Post by anaconda on 2009-12-01
I dont install everything on the list.. 
eg. I dont use open-office very much, and I dont have THAT fast internet connection. SO I wont update openoffice.. almost EVER. (it is a BIG packkage)

And I have sometimes had serious problems with kernel updates and nvidia drivers, so I wont install kernel updates very often. And then only if I have plenty of extra time for fixing possible problems.

And on my work machine updates would break too many things, so I wont install updates to it. (the update manager actually even says that "Not all updates can be installed"

EDIT:
And you can get rid of the "update notifier" by going to 
System>Preferences>sessions
And unclick the "Update Notifier" from there. And the next time you boot your machine the update notifier wont be started...  If you disable that then you will have to remember to run the update manager whenever you want to install the updates..

---

### Post by Spright on 2009-12-01
Thanks guys, you've been very helpful.

---

### Post by ed-koala on 2009-12-01
Unless you're really strapped for space, let it update, especially the kernel.  I'll never use bluetooth, or a bunch of other stuff that comes with Ubuntu, but since it takes up so little room overall, and doesn't slow things down being there, I don't care.  And I never know if someday I just might need it, or something else I might want will use part of what it has installed.

---

