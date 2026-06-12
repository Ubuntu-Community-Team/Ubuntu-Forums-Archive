---
title: "Partition help resize increase space"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Ad88Ab99 on 2009-10-23
i had a windows partition and now i deleted it. there is some space left over and i cant use it on my ubuntu partition. the paritition the second from the left is nearly full and  i want to increase the amount of space there, along with the amount of space on the home partition. how do i do that?
thanks
when i try to unmount iy says:
The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

---

### Post by Elfy on 2009-10-23
You need to boot the livecd and use the partition editor in the System Admin menu; also you will likely need to turn off swap once in there.

It is also likely that the free space is outside the extended partition - you will need, if that is the case, to resize the extended partition before you can resize the ubuntu partition.

If you post the result of

```
sudo fdisk -l
```

we will be able to see if that extended partition scenario is the case.

You need to do the partition work in the livecd as then your install will not be mounted.

---

### Post by Ad88Ab99 on 2009-10-23
there is a picture

---

### Post by Bartender on 2009-10-23
Are you trying to resize from within your Ubuntu installation?

Not gonna work.  You need to boot from a CD that has a partitioning tool.  A lot of people use an Ubuntu LiveCD, but I prefer to create a GParted LiveCD.  It just works better than the partitioner within the Ubuntu LiveCD.

Link to GParted under my sig.  Download the latest stable .iso, burn to a CD like you would an Ubuntu download.  When you're done boot from the CD.

forestpixie beat me to it....

If you would like to post a screenshot, boot from an Ubuntu LiveCD.  When you get to the desktop, plug in a USB thumb drive.  Wait for it to be recognized.  Then go to System>Partition Tool or whatever it's called and bring it up.  Once you have the partition map up, go to Applications>Accessories>Take Screenshot.  Save it to the thumb drive, then make sure to right-click on the thumb drive icon and Eject it.  Get out of the LiveCD, use any PC to post the screenshot to this thread.

---

### Post by Elfy on 2009-10-23
> **mathiscool.a8@gmail.com said:**
> there is a picture

There is not - just post the output of the command I gave :)

---

### Post by m4tic on 2009-10-23
Get your Ubuntu CD and boot from it and not from your hard disk. The same way you did when you installed Ubuntu for the first time. When it first reads from your CD, choose your language and select "Try ubuntu without any change to your computer". After everything loads up and you can see your desktop. Navigate your mouse to the top panel on "system" --> "Admin"-->"Partition editor". Then increase the size of your Ubuntu partition from the side that's next to the empty space by clicking the ubuntu partition than click the resize icon. Use the arows and drag

---

