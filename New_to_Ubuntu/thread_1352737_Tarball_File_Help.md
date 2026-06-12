---
title: "Tarball File Help?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by sodra on 2009-12-12
Hi
Long story short

I tried to configure a Tar.gz file
I Did install the build-essential files
But this is what I get

```

edwin@wesley:~$ cd Desktop
edwin@wesley:~/Desktop$ cd fsg-4.4
edwin@wesley:~/Desktop/fsg-4.4$ ./configure
bash: ./configure: No such file or directory
```

What am i doing wrong?

---

### Post by jacobs444 on 2009-12-12
the file might require cmake and not use a configure file. You can find this out by reading the accompanying readme file.

---

### Post by jacobs444 on 2009-12-12
also you may need to type sudo before that command. Again read the readme file. Or documentation on the distributors website.

---

### Post by Physical Hook on 2009-12-12
> **jacobs444 said:**
> also you may need to type sudo before that command. Again read the readme file. Or documentation on the distributors website.

You don't need to use sudo for ./configure and make.

---

### Post by ramjet_1953 on 2009-12-12
Sorry to ask the obvious, but did you un-archive the targz file before trying to configure the application?

Regards,
Roger :)

---

### Post by jacobs444 on 2009-12-12
> **Physical Hook said:**
> You don't need to use sudo for ./configure and make. Not always but sometimes the readme file says you must use sudo or true root to install correctly.

---

### Post by Physical Hook on 2009-12-12
> **jacobs444 said:**
> Not always but sometimes the readme file says you must use sudo or true root **to install** correctly.

./configure and make doesn't install anything :)

---

### Post by fancypiper on 2009-12-12
Perhaps one of these might help you.

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by jacobs444 on 2009-12-12
again, did you read the documentation?

---

### Post by zipperback on 2009-12-12
> **sodra said:**
> Hi
I tried to configure a Tar.gz file
I Did install the build-essential files


A tar.gz file is a file which contains compressed files.

You will need to uncompress the files and then you can configure and install what ever it is that you are trying to get running.

I don't know how every other distribution of Linux does it, but I have Ubuntu 9.10 with gnome desktop, so I can just right click on the tar.gz file and select the "Extract Here" option. That will uncompress the files for me.

Once you have the files, then you should look to see if there are any instructions which have been included to explain how to install the software you are trying to run.

I hope this helps you.

- zipperback
:popcorn:

---

