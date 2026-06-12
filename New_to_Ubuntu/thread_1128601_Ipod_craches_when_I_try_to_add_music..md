---
title: "Ipod craches when I try to add music."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by LostMagix on 2009-04-17
I try to add files with rhythmbox, it is recognized but is constantly remounting the ipod. I can remove all the files i want but when i try to add the thing crashes. 

Same with gtkpod, songbird and hipo


I have been searching the forums but there are so many problems people have with ipods its hard to find one that helps

---

### Post by Ericyzfr1 on 2009-04-17
What generation of ipod do you have? Did you have any issues before?

---

### Post by LostMagix on 2009-04-17
4gen nano

Bus 001 Device 100: ID 05ac:1263 Apple, Inc.

had no big problems in 8.10, it would have its hang up once in a while but it normally worked fine, in songbird at least, [here]("http://ubuntuforums.org/showthread.php?t=1051474") is the last thread on it.

---

### Post by LostMagix on 2009-04-17
I just logged onto my old 8.10 partition and its not working there ether.

any know a way to format a ipod under linux?

---

### Post by LostMagix on 2009-04-18
*bump

---

### Post by LostMagix on 2009-04-19
*bump

---

### Post by LostMagix on 2009-04-19
I reformated the divise on a windows box, it seems to be working fine now.

---

### Post by LostMagix on 2009-04-19
Wll i guess not, I can only add one file per then it remounts.

---

### Post by LostMagix on 2009-04-19
This error keeps coming up now:


Unable to mount GREENAPPLE (the Ipod)

DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

---

### Post by LostMagix on 2009-04-19
[IMG]http://i105.photobucket.com/albums/m231/crazy_monkey_ninja/Screenshot-10.png[/IMG]

I keep getting this window from rythmebox which crashes after i enter the ipod name and press initialize.

---

### Post by starcannon on 2009-04-19
My Dad's iPod was behaving like this as well. He discovered that the iPod was not liking special characters in song names, some it would tolerate, others it would not... This is second hand after hearing him talk about it on the phone. Perhaps try a naming convention that requires no special characters.

He also noted that one of the utilities he was using to rip songs was not setting the file type correctly. Sure each song would have .mp3 at the end, but in some cases it was being seen as part of the name and not a file type, I can't remember how he figured that out, but once he handled the naming convention and reset the filetype by right-click renaming, he seems to have no more iPod crashes.

GL

---

