---
title: "Need some help running fsck"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by diablo75 on 2010-02-09
I'm trying to troubleshoot a problem by remote so I'm at the mercy of phone calls and emails about the situation... but here's what I do know.

A friend of mine upgraded to 9.10 and it was kinda bumpy.  It's hard to say just how many little tweaks have been made to the system configuration in the past and I think what happened was some settings that shouldn't have been kept around were retained when the upgrade took place and it cause certain aspects to not work after.  He tried an experiment where he'd boot up the system using an older kernel via the grub menu and ever since then the system doesn't boot normally.  I think what he did the first time around when this happened was force the PC to power off, and this has caused some hard drive issues, which I'm trying to fix with fsck.

So I've had him boot into Recovery Mode and drop to a terminal and simply run "fsck" at the prompt.

He says it "illustrates progress on the screen using dashes/lines and pound signs", so as the scan moves along, pound signs replace dashs... I think.

After letting this sit and work for a while, he said it would abruptly come to say the following:

> A maintenace shell will now be started. 

CONTROL-D will teminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

He adds:

"No matter what I do here, it always goes back to restarting what it was doing before.

The whole process starts over again, each time."

So I'm not sure what exactly is going on.  I wish I had more detailed info to provide about the on-screen messages.  I was thinking that there might be some kind of option I should have had him run fsck with in order to get all the way through without a snag like this.  Any ideas?

---

### Post by JBAlaska on 2010-02-09
> **diablo75 said:**
> I'm trying to troubleshoot a problem by remote so I'm at the mercy of phone calls and emails about the situation... but here's what I do know.

A friend of mine upgraded to 9.10 and it was kinda bumpy.  It's hard to say just how many little tweaks have been made to the system configuration in the past and I think what happened was some settings that shouldn't have been kept around were retained when the upgrade took place and it cause certain aspects to not work after.  He tried an experiment where he'd boot up the system using an older kernel via the grub menu and ever since then the system doesn't boot normally.  I think what he did the first time around when this happened was force the PC to power off, and this has caused some hard drive issues, which I'm trying to fix with fsck.

So I've had him boot into Recovery Mode and drop to a terminal and simply run "fsck" at the prompt.

He says it "illustrates progress on the screen using dashes/lines and pound signs", so as the scan moves along, pound signs replace dashs... I think.

After letting this sit and work for a while, he said it would abruptly come to say the following:



He adds:

"No matter what I do here, it always goes back to restarting what it was doing before.

The whole process starts over again, each time."

So I'm not sure what exactly is going on.  I wish I had more detailed info to provide about the on-screen messages.  I was thinking that there might be some kind of option I should have had him run fsck with in order to get all the way through without a snag like this.  Any ideas?

A better idea than fscking yourself is to force fsck the darn thing:
```
sudo touch /forcefsck && sudo reboot
```
:p

---

### Post by philinux on 2010-02-09
fsck needs to be run against a partition. For my root that would be

```
fsck /dev/sdb1 -v
```

-v = verbose

If it offers to fix anything hit the y key.

---

### Post by audiomick on 2010-02-09
have you looked at
```
man fsck
```

---

### Post by sisco311 on 2010-02-09
> **JBAlaska said:**
> A better idea than fscking yourself is to force fsck the darn thing:
```
sudo touch /forcefsck && sudo reboot
```
:p

That no longer works. You have to set the mount count to a high value to force a check:
```
tune2fs -C 50 /dev/sdXY
```

> **philinux said:**
> fsck needs to be run against a partition. For my root that would be

```
fsck /dev/sdb1 -v
```

-v = verbose

If it offers to fix anything hit the y key.

I usually use:
```
e2fsck -C0 -f -v /dev/sdXY
```
-C0 = progress bar
-f = force check

---

### Post by diablo75 on 2010-02-10
> **sisco311 said:**
> 
I usually use:
```
e2fsck -C0 -f -v /dev/sdXY
```
-C0 = progress bar
-f = force check

Can this be run from a Recovery Mode terminal, or should I boot from a Live CD to run this?

---

### Post by audiomick on 2010-02-10
> **diablo75 said:**
> Can this be run from a Recovery Mode terminal, or should I boot from a Live CD to run this?

Hi.
I don't know for sure either way, but I would be more comfortable doing it from a live CD on an unmounted drive. If you have the live CD lying around, I would suggest using it.

---

### Post by sisco311 on 2010-02-10
> **diablo75 said:**
> Can this be run from a Recovery Mode terminal, or should I boot from a Live CD to run this?

You have to run it in the maintenance shell (BusyBox), because running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

If you use a Live CD, then you can check the partition with GParted (System -> Administration -> GParted -> right click on the partition, unmount it then check it for errors).

---

