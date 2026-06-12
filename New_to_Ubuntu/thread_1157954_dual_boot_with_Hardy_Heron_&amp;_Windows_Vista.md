---
title: "dual boot with Hardy Heron &amp; Windows Vista"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by trixman on 2009-05-13
A friend of mine would like to try out Linux Ubuntu Hardy Heron, and install it in windows and dual boot her new machine to have both choices.
The one question she asks is when she uses the Linux side is it a full version of Linux.  She really likes the look and feel of Hardy Heron so she is real excited. And would she need a virus program on the Linux side.

:KS

---

### Post by Bartender on 2009-05-13
Is it a full version?  Well, yeah, I guess so.  Don't know of any half-versions.
Lots of folks are running Linux with no anti-virus at all.  If you're networked to Windows PC's, Linux can pick up a virus that will do nothing to the Linux PC but can leapfrog to a networked Windows PC.
If you're gonna install Ubuntu, might as well install 9.04 instead of 8.10.

---

### Post by Ms_Angel_D on 2009-05-13
Your friend has two options:

[Wubi]("http://wubi-installer.org") & A Tradition Dual boot, here's some info:

Wubi is not a dual boot. I first installed wubi before switching to Ubuntu completely. Wubi simply installs Ubuntu into a file inside your windows installation. Then adds the option to choose to load this file into your master boot record, so when you start your computer you have an option to load either this file with ubuntu or load into your windows installation. If you decide you don't like and Ubuntu isn't for you, then you go into add/remove programs in the control panel and Uninstall it. Just like any other software installation you can choose where to install wubi to in windows.

[LIST]
[*]Wubi installs just like you would install any other piece of software into windows.
[*]Wubi will not create a partition
[*]Wubi will not overwrite your existing data
[*]wubi is great for discovering Ubuntu.
[*]wubi has slightly lower performance than an actual install
[*]using wubi you will not be able to hibernate or suspend your computer
[/LIST]

If something happens your to windows install you will not have access to wubi either since it installs into a file inside of windows. Therefore if you try Ubuntu in this manner & decide you like it, It is recommended that you then proceed to remove wubi, and either dual boot with windows or just wipe windows and install Ubuntu.

[LIST]
[*]These tutorials all have screenshots included
[LIST]
[*][How to dual boot Windows XP and Linux (XP installed first)]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
[*][How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
[*][How to install Ubuntu with Wubi]("http://www.howtoforge.com/wubi_ubuntu_on_windows")
[/LIST]
[*][Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index")
[/LIST]

---

### Post by trixman on 2009-05-13
> **MetalHellsAngel said:**
> Your friend has two options:

[Wubi]("http://wubi-installer.org") & A Tradition Dual boot, here's some info:

Wubi is not a dual boot. I first installed wubi before switching to Ubuntu completely. Wubi simply installs Ubuntu into a file inside your windows installation. Then adds the option to choose to load this file into your master boot record, so when you start your computer you have an option to load either this file with ubuntu or load into your windows installation. If you decide you don't like and Ubuntu isn't for you, then you go into add/remove programs in the control panel and Uninstall it. Just like any other software installation you can choose where to install wubi to in windows.

[LIST]
[*]Wubi installs just like you would install any other piece of software into windows.
[*]Wubi will not create a partition
[*]Wubi will not overwrite your existing data
[*]wubi is great for discovering Ubuntu.
[*]wubi has slightly lower performance than an actual install
[*]using wubi you will not be able to hibernate or suspend your computer
[/LIST]

If something happens your to windows install you will not have access to wubi either since it installs into a file inside of windows. Therefore if you try Ubuntu in this manner & decide you like it, It is recommended that you then proceed to remove wubi, and either dual boot with windows or just wipe windows and install Ubuntu.

[LIST]
[*]These tutorials all have screenshots included
[LIST]
[*][How to dual boot Windows XP and Linux (XP installed first)]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
[*][How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
[*][How to install Ubuntu with Wubi]("http://www.howtoforge.com/wubi_ubuntu_on_windows")
[/LIST]
[*][Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index")
[/LIST]

wubi sounds perfect . thanks

---

