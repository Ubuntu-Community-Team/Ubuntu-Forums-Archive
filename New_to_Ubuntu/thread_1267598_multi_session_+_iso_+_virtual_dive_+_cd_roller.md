---
title: "multi session + iso + virtual dive + cd roller"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by macanudokiosko on 2009-09-15
To be honest: I've been like three months thinking how to submit this query to this site.  
I'll detail what I'd been doing in Windows XP:

Step A:
I periodically burned new pictures of my camera, to CDs. However, -doing this- I always erased all of the previous seasons of pictures (which remained stored inside the disc, of course).

Step B:
I then created an iso-image of that whole CD to the HD -for working right with it daily without using the CDrom drive-.

Step C:
I used the Nero Virtual Drive, to pick that iso-image, creating a virtual drive then.

Step D:
I used CD~Roller for accessing all the iso-CD sessions, one after the other, for retrieving the pictures of each old session -which weren't visible already in the explorer-.

---  Can anyone suggest the best way for doing it so, in Ubuntu? I've been having some troubles.  ---  macanudokiosko :)

---

### Post by abouzar on 2009-09-15
You can create multi-session ISO images using kdb. It is a powerful program which allows you to create and burn images from your files or a CD.

You can mount any ISO 9660 image in your linux system. First, you need to create a mount point which is a directory. If you want to treat it as a cd, then, do the following steps (assuming your image name and path is ~/image.iso):

```
cd /media
sudo mkdir iso
sudo mount -o loop ~/image.iso /media/iso

```This will load your ISO image as a disk. I hope that this can help you ;-)


> **macanudokiosko said:**
> To be honest: I've been like three months thinking how to submit this query to this site.  
I'll detail what I'd been doing in Windows XP:

Step A:
I burnt new pictures of my camera, to CDs. However, for this I erased all of the previous seasons (which remained stored inside the disc, of course).

Step B:
I created an iso-image of that whole CD to the HD, for working right with it daily.

Step C:
I used the Nero Virtual Drive, to pick that iso-image, creating a virtual drive then.

Step D:
I used CD~Roller for accessing all the iso-CD sessions, one after the other, for retrieving the pictures of each old session.

---  Can anyone suggest the best way for doing it so, in Ubuntu? I've been having some troubles.  ---  macanudokiosko :)

---

### Post by dwasifar on 2009-09-15
> **abouzar said:**
> You can create multi-session ISO images using kdb. It is a powerful program which allows you to create and burn images from your files or a CD.

I thought kdb was a debugger.  Do you perhaps mean K3B?

---

### Post by macanudokiosko on 2009-09-16
Problem: the k3b is creating funny separate files for each session, which are nothing like an iso file.

*[quote=abouzar;7956440]You can create multi-session ISO images using kdb. It is a powerful program which allows you to create and burn images from your files or a CD.*

---

