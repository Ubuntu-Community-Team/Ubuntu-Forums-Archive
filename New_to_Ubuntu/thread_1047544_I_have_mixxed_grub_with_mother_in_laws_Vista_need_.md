---
title: "I have mixxed grub with mother in laws Vista need to fix"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ranch hand on 2009-01-22
My dreaded mother in law was nice enough to let me use her computer to test Ubuntu on her DSL connection.  This works great and automatically on both Hardy and Intrepid.

I used an external HDD prepared on my computer at home.  This also worked great.

Then I got clever and installed Hardy on that drive.  I did not disconnect her HDD.

Now I can't boot to Vista except through my drive with grub.

I need to fix this so that I can have my external back and she can boot as she is used to doing.

This is an Acer computer from Walmart and has no Vista disk.  It has the rescue stuff on sda3, if I remember right, and it comes up with the grub menu.  I pulled it up and went no further as I don''t really know what the heck I am doing there.  It is titled with XP and I want to make sure that I do not bugger things up worse.

My idea is to boot to that and try to;

bootcfg /rebuild
fixboot
fixmbr

after disconnecting my external so as to just have her machine involved.

Is there any validity to what I am thinking or am I simply silly?

---

### Post by bsharp on 2009-01-22
That is exactly what you need to do, although at the bare minimum just boot to the recovery console and do ```
fixmbr
``` will fix your problem just fine.

---

### Post by ranch hand on 2009-01-22
I booted into the recovery partition and I have choices;
factory default
repair from CD/DVD
SOMETHING
Exit

Obviously we want the CD option and we don't have one.  How do we get one?

---

### Post by jerome1232 on 2009-01-22
You can torrent this one here and burn it to disc, this isn't an install disc just has the recovery console [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by ranch hand on 2009-01-22
I am back at the ranch now and I doubt I am going sto download that here on dial up.  This is great info though and I will be back in town in a couple days and have a whack at it.

I am a little torqued about this.  She bought the computer with Vista an it.  She bought the OS.  She should get a CD.  This is not right.

She did not count on some bozo doing this either, but at least her machine runs this way.  I have Vista as the default OS and it boots great with grub.

---

### Post by ranch hand on 2009-01-22
Checked the site and it is good I can boot her Vista because it looks like the easiest way to do this.  I think it may just work.

Thanks a bunch jerome1232

---

### Post by ranch hand on 2009-02-04
I got the CD burned and it booted fine and then told me there was nothing wrong with the mbr at all.

Went to the CL and typed fixmbr - no such command.  Did a search and found that the command is supposed to be FixMbr or FixStartup.

Tried that and neither of those commands are reccognized either.

Decided there was nothing wrong with MBR.  Resized the recovery partition (111Gb/10Gb used) and made an extended partition of 50Gb and installed Hardy (32) on her HDD and set Grub to boot to Vista.  It actually boots faster than the origanal MBR anyway.

This way when Vista fills the 112Gb partition it is on with silly duplicate files of everything she can switch.  The woman saves very little and Vista takes up about 20% already.

---

