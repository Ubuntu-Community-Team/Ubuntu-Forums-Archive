---
title: "newbie CHMOD help"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by jakeford18 on 2009-08-30
I was finally able to change the owner and group (ROOT) of an enormous media back up, back to me
I'm not sure why I backed these files up the owner was set to root, since I don't believe they were originally. This is the terminal output showing the file access attributes

me@me:/$ ls -l 01THG
total 16
drwxrwx---  8 me me 4096 2009-08-30 01:54 movies
drwxrwx--- 16 me me 4096 2009-08-30 01:54 music
drwxrwx---  3 me me 4096 2009-08-22 07:09 music videos
drwxrwx--- 17 me me 4096 2009-08-22 07:34 TV Shows

So while I have permissions over the folder, I need the correct syntax to make the file access read and write but not executable. Any help would be greatly appreciated, and like others before, the gksu nautilus didn't work.

---

### Post by R_W322 on 2009-08-30
Are you just trying to delete the files?

RYAN.WDZIECZNY

---

### Post by tgeer43 on 2009-08-30
```
chmod 666 *filename*

```Will give everyone read/write access and remove execute permission for everyone.

tgeer

---

### Post by gsocker on 2009-08-30
> ```
drwxrwx---  8 me me 4096 2009-08-30 01:54 movies
```This is a directory - note the "d" as the first character from the ls listing.
The directory itself must have execute permission set, otherwise you will not be able to view the contents. 
For the files within the directories, the chmod command posted earlier will work fine.

---

### Post by alhaines on 2009-08-30
There is a nice page for newbies at [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
it explains most commands in a simple and clear way.

Only two things are infinite, the universe and human stupidity, and I am not sure about the former. - Albert Einstein-

---

