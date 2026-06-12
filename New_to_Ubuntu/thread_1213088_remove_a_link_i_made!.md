---
title: "remove a link i made!"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by iwannalearn on 2009-07-14
Hi i created the following link

ln /emu/script/gbox /bin/gbox

only thing, i need to remove/delete it. how do i do it please?

i tried 

rm ln/emu/script/gbox /bin/gbox

is this correct please

---

### Post by rampageoberon on 2009-07-14
Hi there,

Just "rm /bin/gbox". That will delete the link that you made and keep the original file (/emu/script/gbox) intact.

Cheers

---

### Post by Tony Flury on 2009-07-14
> **iwannalearn said:**
> Hi i created the following link

ln /emu/script/gbox /bin/gbox

only thing, i need to remove/delete it. how do i do it please?

i tried 

rm ln/emu/script/gbox /bin/gbox

is this correct please

your ln command creates a file called  "/bin/gbox" linked to the file "/emu/script/gbox" (i think that is the right way round)

Therefore
```

rm /bin/gbox

```
will remove the link - but not the original file.

Personally in cases like this - i would have created a symbolic link : 
```

ln -s /emu/script/gbox /bin/gbox

```

The advantage of a symbolic link (for one) is when you do an "ls -l" on a symbolic link will show you which file it is linked to - where as a hard link wont show you the link information.

Also see : [http://ubuntuforums.org/showthread.php?t=310834](http://ubuntuforums.org/showthread.php?t=310834)

---

