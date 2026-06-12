---
title: "linux header kernel problems - help needed"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by jase17uk on 2011-02-16
Hi,
 
Asking same question from my earlier post... 
 
I seem cannot install anything due to kernel problems, tried to install vmware but it returns an error that it cannot find linux headers 2.6.32.22-x1-64  after looking at the net nothing helps so I gave up on it and went for virtualbox but now I have same problem! When trying to load it after installation... it returns an error that it cannot find same kernel at the source! 
 
It seems that this kernel is missing or I dont know what is the problem because when typing in uname -r it returns correct kernel version is used!
 
Please help!
 
Thanks in advance
 
Jase

---

### Post by shunan on 2011-02-16
How are you trying to install, via the Software Center or from source...

try these

```
sudo apt-get update
sudo dpkg --configure -a
```

Give a bit of details of the exact errors...

---

### Post by jase17uk on 2011-02-16
The error with VMware is:
 
E: Unable to locate package linux-headers-2.6.32.22-x1-64
E: Couldnt find any package by regex 'linux-headers-2.6.32.22-x1-64'
 
 
The error with VirtualBox is:
 
opening /proc/modules: No such file or directory
Warning: the vboxdrv kernel module is not loaded. Either there is no module available for the current kernel (2.6.32.22-x1-64) or it failed to load. Please recomplie the kernel module and install it by 
 
sudo /etc/init.d/vboxdrv setup
 
you will not be able to start VMs until this problem is fixed.
Failed to open the X11 display!
 
after typing sudo /etc/init.d/vboxdrv setup 
 
I get this error:
 
Trying to register the VirtualBox kernel modules using DKMS
Error! Your kernel headers for kernel 2.6.32.22-x1-64 cannot be found at /lib/modules/2.6.32.22-x1-64/build or /lib/modules/2.6.32.22-x1-64/source
 
I hope this helps?
 
Tried to enter the commands you mentioned... the last command didnt do anything?
 
Thanks

---

### Post by jase17uk on 2011-02-16
Also checking for that kernel in the modules directories... it seems it didnt exist so how can I combile/install that kernel if this is the problem?
 
Thanks

---

### Post by JKyleOKC on 2011-02-16
Open Synaptic and search for "linux-header" which should get you a whole list of header packages. At least one of them will be the one you need, although you may have to widen the "Package" column by placing the mouse pointer on the vertical line in the header row and dragging it to the right, in order to see the entire package names.

The check box for that header package will probably be empty; click it and select "installation" and you may get a popup window that says another package is also needed. If so, click the "mark" button. Then apply to download the header package(s).

If you have the DKMS package installed, it will automatically run and build the required vbox modules for you. If not, then follow the instructions in the error message -- but it's worth while to install the DKMS package also, which will make everything automatic at future kernel upgrades.

---

### Post by jase17uk on 2011-02-16
is it possible to do it via terminal? as I am running an ubuntu 10.10 server

---

### Post by shunan on 2011-02-16
to search for available linux images in the apt-cache

```
apt-cache search linux-header
```

To install you can try in the terminal

```
sudo apt-get install linux-header-x.x.x-xx
```

where x stand for the version!

or type

```
sudo apt-get install linux-header-
```

and press tab twice to see possible options

---

### Post by pastalavista on 2011-02-16
> **jase17uk said:**
> is it possible to do it via terminal? as I am running an ubuntu 10.10 server

```
sudo apt-get install linux-headers-2.6.32.22-x1-64
```

---

### Post by shunan on 2011-02-16
thanks, pastalavista... i missed a 's' there...

---

### Post by jase17uk on 2011-02-16
still same problem... it just unable to locate linux-headers package  same for it is unable to locate linux-headers-2.6.32.22-x1-64 too. 
 
[EMAIL="root@actioae1"]root@actioae1[/EMAIL]:~# sudo apt-get install linux-headers-2.6.32.22-x1-64
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-2.6.32.22-x1-64
E: Couldn't find any package by regex 'linux-headers-2.6.32.22-x1-64
[EMAIL="root@actioae1"]root@actioae1[/EMAIL]:~#
 
 
Thats the error i keep getting.... it is a mini virtual server from memset datacentre perhaps it is the problem?
 
I could give one of you experts the root access to see what's the exactly the problem?
 
Thanks
 
J

---

### Post by pastalavista on 2011-02-16
After a change to the kernel, a reboot is usually called for. If that's a problem because of the server, you could try ```
 sudo updatedb && sudo apt-get update && sudo apt-get upgrade
```

edit: forget that. You need to check the mini virtual whatever site for a ppa or deb file of the package and/or dependencies

---

### Post by JKyleOKC on 2011-02-16
Try this: ```
sudo apt-get install linux-headers-`uname -r`
```Copy and paste it if you can, else note that those "single quote" characters are really the "grave" character that's to the left of the "1" key on my keyboard, and it's essential that they not get changed to either single or double quotes.

If this still gives the error message, then the program you are attempting to compile is simply incompatible with the kernel that your server is running. Using the command "uname -r" will return the version number of the running kernel so you can compare it with the makefile for the compilation.

---

### Post by jase17uk on 2011-02-17
Hi,
 
Thanks JKyleOKC,
 
Tried the command you had given me, it still gives same error that is unable to find it.
 
Probably you are right the kernel it is running is incompatible.
 
I have left it to someone who is more versed in Ubuntu, he is going to have a look and see what he can do.
 
Will post here of the results of his investigation.
 
Meanwhile, thanks guys for helping.
 
Cheers

---

