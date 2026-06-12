---
title: "not enough disk space"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by zeuso0 on 2010-11-19
It used to be good before I dissembled my laptop.
and I just dissembled my computer and assembled again. I don't know if that is the cause, but I got  a disk space problem now.

"GDM could not write a new authorization entry to disk. Possibly out of disk space“  This msg always pop up when I started Ubuntu. says  i don't have enough disk space.

And I used "ctrl+alt+F2" ,logged in at the prompt then do: sudo apt-get clean , and then got into the desktop.

I looked up the system monitor, the disk of my root disk is 98.2 MB free but the whole disk is 100% used. Why?

attached is a scree shot of disk space status.

---

### Post by DogMatix on 2010-11-19
98MB left out of 6.5 GB is not a lot of room in the scheme of things. How much space is required for an authorization entry? I admit I don't know myself but I would consider 98MB left to be not a lot.

---

### Post by sikander3786 on 2010-11-19
You definitely need to free up some space in your Ubuntu partition.

98.2 is not that much a free space on a 6.5 GiB partition. You can do the maths yourself. I think it would be greater than 99 % any way :-)

If you've got some personal files/data on that partition, move it somewhere else.

Seems like it is running as a virtual machine (??).

I don't get the reason why your /boot partition is triple the size of your root partition? And you also have some more data infact nearly 9 GB of data on that?

---

