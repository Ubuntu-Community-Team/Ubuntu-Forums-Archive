---
title: "how to locate a file ?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by usman idrees on 2009-01-06
How can I search a file if I donot know the location of file ?

---

### Post by nothingspecial on 2009-01-06
> **usman idrees said:**
> How can I search a file if I donot know the location of file ?

```
locate name_of_or_part_of_file
```

---

### Post by Michael.Godawski on 2009-01-06
hi, 
there are some commands you can use:

```
locate
find
whereis
```

and then the filename.

---

### Post by zvacet on 2009-01-06
```
sudo find / -name file_name
```

---

### Post by andrew.46 on 2009-01-06
Hi,

If you have absolutely no idea where the file is you can search the entire computer as follows:

```
$ sudo find / -iname '[COLOR="Red"]**file_I_want**[/COLOR]'
```

and this will perform a case-insensitive search of the entire computer for the file called file_I_want. Almost limitless possibililties with the 'find' command :-).

Andrew

**Edit:** Doh!!! Beaten by zvacet!

---

### Post by thegreenblob on 2009-01-06
You can also use the GUI to do this, if you don't want to use the terminal. :)

Places --> Search for Files...

---

### Post by ajgreeny on 2009-01-06
If you are not sure of the complete file name use the wildcard * at the start and end of the part-filename you do know, eg ```
find -iname *chris*
``` will find any files with that **chris** string in

---

### Post by MrWES on 2009-01-06
sudo updatedb <--- first

locate SOMETHING

if your looking for a path for an executable try

which firefox

---

