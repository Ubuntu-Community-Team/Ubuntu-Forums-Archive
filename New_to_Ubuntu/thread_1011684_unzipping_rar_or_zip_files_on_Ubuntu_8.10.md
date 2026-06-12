---
title: "unzipping rar or zip files on Ubuntu 8.10"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-15
i've downloaded a video which is in either rar or zip files with extensions like this .r00 .r01 .r02 .r03 etc 

how can i uncompress these? i've tried the default archive manager but it wouldn't recognize it...

---

### Post by manuleka on 2008-12-15
i've downloaded a video which is in either rar or zip files with extensions like this .r00 .r01 .r02 .r03 etc 

how can i uncompress these? i've tried the default archive manager but it wouldn't recognize it...

---

### Post by kcy29581 on 2008-12-15
Install "unrar", then try to extract the .rar file.

---

### Post by Existentialist on 2008-12-15
You will want to install the unrar package.
From terminal:

>sudo apt-get install unrar

Afterward, archive manager will be able to decompress .rar files.

---

### Post by Keen101 on 2008-12-15
I've used p7zip in the past. I think in addition to installing p7zip you will also need a GUI for it too. get the gui here [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

```
sudo aptitude install p7zip-full p7zip-rar
```

---

### Post by Keen101 on 2008-12-15
I've used p7zip successfully in the past. I think in addition to installing p7zip you will also need a GUI for it too. get the gui here [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

```
sudo aptitude install p7zip-full p7zip-rar
```



...also try not to double post...

---

### Post by bapoumba on 2008-12-15
Threads merged.

---

### Post by manuleka on 2008-12-17
sudo apt-get install unrar

worked thanks :)

---

### Post by ahmed.php on 2009-03-22
Thanks it's working

---

### Post by Joergen Marmalade on 2009-03-22
I feel it's time to make it official: I LOVE YOU GUYS!

---

