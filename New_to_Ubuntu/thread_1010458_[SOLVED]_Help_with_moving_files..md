---
title: "[SOLVED] Help with moving files."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by dryancu on 2008-12-13
Alright guys and gals, I have an enormous directory copied over from the old Windows OS. It is full of .m4p's and m4a's and mp3's all organized in sub-directories containing names with spaces. In an effort to render itunes obsolete on my computer I want to rip and re-rip all the .m4p's. To make this easier I had hoped to move each one of these .m4p files into the same directory that I could burn from. Instead of dragging and dropping each file individually I hoped to use the versatile and robust terminal to do all that tedious stuff for me. I have come up with this:

~$ cp `find /home/user/Music -name '*.m4p'` ~/targetdirectory

Which obviously has failed miserably. I get this error for each file:

cp: cannot stat 'somefile': No such file or directory

My assumption is that the command cannot find the directories located behind names with spaces. I think I need to implement the -print0 somewhere within. Could someone point me in the right direction? Or enlighten me by showing me some previously overlooked trick that will save me from any further humbling? Thanks!

---

### Post by kaibob on 2008-12-13
The general format for what you want to do should be:

```
find /source/directory -iname '*.png' -type f -exec cp '{}' /destination/directory ';'
```

Just change the source and destination directories and the file extension. Spaces in file names should not be an issue.

---

### Post by dryancu on 2008-12-13
Great, worked exactly how I wanted it to. Thanks for the quick response!

---

### Post by newbee70 on 2008-12-13
> **kaibob said:**
> The general format for what you want to do should be:

```
find /source/directory -iname '*.png' -type f -exec cp '{}' /destination/directory ';'
```

Just change the source and destination directories and the file extension. Spaces in file names should not be an issue.


Where were you for my help with recursion?  this helped me solve my problem.

thanks.

---

