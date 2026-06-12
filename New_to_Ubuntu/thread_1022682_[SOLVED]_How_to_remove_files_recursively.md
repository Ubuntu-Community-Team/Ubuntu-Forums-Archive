---
title: "[SOLVED] How to remove files recursively?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-12-27
I have a folder and has many folder inside of it. All of the folders have files, with pretty much the same name, inside. I was wondering how exactly I can go about deleting all of the files in all of the folders. All of the files I want to delete start with index.random_end. 

For example. The main folder is web, then underneath it I have over 1000 folders and all of them have files in it named; index.html, indes.html?D=A, etc

---

### Post by billgoldberg on 2008-12-27
use

```
rm -r 
```

Lets say you have a folder called "One" in /home

in a terminal

```
rm -r One 
```

would delete that folder and everything in it.

---

### Post by slughappy1 on 2008-12-27
That's not what I meant, sorry. I meant, all of the folders have files I want to keep. I just want to get rid of other files that are in them.

---

### Post by Big_astur on 2008-12-27
Can u use the search for it?

I mean go to Places/Search Files (i have it in Spanish so might be different). Then search for index.random_end in the folder you are talking about, now just select all the files it found, right-click and move to trash.

---

### Post by slughappy1 on 2008-12-27
I didn't even think of that Big_astur, thanks.

---

### Post by Firestone on 2008-12-27
You could try wildcards.
For example :
```
/web$ rm */index.*
```

This will delete every index.something in the subdirs of web/
(check the position of the * a few times before executing to be save)

---

### Post by billgoldberg on 2008-12-27
Oh sorry for my previous post, you can use this command:

```
find /home/web -type f -name "index.*" -exec rm -f {} \;
```

Asuming your "web" folder is located in /home/web.

This wil remove all files that start with index in web and all sub folders.

Read more here:

[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

---

