---
title: "Lost admin privileges"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by JALBird on 2008-12-12
Hello, I am using Ubuntu Intrepid, and have recently run into a problem.  I can in fact log into Ubuntu, but when attempting to perform any sudo command, my password is denied.  I checked and I am still registered as an administrator in the Users panel, and my password logs me into Ubuntu itself.  I am the only account, also.  I cannot install any programs/updates, either.

I think this problem first showed up after I attempted to install drivers on my thinkpad for my fingerprint scanner.  Went through all the steps, but was never able to get it working.  But after I restarted the computer, I was not able to access the pam.d commonauthority file to remove the fingerprint scanner lines, and now I am stuck.

Also I am unable to boot in recovery mode.  I do not have the option of booting into recovery mode, just Ubuntu or Vista (only two choices).  I have also been unsuccessful with booting off the livecd, still cannot get a command prompt.  Please help!

---

### Post by albinootje on 2008-12-12
You can still boot into "recovery mode" by editing the kernel boot line for Ubuntu in the Grub menu.
Just add the word "single" at the end of the line for the kernel.

Here are some more details for editing that line :
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Make sure you have another computer with internet connection around to continue solving this problem after booting into recovery mode.

---

