---
title: "Please I want to solve the problem, the program virtualbox"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by New-usser on 2010-11-10
Hello

I have a problem when the operating system and placebo in the program virtualbox

This is the error

Failed to open a session for the virtual machine xp.
The virtual machine 'xp' has terminated unexpectedly during startup with exit code 1

The second error


Kernel driver not installed (rc =- 1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with / dev / vboxdrv. Please reinstall the kernel module by executing

'/ Etc / init.d / vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary


It was a letter

root@RrR:~# /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel module ...done.
Recompiling VirtualBox kernel module ...failed!
(Look at /var/log/vbox-install.log to find out what went wrong)


I went to the track to see the error

/var/log/vbox-install.log

/etc/init.d/vboxdrv: 382: /usr/share/virtualbox/src/vboxdrv/build_in_tmp: not found

Please I am tired of the problem

Please: (

---

### Post by SeijiSensei on 2010-11-10
Install these first:

```
sudo apt-get install build-essential dkms
```

These provide the libraries and compiler needed to build the VirtualBox "driver" (a "kernel module") from source.

---

### Post by New-usser on 2010-11-10
> **SeijiSensei said:**
> Install these first:

```
sudo apt-get install build-essential dkms
```

These provide the libraries and compiler needed to build the VirtualBox "driver" (a "kernel module") from source.

 is the latest version


root @ RoR: ~ # sudo apt-get install build-essential dkms
Building dependency tree
Reading state information ...
build-essential
dkms is the latest version


:(

---

### Post by toekneewood on 2010-11-10
What about creating the path that it thinks does not exist.  This is an ls -l from my machine.
```


twood ~ $ ls -l  /usr/share/virtualbox/src/vboxdrv
ls: cannot access /usr/share/virtualbox/src/vboxdrv: No such file or directory
twood ~ $ ls -l  /usr/share/virtualbox/src/
ls: cannot access /usr/share/virtualbox/src/: No such file or directory
twood ~ $ ls -l  /usr/share/virtualbox/
total 28
drwxr-xr-x 2 root root 12288 2010-10-06 09:39 nls
-rw-r--r-- 1 root root  1821 2010-09-15 10:51 VBox.png
-rwxr-xr-x 1 root root  2270 2010-09-15 10:28 VBox.sh
-rwxr-xr-x 1 root root  4210 2010-09-15 10:51 VBoxSysInfo.sh

```

Looks like it is missing **src/vboxdrv**

---

### Post by New-usser on 2010-11-10
> **toekneewood said:**
> I your Ubuntu machine (physical PC) gets a kernel update the you have to run the following command so recompile the Virtual box kernel
```

sudo /etc/init.d/vboxdrv setup

```
It should not prompt you to do anything.  Once it has finished you should be able to power on the VM's

woops, sorry just spotted you have done this :-)

root@RoR:~# sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel module ...done.
Recompiling VirtualBox kernel module ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

/etc/init.d/vboxdrv: 382: /usr/share/virtualbox/src/vboxdrv/build_in_tmp: not found < 

:(

---

### Post by toekneewood on 2010-11-10
I have also spotted this on the web
```

sudo usermod -aG vboxusers your_username

```
You will need to log off and on again after doing the command.
[http://www.uluga.ubuntuforums.org/showthread.php?t=1422522]("http://www.uluga.ubuntuforums.org/showthread.php?t=1422522")

---

### Post by SeijiSensei on 2010-11-10
Let's make sure we're all starting from square one.

Are you installing the VirtualBox-OSE package from the Ubuntu repositories or the proprietary Debian/Ubuntu package from virtualbox.org?  You should be using one of these to maintain consistency with the rest of your installation.  I generally just add the VirtualBox repository to apt, so my installation is kept up-to-date.

Follow the instructions for "Debian-based distributions" at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

I ask this because it's clear from the error that the installer is looking for a directory you don't have.  Do you have a /usr/share/virtualbox tree with /usr/share/virtualbox/src/vboxdrv? If so, try creating the missing directory manually with "mkdir /usr/share/virtualbox/src/vboxdrv/build_as_tmp" as root, then run "/etc/init.d/vboxdrv setup" again.

Also if you're already running as root, you don't need sudo.  I don't know whether that would matter or not.

If you still can't get it to work, I suggest you run "apt-get purge virtualbox-3.2" and start over.

---

### Post by New-usser on 2010-11-10
> **toekneewood said:**
> I have also spotted this on the web
```

sudo usermod -aG vboxusers your_username

```
You will need to log off and on again after doing the command.
[http://www.uluga.ubuntuforums.org/showthread.php?t=1422522]("http://www.uluga.ubuntuforums.org/showthread.php?t=1422522")

did not solve the problem

:(

---

### Post by New-usser on 2010-11-10
The problem came, System Update : (

Is it possible to give me a copy of an older program from 3.2

Could work with me: (

---

### Post by New-usser on 2010-11-10
Where are you!

:(

---

### Post by SeijiSensei on 2010-11-10
If you're asking that of me, we do have other things to do in life, you know.

Reread my last posting.  You need to follow the instructions at virtualbox.org and install the version of VB that matches your distribution.

---

### Post by toekneewood on 2010-11-10
Did you have a go at the following & post #7 in this thread
```

mkdir -p /usr/share/virtualbox/src/vboxdrv/build_in_tmp

```

---

