---
title: "Mint almost"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-04-06
installed.  I'm not getting everything installed.  I get [unsupported PM caps regs version 7]- Gave up waiting for root device.- Alert! /dev/sdb1 does not exist.  Dropping to a shell.

(initramfs)

---

### Post by LowSky on 2009-04-06
We need a little more informaiton on what is going on. For instance, when is this issue occurring, what type of machine (Dell/HP/Homebuilt), and the model (hopefully some of the part models too)

---

### Post by Yed Ied on 2009-04-06
I knew better than that, Sorry.  Toshiba Satellite L355, brand new, Vista, never used.  I have Ubuntu and like it a lot, but I wanted to see Mint.  I had run it on CD, but had the chance to do the install on this machine and am sorry Ive hit a snag.  It seems to be telling me I don't have everything installed.  I can put the CD back in and run on that, internet connect, and everything, but wont run without it.  It says type "help" and it gives me a paragraph of stuff.  Should I try to download a different CD?

---

### Post by carml on 2009-04-06
Maybe you choosed the option to try it without installing a thing.

---

### Post by LowSky on 2009-04-06
honestly there is little reason to even try Mint if you have Ubuntu, only some slight changes that mint offers over Ubuntu, but most of which are trivial. Like Codec support, which Ubuntu can do with a small install of some additon files. Long story short Mint fills in the Gaps Ubuntu leaves out of a normal install.

---

### Post by Yed Ied on 2009-04-06
No, it installed, partitioned, did the whole install and ejected the CD,

---

### Post by carml on 2009-04-06
Did you checked the list of the partition with Gparted?You can find it under System->Administration->Partitions Editor if you use a Live cd or you can use GpartedLive. I assume that the Install CD of Mint is similar to a one of Ubuntu,since Mint is a "flavour" of Ubuntu.

---

### Post by estyles on 2009-04-06
> **Yed Ied said:**
> installed.  I'm not getting everything installed.  I get [unsupported PM caps regs version 7]- Gave up waiting for root device.- Alert! /dev/sdb1 does not exist.  Dropping to a shell.

(initramfs)


My guess is this: you have 2 hard drives, and when you booted from the CD, it saw one as /dev/sda and the other as /dev/sdb.  Then, after you installed, when rebooting, the drives are reversed (i.e. the one that it thought was /dev/sda is now /dev/sdb, and vise-versa).  Or, if you only have 1 hard drive, then for some reason it thought you had 2 and installed to /dev/sdb1, which is now /dev/sda1.

Is the error coming before or after grub (i.e. do you get a boot menu?).  If you get a boot menu, then the solution is to modify your /boot/grub/menu.lst file.  You can even edit it from the boot menu itself so you can boot.

If it is coming *before* you get a boot menu, then you'll have to reinstall grub to point at the right drive.

---

### Post by Yed Ied on 2009-04-06
Just one HD, but I tried several installs.  I think I'll stay with ubuntu 8.10 for a while.
Thanks

---

