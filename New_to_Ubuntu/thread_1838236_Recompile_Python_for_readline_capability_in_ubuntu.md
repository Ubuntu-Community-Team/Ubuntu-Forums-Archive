---
title: "Recompile Python for readline capability in ubuntu 11.04?"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by gdoc on 2011-09-03
Hi All,

I am using Ubuntu 11.04. In previous versions of Ubuntu I have been able to use the arrow keys in a python session in a terminal. However when I upgraded I lost this ability. I am using the version of python which came with the os (2.7). 

I have done some poking around online and it seems that the issue is probably that python was not linked to the readline library when it was compiled. I installed libreadline5-dev using apt-get.

Now I guess I would like to recompile python - I am kinda stuck here.

I tried sudo apt-get install --reinstall python2.7, however this did not seem to change anything.

Anyone have any pointers?

Cheers,

G

---

### Post by Leshrac on 2011-09-03
apt-get install --reinstall python2.7 won't compile anything, it just reinstalls the binary package, in the same way as the first time.

You want to download the phyton source, check the configuration to make sure that readline support is enabled and then compile it by running the configure script, then make, then make install.
If you are not sure on how to do it you can follow this how-to [http://opkode.net/media/blog/compiling-python-with-readline-support-on-ubuntu-linux](http://opkode.net/media/blog/compiling-python-with-readline-support-on-ubuntu-linux) but keep in mind that it is for an older version, you'll have to change the numbers for whatever version you want to use.

Alternatively, they might be a way to get readline support without recompiling, such as the method suggested in this stackoverflow answer: [http://stackoverflow.com/questions/3764730/adding-readline-functionality-without-recompiling-python](http://stackoverflow.com/questions/3764730/adding-readline-functionality-without-recompiling-python)

---

### Post by gdoc on 2011-09-03
Thanks Leshrac! Made my life a lot easier.  The solution was in the stackoverflow page. 

In case anyone else has this issue the solution that worked for me was:
sudo apt-get install python-setuptools
sudo easy_install readline

---

