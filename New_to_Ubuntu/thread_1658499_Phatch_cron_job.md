---
title: "Phatch cron job"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by jmumby on 2011-01-02
I'm trying to resize a folder of images using phatch and command line. I have created a action list that resizes and saves the images. I use the following to run it.

```

 phatch -cv resize.phatch  "/path/to/folder"

```Is it possible to specify only jpg's as at the moment I have AVI in the same folder and it is hanging on that. I want to run this as a cron job as well so it would be helpful to specify a source and destination folder. 

Chrs

---

### Post by pqwoerituytrueiwoq on 2011-01-02
you can try useing *.jpg
cause i know you can use * when extracting compressed files ex:
tar xvf start_of_file*.tar

---

### Post by jmumby on 2011-01-02
I have tried 

```

phatch -cv reszie.phatch  "/path/to/pictures/" *.jpg

and 

phatch -cv reszie.phatch "/home/username/"  "/path/to/pictures/"*.jpg

and 

phatch -cv reszie.phatch "/home/username/*.jpg"  "/path/to/pictures/"



```but I get Error: Sorry, "/home/username/*.jpg" is not a valid path.

---

### Post by pqwoerituytrueiwoq on 2011-01-02
try 
```
/path/to/pictures/*.jpg
```no quotes
if there are spaces in the path do this
like
```
/home/me/"my folder"/*.jpg
```

---

### Post by jmumby on 2011-01-02
Thats it! Thanks very much

---

