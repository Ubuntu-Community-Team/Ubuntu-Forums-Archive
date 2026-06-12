---
title: "VirtualBox fails to compile"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by DarthOpto on 2009-02-16
Virtualbox is failing to compile the kernel module.

How do I fix this? I did not have this problem with my other Ubuntu machine. 

This machine is Intrepid Server

When I run /etc/init.d/vboxdrv setup it fails I am running it as root
When I try to access the log as root, it is saying that permission is denied

---

### Post by Eredeath on 2009-02-17
From VirtualBox help...
> 2.3.2. The VirtualBox kernel module
VirtualBox uses a special kernel module to perform physical memory allocation and to gain control of the processor for guest system execution. Without this kernel module, you will still be able to work with virtual machines in the configuration interface, but you will not be able to start any virtual machines.
The VirtualBox kernel module is automatically installed on your system when you install VirtualBox. To maintain it with future kernel updates, for recent Linux distributions -- for example Fedora Core 5 and later, Ubuntu 7.10 (Gutsy) and later and Mandriva 2007.1 and later --, generally we recommend installing Dynamic Kernel Module Support (DKMS)[7]. This framework helps to build kernel modules and to deal with kernel upgrades.
If DKMS is not already installed, execute one of the following: 
On an Ubuntu system:
sudo apt-get install dkms
On a Fedora system:
yum install dkms
On a Mandriva system:
urpmi dkms
If DKMS is available and installed, the VirtualBox kernel module should always work automatically, and it will be automatically rebuilt if your host kernel is updated.
Otherwise, there are only two situations in which you will need to worry about the kernel module:
The original installation fails. This probably means that your Linux system is not prepared for building external kernel modules.
Most Linux distributions can be set up simply by installing the right packages - normally, these will be the GNU compiler (GCC), GNU Make (make) and packages containing header files for your kernel - and making sure that all system updates are installed and that the system is running the most up-to-date kernel included in the distribution. The version numbers of the header file packages must be the same as that of the kernel you are using.
With Debian and Ubuntu releases, you must install the right version of the linux-headers and if it exists the linux-kbuild package. Current Ubuntu releases should have the right packages installed by default.
In even older Debian and Ubuntu releases, you must install the right version of the kernel-headers package.
On Fedora and Redhat systems, the package is kernel-devel.
On SUSE and OpenSUSE Linux, you must install the right versions of the kernel-source and kernel-syms packages.
Alternatively, if you have built your own kernel, /usr/src/linux should point to your kernel sources. if you have not removed the files created during the build process, then your system will already be set up correctly.
The kernel of your Linux host got updated. In that case, the kernel module will need to be reinstalled by executing (as root):
/etc/init.d/vboxdrv setup

---

### Post by DarthOpto on 2009-02-18
I found out what the problem was. Once I figured out where to go to view the log file, I found that it needed some kernel upgrades. I got the kernel packages mentioned in the error message and VirtualBox is working like a charm.

---

