---
title: "Installation of application"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by manojps on 2011-01-20
I have downloaded all the dependencies as well as the application files and stored  in one directory. I want to install it in 20 machines. Is there any method to install these files apart from installing these files one by one???

---

### Post by manojps on 2011-01-22
I think I have to write a shell script for this. Please help

---

### Post by Paqman on 2011-01-22
There are a few different was I know of for doing this (such as apt-cacher, setting up a local mirror, etc) but they're probably all overkill for just installing one package. Are you going to be installing other packages or updates across these 20 machines?

---

### Post by Linyx on 2011-01-22
This is also a method i normally use when i re-install my OS, however you can simply do it on many machines and you won't have to install each package one-by-one manually..

> $ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`


This will make a directory name "dpkg-repack" in home-directory.

To install these packages on another PC or reinstall these packages after a fresh install, all you have to go to this directory and use:-

sudo dpkg -i *.deb

First, this will make a back-up of all your current install packages in your home directory and once it done, you just has to copy the Back-up folder (dpkg-repack) and copy to all your machines,

After that you had just CD(change directory to that folder) and follow the last command in terminal ie "sudo dpkg -i"

---

### Post by manojps on 2011-01-22
> **Linyx said:**
> This is also a method i normally use when i re-install my OS, however you can simply do it on many machines and you won't have to install each package one-by-one manually..



First, this will make a back-up of all your current install packages in your home directory and once it done, you just has to copy the Back-up folder (dpkg-repack) and copy to all your machines,

After that you had just CD(change directory to that folder) and follow the last command in terminal ie "sudo dpkg -i"
Thank you Linyx and Paqman for your reply. The procedure works for me. Thankyou very much.:D:popcorn::popcorn:

---

