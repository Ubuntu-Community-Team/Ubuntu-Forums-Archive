---
title: "Broadcom WLAN driver installer"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by prankstar008 on 2008-08-13
I wrote an installer for the Broadcom WLAN card.  It is my first time ever writing a (useful) bash script and I would appreciate feedback.  Place it in  the directory containing the broadcom tarball files.  32bit or 64bit should work.


EDIT: already found a bug...there is a "break" in the case statement that needs to be an "exit 1"

---

### Post by Ayuthia on 2008-08-13
This is good start for your first useful bash script!  One thing that you could use to prevent the user from making a mistake is uname -m.  This command will help you determine if the machine is 32 or 64 bit.  Another thing that you might consider is to have the user supply the name of the tarball instead of having the filename hard-coded.  This will help the script work for various releases instead of just one.

To help the user through the harder steps is to help blacklist the bcm43xx, b43, b43legacy, ssb, and ndiswrapper modules.  Your script is currently not doing this so the user might run into problems because of driver conflicts.  Of course, this is more difficult to do.  You will have to check and see if the they are already blacklisted and not in /etc/modules.  You will have to check and see if they need the b44 driver also because of ssb.  The b44 driver is the wired driver for Broadcom and it uses the ssb module.  So if they use this driver, they will have to load the b44 and ssb driver after wl (The driver you are installing).

In case you have not seen it, the Ubuntu developers are currently testing this for the 2.6.24.20 kernel.  It is currently in the hardy proposed repositories and will be included in linux-restricted-modules.  

One thing that should be noted is that this is for the new Broadcom driver that was released by Broadcom.  It is not the same as the open source version that is included in the kernel.  It is a proprietary driver, but it does work well for a few selected Broadcom cards.  For those who want to read about it further, you can check this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Users of this script might also need to have build-essential installed because the script does need to use the make command.

If you are able to make a script to help with the blacklisting of the other modules, it will help a lot of people who are trying to use this module.  It is usually where most of the issues occur.

---

### Post by prankstar008 on 2008-08-14
Thanks for the feedback.  I'll try to get a working script that resolves driver conflicts etc... before the release of the new kernel.

---

