---
title: "moving Ubuntu programs"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by gavinUK on 2009-10-19
Hi
I have Ubuntu installed on one machine connected to the internet, with no problems downloading programs. How do I go about copying these downloaded programs and installing them on a stand alone machine with Ubuntu on it, most likely via a flash drive.

cheers

Gavin

---

### Post by MelDJ on 2009-10-19
copy the .deb file into your pendrive? but i think there are issues. i will check

---

### Post by howefield on 2009-10-19
> **gavinUK said:**
> How do I go about copying these downloaded programs and installing them on a stand alone machine with Ubuntu on it, most likely via a flash drive.

Post 26 in this thread is one way.

[http://ubuntuforums.org/showthread.php?t=1292058&page=3](http://ubuntuforums.org/showthread.php?t=1292058&page=3)

---

### Post by philinux on 2009-10-19
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by Bölvaður on 2009-10-19
> **howefield said:**
> Post 26 in this thread is one way.

[http://ubuntuforums.org/showthread.php?t=1292058&page=3](http://ubuntuforums.org/showthread.php?t=1292058&page=3)

the standalone computer doesnt connect to internet so this woudnt work -.-

the content of that file that would be created is a script with something like this
```
 #!/bin/sh
wget -c http://is.archive.ubuntu.com/ubuntu/pool/universe/6/6tunnel/6tunnel_0.11rc2-2_amd64.deb
```it doesnt make sense using it as the script just gets a .deb


all .deb files you've downloaded when using apt-get or synaptic are in /var/cache/apt/archives

so just go there to find your package. to delete all the files there run: sudo apt-get clean


if you can find .deb file anywhere on like on getdeb.com it would be the best way.

it really depends what you are going to do, if it is a program that has alot of dependancies and you get it with synaptic you'll have to list down all the packages that it is dependent of and copy and install them before you install the main package on the standalone computer


[http://keryxproject.org/](http://keryxproject.org/) seems to be the best way if you are going to get the .deb from the repos. but the simplest way is to go to getdeb.com and get the .deb you want.

---

### Post by mikechant on 2009-10-19
Have a look at the 'aptoncd' package.

This allows you to make a repository on a CD.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by howefield on 2009-10-19
> **Bölvaður said:**
> the standalone computer doesnt connect to internet so this woudnt work -.-

I am sure there may be better ways, (philinux has posted one) but it would work.

---

### Post by gavinUK on 2009-10-19
Hi everyone

thanks for the info, I'll look into all the methods mentioned, I think the Keryxproject that you linked phil looks the most slick way of doing things, but I guess it would also be useful to learn how to do it manually using the .deb files if I'm feeling adventurous.

cheers

Gav

---

