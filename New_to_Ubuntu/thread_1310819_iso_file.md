---
title: "iso file"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Drenriza on 2009-11-02
How can i load in iso file, so the machine thinks its an normal "cd".

On the cd are some movie clips that i wanna see.

Thanks on advance:KS

---

### Post by iMisspell on 2009-11-02
maybe this will help you.
[http://ubuntuforums.org/showthread.php?t=426365](http://ubuntuforums.org/showthread.php?t=426365)

---

### Post by Zoot7 on 2009-11-02
You could try out Gmount-Iso; it's a nice GUI to mount ISOs.
```
sudo apt-get install gmountiso
```

Alternatively there's the command line way:
```
sudo mount -o loop -t iso9660 image_file.iso <mount point>
```

---

### Post by coffeecat on 2009-11-02
The app gISOmount is in the repos. It works well enough. Just be warned that the first time you use it, when you click on "browse" to find your iso, it opens in /root. You have to navigate back to your home directory, but thereafter it remembers the path to ~\.

---

### Post by NickJones on 2009-11-02
Another problem I found with gISOmount was if the file name is "Nick.ISO" it will not work, however if it is "Nick.iso" it will work, a minor bug, but beware, I had to re-name any of my 500gb ISO collection if I want it to work. 
Nick

---

### Post by konqueror7 on 2009-11-02
i find [AcetoneISO]("http://www.getdeb.net/release.php?id=4856") more functional and fitting for my needs...

---

