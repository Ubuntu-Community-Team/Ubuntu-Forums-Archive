---
title: "what is the difference between ln and cp"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by y_garti on 2009-04-28
hi
i just start learning Linux and i learn that 
ln = Create a hard link between files. A hard link creates an exact copy of a file
cp=copy the file
what i don't get is what is the difference between those to

---

### Post by muteXe on 2009-04-28
Who told you ln creates an exact copy of the file??

---

### Post by y_garti on 2009-04-28
[http://www.testout.com/](http://www.testout.com/)

---

### Post by iaculallad on 2009-04-28
You can choose to use ln if you wanted both files updated when making changes to the other, choose cp if you just want to copy a file and leave the original file "untouched".

---

### Post by muteXe on 2009-04-28
No idea what that site is mate.
[http://linux.die.net/abs-guide/basic.html](http://linux.die.net/abs-guide/basic.html)
Bottom of the page:
> The ln creates only a reference, a pointer to the file only a few bytes in size.

---

### Post by wizard10000 on 2009-04-28
> **y_garti said:**
> hi
i just start learning Linux and i learn that 
ln = Create a hard link between files. A hard link creates an exact copy of a file
cp=copy the file
what i don't get is what is the difference between those to

I know I'm oversimplifying a whole lot, but...

You know how you create a shortcut to a file in Windows?  ln is the same thing.  cp copies a file, ln makes a shortcut to a file - in Linux we call that a link.

---

### Post by mcduck on 2009-04-28
> **y_garti said:**
> hi
i just start learning Linux and i learn that 
ln = Create a hard link between files. A hard link creates an exact copy of a file
cp=copy the file
what i don't get is what is the difference between those to

ln can create both hard and soft links.

And hard link is not the same as copy. If you copy the file, you get two files (which will both take disk space) that can be edited independently of each other.

If you hardlink the file, you get one file that shows in two different places. If you edit the file in one place the changes will appear in both locations (since it's still one and the same file).

edit:
Links in Linux are not the same as shortcuts in Windows. For example if you have a shortcut on your desktop (in windows) pointing to D:/yourfiles/, clicking the shortcut will take you to D:/yourfiles/. While in Linux if you have a link on your desktop pointing to /media/yourfiles, the link will take you to /home/yourusername/Desktop/yourfiles/. In other words, links don't move you to different location, they make the location appear where the link is.

The equivalent for shortcuts in Windows would be .desktop files in Linux.

---

### Post by Ugluk on 2009-04-28
Don't use hard links unless you know why you need to do this. Some badly written programs which use file truncation can cause data loss.

---

### Post by y_garti on 2009-04-28
OK i got the hard link
so what is the soft link ?

---

### Post by wizard10000 on 2009-04-28
> **y_garti said:**
> OK i got the hard link
so what is the soft link ?

Normally you can't hard link to a directory or to a file on another partition - a soft link will allow both of these.

---

### Post by abhiroopb on 2009-04-28
A soft link is essentially a hard link but it takes up no space. This is useful for using an off-site backup program like dropbox (getdropbox.com).

---

### Post by amac777 on 2009-04-28
A soft link (properly called a "symbolic link") is a small file that references another file or even another directory. So it's a pointer to somewhere else, but unlike a hard link, a symbolic link is stored as a small file that you can see on your hard disk by typing the "ls -l". Most programs under linux understand this little file to be a link and therefore will follow it. 

Wikipedia has lots of info:
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

Edit: This paragraph from wikipedia sums it up nicely:

> 
A symbolic link merely contains a text string that is interpreted and followed by the operating system as a path to another file or directory. It is a file on its own and can exist independently of its target. If a symbolic link is deleted, its target remains unaffected. If the target is moved, renamed or deleted, any symbolic link that used to point to it continues to exist but now points to a non-existing file. Symbolic links pointing to non-existing files are sometimes called orphaned or dangling.

---

### Post by amac777 on 2009-04-28
> **abhiroopb said:**
> A soft link is essentially a hard link but it takes up no space. This is useful for using an off-site backup program like dropbox (getdropbox.com).

What you said about soft link "takes no space" is not true. A soft link **does** take up space as well because it is a small file.

But it is true that it takes up very little space.

---

### Post by y_garti on 2009-04-28
wow thanks a lot to all of you=D>

---

