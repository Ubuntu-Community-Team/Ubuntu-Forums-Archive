---
title: "synaptic package manager error"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by now0pen on 2011-03-04
Help a newbie--

I don't know how I got here, but when I opened synaptic package manager, I got this error and couldn't get past this. What should I do?

[IMG]http://img819.imageshack.us/img819/8315/screenshotjl.png[/IMG]

Thanks!

---

### Post by turtle153 on 2011-03-04
Just do what it says :D
Open a terminal and type ```

sudo dpkg --configure -a
```
and see where that gets you.

---

### Post by now0pen on 2011-03-04
I did what you said, and here's what came out--

```

jimsyyap@jimsyyap-desktop:~$ sudo dpkg --configure -a
[sudo] password for jimsyyap: 
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for hicolor-icon-theme ...
Setting up icoutils (0.29.1-0ubuntu1~lucid) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_NZ.utf8.cache...
Setting up ttf-droid (1.00~b112+dfsg+1-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-droid
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese, defaulting to 0.
No CIDSupplement specified for DroidSansJapanese-JaH, defaulting to 0.

Setting up wine1.2-gecko (1.0.0-0ubuntu4) ...
Setting up libmpg123-0 (1.12.1-0ubuntu1) ...

Setting up cabextract (1.2-3+lenny1build0.10.04.1) ...
Setting up ttf-symbol-replacement (1.2.2-0ubuntu2~lucid1) ...
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ...
procps stop/waiting
procps stop/waiting

Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jimsyyap@jimsyyap-desktop:~$ 

```Synaptic package manager is working now. Thank you for your help. 

I'd like to broaden my understanding. Based on the code above--What happened? How did it happen? How do I avoid this in the future?

Thanks!

---

### Post by turtle153 on 2011-03-04
dpkg is the "behind the scenes" package management system, it's a powerful tool and can fix a lot of package problems automatically. I don't know how you got that problem if you weren't editing system files, you might just be unlucky, but when you get an error message telling you to run a command, the best thing to do is run it :p

One cause could be from cutting to power to the computer: always do a full shutdown

---

