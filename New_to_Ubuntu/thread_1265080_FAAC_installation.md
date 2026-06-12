---
title: "FAAC installation"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by g2no11ah2 on 2009-09-13
I do sudo -s ./configure

Then I try 'make'
and it outputs this:

noah@MAGICBOX:~/Desktop/faac-1.28$ make
make  all-recursive
make[1]: Entering directory `/home/noah/Desktop/faac-1.28'
Making all in include
make[2]: Entering directory `/home/noah/Desktop/faac-1.28/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noah/Desktop/faac-1.28/include'
Making all in libfaac
make[2]: Entering directory `/home/noah/Desktop/faac-1.28/libfaac'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noah/Desktop/faac-1.28/libfaac'
Making all in common
make[2]: Entering directory `/home/noah/Desktop/faac-1.28/common'
Making all in mp4v2
make[3]: Entering directory `/home/noah/Desktop/faac-1.28/common/mp4v2'
source='3gp.cpp' object='3gp.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/sh ../../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include   -Wall  -c -o 3gp.o 3gp.cpp
exec: 519: g++: not found
make[3]: *** [3gp.o] Error 2
make[3]: Leaving directory `/home/noah/Desktop/faac-1.28/common/mp4v2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/noah/Desktop/faac-1.28/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/noah/Desktop/faac-1.28'
make: *** [all] Error 2
noah@MAGICBOX:~/Desktop/faac-1.28$ 

Anyone know why I'm getting these errors?  FAAC'n A

[http://linux.softpedia.com/get/Multimedia/Video/FAAC-554.shtml](http://linux.softpedia.com/get/Multimedia/Video/FAAC-554.shtml)

---

### Post by Grifulkin on 2009-09-13
you could try ```
sudo make
``` also, you don't get any errors with the ```
./configure
```

---

### Post by andrew.46 on 2009-09-13
Hi g2no11ah2,

You should really only need to run ./configure as an ordinary user, and as a side issue have you installed the required compiling tools? These are:

```
sudo apt-get install build-essential
```

And a final thought: do you actually need to *compile* faac? There is a decent version in the Ubuntu repositories + -dev files...

All the best,

Andrew

---

### Post by g2no11ah2 on 2009-09-13
I give up...

How do I install from the + -dev files?

---

### Post by andrew.46 on 2009-09-13
Hi g2nollah2,

> **g2no11ah2 said:**
> I give up...

How do I install from the + -dev files?

It depends what you need faac for. If you simply wish to create aac files by using the commandline faac or if other programs require faac for their own encoding purposes, such as the script abcde, all you need to do is:

```
sudo apt-get install faac
```

If however you are compiling another multimedia application which requires header files from faac, such as FFmpeg or MPlayer, all you need to do is:

```
sudo apt-get install libfaac-dev libfaac0
```

Can I ask what you need faac for?

Andrew

---

### Post by g2no11ah2 on 2009-09-13
To play m4a files that itunes creates.  I'm going to play them with the stock music player with 9.04

---

### Post by g2no11ah2 on 2009-09-13
Thanks man!  It works!

:popcorn:

---

### Post by andrew.46 on 2009-09-13
Hi g2nollah,

> **g2no11ah2 said:**
> Thanks man!  It works!

Great news :). I should have worked out a little earlier that you did not actually need to *compile* faac and this might have saved you a little grief... Mind you faac is the *encoder*, normally various applications would need faad2 for *decoding* but I will not question success!

All the best,

Andrew

---

### Post by kevdog on 2009-09-14
Hmm

When did Andrew become a Ubuntu forum member??  Interesting and Congratulations!!1

---

### Post by andrew.46 on 2009-09-14
Hi kevdog,

> **kevdog said:**
> When did Andrew become a Ubuntu forum member??  Interesting and Congratulations!!1

Thanks :). I successfully applied late in June this year.

Andrew

---

### Post by entrant on 2010-05-22
I did the following to get faac-1.28 for playing mpeg4 files (when it asked me for MPEG4 AAC decoder required but could not find suitable plugins) but no sound is heard from certain files:

1) downloaded faac-1.28.tar.bz2 from [http://linux.softpedia.com/get/Multimedia/Video/FAAC-554.shtml](http://linux.softpedia.com/get/Multimedia/Video/FAAC-554.shtml)
2) tar xjvf faac-1.28.tar.bz2
3) ./bootstrap
4) ./configure
5) sudo make - got an error of mp4v2 not to be present in /commons/
6) sudo apt-get install libfaac-dev libfaac0
7) sudo apt-get install build-essential

Then some files worked and some again showed up asking for plugins to be downloaded but as usual in vain. Also, there is no sound from those files where as animations are seen properly.

Please reply.

~entrant

---

