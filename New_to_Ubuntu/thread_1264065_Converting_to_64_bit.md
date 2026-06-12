---
title: "Converting to 64 bit"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Marlowe221 on 2009-09-11
Ok here's what I'm trying to do. I want to remove the 32 bit version of 9.04 and install the 64 bit version in it's place. 

I still want to dual boot with Vista. I would really prefer not to reinstall Vista unless it's absolutely necessary. Ideally, I would like to find a way to reformat the partition that Ubuntu is on now and install the 64 bit version in the same partition (or a new one of the same size).

Is that possible?

---

### Post by NoaHall on 2009-09-11
Yep, easily done. Just get the 64 bit install disk, boot up, then install to your current ubuntu HD.

---

### Post by Marlowe221 on 2009-09-11
Hmmm.... When I did that it would allow me to create a new partition (that is to say, it would allow me to install 2 separate Ubuntus) but it did not seem to want to let me use the same space that I have it on now.

Did that make any sense?

---

### Post by NoaHall on 2009-09-11
Look at that -[IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu904installation-small_007a.png[/IMG]
Choose entire disk.

Or if Windows and Ubuntu is on the same disk, then boot into the LiveCD, and then use gParted to wipe it.

---

### Post by Jive Turkey on 2009-09-11
You might find it helpful to examine your partitions if you have any similar ones before booting into the install.  This is just so you don't accidentally format the wrong one(s).

When running the installer choose the option to manually specify the partitions.  You need a "/"(root) partition, and a swap partition, if hibernate/suspend works for your machine make sure the swap is at least as big as your memory.  Adding a "/home" partition is highly recommended as you can keep your data across multiple installs (of linux).  I've never had any prob with / being only 10GB, and using more room in /home where I keep my stuff.  Keep in mind though that unless otherwise specified by you /tmp lives in the / partition and you could fill it up somehow.

In some cases the installer does not recognise all of the partitions, or it may look at them as separate hdd's.  In the screenshot above try the drop down bar to see if another hdd is listed.  It may be helpful to reformat the partition from the liveCD prior to running the installer.

---

### Post by Marlowe221 on 2009-09-11
Ok thanks for the help - I think I have it doing what I want it to do now.

---

### Post by NoaHall on 2009-09-11
Yes, if you do it manually, you control it completely.

---

