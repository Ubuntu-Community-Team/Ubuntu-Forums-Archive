---
title: "sudo mount /cdrom -o ro,unhide,uid=nolan"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by swoll1980 on 2009-02-14
Is there a way to get Ubuntu to mount all CDs like this automatically?

---

### Post by Dr Small on 2009-02-14
Post your /etc/fstab

---

### Post by swoll1980 on 2009-02-14
> **Dr Small said:**
> Post your /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c8ded625-4a94-4cd2-be6b-497c5f8e5e00 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2e5bca8c-c362-48ff-afb6-fc69620f2d68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by JohnLM_the_Ghost on 2009-02-14
> **swoll1980 said:**
> If you don't want to help that's fine, to expect me to be able to translate an answer to my question from man fstab is insulting, and completely unappreciated. Next time you can save yourself time by simply typing RTFM. Though if I could understand the f-ing manual I wouldn't need much help.
You've given less enough info to be ambiguous.
besides /etc/fstab is probably what you want to edit.

try having entry like this or similiar
```
/dev/scd0       /media/cdrom0   udf,iso9660 ro,uid=nolan,noauto,unhide,exec,utf8 0       0
```

---

### Post by swoll1980 on 2009-02-14
> **JohnLM_the_Ghost said:**
> You've given less enough info to be ambiguous.
besides /etc/fstab is probably what you want to edit.

try having entry like this or similiar
```
/dev/scd0       /media/cdrom0   udf,iso9660 ro,uid=nolan,noauto,unhide,exec,utf8 0       0
```

so if a change this
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

to
```

/dev/scd0       /media/cdrom0   udf,iso9660 ro,uid=nolan,noauto,unhide,exec,utf8 0       0
```

it would mount Cds in the way that```
 sudo mount /cdrom -o ro,unhide,uid=nolan
``` does?

---

### Post by JohnLM_the_Ghost on 2009-02-14
> **swoll1980 said:**
> so if a change this
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

to
```

/dev/scd0       /media/cdrom0   udf,iso9660 ro,uid=nolan,noauto,unhide,exec,utf8 0       0
```

it would mount Cds in the way that```
 sudo mount /cdrom -o ro,unhide,uid=nolan
``` does?
I do think so... but I am not 100% sure if you asking that?
Just try and see what happens... if it doesn't work, we'll think of something else.

---

### Post by swoll1980 on 2009-02-14
This isn't working either. Certain Windows CDs refuse to mount for some reason unless I use the root account```
 sudo mount /cdrom -o ro,unhide,uid=nolan
``` , and I can't figure out why.

---

### Post by JohnLM_the_Ghost on 2009-02-14
Did edited fstab file helped at all?
I think I failed to mention to reboot, but I guess you should've thought of it already.

By saying "certain windows cds", I suspect those might be Vista's UDF cds.
I know there is some inconsistencies about UDF versions and stuff...
Can't think of anything useful right now though.

btw I'm wondering, why do you actually mount CDs that way?

---

### Post by swoll1980 on 2009-02-15
> **JohnLM_the_Ghost said:**
> 

btw I'm wondering, why do you actually mount CDs that way?

Well I have to use root like i said or they won't mount. The unhide is for certain disk (WoW is the only one I found so far) that hide the .exe for non windows pcs. Figured I'd add it on too, so I would have to worry about it in the future

---

### Post by bapoumba on 2009-02-15
7 posts were removed (including answers and quotes, no worries ;)). Please remember that RTFM is not welcome here. If this is all you have to say, please consider not posting, thanks.

---

### Post by JohnLM_the_Ghost on 2009-02-16
> **swoll1980 said:**
> Well I have to use root like i said or they won't mount. The unhide is for certain disk (WoW is the only one I found so far) that hide the .exe for non windows pcs. Figured I'd add it on too, so I would have to worry about it in the future
Err... that's not too good... At first I thought its something with the options. But I guess in this case earlier proposed solution won't exactly work.
Though I haven't yet encountered a CD which doesn't mount the usual way.
So if you MUST mount them as root, then there is no other way (i know of) than with terminal command.

However, if you leave edited options in /etc/fstab I think simply command ```
sudo mount /cdrom
```
will pull in options from fstab, so you don't have to type them all the time.

Other option would be change the command automounter use for mounting CDs... like making a custom script (it would ask for password though). But I haven't really done stuff with automounter :(

---

