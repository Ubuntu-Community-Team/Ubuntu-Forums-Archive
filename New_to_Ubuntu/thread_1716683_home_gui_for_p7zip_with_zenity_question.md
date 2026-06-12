---
title: "home gui for p7zip with zenity question"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-28
below is my bash script and it is not fancy. It will use 7zip with deflate64 to make zip files. My question is does any body know how to show the % and/or file name being zipped in the --text="zipping" box? also how do you get it to close when it is down? I do not use the archive gui because i like the deflate64 makes smaller zipped files then 7z

#!/bin/bash
zenity --info --text "Choose source file to 7zip using deflate64 /dir in box or click file";
szSavePathfrom=$(zenity --file-selection --multiple --save --confirm-overwrite);
zenity --info --text "Choose file destination";
szSavePathto=$(zenity --file-selection --multiple --save --confirm-overwrite);
7z a -mm=deflate64 $szSavePathto.zip $szSavePathfrom | zenity --progress --text="zipping" --percentage=1 --auto-kill

---

