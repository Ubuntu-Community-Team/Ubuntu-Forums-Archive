---
title: "Error Mounting Volume (USB)"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by Xenomorph05 on 2011-01-20
I have searched the forum and anything on this topic hasn't fixed my problem so I am making this new thread. 

When I insert my usb and go into Disk utility it can't mount it and NTFS is not clean. The temporary fix that has to be run everytime I insert it is NOT good enough for me. I tried this usb on windows and gentoo and it works just fine! Only Ubuntu is complaining.

Is this a bug? Is this fixable? Should I reinstall Ubuntu 10.10?

---

### Post by Xenomorph05 on 2011-01-20
I'm not 100% sure why but this post seemed to have fixed my problem. Hopefully this will make it easier for someone else with this problem to find the fix faster.

> **dabl said:**
> Boot your Live CD, run GParted, navigate to the drive in question, right-click the graphic and choose "check", and then do "Apply".

Might was well do the internal drive(s) while you're at it.

Here's a great resource for such purposes, btw:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)


Note that a partition must be unmounted in order to be checked.

---

### Post by Xenomorph05 on 2011-01-20
I'm not 100% sure why but this post seemed to have fixed my problem. Hopefully this will make it easier for someone else with this problem to find the fix faster.

> **dabl said:**
> Boot your Live CD, run GParted, navigate to the drive in question, right-click the graphic and choose "check", and then do "Apply".

Might was well do the internal drive(s) while you're at it.

Here's a great resource for such purposes, btw:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)


Note that a partition must be unmounted in order to be checked.

---

### Post by Xenomorph05 on 2011-01-20
I'm not 100% sure why but this post seemed to have fixed my problem. Hopefully this will make it easier for someone else with this problem to find the fix faster.

> **dabl said:**
> Boot your Live CD, run GParted, navigate to the drive in question, right-click the graphic and choose "check", and then do "Apply".

Might was well do the internal drive(s) while you're at it.

Here's a great resource for such purposes, btw:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)


Note that a partition must be unmounted in order to be checked.

---

### Post by Xenomorph05 on 2011-01-20
edit: forum lagged and overposted sorry

---

### Post by Xenomorph05 on 2011-01-20
edited: to much lagg wow please delete these extra posts!

---

### Post by Xenomorph05 on 2011-01-20
I found a solution. Using gParted and checking the usb with it from a post on fixing NTFS being not clean.

---

### Post by Xenomorph05 on 2011-01-20
It was only a temporary fix. After restarting my computer and trying the same USB again it is giving the same problem. I also tried an external HDD and it no longer works either. 

What is wrong with my Ubuntu?

---

### Post by Conzo on 2011-01-20
> **Xenomorph05 said:**
> It was only a temporary fix. After restarting my computer and trying the same USB again it is giving the same problem. I also tried an external HDD and it no longer works either. 

What is wrong with my Ubuntu?


[B]sudo apt-get install ntfs-config

After this is installed 


apps then system   ,,then admin  ,,, ntfs config    this will help you 


Conzo 

[/B]

---

### Post by Xenomorph05 on 2011-01-20
> **Conzo said:**
> [B]sudo apt-get install ntfs-config

After this is installed 


apps then system   ,,then admin  ,,, ntfs config    this will help you 


Conzo 

[/B]

I installed it. Tried to open it, it showed up in my window list but then dissapeared. i restarted and tried it again. It oponed, asked for my pass and then closed...?

---

