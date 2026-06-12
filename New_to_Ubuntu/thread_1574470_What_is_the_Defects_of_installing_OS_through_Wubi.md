---
title: "What is the Defects of installing OS through Wubi?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-14
[SIZE=2]*I Have installed Ubuntu through **Wubi** because at that time i haven't any LIVE-CD and it is going well :p*[/SIZE]....... *[SIZE=2]i have seen in many forums , people having a problems with **Wubi**[/SIZE]*,
[SIZE=2]*Can someone tell me the **defects** of using **wubi**..?*[/SIZE]



Thanks.

---

### Post by bbqsandwich on 2010-09-14
"The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate."

"Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events."

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by philinux on 2010-09-14
> **tajiknomi said:**
> [SIZE=2]*I Have installed Ubuntu through **Wubi** because at that time i haven't any LIVE-CD and it is going well :p*[/SIZE]....... *[SIZE=2]i have seen in many forums , people having a problems with **Wubi**[/SIZE]*,
[SIZE=2]*Can someone tell me the **defects** of using **wubi**..?*[/SIZE]



Thanks.

One problem I've seen is when an update for grub-common and grub-pc is available. This update renders the machine unbootable. Personally I would not update wubi. I would just use it to test out ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580606](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580606)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581827](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581827)

---

### Post by mastablasta on 2010-09-14
For testing purposes it is OK but not for propper use as it is basically a virtualisation.
 
Not even for testing purposes, as Full Installation can be better than Live session or Wubi.

---

### Post by 3rdalbum on 2010-09-14
> **mastablasta said:**
> For testing purposes it is OK but not for propper use as it is basically a virtualisation.

Well no, it runs directly on your computer's hardware. The only difference is that the root filesystem is actually a file on a Windows NTFS partition.

The biggest problem with Wubi is that, if Windows crashes and refuses to start up, then you also lose access to Ubuntu until the problem is fixed. Ubuntu can't mount NTFS partitions that haven't been cleanly unmounted, so if this has happened then it can't mount the partition that contains the root filesystem.

The other big issue is that you have limited space with Wubi. There are ways of increasing the amount of space, but you might as well do a full install anyway. Using Wubi because "I don't have a live CD" is a bit of an odd thing to say, because Wubi will actually download the live CD. You might as well have downloaded the live CD yourself and burnt it.

---

