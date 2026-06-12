---
title: "DVD Mounting"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-06-25
[IMG]file:///home/moeb59/Desktop/Screenshot.png[/IMG]Hi,

I am a newbie running 9.04 32bit and was wondering what the error message in the terminal window (attached screenshot) means when I try to mount the dvd udf in order to run the application x-plane which is my favorite flight simulator and requires that the dvd be in the drive when i run it.

thanks

---

### Post by brettg on 2009-06-25
It says that the filesystem you are trying to mount (UDF) does not match the actual cd. 

Try mounting it without the "-t udf" flag and see if it works.

---

