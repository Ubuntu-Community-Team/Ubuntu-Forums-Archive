---
title: "NTFS external hard disk remounts after safely remove"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by npjoseph on 2010-12-04
I upgraded to ubuntu maverick x86_64 recently and noticed a quirk with my external hard disk. Normally, if I right click the icon and click safely remove, the hard disk does not spin down; I can feel it spinning even after the safely remove operation. So what I do is I unmount the hard disk and then safely remove it, in which case, it spins down as it is supposed to. This used to work properly in lucid. In maverick, if I do this, the hard disk safely removes and then starts spinning again and remounts itself. It works properly the second time I unmount and safely remove. The hard disk is formatted in NTFS with a single partition. Any suggestions?

---

### Post by XeonBloomfield on 2010-12-04
Safe Removing is for disabling read/write operations on your device. Not for spinning down it.

---

### Post by coffeecat on 2010-12-04
> **XeonBloomfield said:**
> Safe Removing is for disabling read/write operations on your device. Not for spinning down it.

Maybe, but I can confirm the OP's experience. After 'safely removing', the drive remounts and can be written to again, which is hardly disabling read/write operations. Or at least not for long. I've got into the habit of simply 'safely removing' twice after which it remains unmounted, but it is an irritation. Except for flash drives, for which you get an 'eject' option which works as expected. I don't remember getting 'eject' with usb hard-drives.

@npjoseph, if you unmount the device from the terminal with 'sudo umount' it stays unmounted, but that's not very elegant. I'm surprised I've not seen more of this mentioned because it seems like a bug to me. I'll have a look on launchpad when I get a chance.

**Edit:** by the way...

> **npjoseph said:**
> The hard disk is formatted in NTFS with a single partition

This is unlikely to be a filesystem issue because I get exactly the same with a hfs+ formatted (Apple filesystem) USB hard drive.

---

### Post by coffeecat on 2010-12-04
I've found the relevant bug, here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755)

As you can see it seems that this affects nvidia chipsets only. What is the USB controller on your machine? Nvidia? You'll see that you can also use:

```
udisks --unmount /dev/whatever
```... instead of sudo umount.

Do you have a Launchpad account? If so, it would be helpful if you would do a 'me too' by clicking on the 'this affects me...' at the top of the bug thread, and/or adding a comment. The more report this, the more likely it is to be taken seriously.

---

### Post by npjoseph on 2010-12-04
i am sorry for being unclear. what i meant by unmount is the "eject" button in the nautilus bookmarks pane next to the external's name. i understand that safely remove stops all read/write operations. however, the hard disk does not power down, the hard disk still vibrates after safely removing. the pop i hear when i unplug the hard disk in this state sounds very unhealthy. :o when i "eject" and then safely remove, the hard disk no longer spins. until maverick, when after the same procedure, it starts spinning again and remounts. this never used to happen in lucid. could this be a nautilus bug?

---

### Post by npjoseph on 2010-12-04
thank you coffeecat. yes my machine has an nvidia chipset. i've added myself to the affected list.

---

### Post by npjoseph on 2011-05-29
the bug has not been fixed and still exists in natty. is it possible to remove the usb controller driver from natty and load the driver from lucid? if so, could someone please give me steps to do so? where can i find the controller driver from lucid?

---

### Post by npjoseph on 2011-06-03
bump

---

### Post by boulderbum on 2011-09-23
> **npjoseph said:**
> this never used to happen in lucid. could this be a nautilus bug?

Happens in lucid all the time on my system... I umount at the command line.

---

