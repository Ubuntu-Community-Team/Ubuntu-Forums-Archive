---
title: "How to remove ubuntu"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by MJ.alawami on 2008-12-18
I had a booting problem and I ended up installing ubuntu again so unfortunately I have now 2 ubuntu operating system in my computer and and Xp operating system.So i am willing to remove one ubuntu operating system?
Please answer the following clearly in steps..

Thank you

---

### Post by SuperSonic4 on 2008-12-18
Boot up the ubuntu you want to keep
Go into GParted
Click the other ubuntu install and press delete
Click Apply changes.

You might have grub troubles if you delete the one grub is configured on though

---

### Post by Duck2006 on 2008-12-18
> **SuperSonic4 said:**
> Boot up the ubuntu you want to keep
Go into GParted
Click the other ubuntu install and press delete
Click Apply changes.

You might have grub troubles if you delete the one grub is configured on though

You have to unmount it first, then format the partition.

---

### Post by MJ.alawami on 2008-12-18
> **SuperSonic4 said:**
> Boot up the ubuntu you want to keep
Go into GParted
Click the other ubuntu install and press delete
Click Apply changes.

You might have grub troubles if you delete the one grub is configured on though

Where is gparted

---

### Post by MJ.alawami on 2008-12-18
> **Duck2006 said:**
> You have to unmount it first, then format the partition.

How to unmount and how to format it

---

### Post by Duck2006 on 2008-12-18
System->Administration->Partition Editor
If it is not there open Synaptic Package Manager and load gparted from there.

---

### Post by lovelyvik293 on 2008-12-18
Gparted is same as the partition editor(System-> administration->Partition editor).
And here you can unmount and mount the partition and format them.

---

### Post by oldos2er on 2008-12-18
> **MJ.alawami said:**
> Where is gparted

 It's not installed by default. Run "sudo aptitude update && sudo aptitude install gparted" in a terminal to install it.

 Or boot from the LiveCD and run it from there.

---

### Post by Duck2006 on 2008-12-18
> **MJ.alawami said:**
> How to unmount and how to format it

When you run partition editor, Right click on the partition and click unmout.

---

### Post by MJ.alawami on 2008-12-18
> **Duck2006 said:**
> When you run partition editor, Right click on the partition and click unmout.

I right click for unmounting but an error appeared sayinge the following cannot be unmounted because of the "/" and it said you have to unmount manually how to do that ?

---

### Post by Duck2006 on 2008-12-18
Download the live cd of gparted and use that to do it with.

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by oldos2er on 2008-12-18
> **MJ.alawami said:**
> I right click for unmounting but an error appeared sayinge the following cannot be unmounted because of the "/" and it said you have to unmount manually how to do that ?

 If you're booted to / (root), then you can't unmount. That's why it's easiest to run gparted from a LiveCD.

---

