---
title: "The reasoning behind &quot;owning&quot; and then &quot;setting permission&quot; with a new hard drive?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by ruegore on 2009-03-25
Hi I'm new, but I've been trying to use Ubuntu for over half a year, and my experience has been quite a rough one.

My newest adventure had me adding a new 1 TB internal SATA hard disk to my Ubuntu desktop computer, and learning the very hard way that I not only needed to learn how to format the new device, but also to "chown" it AND set read/write permissions.

I have been trying for hours to figure out why my new HDD wasn't allowing me to write anything to it. Well, least to say I finally got it to work while lurking through multiple threads on this topic here. I'm not asking for more help with my new hdd, but I'm here to simply ask:

"Why can't adding a new hard drive be easier?"

Or maybe to be more direct, why can't all of the prerequisites be handled automatically while I'm using GParted to format my new hard drive so that once format of a new hard drive is complete, the current user will take ownership of it, have it mounted, and allowed to read and write to it instead of doing all of this footwork with next-to-no-help from the operating system?

Honestly, installing, formatting and using a new hard drive should not need be this difficult. Maybe there is some sort of linux philosophy behind this? I don't know.


As a side note, it's interesting that with several other SATA hard drives attached to the same desktop previously formatted in NTFS are still owned by root, but the current logged on user (me) has full read/write capabilities (even though the permissions tab says otherwise). I never had to modify /etc/fstab either. The volumes are listed in computer:/// and all I ever had to do was highlight and mount. Simple.

---

### Post by 3rdalbum on 2009-03-25
You shouldn't have needed to chown the entire device, just "chmod" mount point that you have created for it so your user has permission to read and write. Then you add the drive to fstab.

As for formatting, you always need to format a new internal hard disk no matter what operating system you are on.

Gparted's job is to format a disk, not organise mounting and mount points. Besides, it runs as ROOT; expecting it to mount the drive with read/write "for the current user" wouldn't help as the current user is not your user account, but root.

I recently added two new internal HDDs and I didn't find it difficult.

---

### Post by pbpersson on 2009-03-25
Last time I added hard drives I created a new folder in my home directory called "My Hard Drives" and then in there added new folders called SATA2 and SATA3.

Then I installed a hard drive mount GUI app, a couple of clicks and I was done.

Never had to change permissions on anything, never had to edit any fstab file, never had to go near the command line.

This is how things should work in the 21st century, in my opinion.

YMMV

---

### Post by ruegore on 2009-03-25
> **pbpersson said:**
> Last time I added hard drives I created a new folder in my home directory called "My Hard Drives" and then in there added new folders called SATA2 and SATA3.

Then I installed a hard drive mount GUI app, a couple of clicks and I was done.

Never had to change permissions on anything, never had to edit any fstab file, never had to go near the command line.

This is how things should work in the 21st century, in my opinion.

YMMV


That does sound very nice. Maybe the information I was reading was outdated?

By the way, what's the name of that hard drive mount GUI app?

---

### Post by pbpersson on 2009-03-25
> **ruegore said:**
> That does sound very nice. Maybe the information I was reading was outdated?

By the way, what's the name of that hard drive mount GUI app?

Let me preface this by saying - you need to have the folders setup on your drive where you are going to mount the drives and you need to know what partitions you are mounting.

In my case I was starting with sdb1 and sdc1 and I wanted to mount them to the folders I had created called SATA2 and SATA3.

This GUI app does not have a lot of options - you cannot do anything fancy with it - but that is why I like it.  Here is the description:

**PySDM is a PyGTK Storage Device Manager that allows full customization of hard disk mountpoints whitout manually access to fstab.**

---

