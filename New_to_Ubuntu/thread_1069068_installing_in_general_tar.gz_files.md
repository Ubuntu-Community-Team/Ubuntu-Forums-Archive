---
title: "installing in general tar.gz files"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by dyyyy on 2009-02-13
hi 
i'm a very new ubuntu user and i just want to know how to install stuff,
i'm used to windows where i can double click and a wizard does it all..
and here when i have a .tar.gz file how do i install it on ubuntu
fon instance i downloaded songbird, how do i use it.

thank you

---

### Post by halitech on 2009-02-13
it depends on the file. Some are just used to compress files and you just run the program where ever you extract it. others you would run ./configure, make, make install, some need to be run as sudo.

There should be a readme file for instructions.

---

### Post by BDNiner on 2009-02-13
Every application should come with a readme file inside the tar.gz file with instructions on how to install it. But the first thing you would need to install is the package build-essential
```

sudo apt-get install build-essential

```
this contains the neccesary programs that you will need to compile the code that is in the tar.gz archive

---

### Post by BDNiner on 2009-02-13
A good practice since you just came from windows would be to look for deb files. there are songbirds debs located at this site:

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by bodhi.zazen on 2009-02-13
First, you should probably use the repositories first, before installing from source. The Ubuntu repositories are quite large and using the repos has a number of advantages.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

See also :

[https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html)

==========

If you really wish to install from source, there are several ways to do this.

The "*.tar" is an archive, like a zip file. You extract it and read the README or look on the home page where you obtained the package.

In general you install build-essential

```
sudo apt-get install build-essential
```

Then you ./configure, make, and and make install ...

cd into the directory you extracted from teh tar

./configure --prefix=/usr/local

make

sudo make install

Any error messages will need to be resolved, A majority are missing dependencies, or additional packages that must also be insalled, typically the -dev" package (which contains the headers)

========

With that brief into , tell us what you are trying to install and we can give more detailed instructions.

---

### Post by dyyyy on 2009-02-13
ok so i understand that .tar.gz, is a compressed folder,
it can contain programs, if it does normally it contains a readme.txt to explain how to run the program
a simpler way is to download a .deb file wich installs automatically the program (like windows setup)
thank you all for ur responses,it is clear for me now
(should i close the thread in some way?)

---

### Post by bodhi.zazen on 2009-02-13
Nope, just keep reading and learning. ask questions if you get stuck.

---

