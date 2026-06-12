---
title: "Gedit Executing Text File"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by ajdrew06 on 2009-09-23
I use text files to make notes for myself.

When I open a text file, I am tired of it asking if I want to execute the text file or display it. Now, I have found that by right clicking, going to Permissions, I can uncheck the option to have it execute.  However, I have to do this file by file.  

1. Is there any way to have gedit save files with this option unchecked by default?  

2. I have my files backed up on a usb external harddrive, and I CANNOT uncheck this option.  How do I go about unchecking the option on these files?

Any help would be appreciated.

---

### Post by 3rdalbum on 2009-09-23
In gconf-editor, you can change the key:

/apps/nautilus/preferences/executable_text_activation

to "display". This will affect all text files with executable permission.

---

### Post by mcduck on 2009-09-23
..or change the same setting in Nautilus preferences. ;)

---

### Post by ajdrew06 on 2009-09-23
Thank you!  I knew it had to be something simple haha.

---

