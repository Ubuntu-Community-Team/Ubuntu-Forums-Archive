---
title: "Partitioning  problem with Gparted"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Indigo340 on 2009-12-05
I'm trying to re-size my partitions using Gparted but when I right click the partition, the options I want are not available, the only options I can use are 'Format' and 'Delete'.

I have managed to delete a small partition to create unallocated space and want to re-size the partition next to this space.

Only have Ubuntu 9.10 installed, don't have Windoze any more.

The help files are not much help, can someone please point me in the right direction or give me a link for more information ?

---

### Post by electricFan on 2009-12-05
What kind of partition are you trying to resize?  Maybe you could link a screenshot of what your gparted looks like?

Psychocats has kind of an explanation of how to use gparted
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Paqman on 2009-12-05
You can't modify any partition while it's in use. Boot up into your LiveCD and run Gparted from there. You'll need to deactivate your swap partition by right click > Swapoff. But after that you should be free to make any changes you want.

---

### Post by Indigo340 on 2009-12-05
Can't just paste a screenshot into text box, I need to have a URL.

That is the very tutorial I was using but could not see what the problem is.

I'll try to describe the Gparted window.

Top line, Unallocated space, /dev/sda2  20.02GiB.   /dev/sda6 16.4GiB.  /dev/sda5 29.3GiB

Main window, 
unallocated                                      7.92GiB
/dev/sda2       ntfs                          20.02GiB            boot
/dev/sda3       extended                  46.85GiB            lba
    /dev/sda6   evt4            ubuntu   16.47GiB
    /dev/sda7   linux swap               783.39MiB
    /dev/sda5   ntfs                          29.35GiB

When I right click /dev/sda2 and /dev/sda7 and select Information, I get a notice which says, 'Warning. Unable to read the contents of this file system! Because of this some operations may be unavailable.

---

### Post by The Pinny Parlour on 2009-12-05
I have experienced something similar with GParted.  I used Hirens BOOT CD to resize when GP fails.

---

### Post by k3lt01 on 2009-12-05
> **Indigo340 said:**
> Can't just paste a screenshot into text box, I need to have a URL.

That is the very tutorial I was using but could not see what the problem is.

I'll try to describe the Gparted window.

Top line, Unallocated space, /dev/sda2  20.02GiB.   /dev/sda6 16.4GiB.  /dev/sda5 29.3GiB

Main window, 
unallocated                                      7.92GiB
/dev/sda2       ntfs                          20.02GiB            boot
/dev/sda3       extended                  46.85GiB            lba
    /dev/sda6   evt4            ubuntu   16.47GiB
    /dev/sda7   linux swap               783.39MiB
    /dev/sda5   ntfs                          29.35GiB

When I right click /dev/sda2 and /dev/sda7 and select Information, I get a notice which says, 'Warning. Unable to read the contents of this file system! Because of this some operations may be unavailable.

Is this running within Ubuntu? or are you using a separate Gparted CD? if you have it running within Ubuntu you'll have some difficulties because of things already mentioned. Google Gparted and download and then burn the latest Gparted CD. Use it to do the job if you aren't already that way you are running of a LiveCD and can resize the partitions as required.

---

### Post by louieb on 2009-12-05
> **Indigo340 said:**
> Can't just paste a screenshot into text box, I need to have a URL.

You can attach it.  (the paper clip).

---

### Post by Bartender on 2009-12-05
There are some functions within GParted that GParted can do but you have to go at it a little differently.  I've run into this several times.  Just recently I couldn't delete an extended partition until I used my magic trick.

The magic trick is...drum roll, please...

Right-click on the text describing the partition, down below the partition map.  Very often this will give you options that aren't available to you when you right-click on the visual depiction of the partition across the top of the screen.

Try it.

---

### Post by Indigo340 on 2009-12-05
OK thanks guys, it seems I overlooked the fact that you need to boot from Live CD.
I have now managed to move one partition but when I was reducing another one I got an ERROR message, it's not clear what the Error was because it completed the task to reduce another partition but so far so good.
I now want to extend the size of the main partition into some unallocated space but it won't let me.
And I don't see a paper clip to attach screenshots.

---

### Post by zaphod777 on 2009-12-05
Your other partition is most likely in the way you need to move the one that is in front of your main partition then you should be able to expand it.

Notice in my screen shot the swap is all the way on the right?

---

### Post by Indigo340 on 2009-12-05
Thanks Zaphod, it appears that I can only resize the partitions and not move them.
I have created plenty of unallocated space but cant move the partition to make way for enlargement of the main partition.



And Bartender, I don't see any other options when I click on the text


Still can't find that paper clip either.

---

### Post by zaphod777 on 2009-12-05
try right clicking on it you should be apple to move it if you are using the live cd. 

make sure it's not mounted etc. I know I have done it before when I upgraded my HDD.

---

### Post by Indigo340 on 2009-12-05
The action starts but always I get an error message and it never completes the action to move the partition.

I'll give Hirens CD a try when I get time

---

