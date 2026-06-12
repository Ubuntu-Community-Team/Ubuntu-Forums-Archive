---
title: "I'm fed up - your advice on continual wubi fails"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by CaptainOblivious on 2010-10-17
I have been running Ubuntu Netbook for a couple semesters now.  I truly find it worth my time to ask you why my Wubi installation continues to fail on me.  Every time I get a kernel update (from 9-something to 10.04, and most recently from 10.04 to 10.10), I can no longer boot into Ubuntu or access Grub.  Selecting Ubuntu from the OS choice menu immediately restarts the machine with no error messages.

I'm not entirely helpless.  I've been around the Net for weeks following suggestions.  I keep backups of my root.disk images.  Reinstalling Grub in whole or part has no effect.  Replacing disk images with my backups within the same kernel version also fails.  Various other hacky tricks via boot CDs and the like have let me down.

I have had to resort to installing a fresh copy of Ubuntu, mounting my disk backups and MANUALLY recovering my class notes, files and app data.  I then must go through the process of reinstalling the applications I use.  It's as tedious as it sounds, and I've done it five times on three drastically different computers.  Furthermore, a quick google search shows I'm certainly not the only one experiencing this issue.

I'm fed up with Ubuntu.  This is the sort of bug just shouldn't make it through any kind of development process.  I'm not jumping ship yet, though.  What are your suggestions for preventing my installation from failing during BASIC UPDATING?  I'm all ears.

---

### Post by Sef on 2010-10-17
> I'm fed up with Ubuntu. This is the sort of bug just shouldn't make it through any kind of development process. I'm not jumping ship yet, though. What are your suggestions for preventing my installation from failing during BASIC UPDATING? I'm all ears.

1) Uninstall any proprietary drivers.

2) Run a live USB to check system compatibility.

3) Back up your files before updating.

---

### Post by diablo75 on 2010-10-17
I am personally NOT a fan of Wubi.  It seems to me one of the biggest problems with it is the fact that Linux isn't actually installed on it's own ext3/4 partition and instead rests inside of a FOLDER on the original NTFS partition.  The upside to this is it's safe (no partition resizing required) and fast, but the downside is that it *seems like* NTFS doesn't support certain features that are native to the ext3/4 filesystem.  I don't know specifics, but it's just *felt* like that was involved with the problems I had with it when I tried it after it was first introduced.

Since you're on a netbook, you probably don't have a CD-ROM.  However it is possible to create a bootable USB stick using a program called unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you create one, you can boot from it and use it to shrink your NTFS partition and install Ubuntu alongside Windows in it's own native ext4 partition.

---

### Post by cpmman on 2010-10-17
Wubi is not designed to be a long-term installation.  For a permanent data critical use Ubuntu should be installed in its own partition.  See the Wubi guide linked in my signature.

---

### Post by CaptainOblivious on 2010-10-17
Thank you for the quick replies, everyone.  No proprietary drivers in use on any system of mine.  I always backup, but certain pack-in programs require invasive file system work to restore them.

I guess my main concern is why it fails first time, every time I allow such major updates.  Whether or not Wubi is designed for long-term use, this appears to be an enormous problem.

I'm willing to test and retest my case for anyone who's interested in whatever logs can be obtained from doing so, so long as it would further Ubuntu's development and Wubi's viability.  Just tell me what to do.

---

### Post by beew on 2010-10-17
To my mind wubi is second class status, it is basically for hesitant windows users to get a taste of Ubuntu without making any commitment. It has limitations that come with being second class as others have mentioned. If you use Ubuntu long enough to get upgrade it seems there is no reason not to get a real installation instead.

If you cannot give up Windows either a dual boot or a full installation of Ubuntu in an external drive would be much better way to give Ubuntu its due than wubi.

---

### Post by bcbc on 2010-10-17
1. Lock the version of grub-pc and grub-common in synaptic. Grub2 is the source of most of wubi's problems since 9.10, and updates rarely make any positive difference to wubi installs, so just bypass them.
2. Read release notes before upgrading - 10.10 release notes clearly state that wubi upgrades are known to fail.
3. As you do, backup regularly before major updates/upgrades.
4. There is a workaround for the 10.10 upgrade problem. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by HermanAB on 2010-10-17
Howdy,

Two comments:
1. Don't use Wubi.
2. Don't fix it if it ain't broke.

So, do a proper install of Ubuntu and once it works, turn the automatic f-up/update feature off.

---

