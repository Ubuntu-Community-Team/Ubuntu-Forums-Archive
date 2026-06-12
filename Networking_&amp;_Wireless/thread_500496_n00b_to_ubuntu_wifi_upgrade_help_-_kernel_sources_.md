---
title: "n00b to ubuntu wifi upgrade help - kernel sources directory"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by nuke072786 on 2007-07-13
Hello everyone, I'm happy to say I decided to learn Linux and am going to use ubuntu as my first linux distro!!

I've run into several problems along the way so far but have managed to fix several via the great help you all give on the forums here, however I have an issue that is probably simple to solve, I just don't know the OS well enough yet.

I'm trying to install an update patch for my Broadcom wifi card and the directions i'm using to install it are telling me to place the patch file i downloaded in the "kernel sources directory"

Where in the world is this folder? If someone could just tell me i should be able to make this update. i've read around several places and cannot find a clear answer.

Thanks in advance!

---

### Post by Vajra Vrtti on 2007-07-14
Enter these commands in a terminal to install the kernel source and tools eventually required:
[LIST=1]
[*]uname -r
[*]sudo apt-get install linux-source build-essential gawk
[*]cd /usr/src/
[*]sudo tar xvjf linux-source-????????.tar.bz2
[*]sudo ln -s linux-source-???????? linux
[/LIST]
*where ???????? is the response from command 1.*

The kernel source code will be in **/usr/src/linux**.

---

### Post by nuke072786 on 2007-07-14
Ok, Will try these commands.

So...after a normal Ubuntu install, there is no specific "kernel sources directory", you need to setup and install one? What exactly is it for (possibly help me in the future if I understand and learn early on!).

Thanks for your help Vajra Vrtti

---

### Post by Vajra Vrtti on 2007-07-14
> **nuke072786 said:**
> So...after a normal Ubuntu install, there is no specific "kernel sources directory", you need to setup and install one? What exactly is it for (possibly help me in the future if I understand and learn early on!).
Yes, there is no kernel source directory because you usually don't need it. Even if you compile applications that have kernel dependencies, most of the time they only need the kernel headers, and these are installed by default (package l**inux-headers-2.6.20-16** in Feisty). So, unless you have very specific applications or need to compile the kernel itself, the kernel sources are unnecessary (and it's a huge package).

If you really need the kernel sources to compile an application, you can install the sources package, compile the application, and then uninstall it. If you do that, you should also delete the uncompressed directory and the symbolic link.
```
cd /usr/src/
sudo rm linux
sudo rm -R linux-source-????????/
```

---

### Post by nuke072786 on 2007-08-02
Ok, well I think I got the kernel directory going, I now have another small issue.

To finish the patch on my wifi driver, I'm told to:
"Recompile your modules with 'make modules' followed by 'make modules_install' "
When I ran "sudo make modules" an error was spit back at me saying:

scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2

The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.

make: *** [modules] Error 1

So i tried this "make config" command and went through what seemed like an endless amount of yes or no answers before I gave up. Is there an easier way to get the kernel setup so i can run the "make modules' and "make modules_install" commands effortlessly?

Thanks for your help in advance!
Then build a kernel with module support enabled.

---

### Post by Vajra Vrtti on 2007-08-03
I can't help you with this issue because I've never build a kernel. I installed the kernel sources in order to compile another application that required them. I suggest you post this problem in new thread so that more people will see it.

---

