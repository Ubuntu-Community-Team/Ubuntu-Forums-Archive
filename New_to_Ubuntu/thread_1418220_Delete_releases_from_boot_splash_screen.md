---
title: "Delete releases from boot splash screen?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Juhla Mokka on 2010-02-28
Hello

My machine boots to Ubuntu and Vista and I can select at the start which one I go to. After many ubuntu updates the list however has grown and grown, and now has like 15 different linux releases on it.

I think they are linux kernel versions (even don't know what a kernel is) and they have lots of numbers on them starting with 2.24 or somehtinglikethat.

**How can I shorten the list?**
What do they mean - do they take space on my hard drive?

Thanks :)

---

### Post by JKyleOKC on 2010-02-28
> **Juhla Mokka said:**
> **How can I shorten the list?**
What do they mean - do they take space on my hard drive?To shorten the list, navigate to the /boot/grub directory and open the "menu.lst" file there. About halfway down (line 113 in my copy) you'll see a line reading "# howmany=all" and if you change "all" to "2" you'll see only the two most recent kernels after your next update.

While you can change the line without root privileges, you can't save the changed file. To make the change stick, open a terminal window and type "gksu nautilus" to launch nautilus with root privilege. Then go to the file, make the change, save it, and exit from nautilus. Still in the terminal window, type "sudo update-grub" to put the change into effect.

These instructions work with Hardy LTS but if you upgrade to Karmic or Limpid, they use a different version of grub that doesn't have menu.lst.

As for taking up space on your disk, yes, the different kernel packages do take up space. You can go into synaptic and remove all of them but the most recent two (2.6.24.26 and 2.6.24.27 for Hardy LTS) to free up the space. It's a good idea to keep at least two, however, since sometimes the "latest" one will fail to work right after an update. When that happens, you can select the next-newer version and keep working.

And to explain what the "kernel" is, it's the true heart of the operating system that makes everything else work. It's continually being tweaked and improved. The 2.6 series is the third major revision since it was originally written, and the 24 in the version numbers indicates 24 minor revisions to the original 2.6 release. Finally the 26 and 27 show that many tweaks have been made.

Newer Ubuntu versions have kernels in the 2.6.31 range. However Hardy LTS won't ever leave the 2.6.24 series.

---

### Post by Paddy Landau on 2010-02-28
There's a better way than trying to fiddle with your Grub.

Simply uninstall the older versions!


[LIST=1]
[*]After you've successfully booted into the latest version, open Synaptic Package Manager (in your System > Administration menu).
[*]Go to Status > Installed.
[*]Search for the following, and for each one found *Mark for Complete Removal*. **Warning: Do _not_ mark the latest version, and I recommend that you also leave the next-most recent.** For example, if you have version 2.6.24-27, then don't mark 2.6.24-27 or 2.6.24-26; mark only the older ones.
[LIST]
[*]linux-headers
[*]linux-image
[*]linux-restricted-modules
[*]linux-ubuntu-modules (if this is missing, that's OK)
[/LIST]
 
[*]Go to Custom Filters > Marked Changes. Double-check that you haven't accidentally marked the two newest versions.
[*]Press Apply.
[/LIST]

---

