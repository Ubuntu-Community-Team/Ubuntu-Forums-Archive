---
title: "finding and deleting corrupt mp3 files"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Barky on 2009-05-22
hey all,

I've got a good amount of mp3 files floating around my hard drive that have gotten corrupted in one way or another. Some are duplicates of other mp3's, some are just corrupt by themselves. They all share the same attribute though, they will play for about 4-5 secs and then it is as if the song is over. Is there a way to "search and destroy" these kinds of files using a script or program? Thanks

---

### Post by wpshooter on 2009-05-22
Seems to me that the is a "find" function on one of the menus in Ubuntu.  Why don't you just use that and search the drive for file with mp3 in the name ?

---

### Post by nandemonai on 2009-05-22
Best thing you're going to be able to do I think is list all mp3s on the system.

I don't know of anyway for a program to know what's legit and what's corrupted without trying something tricky like play length, which is bound to screw up and delete good files.

Set aside a day to manually sift through them would be my suggestion ;)

---

### Post by andrew.46 on 2009-05-22
Hi Barky,

> **Barky said:**
> I've got a good amount of mp3 files floating around my hard drive that have gotten corrupted in one way or another. Some are duplicates of other mp3's, some are just corrupt by themselves. They all share the same attribute though, they will play for about 4-5 secs and then it is as if the song is over. Is there a way to "search and destroy" these kinds of files using a script or program? Thanks

Well what about a "search and size" for starters:

```
sudo find / -iname '*.mp3' -type f -exec du -h '{}' \;
```

This will show the *size* of all mp3s on your system. Once you are happy to delete (for example) mp3s that are smaller than 20 kilobytes each you could use something like:

```
sudo find / -iname '*.mp3' -type f -size -20k -ok rm {} \;
```

This will search for all of the mp3s on your system that are less than 20 kilobytes in size and then ask you one by one if you want to delete them. There are of course several different ways to do this :-).

Andrew

---

