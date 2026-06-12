---
title: "lirc 0.8.6 not loading snapstream"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by outleradam on 2010-01-31
I can't find my snapstream driver in lirc 0.8.6.  It  was present in 0.8.4 but Now I only ghave the option of the ATI/NVidia/X10 I & II RF Remote.   

Ok, so it's the same lirc_atiusb driver but now I've got a problem.  The remote is not porting output to irw.

I can't find a usbcore.ko on my system.  How do I go about recompiling usbcore.ko or making it load?

---

### Post by Methuselah on 2010-01-31
lsmod | grep usbcore

Running that in a terminal will produce a line of output if the module is already loaded.

To load it yourself do:
sudo modprobe usbcore

You can add it to /etc/modules to have it load automatically at boot.

I can't help you directly with the lirc stuff.

---

### Post by outleradam on 2010-01-31
```
root@XBMCLive:~# lsmod | grep usbcore
root@XBMCLive:~# sudo modprobe usbcore
FATAL: Module usbcore not found.
root@XBMCLive:~# 

```I recompiled my kernel using the following:

```
sudo apt-get install wget
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7/linux-headers-2.6.32-02063207_2.6.32-02063207_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7/linux-headers-2.6.32-02063207-generic_2.6.32-02063207_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7/linux-image-2.6.32-02063207-generic_2.6.32-02063207_i386.deb
sudo dpkg -i linux-headers-2.6.32-02063207_2.6.32-02063207_all.deb linux-headers-2.6.32-02063207-generic_2.6.32-02063207_i386.deb linux-image-2.6.32-02063207-generic_2.6.32-02063207_i386.deb
```then to recompile lirc
```
apt-get install dialog
wget http://downloads.sourceforge.net/project/lirc/LIRC/0.8.6/lirc-0.8.6.tar.bz2
tar xvf lirc-0.8.6.tar.bz2
cd lirc-0.8.6
./setup.sh
sudo make
sudo make install

```it didn't set up usbcore.

I should see this:
lsmod |grep lirc_atiusb
```
 
lirc_atiusb            19232  1 
lirc_dev               15732  1 lirc_atiusb 
usbcore               146412  5 lirc_atiusb,usbhid,ehci_hcd,ohci_hcd 
```but I only see this
```
lirc_atiusb            12945  0 
lirc_dev                8780  1 lirc_atiusb

```How can I get that usbcore entry in my lsmod?
[COLOR=#000000][COLOR=#0000bb]
[/COLOR][/COLOR]when I run irw I see this:
```
root@XBMCLive:~# irw
connect: No such file or directory

```

---

### Post by Methuselah on 2010-01-31
sudo modprobe usbcore

---

### Post by outleradam on 2010-01-31
```
root@XBMCLive:~# sudo modprobe usbcore
FATAL: Module usbcore not found.

```

---

### Post by Methuselah on 2010-01-31
OK, I just realised you posted that above.
Sorry, I don't have an answer for you off the top of my head.
usbcore is a pretty standard module that is usually present even if not loaded.

---

### Post by outleradam on 2010-01-31
ok, so how can usbcore.ko be recompiled?

---

### Post by Methuselah on 2010-01-31
Maybe your kernel configuration file does not enable the usbcore module.
AFAIK, vanilla Ubuntu should have it.

---

### Post by outleradam on 2010-01-31
my previous kernel did have it

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.7]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.7/is")  is the kernel I'm using now.  where can I get the vanilla version?

---

### Post by outleradam on 2010-01-31
I dont' know if I'm getting anywhere here, but I did manage to get some raw codes from my remote.

```
root@XBMCLive:~/lirc-0.8.6# mode2 --raw
code: 0x14721d8000
code: 0x14721d8000
code: 0x14f49f8000
code: 0x14f49f8000
^C      
root@XBMCLive:~/lirc-0.8.6# irw
connect: Connection refused

```

But irw is still refusing connection.

I just don't know how to get a lirc connection

---

### Post by outleradam on 2010-01-31
I just don't get it...

```
root@XBMCLive:~# apt-get install lirc-modules-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  kernel-source
The following NEW packages will be installed:
  lirc-modules-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/272kB of archives.
After this operation, 1,204kB of additional disk space will be used.
Selecting previously deselected package lirc-modules-source.
(Reading database ... 75691 files and directories currently installed.)
Unpacking lirc-modules-source (from .../lirc-modules-source_0.8.6-0ubuntu2_all.deb) ...
Setting up lirc-modules-source (0.8.6-0ubuntu2) ...
Loading new lirc-0.8.6 DKMS files...
First Installation: checking all kernels...
Building for architecture i686
Building initial module for 2.6.32-02063207-generic

Error! Bad return status for module build on kernel: 2.6.32-02063207-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.6/build/ for more information.
dpkg: error processing lirc-modules-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by outleradam on 2010-02-01
where can I get a vanilla kernel?

---

### Post by HaZee on 2010-03-04
It's 4 week ago since last post. Did you find the correct version or workaround for 2.6.32-02063207-generic?

---

### Post by outleradam on 2010-03-16
ya, i reverted to a previous kernel version.

---

