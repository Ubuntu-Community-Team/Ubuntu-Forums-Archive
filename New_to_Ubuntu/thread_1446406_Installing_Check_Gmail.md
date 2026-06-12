---
title: "Installing Check Gmail"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-04
While installing checkgmail i got a dependency error,how to rectify it.?

---

### Post by dineshs on 2010-04-04
Try installing via synaptic package manager or try```
sudo apt-get install checkgmail

```

---

### Post by sikander3786 on 2010-04-04
> **getyourkarthick said:**
> While installing checkgmail i got a dependency error,how to rectify it.?

The best way around is already posted in the above post.

Just posting to make a note that try to install software through apt-get or synaptic because it automatically solves dependencies and the software get updates from Ubuntu servers.

For software that are not present in repositories you will have to install the missing packages manually most of which are available at

packages.debian.org

or

packages.ubuntu.com

Hope it helps in future.

Sikander.

---

### Post by @rizz on 2010-04-04
Hi there,

[COLOR=Red]** try a k before the checkgmail i.e.  kchekgmail**[/COLOR]

```
$ sudo apt-get install kcheckgmail
```

---

### Post by karthick87 on 2010-04-04
> **@rizz said:**
> Hi there,

[COLOR=Red]** try a k before the checkgmail i.e.  kchekgmail**[/COLOR]

```
$ sudo apt-get install kcheckgmail
```


what is kcheckgmail?

---

### Post by @rizz on 2010-04-04
KCheckgmail is a systray application which checks checks gmail accounts for new mail!!!

[http://kcheckgmail.sourceforge.net/](http://kcheckgmail.sourceforge.net/)

---

### Post by sikander3786 on 2010-04-04
```

sudo apt-get install checkgmail

```

It installs the software pretty easily.

While kcheckgmail might be the Kubuntu's gmail package.

---

### Post by @rizz on 2010-04-04
Yes it is for KDE but also works on gnome and has better features(eats more space though!!!)

 and Sikander you are right 

apt-get install checkgmail is working just fine but if it in case it doesnt we can use that as an alternative

cheers

---

### Post by karthick87 on 2010-04-05
> **@rizz said:**
> KCheckgmail is a systray application which checks checks gmail accounts for new mail!!!

[http://kcheckgmail.sourceforge.net/](http://kcheckgmail.sourceforge.net/)

I have installed kcheckgmail,but its not working properly..When ever i set my password it automatically resets to someother password..

---

### Post by @rizz on 2010-04-05
Strange!!!

 Is it also havinga similar dependency error.....?

 may be we should try this before installing.....
```

$ sudo apt-get autoremove checkgmail

$ sudo apt-get autoremove kcheckgmail

$ sudo apt-get update

```

and then go for 

```
sudo apt-get install checkgmail
```

Hope this works!!!

---

### Post by karthick87 on 2010-04-05
```
karthick@Learners-desktop:~$ sudo apt-get install checkgmail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
  libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
  libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-simple-perl
The following NEW packages will be installed:
  checkgmail libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
  libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
  libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-simple-perl
0 upgraded, 12 newly installed, 0 to remove and 182 not upgraded.
Need to get 429kB of archives.
After this operation, 2101kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/universe libgtk2-trayicon-perl 0.06-1 [19.4kB]
Get:2 http://archive.ubuntu.com jaunty/universe libcrypt-ssleay-perl 0.57-1 [57.2kB]
Get:3 http://archive.ubuntu.com jaunty/main libxml-namespacesupport-perl 1.09-3 [15.3kB]
Get:4 http://archive.ubuntu.com jaunty/main libxml-sax-perl 0.16+dfsg-3 [83.4kB]
Get:5 http://archive.ubuntu.com jaunty/main libxml-sax-expat-perl 0.40-1 [12.5kB]
Get:6 http://archive.ubuntu.com jaunty/main libxml-simple-perl 2.18-1 [68.7kB]
Get:7 http://archive.ubuntu.com jaunty/main libcrypt-blowfish-perl 2.10-1build2 [22.1kB]
Err http://archive.ubuntu.com jaunty/universe libgtk2-sexy-perl 0.04-1
  403 Forbidden
Get:8 http://archive.ubuntu.com jaunty/universe checkgmail 1.13+svn37-1 [68.4kB]
Get:9 http://archive.ubuntu.com jaunty/universe libemail-mime-encodings-perl 1.311-3 [6072B]
Get:10 http://archive.ubuntu.com jaunty/universe libcrypt-simple-perl 0.06-4 [9004B]
Err http://archive.ubuntu.com jaunty/universe libsexymm2 0.1.9-3
  403 Forbidden
Fetched 362kB in 0s (1633kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/libg/libgtk2-sexy-perl/libgtk2-sexy-perl_0.04-1_i386.deb  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsexymm/libsexymm2_0.1.9-3_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by @rizz on 2010-04-05
Well,

 its seems that u are not able to access the  online repositories "UNIVERSE"

Go to system->adimintration->Software source and check on the Ubuntu Software tab if the community maintained repositories (universe) is checked or not........ if not please check it.

and it it is checked


check with your repositories /etc/apt/source.list

 if required add the link for the universe repositories manually to the source.list file 

add the following lines if missing(if any)

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe 

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe

deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe 

deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe 

But be very carefull plzzz

and be sure to use the sudo command

once all that is taken care of

reopen the terminal

```

$ sudo apt-get source checkgmail 
$ sudo apt-get install checkgmail

```

---

