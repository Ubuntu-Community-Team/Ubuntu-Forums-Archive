---
title: "Problem to install GNUtrition 3.1"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by snoopy123 on 2011-02-26
Dear Friends,

I have problem to install the gnutrition.  I am new to Ubuntu, so I really can't figure out what the root cause is.  Please refer to below for the problem.  You help will be greatly appreciated.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++
 qq01@qq01:~$ /home/qq01/Desktop/gnutrition/configure
  checking for python... /usr/bin/python
  checking for python >= 2.2... yes
  checking for a BSD-compatible install... /usr/bin/install -c
  checking whether make sets $(MAKE)... yes
  checking for pygtk... yes
  checking for MySQLdb... yes
  configure: creating ./config.status
  config.status: creating run-gnutrition.py
  config.status: creating src/install.py
  config.status: creating Makefile
  config.status: creating src/Makefile
  config.status: creating data/Makefile
  config.status: creating pixmaps/Makefile
  config.status: creating doc/Makefile
  config.status: WARNING:  '/home/qq01/Desktop/gnutrition/doc/Makefile.in' seems to ignore the --datarootdir setting
  config.status: creating rpm/Makefile
  config.status: creating rpm/gnutrition.spec
  config.status: creating debian/Makefile
  qq01@qq01:~$ make
  for dir in src data pixmaps doc rpm debian; do \
                  make -C $dir all; \
          done
  make[1]: Entering directory `/home/qq01/src'
  chmod +x /home/qq01/Desktop/gnutrition/py-compile
  /home/qq01/Desktop/gnutrition/py-compile *.py
  Byte-compiling python modules...
  install.py
  Byte-compiling python modules (optimised versions) ...
  install.py
  make[1]: Leaving directory `/home/qq01/src'
  make[1]: Entering directory `/home/qq01/data'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/data'
  make[1]: Entering directory `/home/qq01/pixmaps'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/pixmaps'
  make[1]: Entering directory `/home/qq01/doc'
  make[1]: *** No rule to make target `gnutrition.sgml', needed by `create-html'.  Stop.
  make[1]: Leaving directory `/home/qq01/doc'
  make[1]: Entering directory `/home/qq01/rpm'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/rpm'
  make[1]: Entering directory `/home/qq01/debian'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/debian'
  qq01@qq01:~$ sudo make install
  for dir in src data pixmaps doc rpm debian; do \
                  make -C $dir all; \
          done
  make[1]: Entering directory `/home/qq01/src'
  chmod +x /home/qa01/Desktop/gnutrition/py-compile
  /home/qq01/Desktop/gnutrition/py-compile *.py
  Byte-compiling python modules...
  install.py
  Byte-compiling python modules (optimised versions) ...
  install.py
  make[1]: Leaving directory `/home/qq01/src'
  make[1]: Entering directory `/home/qq01/data'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/data'
  make[1]: Entering directory `/home/qq01/pixmaps'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/pixmaps'
  make[1]: Entering directory `/home/qq01/doc'
  make[1]: *** No rule to make target `gnutrition.sgml', needed by `create-html'.  Stop.
  make[1]: Leaving directory `/home/qq01/doc'
  make[1]: Entering directory `/home/qq01/rpm'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/rpm'
  make[1]: Entering directory `/home/qq01/debian'
  make[1]: Nothing to be done for `all'.
  make[1]: Leaving directory `/home/qq01/debian'
  mkdir -p /usr/local/bin
  mkdir -p /usr/local/share/gnutrition
  for dir in src data pixmaps doc rpm debian; do \
                  make -C $dir install; \
          done
  make[1]: Entering directory `/home/qq01/src'
  mkdir -p /usr/local/share/gnutrition/src
  /usr/bin/install -c -m 644 -c *.py *.pyc *.pyo /usr/local/share/gnutrition/src
  make[1]: Leaving directory `/home/qq01/src'
  make[1]: Entering directory `/home/qq01/data'
  mkdir -p /usr/local/share/gnutrition/data
  /usr/bin/install -c -m 644 -c *.txt /usr/local/share/gnutrition/data
  /usr/bin/install: cannot stat `*.txt': No such file or directory
  make[1]: *** [install] Error 1
  make[1]: Leaving directory `/home/qq01/data'
  make[1]: Entering directory `/home/qq01/pixmaps'
  mkdir -p /usr/local/share/gnutrition/pixmaps
  /usr/bin/install -c -m 644 -c *.png /usr/local/share/gnutrition/pixmaps
  /usr/bin/install: cannot stat `*.png': No such file or directory
  make[1]: *** [install] Error 1
  make[1]: Leaving directory `/home/qq01/pixmaps'
  make[1]: Entering directory `/home/qq01/doc'
  make[1]: *** No rule to make target `gnutrition.sgml', needed by `create-html'.  Stop.
  make[1]: Leaving directory `/home/qq01/doc'
  make[1]: Entering directory `/home/qq01/rpm'
  make[1]: Nothing to be done for `install'.
  make[1]: Leaving directory `/home/qq01/rpm'
  make[1]: Entering directory `/home/qq01/debian'
  make[1]: Nothing to be done for `install'.
  make[1]: Leaving directory `/home/qq01/debian'
  mkdir -p /usr/local/bin
  /usr/bin/install -c run-gnutrition.py /usr/local/bin/gnutrition
  mkdir -p /usr/local/gnome/apps/Applications/
  /usr/bin/install -c -m 644 gnutrition.desktop /usr/local/gnome/apps/Applications/
  /usr/bin/install: cannot stat `gnutrition.desktop': No such file or directory
  make: *** [install] Error 1
  qq01@qq01:~$ gnutrition
  Traceback (most recent call last):
    File "/usr/local/bin/gnutrition", line 28, in <module>
      import src.run_app
  ImportError: No module named src.run_app
  qq01@qq01:~$ 
  

 Thanks again.

---

### Post by gmargo on 2011-02-26
You need to run the configure/compile/install from within the gnutrition-0.31/ directory.  It does not seem to support building in a parallel directory.

---

### Post by snoopy123 on 2011-02-28
Dear Gmargo,

Can you please describe it in more detail (step by step)?  I am new to ubuntu, so I don't quite understand what you mean.  Your help will be greatly appreciated.  Thanks you very much.

---

### Post by gmargo on 2011-02-28
> 
qq01@qq01:~$ /home/qq01/Desktop/gnutrition/configure
In the above, you are currently in your $HOME directory, but the gnutrition source code is elsewhere.  You need to run configure from within the gnutrition source code directory.

I'm not sure where you got your source code from, but here's a step-by-step with the latest released code:
```

mkdir work ; cd work
wget http://mirrors.ibiblio.org/pub/mirrors/gnu/ftp/gnu/gnutrition/gnutrition-0.31.tar.gz
tar xzfv gnutrition-0.31.tar.gz
cd gnutrition-0.31
./configure
make
make install

```

---

### Post by snoopy123 on 2011-03-01
What I did is download and save the zip file on desktop, then unzip it.  After that, I follow the instruction in the "installation" file.  
Now, am I just using your code directly in terminal without downloading the file first?
mkdir work ; cd work
wget [http://mirrors.ibiblio.org/pub/mirrors/gnu/ftp/gnu/gnutrition/gnutrition-0.31.tar.gz](http://mirrors.ibiblio.org/pub/mirrors/gnu/ftp/gnu/gnutrition/gnutrition-0.31.tar.gz)
tar xzfv gnutrition-0.31.tar.gz
cd gnutrition-0.31
./configure
make
make install
Thanks you very much.

---

