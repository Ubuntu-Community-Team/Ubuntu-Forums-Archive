---
title: "Hidden Files"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
i have 3 partitions.. 
in one i have installed both windows and ubuntu(using Wubi)...

yesterday i copied some files into a folder in my second partition.. 

everything seeemed fine..everything copied into the folder in that partition.. but the folder in which these files are present is hidden now..

i may have pressed some keys accidentally, but i dont seem to know what keys i happen to press.. 

can u please help me on how to change the status of that folder to normal,from hidden?? 

i had enabled to view hidden files(ctrl+h)..

please help...

---

### Post by iaculallad on 2009-01-20
Simple, while on nautilus window, click on the file/folder and press F2 key to rename it, append the . character (dot) before the file/folder name and press Enter key.

---

### Post by diablo75 on 2009-01-20
In linux, a hidden file begins with a period (like .thisfile.doc or /.thisfolder/)

If the file is hidden, CTRL-H would have revealed it.  If it were hidden by Windows it would be shown in Linux because it doesn't begin with a period.  It's possible the key you accidentally hit was the delete key, as it does not ask you if "you are sure you want to delete x file/folder" before moving it to the trashbin.

---

### Post by lykwydchykyn on 2009-01-20
> **chethankrish said:**
> i have 3 partitions.. 
in one i have installed both windows and ubuntu(using Wubi)...

yesterday i copied some files into a folder in my second partition.. 

everything seeemed fine..everything copied into the folder in that partition.. but the folder in which these files are present is hidden now..

i may have pressed some keys accidentally, but i dont seem to know what keys i happen to press.. 

can u please help me on how to change the status of that folder to normal,from hidden?? 

i had enabled to view hidden files(ctrl+h)..

please help...

Are they hidden in Linux or in Windows?  In Linux, the only way I know of to hide a file is to add a "." at the start of its name (such as ".filename").  Windows uses file attributes to hide files, I don't believe Linux recognizes or honors those.

---

