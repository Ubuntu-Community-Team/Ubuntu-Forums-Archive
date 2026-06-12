---
title: "Need help installing a program from source"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by jitup on 2009-06-07
hello, I am trying to turn my old laptop into a multi FX processor for guitar, which I will control via a GT-6 utilizing its midi control mode, but I need help installing the software! I have jack and the other sound stuff needed, I just cant figure out how to install rakarrack-0.3.0 from the source. I extracted the the .tar and made a foulder in my home (jim) called Rakarrack, where I extreted the folder rakarrack-.0.3.0 
so it is jim/Rakarrack/rakarrack-.0.3.0 
here is as far as I got> 
jim@jim-laptop:~$ cd jim/Rakarrack/rakarrack-0.3.0
bash: cd: jim/Rakarrack/rakarrack-0.3.0: No such file or directory
jim@jim-laptop:~$ 

I tried following another thread on how to compile programs, I was wondering if someone could type out the code in a quote for me so I can paste it in terminal. I cant use the the internet on my lappy because I have dial up, and I could not find the .deb file for ubuntu 9.04. If some has a link to a direct download of the package, I can download that, put it on my flash drive and install it that way. thanks

---

### Post by sandyd on 2009-06-07
> **jitup said:**
> hello, I am trying to turn my old laptop into a multi FX processor for guitar, which I will control via a GT-6 utilizing its midi control mode, but I need help installing the software! I have jack and the other sound stuff needed, I just cant figure out how to install rakarrack-0.3.0 from the source. I extracted the the .tar and made a foulder in my home (jim) called Rakarrack, where I extreted the folder rakarrack-.0.3.0 
so it is jim/Rakarrack/rakarrack-.0.3.0 
here is as far as I got
I tried following another thread on how to compile programs, I was wondering if someone could type out the code in a quote for me so I can paste it in terminal. I cant use the the internet on my lappy because I have dial up, and I could not find the .deb file for ubuntu 9.04. If some has a link to a direct download of the package, I can download that, put it on my flash drive and install it that way. thanks

looks like it has a flawed instruction.
it should be 
```

jim@jim-laptop:~$ cd ~/Rakarrack/rakarrack-0.3.0

```
not
```

jim@jim-laptop:~$ cd jim/Rakarrack/rakarrack-0.3.0
 
```

---

### Post by jitup on 2009-06-07
I tried that and this is what I got now,
```
jim@jim-laptop:~$ cd ~/Rakarrack/rakarrack-.0.3.0
bash: cd: /home/jim/Rakarrack/rakarrack-.0.3.0: No such file or directory
jim@jim-laptop:~$ 
jim@jim-laptop:~$ ./configure
bash: ./configure: No such file or directory
jim@jim-laptop:~$ 
jim@jim-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
jim@jim-laptop:~$ 
jim@jim-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
jim@jim-laptop:~$ 




```

---

### Post by _Purple_ on 2009-06-07
What is the output of
```
ls -l ~/Rakarrack/
```

---

### Post by mgt_90 on 2009-06-07
Well what's clearly going wrong is not the compilation but the fact you can't cd into the appropriate directory.   Could you run "ls" for us when you're in home?  Also, are you using tab completion to fill in the pathnames or are you typing it all out? I'd suggest the former to eliminate the possibilities of a typo in entering the pathnames.

---

### Post by jitup on 2009-06-07
this is what I got after tunning that last code
```


jim@jim-laptop:~$ ls -l ~/Rakarrack/
total 4
drwxrwxrwx 7 jim jim 4096 2008-11-25 07:17 rakarrack-0.3.0
jim@jim-laptop:~$ 


```

---

### Post by mrbiggbrain on 2009-06-07
you know i find linux's completion verry useful, have you tryed

cd ~/R<TAB><TAB>

that would list every last folder in your home directory begining with r, and if one exists it will complete it for you

then just do it again, i do this alot so i dont have to type alot of versions or random letters.

---

### Post by ethoxyethaan on 2009-06-07
cd ~/Rakarrack/rakarrack-0.3.0

---

