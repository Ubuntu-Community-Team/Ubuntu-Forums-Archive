---
title: "DVD Burning/DVD conversion software questions."
date: 2009-03-22
forum: New to Ubuntu
---

### Post by arce on 2009-03-22
I currently Ubuntu installed on my laptop. This has been a 3 day trial run so far. I would like to install it on my desktop but I would like suggestions on what projects I would need to do what I currently can do with Windows XP

Need to be able to create ISO's
Need to burn to multiple DVD drives.
Adjust burn speeds
Support for DVD5 DVD9
Copy DVD's
Burn CD's/Music and data

Cut to the chase, a Nero for Unbuntu.



I currently use XtoDVD and WinAVI 9.0 for movie conversions. This allows me to add menus and convert between multiple movie formats. I bascially convert mpg4,avi,divx and others and convert to DVD format. I would have to be able to do this. 



I also I need to be able to join AVI's

I currently have k9copy installed.

---

### Post by James_Lochhead on 2009-03-22
Try K3b, it is quite powerful.

---

### Post by men28 on 2009-03-22
In order to burn CD/DVD you have "Brasero Disk Burning".

For different formats conversion use ffmpeg. In order to install it type in terminal:
```
sudo apt-get install ffmpeg
```
For proprietary formats conversion activate "medibuntu" repository.
There are a lot of examples in the internet about how to use ffmpeg.

About ISO images try reading this thread:
[http://ubuntuforums.org/showthread.php?t=6509]("http://ubuntuforums.org/showthread.php?t=6509")

The most powerful tool in Linux is Terminal and command line.

---

