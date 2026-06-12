---
title: "unable to boot ubuntu 8.10"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by dimple148 on 2009-06-06
Hi,

I use Ubuntu 8.10 on my office system.  I used Update Manager to update all the installed software.  It did its job, except for a few software which it said it could not find on the Ubuntu server.  Meanwhile it had also asked me to configure LILO.  As am not familiar with what LILO is I chose the default options.  After this, I was unable to use the 'reboot' or 'shutdown -h now' commands in the terminal.  At the end of the day I forced shutdown the machine. In the next boot, Ubuntu dropped me in the 'initramfs' shell.  A search thru Ubuntu forums lead me to few posts which said that 'exit' or ^D will boot the machine.  

My problem is am unable to exit the initramfs shell with either 'exit' or ^D.

Can somebody help me in setting the system right again?

Regards,
Dimple.:confused:

---

### Post by kiridude on 2009-06-06
You need to reinstall your boot loader. I would use GRUB instead of LILO and if you follow the directions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), you should be ok.

Good luck.

---

### Post by dimple148 on 2009-06-06
Hi,

Thanks for the quick response. I was using GRUB. I really dunno why the LILO dialog box came up while updating.  

I will try this out on Monday and post the results on the forum.

Thanks again,
Dimple.

---

### Post by dimple148 on 2009-06-10
> **kiridude said:**
> You need to reinstall your boot loader. I would use GRUB instead of LILO and if you follow the directions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), you should be ok.

Good luck.


Hi,

I tried the above method but no luck.  :( I still end up at the (initramfs). Any other ideas?  And also would like to mention I am using only Ubuntu 8.10 on my system. I do not have a dual boot system with Windows.

Dimple.

---

### Post by kiridude on 2009-06-10
Did you reinstall grub and it still doesn't work?  -strange...

If you have a backup of your stuff it would be easiest to simply do a fresh installation with 9.04. If you don't have a backup, you can get into your file system with the live cd and copy all your important files, then reinstall.

---

### Post by dimple148 on 2009-06-10
> **kiridude said:**
> Did you reinstall grub and it still doesn't work?  -strange...

If you have a backup of your stuff it would be easiest to simply do a fresh installation with 9.04. If you don't have a backup, you can get into your file system with the live cd and copy all your important files, then reinstall.

Hi,

Yes, I reinstalled grub and yet it didn't work. Well, I guess, I will have to do a fresh install. Thanks again for the help. :)

Dimple.

---

