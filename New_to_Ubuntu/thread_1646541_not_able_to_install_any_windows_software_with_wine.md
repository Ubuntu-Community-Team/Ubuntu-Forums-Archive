---
title: "not able to install any windows software with wine."
date: 2010-12-16
forum: New to Ubuntu
---

### Post by kart168 on 2010-12-16
Hi!

I've been using ubuntu for quite some time. now i'm using ubuntu 10.10 ( dual boot along with windows xp ) and when i'm attempting to install any software with wine ( windows emulator) i'm getting the following  error message: 

"The file '/media/Local Disk/software backup/FoxitReader23_setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

I can't any windows software in my ubuntu. Could anyone please help me with this???? 

Thank you

---

### Post by seawolf167 on 2010-12-16
To mark something as executable, run the following command in a terminal:

Change to the file directory

```
cd /path/to/file
```Give execute permission

```
chmod +x nameoffile
```

Run File

Right click -> select Open With -> Select Wine Program Loader, then double click the exe

---

