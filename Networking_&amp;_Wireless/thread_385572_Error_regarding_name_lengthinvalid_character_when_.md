---
title: "Error regarding name length/invalid character when copying files from the network"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by stewymcstewstew on 2007-03-15
I just recently set up an Ubuntu file server.  It was a bit of a headache but nothing to bad, but I am very stuck.  I have all of my music on a mac laptop running os x, and am attempting to move all my music from the laptop to the server, but when I copy it gives me an error for any file with "/" or "?" in it.  I was wondering if anyone knows a way to force ubuntu to accept this character types OR to somehow append them with nothing or whatever it needs to do.  Nothing is worse than getting up to let your 20 gig transfer go and coming back hours later to see an error messege produced in the first 100 MBs of files!  Thanks in advance, and sorry if it's in the wrong forum.

---

### Post by Mr. C. on 2007-03-15
File names *cannot* contain / characters in Unix systems.  I am not sure what MacOS is doing, but I'd suspect they are mapping the / into an acceptable equivalent.

You must change /'s into some other character before the transfer, or use a program that will change the characters during the transfer.

There is nothing wrong with ? in file names, but they have to be appropriately escaped.  It may be tripping up your transfer program, but not knowing how you are transfering the files, I can't say for certain.  You can change these too if necessary.

How are you transferring them?

MrC

---

### Post by stewymcstewstew on 2007-03-16
Just through SAMBA file sharing.

---

### Post by stewymcstewstew on 2007-03-16
Oh and thanks for the reply!

---

### Post by Mr. C. on 2007-03-16
Ok, that explains the ? problem too.  Windows does not allow either ? or /, so you need to rename them first.  There are probably utilities to do this, or you can use a rename script.

MrC

---

### Post by stewymcstewstew on 2007-03-23
Thank you for the help!  I downloaded a mac application NameChanger, combined with spotlight it's been pretty easy.  I still have a few files here and there giving me trouble, but i'm getting them edited and it's MUCH less daunting.  It's kind of a pet peeve of mine when people don't follow up threads like this with any sort of confirmation, so I thought I would let you know I got it working!

Thank you for the help!  Community based support is awesome!

---

