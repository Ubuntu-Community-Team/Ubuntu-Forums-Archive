---
title: "trubble with installing &amp; compiling linux kernel 2.6.34.1"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by auroraa9420 on 2010-07-25
yes iv been trying to install the 2.6.34.1 kernel since yestoday because i have the ATI 5830 card (yes i know ATI sucks but damn it) and the curent Ubuntu kernel dosen't support it. Yes i im not some kid-beginer and i know the basics (at least i think i do ;)). Can't find any tutorial on the internet (i did find a few but they were realy old :???:)

can someone help me with compiling and installing the kernel and if posible to send me a git repository with the evergreen driver

TNX TO ANYONE WHO CAN HELP ME LIKE A PRO ;)

pease :guitar:

---

### Post by Paddy Landau on 2010-07-25
Sorry, I don't know the answer.

Have you tried a different distro?

Alternatively: You say that the current Ubuntu kernel "doesn't support" the ATI. In what way -- what are the symptoms? Maybe we can help fix the problem.

---

### Post by auroraa9420 on 2010-07-25
> **Paddy Landau said:**
> Sorry, I don't know the answer.

Have you tried a different distro?

Alternatively: You say that the current Ubuntu kernel "doesn't support" the ATI. In what way -- what are the symptoms? Maybe we can help fix the problem.

yes i could say something like that...well lets do it your way

yes...i have a 5830 ATI card witch dosen't support the current ubuntu lucid linux kernel

as i read on the Phonorix site, they said that the evergreen drivers are supported on the 2.6.34 kernel (witch is the latest one)

---

### Post by Paddy Landau on 2010-07-25
Hmm, sorry, I don't know how to compile kernels.

If you can't use another distro, what happens when you try to use Ubuntu? Does it not load, or what?

---

### Post by auroraa9420 on 2010-07-25
> **Paddy Landau said:**
> Hmm, sorry, I don't know how to compile kernels.

If you can't use another distro, what happens when you try to use Ubuntu? Does it not load, or what?


sorry the only 2 distros i use are debian and ubuntu

debian for work and ubuntu for home usage (i used windows for some game things but if i fix this problem then its ubuntu for good) and i dont think so because this kernel is too new for new distro development so the only solution is to compile your self the kernel :S

is there someone in the forum or some ubuntu developer that can help me?

---

### Post by gianluca.pettinello on 2010-08-07
Hello,
I have compiled and installed kernel 2.6.34.1 as well as kernel 2.6.35 on ubuntu 10.04 but prefer 2.6.34.1 because it seems faster

So you download the source from kernel.org if you want to start from vanilla.
You extract it on /usr/src
Then you have to download the patch to enable ureadahead. You can find it on google the name is 0001-trace-add-trace-events-for-open-exec-an-.patch
the patch is applied by moving on the souirce directory and using the command
patch -p1 </path/name of the patch

then you have to take a .config file, you can extract it from a linux-image-2.6.34 package

Finally  you run
export CONCURRENCY_LEVEL="n° kernel+1"
sudo fakeroot make-kpkg --initrd --append-to-version="something" kernel-image kernel-headers

After some time you have your deb packages done on /usr/src

If you have problems you can see the ubuntu documentation (search on google kernel ubuntu compile and choose the old debian way)

For me it worked

Ciao
Gianluca

---

### Post by stmiller on 2010-08-07
There is no need to compile kernels for Ubuntu unless you need something specific. 

Each kernel is available from the kernel ppa as a deb. :)

Just download and install.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by auroraa9420 on 2010-08-08
> **gianluca.pettinello said:**
> Hello,
I have compiled and installed kernel 2.6.34.1 as well as kernel 2.6.35 on ubuntu 10.04 but prefer 2.6.34.1 because it seems faster

So you download the source from kernel.org if you want to start from vanilla.
You extract it on /usr/src
Then you have to download the patch to enable ureadahead. You can find it on google the name is 0001-trace-add-trace-events-for-open-exec-an-.patch
the patch is applied by moving on the souirce directory and using the command
patch -p1 </path/name of the patch

then you have to take a .config file, you can extract it from a linux-image-2.6.34 package

Finally  you run
export CONCURRENCY_LEVEL="n° kernel+1"
sudo fakeroot make-kpkg --initrd --append-to-version="something" kernel-image kernel-headers

After some time you have your deb packages done on /usr/src

If you have problems you can see the ubuntu documentation (search on google kernel ubuntu compile and choose the old debian way)

For me it worked

Ciao
Gianluca

how certain are you that this wont cause a kernel panic and or a Out of range monitor

because i dont whant to risk reinstaling the kernel again

---

### Post by auroraa9420 on 2010-08-08
> **stmiller said:**
> There is no need to compile kernels for Ubuntu unless you need something specific. 

Each kernel is available from the kernel ppa as a deb. :)

Just download and install.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")


hehe actualy there is...i tried with ppa kernel updates and it didnt't work

even after the 10.7 catalist update

---

### Post by sandyd on 2010-08-08
> **auroraa9420 said:**
> yes iv been trying to install the 2.6.34.1 kernel since yestoday because i have the ATI 5830 card (yes i know ATI sucks but damn it) and the curent Ubuntu kernel dosen't support it. Yes i im not some kid-beginer and i know the basics (at least i think i do ;)). Can't find any tutorial on the internet (i did find a few but they were realy old :???:)

can someone help me with compiling and installing the kernel and if posible to send me a git repository with the evergreen driver

TNX TO ANYONE WHO CAN HELP ME LIKE A PRO ;)

pease :guitar:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573167](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573167)

and catalyst 10.7 supports it. I tried it just a few seconds ago before returning to the radeon drivers. [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by gianluca.pettinello on 2010-09-15
I compiled the kernel because the geenric doesn't support my sound card. So I had to patch it and compile

Gianluca

---

