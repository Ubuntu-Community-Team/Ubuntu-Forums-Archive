---
title: "mutliple images with an impossible dpkg problem"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by openick on 2011-01-27
Hello

I have 10.04 LTS in a netbook for almost 6 months now, some problems developed that forced low graphics mode, updated the versions two or three times with the result that there are six images between versions 32.21 to 35.23.   

There is a persistent dpkg problem, I have tried different work arouds, different solutions but the dpkg issue invariably blocks updates, removal of packages, fixes and even removal of redundant images.

Is there a way to remove older kernels from any other prompt other than the terminal root prompt? Perhaps from a maintenance prompt or grub prompt? 

And is there a way to copy dpkg related files from that prompt ?

It would be possible to update the present installation and upgrade to 10.10 only after fixing the dpkg issue. 

Thank you.

---

### Post by regala on 2011-01-27
> **openick said:**
> Hello

I have 10.04 LTS in a netbook for almost 6 months now, some problems developed that forced low graphics mode, updated the versions two or three times with the result that there are six images between versions 32.21 to 35.23.   

There is a persistent dpkg problem, I have tried different work arouds, different solutions but the dpkg issue invariably blocks updates, removal of packages, fixes and even removal of redundant images.

Is there a way to remove older kernels from any other prompt other than the terminal root prompt? Perhaps from a maintenance prompt or grub prompt? 

And is there a way to copy dpkg related files from that prompt ?

It would be possible to update the present installation and upgrade to 10.10 only after fixing the dpkg issue. 

Thank you.

what are the exact and various error messages you get when using aptitude/apt/dpkg ? (sorry, crystal balls are down for today)

---

### Post by openick on 2011-01-27
> **regala said:**
> what are the exact and various error messages you get when using aptitude/apt/dpkg ? (sorry, crystal balls are down for today)

The following happens during update, removal, new package installation:

$ sudo apt-get install colorname
[sudo] password for uma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  colorname
0 upgraded, 1 newly installed, 0 to remove and 100 not upgraded.
Need to get 22.5kB of archives.
After this operation, 143kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe colorname all 0.4+dfsg.1-1 [22.5kB]
Fetched 22.5kB in 3s (6,576B/s)    
Selecting previously deselected package colorname.
(Reading database ... 
dpkg: warning: files list file for package `gdebi' missing, assuming package has no files currently installed.
(Reading database ... 65%

(The terminal hangs at this point)

When I run apt-get update, it proceeds well, all the updates piled up during the last two months are downloaded one by one, the installation proceeds and then when it comes to this Reading database point, it again hangs at 65%

I located threads with the gdebi error, there are some solutions given, tried every solution, even tried 

[PHP]sudo e2fsck -f -y -v /dev/sda1[/PHP]

(booting the O/S from a DVD) and after all this it is back to the same problem.

Tried removing excessive images, the same issue with gdebi.

Thank you.

---

