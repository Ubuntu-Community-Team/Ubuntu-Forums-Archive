---
title: "How to install a Cad Program bricad_7.10.4_ia32.tar.bz2"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by SG12010 on 2010-10-28
Hi

How dose one install a Cad program downloaded as "bricad_7.10.4_ia32.tar.bz2".


[http://brlcad.org/](http://brlcad.org/)


Thanks SG

---

### Post by bance on 2010-10-28
[URL="http://brlcad.org/wiki/Documentation"]http://brlcad.org/wiki/Documentation
[/URL]

[http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL](http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL)


It helps if you read a little;)

---

### Post by SG12010 on 2010-10-29
I have read the the Documentation but I just get this error.

Every time I try and install these tar.gz they always say no such file.

Also I installed the program through archive manager which created the folder but still get bad command on terminal when trying to start the program.


Thanks SG1


gunzip brlcad-7.2.4_linux_ia64.tar.gz
gzip: brlcad-7.2.4_linux_ia64.tar.gz: No such file or directory
sgu@sgu-desktop:~$ tar -xvf brlcad-7.2.4_linux_ia64.tar
tar: brlcad-7.2.4_linux_ia64.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
sgu@sgu-desktop:~$ sudo mv usr/brlcad /usr/.
mv: cannot stat `usr/brlcad': No such file or directory









> **bance said:**
> [URL="http://brlcad.org/wiki/Documentation"]http://brlcad.org/wiki/Documentation
[/URL]

[http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL](http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL)


It helps if you read a little;)

---

### Post by SG12010 on 2010-10-29
unsolved

---

### Post by SG12010 on 2010-10-29
Helloe

I have downloaded a cad program into the download folder as bricad_7.10.4_ia32.tarbz2

How dose one install this program in terminal keeps on saying that the program dose not exist.

In terminal I thought the home directory is Desktop and the root directory.

Terminal dose not show the download program when installed in home or root.

I have tried these instructions

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
sudo mv usr/brlcad /usr/.


./configure --enable-optimized
  make
  make benchmark
  make test
  make install   # as root, e.g. sudo make install



Without any progress what so ever.



Thanks SG

---

### Post by aeiah on 2010-10-29
> **SG12010 said:**
> Helloe

I have downloaded a cad program into the download folder as bricad_7.10.4_ia32.tarbz2

How dose one install this program in terminal keeps on saying that the program dose not exist.

In terminal I thought the home directory is Desktop and the root directory.

Terminal dose not show the download program when installed in home or root.

I have tried these instructions

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
sudo mv usr/brlcad /usr/.


./configure --enable-optimized
  make
  make benchmark
  make test
  make install   # as root, e.g. sudo make install



Without any progress what so ever.



Thanks SG

where does it fail? could you provide a link to the instructions?

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
this bit unzips the archive into the current directory. your current directory, if you havent moved anywhere, will be your home dir.

sudo mv usr/brlcad /usr/.

this moves the brlcad (is it not bricad?) to /usr/

the ./configure line runs the config script. but you've just moved your bricad files over to /usr/brlcad, so you'll need to navigate there before issuing that command:
```

cd /usr/brlcad

```

but really, that isnt usually the way you compile things. usually, you dont move things into /usr/ before you've configured and compiled it. it usually gest installed with 'sudo make install', so it'd be useful if you provide the installation guide i guess.

normall what id do if i cant install it through synaptic (like in this case) is:

unpack the archive, using the file manager (just double click and extract)

look in the directory for a README file, or something to see if there's anything useful in it. if not, ill open a terminal and
```

cd foldername
./configure --enable-optimized
make
make test
sudo make install

```

note that the instructions you follow moves the files into /usr/ before doing anything with them. if this needs to be done, then all subsequent commands will have to be run with sudo infront of them (super user do).. and those rights could allow the configure / install scripts to mess up the system due to having system-wide write access. normally you'd only use sudo with the last command.. configure and make wouldnt have the power to do anything until you know that it's passed those steps without error.

---

### Post by brlcad on 2010-10-29
> **SG12010 said:**
> Helloe

I have downloaded a cad program into the download folder as bricad_7.10.4_ia32.tarbz2

How dose one install this program in terminal keeps on saying that the program dose not exist.

In terminal I thought the home directory is Desktop and the root directory.

Terminal dose not show the download program when installed in home or root.


It sounds like you are lacking a lot of basic understanding in order to install BRL-CAD.  If you're having this much trouble installing BRL-CAD, then you may continue to encounter difficulty overcoming BRL-CAD's steep learning curve.

That said, the installation instructions for both BINARY and SOURCE distributions are included in the download and is also available online here:

[http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL]("http://brlcad.svn.sourceforge.net/svnroot/brlcad/brlcad/trunk/INSTALL")


> **SG12010 said:**
> I have tried these instructions

gunzip brlcad-7.2.4_linux_ia64.tar.gz
tar -xvf brlcad-7.2.4_linux_ia64.tar
sudo mv usr/brlcad /usr/.


These are a variant of the installation instructions for a BINARY release (and the version numbers do not match what you said you downloaded.  Assuming that was just a typo, then running "/usr/brlcad/bin/mged" might work.


> **SG12010 said:**
> ./configure --enable-optimized
  make
  make benchmark
  make test
  make install   # as root, e.g. sudo make install


Those would be instructions for compiling and installing from a SOURCE distribution, which you did not indicate you downloaded.  Moreover, compiling from source is generally a bit more involved and requires a bit more installation familiarity.

Best of luck.  If you still can't get the install to work after reading the INSTALL file, then your next best option is to submit a request to have BRL-CAD packaged for Ubuntu (e.g., [https://bugs.launchpad.net/ubuntu/+bug/195558]("https://bugs.launchpad.net/ubuntu/+bug/195558")).

Cheers!
Sean

---

### Post by chaanakya_chiraag on 2010-10-29
Wouldn't the proper command be
```
sudo mv brlcad /usr
```?

---

### Post by aeiah on 2010-10-29
> **brlcad said:**
> If you're having this much trouble installing BRL-CAD, then you may continue to encounter difficulty overcoming BRL-CAD's steep learning curve.


haha, check the patronising CAD representative :)

maybe he's just come from the windows world. he could already be using BRL-CAD

---

### Post by oldos2er on 2010-10-29
What folder did you download bricad_7.10.4_ia32.tar.bz2 to? You need to be in that same folder when you run "tar zxvf bricad_7.10.4_ia32.tar.bz2" for example.

---

### Post by uRock on 2010-10-29
Duplicate threads merged. Please do not create duplicate threads.

---

### Post by brlcad on 2010-10-30
> **aeiah said:**
> haha, check the patronising CAD representative :)

maybe he's just come from the windows world. he could already be using BRL-CAD

Entirely possible but just not very likely.  The difficulties encountered are fairly common to new users.

My comments were not intended to be patronizing in the least, though.  They were merely to set expectations accordingly.

BRL-CAD is heavily designed around UNIX principles.

---

### Post by SG12010 on 2010-10-31
The folder I loaded into was Desktop and also the root directory or home folder, jus to see if that made any difference.

Thanks 


> **oldos2er said:**
> What folder did you download bricad_7.10.4_ia32.tar.bz2 to? You need to be in that same folder when you run "tar zxvf bricad_7.10.4_ia32.tar.bz2" for example.

---

