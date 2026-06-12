---
title: "Ubuntu and UDF - any easy solution?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-22
My mate has hundreds of movies backed up onto UDF formatted DVDs that he burnt using Windows Vista, and I want to grab a few off him but Ubuntu won't mount the disks. I've googled it and it seems to be a bit of an issue, even the UDF wiki page has a section on why UDF disks won't work on certain operating systems.

The solutions i've found seem overly complex, and are rather outdated... is there any way to get new UDF mount/read/write support on 9.04, like installing a certain package or a quick file edit?

---

### Post by CyberJack on 2009-09-22
Have you tried mounting them manualy?
like: sudo mount <drive> -t udf <mount point>

---

### Post by humphreybc on 2009-09-22
Nope I haven't yet, I'll have to borrow another disc off him for testing. As far as I know, that doesn't work.... from reading through other threads. Although most of those were quite old, going back to Gutsy/Hardy so I'm not sure if it's fixed by now or not.

---

### Post by haydnc on 2009-09-22
Reading UDF discs can and will work under 9.04 - I don't know about earlier versions of Ubuntu.

From memory I had to do two things, one very simple one a bit more advanced:

Install udftools:

```
sudo apt-get install udftools
```

(That's the easy one.)

When I went looking for a solution I also had to edit my /etc/fstab file so that Ubuntu can properly mount UDF discs (as well as older iso9660 discs). This may have been fixed in the latest versions but originally I had to do the second step (below).

Use your favourite editor and edit /etc/fstab:

Look for a line that looks like this...
```
/dev/scd0    /media/cdrom0   iso9660,udf user,noauto,exec,utf8   0  0 

or 

/dev/scd0    /media/cdrom0  udf,iso9660  user,noauto,exec,utf8   0  0
```

then change it so that it looks like this...
```
/dev/scd0   /media/cdrom0  auto  user,noauto,exec,utf8    0   0
```

Then try to mount your UDF disc and it *should* work.

---

