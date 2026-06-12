---
title: "Using CP command"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-05-25
I'm trying to copy a file to my usb drive. I can't figure out what my usb drive is called in the command line. This is what I have tryed.

cp /home/brian/videos/across/across.avi /media/disk

brian@brian-desktop:~$ cp /home/brian/videos/across/across.avi /media/disk
cp: cannot stat `/home/brian/videos/across/across.avi': No such file or directory

I tried taking out the first /'s and that didn't work. Just to check the directory I did cd /home/brian/across.avi and many other combos still not finding the file.

---

### Post by lisati on 2010-05-25
Try:
```
cp /home/brian/videos/movie.avi /media/disk/
```

---

### Post by baddog144 on 2010-05-25
You're missing a / before media and home, I think. It should read
```

cp /home/brian/videos/movie.avi /media/disk

```

Have a look for something that explains the structure of the linux filesystem, it'll come in handy :)
EDIT: Beaten to it!

---

### Post by Drenriza on 2010-05-25
```
cp home/brian/videos/movie.avi media/disk
```
 
This cant work because.
 
 
```
cp home/brian/videos/movie.avi 
```
This section to work you need to stand in the /home or home path, because you refear to this as an relative path. 
 
but here
```
media/disk
```
you also refear to this as an relative path, and since you cant stand in 2 paths at the same time. You cannot copy the .avi file.
 
you can do 2 things.
```
cp /home/brian/videos/movie.avi /media/disk
```
or
stand in /home path, you do this by changing to it first. ```
cd /home
```
and then
```
cp brian/videos/movie.avi /media/disk
```
 
EDIT:
You can probably also stand in the /media path and then copy the file from their.
```
cp /home/brian/videos/movie.avi /disk
```
 
EDIT2: Edited my Sloppy mistake.

---

### Post by baddog144 on 2010-05-25
> **Drenriza said:**
> ```
cp home/brian/videos/movie.avi media/disk
```
 
This cant work because.
 
 
```
cp home/brian/videos/movie.avi 
```
This section to work you need to stand in the /home or home path, because you refear to this as an relative path. 
 
but here
```
media/disk
```
you also refear to this as an relative path, and since you cant stand in 2 paths at the same time. You cannot copy the .avi file.
[B]
you can do 2 things.
```
cp /home/brian/videos/movie.avi /media/disk
```
or
stand in /home path, you do this by changing to it first. ```
cd /home
```
and then
```
cp home/brian/videos/movie.avi /media/disk
```
[/B]

Just note: that won't work, if he's already in home, there's not another home/ directory under that. It should be cp brian/videos/movie.avi :P

---

### Post by v1ad on 2010-05-25
cp home/brian/videos/movie.avi /media/disk

this will work.

---

### Post by Drenriza on 2010-05-25
Ye ofc. I was sleeping their.
Edited my post.

---

### Post by baddog144 on 2010-05-25
> **v1ad said:**
> cp home/brian/videos/movie.avi /media/disk

this will work.

Er. Only if you change home/ to /home/
:|

---

### Post by Failboat88 on 2010-05-25
Wow, I feel dumb. It's case sensitive.

---

### Post by lisati on 2010-05-25
Is it just me, or are we going round in circles, add / here, drop it there? :confused:
I hope the OP isn't getting too confused.

---

### Post by baddog144 on 2010-05-25
It doesn't matter, because it turned out he had them there anyway. And I still don't know if he found the solution or not.

---

### Post by Failboat88 on 2010-05-25
I was just trying this as a work around to the mysterious deteriorating file transfer speed when transferring files with drag and drop.  

It failed =(

Still gets super slow after about 150mb. Slow as in < 500kb/s.

I did find the solution btw. It worked when I used the right case.

---

### Post by sbergman on 2010-05-25
> **Failboat88 said:**
> I did find the solution btw. It worked when I used the right case.

Good! cos I was really confused... a lot of those above commands looked okay to me tho' apparently they werent. Funny how it turned out to be a filename problem (case-sensitivity) in the end.

---

