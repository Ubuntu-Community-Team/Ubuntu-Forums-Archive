---
title: "A grub thing."
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Nutbun on 2011-03-01
I have two hard drives, one has win Xp the other Ubuntu 10.10.
What I want to do is reinstall win Xp, in doing so this will wipe out my grub menu thing. After I have reinstalled win Xp how would I go about refreshing my grub menu without having to reinstall Ubuntu?

Thank you.

---

### Post by Yegor on 2011-03-01
Following article should be helpful:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nutbun on 2011-03-01
Not yet being a expert in Linux I don't really understand most of what that document is talking about.  I can only hope luck is with me when I attempt it. :)

---

### Post by YesWeCan on 2011-03-01
The good thing about having two drives is that you can keep the two systems separate. This is a good idea. You can disconnect one drive and install an OS on the other, then repeat for the other drive.

Unfortunately, the XP bootloader will not boot Ubuntu off the other disk. However, the Ubuntu bootloader, called Grub, will boot XP. You have to tell Grub to look for XP and create a boot menu so you can choose between XP and Ubuntu. After you have installed both OS separately, connect both drives and tell the bios. to boot the Ubuntu drive first. Boot Ubuntu and in a console type 'sudo update-grub'. The next time you boot the Ubuntu drive you will get a boot menu. You will still be able to boot the XP drive directly.

---

### Post by grahammechanical on 2011-03-01
The link that Yegor gave you is complex because it is comprehensive. It is like a chapter in a technical book that covers many situations. You only need to understand a small part of it.

You are using 10.10 so you are likely using Grub2. I see on my Grub menu Grub 1.98 something, something. So, for all intents and purposes we have Grub2.

The smart thing about this Grub program is that when we issue the command sudo update-grub or sudo update-grub2 (both work) the program searches for other operating systems and works out the commands needed to load them. It should find the XP installation as well as the Ubuntu installation and set up a boot menu for you. Smart, yes?

Regards.

---

