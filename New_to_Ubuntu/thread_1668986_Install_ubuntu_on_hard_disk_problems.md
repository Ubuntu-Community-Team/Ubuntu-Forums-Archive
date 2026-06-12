---
title: "Install ubuntu on hard disk problems"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by fabricator4 on 2011-01-17
Something seems to have been lost in the translation, however...

Booting off the LiveCD uses a virtual drive. Data is not saved between sessions but it is a good way to try Ubuntu and testing compatibility without changing anything on your system.

A Wubi install is much faster than booting off the live CD however it is still slower than having a dedicated Linux (Ubuntu) partition.  It does not use a virtual drive - programs and data are stored on the hard drive and the operating system works very well.  I recommend release (version) 10.04 LTS for a Wubi install. To start a Wubi install boot Windows and then insert the LiveCD.  It should prompt you to start the Wubi installation.  Follow the prompts and install the appropriate language for your location or preference.

I hope your translator does better on this message.  There may be a support forum where you can get help in your own language.

Chris

---

### Post by diablo75 on 2011-01-17
The main difference between Wubi and an Ubuntu Live CD is that Wubi does not repartition your hard drive.  Wubi creates a folder on your Windows partition called Ubuntu and installs the OS into that folder.  The bootloader then does it's best to simulate an ext3 partition on top of the NTFS partition being shared with Windows.  It's good as a quick way for new users to try the OS out without having to burn any CDs and makes uninstalling the OS very easy.

Installing with a Live CD allows you to shrink your Windows NTFS partition to make room for a new Linux ext3 or ext4 partition (as well as a swap partition).  It's not quite as convenient as the Wubi installer but you will have a more stable experience with Ubuntu if you install it this way.

---

