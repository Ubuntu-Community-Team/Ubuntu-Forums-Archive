---
title: "are there programs to automate install?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by slixz85 on 2010-12-15
hi i noticed all the different types of files .sh .bin .tar.gz rpm deb etc etc etc etc and just wondering if there is a tool that works on some or most all to automate the install make it easier, as in gui since i am newer to linux?

---

### Post by 3rdalbum on 2010-12-15
If you are a beginner, stick to Ubuntu Software Center and third-party repositories.

---

### Post by Frogs Hair on 2010-12-15
I found this helpful when I started . [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by kalos on 2010-12-15
The single program for installing software is the Ubuntu Software Centre (software-center). Make sure you enable all software repositories:
[LIST=1]
[*]Run Ubuntu Software Centre
[*]Edit > Software Sources...
[*]Check the first four check boxes (main, universe, restricted, multiverse).
[/LIST]
That will ensure that it can find more software.

If you find anything that you want to install, search for it first in software-center. If it's not there, then see if the software provider has an apt package server. If they do, you can add that server to software-center's list and when you search again. Read more at [Repositories/Ubuntu - Third-Party Software Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party Software Tab"). (For example, Google offers some of their software through [their apt package server]("http://www.google.com/linuxrepositories/apt.html").)

If you still can't install it, then there are still some simple options.

.deb
These are debian package files and are (generally) compatible with Ubuntu. You can double click on them to install.

rpm
These are Red Hat packages. You can use Alien to convert them to deb files. See [AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto").

.sh .bin
These are simple executables and will probably walk you through the install process. Just run them from a terminal.

.tar.gz
You can right click on these and select "Extract Here" to install to the current location. However, if they are "source tarballs", then you will have to compile them. This is an involved process. For more info, see [CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by sgosnell on 2010-12-15
Short answer: use only the software center or Synaptic package manager.  

Slightly longer answer: stick with .deb files, and you can just double-click on a downloaded .deb file to install it.

For packages in other formats, the short answer is "no".  There are no programs that I know of that will automatically install other type files.  There is no standard format, and the installation method required varies.

---

### Post by slixz85 on 2010-12-16
thanks for all your answers. i would like to use as many repositories as i can but how can you guess if one is gonna be bad or not when you install your software? because i have had to add the ppa for certain programs and what not and errors always happen with authenication to install new software. so since being new to linux as well, could someone please tell me the terminal command to save a log of these errors to post here or something. thanks

---

### Post by Paqman on 2010-12-16
PPAs are, by definition, going to be a less trusted source of software then the official repos. It really depends on the PPA though. For example, some projects have an official PPA for their releases. On the other hand, some PPAs are just what the name suggests; somebody's Personal Package Archive.

The simplest way to add a PPA (that will also take care of your authentication issues) is to use the command line:
```
sudo add-apt-repository ppa:<repository-name>
```

---

### Post by sgosnell on 2010-12-16
Authentication errors for PPAs are not really a problem.  They're just a warning that you don't have the gpg key for the repository.  The packages will still install without any problems.  Each PPA should have a verification key available, and it's not hard to install it, but it's not essential.

---

