---
title: "Uninstall Ubuntu"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by klaxor on 2010-01-13
I'm in desperate need to uninstall this os.  I can't keep up with the updates because my hard drive is too small.  There is no way that I can continue to use this and keep my sanity.

So please, please, please, please tell me how to uninstall ubuntu 8.04!

---

### Post by DestructionsRightHand on 2010-01-13
I would recommend a fresh install to 9.10.
or
What do you want to replace it with?  Do you have your files backed up?

---

### Post by klaxor on 2010-01-13
All of my files are on an external.  So yeah, they're pretty backed up.  Don't hate me, but I'm going back to windows. *winces and dodges a hit prematurely*

---

### Post by Cheesemill on 2010-01-13
How did you install it?
What is your other OS?
What is the output of:
```
sudo fdisk -l
```
and:
```
df -h
```

Answer these and we should be able to help :)

Also if you want to keep Ubuntu it's possible to give it more room.

---

### Post by klaxor on 2010-01-13
It came on my little laptop.  Saved me fifty bucks and I thought it would be a good challenge.  It was for a while, then it just became a hassle.


Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c1a5c1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4         460     3670852+  83  Linux

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.2G   30M 100% /
varrun                247M  100K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   36K  247M   1% /dev
devshm                247M   12K  247M   1% /dev/shm
lrm                   247M  1.9M  245M   1% /lib/modules/2.6.24-22-lpia/volatile
gvfs-fuse-daemon      3.4G  3.2G   30M 100% /home/kenny/.gvfs

---

### Post by adam814 on 2010-01-13
Yeah, that's going to give you hassles alright...completely full volumes cause all kinds of weirdness (probably can't start X).

I'll actually be interested to know if Windows will install and run on a drive that small either...seems like you'd need something lighter than a full Ubuntu install on it anyway (might pull off Xubuntu if you don't install much, any of you out there running UNR pulled off something like this?).

---

### Post by klaxor on 2010-01-13
I'm installing XP as well, just to keep my storage needs down.

---

### Post by adam814 on 2010-01-13
I was just thinking that even with XP you'll probably have to turn off System Restore.  I have an XP Pro installation here that takes up about 3.4GB out-of-the-box.  Maybe other XP versions use less space though.

As for actually uninstalling I'd think you could just format the whole disk and install XP and not worry about it.

---

### Post by Dayofswords on 2010-01-13
> Disk /dev/sda: 3791 MB, 3791241216 bytes
jeez, even my windows 98 desktop came with 4 more gb

---

### Post by snowpine on 2010-01-14
4gb of hard drive space is the bare minimum required for Ubuntu; 8gb (or more) is recommended:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

With only 3.4gb available, I'm not surprised you ran into problems. If you decide to come back to Linux, I would recommend a "lighter" distro like Xubuntu or Puppy. Good luck with XP!

---

### Post by audiomick on 2010-01-14
> **klaxor said:**
> I'm installing XP as well, just to keep my storage needs down.

Since when does XP need less room than Ubuntu?

---

### Post by kansasnoob on 2010-01-14
You'll need to use Gparted from an Ubuntu Live CD, or download the gparted iso and burn it to disc:

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso/download)

Then delete Ubuntu. I don't know what to tell you about the Dell utility?????????

After deleting Ubuntu just install Windows.

---

### Post by Merk42 on 2010-01-14
> **audiomick said:**
> Since when does XP need less room than Ubuntu?

Since always. It requires only **1.5GB**

The "issue" is that we're comparing Ubuntu 8.04 (circa 2008) with XP (circa 2001)
a more accurate comparison would be Vista (circa 2006) that requires **15GB** or 7 (circa 2009) that requires **16GB**

---

### Post by audiomick on 2010-01-14
> **Merk42 said:**
> Since always. It requires only **1.5GB**


Oh, I thought it was more than that.

---

### Post by ugm6hr on 2010-01-14
This smells of a Dell Mini 9 with 4GB SD "hard drive"

It is a real shame that Dell made a mess of Ubuntu on this device.

If you do want to persevere with Ubuntu, I would recommend doing a fresh install of the standard Netbook Remix.  It is smaller than the Dell 8.04 version.

Another simple trick:
```
sudo apt-get clean
```

Will remove all the unnecessary update files stored.  Despite this, because of the way Dell releases updates in bulk, it still causes a mess.  There are ways around this, but installing 9.10 is just more sensible.

After all this, if you want XP, just get an external CD drive and install it.  There should be no need to "uninstall" Ubuntu at all.  If this is not the case, you may have to reformat the drive, since XP installer sometimes refused to recognise a HD with ext3 format.

---

### Post by jollysnowman on 2010-01-14
Try CrunchBang or CrunchBang Lite. That'll fit easily.

---

