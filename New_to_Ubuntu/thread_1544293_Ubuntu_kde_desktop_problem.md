---
title: "Ubuntu kde desktop problem"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by gazz1982 on 2010-08-02
Hi I have a general problem, I log in and the desktop does not appear, I get the nice blue background with a command promt in the top left corner which is fixed in place, I can use this to open programs but I can not miminise them or move the windows.

I had this problem in koala so upgraded to lynx but still no joy :( The gnome desktop does something similar, therefore not a desktop issue, the login splash screen works fine, although I now get a: 

Warning: cannot open console kit session unable to open session. The permission of the setuid helper is not correct.

I have been working via a windows machine and ssh for a year now, I would really like my destop back, but i don't want to lose my programs I have installed or data by doing a clean install.

Many thanks

Gary

---

### Post by LowSky on 2010-08-02
have you ever logged in or used the file manager as root? If yes you probably somewhere along the line have messed up your user account's permissions by accident.

---

### Post by gazz1982 on 2010-08-02
It happened before I had chance to setup any account or sort permissions! I did an update I think.

---

### Post by MusicallyInspired on 2010-12-05
I know this is an old thread, but this just happened to me last night when upgrading from Kubuntu 10.04 to Kubuntu 10.10. When the message appears I have no keyboard or mouse control and can't do anything. I also don't want to lose everything I just set up. What can I do?

---

### Post by pcarbonell on 2011-08-10
Hi folks,

Had this problem today (1 year later than this thread) but found a solution at [http://ubuntuforums.org/showthread.php?t=1705223]("http://ubuntuforums.org/showthread.php?t=1705223")

try this to fix it:

```
sudo dpkg --configure -a
```

and rerun update commands.

Cheers

---

