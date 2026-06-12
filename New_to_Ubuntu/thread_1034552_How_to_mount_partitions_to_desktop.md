---
title: "How to mount partitions to desktop?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by sativares on 2009-01-08
I've tried to mount a windows partition icon to my desktop, it works fine, I can see the icon and so, but after I reboot my system, its gone and I have to remount it again.

So my question is: How do I make the icon to stay on my desktop forever?

I use ubuntu 8.10

---

### Post by lovelyvik293 on 2009-01-08
To do this you have to mount the partition permananently,with the help /etc/mtab or /etc/fstab.

---

### Post by albinootje on 2009-01-08
> **sativares said:**
> I've tried to mount a windows partition icon to my desktop, it works fine, I can see the icon and so, but after I reboot my system, its gone and I have to remount it again.

So my question is: How do I make the icon to stay on my desktop forever?


Is it a NTFS partition ?
If so, install ntfs-config, and use that :
```

sudo apt-get install ntfs-config
gksu ntfs-config

```

---

### Post by matt79 on 2009-01-08
> **sativares said:**
> I've tried to mount a windows partition icon to my desktop, it works fine, I can see the icon and so, but after I reboot my system, its gone and I have to remount it again.

So my question is: How do I make the icon to stay on my desktop forever?

I use ubuntu 8.10

Well you can write a mount bash script or you can see if a mount manager will work. I have never tried the manager so I do not no what options they have.
Just go to Add/Remove and search for "mount" and see what comes up.

---

### Post by Facetious Falcon on 2009-01-08
Best way is to edit your fstab file. Might sound a bit daunting if you're new to ubuntu but basically in the terminal type:

sudo gedit /etc/fstab

You'll see a text file with something like:

/dev/sda1      /media/HARDDISK/      ntfs      defaults      0    0

Each of these lines represents a hard disk the first bit '/dev/sda1' represents the hard drive it will automatically be here if the hard disk exists (you need to make sure you choose the right one) and the second parameter '/media/HARDDISK/' is where that drive is mounted to - this can be wherever you choose but preferably in the /media/ directory. 

So just add a line that represents your hard drive in that format.

For an NTFS drive all the other options should be the same.

---

### Post by floatingpoint on 2009-01-08
This thread might be relevant: [http://ubuntuforums.org/showthread.php?t=1033965](http://ubuntuforums.org/showthread.php?t=1033965)

I had a very similar problem yesterday, and the advice i got in that thread fixed it.
Not a million miles from the advice already given here, mind, And this stuff is probably more specific to your particular problem.

---

### Post by gs_berg on 2009-01-08
I am very happy with the applet Disk Mounter, which I also recommend to you.  Just right-click on the top panel, select "**Add to Panel**" and then select **Disk Mounter**.  After that, you will have icons of all your disks on top of the screen all the time. Besides, icons of any external disks you mount will be added there too.

You can mount, open or dismount any drive by clicking on its icon and selecting an option from the drop-down list.  By mounting a drive, its icon will also be on the desktop.

If you want your disk to be accessible all the time, then when prompted for password to open it, you can check the box "remember password", which I however do not recommend and never do myself.

---

