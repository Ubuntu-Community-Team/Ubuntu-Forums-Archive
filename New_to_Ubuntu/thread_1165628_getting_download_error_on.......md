---
title: "getting download error on......"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by archdlx on 2009-05-20
update manager.

Hi folks! First post, did search a little, can't find any answers. I am new to Ubuntu/Linux, but I think I am getting the hang of it.

Anyway here is the message I get:

"Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

I would appreciate any input.....probably something simple ;)

Thanks for your time,
archdlx

---

### Post by Zzl1xndd on 2009-05-20
you have a CDrom enabled as a repository. Go to software sources> third party tab and uncheck the cdrom line. Then you should be ok.

---

### Post by archdlx on 2009-05-20
tweak....
I did try that! It actually was "removed" from the list, but no joy!
Is there something in Terminal I should be doing?

Thanks again!

---

### Post by supersonicdarky on 2009-05-20
Make sure the lines that containing **cdrom://** are commented out or non-existant in /etc/apt/sources.list

---

### Post by archdlx on 2009-05-21
tweakedenigma and supersonicdarky.....

WOW - love those handles!!

If I had read tweaks post a little closer, or thought about what was written, DUH!

Thanks for the help from the both of you.):P


archdlx

---

