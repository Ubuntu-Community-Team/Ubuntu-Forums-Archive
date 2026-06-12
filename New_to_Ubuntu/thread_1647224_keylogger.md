---
title: "keylogger"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by raju7258 on 2010-12-17
can anybody help me to install lkl.tar.gz file......................pls its urgent pls............

---

### Post by Rubi1200 on 2010-12-17
Why do you want to install this?

Is it on your own computer?

---

### Post by mendhak on 2010-12-17
Have you extracted it?

Try 

tar -zxvf lkl.tar.gz

---

### Post by seawolf167 on 2010-12-17
Change to the directory containing the tar.gz file

```
cd /path/to/file
```Extract the file

```
tar zxvf nameoffile.tar.gz
```Configure, make & install

```
./configure
make
sudo make install
```

---

### Post by seawolf167 on 2010-12-17
You may also need 

```
sudo apt-get install build-essential
```

to run the above commands

---

### Post by khelben1979 on 2010-12-18
I just checked this [LKL]("http://nixbit.com/cat/system/logging/lkl/").

From the webpage: > 1. `cd' to the directory containing the package's source code and type `./configure' to configure the package for your system.

If you're using `csh' on an old version of System V, you might need to type `sh ./configure' instead to prevent `csh' from trying to execute `configure' itself.

Running `configure' takes awhile. While running, it prints some messages telling which features it is checking for.

2. Type `make' to compile the package.

3. Optionally, type `make check' to run any self-tests that come with the package.

4. Type `make install' to install the programs and any data files and documentation.

5. You can remove the program binaries and object files from the source code directory by typing `make clean'. To also remove the files that `configure' created (so you can compile the package for a different kind of computer), type `make distclean'.

---

### Post by ronnielsen1 on 2010-12-18
Is this linux keylogger? It should be in synaptic under lkl (Universe repositories)

> LKL is a userspace keylogger that runs under Linux on the x86 architechture. LKL sniffs and logs everything that passes through the hardware keyboard port (0x60). It translates keycodes to ASCII with a keymap file. 	  

[http://packages.ubuntu.com/karmic/lkl](http://packages.ubuntu.com/karmic/lkl)

or here's a guide to compile

[http://webnesbay.com/linux-keylogger-in-ubuntu/](http://webnesbay.com/linux-keylogger-in-ubuntu/)

---

