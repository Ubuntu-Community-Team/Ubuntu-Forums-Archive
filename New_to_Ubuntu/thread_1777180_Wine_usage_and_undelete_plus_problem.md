---
title: "Wine usage and undelete plus problem"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-06-07
Background: I have an SD card I am trying to recover lost files on. After a Google search it looks like UNDELETE PLUS is highly suggested but it's a Windows application.
 
I installed and configured wine (boy does that take a while!) and successfully installed UNDELETE PLUS. It opened automatically and for the first time I was so happy something just worked like I wanted it to!
 
I tried to do a scan and it said I can't scan the drives because I need administrator rights.
 
I thought for a moment and said "DUH! Let's throw sudo at it and see what happens."

So I tried.. sudo wine /path/file.exe and it prompted for a password. Then it slapped me in the face saying "you aren't the owner of this" or something very close.  If sudo is root, how is root not the owner of either WINE, the directory it made or the program I am trying to execute with admin?
 
Anyone familiar with this program or WINE know what I have to do? Or anyone know of a better program that's not extraordinarily difficult to work on Ubuntu to recover lost files on an SD card?

---

### Post by mcduck on 2011-06-07
I doubt the program would have a slightest clue about the permissions and devices on your system, it being a Windows application. While Wine is fine for running some programs and desktop apps, it definitely isn't suitable for any lower-level stuff.

I would recommend you give PhotoRec a try, it's natively available for Linux and often recommended as a great file recovery tool.

[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

edit: PhotoRec should be available in Ubuntu's repositories, I believe it comes in the same package with TestDisk.

---

### Post by perlgoodies on 2011-06-07
> **mcduck said:**
> I doubt the program would have a slightest clue about the permissions and devices on your system, it being a Windows application. While Wine is fine for running some programs and desktop apps, it definitely isn't suitable for any lower-level stuff.
 
I would recommend you give PhotoRec a try, it's natively available for Linux and often recommended as a great file recovery tool.
 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
 
edit: PhotoRec should be available in Ubuntu's repositories, I believe it comes in the same package with TestDisk.
 
Thank you for the recommendation about PhotoRec. I used that to recover a partition on a separate computer and it mucked it up so bad the data is pretty much useless. Something about it renaming all the files and storing them in unrelated folders make it extremely difficult to make the data usable again. It sure recovered a lot of files for me but since most of my data were images, scripts or databases it really ruined my chances of recovering anything useful.
 
I figured the problem was it was a Win application and it doesn't know better.

---

### Post by mcduck on 2011-06-07
Yeah, photorec tends to do that. Bit of a command-line magick, though, and you can have the files sorted out and renamed by filetype. You'd still have to fix the actual file names, but at least getting the file name extensions right should make sorting out the files more tolerable)

(the *file* command detects a file's  type based on contents, not name, so a simple script based on that should work for renaming and sorting any files that PhotoRec managed to recover completely.)

---

