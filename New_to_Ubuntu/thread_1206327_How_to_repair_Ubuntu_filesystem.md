---
title: "How to repair Ubuntu filesystem?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Seri Linux on 2009-07-07
I recently installed Ubuntu 9.04.
 
Everything work fine until yesterday, I received this error message....
 
 
[IMG]http://2.bp.blogspot.com/_oBfdd4UBM40/SlLYcbtwAKI/AAAAAAAAAFU/yilhBkeXiZg/s400/101_0485.jpg[/IMG]
 
 
My question is, how can I repair my Ubuntu filesystem without reinstalling the whole filesystem?
 
Then I try to enter the Recovery Console...
 
[IMG]http://3.bp.blogspot.com/_oBfdd4UBM40/SlLY0lb41II/AAAAAAAAAFk/_oWmS57EpTQ/s400/101_0488.jpg[/IMG]
 
I try to select Repair broken packages.. But it still won't help.. It still got stuck.. cannot load.
 
 
So, my question is, how can I repair my Ubuntu filesystem without reinstalling the whole filesystem?
Because I already installed so many updates and programs on my Ubuntu.
 
Please help me, I'm waiting..
 
Thank you...

---

### Post by sdlynx on 2009-07-07
this has happened to me and for my case it fixed when I ran ```
fsck -a
``` when prompted to do so (it is shown in your screenshot also where you should have run that and not press Ctrl + D).  This process takes about an hour or more to run though so make sure you have time on your hands.

Good luck

---

### Post by binbash on 2009-07-07
I had that problem also.fsck should do the trick as mentioned above.

---

### Post by Herman on 2009-07-07
You can use Gnome Partition Editor (GParted) in your Ubuntu Live CD or you can use a special dedicated GParted live CD like [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or [Parted Magic]("http://partedmagic.com/").
Always leave your file systems unmounted until after the file system check, never try to run a file system check in a file system while it's mounted.

[LIST=1]
[*]Boot your Live CD, open Gnome Partition Editor and right-click on the partition you want checked. In Hardy Heron it is 'System-->'Administration'-->'Partition Editor'.
[*]Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply'  check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair filesystem (ext3_ on ....)' for details
[*]Be sure to fully expand all details and read what has been done. If it's the Ext3 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]

---

### Post by mcduck on 2009-07-07
> **Seri Linux said:**
> I recently installed Ubuntu 9.04.
 
Everything work fine until yesterday, I received this error message....

 
My question is, how can I repair my Ubuntu filesystem without reinstalling the whole filesystem?
 
Then I try to enter the Recovery Console...
 
 
I try to select Repair broken packages.. But it still won't help.. It still got stuck.. cannot load.
 
 
So, my question is, how can I repair my Ubuntu filesystem without reinstalling the whole filesystem?
Because I already installed so many updates and programs on my Ubuntu.
 
Please help me, I'm waiting..
 
Thank you...

Repairing broken *packages* has nothing to do with your problem.

Anyway, you could either try the "File System Check"-option, or open a root shell and then run "fsck /dev/sda7", as the error message suggests.

---

### Post by Seri Linux on 2009-07-07
Ok..I'll try this.
 
Thanks,

---

### Post by Seri Linux on 2009-07-07
> **Herman said:**
> You can use Gnome Partition Editor (GParted) in your Ubuntu Live CD or you can use a special dedicated GParted live CD like [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or [Parted Magic]("http://partedmagic.com/").
Always leave your file systems unmounted until after the file system check, never try to run a file system check in a file system while it's mounted.

[LIST=1]
[*]Boot your Live CD, open Gnome Partition Editor and right-click on the partition you want checked. In Hardy Heron it is 'System-->'Administration'-->'Partition Editor'.
[*]Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply' check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair filesystem (ext3_ on ....)' for details
[*]Be sure to fully expand all details and read what has been done. If it's the Ext3 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]
 
 
Thanks for this tips, Herman..

---

