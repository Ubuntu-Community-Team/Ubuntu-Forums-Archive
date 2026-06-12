---
title: "How to search for a particular file types in my system"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-07
I wanted to search my system completely for a particular file type like [COLOR=red]**jpg [COLOR=black]([COLOR=blue]including hidden files[/COLOR])[/COLOR]**[/COLOR][COLOR=black]and i wanted to copy all those files to a particular folder..How to write a bash script for this.?[/COLOR]

---

### Post by nothingspecial on 2010-04-07
Supposing you want to copy them to a folder called photos in your home directory

```
find / -name '*.jpg' -exec cp '{}' ~/photos \;
```

That will search the entire file system and copy any jpgs (including any icon jpgs or album art you have, so watch out.

---

### Post by Azrael3000 on 2010-04-07
in case you just want your home directory use a ~ instead of the first / since you probably will have stored all your photos somewhere in your home folder.

---

### Post by nothingspecial on 2010-04-07
Oh yeah, and if you use -iname instead of -name that will get any .Jpg or .JPG - or .JpG etc

---

### Post by karthick87 on 2010-04-08
Thanks a lot,but will it search hidden files?

---

### Post by Azrael3000 on 2010-04-08
yes it will. Hidden files are only specified by a . in front of their name. since you are only looking for files ending with *.jpg it doesn't matter if there's a point up front.

---

### Post by undecim on 2010-04-08
If you have any jpgs already in your photos directory, that command will give you errors that look like
```
cp: `filename.jpg' and `~/photos/filename.jpg~' are the same file
```
but you can safely ignore those. It's just finding files that are already in your photos directory.

---

### Post by karthick87 on 2010-04-11
> **nothingspecial said:**
> Supposing you want to copy them to a folder called photos in your home directory

```
find / -name '*.jpg' -exec cp '{}' ~/photos \;
```That will search the entire file system and copy any jpgs (including any icon jpgs or album art you have, so watch out.


I tried this,but its not copying any files to my Home folder.

---

### Post by Didius Falco on 2010-04-11
is it giving any kind of message at all? Did you first create the photo directory under home/yourusername?

---

### Post by karthick87 on 2010-04-11
It s not saving the files to my directory.Already i have a directory named Photos in my home folder.

---

### Post by kaibob on 2010-04-11
> **getyourkarthick said:**
> It s not saving the files to my directory.Already i have a directory named Photos in my home folder.

The suggested find command copies to the ~/photos directory not to the ~/Photos directory.

---

### Post by karthick87 on 2010-04-11
Sorry just now i have noticed,and now its working..Thanks dude.!

---

### Post by nothingspecial on 2010-04-11
Remember, linux is case sensetive. P and p are different.

---

