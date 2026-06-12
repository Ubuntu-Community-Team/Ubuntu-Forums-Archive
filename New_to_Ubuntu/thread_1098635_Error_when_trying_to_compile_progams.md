---
title: "Error when trying to compile progams"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by hellomoto on 2009-03-17
Hi when ever I try to compile programs (and I have try a number of diffrent ones) I constantly get the same error when running configure. 

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.


```

 Can anyone help?

Thank you.

---

### Post by raedbenz on 2009-03-17
Hi,,
how do u compile??? what is the command line u use?
what ubuntu version u have??
cheers

---

### Post by hellomoto on 2009-03-17
This is with ubuntu 8.10 and I use the command "sudo sh ./configure" when I get this error.

---

### Post by raedbenz on 2009-03-17
try:

```
#./configure

# make

And install the compiled code:

# make install

```

---

### Post by taurus on 2009-03-17
You have already installed the build-essential package, right?

---

### Post by hellomoto on 2009-03-17
does the build essential package come preinstalled? I have tryed running just sudo ./configure but had no luck

---

### Post by Eisenwinter on 2009-03-17
The package build-essential does not come preinstalled:

```
sudo apt-get install build-essential
```

This package will give you all sorts of tools for installing programs from source. Install it, and try again.

---

### Post by Bodsda on 2009-03-17
run the following commands please, they install the necessary packages to compile and then compile it

```
sudo apt-get install build-essential
```

then cd to the directory containing the code you want to compile

```
cd /path/to/directory
```

then run these three commands exactly as shown

```
./configure
```
```
make
```
```
sudo make install
```

NOTE: you dont need sudo untill the 3rd command 'make install'

thanks,

Bodsda

Edit: If the above does not work can you also paste the contents of the config.log file, it might contain useful information

---

### Post by hellomoto on 2009-03-17
ok I have install build essentials (which I didn't have).

I ran sudo sh ./configure and got the same error:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

then i ran just sudo ./configure and I get the following error:
```

sudo: unable to execute ./configure: Permission denied

```

i also tryed to just run ./configure
```

bash: ./configure: /bin/sh: bad interpreter: Permission denied

```

I don't see the point in sunning make untill configure has completed? Also I am in the directory of the program I wish to install.

---

### Post by taurus on 2009-03-17
Can you post the exact command you ran to install build-essential (not build essentials or build-essentials)?

---

### Post by binbash on 2009-03-17
sudo make clean 
then :
./configure or ran sudo ./configure

---

### Post by hellomoto on 2009-03-17
> **taurus said:**
> Can you post the exact command you ran to install build-essential (not build essentials or build-essentials)?

I used sudo apt-get install build-essential

---

### Post by oldos2er on 2009-03-17
Drop "sudo" and "sh" and just run "./configure". Does it work?

---

### Post by SunnyRabbiera on 2009-03-17
Why compile?
A lot of the apps you need are in the repos.
What are you trying to compile anyway?

---

### Post by hellomoto on 2009-03-21
i am trying to compile a program ignuit - an educational application. 

however there are still a number of other programs i would like to compile that i can compile on my other ubuntu boxes. Just because it doesn't work doesn't mean I should give up!

I really want to try out ubuntu netbook remix too but because of my compiler not working, im not having much luck!

I still get the following error no matter what I try to compile:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have tryed uninstalling and re-installing the package, with no luck.

Is there anything else I can do, this error is becoming a real problem!

Thank you!

---

### Post by hellomoto on 2009-03-21
I have also just put in a live CD and then run configure and it worked first time. So there must be a problem with my GCC compiler.

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /media/Media: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... 
no
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
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E

```

Can anyone tell me exactly what packages I need for my GCC compiler to work. Then i can check if I have the correct packages or any extra ones that maybe interfering with GCC.

Thank you.

---

### Post by oldos2er on 2009-03-21
If you're running 8.10, try [https://edge.launchpad.net/~antono/+archive](https://edge.launchpad.net/~antono/+archive)

---

### Post by carml on 2009-03-21
If you installed build-essential you should have got also gcc 4 or above,maybe there some more library needed:confused: . 
Have you got some more info on the program you want to compile? I mean do you know what the dependences are?

---

### Post by hellomoto on 2009-03-21
i just found this

```

checking whether the C compiler works... configure: error: cannot run C compiled programs.
I think you'll find that you are using gcc 4.x instead of gcc 3.4, the older version.
There was some change with gcc 4.0 and many older systems haven't caught up with their configuration scripts.

I haven't fixed this error yet myself, but perhaps someone else has. I'd appreciate feedback! :)
Of course, you can try tyo deinstall gcc 4.x and install gcc 3.x instead but you may not know how or don't want to

```

I tried installing GCC3 but still had no luck,

---

### Post by taurus on 2009-03-21
> **hellomoto said:**
> i just found this

```

checking whether the C compiler works... configure: error: cannot run C compiled programs.
I think you'll find that you are using gcc 4.x instead of gcc 3.4, the older version.
There was some change with gcc 4.0 and many older systems haven't caught up with their configuration scripts.

I haven't fixed this error yet myself, but perhaps someone else has. I'd appreciate feedback! :)
Of course, you can try tyo deinstall gcc 4.x and install gcc 3.x instead but you may not know how or don't want to

```

I tried installing GCC3 but still had no luck,

But did you remove version 4 when you installed an older gcc compiler?

```
gcc -v
```

---

### Post by hellomoto on 2009-03-21
heya, yeh i have and it all seams to be working now. I can compile all my programs :)

However it doesn't make much sense i installed Gcc 3.x and running gcc -v shows.

```

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 

``` 

so it still says i am using gcc 4.x

the only thing i can think of is after i installed gcc 3.x I didn't reboot, tryed to use it and it didn't work.

then i rebooted tryed to use it again and it did work
seams all a bit dodgy but hopfully it was a one off with my current install due to me messing some settings i shldn't of!

---

