---
title: "Cover Gloobus installation help needed"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-08-27
I downloaded the tar.gz file from [here]("http://launchpad.net/covergloobus/1.6/1.6stable/+download/covergloobus_1.6.tar.gz"). After unpacking the contents and cd-ing to the location. I did ./configure. It gave the following:
```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
configure: error: cannot run /bin/bash ./config.sub

```
I think only the last line is significant. I downloaded the same package from other sources too. No luck.
Please guide.

---

### Post by Bobbyrne01 on 2010-09-13
your prob betta off just adding the ppa . . check out [http://gloobus.net/wiki/index.php?title=Install#Installing_CoverGloobus_from_the_PPA]("http://gloobus.net/wiki/index.php?title=Install#Installing_CoverGloobus_from_the_PPA") for installation :)

---

### Post by sosaited on 2010-11-11
You need to have autoconf and probably libtool too for ./autogen

Run 
```

sudo apt-get install autoconf
sudo apt-get install libtool

```

---

