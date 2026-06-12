---
title: "Use ubuntu (wubi) after reinstall Window"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by luckymancvp on 2009-08-26
I installed ubuntu 9.04 through wubi.
Now I reinstall Window. How can I use ubuntu :(

---

### Post by celthunder on 2009-08-26
Not sure how wubi works but normally you'd just have to reinstall grub  from a livecd or usb and add ubuntu and windows to /boot/grub/menu.lst

---

### Post by inobe on 2009-08-26
ubuntu was installed inside windows as a program, when you reinstalled windows' that unfortunately removed ubuntu especially if the windows partitioner formatted the hard drive.

now if you did an in place upgrade/ repair install ?

---

### Post by zeroseven0183 on 2009-08-26
> **inobe said:**
> ubuntu was installed inside windows as a program, when you reinstalled windows' that unfortunately removed ubuntu especially if the windows partitioner formatted the hard drive.

now if you did an in place upgrade/ repair install ?

That could be the case if it was installed inside drive C. Now luckymancvp should clarify which partition (if applicable) it was set up.

But I'm sure, just like what you mentioned, that it was deleted when Windows was reinstalled.

Perhaps, he can give us the error message he receives.

---

### Post by luckymancvp on 2009-08-26
I installed ubuntu in E drive.

Now I install new window in C drive.

---

### Post by Mark Phelps on 2009-08-26
It's possible that the Wubi developers figured out how to install a Windows application without using the Registry, but that's unlikely.  If any keys were written to the Registry, when Windows was reinstalled, the old Registry was overwritten, effectively removing any Wubi entries.

In that case, you would have to reinstall Wubi to recreate the Registry entries.

---

### Post by LewRockwell on 2009-08-26
wubi penguin you're the one...you make reinstall-time so much fun...

{{sigh}}

> we had our wubi-buntu exactly how we wanted it and then windows blew-up...

we had to reinstall windows...

now where did our wubi-buntu go?

{{chuckle}}

now is it a little more apparent why we recommend a separate partition for other distros?

caveat: it should be noted that many OEM operating system re-installation/recovery disks are set up to ONLY allow the installer to COMPLETELY seize the whole disk(regardless of past partitioning) and so that would cause the loss of anything/everything in those other partitions

this requires the cloning of those partitions that one desires to keep so that they may be re-positioned on fresh partitions after the windows re-install

windows...argh

.

---

### Post by zeroseven0183 on 2009-08-28
> **luckymancvp said:**
> I installed ubuntu in E drive.

Now I install new window in C drive.


So what happened now after your several installations?

---

### Post by theozzlives on 2009-08-28
If you did not format drive E:, your WUBI disk is safe. How to get it into a new install, I'm unsure. You'll have to search the online documentation, I'll see what I can find.

EDIT: I can't find it, what I would do is backup your ubuntu folder on E:, reinstall (to set the registry values and BOOT.INI) using the same size disk, then restore the folder overwrighting the new install. See if that works for ya.

EDIT (also): This may help. Maybe you can find something I didn't: [https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?")

---

### Post by Mark Phelps on 2009-08-28
> **theozzlives said:**
> If you did not format drive E:, your WUBI disk is safe. 

It's not the Wubi "disk" that's the problem; the problem is that when the OP reinstalled MS Windows, he blew away any existing registry entries that were created when Wubi was installed.

As I said earlier, if the Wubi developers figured out a way to install an MS Windows app without using the registry at all, it may be recoverable; if not, he will have to reinstall Wubi to rewrite the registry entries.

---

### Post by LewRockwell on 2009-08-28
still...

and again...

and still again...

wubi penguin you're the one...you make reinstall-time so much fun...

{{sigh}}

> we had our wubi-buntu exactly how we wanted it and then windows blew-up...

we had to reinstall windows...

now where did our wubi-buntu go?
{{chuckle}}

now is it a little more apparent why we recommend a separate partition for other distros?

**caveat: it should be noted that many OEM operating system re-installation/recovery disks are set up to ONLY allow the installer to COMPLETELY seize the whole disk(regardless of past partitioning) and so that would cause the loss of anything/everything in those other partitions**

this requires the cloning of those partitions that one desires to keep so that they may be re-positioned on fresh partitions after the windows re-install

windows...argh

.

---

