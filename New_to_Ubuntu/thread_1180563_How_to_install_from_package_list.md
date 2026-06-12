---
title: "How to install from package list?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by wooly on 2009-06-07
Before I wiped out Ubuntu 7.10 and installed 9.04 on my son's computer, I ran:
```
sudo dpkg --get-selections>installed_package_list
```
and it generated a list of installed packages that looks like this:
```
acpi						install
acpi-support					install
acpid						install
adduser						install
...etc.
```

Now I want to install all the packages on that list.

I tried this:
```
sudo dpkg --set-selections<installed_package_list[
```
... but it doesn't install them.

Is there a way to install from that list?
Thanks for any advice!

---

### Post by rickycodie on 2009-06-07
this is not elegant at all, but here goes.

copy the results from you first command into text editor, and use sudo apt-get install with the resulting packages pasted on the end.

---

### Post by wooly on 2009-06-07
Thanks, rickycodie.

I tried your suggestion but the shell seemed to lock up when fed 1200 install commands strung together!

Afer googling some more, I found out that after the 
```
dpkg --set-selections < loaded-apps.txt
```
command, I should have called:
```
dselect
```
So after installing dselect I was able to re-install all the packages.

It's running now, and the output like:
```
Get:50 http://us.archive.ubuntu.com jaunty/main openjdk-6-jre-lib 6b14-1.4.1-0ubuntu7 [4770kB]
```
...looks to me like it's installing the jackalope packages, not the old ones. 

Along with setting up a separate /home partition, the dpkg package list seems like an almost painless way to do a major upgrade.

---

