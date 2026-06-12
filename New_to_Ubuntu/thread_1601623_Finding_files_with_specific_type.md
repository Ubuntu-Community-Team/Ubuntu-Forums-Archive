---
title: "Finding files with specific type"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-10-20
I'm looking for a method to find a specific type of file among many other files, from the terminal that is.

Example I have my photo album that contain loads of files, most of them are jpg or png, but there are some bmp files. To make it trickier do these bmp files labled as .jpg. 

I looked at 'find' but it looks like you can't specify a specific type only directory or file, not what kind of file.

---

### Post by HermanAB on 2010-10-20
```
$ find /where/ever -name *jpg
```

---

### Post by SpinningAround on 2010-10-20
> **HermanAB said:**
> ```
$ find /where/ever -name *jpg
```

Thanks for answering but it don't solve the problem since I only want to get files that are of the type .bmp, they might be named as .jpg files even if they aren't. The 'file' command might be something but I don't know how to use it so it only finds the .bmp files.

---

### Post by mick8985 on 2010-10-20
If all the images are in the same folder you can get a list of all their mime types by placing a wildcard in the path like so:

```
mimetype ~/Pictures/*
```

---

### Post by JKyleOKC on 2010-10-20
If you know which directory they are in, just "cd" to that directory and issue the command "file *|grep bitmap" to get them listed. You may want to redirect the output to a text file if there are a lot of them...

---

### Post by marshmallow1304 on 2010-10-20
This isn't perfect, but it should give you a start.
Go to the root directory of the images

```
find ./ -name *.jpg > tempfile
file -f tempfile | grep bitmap
```

---

