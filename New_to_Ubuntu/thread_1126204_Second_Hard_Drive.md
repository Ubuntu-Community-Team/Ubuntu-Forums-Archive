---
title: "Second Hard Drive"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Tambaqui on 2009-04-15
Hey all!

Loving Ubuntu!

Now what I did just recently is reformatted and re-partition my second Hard Drive to ext3 cause I am officially done with Windows.

Now I did the usual steps to mount the actual drive no problems!

Question though, is there a way to get the drive to be seen in "Computer" and maybe the "Places" menu?

Like before with NTFS (from windows) it was already set up from fresh install. But since I have reformatted it and all, its no longer on it :-/

Any help would be appreciated!

Thanks

---

### Post by aktiwers on 2009-04-15
I think you need to add it to your fstab file..  here is a looong guide:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

But all you need is to add one line.

---

### Post by MegaJim on 2009-04-15
aktiwers, I think he already has the drive automounting, which is why it doesn't show up under My Computer.

That is the way nautilus is setup, it only shows unmounted drives in my computer.

Linux' view of storage is somewhat different (simpler) than Windows.  But to see the top level of a given storage device, navigate to its mount point.  You can then add a bookmark to that location, which will be accessible from the places menu in nautilus and the gnome panel.

A nice tool for managing all this stuff is Disk Manager, its in the repos and will make your life a great deal easier.

---

### Post by Tambaqui on 2009-04-15
Thanks!

Atkiwers post and looking through lead me to here:

[http://users.bigpond.net.au/hermanzone/p10.htm#Click-Icon_Mounting](http://users.bigpond.net.au/hermanzone/p10.htm#Click-Icon_Mounting)

I had to set up a label in order for it to appear on Computer and Places. Did it and got it working!

Thanks anyway! Much appreciated!

---

### Post by aktiwers on 2009-04-15
Great - glad you got it to work! 
I better check if I remembered to label my partitions when I get home

---

