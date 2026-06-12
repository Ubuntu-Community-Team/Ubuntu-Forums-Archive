---
title: "wubi in win 7"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by davellew69 on 2010-01-26
Hi, I have Ubuntu on an old laptop, but I am sitting here after downloading wubi on a new laptop from santa. its 3gb ram and 250gb of space.
I`m just droping brick  about installing ubuntu using WUBI, how easy is it? and what are the recomended settings?

i`m showing installation drive as 178gb free, insallation size 17gb
how does this look? do i need to reduce any of the settings? what would be the minimum required to run ubuntu

Any help is welcome

---

### Post by 3rdalbum on 2010-01-26
The base system uses about 3 gigabytes. Then you need room for extra programs - on Linux, programs tend to be 1/3 the size of equivilant Windows programs due to more efficient code reuse. Then you need room to store your personal files.

17 gigabytes should be fine, unless you want to edit video or do DVD authoring.

I would, however, recommend creating a Windows recovery disk, then defragmenting Windows, and then booting from the Ubuntu CD and doing a real dual-boot installation. Wubi has several annoying [limitations]("http://www.google.com.au/url?q=http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)%23Limitations&usg=AFQjCNEfOVVzbGoOkXUTwcNSqDyvqFSIbg&ei=XqpeS_2QLIqUkAXEpamgAg&sa=X&oi=section_link&resnum=1&ct=legacy&ved=0CA0QygQ").

If you really just want to try Ubuntu for a couple of days before deciding whether to keep it, then Wubi is a good option.

---

### Post by davellew69 on 2010-01-26
thanks, I done a recovery disk, and defrag, i take it that setting up duel boot with a disk is easy? what are wubi`s limitations?>

---

### Post by davellew69 on 2010-01-26
otherwise in wubi do i just click install and just let it run?

---

### Post by 3rdalbum on 2010-01-26
> **davellew69 said:**
> otherwise in wubi do i just click install and just let it run?

Pretty much, just set what drive you want the Ubuntu file to be on and how much space you want, and then what your user account name and password should be.

Dual-booting by booting the disc is pretty much as easy as doing it from Wubi. The main difference is that you have to move a slider at the bottom of the window to show how you want to resize the Windows part of the system, to make room for Ubuntu.

Also, I forgot to mention: Back up your data before doing any partitioning.

---

### Post by djchandler on 2010-01-26
I have a laptop with the same size hard drive. What I  alotted for Ubuntu is about 60GB , which is way more than enough. I have a bunch of software installed, and I still have 50GB left (not including swap). But what I do is mount the NTFS (Windows) partition under Ubuntu and store most of my big data files on the NTFS partition so it's accessible from both Win 7 and Ubuntu. If you install ntfs-config, AKA NTFS Configuration Tool, it will let you mount your NTFS partitions automatically after booting into Ubuntu.

Be careful just to put data files that you want available for both systems in Users/Public on the NTFS partition. The other thing to be careful about is stay away from the virtual disk file on the Windows partition that actually holds the Ubuntu system. Recursive access to that file could create a problem potentially. I'm not sure that it would, it's just something I wouldn't do.

So if you put most of your data on the ntfs, 12-16gb should be plenty of room for testing Ubuntu with Wubi. But with 178gb free, go with the installation defaults. If you decide it needs to be changed, back up your ubuntu data that you wish to keep from your home directory to the ntfs partition, then go back to Windows and uninstall then reinstall Wubi. Or, if you decide you want to keep Ubuntu permanently, you can partition your disk using the Ubuntu Live CD and get your Ubuntu specific data back the same way.

Wubi is very good for not locking you into an early decision that develops into a less than optimal situation later. Give it a shot. It's probably easier to uninstall Wubi than most Windows applications.

---

### Post by davellew69 on 2010-01-26
Thanks every one I will try it tonight...happy surfing folks

---

