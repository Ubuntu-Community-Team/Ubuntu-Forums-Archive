---
title: "nautilus script to deflate64 zip files"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-16
I would like to know how i creat a nautilus script to zip a file or dir using 7zip deflate64?

#!/bin/bash i know is need to start the file how ever I do not know what to do from their.

I know how to use 7zip form the command line to zip a file and dir

7z a -t=zip -mm=deflate64 archive.zip file

7z a -t=zip -mm=deflate64 archive.zip file/

how do i use what i know to make the script? I just want to be able to click the file or dir in nautilus and zip it using deflate64 from 7zip.

I have p7zip and p7zip-full installed. I'm also uing the new ubuntu 9.10 (code name "Karmic Koala")

---

### Post by lance bermudez on 2009-12-16
this below works in command line but not in nautilus scripts

#!/usr/bin/bash

gui=`which zenity`
echo '7zip file name'
read  name
7z a -mm=deflate64 archive.zip $name
exit 0

how do i get the gui interface for nautilus scripts?

---

### Post by lance bermudez on 2009-12-16
remove the line

gui=`which zenity`

and it works. when i posted it i did not think that was in the line.

---

### Post by lance bermudez on 2009-12-17
I have my script in the nautilus scripts part of gome however when i click on it the script does nothing. I have to use it from the command line. by using zenity i mean a box will pop up to take the name of the file or dir i want ziped (the read name from above) and insert the name into the $name (the 7z a -mm=deflate64 archive.zip $name from above) I was told by youtube that this could be done but the guy in the video did not explain it on my very low level to get what he was taling about.

---

### Post by lance bermudez on 2009-12-18
kaibob

told me

When using a Nautilus script, the name of the file or files to be processed is obtained by way of the Nautilus file manager. Thus, for example, you would open Nautilus, right click on the file or files to be archived, scroll down to "scripts", and then select the name of the script.

The following is the Nautilus-script equivalent of the shell script included in your original post. $@ is the file name or names passed from Nautilus to the script. I used the zip utility, because its the one I'm familiar with, and because it's already installed on my computer and allowed me to test the script.

Code:

#!/bin/bash

zip -r archive.zip "$@"

As previously mentioned, this script has to be placed in the nautilus script directory. Also, this nautilus script should work to archive a directory, although you have to select the directory to be archived in the right pane of Nautilus.

---

### Post by lance bermudez on 2009-12-19
I have

#!/bin/bash

7z a -mm=deflate64 archive.zip "$@" | zenity --progress --text="zipping" --pulsate --auto-kill

and it works if you dont mind the progress bar not moving. I have enven tried the --percentage=INT with INT= an number and the bar still does not move. I&#7743; also zipping big files becuse the bar just set their for a little while with out moving but when it is done it is all full. it is blank wait all full no moving and their is time for it to have moved. but it does not move.

---

