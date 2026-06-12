---
title: "OSX 10.5 and Gutsy networking"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by hkgonra on 2008-02-19
I keep getting this error every time wo try to share files from Leopard to Ubuntu.

Name is too long or includes characters that cannot be displayed. 
I attached an image of the error message. 
Any suggestions ?

---

### Post by nixscripter on 2008-02-21
Not sure how to fix it, but it looks like something doesn't like that carriage return at the end of the fiile name (notice the quote mark is on the next line instead of being right next to the end of the name).

Silly suggestion: rename the file?

---

### Post by hkgonra on 2008-02-21
> **nixscripter said:**
> Not sure how to fix it, but it looks like something doesn't like that carriage return at the end of the fiile name (notice the quote mark is on the next line instead of being right next to the end of the name).

Silly suggestion: rename the file?


Great suggestion if it weren't for the fact that there are thousands of files. 
I run into this problem all the time with our macs. They don't have file extensions and they don't care what or how you name a file.

---

### Post by nixscripter on 2008-02-21
> **hkgonra said:**
> Great suggestion if it weren't for the fact that there are thousands of files. 
I run into this problem all the time with our macs. They don't have file extensions and they don't care what or how you name a file.

If you are willing to rename the files on the Macintosh, something I don't know what consequences it would have, you can open a terminal and run this to rename all of the files in the directory **my-dir**

```

find **my-dir** -name '*
' -print0 | perl -0ne 'print qq(bash -c \"mv ).chr(39).qq($_).chr(39).qq( ).chr(39).substr($_, 0, -2).chr(39).qq(\")' | sh

```

I'm not quite sure what else to suggest. I'm afraid don't know what the underlying cause is.  :-|

---

