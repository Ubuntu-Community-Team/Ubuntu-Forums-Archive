---
title: "remove usplash theme"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by djbushido on 2009-03-23
I currently have a usplash theme on my computer that is buggy and every time I boot, it crashes. I installed it using start-up manager, and now I am using Fedora trying to fix it. Currently I would like it removed and the default (xubuntu) splash (saved on harddrive) reinstalled. Any help would be greatly appreciated. Thank you!

---

### Post by bodhi.zazen on 2009-03-23
Can you not simply re-run start-up manager ?

---

### Post by djbushido on 2009-03-23
No, because I can't boot into xubuntu. I don't think. It seems to hang, but I can try again. I will post back results.

---

### Post by Bachstelze on 2009-03-23
> **djbushido said:**
> No, because I can't boot into xubuntu. I don't think. It seems to hang, but I can try again. I will post back results.

You can disable usplash temporarily by hitting "e" while your Ubuntu entry is highlighted in the GRUB menu. Then move to the "kernel" line, press "e" again to edit it, and remove the "splash" parameter. Then press Enter to validate your modifications, and "b" to boot.

---

### Post by djbushido on 2009-03-23
will try this, thank you.

---

### Post by CJ Master on 2009-03-23
If this temporary solution works for you, once your in you can use synaptic to remove the Usplash package (This will also remove the Ubuntu-desktop package. This won't harm your system in any way, HOWEVER you need it if you want to distro-upgrade.)

---

### Post by bodhi.zazen on 2009-03-23
You can probably also use chroot to run start-up manager.

---

### Post by djbushido on 2009-03-23
what do you mean by chroot startup manager? chroot in terminal and then fire that up? If so, that might be a good idea, because currently I'm getting dropped to init shell.

---

### Post by bodhi.zazen on 2009-03-23
yea, is start-up-manager an X application or command line tool ?

---

### Post by djbushido on 2009-03-23
Start-up-manager is X. My idea is to chroot inside my Fedora distro and then use that to configure it. Might work. Hope so. Don't even know if startup is in Fedora. Will try doing a chroot in terminal and launching startup manager. Currently nothing else has worked, i get dropped to an init shell after a lot of errors (and saying that my disk can't be found in /dev/disk/by-uuid). The other problem is that the system recognizes the drive as "External Hard Drive" where previously it has been "Seagate FreeAgent Go". Ideas?

---

### Post by bodhi.zazen on 2009-03-23
you can do it with chroot, although there are additional steps required for X apps.

[http://www.pixelbeat.org/docs/chroot.html](http://www.pixelbeat.org/docs/chroot.html)

---

### Post by djbushido on 2009-03-24
Okay, still not getting that to work. Is there a simple console way to change the usplash theme? Better yet, is there a console way to change the theme? And update initramfs, because I think I screwed that up too.

---

### Post by Bachstelze on 2009-03-24
Why bother with a chroot? Just boot with usplash disabled as I told you, and run start-up-manager normally...

---

### Post by bodhi.zazen on 2009-03-24
> **djbushido said:**
> Okay, still not getting that to work. Is there a simple console way to change the usplash theme? Better yet, is there a console way to change the theme? And update initramfs, because I think I screwed that up too.

> **HymnToLife said:**
> Why bother with a chroot? Just boot with usplash disabled as I told you, and run start-up-manager normally...

He tried : > Will try doing a chroot in terminal and launching startup manager. Currently nothing else has worked, i get dropped to an init shell after a lot of errors (and saying that my disk can't be found in /dev/disk/by-uuid).

@djbushido : I am getting the impression that more either you did not edit the boot parameters properly or more is wrong with your system hen the boot splash.

When booting, edit the kernel line, and the only change you make is to remove the word "splash".
]
Can you tell us what edit you made and the error messages ?

---

### Post by egalvan on 2009-03-24
> **djbushido said:**
> i get dropped to an init shell ...(and saying that my disk can't be found in** /dev/disk/by-uuid).**
 ... the system recognizes drive as "External Hard Drive"
previously  been "Seagate FreeAgent Go".
 Ideas?

the UUID's may be messed up.

see if
```
sudo blkid
```

will run from that init shell...

then verify the UUID tags.

Personally, I don't ever use spaces in drive labels...
replace them with underscores.

---

### Post by kansasnoob on 2009-03-24
I recently hosed things in 8.04 downloading different themes from gnome-art and I was able to get booted by booting into recovery mode. After that ran I was presented with 4 options and I chose dpkg, it asked me if I wanted to do something (sorry didn't make notes) and I said (y) yes.

When presented with the 4 options again I chose resume normal boot and it ran through a "script" rather than using usplash. Once booted into the desktop I used startupmanager to change the usplash theme and all was fine. (I used the "manage usplash themes" option to remove the offending culprit!

---

### Post by djbushido on 2009-03-24
Okay, the problem was that i messed with initramfs. That is fixed. The system is hanging after trying to boot with JUST the "splash" option removed. UUID's are ok. The initramfs was causing that. I need to try booting to recovery mode, will see if that helps.

EDIT: After booting to recovery mode, the startup hangs at "Begin /scripts/init-bottom" Not sure on the Begin part, but the /scripts/init-bottom is correct. Hope that helps. Note, that this also happens running the normal boot with "quiet" removed. As well as splash.

QUESTION: Is there a way to change usplash theme from terminal? I can boot my recovery cd and use that if so. The old xubuntu usplash was left on the drive.

---

### Post by djbushido on 2009-03-25
Problem fixed. Booted an older kernel on my system, reinstalled .11 image, should fix it. If it doesn't, I'll just wait for the next update, and that should work. Thanks everyone!

EDIT: Did fix it.

---

