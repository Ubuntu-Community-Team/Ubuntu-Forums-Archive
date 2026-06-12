---
title: "formatted /home partition"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by adedi on 2009-08-11
I got some help installing ubuntu 9.0.4(dual boots with windows vista)

I mistakenly formatted /home partition while on windows to NTFS and I did not backup some of my documents,  is there anyway I can recover the partion or my documents if I am to do it myself?

---

### Post by mgranet on 2009-08-11
Firstly: Unmount or stop using the drive experiencing data loss, if at all possible.

I deleted some critical files once, and used Foremost with good results. (It will take a loooong time to run. Let it run, even if it appears locked)

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

There are some more good options out there, so wait for others to comment before you commit to one.

EDIT: Debs can be had here:

[http://linuxappfinder.com/package/foremost](http://linuxappfinder.com/package/foremost)

Since this needs to be done on a unmounted drive, you should download the deb and install from the LiveCD.

---

### Post by starcraft.man on 2009-08-11
STOP writing to the drive for the love of everything. Shutdown and reboot to a live CD.

OP please see testdisk. It is used for partition reconstruction. I'm not 100% certain, but I believe if you used testdisk to reconstruct the partition and reassign it to the filetype (ext 3 or 4, know which one) it was before format you could simply mount and get off any valuables.

See my thread on this, [here]("http://ubuntuforums.org/showthread.php?t=1200149"). I wrote a lengthy explanation, see the REALLY REALLY long post explaining. Test disk can't hurt the drive anymore imo, it just makes a new table. The instructions weren't written specifically for you, but I'm sure ya can figure it out. Download a copy on any live CD (or install to live CD) and run from console, comes with a text GUI. It doesn't write anything to the actual data, so you can always fall back to mgranet's idea for file recovery, that way a bit more involved though I imagine.

After table creation, try and mount it as normal in a file manager from Ubuntu. If it doesn't work and you can't see data, mgranet. 

In future, triple check what drive ya format, it's serious stuff.

---

### Post by adedi on 2009-08-11
thanks alot

---

