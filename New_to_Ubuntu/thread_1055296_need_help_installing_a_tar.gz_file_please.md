---
title: "need help installing a tar.gz file please"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by kapi on 2009-01-30
Am in the throws of trying to install uniconverter so as to extract ai files but only have a tar file, is there a standard process that is to be used when dealing with a tar file. Have looked at numerous forums and still none the wiser.

Thanks

Kapi

---

### Post by smothpocket on 2009-01-30
open a terminal and type ```
tar -xzvf yourfile.tar.gz
```

your file is an archive and that will extract the files into a folder

if you need more information on tar and it's flags type ```
man tar
``` in the terminal

From there based on your description you may have to compile the program yourself.

---

### Post by taurus on 2009-01-30
Open a terminal and change to the directory where the .tar.gz is.  Then, unpack it.

```
cd ~/Desktop
tar xvzf filename.tar.gz
```
That would create a new directory so you need to change to that new directory and have a look at either README or INSTALL.

---

### Post by Hospadar on 2009-01-30
Are you looking for "uniconvert_o_r", the vector graphics translator?
that's available in the repositories, install "python-uniconvertor" from synaptic or at the command line ```
sudo apt-get install python-uniconvertor
```

If it's something else alltoghether, perhaps this:

Generally, for programs written in C/C++:
make sure you have your compilers installed and whatnot```
sudo apt-get install build-essential
```
unpack the tar file (let's say you saved it to your desktop) and move into the new directory```
tar -xzvf ~/Desktop/<name of the file>.tar.gz
ls
cd <the name of the newly unpacked directory>
```
build and install```
make
sudo make install
```
You might want to use checkinstall, it will replace the "make install", it makes a deb package that can be easily uninstalled in synaptic, in which case, replace "sudo make install" with ```
sudo apt-get install checkinstall
sudo checkinstall
```

There's a couple things here:
A tar.gz file is not necesarily installed that way.  tar.gz is just a type of compression, like zip or rar, that could contain any kind of files.  It is just commonly used for source code because it compresses better than zip, and is an open standard, unlike rar or a few others.

So you should look for a readme inside the archive and see what it tells you to do.  The package may depend on other libraries you will need to install (generally install from synaptic the libwhatever-dev, this contains the header files you need to compile software.  It may not even be C/C++ source code at all, it could be python or something else.

---

### Post by rgb96 on 2009-01-30
Yeah. Usually the README or the INSTALL files will show you how to install, but if they don't, a common combination of commands is:

```
sudo ./configure
sudo make
sudo make check
sudo make install
```

---

### Post by kapi on 2009-01-30
Thanks fore replying, I have extracted the file from the tar file to the desk top ( i just right clicked and cose extract here)

whats next - I did try the way you suggested but kept geting no file exists

Any help would be very appreciated

thanks

---

### Post by kapi on 2009-01-30
Thanks Hospadar,

I have the uni convertor installed I take it it should work automatically when i try to import an ai file.

or do i access the program somehow?

kapi

---

### Post by Nepherte on 2009-01-30
> **rgb96 said:**
> Yeah. Usually the README or the INSTALL files will show you how to install, but if they don't, a common combination of commands is:

```
sudo ./configure
sudo make
sudo make check
sudo make install
```
There's no need to use sudo for the first three commands. They don't require admin privileges.

---

