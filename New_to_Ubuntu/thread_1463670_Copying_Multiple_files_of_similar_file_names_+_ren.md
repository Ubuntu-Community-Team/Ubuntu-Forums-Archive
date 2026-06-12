---
title: "Copying Multiple files of similar file names + renaming"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by Sapphirrix on 2010-04-27
Greetings all, 

by the title of my post you can see that I'm in need of some help with copying multiple files with similar names (i.e. Image 001.jpg, Image 002.jpg) and renaming them in the process

I've been told that this is easiest to do using CLI, however I've got rather limited knowledge and I have trouble understanding the manual and help entries for the commands that I've looked at.

In short I'd like some help putting together a command that will allow me to copy a series of files from my external hard-drive to my main hard-drive, whilst renaming them to something more appropriate. 

unfortunately, I also have a catch in that the file names go something like this:
Image001.jpg
Image003.jpg
Image004.jpg
Image006.png
Image007.jpg
Image010.jpg
Image011.jpg

all the way into the 70s with quite a few missing in the mid-section... 

Thanks for taking the time to have a look, and I hope to learn more about Ubuntu, and Linux in general.
 - Sapph

---

### Post by ubunterooster on 2010-04-27
Command line is _not_ easiest. It _may_ be fastest, _if_ you know how to do it. Generally, you don't need to do it anyway that you don't like.

---

### Post by kaibob on 2010-04-27
The command line is useful in renaming a series of files if there is some pattern or underlying data (e.g. exif) that can be used to ascertain the new file names. That appears not to be the case with your files. So, if I understand your situation correctly, I think you have to manually rename the files.

As an aside, you probably should explain what you mean when you state that you want to rename the files "to something more appropriate."

---

### Post by eriktheblu on 2010-04-27
The syntax would be
```
cp /source/filename.jpg /destination/newfilename.jpg
```

Since my command line knowledge is still limited, here's what I'd do for mass copying and renaming:

First, export the file list
```
ls /path/to/source/files/*.* > ~/Desktop/list.txt
```
Copy and paste the results (from list.txt now on the desktop) into a spreadsheet (like OO.o Calc)

Use a spreadsheet formula to create a command
```
="cp /source/" & A1 & " /destination/" & right(A1,7)
```
The result if A1 is Image001.jpg would be
```
cp /source/Image001.jpg /destination/001.jpg
```

Transpose this down until all files have a respective formula, copy and paste into the terminal.

Alternatively, you can set up a sort of autonumber (if the file names are all out of whack and you just want them enumerated:
Column A is the original file name.
Set Cell B1 to 1, and B2 to =B1+1. Transpose down.
Set column C to:
```
="cp /source/" & A1 & " /destination/" & B1 & right(A1,4)
```

Ugly, and probably wrong, but it works.

---

