---
title: "[B]how to make files hidden in ubuntu 8.04 [/B]"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2008-12-15
hi techies...


i just wanna know that how we can make the desired files and folders hidden in ubuntu8.04 ... just like we do this in windows...

is there any procedure to hide the files and folders in ubuntu 8.04


thanking u in advance...

---

### Post by adobrakic on 2008-12-15
I just rename the file i want to hide with a '.' in front of it.

so for example, file01 would be .file01

and i press ctrl+h in that folder to see it.

---

### Post by Tatty on 2008-12-15
Generally files are hidden if they start with a '.'

so ~/.hidden  will be a hidden file in my home folder called .hidden

**EDIT:** Beaten by a faster mouse, lol.

---

### Post by drs305 on 2008-12-15
To hide them in nautilus, there are at least two methods. Both require that nautilus's View, Show Hidden Files (CTRL+H) is unchecked. One requires renaming the file, the other doesn't.

1. Rename the file or folder to begin with a period ( . ). e.g rename *myfile* to *.myfile*

2. The second way is to create a file called ".hidden"  Open the file and add the filenames of any file or folder in the same directory which you want hidden. Save the file and close. Any files listed in the file ".hidden" will not be displayed.

---

### Post by shreyanshjain8 on 2008-12-15
thank youuuuuuuuuuuuuuu very much techies.....




thanks alot......

it worked....

---

