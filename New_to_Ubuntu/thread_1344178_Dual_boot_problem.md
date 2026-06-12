---
title: "Dual boot problem"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Leprachaun on 2009-12-02
I guess I did something wrong when I installed 9.10. Ubuntu is the only thing that loads GRUB doesnt give me an option to load anything. I checked the forums to see how to get windows to be an option in grub and came up with editing /boot/grub/menu.lst at the end of the file with 
 
title Windows
rootnoverify (hd0,0)
chainloader +1
 
problem is /boot/grub/menu.lst is empty. 
Please help and sorry if I dont have all the info you need.

---

### Post by namok on 2009-12-03
Ubuntu 9.10 uses GRUB2, which not use menu.lst but grub.cfg. Have a look at the [GRUB2 guide]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by ukripper on 2009-12-03
post output of this:
```
gedit /etc/default/grub
```

---

### Post by musarraf172 on 2009-12-03
> **Leprachaun said:**
> I guess I did something wrong when I installed 9.10. Ubuntu is the only thing that loads GRUB doesnt give me an option to load anything. I checked the forums to see how to get windows to be an option in grub and came up with editing /boot/grub/menu.lst at the end of the file with 
 
title Windows
rootnoverify (hd0,0)
chainloader +1
 
problem is /boot/grub/menu.lst is empty. 
Please help and sorry if I dont have all the info you need.

It seems that ubuntu did not recognise your windows install. Ubuntu 9.10 uses grub2. It does not have any menu.lst . It keeps all the grub configuration in "/boot/grub/grub.cfg" . Manual editing of grub.cfg is not suggested. But nothing to worry about..

Just edit the manual os prober file..
Then run " sudo update-grub2"

To do so ,

open a terminal then type the following:

$ sudo gedit /etc/grub.d/40_custom


The gedit will open the 40_custom
Now add the followings. 


title Windows
rootnoverify (hd0,1)
chainloader +1


Now save the file and exit from gedit. [ I am assuming that windows is installed in your primary hdd first partition. The numbering of partion in grub2 is different from grub. Therefore (hd0,0) is replaced with (hd0,1) ]

Now run the following command :


$ sudo chmod a+x /etc.grub.d/40_custom
$ sudo update-grub2

The windows entry will be added in your boot menu. U can cross verify by opening the file "/boot/grub/grub.cfg"

Now reboot your system and hope u can boot in your windows partition...

---

### Post by Leprachaun on 2009-12-04
thanks but I have no idea what I did wrong but it aint working. windows is on sda1 and I tried inputing that as well and still no luck. if I try to mount the drive in ubuntu i get an unable to mount filesystem error. but when i boot from a puppy cd I can view the files. there is also 2 different versions of windows xp on that drive (home and Pro). I really only want to run windows once more before I delete it so I can get all the programs from this compter to my wifes

---

### Post by musarraf172 on 2009-12-04
> **Leprachaun said:**
> thanks but I have no idea what I did wrong but it aint working. windows is on sda1 and I tried inputing that as well and still no luck. if I try to mount the drive in ubuntu i get an unable to mount filesystem error. but when i boot from a puppy cd I can view the files. there is also 2 different versions of windows xp on that drive (home and Pro). I really only want to run windows once more before I delete it so I can get all the programs from this compter to my wifes



I think you may have some file system errors in your windows partition. Try to run chkdsk after booting from some msdos rescue program.

---

### Post by Leprachaun on 2009-12-04
can u recommend one?

---

### Post by tom.gobel on 2009-12-04
[Ultimate boot CD for Windows]("http://www.ubcd4win.com/")

---

### Post by QIII on 2009-12-04
If it is any help to you.  Here is my 40_custom.

I don't think musarraf172 has it quite right.  That looks like an old menu.lst entry.

The drive designations/partitions will be different in your case.  I have three physical drives with one OS on each.

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Vista" {
        set root=(hd1,1)
        chainloader +1
}

menuentry "OpenSolaris" {
        set root=(hd2,1)
        chainloader +1
}

```

---

### Post by Leprachaun on 2009-12-04
so should I put sda1 instead of hd1?
could the problem be that I have 2 windows os's on the same partition?

---

### Post by QIII on 2009-12-04
Mine works as is, with "hd".  I have three SATA drives.

---

### Post by Leprachaun on 2009-12-16
well I finally got it to work I didn't know how to get the GRUB menu to show. found out you had to hold the shift key down at boot. now how do I get the menu to load automatically?

---

