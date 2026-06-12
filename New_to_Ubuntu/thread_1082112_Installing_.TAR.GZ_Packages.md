---
title: "Installing .TAR.GZ Packages"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Joomla12 on 2009-02-27
I'm still very new to Ubuntu and I know some of the basics. I know how to install Debian files with no problems but I need help compiling the files .tar.gz document. Thanks in advance.

---

### Post by smani on 2009-02-27
tar.gz files usually contain source code. The general procedure for compiling a program from source is
```

./configure
make
make install
#or
sudo make install
```
but each source package always should include some sort ot README or INSTALL file which will give you more instructions. One of the most difficult tasks is getting the dependencies. Generally it is preferable to search if a deb package does not already exist somewhere (maybe in the main repositories, or in a personal package archive (PPA)). If you are trying to compile a newer version of a program that already has a deb package for an older version, the command
```
sudo apt-get build-dep <progname>
```
will likely fetch most of the dependencies for you.

---

### Post by taurus on 2009-02-27
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Hospadar on 2009-02-27
Just so you know, a tar.gz file is not necesarily a package that contains software, it's just a compression format like .zip or .rar that is often used for source code.  There's typically a pretty standard way to build and install what's in them, but you should generally refer to their own documentation or the readme that is probably contained inside of them.

Familiarizing yourself with the general methods to build software as per taurus' link would be a good starting place though.

Also, often noobs (I used to do this all the time) find something floating about online and want to install it, you should check the ubunut repositories (i.e. System->Administration->Synaptic) and see if the software is already there in a nice easy to install pre-packaged format.  You could also check websites like "getdeb" (just google it), they have a ton of nicely pre-built packages that you can just download and double click to install, if you want something that's not in the repositories or you are looking for a newer version, that can be a really easy way to get it.

---

### Post by stchman on 2009-02-27
> **Joomla12 said:**
> I'm still very new to Ubuntu and I know some of the basics. I know how to install Debian files with no problems but I need help compiling the files .tar.gz document. Thanks in advance.

I have been using Ubuntu now for over two years and have only needed to build from source twice (drivers).  There is probably something in the repos that will do the job.

Any rate, there is usually a readme in the archive that tells you how to build the application.

---

### Post by Joomla12 on 2009-02-28
Thank you everyone for the replys. My main proble was compiling the source. 

I'll try these methods when I boot back into Intrepid.

---

### Post by banerjeerupak on 2009-03-01
I want to install Opera web browser in my Ubunutu. I have been able to locate the .tar.gz file. But i'm still unable to find it in any repository. Can you suggest where to get it from.

---

### Post by gjoellee on 2009-03-01
> **banerjeerupak said:**
> I want to install Opera web browser in my Ubunutu. I have been able to locate the .tar.gz file. But i'm still unable to find it in any repository. Can you suggest where to get it from.

Opera has a DEB available, just install the DEB instead. Download it here: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

