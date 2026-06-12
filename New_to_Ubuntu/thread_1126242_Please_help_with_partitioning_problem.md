---
title: "Please help with partitioning problem"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by feb3 on 2009-04-15
In my experiment with dual-boot of Ubuntu with Vista, have encountered problems. Please could someone advise?

Laptop has a 160GB hard drive (one partition only).
I shrunk this partition to create a second of 66.5GB for Ubuntu.
Got it installed using guided install and Ubuntu resizd it to 50%for the installation i.e. 33.30GB.
I uninstalled Ubuntu from within Windows by deletion and repaired Vista to boot straight into it - no problems with that.
Now I have the C Partition of 113GB and 33.33GB of free space.
I remember that after there was another bit of free space which allowed me to delete it and it was taken up.
Now this free space does not want to be made into a simple volume.
Everytime I input the figures - advised 8 to 34129 MB it comes back with not enough space. Kept reducing it and got down to 18GB and still reckons not enough space.
The option for extending the C partition back to how it was is not offered on the right-click menu.
If I try to delete the free space it says it will become inaccessible.
Ideally, would like to restore it to as it was in the first place. Could someone please tell me how to do it?
feb3 is online now Report Post   	Edit/Delete Message

---

### Post by Hospadar on 2009-04-15
You should boot off a liveCD (could be any ubuntu cd, knoppix gparted cd, partition magic cd, whatever) and change the partitions back how you want them.  Windows doesn't play particularly nice with other people's partions, so the best bet is to use an external cd.  Furthermore, even in windows, on-line (as in, while the partition is in use) partition handling is difficult, and possibly dangerous (to your data).

In an ubuntu livecd, Alt-F2, type in "gksu gparted" and you'll get the partition editor and it's very straightforward what to do from there. (If you can't move or delete a swap partition, right click it and "swapoff")

---

### Post by feb3 on 2009-04-15
Thank you very much for the advice - now seems logical that Windows wouldn't like the Linux bit. Had thought about going back into the CD so your instructions are very much appreciated.

---

### Post by steve101101 on 2009-04-15
> **Hospadar said:**
> You should boot off a liveCD (could be any ubuntu cd, knoppix gparted cd, partition magic cd, whatever) and change the partitions back how you want them.  Windows doesn't play particularly nice with other people's partions, so the best bet is to use an external cd.  Furthermore, even in windows, on-line (as in, while the partition is in use) partition handling is difficult, and possibly dangerous (to your data).

In an ubuntu livecd, Alt-F2, type in "gksu gparted" and you'll get the partition editor and it's very straightforward what to do from there. (If you can't move or delete a swap partition, right click it and "swapoff")

i have done this myself before. Its quite easy.

---

