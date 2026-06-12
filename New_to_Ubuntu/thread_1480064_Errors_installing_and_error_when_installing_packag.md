---
title: "Errors installing and error when installing packages"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-05-11
**[B]I am reposting this in the beginners section.**

Errors installing and error when installing packages[/B] 			
 			 			 		   		 		 		When I did the  upgrade to 10.04 I received some error messages and a message said it  could only do a partial install.  Everything worked fine and I didn't  think much of it.  Now every time I install or uninstall a program using  Synaptic Package Manager I get this error:

                                       E:  linux-headers-2.6.31-21-generic: subprocess installed post-installation  script returned error exit status 2


[SIZE=2]I'm not sure what this is.  Does anybody have a solution?   Should I reinstall 10.04 from a disk?  I just did the upgrade from  Update Manager.[/SIZE]


[SIZE=2]The programs work if I just hit OK and bypass this error  but something is not quite right.
[/SIZE]

---

### Post by jd65pl on 2010-05-11
If you do:
```
sudo apt-get update
```
What are the errors above and below the one you have shown there?

also what is the output of
```
uname -r
```

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> If you do:
```
sudo apt-get update
```What are the errors above and below the one you have shown there?

I just did that and no errors came up

also what is the output of
```
uname -r
```

This what comes up:

2.6.32-22-generic

---

### Post by dondiego2 on 2010-05-11
I just read my reply and my first answer came up in your quote :(

But running

 sudo apt-get update

produced no errors at all.

The error pops up when I install or uninstall something from the Synaptic Package Manager.

---

### Post by jd65pl on 2010-05-11
No problems!

You are running a newer kernel so if you are having no other problems other than this it is safe to remove any trace of the old one. The command below should solve the problem.

```
sudo apt-get purge linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> No problems!

You are running a newer kernel so if you are having no other problems other than this it is safe to remove any trace of the old one. The command below should solve the problem.

```
sudo apt-get purge linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```


I ran that command and got errors.  I installed something from Synaptic Package Manager to see if it fixed it anyway and got this error

E: linux-headers-2.6.31-21-generic: subprocess installed post-installation script returned error exit status 2

Here is the output from the purge command above that I ran

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.32-21 is not installed, so not removed
Package linux-headers-2.6.32-21-generic is not installed, so not removed
Package linux-image-2.6.32-21-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-headers-2.6.31-21-generic (2.6.31-21.59) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.31-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-headers-2.6.31-21-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jd65pl on 2010-05-11
Try 
```
sudo dpkg --remove linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> Try 
```
sudo dpkg --remove linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```


It just ignores the request (all 3) and says the packages are not installed.

---

### Post by jd65pl on 2010-05-11
do
```
\ls /var/lib/dpkg/info | grep linux | grep 2.6.32.20
```
it should return a list exactly the same as the one below (except mine are for 2.6.32.21)
```
linux-headers-2.6.32-21-generic.list
linux-headers-2.6.32-21-generic.md5sums
linux-headers-2.6.32-21-generic.postinst
linux-headers-2.6.32-21.list
linux-headers-2.6.32-21.md5sums
linux-image-2.6.32-21-generic.list
linux-image-2.6.32-21-generic.md5sums
linux-image-2.6.32-21-generic.postinst
linux-image-2.6.32-21-generic.postrm
linux-image-2.6.32-21-generic.preinst
linux-image-2.6.32-21-generic.prerm
```
If the same list is returned run the following commands
```
\ls /var/lib/dpkg/info|grep linux|grep 2.6.32.20|xargs sudo rm -f
```
```
sudo apt-get update -f
```
```
sudo apt-get upgrade
```

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> do
```
\ls /var/lib/dpkg/info | grep linux | grep 2.6.32.20
```it should return a list exactly the same as the one below (except mine are for 2.6.32.21)
```
linux-headers-2.6.32-21-generic.list
linux-headers-2.6.32-21-generic.md5sums
linux-headers-2.6.32-21-generic.postinst
linux-headers-2.6.32-21.list
linux-headers-2.6.32-21.md5sums
linux-image-2.6.32-21-generic.list
linux-image-2.6.32-21-generic.md5sums
linux-image-2.6.32-21-generic.postinst
linux-image-2.6.32-21-generic.postrm
linux-image-2.6.32-21-generic.preinst
linux-image-2.6.32-21-generic.prerm]

I ran
[CODE]\ls /var/lib/dpkg/info | grep linux | grep 2.6.32.20
```and it returned nothing.  The next line was the prompt.

I ran this

```
\ls /var/lib/dpkg/info | grep linux | grep 2.6.31.21
```and I got this

carl@carl-desktop:~$ \ls /var/lib/dpkg/info | grep linux | grep 2.6.31.21
linux-headers-2.6.31-21-generic.list
linux-headers-2.6.31-21-generic.md5sums
linux-headers-2.6.31-21-generic.postinst
linux-headers-2.6.31-21.list
linux-headers-2.6.31-21.md5sums
linux-image-2.6.31-21-generic.list
linux-image-2.6.31-21-generic.md5sums
linux-image-2.6.31-21-generic.postinst
linux-image-2.6.31-21-generic.postrm
linux-image-2.6.31-21-generic.preinst
linux-image-2.6.31-21-generic.prerm
carl@carl-desktop:~$

---

### Post by jd65pl on 2010-05-11
Sorry error on my part I thought the problem was with 2.6.32.20, complete lapse in my mental ability I think!

Just run:

```
\ls /var/lib/dpkg/info|grep linux|grep 2.6.32.21|xargs sudo rm -f
```
```
sudo apt-get update -f
```
```
sudo apt-get upgrade
```

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> Sorry error on my part I thought the problem was with 2.6.32.20, complete lapse in my mental ability I think!

Just run:

```
\ls /var/lib/dpkg/info|grep linux|grep 2.6.32.21|xargs sudo rm -f
``````
sudo apt-get update -f
``````
sudo apt-get upgrade
```


Should that be 2.6.32.21 or 2.6.31.21?

---

### Post by dondiego2 on 2010-05-11
I ran exactly what you said and I still received errors after and during the upgrade.

For example

Errors were encountered while processing:
 linux-headers-2.6.31-21-generic


Which leads me to believe I still have a problem.

---

### Post by dondiego2 on 2010-05-11
> **jd65pl said:**
> No problems!

You are running a newer kernel so if you are having no other problems other than this it is safe to remove any trace of the old one. The command below should solve the problem.

```
sudo apt-get purge linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-image-2.6.32-21-generic
```


OK I figured it out.  You kept telling me the right stuff but the wrong numbers.   The issue was 2.6.31-21  not 2.6.32-21.  When I ran the purge command with 2.6.31-21 it took care of the problem.

Thanks for your help.

---

