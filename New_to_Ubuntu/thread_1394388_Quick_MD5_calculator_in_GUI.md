---
title: "Quick MD5 calculator in GUI"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by penguin007 on 2010-01-30
Most download sites provide an MD5 checksum with the downloadable files. This is used after you have downloaded the file to check that the transmission went clean. Many newcomers find it difficult / don't know how to calculate the MD5 checksum of a file. If you want to have a "right-click-on-file-and-just-do-it" solution, then copy the script below to .[FONT="Courier New"]~/.gnome2/nautilus-scripts[/FONT] and make it executable:

```
#!/bin/bash 
if [ $# = 0 ] ; then exit ; fi 
zenity --question --text "MD5 calc may take some time..." 
if [ $? -eq 0 ] ; then 
    md5=`md5sum $1` 
    zenity --info --text $md5 
fi
```

Notes:
1. Any executable script dropped into [FONT="Courier New"]**~/.gnome2/nautilus-scripts**[/FONT] will become visible upon right-click on a file in Nautilus.
2. Nautilus passes the name of the file to your script (usable as variable **$1**)
3. The line [FONT="Courier New"]**if [ $# = 0 ] ; then exit ; fi**[/FONT] above is just to check that the script received a filename (so you can use it stand-alone); it can be dropped.

---

### Post by hemimaniac on 2010-01-30
nice, ty

---

### Post by cybergus on 2010-05-18
Dead simple and invaluable... you're a gentleman and a scholar.
Thank you.
:popcorn:

---

### Post by airvzxf on 2011-10-28
Este código permite obtener el MD5 de varios archivos seleccionados.

This code allows to get the MD5 of several selected files.

==================================================
```

#!/bin/bash

if [ $# = 0 ] ; then exit ; fi

MSJ=""
TMP=""
MD5=""
FILES="$@"

for f in $FILES
do
	cadena=$(md5sum "${f}")
	buscar=".*[\xA9]"
	MD5=$(echo $cadena | egrep -oE $buscar)

	TMP="${f}\n$MD5\n"
	MSJ=${MSJ}${TMP}
done
zenity --info --text $MSJ

```

---

### Post by jasonsmith01 on 2012-07-27
> **penguin007 said:**
> 

```
#!/bin/bash 
if [ $# = 0 ] ; then exit ; fi 
zenity --question --text "MD5 calc may take some time..." 
if [ $? -eq 0 ] ; then 
    md5=`md5sum $1` 
    zenity --info --text $md5 
fi
```



When this script is used I am questioned that the md5 calc may take some time, how do I modify the script to auto answer "Yes"?

EDIT: Cancel that, I just deleted the lines that made that dialog:

```

#!/bin/bash 
if [ $# = 0 ] ; then exit ; fi 
    md5=`md5sum $1` 
    zenity --info --text $md5 
fi

```

---

### Post by wildmanne39 on 2012-07-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

