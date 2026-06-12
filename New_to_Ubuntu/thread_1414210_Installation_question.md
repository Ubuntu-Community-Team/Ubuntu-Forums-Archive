---
title: "Installation question"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Captain_Yosemite on 2010-02-23
Have loaded ubuntu on to a second drive while keeping original windows build on primary drive.  Everything works fine when I boot and I get choice of windows, ubuntu or test environments.

I now want to ditch the windows drive and use the second drive with ubuntu on it as the main drive.  I tried removing primary drive and setting ubuintu drive as master but it says no drive found and will not boot. 

What am I doing wrong?

Thanks!

---

### Post by Ozymandias_117 on 2010-02-23
Your Grub Bootloader is installed on your primary drive. You will have to remove your windows drive, set the other to master, and install GRUB.

---

### Post by undecim on 2010-02-23
> **Ozymandias_117 said:**
> Your Grub Bootloader is installed on your primary drive. You will have to remove your windows drive, set the other to master, and install GRUB.

+1

You can find a guide on installing grub here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The tutorial is meant for fixing it after Windows wipes it out, but it's the same thing (just installing grub).

---

### Post by ajgreeny on 2010-02-23
Probably the easiest way while you still have the windows disk in the machine is to boot to ubuntu and use the command ```
sudo grub-install /dev/sdb
``` where sdb is your ubuntu disk.  I assume /dev/sda is your windows disk in this.

Now when you remove the windows disk grub will be there for you.  You can use the live CD to do it as well, but I think my way is quicker, if you are able to do it.

---

### Post by Captain_Yosemite on 2010-02-23
Thanks everyone - solved!

---

