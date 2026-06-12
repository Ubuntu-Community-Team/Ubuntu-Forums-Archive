---
title: "Installing tar.gz - Where do I learn this skill?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by cat2005 on 2009-10-21
I know I can't be the first to ask this and I know I won't be the last:  How do I install something labeled "tar.gz"?

Do you know of any general instructions, tutorials, resources, etc which I could use?

I would appreciate being pointed in the correct direction.  This is something I want to learn and now I have an opportunity (tar.gz file I downloaded) to learn it.

Thanks!

---

### Post by SkyNet2029 on 2009-10-21
```
$man tar
```
will output the format and correct usage of that command

---

### Post by wojox on 2009-10-21
Open a terminal:

```
man tar
```

Is the manual for .taped archives

Use man for all you utilities.

---

### Post by aysiu on 2009-10-21
There is no general.

A .tar.gz is just a compressed file (like a .zip file).

It could contain source code to be compiled. It could contain a precompiled binary. It could contain a .bin installer to be run. It might not even be a program. A lot of themes come as .tar.gz files that you drag and drop to the System > Preferences > Appearances window.

Best to avoid .tar.gz files and stick to the repositories if you're installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If that's not possible, you need to take it on a case-by-case basis. **There is no general procedure for .tar.gz files.**

---

### Post by coolbrook on 2009-10-21
I'm not sure why this was removed from the documentation for 9.04.  It will work just the same.

[https://help.ubuntu.com/8.10/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/8.10/add-applications/C/install-file.html#tarballs)

---

### Post by Niko Johnson on 2009-10-21
for a tar.gz file always remeber this code ```
tar -xzvf file.tar.gz 
```

---

### Post by aysiu on 2009-10-21
> **Niko Johnson said:**
> for a tar.gz file always remeber this code ```
tar -xzvf file.tar.gz 
```
And if you forget that code, you can right-click the .tar.gz and select **Extract here**

---

### Post by staticextasy on 2009-10-21
> **aysiu said:**
> And if you forget that code, you can right-click the .tar.gz and select **Extract here**

haha not everyone uses a desktop environment so right clicking isnt always the case :P

---

### Post by OpenGuard on 2009-10-21
Extract it:
```
tar xvfz application.tar.gz
```

Compile and install it:
```
./configure
make
sudo make install

```

---

### Post by aysiu on 2009-10-21
> **staticextasy said:**
> haha not everyone uses a desktop environment so right clicking isnt always the case :P
If someone doesn't have a desktop environment and is posting in Absolute Beginner, then that someone should request to have the thread moved to the Server subforum. Otherwise, it makes sense to put "I really would like to know how to do this strictly by command-line, as I do not have a desktop environment installed."

---

### Post by staticextasy on 2009-10-21
> **aysiu said:**
> If someone doesn't have a desktop environment and is posting in Absolute Beginner, then that someone should request to have the thread moved to the Server subforum. Otherwise, it makes sense to put "I really would like to know how to do this strictly by command-line, as I do not have a desktop environment installed."

true but then again, this is the Absolute Beginner talk here.. need i say more. Anyways, sorry for going off topic cat2005; i hope everyones answers helped you out.

Good luck.

---

### Post by cat2005 on 2009-10-21
Wow...yes...thanks for all the quick replies.

Normally I am wary of tar files but these are major open source voip programs:

a) freeswitch
b) yate
c) asterick

If I have more questions, then I will post again.

Thanks all!

---

### Post by MelDJ on 2009-10-22
try: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by 3rdalbum on 2009-10-22
I'm not trying to be insulting, but what does the documentation for the program tell you to do? There is usually a file called "INSTALL" inside the tarball that tells you the procedure for installing or running the program.

If there's something about the instructions that you don't understand, post back here with that particular instruction and we'd be happy to clear it up for you.

---

