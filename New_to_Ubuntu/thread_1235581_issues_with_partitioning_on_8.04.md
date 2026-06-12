---
title: "issues with partitioning on 8.04"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2009-08-09
Hello again all.. so recently I decided I wanted to try out ubuntu again, as i'm getting pretty bored of Vista. So I whacked in my 8.04 disk. Bare in mind I wanted to keep Vista on this system for now so I can transfer stuff over.

Anyway... I remember last time I installed it I was given the choice of shrinking down my partition to make room for ubuntu, which was perfect. This time however.. it isn't giving me the same option. When asked how I want to partition the disk, the only option i'm given is to use the entire disk or do it manually. 

As shown here: [img]http://img190.imageshack.us/img190/6627/screenshot1uyu.png[/img]

Quite frankly i'm confused.. and was even more when I looked up a tutorial and realised it should look like this:

[img]http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__XP_first__images/ubuntu.jpg[/img]

So... any suggestions what to do? I'd rather not use the entire disk as there's stuff I need to remove from my vista partition and I don't have any external hard drives etc to do so.

---

### Post by jerrrys on 2009-08-09
your screenshot looks more like 7.04 to me.  you sure about it being 8.04?

---

### Post by mapes12 on 2009-08-09
Hi

What I would do is boot my machine using a GParted Live CD then setup my partitions with Gparted by resizing windoze to create the space I needed. Then in the free space create separate partitions for "/", /home and then swap. Reboot with the Ubu installation disk. At partitioning select **manual** then configure the installer to install in accordance with the partitons pre set for "/", /home and swap.

---

### Post by LewRockwell on 2009-08-09
Several Issues:

One is that your post references Vista and a screenshot shows XP?

If it is Vista then you must use Vista to prepare your partitions!

If it is XP then you'll find various posts, threads, and tutorials both on the ubuntuforums and strewn across cyberspace...

Also, it is highly recommended that you try out Ubuntu 9.04 Jaunty Jackalope via the LiveCD function and install the latest version if it works with your equipment...

And, it is preferable for screenshots to be attached to the post as opposed to included within the post itself...

We now return you to your regularily scheduled programming

.

---

### Post by LewRockwell on 2009-08-09
> **mapes12 said:**
> Hi

What I would do is boot my machine using a GParted Live CD then setup my partitions with Gparted by resizing windoze to create the space I needed. Then in the free space create separate partitions for "/", /home and then swap. Reboot with the Ubu installation disk. At partitioning select **manual** then configure the installer to install in accordance with the partitons pre set for "/", /home and swap.

please disregard the above quoted post if you are using Vista(as per my previous post)

.

---

### Post by mapes12 on 2009-08-09
> **LewRockwell said:**
> please disregard the above quoted post if you are using Vista(as per my previous post)

.Sorry!

I thought GParted supported ntfs? Are we saying that GParted is only useful for filesystems outside of windoze? and if so I would be happy to learn more about any shortcomings that GParted may have. I've been relying on it so much with the boxes I have been configuring. No problems so far 8-[

Thank you.

---

### Post by LewRockwell on 2009-08-09
> **mapes12 said:**
> Sorry!

I thought GParted supported ntfs? Are we saying that GParted is only useful for filesystems outside of windoze? and if so I would be happy to learn more about any shortcomings that GParted may have. I've been relying on it so much with the boxes I have been configuring. No problems so far 8-[

Thank you.

there are many reports of extreme Vista displeasure after using the partition editor

therefore we have been discouraging others from making this same mistake

it is an issue with Vista...not the file system...the partition editor does work with NTFS and XP doesn't seem to mind at all

.

---

### Post by MrJoeyUK on 2009-08-09
Sorry for any confusion with the XP screenshot.. it wasn't one I took, I found it on a google search and used it as an example, to show what was missing from my partition screen.

As for doing it manually..i'm not too sure I want to, as I'm not particularly confident I'd do it correctly.. What I have realised is that I had 10 GB of free space, which wasn't attached to my main vista partition, so maybe that was making the partition editor think I didn't want to dual boot, so i've resized it and i'm gunna try again in a minute. I'll report back. :)

---

### Post by mapes12 on 2009-08-09
> it is an issue with Vista...not the file system...the partition editor does work with NTFS and XP doesn't seem to mind at allThank you Lew. That explains it then. I have only been setting up XP dual boot boxes. Thanks for the heads up about Vista, although only my daughters laptop has that installed and I'm sure she won't let my hands anywhere near it [-X

MrJoeyUK - Best of luck with your install. More than happy to input further from my Ubu experience case of need :lolflag:

---

### Post by MrJoeyUK on 2009-08-09
Well.. it didn't work. Could someone guide me to a useful guide on doing it manually? I think I could do it, I'd just want to be sure.

---

