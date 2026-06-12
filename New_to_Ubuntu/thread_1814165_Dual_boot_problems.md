---
title: "Dual boot problems"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-29
Ok, I have searched and read many threads, and none of them seems to address this problem, so here we go.

I have a desktop (clone) in which I had, up until a couple of hours ago, 1 hard drive, with Windows 7 and Wubi.
Now, I added a second hard drive, and proceeded to reinstall everything, in order to have W7 again, and Ubuntu in the second hard drive, in a dual boot setup.
I installed W7 without incident, but now, when I try to install Ubuntu, it won't even show the second hard drive in the partitioner. And if I check on the "Use the largest continuous free space" box, it shows the drive in blue, and doesn't let me install there.
At this moment, after checking that box, I checked the "specify partitions manually" box, and I get a list of the partitions (including the second drive), but, when I select it and click on "Forward", I get a message saying "No root file system is defined. Please correct this from the partitioning menu"

What should I do next?

Thanks in advance. :)

---

### Post by carverj on 2011-07-29
I found a nice guide that may help you to get past your partitioning problems. Let us know if still stuck.

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

### Post by Matt__ on 2011-07-29
Inodoro; you just need to specify the ubuntu install drive as root by selecting '/' in the mount point drop down box in the partition properties.

@carverj; the guide looks ok, but there is no need for a boot partition imo, just / and swap, though some use a separate home for ease of reinstall should the worst happen.

---

### Post by Inodoro Pereyra on 2011-07-29
Thank you both for the replies.

First, I forgot to put one little detail in my first post: I'm trying to install 9:10. Sorry.:oops:

Anyway, I followed Carverj guide, and, so far, it's installing perfectly. I will keep this thread open, in case I have any more trouble.

Thanks again. :)

---

### Post by Inodoro Pereyra on 2011-07-29
Ok, update.
Tried the method on the guide Carverj linked. No luck.
Tried as Matt_ suggested. Nothing.
Tried several other ways (same method, just installing it in different partitions). Still nothing.

In most cases, after finishing the install and rebooting, I got the message:

> Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a keySo, finally, when I was getting ready to go buy a gallon of gas and take care of the computer for good, I decided to disconnect the master drive (in which Windows is installed), and put the second hard drive as master. Everything installed perfectly.

Now, I connected the 2 hard drives as they were installed originally, and got a new problem (yeah, shocking, I know):

Ubuntu works perfectly, but, when I try to boot on the other hard drive, I get this:

> GRUB loading.
error : no such disk
grub rescue>How do I fix it? :(

---

### Post by westie457 on 2011-07-29
Hi happened to find this thread by chance and may be of some help.

To recap your situation. You have two hard drives each with its own OS, and you can boot your computer with either drive on its own but not with both connected. Is that correct?

Are both your hard drives IDE (big flat ribbon cable) or SATA (small round cable) or do have one of each? 
Once that question is answered we can work out a solution.

By the way some good advice from the other posters.

---

### Post by Inodoro Pereyra on 2011-07-29
Hmmm... no.

I have 2 IDE hard drives, in a master/slave setup.
I installed Windows 7 in the master drive, and everything was working perfectly.
Then, I installed Ubuntu (9.10, and then upgraded to 10.04) on the second HD, connected as master, alone.
Now, with both drives connected as before, or with only the Windows drive connected, I get the error message posted above. Only the Ubuntu drive is working on the machine.
Both drives are recognized by the setup, and I can switch between them without a problem, but, when time comes to boot, the grub loads (even when the Ubuntu drive is not connected), and tells me there's no drive.

Now that I think about it, I think I just answered my own question. I must have messed up my windows install, when I was trying to install Ubuntu...

I'm gonna try reinstalling Windows, see what happens.

---

### Post by Inodoro Pereyra on 2011-07-29
YES!!

I did mess up the Windows.
Now everything is working perfectly.

Thanks again. :D

---

