---
title: "Best way to remove Ubuntu and start over"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Indianrock on 2010-11-24
I used to work at Unix command line every day for a few years in a previous job, but it's been a while. So I installed Ubuntu 10 ( dual boot ) the other day in a new 30GB partition (U drive )  I created on my Vista Laptop.   After looking around in Ubuntu for a while I was very impressed -- haven't looked at Linux at all since Red Hat back in the 1990s.

When I saw the download updates feature I downloaded updates.  Don't recall exactly what happened next but after rebooting I got the **no such device Grub Rescue **prompt.  The next step was to install Ubuntu 9.1 from a liveCD since that's all I had available at the moment on CD.   This went into some of the free space on the C (vista) partition.   After restarting I could see most of the boot menu again, but still odd.

So I recovered with Vista recovery disk (   bootrec.exe /fixmbr  )  Now when I restart I see Vista or Ubuntu 10.04 Lucid Lynx so I guess the 9.1 is still taking up space on the C drive. What's the best way to get rid of 9.1, eliminate it from disk management in Vista?

---

### Post by philinux on 2010-11-24
If this is Wubi then uninstall via add remove and set up a normal dual boot.

---

### Post by Yougo on 2010-11-24
sounds to me you have a 9.10 wubi installation. this is actually installed as software in windows. you should be able to uninstall it through the control panel

also i didn't know Vista's fixmbr recognises ubuntu installs?

---

### Post by Indianrock on 2010-11-24
Yes I see now the ubuntu 10.04 is the wubi and is visible in Vista add/remove programs.  For now I'm going to leave that alone.  It's the 9.1 partition I'd like to add back to Vista's C drive.  I deleted the 9.1 partition leaving 27GB of free space so now how do I add that back to the Vista OS partition?

---

### Post by chaanakya_chiraag on 2010-11-24
I would use something like GParted or similar to resize.  You could use the Disk Management tool found in Windows, but TBH, I never actually understood how to work the thing :D

---

### Post by bcbc on 2010-11-24
> **Indianrock said:**
> Yes I see now the ubuntu 10.04 is the wubi and is visible in Vista add/remove programs.  For now I'm going to leave that alone.  It's the 9.1 partition I'd like to add back to Vista's C drive.  I deleted the 9.1 partition leaving 27GB of free space so now how do I add that back to the Vista OS partition?

Use the windows vista disk utility tools to merge that partition back to windows.

Note that you have another option: you can migrate your wubi install to that new partition - keeping all settings and data using this guide: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

