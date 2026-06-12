---
title: "I installed Jaunty through Wubi, but what happens if I get rid of Windoze entirely?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by cleverusername on 2009-08-12
Hello Ubuntu forums,

As the title suggests, I installed Ubuntu 9.04 through Wubi on a Windows Vista installation to a second hard drive (WinVista was installed on what was the "C:/" drive on Windows, Ubuntu was installed on what was the "D:/"), and I'm just wondering what would happen if I formatted my C:/ drive for a fresh installation.

Would I be able to access my Wubi installation of Ubuntu?
Or would I have deleted the Windows bootloader?
Would Ubuntu ever boot again, or would I be stuck with a useless Wubi installation sitting dormant on my D:/ drive until I re-installed Windows and re-added it to my boot.ini?

And also, if I couldn't, could I somehow salvage my precious Wubi-Ubuntu "partition" with my installed packages and settings?

I know this is a LOT to ask, but help would be greatly appreciated!

Help save me from M$!

-Scott.

---

### Post by lisati on 2009-08-12
If you've installed Ubuntu using Wubi and later delete Windows, your Ubuntu installation will be lost. 

It's always a good idea to make backups of important data before making changes to your computer.

---

### Post by cleverusername on 2009-08-12
That's a shame, but thanks for the quick reply, it's appreciated. :)

In that case, if I want a more permanent solution, would you recommend jotting down the important packages/drivers I have gotten since I installed Wubi, formatting, partitioning and installing a full Ubuntu installation?

---

### Post by LewRockwell on 2009-08-12
> **cleverusername said:**
> That's a shame, but thanks for the quick reply, it's appreciated. :)

In that case, if I want a more permanent solution, would you recommend jotting down the important packages/drivers I have gotten since I installed Wubi, formatting, partitioning and installing a full Ubuntu installation?

whatever works best for you

.

---

### Post by cleverusername on 2009-08-12
Okay, thanks.

Sorry to keep going on, but I have one last question.

Is there a terminal command that I could enter that would list my installed packages?

Thanks again.

-Scott.

---

### Post by xPr0star on 2009-08-12
```
dpkg --get-selections > installed software
```

this will make a list of installed packages in your home directory

---

### Post by cleverusername on 2009-08-12
Brilliant, many thanks everyone. :)

-Scott

---

