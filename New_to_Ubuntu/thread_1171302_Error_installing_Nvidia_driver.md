---
title: "Error installing Nvidia driver"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by ashton88 on 2009-05-27
I am having troubles installing the Nvidia 177.82 driver after upgrading from Hardy (8.10) to Jaunty (9.04).

These are the steps that I took under Hardy, which worked fine until the upgrade, and continue to work with any of the Nvidia drivers *after* the 177.82 release:

1. CTRL-ALT-F2 && Login
2. Backup /etc/X11/Xorg.conf
3. sudo /etc/init.d/gdm stop
4. sudo /path/to/downloaded/file/NVIDIA-Linux-x86-177.82-pkg1.run
5. (default install - yes yes yes - next next next)
6. sudo /etc/init.d/gdm start

This still works if I use the Nvidia 180.22 or 180.51 drivers.  However because of a problem I detail [this thread]("http://ubuntuforums.org/showthread.php?p=7350363") I am trying to roll back to a version of the Nvidia driver I know for certain worked - the one I used prior to the upgrade from 8.10 to 9.04.

The issue is this: When going through the nvidia-installer script for 177.82 (only) I get a long error message that says (in brief) "If you are running kernel version 2.6 please make sure that you point the environment variable SYSOUT to your configured kernel sources."

This is odd, because I have never needed kernel sources to install Nvidia drivers before, and I don't need them for any of the later versions.

Determined, I followed the instructions [here]("https://help.ubuntu.com/community/Kernel/Compile") to install the kernel sources.  Then after some research I used a "export SYSOUT=/usr/src/linux-headers-$(uname -r)" and tested it with a "cd $SYSOUT" to make sure I ended up in the right place.  I ran the nvidia-installer script again and had the same problem.  So I need a nudge on what direction to go.

Here are a couple considerations:
1) I often need to switch between Nvidia drivers, often using the latest versions, so programs that manage your nvidia drivers haven't historically worked that well for me because they tend to lag behind.  Mind you I haven't looked in a while.
2) I suspect that just because I have installed the kernel sources, those sources may not come installed as per the default kernel image I have installed on my system.
3) After reading, I'm assuming that having the sources on your system does not "void the warranty" - only that using them to compile a custom kernel does.  I have no intention of doing that - and I'm hoping that isn't involved in the solution.
4) I'm concerned that the sources are in directories called "headers" - I don't know if that is significant, but if there is a difference between the real kernel sources and the header sources then I have the latter installed, and I probably need the former. As evidenced by this point, I'm out of my depth at this level.

And all that said - if I am going about this completely the wrong way and there is a quicker way to install 177.82 I would be happy to give that a go at this point.

Many thanks to all you Ubuntu gurus!

---

