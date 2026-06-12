---
title: "Starting Problem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by jesuspar on 2008-12-04
I am new to Ubuntu to please help me.

When booting the system I am getting the following message, and it freezes my computer.

[ 0.032111] ACPI : Unable to load the System Despriction Tables

[ 2.474282] Invalid Compressed Format (err22)

[ 2.575122] Kernel panic- not syncing : VFS : Unable to mount root fson unknow -block (0,0)

It is stopping every other Start up. 

Please help!

---

### Post by Michael.Godawski on 2008-12-05
Add the following to the boot options during start up:
```
acpi=off
```
How to do this? Have a look here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

