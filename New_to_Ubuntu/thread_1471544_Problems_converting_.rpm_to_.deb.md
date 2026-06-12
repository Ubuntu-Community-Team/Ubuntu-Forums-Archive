---
title: "Problems converting .rpm to .deb"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by burnin5619 on 2010-05-03
Hey everyone,

This will be my official first post here on the forums and I really need your help with this annoying problem I have.

Throughout the semester, I've been trying to get Petite Chez Scheme installed on my 64-bit Ubuntu setup. It's for a computer science class I'm taking. 

First, I downloaded the .rpm files from the website provided for the class ([www.scheme.com/download](www.scheme.com/download)). I was told by my AI that I should be able to use the alien command to convert the .rpm package into a .deb file for install, but everytime I attempt to do this I get an error message.

We tried this at the beginning of the year and realized that it was because I was running a 64-bit install trying to run the 32-bit version of scheme. I suppose this made sense, but now even with the 64-bit versions on the website that were recently added, I still can't get things to work.

First I tried using the PetiteChezScheme-8.0-1.x86_64.rpm file

jordan@ubuntu:~/Downloads$ sudo alien -d PetiteChezScheme-8.0-1.x86_64.rpm 
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
error: incorrect format: unknown tag
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
Warning: Skipping conversion of scripts in package PetiteChezScheme: postinst
Warning: Use the --scripts parameter to include the scripts.
warning: PetiteChezScheme-8.0-1.x86_64.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
chown: cannot access `PetiteChezScheme-8.0//usr/lib/csv8.0/a6le/petite.heap': No such file or directory
failed chowning /usr/lib/csv8.0/a6le/petite.heap to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 6.

Then my AI told me that for some reason, the *.src.rpm file is the one to use, so I attempt it with that one. Here's what I get, ending with the .deb file being created:

jordan@ubuntu:~/Downloads$ sudo alien -d PetiteChezScheme-8.0-1-a6le.src.rpm 
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
error: incorrect format: unknown tag
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
warning: PetiteChezScheme-8.0-1-a6le.src.rpm: Header V4 DSA signature: NOKEY, key ID 0aaf293b
petitechezscheme_8.0-2_amd64.deb generated

I attempt to install with the .deb file but it doesn't work. I guess that's not too surprising with all the other errors it spits out when trying to convert the file.

Anybody have any sort of advice on what's going on or something else I can try to get this working? You'd be helping not only me, but the few other Ubuntu users in the department too that have been having to use windows to run this instead. Really is the main thing keeping me from totally moving to Ubuntu.

Thanks!

---

### Post by Cowboybebop79 on 2010-05-03
Just had a quick look at the the site for chez Scheme. I,m not an expert in rpm to deb conversions although I had to do this with a canon printer filter before however have you considered building the software from source the last section of the download site has instructions for building the program from a tarball and there is a guide on compiling programs in Ubuntu here [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo"). I'm not saying that it will be any easier but you may have more success than with alien worth a try :neutral:

---

### Post by oldos2er on 2010-05-03
Have you tried compiling the source code?

---

### Post by Troublegum on 2010-05-03
The source is available on that site. I tried to install that software in a Virtual Machine. I tried it with alien and tried to install it from source. Did not work for me.
```

nam@vm-lucid64:~/Desktop$ wget http://www.scheme.com/download/pcsv8.0-a6le.tar.gz
nam@vm-lucid64:~/Desktop$ tar -xzf pcsv8.0-a6le.tar.gz
nam@vm-lucid64:~/Desktop$ cd csv8.0/custom
nam@vm-lucid64:~/Desktop/csv8.0/custom$ ./configure
nam@vm-lucid64:~/Desktop/csv8.0/custom$ sudo make install
if [ yes = no ]; then if [ ! -f ./scheme ]; then /bin/rm -f ./scheme; ln -s ../bin/a6le/scheme ./scheme; fi; fi
if [ ! -f ./petite ]; then /bin/rm -f ./petite; ln -s ./scheme ./petite; fi
/bin/rm -f ./scheme
echo "const char *S_date_stamp = \"`date +%m%d%Y%H%M%S`\";" > datestamp.c
gcc -m64 -rdynamic -o ./scheme datestamp.c ../boot/a6le/kernel.o ../boot/a6le/custom.o   -lm -ldl -lncurses -lrt
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status
make[2]: *** [scheme] Error 1
make[1]: *** [buildpetite] Error 2
make: *** [install] Error 2
nam@vm-lucid64:~/Desktop/csv8.0/custom$ 

