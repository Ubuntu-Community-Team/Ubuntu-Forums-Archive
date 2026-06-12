---
title: "ABCDE filename help"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by natpagle on 2010-01-12
Just wondering if anyone could help with setting up my filenames and folder structure on ABCDE.

I'd like my settings to output like this in my current folder:

Artist/Album/01 - Track Title.mp3

Folder for Artist, only Artist's name. Under that, folder for Album, only Album's name. Then a leading 0 before tracks that are single digit. No leading 0 for 10. A space after track #, a dash, another space, then Track Title with spaces instead of _Underscores_. 

Here is my current set up, let me know if this is possible

```
#mungefilename ()
#{
#	echo "$@" | sed s,:,\ -,g | tr / \ __ | tr -d \'\"\?\[:cntrl:\]
#}

```
```

#OUTPUTFORMAT='${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

```

---

### Post by bcn17 on 2010-01-12
Yes, it is possible. 

This site helped me tweak abcde pretty nicely FIY.

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

And I would try this- although no gaurantees. Just play arround with it.

OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'

For the underscores and leading zeros refer to the site above, or the man page.
>>man abcde

edit:And if you didn't know, the "#" is a comment mark that tells abcde to NOT read the line. So if a "#" is in front of a line its as if the line wasn't their and abcde reverts to defaults. So to make it work you have to delete the # and change the line how you like. GL!

---

### Post by natpagle on 2010-01-12
That worked flawlessly. I had read though those man pages but I still didn't understand the symbols and how they worked together. Thanks so much!

---

### Post by bcn17 on 2010-01-15
Glad to help.

And just so you know. You can make the save path anything using ARTISTFILE, ALBUMFILE, TRACKNUM, or TRACKFILE as long as you put a "$" in front and enclose it with {}. The "/" means make what is after a folder name. The spaces and dashes are just interpeted as text because they are not in the variable ${}.

---

### Post by natpagle on 2010-01-16
Cool, thanks for the tips!

---

