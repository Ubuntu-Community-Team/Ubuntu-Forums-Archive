---
title: "how to open and install tar gz files"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by butinoxtwo on 2010-09-03
hi there  just new to the forum i have ubuntu 10.4 installed but cant get tar files to open or install

---

### Post by valbaca on 2010-09-03
A tar file (.tar) is a single, uncompressed archive of multiple files. It's NOT like a .exe file in windows that can be run. Neither is it like a .deb file in Debian/Ubuntu that automatically runs an installer.
Tar files are usually compressed with gzip or bzip2 or lmza, these usually have the extension .tar.gz, .tgz, .tar.bz, or .tbz. These are known as "tarballs" collectively
[http://en.wikipedia.org/wiki/Tar_%28file_format%29]("http://en.wikipedia.org/wiki/Tar_%28file_format%29")
To open a tar file, you can usually just right click and "Extract here." This creates a folder with the contents inside. From the terminal you can use the following for .tar.gz or .tgz
```
tar -xfz filename.tar.gz
```The following works for .tar.bz2 or .tbz
```
tar -xfj filename.tar.bz2
```Once you have the tarball uncompressed
```
cd filename/
```to go into the directory now created by the uncompress commands.
Then read the README file found there for special instructions.
Unless the README file says otherwise, you install by running the following commands
```
sudo apt-get install build-essential
```(edit: added this line) build-essential is everything you will need to compile programs that are up to the GNU standards```
./configure
```this usually gets specific information about your computer the program will need```
make
```This compiles the program It may take a while, be patient.```
sudo make install
```Finally, this installs it to your system.

Good luck.

---

### Post by audwan on 2010-09-03
You should be able to just rightclick and chose unpack, or extract them using Archive Manager (Alt-F2 and type file-roller if you can't find it).

If your comfortable in the terminal you can type
```
tar xvfz filename.tar.gz
```

---

### Post by da burger on 2010-09-03
Hi. Can you tell us what your trying to install. Generally it's a bad idea to install tar.gz files on your system unless you really need to or are an advanced user. Secondly, and merely as a useful tip if you like using the terminal, the same command can be used for any tar archive if the file extension is correct:```
tar -xavf filename.tar.gz
```.

---

### Post by Paqman on 2010-09-03
> **da burger said:**
> Generally it's a bad idea to install tar.gz files on your system

+1 to this. Stick to getting your software from Ubuntu Software Centre, or as .deb files. Installing random stuff from tarballs can cause a lot of problems, and is a bit of a pain.

---

### Post by butinoxtwo on 2010-09-03
> **da burger said:**
> Hi. Can you tell us what your trying to install. Generally it's a bad idea to install tar.gz files on your system unless you really need to or are an advanced user. Secondly, and merely as a useful tip if you like using the terminal, the same command can be used for any tar archive if the file extension is correct:```
tar -xavf filename.tar.gz
```.

hi there thank you for your quick reply i am trying to install adobe flash update

---

### Post by jtarin on 2010-09-03
Are you wanting the browser plug-in? You can install it using the Synaptic package manager you will find in your menu under System>Administration>Synaptic Package Manager. When open just type "flash" in the search box.

---

### Post by Tracy177 on 2010-09-03
there is other way right click on the tar file scroll to extract extract it just like in windows.

then open new created folder and check up install there is alwways instruction how to install it sometimes u need to use different ways to install something

sometimes ./configure

than

make and sudo make install

---

### Post by WRDN on 2010-09-03
As others have noted, a file with the extension "tar" or "tar.X" (where X may be ".gz" or ".bz" typically). If the file contains an application, then usually, it must be built.

Others have described the commands "./configure", "make" and "make install".

I would recommend a slightly modified series of commands however:

```
./configure
```

This configures the program for your system, and ensures all required programs are installed.

```
make
```

This builds the program and provides you wish the executables you need. You can now run the program if you wish, or install it:

```
sudo checkinstall
```

The [checkinstall]("https://help.ubuntu.com/community/CheckInstall") program is useful as the application will be added to the system program database. This way, you can easily remove it using the standard removal procedures, such as using apt-get, aptitude or the Synaptic Package Manager.

---

### Post by jtarin on 2010-09-03
> **WRDN said:**
> ```
sudo checkinstall
```
The [checkinstall]("https://help.ubuntu.com/community/CheckInstall") program is useful as the application will be added to the system program database. This way, you can easily remove it using the standard removal procedures, such as using apt-get, aptitude or the Synaptic Package Manager.I highly agree. I run Slackware and as many of you know unless its a Slackware package it can be difficult to completely remove and I've always used this,

---

### Post by butinoxtwo on 2010-09-04
hi jtarin did what you said flash plug-in working thanks

---

### Post by jtarin on 2010-09-04
Your welcome.

---

### Post by mjolnar on 2013-01-30
> **valbaca said:**
> A tar file (.tar) is a single, uncompressed archive of multiple files. It's NOT like a .exe file in windows that can be run. Neither is it like a .deb file in Debian/Ubuntu that automatically runs an installer.
Tar files are usually compressed with gzip or bzip2 or lmza, these usually have the extension .tar.gz, .tgz, .tar.bz, or .tbz. These are known as "tarballs" collectively
[http://en.wikipedia.org/wiki/Tar_%28file_format%29]("http://en.wikipedia.org/wiki/Tar_%28file_format%29")
To open a tar file, you can usually just right click and "Extract here." This creates a folder with the contents inside. From the terminal you can use the following for .tar.gz or .tgz
```
tar -xfz filename.tar.gz
```The following works for .tar.bz2 or .tbz
```
tar -xfj filename.tar.bz2
```Once you have the tarball uncompressed
```
cd filename/
```to go into the directory now created by the uncompress commands.
Then read the README file found there for special instructions.
Unless the README file says otherwise, you install by running the following commands
```
sudo apt-get install build-essential
```(edit: added this line) build-essential is everything you will need to compile programs that are up to the GNU standards```
./configure
```this usually gets specific information about your computer the program will need```
make
```This compiles the program It may take a while, be patient.```
sudo make install
```Finally, this installs it to your system.

Good luck.
I can get to the file when uncompressed, but when I type ./configure I get'No such file or directory'.

---

### Post by lisati on 2013-01-30
> **mjolnar said:**
> I can get to the file when uncompressed, but when I type ./configure I get'No such file or directory'.

Old thread closed: from the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

In answer to your question, you need to run configure from the directory where it is stored.

---

