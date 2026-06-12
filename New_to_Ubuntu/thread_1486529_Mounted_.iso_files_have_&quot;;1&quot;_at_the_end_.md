---
title: "Mounted .iso files have &quot;;1&quot; at the end of all filenames"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by El Lance-O on 2010-05-17
When I mount .iso images, ";1" is appended at the end of all filenames rendering them useless unless I rename them.

How might I prevent this from happening?

---

### Post by El Lance-O on 2010-05-18
bump?

---

### Post by jbrown96 on 2010-05-18
Not entirely sure what is happening. Could you post the output of ```
ls -al
``` on the directory where it is mounted?

---

### Post by balgaltz on 2010-05-18
Try this:
Get "gmount-iso" from Ubuntu Software Center.
Then
```
sudo gedit /usr/share/gmountiso/Gmount-iso.py
```
Go to line 198, you should see
```
+ '-- mount -o loop -t iso9660 '
```
Replace it with
```
+ '-- mount -o loop -t auto '
```
and save it.

Then use gmount-iso to mount your images.
Report back if you still see the ";1" at the end of filenames

---

### Post by jbrown96 on 2010-05-18
> **balgaltz said:**
> Try this:
Get "gmount-iso" from Ubuntu Software Center.
Then
```
sudo gedit /usr/share/gmountiso/Gmount-iso.py
```
Go to line 198, you should see
```
+ '-- mount -o loop -t iso9660 '
```
Replace it with
```
+ '-- mount -o loop -t auto '
```
and save it.

Then use gmount-iso to mount your images.
Report back if you still see the ";1" at the end of filenames

I don't think that's likely to help at all. the type is iso9660 anyway, so auto will always choose it. Plus, gmount isn't necessary.

---

### Post by El Lance-O on 2010-05-18
> **jbrown96 said:**
> Not entirely sure what is happening. Could you post the output of ```
ls -al
``` on the directory where it is mounted?

I'm not quite sure where it is located, I'm mounting it with the built-in Archive Mounter. I checked /media and /mnt.

---

### Post by j.bell730 on 2010-05-18
> **El Lance-O said:**
> I'm not quite sure where it is located, I'm mounting it with the built-in Archive Mounter. I checked /media and /mnt.

Use this command...
```
sudo find / -iname \*.iso
```

**sudo** - elevates your privileges to search.
**find** - command used to search for files and directories.
**/** - your root directory (or all files and folders on your computer), you need sudo rights to search here.
**-iname** - case insensitive search for any files with the following parameter in the name.
**\*.iso** - the file extension (the only thing we have to go on) -- '\*' is appended to the beginning because we don't know the full filename, and that's used as a wildcard.

---

### Post by El Lance-O on 2010-05-20
No, that locates the .iso file I'm mounting, but it does not show the location of where it is mounted. I know what directory the file is in, that is not the issue here.

Whenever I mount an .iso, it appends ";1" to the end of all filenames within the .iso. Using Archive Mounter with the right-click menu, it does not mount it to /media or /mnt, the usual mount directories.

For example:

"SETUP.EXE" is displayed as "SETUP.EXE;1", rendering the extension useless.

---

### Post by ateap0tist on 2010-08-13
I have the exact same problem. Tried to install rybka, mount iso with archieve mounter and all files have ;1 at the end... Anyone got a solution?

---

