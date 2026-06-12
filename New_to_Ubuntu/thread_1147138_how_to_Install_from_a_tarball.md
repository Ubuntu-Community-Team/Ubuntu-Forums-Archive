---
title: "how to Install from a tarball?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by chipppy on 2009-05-03
Silly question.
Where can I find a guide to learn how to install new software (a game) from something called a tarball ******.tar.gz type thing.

I am reading through Linux Format Magazine and want to install one of the games reviewed in the magazine.

Cheers
Chipppy

---

### Post by spiderbatdad on 2009-05-03
Chippy,
tarballs are just archives...zip packages. You need to extract them and see what's inside before know what tools you'll use to install. Some contain binary programs that you just run. Others have readme files with details on installing.

---

### Post by Skrynesaver on 2009-05-03
Hi Chippy,
a tar.gz file is a Tape ARchive that has been compressed with GZip.

Make a directory and copy the file into it, then, open a terminal and type the following substituting filename as apropriate
```
tar -xzf filename.tgz
```This should create a new folder in the directory, or a load of files if the archive is badly packaged.
Check for a file called README.INSTALL, INSTALL or INSTALL.Debian.
This should contain the install instructions.

HOWEVER, before that enable universe in System>admin istration>software sources, and search for the game in synaptic.  If it is present in Synaptic install from there as this way you will recieve any updates that are available for the package.

Hope this helps

---

### Post by llemm on 2009-05-03
> **chipppy said:**
> Silly question.
Where can I find a guide to learn how to install new software (a game) from something called a tarball ******.tar.gz type thing.

I am reading through Linux Format Magazine and want to install one of the games reviewed in the magazine.

Cheers
Chipppy

tar ballsalways has documentation inside 
after doing the tar xvf filename.tar.gz 
cd to the new folder 
ls | grep - readme - to look for a readme or some documentation about installing the package
if you found one
use more or gedit to open it

Most Packages has documentation on how to install it if you find none do

./configure options

eg: ./configure --prefix=/usr/local/

make
make check
make install

This will configure, build, test and install your application under /usr/local/bin or /usr/local/sbin depending on the application.

HTH

---

### Post by arochester on 2009-05-03
For general guidance look at [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) and "How to install ANYTHING in Ubuntu!" on [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by spiderbatdad on 2009-05-03
> **Skrynesaver said:**
> Hi Chippy,
a tar.gz file is a Tape ARchive that has been compressed with GZip.

Make a directory and copy the file into it, then, open a terminal and type the following substituting filename as apropriate
```
tar -xzf filename.tgz
```This should create a new folder in the directory, or a load of files if the archive is badly packaged.
Check for a file called README.INSTALL, INSTALL or INSTALL.Debian.
This should contain the install instructions.

HOWEVER, before that enable universe in System>admin istration>software sources, and search for the game in synaptic.  If it is present in Synaptic install from there as this way you will recieve any updates that are available for the package.

Hope this helps
wow. I usually just click the package to see what's inside...usually a directory. The click "extract." And the diretory is automatically created. Of course you can add as many layers of complexity as you like.

---

### Post by MrWES on 2009-05-03
> **llemm said:**
> tar ballsalways has documentation inside 
after doing the tar xvf filename.tar.gz 
cd to the new folder 
ls | grep - readme - to look for a readme or some documentation about installing the package
if you found one
use more or gedit to open it

Most Packages has documentation on how to install it if you find none do

./configure options

eg: ./configure --prefix=/usr/local/

make
make check
make install

This will configure, build, test and install your application under /usr/local/bin or /usr/local/sbin depending on the application.

HTH

I would also consider using checkinstall
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")
Especially if you plan on installing quite a bit of software from the source. Makes management a little easier. Also, if you're into the latest and greatest, you might look into Subversion;
[https://help.ubuntu.com/community/Subversion]("https://help.ubuntu.com/community/Subversion")
Makes upgrading your source packages a lot easier. I've only used it for rtorrent, it made upgrading easier.

Bill

---

### Post by Skrynesaver on 2009-05-03
Fair enough, I'm more used to the terminal, and usually find it easier, as the Perl motto goes, "There's more than one way to do it" ;)

---

### Post by chipppy on 2009-05-04
WOW!

I didnt realise that there could be somany different ways to install a game!

Anyway  thanks heaps for the assistance.  I will try different ways to see which one feels best for me (there is more then one game to be installed so I have plenty to try), after I do a little bit more reading from the various options as above.

Thanks heaps

Cheers
Chipppy

---

