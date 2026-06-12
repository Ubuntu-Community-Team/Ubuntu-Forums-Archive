---
title: "Need help with Archive manager. plz"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by LazyPony on 2010-01-17
Hey again,
I dont know anything about ubuntu but ive been getting an error whenever i try to open a DL'd file.

It keeps saying this,
Archive:  /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe
[/home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe or
          /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe.zip, and cannot find /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe.ZIP, period.



can sum1 tell me whts goin on?

---

### Post by kerry_s on 2010-01-17
looks like your trying to extract a exe file.
you do know exe is for windows, you can try running it with wine, but it might not work.

---

### Post by LazyPony on 2010-01-17
I have wine, but i dont know how to use it :[

---

### Post by Puzzled Guy on 2010-01-17
> **LazyPony said:**
> Hey again,
I dont know anything about ubuntu but ive been getting an error whenever i try to open a DL'd file.

It keeps saying this,
Archive:  /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe
[/home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, [COLOR=Red]_***or it constitutes one disk of a multi-part archive***_[/COLOR].  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe or
          /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe.zip, and cannot find /home/joe/Downloads/DAZStudio_3.0.1.144_Win32.exe.ZIP, period.



can sum1 tell me whts goin on?

I have 3 suggestions:
1. Try opening the archive with the GUI version of the archive manager and see if that works.

2. Notice the part I highlighted in red, are you sure that the archive is complete and not that you have only 1 part of a split archive?

3. Try to download that file again, yours might be corrupted. You might also try to get it from a different source.

---

### Post by LazyPony on 2010-01-17
OMG thx for the help guys! I got it working now
Have a nice night :]

Joesy

---

