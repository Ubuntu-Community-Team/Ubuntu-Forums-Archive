---
title: "Install samba 4"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by renzo-gaido on 2014-01-09
after typing ./configure I obtain the followin error:
command returned 'Build failed:  -> task failed (err #1): \n\t{task: cc_link test_1.o -> testprog}'Could not find the python development headers
I searched for a solution with google but I found nothing.
What does this mean?


I work with 64bit ubuntu 13:10
Ty

---

### Post by tfrue on 2014-01-09
To compile in Linux you have to have the libraries and tools to compile, and Ubuntu doesn't come with them. I will be of little help, since I do not know a lot about this, but you can type:```
apt-get install build-essential
```
I believe this will give you the gcc compiler and other essential building tools, but if you want other compilers like C #, then look up Linux C compilers.

Another thing to keep in mind is you will need dependencies for these compilers and build tools, so maybe a Google search for gcc dependencies for Linux, or C dependencies for linux, or even build-essential dependencies for Linux might help. Make sure that the articles and info you read are up to date at least a year or two. 

Hope this helped,
Chris

---

### Post by tfrue on 2014-01-09
Another thing to keep in mind is for ./configure to work, you have to be in the directory that has that option. If you download software from source you will have to un tar and un zip the file, then try and build the software from the directory.

Here is a website I just found that explains how to compile
[http://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/](http://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/)

This is why I generally stay away from source as long as I can, because I haven't had much luck with it, but it does work you've just got to do some research!

Good Luck,
Chris

---

### Post by renzo-gaido on 2014-01-09
if I type sudo apt-get build-essential i obtain:
build-essential is already the newest version.
The package is: samba-4.1.3.tar.gz downloaded from samba.org site ed the command ./configure is typed into the extracted folder.

---

### Post by tfrue on 2014-01-10
What are you trying to do anyway? Just install Samba? Have you tried
```
sudo apt-get install samba
```

Chris

---

### Post by renzo-gaido on 2014-01-10
if I type sudo apt-get install samba ubuntu install samba 3.6
I solved the problem in this mode:

1) Check if the universe repository is enabled.
Inspect /etc/apt/sources.list using your favourite editor with sudo which will ensure that you have the correct permissions.
sudo gedit /etc/apt/sources.list
Ensure that universe is included.

After any changes you should run this command to update your system.

sudo apt-get update

You can now install the package like this.

Install samba4
sudo apt-get install samba4
Which will install samba4 and any other packages on which it depends.

the installation is ok, now I test if work fine.

---

