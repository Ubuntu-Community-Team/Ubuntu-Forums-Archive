---
title: "How long do I have to wait?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by thebarisaxkid on 2010-10-02
I have Ubuntu only 10.04 and I am running an update.  It seems to be "stuck" at linux-image-2.6.32-24-generic.  I look at the details and apperently it is at Generating grub.cfg... (I don't have grub installed yet)

The system isn't frozen, but this grub thing has been there for 20 minutes.

How long does it usually take?

---

### Post by cotcot on 2010-10-02
For sure not 20 min for grub config. Look if you do not have somewhere a window asking you if you want the packagers grub proposal or if you want to keep the version you have before updating.

---

### Post by JohnHeikkila on 2010-10-02
You should install GRUB before you update. How can you not have GRUB installed? Do you have a dual-boot or just Ubuntu on your PC?

```
sudo apt-get install grub2
```
To install GRUB.

---

### Post by nlsthzn on 2010-10-02
> **thebarisaxkid said:**
> I have Ubuntu only 10.04 and I am running an update. It seems to be "stuck" at linux-image-2.6.32-24-generic. I look at the details and apperently it is at Generating grub.cfg... (I don't have grub installed yet)
 
The system isn't frozen, but this grub thing has been there for 20 minutes.
 
How long does it usually take?
 
You don't have grub installed (yet)?

---

### Post by drs305 on 2010-10-02
> **thebarisaxkid said:**
> I have Ubuntu only 10.04 and I am running an update.  It seems to be "stuck" at linux-image-2.6.32-24-generic.  I look at the details and apperently it is at Generating grub.cfg... (I don't have grub installed yet)

The system isn't frozen, but this grub thing has been there for 20 minutes.

How long does it usually take?

If Grub2 is installed, usually less than 15 seconds, but it depends on how many disks/partitions it's looking at and how large they are. But 20 minutes is too long. Check for an open window asking you whether you want to update or keep your current package.

If you can still see the script output, if it has already generated the initrd image (initramfs) you are probably ok to stop it. The grub.cfg file creation is usually one of the last steps.

You say you don't have Grub installed yet? How are you booting without Grub. It can certainly be done, but a normal installation would include installing Grub. If the grub.cfg file isn't created or is corrupted *and* you *are* using Grub, you may have difficulty booting (but we can fix that).

If you abort the install you may also get error messages when trying to open Synaptic or run an update/upgrade.

If the system is hung, there isn't much you can do but interrupt it and take your chances. We can most likely help you with whatever problem arises, especially if you have a LiveCD handy.

---

### Post by Rubi1200 on 2010-10-02
Whenever there is a kernel update/upgrade the grub.cfg file is updated, but it should not be taking 20 minutes!

EDIT: follow the advice above (did not see it as I was posting)

---

### Post by thebarisaxkid on 2010-10-02
I declare myself the luckiest person on the face of the earth!

I force quitted the update, restarted, and I still boot up without a hitch!

---

### Post by gandaran on 2010-10-02
have you looked for a small window hiding behind the big one, this could be the problem, it's waiting for you to click something.

---

### Post by thebarisaxkid on 2010-10-02
I now installed grub and am currently updating.  I am now halfway done with updates.  Thanks guys!

(BTW: I only had Ubuntu, no XP or Vista or 7, so that is why there was no grub)

---

### Post by drs305 on 2010-10-02
If all you had was Ubuntu then you had Grub. It's the default bootloader. It would have been installed when you installed Ubuntu. The bootloader is necessary even if you have only one OS.

Most likely there was a window asking you if you wanted to retain your current Grub2 configuration or update to the maintainer's version. 

Generally it's best to update to the newer version, as there may be improvements that prevent failed boots or give you more options. The downside to accepting the maintainer's version is that you will often lose any customizations you have made to the Grub2 files, such as timeouts, splash images, etc (depending on which files are updated).

---

