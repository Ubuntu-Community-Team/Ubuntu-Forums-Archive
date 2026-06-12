---
title: "opening *.ini files"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by msidhard on 2009-03-03
How to open *.inf in ubuntu 8.10

---

### Post by cb951303 on 2009-03-03
*.ini or *.inf?

both are text files anyway. double click them. or try opening with gedit.

---

### Post by msidhard on 2009-03-03
It says text encoding failed.

---

### Post by trlkly on 2009-03-03
The file may be corrupted. Care to post it?

---

### Post by albandy on 2009-03-03
type:

file filename.inf

to know what kind of file you're trying to open

---

### Post by linux_tech on 2009-03-03
gedit, nano, any text editor should work with them

---

### Post by mikechant on 2009-03-03
If the file won't open with a standard text editor due to unrecognized coding (possibly corruption or just some weird characters), try installing the hex editor 'ghex'. That should open it regardless and display all the characters that can be displayed.

---

### Post by albandy on 2009-03-03
> **mikechant said:**
> If the file won't open with a standard text editor due to unrecognized coding (possibly corruption or just some weird characters), try installing the hex editor 'ghex'. That should open it regardless and display all the characters that can be displayed.

or you can type strings filename to dump all text lines

---

### Post by Mark Phelps on 2009-03-03
> **msidhard said:**
> How to open *.inf in ubuntu 8.10

.inf files in MS Windows are typically used to install device drivers.  Is that what you're trying to do?  You should be able to right-click on any of these files (.ini or .inf) and select open with and enter "nano" or "gedit" ( in Gnome) or "kate" (in KDE).

---

