---
title: "Problems with John the Ripper"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by CarlCromer on 2009-10-01
I need a little help. I am switching from window to Ubuntu and I am trying
to install John the Ripper. The first thing that I found odd was the name
of the file. "john-1.7.3.4.tar.tar". Tar.tar I have worked with unix for
five years. Who would name a file like this. Everyone know that when you
use tar it applies the suffix. 
When I extract the tar ball I get a John<version> directory and three 
sub-directories: run,doc, and src. Most tutorials I have seen just say go
to the run directory and use the "john" executable. I don't have that in 
run directory. here are the contents of my run directory:
-rw------- 1 carl carl 341064 2005-12-16 09:20 all.chr
-rw------- 1 carl carl 232158 2005-12-16 09:20 alnum.chr
-rw------- 1 carl carl 131549 2005-12-16 09:20 alpha.chr
-rw------- 1 carl carl  40391 2005-12-16 09:20 digits.chr
-rw------- 1 carl carl  19988 2009-09-09 00:02 john.conf
-rw------- 1 carl carl 215982 2005-12-16 09:20 lanman.chr
-rwx------ 1 carl carl    785 2002-04-10 09:13 mailer
-rw------- 1 carl carl  22346 2005-12-16 09:29 password.lst
So naturally I thought that I would have to compile the source code
to get those executes. so I went to the src directory and this is what 
is there:
AFS_fmt.c   config.h    idle.h        memory.c     recovery.c  tty.h
alpha.h     cracker.c   inc.c         memory.h     recovery.h  unafs.c
alpha.S     cracker.h   inc.h         mips32.h     rpp.c       unique.c
batch.c     crc32.c     john.asm      mips64.h     rpp.h       unshadow.c
batch.h     crc32.h     john.c        misc.c       rules.c     vax.h
bench.c     DES_bs_b.c  john.com      misc.h       rules.h     wordlist.c
bench.h     DES_bs.c    list.c        nonstd.c     sboxes.c    wordlist.h
best.c      DES_bs.h    list.h        options.c    signals.c   x86-64.h
best.sh     DES_fmt.c   LM_fmt.c      options.h    signals.h   x86-64.S
BF_fmt.c    DES_std.c   loader.c      params.c     single.c    x86-any.h
BF_std.c    DES_std.h   loader.h      params.h     single.h    x86-mmx.h
BF_std.h    detect.c    logger.c      pa-risc.h    sparc32.h   x86-mmx.S
BSDI_fmt.c  external.c  logger.h      path.c       sparc64.h   x86.S
charset.c   external.h  Makefile      path.h       sparc.S     x86-sse.h
charset.h   formats.c   Makefile.dep  ppc32alt.h   sparc.sh    x86-sse.S
common.c    formats.h   math.c        ppc32.h      status.c
common.h    getopt.c    math.h        ppc64alt.h   status.h
compiler.c  getopt.h    MD5_fmt.c     ppc64.h      symlink.c
compiler.h  ia64.h      MD5_std.c     ppc-alti.c   times.h
config.c    idle.c      MD5_std.h     ppc-alti.pl  tty.c
So I tried make Makefile and I get this error:
[EMAIL="carl@carl-desktop:~/john_ripper/john-1.7.3.4/src$"]carl@carl-desktop:~/john_ripper/john-1.7.3.4/src$[/EMAIL] ./make Makefile
bash: ./make: No such file or directory
Any help with this would be greatly appreciated. Thank you.

---

### Post by boblemur on 2009-10-01
hey firstly, is there any particular reason why you are trying to compile this from source??

you can simply get JTR by running:
```
sudo aptitude install john
```

or going to synaptic and searching for john. as JTR is already in the ubuntu repositories.


if you do need to compile from source then your problem is. you dont not need to specify ./make as make is a program which is actually in 
```
$ which make
/usr/bin/make

```

so you simply need to run:
```
make
```

and then usually 
```
make install
```

if this fails try installing build essentials.
```
sudo aptitude install build-essential
```

hope this helps :)

---

### Post by CarlCromer on 2009-10-02
Hey thanks for the quick reponse. Again I am new to working with Ubuntu, not new to unix. 
 
When I did the first command "sudo aptitude install john" I got the message "Couldn't find any package whose name or description matched "john" "
 
Then when I tried the command "sudo aptitude install build-essential". I got this message "No candidate version found for build-essential"
 
In both errors it says "Need to get 0B of archives" I don't know what this is. I check a couple of sites and didn't get a definitive answer.

---

### Post by gali98 on 2009-10-02
You might need to run
sudo apt-get update
before. 
so 
sudo apt-get update
sudo apt-get install john
should get you every thing.
I am on ubuntu Jaunty, and john is a package in the repository.
Kory

---

### Post by kanikilu on 2009-10-02
JTR is definitely in the repos: [http://packages.ubuntu.com/jaunty/john](http://packages.ubuntu.com/jaunty/john) - it might be that the servers are getting hammered right now (there are several threads this morning about it). Maybe try again later or choose another mirror in Software Sources?

---

### Post by boblemur on 2009-10-02
ok so, this is basically what you are wanting to see:

```
:~$ sudo aptitude install john
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  john john-data{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 831kB of archives. After unpacking 1,561kB will be used.
Do you want to continue? [Y/n/?] 
```

and this is where im getting it from apparently:

```
http://au.archive.ubuntu.com/ubuntu/pool/main/j/john/john-data_1.7.2-3ubuntu2_all.deb
http://au.archive.ubuntu.com/ubuntu/pool/main/j/john/john_1.7.2-3ubuntu2_amd64.deb
```

so your next step is to try going to:
```
System > Administration > Software Sources
```

and 1) make sure your multi-verse and universe are enabled ([]("http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html"))

and then 2) pick a different server, again under: 

```
System > Administration > Software Sources
```

and under the box that says "Download From:" select other and then select from the list one that seems appropriate (ie. one thats in the same state/country as you, or a provider you know is fast).

then retry the top command. i would be very surprised if this fails but if it does let us know :)

---