### Post by kevdog on 2009-06-07
As a side note, I can tell this is going to be a long process :(

---

### Post by jitup on 2009-06-08
I think you are right about this being a long process :(
this is what I got now
```
jim@jim-laptop:~$ cd ~/Rakarrack/rakarrack-0.3.0
jim@jim-laptop:~/Rakarrack/rakarrack-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
jim@jim-laptop:~/Rakarrack/rakarrack-0.3.0$ make
make: *** No targets specified and no makefile found.  Stop.
jim@jim-laptop:~/Rakarrack/rakarrack-0.3.0$ sudo make install
[sudo] password for jim: 
make: *** No rule to make target `install'.  Stop.
jim@jim-laptop:~/Rakarrack/rakarrack-0.3.0$ 


```
I really hope I can get this to work

---

### Post by abhiroopb on 2009-06-08
could you please provide a link to where you got this programme from. I would like to try downloading and compiling it myself.

Its usually a simple process but if there is a small file or something missing it can go wrong.

---

### Post by oldos2er on 2009-06-08
"configure: error: C++ compiler cannot create executables"

 Run **sudo apt-get install build-essential**

---

### Post by gamblor01 on 2009-06-08
According to the output above you are missing all sorts of necessary utilities for compiling software (you're missing g++, c++, CC, xlC, and so on).   My guess is that the console.log file would support this idea as well.  The output specifically tells you to look at that file (but it will probably just tell you that you're missing these packages):

> 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
I would suggest you start with the build-essential package:

```

sudo apt-get install build-essential

```That should get you gcc and a few other very important utilities -- then try the three commands again:

```

./configure
make
sudo make install

```

---

### Post by jitup on 2009-06-08
this is where I got the taball
[http://sourceforge.net/project/showfiles.php?group_id=215888](http://sourceforge.net/project/showfiles.php?group_id=215888)

I am going to try the above codes now, then I will let you know what happens. Thank you for all your help this far

---

### Post by jitup on 2009-06-08
this is what I got when I tried to do the build essentials

```
jim@jim-laptop:~$ sudo apt-get install build-essential
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 6270kB of archives.
After this operation, 21.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com jaunty/main libstdc++6-4.3-dev 4.3.3-5ubuntu4
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main g++-4.3 4.3.3-5ubuntu4
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main g++ 4:4.3.3-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main patch 2.5.9-5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main dpkg-dev 1.14.24ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main build-essential 11.4
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.3-5ubuntu4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.3.3-1ubuntu1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-5_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.14.24ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.4_i386.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jim@jim-laptop:~$ 


```dose any one have .deb package they can send me of rakarrack 0.3.0 four ubuntu 9.04? private msg me and I'll send you my email. thanks

---

### Post by oldos2er on 2009-06-08
Do you have a working internet connection?

---

### Post by jitup on 2009-06-08
I have a working conection on my XP computer (only reason I still have windows on it) but I don't on my linux machine, because I have dialup and my provider dose not support linux,  I have Juno, so if any one knows how to get a connection using that I would be over joyed

---

### Post by oldos2er on 2009-06-08
If you have an Ubuntu LiveCD or DVD, you can install build-essential from there. You just need to enable it via Software Sources (via the System, Admininstration menus).

---

### Post by gamblor01 on 2009-06-08
> **jitup said:**
> I have a working conection on my XP computer (only reason I still have windows on it) but I don't on my linux machine, because I have dialup and my provider dose not support linux,  I have Juno, so if any one knows how to get a connection using that I would be over joyed
If you don't have a working internet connection then you can't install the build-essential package unless you use the live CD as suggested above.

In regard to using Juno, it appears that others were able to get the Linspire packages (another distro based off of Debian, much like Ubuntu) to install on Ubuntu 6.10 -- which is a REALLY old version.  My guess is that you can follow the instructions here.  Look at the last post:

[http://ubuntuforums.org/showthread.php?t=342189&highlight=Juno](http://ubuntuforums.org/showthread.php?t=342189&highlight=Juno)

---

### Post by jitup on 2009-06-09
I got it to work. I found the .deb at
[https://launchpad.net/~rzr-team/+archive/ppa/+sourcepub/488460/+listing-archive-extra]("https://launchpad.net/~rzr-team/+archive/ppa/+sourcepub/488460/+listing-archive-extra") thanks for the help):P

---

