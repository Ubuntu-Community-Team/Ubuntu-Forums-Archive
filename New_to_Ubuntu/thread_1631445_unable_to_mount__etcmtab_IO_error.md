---
title: "unable to mount : /etc/mtab I/O error"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Bhushi on 2010-11-26
All,

I am running Ubuntu 10.04 using persistent 8 GB USB drive. Everything was working perfectly till I installed a windows emulator (WINE) on my system. 

After the install every time I insert a USB pendrive or a USB external Hard drive. It gives the following exception 

> Error mounting: mount exited with exit code 16: mount: can't open /etc/mtab for writing: Input/output errorI checked the file through terminal. 

> 
ls: cannot access mtab: Input/output error
-?????????  ? ?       ?           ?                ? mtab
I have seen many people facing this problem, but haven't got any resolution to this.
Can someone please help ?

---

### Post by mikewhatever on 2010-11-28
Could be a file system error. What happened when you tried accessing mtab? Can you post the output including the command used.

---

### Post by Bhushi on 2010-12-01
My previous message contains the output of ls command.
Whenever I try to mount a USB Stick this message comes up...

---

### Post by ppv on 2010-12-01
It may not be wine that is causing it...

Did you have a forced shutdown or a sudden pull of a usb drive...

---

### Post by Bhushi on 2010-12-01
No that didn't happen...

Now as soon as I mount the USB, it gets mounted with error. Then whenever I unmount it it throws exception and the desktop icon also doesn't disappear, as it used to earlier..

---

