---
title: "Update of linux-image-2.6.31-generic"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Ol'manScratch on 2010-11-27
I received this update notice below and am not  sure what to do. I did not install this and went looking for the linux-generic meta-package called for, but I am not sure which one I need. Can anyone enlighten me?
Thanks
-------------------------------------
This package contains the **Linux kernel image for version 2.6.31 on x86/x86_64.**
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the **linux-generic meta-package**, which will ensure that upgrades work correctly, and that supporting packages are also installed.

---

### Post by gurmeet1109 on 2010-11-27
It is an upgrade to the kernel image of the linux you are running. Pls. go ahead. It is safe to install.

In general, you should be able to trust the packages coming from Ubuntu's default repository. Unless you do something over the top, you can safely press the update button.

Also as suggested install the linux-generic package by issuing the command "sudo apt-get install linux-image-generic". Since it is a system wide change, It will ask you for password. Pls. provide that and let it do it's job. That's it reboot and enjoy your updated linux system.

---

### Post by QLee on 2010-11-27
[QUOTE=Ol'manScratch]I received this update notice below and am not  sure what to do....[/QUOTE]

Since you don't have many beans and are posting in beginners forum, you may not have much or any experience with manual upgrading (or not, you could also be a power user with just this one question). If inexperienced, it might be easier for you to bring up the Update Manager GUI and then do a "Check", followed by an "Install Updates", or, with Synaptic Package Manager, a "Reload", followed by a "Mark All Upgrades", followed by "Apply". No need to look manually for things.

---

### Post by Ol'manScratch on 2010-11-27
Thank you. My problem was with the note at the bottom of the update that said "You likely do not want to install this package directly."
I usually do install updates as they come in, but this one made me cautious.
When I went looking for the generic meta-package, I wasn't sure which one I should install - several are listed.

---

### Post by Ol'manScratch on 2010-11-27
Thanks Q-Lee.
I'm a little above an absolute beginner, but far from a power user. As I said above, it was the note on the upgrade saying "You likely do not want to install this package directly" that threw me off-course.

When I first began using linux I installed a package improperly and it crashed my system for weeks. (It was later traced to a hardware problem with no connection to linux) So I just like to be certain on what I am doing.
I appreciate your help.

---

### Post by mikewhatever on 2010-11-27
The metapackage is 'linux-image-generic'. If not installed, then do install it to get rid of that message.

---

### Post by Ol'manScratch on 2010-11-27
Great! Thanks again

---

### Post by QLee on 2010-11-28
[QUOTE=Ol'manScratch]...
When I went looking for the generic meta-package, I wasn't sure which one I should install - several are listed.[/QUOTE]
An image metapackage is the package that will always depend (think of that as, require) on the latest kernel image for the kernel your system is using. In that way the package manager will be able to do upgrades (updates in this context) automatically for you, without you having to track the version of the latest kernel for your system.

In your case it was the metapackage for the latest "generic" kernel (you don't use 4 or more MB RAM), in other cases it might be the latest "virtual" kernel image or the latest "server" kernel image. I think the metapackage for system's kernel flavour is installed by default, so you likely manually removed it at some point. Sometimes people do that when they choose to not have their kernel automatically upgraded, a practice I don't recommend but some do.

---

