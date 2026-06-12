---
title: "Question about ndiswrapper installation"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by kamaboko on 2007-03-04
I have been reading the installation instructions at ndiswrapper.sourceforge.net, and I want to make sure I understand this correctly.  I have to install the build-essentials, right?  And in order to do that, I need a connection to the Inet, right?  Hard line.  Is there NO other way?  

Thanks,
K

---

### Post by chimerical_brio on 2007-03-04
I'm not sure if it's on the install disk for Ubuntu, but if you have access to another computer that can connect to the net, point your browser to [http://packages.ubuntu.com/edgy/devel/build-essential.en.html](http://packages.ubuntu.com/edgy/devel/build-essential.en.html) and download the file, transfer it to your Ubuntu box, and install it using make.

---

### Post by kamaboko on 2007-03-04
Thanks for the file link.  I haven't been able to find anything on google for how to install them though.  Everything I've come across says, "sudo apt-get...."  I'm assuming this refers to getting them off the net, rather than downloading them to one's computer and then installing them from there.

---

### Post by chili555 on 2007-03-04
From a terminal:```
sudo dpkg -i <pkg_to_install>.deb
```

---

### Post by kamaboko on 2007-03-04
OK. I downloaded a package that reads: build-essential_11.3.tar.gz.

Am I to install it as follows?: sudo dpkg -i build-essential_11.3.tar.gz.deb

And Ubuntu knows where to throw all of this stuff?

---

### Post by mathaeus on 2007-03-04
> **kamaboko said:**
> Thanks for the file link.  I haven't been able to find anything on google for how to install them though.  Everything I've come across says, "sudo apt-get...."  I'm assuming this refers to getting them off the net, rather than downloading them to one's computer and then installing them from there.

The "sudo apt-get" is how you would go and download a pre-set package from a repository on the net. Here is the link where I found the installation information for ndiswrapper:

 [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

While this has worked for me with my Gateway laptop running Mandriva,  I have hit a snag with Ubuntu.  I am waiting to find out what some of the messages I get (device and driver load fine, but OS still doesn't see the built-in device to complete the setup) when working with final set-up.  Could be that no one else is working with the same model laptop / built-in card (driver for mine is bcmwl5).

Hope this helps you,
Mathaeus

---

### Post by chili555 on 2007-03-04
The post above points to a .deb file. I didn't know you had a tar.gz.

I would suggest getting the .deb from the Ubuntu repository and not the tar.gz from who knows where. Open a terminal and issue a command:
```
wget -c http://ftp.ale.org/pub/mirrors/ubuntu/pool/main/b/build-essential/build-essential_11.3_i386.deb
```

Then you will have a .deb you can install as I described. And, yes, Ubuntu knows where to throw all this stuff!

Post back if you get stuck.

---

### Post by aysiu on 2007-03-04
*ndiswrapper* is on the Ubuntu CDs--both the Alternate CD and the Desktop CD. You do not need an internet connection to install it.

Just type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by incubus on 2007-03-04
> **aysiu said:**
> *ndiswrapper* is on the Ubuntu CDs--both the Alternate CD and the Desktop CD. You do not need an internet connection to install it.

Just type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

That's true, aysiu, but beware that the official ubuntu version is relatively old.  In many cases it won't work (it didn't for me).  It may be worth the shot.

Back to build-essential, though, I'm pretty sure there are other dependencies.  I'll try to check here.

incubus

---

### Post by aysiu on 2007-03-04
Well, *build-essential* is also on the Ubuntu CDs. Is that an old version as well?

---

### Post by incubus on 2007-03-04
I'm running Feisty right now, but here's some output:
```

$ apt-cache show build-essential |grep Depends
Depends: libc6-dev | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)

```

So it seems build-essential will also ask you to get
```

libc6 gcc g++ make dpkg-dev

```

incubus

---

### Post by aysiu on 2007-03-04
Well, unless you need a more up-to-date version of *build-essential*, you can get it and all its dependencies with these commands and no internet connection: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

