---
title: "Placing the /home directory on a different partition."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-15
I've heard people mention it, how exactly do you set that up?  Is it something you indicate during installation or is it as simple as moving the folder to a different partition after Ubuntu is installed?

---

### Post by sydbat on 2010-01-15
You can do either, but it makes it easier on you to set it up during installation. When installing, use the manual partitioner and set your / to about 10GB (I use 20GB just cuz) and your /home to whatever remains on your hard drive. Then, when you decide to upgrade or bork your system or try another distro, your data will not be affected.

---

### Post by audiomick on 2010-01-15
> **sydbat said:**
> Then, when you decide to upgrade or bork your system or try another distro, your data will not be affected.

more precisely put, you can re-mount the old /home partition on a fresh install without formatting, thereby retaining your data and settings. It is not automatic, but does work reliably and well.


Here are two links to guides for creating a separate /home from an existing installation.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Dreakon on 2010-01-15
Is this roughly what it looks like during installation?

[IMG]http://www.serenux.com/~hyrax/snaps/UbuntuJauntyManuallyPartition2.png[/IMG]

And I would simply move the Mount Point /home to the partition I want it on, and put the / to where I want Ubuntu?  Can I just "move" the Mount Point at this screen as I please?  (I won't be dual booting, so it will look slightly different on my laptop)

Should I change the partition I want the data on (and not Ubuntu) from NTFS to ext4?  Or would staying as NTFS be safer?

---

### Post by oldfred on 2010-01-15
I do not know what you did but you can attach files, thumbnails with the paperclip to attach files.

You have to use a linux file system for Ubuntu not a windows file system like NTFS that does not support all the permissions and user settings.

You can create another partition that is NTFS to share data with windows (which I have) and mount that into /home for ease of access. I now rarely use windows so I have another /data partition for Ubuntu only data.

---

