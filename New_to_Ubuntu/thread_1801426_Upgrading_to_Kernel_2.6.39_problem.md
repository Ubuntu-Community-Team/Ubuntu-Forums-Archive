---
title: "Upgrading to Kernel 2.6.39 problem"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by u bun tu on 2011-07-10
Hello everyone! I'm still just learning about ubuntu.

I am running Ubuntu 11.04 and I am trying to upgrade to the kernel 2.6.39.

Here are my steps:

1. sudo add-apt-repository ppa:kernel-ppa/ppa

2. sudo apt-get update

3. apt-cache showpkg linux-headersapt-cache showpkg linux-headers

4. sudo apt-get install linux-headers-2.6.39-0

5. reboot

When I use the command 'uname -r', after the reboot, it displays '2.6.38-1208-omap4' instead of '2.6.39.0'

Can someone please tell me what I'm doing wrong? Thanks for your help!

Note: I not going through the GUI, I am strictly using the command line only.

---

### Post by ajgreeny on 2011-07-10
I think you only installed the **linux-headers**, not the kernel itself.  Look for **linux-image-2.6.39** package, and install that if it is available.

---

### Post by u bun tu on 2011-07-10
> **ajgreeny said:**
> I think you only installed the **linux-headers**, not the kernel itself.  Look for **linux-image-2.6.39** package, and install that if it is available.

You're right!

When I use the command, "apt-cache showpkg linux-headers", I see the 2.6.39.0 header file.

BUT when I use the command, "apt-cache showpkg linux-image", I DON'T see the 2.6.39.0 image file.

I don't know why it is not there, I don't think the ppa:kernel-ppa/ppa source has it.

Do you know of another PPA site where I can get both the header and image files for the kernel 2.6.39.0?

Thanks again for your help!

---

### Post by terrykiwi83 on 2011-07-10
The PPA no longer updates the kernel, you can download the debs directly from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

---

### Post by u bun tu on 2011-07-10
> **terrykiwi83 said:**
> The PPA no longer updates the kernel, you can download the debs directly from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-rc4-natty/")

Thank you everyone, let me remind all of you that I am an absolute beginner!

Ok, so I downloaded the .deb files:

linux-headers-2.6.39.0...._all.deb
linux-headers-2.6.39.0...._amd64.deb
linux-images-2.6.39.0...._amd64.deb

When I run the command:
sudo dpkg -i linux-headers-2.6.39.0-..._amd64.deb

I get the following error: 

**dpkg: error processing linux-headers-2.6.39..._amd64.deb (--install): package architecture (amd64) does not match system (armel)**

When I run the command: uname -a, it displays the following:

Linux pandaboard2 2.6.38-1208-omap4 #11-Ubuntu SMP PREEMPT Fri Apr 15 16:34:35 UTC 2011 armv7l armv7l armv7l GNU/Linux


Which Kernel 2.6.39.0 version *.deb file do use for an ARMEL system?

If anyone could help me out, I would appreciate it! 

Note: I'm trying to upgrade the kernel on a Pandaboard, not on the Host system.

---

### Post by jtarin on 2011-07-10
While I can't answer you question directly, I can point you to the installation guide for, what I believe is what you need.[ Here]("https://launchpad.net/ubuntu/+source/installation-guide/20100518ubuntu4"). Scroll down and on the right.

---

### Post by VanR on 2011-07-10
Sounds like you need the 32-bit files instead of 64. Are you sure you are running 64-bit Ubuntu?

Those are .deb files so you should be able to download them and double-click and install them through the Software Center.

I usually use gdebi to install them.

---

### Post by u bun tu on 2011-07-10
> **jtarin said:**
> While I can't answer you question directly, I can point you to the installation guide for, what I believe is what you need.[ Here]("https://launchpad.net/ubuntu/+source/installation-guide/20100518ubuntu4"). Scroll down and on the right.


Thanks for the link and all of your help!

I downloaded the "installation-guide-armel_20100518ubuntu4_all.deb" file, and ran the command:

sudo dpkg --install installation-guide-armel_20100518ubuntu4_all.deb

but I'm not sure what to do after that...

I also downloaded the "installation-guide20100518ubuntu4.tar.gz" file, but when I untar the file, the README was empty and all of the HOWTO files were in *.xml and it was difficult for me to read it since I am only using the command line (I am ssh'ing into the Pandaboard).

---

### Post by u bun tu on 2011-07-10
> **VanR said:**
> Sounds like you need the 32-bit files instead of 64. Are you sure you are running 64-bit Ubuntu?

Those are .deb files so you should be able to download them and double-click and install them through the Software Center.

I usually use gdebi to install them.

I'm pretty sure my environment is an armel system but I can give the 32-bit files a try. Also because I'm not going through the Graphical Interface, I can't just double-click because I am going through the command line.

I'll give the 32-bit files a try and keep you posted. Thanks again for the help!

---

### Post by sandyd on 2011-07-10
Your running Ubuntu on ARM.

Your gonna have to compile your own kernel, because there are no prebuilt kernels for you.

Install the kernel sources, then, 

As a hint, copy your kernel configuration /boot/config-* (the star represents the latest kernel, to where you placed your kernel sources.

I don't use ubuntu, so I can't help you at this part.
However, once you find where the kernel sources install to, copy the /boot/config-* file to the root folder of the source, and rename it to .config.

---

### Post by jtarin on 2011-07-10
I agree....if you want this to work your gonna have to compile it. 
[Links]("http://marcin.juszkiewicz.com.pl/2010/10/19/how-to-cross-compile-arm-kernel-under-ubuntu-10-10/")
[More Links]("http://www.debian.org/ports/arm/")
Toolchain:[ A set of binutils and gcc for the ARM with appropriate patches is available on the ARM Linux ftp site.]("ftp://ftp.arm.linux.org.uk/pub/linux/arm/toolchain/src-3.2/build-toolchain")
[ARM Linux Developer]("http://www.arm.linux.org.uk/developer/")

---

