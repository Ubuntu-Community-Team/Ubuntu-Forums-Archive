---
title: "[SOLVED] Trouble compiling madwifi"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by wmdiem on 2008-07-15
I have been trying to compile madwifi that supports 5007. I have  been trying to follow varrious different instructions, but all seem to be ending with the same error.
The main instructions I have been following are:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)
[http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi&page=2](http://ubuntuforums.org/showthread.php?t=795984&highlight=compiling+madwifi&page=2)
[http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007](http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007)

I think there were some others, but the only real difference seems to be the snapshots of madwifi that they are referencing. 

When I try to "sudo make" I get 

wmdiem@diem-acer:~/sources/madwifi-w5k/madwifi-nr-r3366+ar5007/madwifi-ng-r3366+ar5007$ sudo make
./kernelversion.c:13:30: error: linux/utsrelease.h: No such file or directory
Checking requirements... ok.
Checking kernel configuration... /bin/sh: Syntax error: "|" unexpected
make: *** [configcheck] Error 2

I found [http://ubuntuforums.org/showthread.php?t=652125&page=5](http://ubuntuforums.org/showthread.php?t=652125&page=5) where someone gets this error and someone said it was covered in the README, and gave a link. Following through it, it looked like (a) this was to integrate MadWifi into the kernel source prior to compiling a custom kernel (I was trying to just make a module, maybe you can't do that?) (b) the step I hadn't gotten was running install.sh from the "patch" directory. The tarball didn't make a patch directory, but it did have a "kernel-patch" directory, and kernel-patch did have an install.sh. When I ran it, I got:
wmdiem@diem-acer:~/sources/madwifi-w5k/madwifi-nr-r3366+ar5007/madwifi-ng-r3366+ar5007/patch-kernel$ sudo ./install.sh
FATAL ERROR: Kernel build system is not supported

I've never compliled anything before, let alone a kernel. And I have no idea what is going on. I've been trying to slowly trouble-shoot my way through various other errors, and now I just don't know what else to try. It is particularly frustrating because no one else, even using ubuntu, seems to be having this problem. I know I am probably missing something obvious, but it's not obvious to me, so I don't know how to fix it. I have (tried to) RTFM I just don't know enough of the details of what I'm actually doing (i.e., how a driver works in linux, how compilation is supposed to happen under normal circumstances, etc) to make any sense of it. I'm basically flying-blind (by the instructions with little idea of what i'm actually acomplishing) so when I get an error I have no idea how to fix it. Please help. Any suggestions are GREATLY appreciated.

---

### Post by jeremyswalker on 2008-07-15
Did you install build-essential? I believe I have had that error before, and that was what I was lacking. In a terminal, type:  sudo apt-get install build-essential. See if that works.

---

### Post by chili555 on 2008-07-15
Your first link refers to this: [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3752-20080706.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3752-20080706.tar.gz)

With *build-essential* and *linux-headers-generic* installed, it 'makes' without an error or even a warning!

---

### Post by wmdiem on 2008-07-15
The headers did it. It is up and seems to be working fine. Thanks so much. And it is so much nicer than ndiswrapper, with ntos_wq eating up all those cycles. 

So just in case anyother noob stumbles accross this with the same probelms here are the steps that I didn't get from the turorials. 
1) in addition to build essentials, you also need to install the package for your kernel source and the package for your kernel headers. (to get your version of the kernal use uname -r). These should be installed to /usr/src/your-kernel-version/
2) copy the kernel's config file to the directory where your new kernel source is (mentioned above). This file is found in /boot/ and is named config-your-kernel-version. once it is copied, rename the copy .config , the leading dot is part of the name. 
3) make a link named build to the kernel source directory (mentioned above. I *think* this is what the kernelpath error was about). if you run make from the madwifi directory, it will give you an error and tell you where it is looking. If I recall it was /lib/modules/your-kernel-version/ where you needed to place the link, so the whole path including the link becomes /lib/modules/your-kernel-version/build/

---

