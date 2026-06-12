---
title: "Installing QQ for linux"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Falc7 on 2011-04-30
I am trying to install 32bit QQ for linux on 64 bit Kubuntu.

I get some error messages though:
```
jamie@jamie-Inspiron-N5010:~/Downloads$ sudo dpkg -i --force-architecture linuxqq_v1.0.2-beta1_i386.deb
[sudo] password for jamie: 
dpkg: error processing linuxqq_v1.0.2-beta1_i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 7 package 'linuxqq:i386':
 error in Version string 'v1.0.2-beta1': version number does not start with a digit
Errors were encountered while processing:
 linuxqq_v1.0.2-beta1_i386.deb
jamie@jamie-Inspiron-N5010:~/Downloads$ 


```

---

### Post by user333 on 2011-04-30
Do you have ia32-libs installed?

---

### Post by Falc7 on 2011-04-30
yep

---

### Post by Falc7 on 2011-05-06
bump

---

### Post by Falc7 on 2011-05-22
anyone?
I could install is on 10.10

---

### Post by smilehoe on 2011-05-23
Extract the linuxqq_v1.0.2-beta1_i386.deb package. Then go to DEBIAN/control. Open the control file with a text editor and remove the letter v in the 7th row, it should now read "Version: 1.0.2-beta1"

Then you'd have to package the extracted folder back into a deb. In terminal, type 
```
dpkg-deb --build linuxqq_v1.0.2-beta1_i386
sudo dpkg --force-all -i linuxqq_v1.0.2-beta1_i386.deb
```

---

### Post by Falc7 on 2011-05-25
I did this
```
ar vx linuxqq_v1.0.2-beta1_i386.deb
```

Then I right clicked and extracted control.tar.gz
Opened the Control text file, took out the V

And then

```
jamie@jamie-Inspiron-N5010:~/Downloads/New Folder$ dpkg-deb --build linuxqq_v1.0.2-beta1_i386
dpkg-deb: error: failed to open package info file `linuxqq_v1.0.2-beta1_i386/DEBIAN/control' for reading: No such file or directory
```

I don't see a DEBIAN/control folder anywhere though, i think maybe I am doing the extracting process incorrectly

---

### Post by Falc7 on 2011-05-31
bump

---

### Post by Falc7 on 2011-06-04
I made some progress, but i am still stuck

```
jamie@jamie-Inspiron-N5010:~/Downloads/New Folder$ sudo dpkg --force-all -i linuxqq_v1.0.2-beta1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 141633 files and directories currently installed.)
Preparing to replace linuxqq:i386 1.0.2-beta1 (using linuxqq_v1.0.2-beta1_i386.deb) ...
Unpacking replacement linuxqq:i386 ...
dpkg: dependency problems prevent configuration of linuxqq:i386:
 linuxqq:i386 depends on libc6.
 linuxqq:i386 depends on libcairo2.
 linuxqq:i386 depends on libglib2.0-0.
 linuxqq:i386 depends on libgtk2.0-0.
 linuxqq:i386 depends on libpango1.0-0.
dpkg: error processing linuxqq:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linuxqq:i386

```

I checked on synaptic, and i have those packages

---

### Post by SynonM on 2012-01-29
[IMG]http://img600.imageshack.us/img600/3715/cran29012012183835.png[/IMG]
I just extracted the QQ file and executed it as a stand alone. It works however there is a problem with it.

The program seems to function by itself.

[IMG]http://img4.imageshack.us/img4/6863/cran29012012183857.png[/IMG]

Just extract the .deb file with archive.

Then go into the usr file. 

Run the executable file.

You'll see that it opens and works etc...

[IMG]http://img252.imageshack.us/img252/1951/cran29012012183918.png[/IMG]

However, I think you may need to manual open a port that supports it.

I could be wrong, and it may not work like that.

---

### Post by SynonM on 2012-01-29
What I did was...

1. Extract the LinuxQQ .deb (whatever version) with archive manager
2. sudo into file manager (usually it's nautilus or thunar)
i.e. ```
sudo nautilus
``` 
or
```
sudo thunar 
```
or
```
sudo dolphin-browser
```

3. Copy the /usr/ file that you find in the exctracted folders to the beginning of your file system @  " / "

Your done.

Login in logout or use a reset command in terminal and your done.

However I still don't know how to sign in.

This tutorial is useless until I find out.:popcorn:

I believe Tencent has updated their login requirements, but I haven't checked to see if the Macintosh standalone still works with Macintosh computers.

They are very similar to the linux QQ. 

However if it doesn't work, I don't understand why Tencent still offers this version of QQ.

---

### Post by More or Less on 2012-04-23
dpkg: error processing linuxqq_v1.0.2-beta1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linuxqq_v1.0.2-beta1_i386.deb

Can't get QQ installed :mad:

---

### Post by alazyrabbit on 2012-09-28
You don't have to use ar, use dpkg-deb instead, because it's easier.

Here is the detail solution:

[http://liangsun.org/linux/resolve-error-version-number-does-not-start-with-digit/]("http://liangsun.org/linux/resolve-error-version-number-does-not-start-with-digit/")

---

### Post by josephmills on 2012-09-28
Just a thougt but have you ever used debtree ? it is a program that makes a list (or picture) of all dependency's that are located in a package. 

Example 

```
debtree linuxqq_v1.0.2-beta1_i386.deb | dot -Tpng >~/Desktop/linuxqq_v1.0.2-beta1_i386.png
```

Also this mnight help you 

[https://launchpad.net/~qtqq](https://launchpad.net/~qtqq)

---