```

---

### Post by burnin5619 on 2010-05-03
Went ahead and tried compiling it from source like mentioned and I got the same error as Troublegum..

Not sure if this will be any help, but this is a write-up another former student I believe wrote to help with installs. It's a bit dated, but maybe theres something in there that I'm not catching that could help solve the problem

> Advice from Ray about how to run SWL and Petite under Ubuntu
linux.

This works on Ubuntu 8.10/9.04/9.10, and may work on other
distributions with slight mods (not really sure about how Fedora
packages ncurses these days and whatnot).

Here we go.

Installing Petite Chez Scheme itself is rather trivial:

Make sure you have libncurses installed:

sudo apt-get install ncurses-base ncurses-bin ncurses-term


Download the linux .rpm file
<http://www.scheme.com/download/PetiteChezScheme-7.4d-1.i386.rpm>for
Petite Chez Scheme, open a terminal, cd to the download directory and
run:

sudo alien *chez_scheme_rpm_file*

(this will likely be named PetiteChezScheme-*version*.rpm)


This will create a .deb from the rpm with the same filename (caps may
be different). Install this using gdebi or alternatively:

sudo dpkg -i *new_chez_scheme_deb*


Type petite at console to run

THIS WILL NOT WORK AT FIRST, however. The system will grumble at you
about libtinfo.so.5 not being found. This is because the version of
curses Ubuntu ships with incorporates this functionality into
libncurses.so.5. The fix would then be to run:

sudo ln -s /lib/libncurses.so.5 /usr/lib/libtinfo.so.5

This will create a symlink called libtinfo.so.5 which redirects to the
libncurses file. All should be well with the CLI stuff/interpreter
now.

====================================================================


Now, we need to install SWL. DO NOT UNDER ANY CIRCUMSTANCES USE THE
.RPM INSTALLER. It is improperly packaged, and does not contain the
binary applications. Download the
.tar.gz<http://www.scheme.com/download/swl1.0d-src.tar.gz>and move to
the download directory. Using your preferred archiver, extract the
files into a new folder. This can be accomplished graphically, but you
can also do:

tar xvf swl1.0d-src.tar.gz


or whatever your filename is.

In the terminal, cd into the new directory (likely swl1.0d) and do:

sudo make install


This will copy all files to where they need to be.

Once again, however, we are in trouble with some external libs. You
need to install tk8.5 and symlink some more stuff. Once again, in
terminal:

sudo apt-get install tk8.5


It will likely ask you if you REALLY want to install this, type y and
hit enter.

Once this is done, do the following:

sudo ln -s /usr/lib/libtk8.5.so.0 /usr/lib/libtk8.5.so


sudo ln -s /usr/lib/libtcl8.5.so.0 /usr/lib/libtcl8.5.so


These two commands are NECESSARY. Otherwise, SWL will whine about
libtk8.5.so and libtcl8.5.so not being present, while proceeding to
not run at all. It's just cool like that.

Now, just type *swl *in terminal / at the alt+F2 dialog to see that
beautiful, beautiful REPL. On Ubuntu. Natively.

Bamshizzle.

Hope this helps at least one Linux-nerd out in the future.

- Ray, resident linux pseudo-guru.

---

### Post by Mazin on 2010-12-03
I love digging up old threads, but there is now a 64-bit Ubuntu package of Petite Chez Scheme available to download at 

[http://notes.ericjiang.com/posts/97](http://notes.ericjiang.com/posts/97)

If you're distrustful of third-party packages, it was built by downloading the provided object files of Petite, linking them, and generating the deb using checkinstall.

This is one of the higher ranked pages for "ubuntu chez scheme", so I thought I'd leave that here.

---

