---
title: "Problems Creating a Makefile/ Using ./configure Command"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-07-26
I just downloaded the songbird .tar.gz file (*gasp* horrors!) and untarred it, but when I tried to ./configure it gave me the error message:
bash: ./configure: No such file or directory. 
The instructions I am using said that I should just continue and make it if it gave me an error during the configuring step, but when I entered make it said:
make: *** No targets specified and no makefile found.  Stop.
I'm in the proper directory so I don't know what is wrong. Anybody got an idea?

---

### Post by lswb on 2009-07-26
I see you said that you are in the proper directory yet the error messages you report indicate otherwise. what does "ls configure" and "ls make" return while you are in this directory, also the command "pwd"

Also, look for a text file named README or INSTALL or other likely looking name, there may be directions specific to the tarball you downloaded.

---

### Post by Commisar Jimp on 2009-07-26
I wasn't sure if the comands were is configure/make with a capital i or lowercase L (I'm new at this) so I tried both ways and is with lowercase I but all I got was: 
bash: is: command not found
pwd showed me:
/home/me/dtars/Songbird
Which I'm pretty sure is the right directory, it is the directory made when I uncompressed the original .tar.gz file.

---

### Post by lswb on 2009-07-26
That is "ls" with a lower case L 

I did a little googling and found that at least some of the tarballs for songbird include the binaries, so configure & make would not be required, the songbird executable is included in the tarball. If this is the case you, you should be able to run songbird from the directory it is in with  ./Songbird or ./songbird

You may want to check this link,

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

It has a link to a .deb package you can install with dpkg and also has a script that will do the installation for you.

---

### Post by Commisar Jimp on 2009-07-26
> **lswb said:**
> That is "ls" with a lower case L 

I did a little googling and found that at least some of the tarballs for songbird include the binaries, so configure & make would not be required, the songbird executable is included in the tarball. If this is the case you, you should be able to run songbird from the directory it is in with  ./Songbird or ./songbird

You may want to check this link,

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

It has a link to a .deb package you can install with dpkg and also has a script that will do the installation for you.
That's done it, thanks so much for the help.

---

