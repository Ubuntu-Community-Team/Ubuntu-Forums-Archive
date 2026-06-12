---
title: "Too scared to upgrade...should I?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by listerdl on 2010-02-02
Hi, although my signature lists the latest ubuntu release I am typing on another machine that runs an older release. I would like to update this but I have had Monumental Problems with lack of sound....

If I upgrade and lose the sound, (which seems probable) can I roll-back to a previous good version and how do I do that? Thanks!!

---

### Post by audiomick on 2010-02-02
Hi.
If you are worried about it, I would suggest doing an additional install to test with, or maybe just booting into the live CD of the newer version. It is a lot easier to remove an install and update grub than it is to take an established install back one version.

There is no easy way, as far as I know, to do a rollback. You have to re-install. I have also seen numerous posts agreeing with this opinion.

---

### Post by warfacegod on 2010-02-02
> **audiomick said:**
> Hi.
If you are worried about it, I would suggest doing an additional install to test with, or maybe just booting into the live CD of the newer version. It is a lot easier to remove an install and update grub than it is to take an established install back one version.

There is no easy way, as far as I know, to do a rollback. You have to re-install. I have also seen numerous posts agreeing with this opinion.

Downgrading or rollingback is technically possible but is almost certain to break your system.


I think Ailurus has a restore point utility. I have no idea if would work after an upgrade.

---

### Post by *Raz0r* on 2010-02-02
If I remember correctly during the upgrade an option should pop up which allows the user to keep all his older programs, files, without having them updated. But it will update the drivers though, and you might loose the sound, but that is unlikely

---

### Post by walt.smith1960 on 2010-02-02
> **audiomick said:**
> Hi.
If you are worried about it, I would suggest doing an additional install to test with,** or maybe just booting into the live CD of the newer version.** It is a lot easier to remove an install and update grub than it is to take an established install back one version.

There is no easy way, as far as I know, to do a rollback. You have to re-install. I have also seen numerous posts agreeing with this opinion.

Burning a Live CD would be my approach. That should tell you in short order which hardware is recognized "out of the box" so to speak. In fact, I did just that with Lucid Lynx Alpha 2. Works well so far!! If you're really scared you'll make a mess, you might think about an imaging program. If you create an image of your hard drive, you can restore that image and get back to where the machine was at the time the image was created no matter what you do subsequent to creating the image. But a Live CD will not do anything to your hard drive unless you select "install" from the initial menu.

---

### Post by Old_Grey_Wolf on 2010-02-02
When I only had one computer for Linux use, I dual or triple booted it. It had a fairly large hard disk. I had a Windows partition, an old Ubuntu partition, and a partition with the latest Ubuntu release. I did not have a separate /home partition. After I installed the latest Ubuntu release to the new partition and set it up for testing, I would copy the files of the old Ubuntu partition containing mail, preference, application settings, and so forth to the new release partition. I would boot to the new release as much as possible. After I was comfortable with it, I made that the default boot option. I ping-ponged the old and new Ubuntu partitions as new releases became available.

---

### Post by Sef on 2010-02-02
> If I upgrade and lose the sound, (which seems probable) can I roll-back  to a previous good version and how do I do that? Thanks!!

1) **Back up** your **data** first.  There are no guarantees that all will go well.

2) Run a live cd for a while and see if there are any issues.  If there are, they will usually occur upon install.

---

### Post by nhasian on 2010-02-03
actually there is an easy way to roll back.  simply use Clonezilla before the upgrade and backup your entire drive to an image and save it to an external hard disk.  then you can safely upgrade your system.  if you are unhappy with the results, boot off the Clonezilla LiveCD again and restore your hard disk to the way it was before the upgrade.  I use this method when testing the developmental release of Ubuntu since you never know when a *sudo apt-get dist-upgrade* will break your system.  :)

> **listerdl said:**
> If I upgrade and lose the sound, (which seems probable) can I roll-back to a previous good version and how do I do that? Thanks!!

---

### Post by listerdl on 2010-02-03
Great thanks for all replies. Clonzilla seems the answer.

---

