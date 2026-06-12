---
title: "I have a Dell Mini..."
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Tonya_in_FL on 2010-09-03
So, hi everyone. I'm brand new to the forums, and relatively new to Ubuntu (only using for a year). I have a Dell Mini Inspiron 910 running Hardy 8.04. Recently I installed an update from update manager and now some things on my computer are hinky. My Firefox has some issues - mostly cosmetic, but the big problem is I can't load Java applets. Everytime I try to check if I have java on the sun website it asks to install a missing plugin (icedtea6). When I try to install, it always fails saying ```
failed to fetch http://dl.google.com/linux/deb/dists/stable/ release unable to find expected entry main/binary-lpia/packages in meta-index file
```.

I've read some information before about Dell making a "special" version of ubuntu on the minis and it having odd results, but it hadn't affected me until now. I really hope someone can help me fix firefox and get my java working again. :sad:

---

### Post by llamabr on 2010-09-03
Hi.  For better results, you should have a more descriptive subject line.

Post the output of:

```
cat /etc/apt/sources.list
```

and 

```
cat /etc/apt/sources.list.d/
```

I'm not sure about your java problem, but I think I can fix that error.

---

### Post by Tonya_in_FL on 2010-09-03
Thanks so much for quick reply. Sorry about the subject line thing.

Um my results were:

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```and

```
cat: /etc/apt/sources.list.d/: Is a directory
```

---

### Post by llamabr on 2010-09-03
Uh huh.  And what happens is you try to run:

```
sudo apt-get install sun-java6-plugin sun-java6-jre
```

---

### Post by Tonya_in_FL on 2010-09-03
OK. I tried this and nothing happened. :(

---

### Post by llamabr on 2010-09-03
What do you mean, nothing happened?  did they install?

---

### Post by Tonya_in_FL on 2010-09-03
I don't know. I typed the previous code in terminal and after asking for sudo password it didn't do anything except go back to the command prompt. I restarted just in case something had happened, but on startup everything seemed the same. I tried to load a java applet and it still wouldn't load.

---

### Post by Tonya_in_FL on 2010-09-04
Has anyone else encountered this problem and fixed it?

---

### Post by sandyd on 2010-09-04
> **Tonya_in_FL said:**
> So, hi everyone. I'm brand new to the forums, and relatively new to Ubuntu (only using for a year). I have a Dell Mini Inspiron 910 running Hardy 8.04. Recently I installed an update from update manager and now some things on my computer are hinky. My Firefox has some issues - mostly cosmetic, but the big problem is I can't load Java applets. Everytime I try to check if I have java on the sun website it asks to install a missing plugin (icedtea6). When I try to install, it always fails saying ```
failed to fetch http://dl.google.com/linux/deb/dists/stable/ release unable to find expected entry main/binary-lpia/packages in meta-index file
```.

I've read some information before about Dell making a "special" version of ubuntu on the minis and it having odd results, but it hadn't affected me until now. I really hope someone can help me fix firefox and get my java working again. :sad:


lpia architecture is no longer supported.
reinstall ubuntu, downloading the 32-bit version from the [http://ubuntu.com](http://ubuntu.com) site.
run
```

uname -a
```and post output to comfirm that you are running the lpia arch

---

### Post by Tonya_in_FL on 2010-09-04
The results I got were:

```
Linux toni 2.6.24-27-lpia #1 SMP Thu Apr 8 18:04:46 UTC 2010 i686 GNU/Linux
```

Is there anyway I can update instead of reinstalling? I would like to try the Lucid netbook remix anyway.

---

### Post by sandyd on 2010-09-04
yeah, your using LPIA
> **Tonya_in_FL said:**
> The results I got were:

```
Linux toni 2.6.24-27-lpia #1 SMP Thu Apr 8 18:04:46 UTC 2010 i686 GNU/Linux
```Is there anyway I can update instead of reinstalling? I would like to try the Lucid netbook remix anyway.
nope. since LPIA is no longer supported, you cannot update.
Not sure why dell is still sending out dell minis even though LPIA is no longer supported...

---

### Post by Tonya_in_FL on 2010-09-04
Well, thanks I'll see if i can back up everything and just reinstall. I'll put lucid on.

---

