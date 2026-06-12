---
title: "partimage installation problem"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by tim1970 on 2009-04-26
I am trying to install partimage, so that I can image my new installation.  When I type the command sudo apt-get install partimage i get the following error message...

Package partimage is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package partimage has no installation candidate


What am I doing wrong?  I also did sudo apt-get update before trying to install.

ps  all repositories are enabled from package manager and I am using 9.04

Thanks in advance

Tim

---

### Post by Didius Falco on 2009-04-26
Hi Tim,

Are you running 32 or 64 bit? I just installed it into a 32 bit 9.04 installation with no problem.

---

### Post by tim1970 on 2009-04-26
64 bit.  Sorry I forgot to include that bit of information. 


Tim

---

### Post by fdrake on 2009-04-26
manual installation:
1.download from [this link]("http://sourceforge.net/project/downloading.php?group_id=6212&filename=partimage-0.6.7.tar.bz2&a=97886537")
2.extract the content on your desktop
3.cd ~/Desktop/partimage*
4../configure && make && make install
5.(to run)sudo partimage

synaptic installation 
see the link of  [ www.psychocats.net/ubuntu/partimage ]("http://www.psychocats.net/ubuntu/partimage")for help
see also on that page how to add sources on the repos.
if you just need to make an image of a partition the use the live-cd and boot the pc with it.

---

### Post by tim1970 on 2009-04-26
> **fdrake said:**
> manual installation:
1.download from [this link]("http://sourceforge.net/project/downloading.php?group_id=6212&filename=partimage-0.6.7.tar.bz2&a=97886537")
2.extract the content on your desktop
3.cd ~/Desktop/partimage*
4../configure && make && make install
5.(to run)sudo partimage

synaptic installation 
see the link of  [ www.psychocats.net/ubuntu/partimage ]("http://www.psychocats.net/ubuntu/partimage")for help
see also on that page how to add sources on the repos.
if you just need to make an image of a partition the use the live-cd and boot the pc with it.

I tried this, put when I got to step 4 I got the following message

bash: ../configure: No such file or directory

I was in the following directory when I typed the command:
/home/elvis/Desktop/partimage-0.6.7

---

### Post by fdrake on 2009-04-26
> bash: ../configure: No such file or directory

Note Carefully 
I wrote 
```
./configure
```(1 point)

you wrote```
../configure
```(2 points)

---

### Post by tim1970 on 2009-04-26
You are correct.  But I saw the period after the 4 and it looked like this

..

when I ran the correct command it ran for a few seconds then I got this message:

configure: error: *** bzip2 library (libbz2) not found or too old: version 1.0.0 or more recent is need


Tim

---

### Post by tim1970 on 2009-04-26
Here is a screenshot of what I have installed now...

---

### Post by fdrake on 2009-04-26
select(check) to install the package libbz2-dev. Yours is unchecked

before you repeate the configure option again type this commands, just to make sure you don't miss any other more libraries; when asked press "y" and "enter" to install the packages:

```
sudo apt-get install libbz2-dev libnewt-dev libcurl4-openssl-dev
```

---

### Post by tim1970 on 2009-04-27
After installing the additional packages I tried to compile, and got the following message...

make[2]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/po'
Making all in src
make[2]: Entering directory `/home/elvis/Desktop/partimage-0.6.7/src'
Making all in shared
make[3]: Entering directory `/home/elvis/Desktop/partimage-0.6.7/src/shared'
source='common.cpp' object='common.o' libtool=no \
	DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
	g++ -DHAVE_CONFIG_H -DLOCALEDIR=\"/usr/local/share/locale\" -D_REENTRANT -D_FILE_OFFSET_BITS=64 -I. -I../.. -I../.. -I../../src/client -I../../src/shared -I/usr/include/slang  -Wno-deprecated -I/usr/include/openssl -Wall   -c -o common.o common.cpp
../../depcomp: line 566: exec: g++: not found
make[3]: *** [common.o] Error 127
make[3]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/src/shared'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7'
make: *** [all] Error 2

---

### Post by Didius Falco on 2009-04-27
Here is a link to a pre-compiled version for 64 bit:

[http://ftp.debian.org/debian/pool/main/p/partimage/partimage_0.6.7-2_amd64.deb](http://ftp.debian.org/debian/pool/main/p/partimage/partimage_0.6.7-2_amd64.deb)

That version is the latest available.

I hope that gets you working.

Just so you know, you can't use it from the partition you are going to image. Any partition you are going to image has to be unmounted. The only partition that should be mounted is the one you are backing up to, if are using a partition for backups.

You would probably be better off downloading a copy of the System Rescue CD, which will include it. The developers of Partimage are also invloved in the System Rescue CD:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by kansasnoob on 2009-04-27
Somehow (going back to your original post) I don't think you got the full repo download. I had that happen recently and have no idea why:confused:

Maybe the servers were overloaded? I dunno.

Anyway go to synaptic and click on Settings > Repositories (yeah I know you've been there already), but double check.

[ATTACH]111485[/ATTACH]

[ATTACH]111486[/ATTACH]

[ATTACH]111487[/ATTACH]

Of course my Third Party is modified and you don't need that but make sure partner is ticked.

Then look at what server you're downloading from! try a different one and click on reload!

My point is that partimage should be in the repos! If you click on search in synaptic and type partimage it should be there or you have something broken!

---

### Post by tim1970 on 2009-04-27
Thanks for the help.  I will try this pre-compiled version.   

I knew if I was restoring that I could not restore to a mounted drive, I was unaware though, that I could not backup from a mounted drive.

My best bet after all may be to use the systemrescue cd you talked about, or I can always boot Ubuntu 9.04 from the livecd, and then install the 32 bit version of partimage.

Thanks for all of the help.


Tim

---

### Post by fdrake on 2009-04-27
> 
After installing the additional packages I tried to compile, and got the following message...

make[2]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/po'
Making all in src
make[2]: Entering directory `/home/elvis/Desktop/partimage-0.6.7/src'
Making all in shared
make[3]: Entering directory `/home/elvis/Desktop/partimage-0.6.7/src/shared'
source='common.cpp' object='common.o' libtool=no \
DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
g++ -DHAVE_CONFIG_H -DLOCALEDIR=\"/usr/local/share/locale\" -D_REENTRANT -D_FILE_OFFSET_BITS=64 -I. -I../.. -I../.. -I../../src/client -I../../src/shared -I/usr/include/slang -Wno-deprecated -I/usr/include/openssl -Wall -c -o common.o common.cpp
../../depcomp: line 566: exec: g++: not found
make[3]: *** [common.o] Error 127
make[3]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/src/shared'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elvis/Desktop/partimage-0.6.7'
make: *** [all] Error 2
```
sudo apt-get install build-essential

```

---

### Post by Didius Falco on 2009-04-28
> **tim1970 said:**
> Thanks for the help.  I will try this pre-compiled version.   

I knew if I was restoring that I could not restore to a mounted drive, I was unaware though, that I could not backup from a mounted drive.

My best bet after all may be to use the systemrescue cd you talked about, or I can always boot Ubuntu 9.04 from the livecd, and then install the 32 bit version of partimage.

Thanks for all of the help.


Tim

Here is a really good tutorial you can print out or just google for in the Live CD. It walks you through it all, including installing it to the CD.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

It'll be worth all the trouble once you have that safe, warm feeling of a good backup. :)

---

