---
title: "Access files on (Wubi) Ubuntu from Windows?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-11-12
As the title reads: how can I access my files on (Wubi) Ubuntu 9.10 from Windows 7?

---

### Post by nhasian on 2009-11-12
while your in windows, i dont think you can access the data in the virtual (wubi) disk.  instead of using wubi if you install ubuntu into its own partition then you would be able to access the data from windows.  

if you want to access your windows files from ubuntu (wubi) then they are in /host.

---

### Post by praveesh on 2009-11-12
> **ubuntuforums said:**
> As the title reads: how can I access my files on (Wubi) Ubuntu 9.10 from Windows 7?

that's not possible . If you install in a seperate partition, it's possible

---

### Post by brianfactors on 2009-11-12
To my knowledge, you cannot mount the windows file system like another partition, because Wubi installs Ubuntu INSIDE the Windows Disk, instead of creating a new section like happens in normal installation.

In my system, the Windows file system can be accessed in /host

So, open Nautilus, click on "File System" > host (assuming it's there) and (if my memory serves me) you can see the windows files (read only, unfortunately, but they're at least there).

---

