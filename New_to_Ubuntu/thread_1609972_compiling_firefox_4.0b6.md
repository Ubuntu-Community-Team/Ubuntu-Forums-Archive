---
title: "compiling firefox 4.0b6"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by mahmoodkamal on 2010-10-31
Guys, I am using firefox 3.6.12 and have no problem with it. However, wanted to test the beta release 4.0b6. When i downloaded it was a tar.bz2 file. I saved this file on my desktop and extracted files from it.

Now it appears that I have to compile it, for which I need some help. Kindly can anyone guide me on this task. :)

---

### Post by Verbeck on 2010-10-31
why don't you try the firrfox ppa? it'll be easier. run in a terminal :
**sudo apt-add-repository [B]ppa:ubuntu-mozilla-daily/ppa**[/B]
            **sudo apt-get update**
**sudo apt-get install                 firefox-4.0               **

---

### Post by mahmoodkamal on 2010-10-31
will try and let you know. Thanks

---

### Post by crichard on 2010-10-31
> **mahmoodkamal said:**
> Guys, I am using firefox 3.6.12 and have no problem with it. However, wanted to test the beta release 4.0b6. When i downloaded it was a tar.bz2 file. I saved this file on my desktop and extracted files from it.

Now it appears that I have to compile it, for which I need some help. Kindly can anyone guide me on this task. :)

Try this tutorial [http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/](http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/)

---

### Post by mahmoodkamal on 2010-11-01
Thanks guys. Both of the tips were very useful and I learnt a lot from them.

I realized that the file I downloaded was not source code, rather it could be run directly in Linux after decompressing the tar.bz2 file as mentioned by crichard.

**By the way, is there any benefit in compiling yourself on your machine. I heard that you can achieve performance improvements, if you compile the source code specific to your machine.**

---

### Post by Silent Warrior on 2010-11-01
It IS true that you can optimise the compilation for your particular processor - setting flags, -O level, stripping support for some things you don't need. I think the Gentoo-crowd are more vocal (and knowledgable) in regards to this question. Me, I just think it's often more trouble than it's worth. You might get a smaller binary, quicker start - netting you maybe a few milliseconds each day after hunting down -dev packages, spending x minutes compiling, and ending up with a binary you won't receive updates for through the official repositories. If you're up for it, though, you might as well fire away. Firefox 4 doesn't seem to receive frequent updates yet, but I'll heartily recommend sticking to the version in the repositories once it's released. Do remember to 'make uninstall'...

---

