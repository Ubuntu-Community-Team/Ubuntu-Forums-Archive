---
title: "ndiswrapper installation problems - please help"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by noelnoel on 2005-08-22
I am a bit of a Linux newbie, but I kind of know what I need to do just not how! I am trying to install ndiswrapper but I keep getting the error message at the bottom of this message. I am assume I need to link to the kernel source, but how do I do this? 

Per the Wiki on the ndiswrapper website I can do this manually by

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

Unfortunately I am clearly not  being that smart as when I go into /usr/src I only have the directory rpm. 

I know the latter half should be /lib/modules/2.6.10-5-powerpc/build but I don't know about the /usr/src/linux-<kernel-version> bit. Can anyone help me out? What do I need to point at what?

Many thanks for the help,

Charlie



Error message from the make install command below:
----------------------------------------------------------------------------------------------------------------------------


root@ubuntu:/home/charlie/ndiswrapper-1.3rc1 # make install
make -C driver install
make[1]: Entering directory `/home/charlie/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-powerpc/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/charlie/ndiswrapper-1.3rc1/driver'
make: *** [install] Error 2
root@ubuntu:/home/charlie/ndiswrapper-1.3rc1 #

---

### Post by Davec on 2005-08-23
It should be

/usr/src/linux-2.6.10-5-powerpc

Kernel modules, like you're compiling, and kernels share the same version numbers, because they have to fit together.

Alternatively you could
cd /usr/src

and
ls

to see what you've got there. If you don't have a linux-<something> directory in /usr/src then you need the kernel source before going ahead anyway. I think the package in synaptic is linux-source?

---

### Post by luc1972 on 2005-08-26
I had the same problem, but searching round these forums someone mentioned using fakeroot to sort out the linux headers.  Search for those terms and fingers crossed that will sort it out.,

---

### Post by hbweb500 on 2005-08-26
I had the same problem (kind of) with Kubuntu. My sources were incomplete. You should be able to install the sources just by using your installation CD, no downloading required.

Try typing this at a command prompt:

```
sudo apt-get install build-essential linux-headers-<version>
``` 

An, of course, replace <version> with the output from the command 'uname -r'.

Have fun,
Jeff

---

