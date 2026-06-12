---
title: "Another wireless disaster"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by papajack on 2007-03-12
Still a noob at linux, and very much considering switching back to the other side. I find linux is difficult to learn but not impossible. Obviuosly there is something very appealing about linux because there would be no other excuse for this self inflicting pain. This wireless issue has got me so frustrated I could scream. After all the countless howto's, forums, blogs, wiki's and so forth, it is very hard to find instructions that are consistant or that apply to my particular situation. 

I have a edgy eft set up, clean install. I have a belkin wireless g desktop card part# fsd7000. I thought this card used the broadcom chipset but when I run lspci I get 02:00.0 Ethernet controller: Belkin Unkown device 700f (rev20). I follwowed theses steps but can only get so far before I recieve an error.

1. create directory in home folder called Ndiswrapper
2. download Ndiswrapper from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)
3. Move tar file into Ndiswrapper directory and run: make distclean
5. Type: make install KSRC=/usr/bin/kernels/

I get an error message after step 5 that states: Can't find kernel build files in /usr/bin/kernels/;
give the pathe to kernel build directory with KSRC=<path> argument to make

This card does nto use the BCM driver I find so popular in threads. I pulled the driver for this card off the install cd under the XP directory: BLKWGDv7.inf

Can anyone help with this issue. I thought it would be a simple matter of installing ndiswrapper, installing the driver, configuring the setup and thats it.

---

### Post by rjfioravanti on 2007-03-12
I think it is looking for linux headers and not finding them

try 

sudo apt-get install build-essential


I'm not entirely sure that downloads linux headers, (im not even entirely sure that is your problem =) ) but i think it is worth double checking you have that and trying to figure out if you do in fact have the linux headers

---

### Post by rjfioravanti on 2007-03-12
your problem may also be you missed a 'configure' step

usually when you download source code you have to type 

```

./configure

```

before doing the make install

are there install instructions included with the source code?  do they include any steps that whatever web tutorial you were following did not include?

---

### Post by papajack on 2007-03-12
rjfioravanti,
this is was taken from the INSTALL file for Ndiswrapper:

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install

---

### Post by rjfioravanti on 2007-03-12
ok did you check out the stuff about downloading build-essential and having linux headers? 

I installed ndiswrapper a few weeks ago, and I think I got an error at first

Just copy the error exactly as your terminal spits it out, and do a google search on it. People are running in with so many problems using ndiswrapper you are bound to find what you are looking for

---

### Post by papajack on 2007-03-12
Is it possible that the kernel needs to be updated or the headers need to match the kernel? I'm not sure what all this means or how to do it, at this point I'm willing to try anything.

---

### Post by papajack on 2007-03-12
I just finished installing build-essential. Does this install the linux headers as well. After installing build-essential I ran through the steps again and got the same error: Can't find kernel build files in usr/bin/kernels/

---

### Post by rjfioravanti on 2007-03-12
looks like there is some good information here

[http://www.linuxquestions.org/questions/showthread.php?t=428731](http://www.linuxquestions.org/questions/showthread.php?t=428731)

let me know how it goes

---

### Post by papajack on 2007-03-12
I have to run to work here shortly but I will let you know how everything goes. Thanks for all your help.

---

