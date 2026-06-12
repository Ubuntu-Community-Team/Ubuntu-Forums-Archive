---
title: "install g++ on Ubuntu 8.1"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by rajeshwari2413 on 2009-03-09
I have tried many things. But nothing is working . Pl. do help me.


sudo apt-get install build-essential
[sudo] password for ganesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
ganesh@ubuntu:~$ 

==============================================

sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for build-essential
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

================================================

ganesh@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Reading package lists... Done

==========================I have only the following in /etc/apt/sources.list file.
>
> Should I add some more?
>
> Pl. do help me.
>
> I am trying to install g++ in ubuntu and I am unable to.
>
> main restricted
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
>
> I have only these three lines.
>
> All others have been commented out.
=====

Pl. do help me.

Thanks

---

### Post by silent contender on 2009-03-09
Do you mean gcc (the GNU C/C++ compiler)?  If that's it, run
```

gcc

```

---

### Post by taurus on 2009-03-09
Not sure what happens to your /etc/apt/sources.list but you need to edit it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Remove those those lines in there.  Then, paste these new repos to it.

```

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```
Save it.  Then run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

