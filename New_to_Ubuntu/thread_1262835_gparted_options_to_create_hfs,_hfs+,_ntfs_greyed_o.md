---
title: "gparted: options to create hfs, hfs+, ntfs greyed out while partitioning external HD"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by swarup on 2009-09-10
I just bought an external HD and am partitioning it from the gparted which I have in installed in Jaunty. I have a dual boot set up with Jaunty/OSX (the computer is a MBP), and so I want to have two partitions on the external HD, which is my backup HD. One partition will be ext3, and the other hfs+. I've created the ext3 partition, but the option for hfs+ (as well as ntfs and others) is greyed out. How do I get the options to be available ?

---

### Post by mapes12 on 2009-09-10
I would try burning a [GParted Live CD]("http://gparted.sourceforge.net/"), booting from it then trying again.

---

### Post by swarup on 2009-09-10
I just found the solution, on the [gparted forum]("http://gparted-forum.surf4.info/viewtopic.php?id=1527"): 

> As of version 0.3.9 of GParted you can create and check hfs+ file systems.  To do this you also need the hfsprogs package.

Just open synaptic, search for and install hfsprogs, and then gparted works perfectly fine for creating and manipulating hfs+ partitions any way you like.

---

### Post by drs305 on 2009-09-10
Look at the Gparted main menu: View > File System Support.

I am running Karmic and the options for HFS and HFS+ only include moving, shrinking and copying. The Ubuntu version does not natively 
include the capability to create an hfs+ partition.

Check to see if the Gparted CD does. The same thing used to be true of NTFS - available on the Gparted CD but not in Ubuntu (although you could gain that ability by installing ntfsprogs).

---

### Post by swarup on 2009-09-10
Now: I'd like to mark this thread as SOLVED. What is the latest way for doing this? I noticed that when one opens a new thread, there is an option for setting the distribution instead of "ubuntu, or "kubuntu" etc, to "SOLVED". But once the thread is created, I don't see how to go back and reset that. 

I'd prefer not to add "[SOLVED]" to the thread title at this point, as there is no room for it without removing words from the current title, which as it stands may be informative for future users.

---

### Post by drs305 on 2009-09-10
> **swarup said:**
> Now: I'd like to mark this thread as SOLVED. What is the latest way for doing this? I noticed that when one opens a new thread, there is an option for setting the distribution instead of "ubuntu, or "kubuntu" etc, to "SOLVED". But once the thread is created, I don't see how to go back and reset that. 

I'd prefer not to add "[SOLVED]" to the thread title at this point, as there is no room for it without removing words from the current title, which as it stands may be informative for future users.

The way to mark it solved is through the Thread Tools link at the top right of the original post - but it marks it SOLVED so it looks the same as the format you don't want. However, you **can** also *unmark* it solved if that becomes necessary.

---

### Post by swarup on 2009-09-10
> **drs305 said:**
> The way to mark it solved is through the Thread Tools link at the top right of the original post - but it marks it SOLVED so it looks the same as the format you don't want. However, you **can** also *unmark* it solved if that becomes necessary.

I see. It's too bad one has to truncate the thread title in order to mark a post as "solved". I hope at some point they make it so one can change the "ubuntu/kubuntu" classification to "[SOLVED]". That way the title can remain intact.

---

### Post by drs305 on 2009-09-10
> **swarup said:**
> I see. It's too bad one has to truncate the thread title in order to mark a post as "solved". I hope at some point they make it so one can change the "ubuntu/kubuntu" classification to "[SOLVED]". That way the title can remain intact.

From what I can see the entire title is still displayed, unless it is a REALLY long title.

---

### Post by swarup on 2009-09-10
> **drs305 said:**
> From what I can see the entire title is still displayed, unless it is a REALLY long title.

Well, yes that is true. But any title which utilizes the entire allowed space, such as mine did in this thread, will be truncated.

---

