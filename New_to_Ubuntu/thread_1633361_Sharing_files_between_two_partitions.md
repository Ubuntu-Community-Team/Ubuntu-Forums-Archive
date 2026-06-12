---
title: "Sharing files between two partitions?"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Devio on 2010-11-29
I know this sounds like a fairly silly question but it might be worth asking...

I've had Ubuntu installed via Wubi for a couple of months now but I don't want to make a full move over yet because I'm not totally confident.

Would it be possible, however, to find my music on my Windows partition and play it on my Ubuntu partition without copying it over?

Also while I'm on the subject, in the future when I decide to make a bigger move, is it out of the question to change the sizes of partitions so I could make my Ubuntu partition bigger? Maybe get a second hard drive and move it to fill that?

Sorry for the long post, thanks for reading.

---

### Post by Verbeck on 2010-11-29
not sure what you mean but you could make a link to that file/folder in your home directory (or access it directly)
just navigate to the file/folder, hold down 'alt' and left click and drag to where you want the link to be and select 'link here' from the context menu

edit : the location of the c: drive would be /host for a wubi install
open up places>computer>filesystem>host

---

### Post by Dark7man on 2010-11-29
> **Devio said:**
> Would it be possible, however, to find my music on my Windows partition and play it on my Ubuntu partition without copying it over?

I'm pretty much a noob to Ubuntu myself dude... but I'm doing this myself at the minute... I have a dual boot install with Windoze 7

I haven't tried the Wubi install before, and I'm not sure if how I am accessing files on my Windoze partition will be the same for Yourself, but no harm in trying to help... I'm sure someone with better knowledge will be along soon!

How I do it...
Go to (top left screen)  "Places>Computer" when inside there I can see all the partitions on my harddrive, and can browse through them.  Like I say I dont know if in Your setup this same way is possible but just thought I'd try n help! :)

Best of luck!

---

### Post by Devio on 2010-11-29
Sorry I posted this thread then went to uni for the day...  I totally didn't expect to be able to find everything in the host folder! That's awesome! Thanks for that!

I certainly feel better being able to share files between the partitions!

The other question I'd asked quite badly as it was kind of two put together; I'd asked, is it possible when a partition is already made to change the size of it.  And secondly, is it possible to take a partition to another harddrive connected to the machine?

---

### Post by aeiah on 2010-11-29
> **Devio said:**
> 

The other question I'd asked quite badly as it was kind of two put together; I'd asked, is it possible when a partition is already made to change the size of it.  And secondly, is it possible to take a partition to another harddrive connected to the machine?


yes, its possible to do both but usually its easiest to just reinstall. i guess it depends how customised things are and how time consuming it was to get things working (like if you have some funky wireless card or graphics problem).

if there's space on the disk, you can grow / shrink partitions. you should back things up before doing it though.

you can clone a partition from one device to another but if you aren't careful you can end up with issues. you should test it for quite some time before wiping the original drive. i suspect a common error is moving things across and thinking everything is working, only to wipe the original drive and realise the only copy of grub was on the original one.

---

### Post by Dark7man on 2010-11-29
> **Devio said:**
> Sorry I posted this thread then went to uni for the day...  I totally didn't expect to be able to find everything in the host folder! That's awesome! Thanks for that!

I certainly feel better being able to share files between the partitions!

The other question I'd asked quite badly as it was kind of two put together; I'd asked, is it possible when a partition is already made to change the size of it.  And secondly, is it possible to take a partition to another harddrive connected to the machine?

Sorry mate I meant to add... I can read my Windoze partition from Linux, but **I Cannot** read my linux partitions from within Windows, well not when dual booting the two OS like I am... I dont know even if its possible to with some configuration... due to Linux's File/format system "Ext4" [SIZE="1"](Which You never need to defrag ever I must add-I like that :D)[/SIZE] maybe a Guru could come along and clarify this for us?  :popcorn:

However, You'll be using Ubuntu more and more mate, its the future! :D  And You can browse Your Windoze partitions no problem from Ubuntu, what more is needed ;) :D

Let me know if You get stuck again mate, like I say I'm a noob myself but no harm in trying to help a fellow community member :guitar: Give a bit back from all the help the guys have given me! :)

---

### Post by philinux on 2010-11-29
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

Wubi is really only recommended to test out ubuntu.

I would recommend a dual boot setup.

---

### Post by Devio on 2010-11-29
Thanks all!  Very helpful.

And I am mainly only testing Ubuntu at the moment philinux, I plan on making it full dual booted over Christmas holiday when I have less work on.  Thanks for the input everyone :)

Ric

---

### Post by Megaptera on 2010-11-29
When you get round to it, useful guide here for partition sharing Windows/Ubuntu dual boot:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

