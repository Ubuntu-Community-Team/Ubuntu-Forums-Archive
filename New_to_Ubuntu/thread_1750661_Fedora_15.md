---
title: "Fedora 15"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by robgraves on 2011-05-05
I currently have a dual boot setup on my PC with windows 7 and ubuntu 11.04, i want to keep both of those, however i'm contemplating setting it up as a triple boot with fedora 15.  Currently fedora 15 is in beta and i'm wondering if i should just wait until the final release of F15 to attempt this or set it up with fedora 15 beta.
    My main question is that i have one hard drive, primary partition that windows set up as a boot partition, the windows partition, an extended partition that contains logical partitions for ubuntu 11.04 and linux swap, then a primary partition which is the recovery partition for windows.  my plan was to shrink the windows partition as did originally to make room for ubuntu, this would create unallocated space between the windows partition and the extended partition, i'm assuming i would have to add this to the extended partiton and create another logical partition for fedora 15,  what is the easiest method to do this?

---

### Post by garvinrick4 on 2011-05-05
You are allowed 4 primary partitions and extended partition counts as 1, the best way is to make room in extended partition for another operating system. So if you can make some
space and make your extended larger to accommodate another logical.
 When you install Fedora it uses Anaconda as a installation tool when you get to where to put grub say none, it uses grub-legacy and will cause a major problem. When you are
through installing go to your Ubuntu and update-grub and OS-prober will put Fedora in Grub2 config file and as a menu entry and all will be well in the world.

---

### Post by robgraves on 2011-05-05
Alright i have the partitions set up now, just need to install, yeah i heard about the grub conflict so i was intending on doing on what you said, thanks.

---

### Post by georgemc on 2011-05-05
Check this thread:

[http://ubuntuforums.org/showthread.php?t=1610092](http://ubuntuforums.org/showthread.php?t=1610092)

Even though its about F13 I think its still relevant to F15.  Lots of good info.

I will be updating my F13 install, aka fresh install with separate Home directory, to F15 when it comes out.

Since I do not Beta test on production machines I wait till the official release is out and then test the release on a spare computer.

Hope this helps.

George

---

### Post by robgraves on 2011-05-05
success, all three OS's, windows 7, ubuntu 11.04, and fedora 15 beta are instlled and functioning properly, thank you.

---

