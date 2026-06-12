---
title: "Unable to boot into Ubuntu"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by alec4rs on 2011-02-28
Hey guys,

Im running a dual boot with Ubuntu and Windows 7 (Windows 7 partition still works). When I try to boot into Ubuntu, I get the error message 

Killed
Mount: mounting on /dev on root/dev failed, no such file or directory.

I booted Ubuntu from my flash drive and I can see the partition. When I click to mount it, nothing happens (and later in disk utility you can see the "mounting" icon). In Diskutility, when I check the file system on the partition it says "File system not clean"

I then went to gparted and tried to repair the file system, but it didnt work.

How can I fix my file system? Thanks

---

### Post by ajgreeny on 2011-02-28
From your live ubuntu USB, run the following command in terminal ```
sudo fsck /dev/sdx#
``` the sdx# being the faulty partition.  Make sure the partition is unmounted first.

That may sort out the problem, but if not come back again with any error messages thrown up.

---

### Post by deconstrained on 2011-02-28
What does your fstab look like?

---

### Post by alec4rs on 2011-02-28
I tried fsck and this is what happened:

ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?


Any thoughts? Also typing fstab in terminal doesnt do anything, not sure what you meant by this.

---

### Post by guilleme on 2011-02-28
Hi. I personally would recommend reinstalling ubuntu if you have the time. It could be easier to reintall than repair on this case. (First backup the important files somewhere else:)). I had a very similar problem recently, and got it fixed by reinstalling. If you are to do so, I'd recommend using a ext3 partition instead of ext4, I've found they work better. 
See y'a. And good luck. :).

---

### Post by Rubi1200 on 2011-03-01
I definitely agree with guilleme that you should try and backup all important data before doing anything else. Don't agree that reinstalling is the only option right now.

Here is what you should do:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Also, download and burn to CD a distro called Slax.
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Once you have done that, we can advise you further.

---

### Post by ajgreeny on 2011-03-01
> **alec4rs said:**
> I tried fsck and this is what happened:

ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?


Any thoughts? Also typing fstab in terminal doesnt do anything, not sure what you meant by this.
Using the live CD/USB try ```
sudo umount /dev/sda2
```then the ```
sudo fsck /dev/sda2
``` again.  It seems that the partition was mounted last time you tried, so perhaps you had mounted it to make sure you had the correct one.

---

### Post by alec4rs on 2011-03-02
@ Rubi, when I did that, the terminal got stuck at searching sda2... 

@Ajgreeny : I tried umount, and it said it was already unmounted, and of course fsck didnt work.

---

### Post by Rubi1200 on 2011-03-02
Hi,
let's try something else.

Download and burn to CD to use as a LiveCD the following distro:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

If you can then boot the computer, try and run the script again.

You will not need to preface it with sudo because Slax uses a root terminal by default.

---

### Post by deconstrained on 2011-03-02
> **alec4rs said:**
> Also typing fstab in terminal doesnt do anything, not sure what you meant by this.
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
```
cat /etc/fstab
```

When your system doesn't boot, or fsck fails, /etc/fstab is **THE FIRST THING** you should check for mistakes. But it sounds like, apart from not being able to boot, you can't get your root partition mounted, in which case:

fsck is probably failing while you're booted up to your livedisk because the livedisk IS /dev/sda; the names of block devices as shown in /dev are assigned at boot time by a core Linux utility called udev, and these names can differ between reboots. **The following command should tell you which block device in /dev corresponds which physical drive:**

```
sudo blkid
```

When you've identified your root partition (on which Ubuntu is installed), let us know and we can help you go from there.

Also, I disagree with the motion that reinstalling would be necessary or worthwhile.

---

### Post by alec4rs on 2011-03-02
Hey guys!

Problem solved (Thanks Rubi)

I made a bootable USB with Slax and before I even tried anything else I tried fsck which worked. No file loss (it seems like) and everything is exactly how I left it.

---

### Post by guilleme on 2011-03-02
It's great you have fixed it!, Congrats. 
Just wanted to make a small clarification. On my first comment here, I proposed that it could be Easier to just install again than to repair, but I never wanted to say that re-installing was the only way to go. On most cases, almost each and every case actually, it is perfectly possible to repair the damaged thing. but sometimes it is easier to remake :).
Well, that's all, and see-ya.

---

### Post by Rubi1200 on 2011-03-03
> **alec4rs said:**
> Problem solved (Thanks Rubi)

I made a bootable USB with Slax and before I even tried anything else I tried fsck which worked. No file loss (it seems like) and everything is exactly how I left it.
Excellent! You are more than welcome too for the help :-)

Unlike the Ubuntu CD, Slax does not try and auto-mount partitions.

Keep it around, as you never know when it might come in handy again.

Also, please mark this thread Solved using the Thread Tools near the top of the page.

---

