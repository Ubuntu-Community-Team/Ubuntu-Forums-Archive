---
title: "Deleted file"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by unknown user on 2009-10-07
I deleted a file the other day, which I done by mistake. It was deleted and not sent to the trash can.

Is there anyway I can get it back?

---

### Post by zeroseven0183 on 2009-10-07
It's still possible to recover given that the location where the file was written in the disk is not yet overwritten by another file.

You can check out steps to recover your file here: [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Malta paul on 2009-10-07
Was your file in root? If it was it will not show in the desktop trash can as there is another trash can in root.

---

### Post by unknown user on 2009-10-07
Cheers guys, will do this when I get home.

So if they can be recovered, is there any way to permantly delete files of a hard drive (such as bank details and passwords), that I have previously deleted and have not yet been written over? I know there are programs for windows, that do this.

---

### Post by t0p on 2009-10-07
> **unknown user said:**
> Cheers guys, will do this when I get home.

So if they can be recovered, is there any way to permantly delete files of a hard drive (such as bank details and passwords), that I have previously deleted and have not yet been written over? I know there are programs for windows, that do this.

The program 'shred' can permanently delete files. It is of limited use if you use a journalled filesystem, but if you use ext3 in default (data=ordered) mode, it works fine. Check the shred manpage for full details. There is also a package called 'secure-delete' which offers similar functionality to shred plus other features such as secure deletion of data in  RAM. Both of these packages are in the repos I believe.

---

### Post by unknown user on 2009-10-07
Great thanks for that, will have a look:)

---

### Post by unknown user on 2009-10-07
I have installed shred and I think that it is working fine.

I have been unable locate the file in the root. Where about could I look?

---

### Post by jmszr on 2009-10-07
unknown user,

This has some instructions for using shred, plus other file deletion tools: [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html) .

---

### Post by unknown user on 2009-10-08
I have installed shred and can right click to delete a file. Is there anyway that I can see the progress of the file being shred in say a terminal window? As now it just goes and no way of checking it has gone.

Also I have tried to use the terminal window and shred a file by typing (shred -f -u -v -z filename) and it tells me the file can not be found. I have tried the file name only and even the full path and still no good.

Any ideas?

---

