---
title: "Broken Package: nfs-kernel-server"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-11
While following an online guide to setup file sharing, I was told to enter in the following code:

```
sudo apt-get install nfs-kernel-server
```

during the installation, the kernel completely locked up and i could not even escape to tty1. I had to force-shutdown. on reboot, i now have a permanently broken package:

```
sudo /etc/init.d/nfs-kernel server stop
```

followed by:

```
sudo apt-get remove --purge nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nfs-kernel-server*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 414kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109056 files and directories currently installed.)
Removing nfs-kernel-server ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing nfs-kernel-server (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
girdy@girdy-laptop:~$ 

```

thus, the guide that was supposed to set up network file sharing has instead permanently broken it. 

I tried going into recovery mode and fixing broken packages - failed.
I tried going into TTY1 mode and running the same removal commands - failed.

am i going to have to reinstall the entire operating system to fix this simple problem or am i just doing something wrong?

thanks in advance

---

### Post by yaknowwat on 2009-05-11
It's not
apt-get remove --purge
it's 
apt-get purge

so instead you should do this command

```
sudo apt-get purge nfs-kernel-server
```

of course stop or disable it from start up before doing anything.
I've had errors like this before too no sure exactly how it was fix, wasnt a reinstall i think i just installed the application again and uninstalled it.  First try the fixed command though.

Now I remember what it was when i'd get errors like that because an install was interrupted ( someone bumping power button etc )
I'd do a reconfigure if needed
```
sudo dpkg-reconfigure -a
```

It's possible to reconfigure a single package.  Just to simplify things i put -a, for all packages.

---

### Post by TransitMan on 2009-05-11
Try using Synaptic to remove the broken package instead of command line.
I have used it to fix broken packages in the past without problem.

---

### Post by asuastrophysics on 2009-05-11
> **TransitMan said:**
> Try using Synaptic to remove the broken package instead of command line.
I have used it to fix broken packages in the past without problem.

synaptic gives the exact same outcome.

yaknowhat: I tried the following steps:

sudo dpkg-reconfigure -a

(it was a long process, took about 5 minutes)

followed by a 

sudo apt-get purge nfs-kernel-server

and got the exact same result: 
```
sudo apt-get purge nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nfs-kernel-server*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 414kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109056 files and directories currently installed.)
Removing nfs-kernel-server ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing nfs-kernel-server (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
girdy@girdy-laptop:~$ 

```

is there anything else i could try? i issued a stop command for nfs-kernel-server. is there any way that it could still be running even though i stopped it?

---

### Post by asuastrophysics on 2009-05-13
i gave up and just reinstalled the entire operating system. obviously there is no solution. 
installing packages in ubuntu needs to be more fail-safe than this. i just installed ubuntu 2 days ago and i already had to wipe everything out and start over.

but you know, that's the nature of the beast i guess. :rolleyes:

---

