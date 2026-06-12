---
title: "Ubuntu 8.04 LTS is not dectecting 4GB Ram"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-09-20
Hi,

    I'm using Ubuntu 8.04 LTS kernel version 2.6.24-24-generic. When I install the OS, I was using 2GB Ram. Now I inserted 2 more GB.  So the total ram size is 4GB. But it is showing only 3GB. Can you please gave me a solution for this. I have Windows also in my system there my 4GB RAM is detecting why not in Linux Ubuntu 8.04 LTS?. Do I need to do any setting for this.

---

### Post by Crunchy the Headcrab on 2009-09-20
I take it you're using a 32bit operating system. If you can use a 64bit OS, then give that a try for ubuntu also.

---

### Post by roger_1960 on 2009-09-20
Are you using 32bit or 64 bit Ubuntu?  I believe it needs to be 64 bit to address more than about 3.2Gb of RAM.

---

### Post by halitech on 2009-09-20
32bit linux will show about 3.2gig of ram as some is taken by the bios and the limitation of 32bit. to show the full 4 gig you either need 64bit (if your system will handle it) or you need to compile the PAE feature into your kernel so it can see all your ram.

---

### Post by scorp123 on 2009-09-20
> **halitech said:**
> or you need to compile the PAE feature into your kernel so it can see all your ram. ```
sudo apt-get install linux-server 
```

This will install the Linux kernel of the "Ubuntu Server" edition. That one has PAE already enabled. So you don't need to bother about compiling this stuff yourself.

---

### Post by halitech on 2009-09-20
> **scorp123 said:**
> ```
sudo apt-get install linux-server 
```

This will install the Linux kernel of the "Ubuntu Server" edition. That one has PAE already enabled. So you don't need to bother about compiling this stuff yourself.

wasn't aware the new server kernel with PAE already enabled, thanks for pointing that out to me (and others who read this thread)

---

### Post by scorp123 on 2009-09-20
> **halitech said:**
> wasn't aware the new server kernel with PAE already enabled Ubuntu's 32-bit server kernel always had PAE enabled. This is nothing new.

Other distros that ship with PAE enabled:
- Novell SuSE Linux Enterprise Server
- Novell OpenSUSE (it will install a PAE kernel if it detects 4GB RAM or more)
- Red Hat Enterprise Linux
- CentOS
- probably many others too

---

### Post by webwiller on 2009-09-20
Does this mean Ubuntu can actually use all the available ram, or just that he's able to see it?

---

### Post by nhasian on 2009-09-20
if you install linux-server then yes ubuntu will use all of you ram.  unlike WindowsXP/Vista 32bit.  The OS will report 4 gigs of ram but only use 3 of it.  thanks to complaints from MS end users, the service pack "fixed" it so it showed the correct amount of memory in the system properties.  haha of course it still doesnt use all the ram unless they install the 64 bit windows.

---

### Post by webwiller on 2009-09-20
I did install linux-server package...and after reboot required I log into a completely black screen! Gnome is gone! Any clue if it could be cause of the new package? I removed it from recovery terminal...but still...oh god! I opened another thread anyway...

---

### Post by scorp123 on 2009-09-20
> **webwiller said:**
> ...and after reboot required I log into a completely black screen! Do you have an Nvidia card? In that case you probably also need this package:

```
sudo apt-get install linux-restricted-modules-server
```

---

### Post by vipin.balakrishnan on 2009-09-21
Hi All,

  I 'm using 32 bit OS. When I went to ubuntu site for downloading 64 bit. It shows  only for AMD 64 bit ( [http://ubuntu.ipacct.com/releases/hardy/ubuntu-8.04.3-desktop-amd64.iso](http://ubuntu.ipacct.com/releases/hardy/ubuntu-8.04.3-desktop-amd64.iso) ). I'm using Intel EM64 bit Processor. So to use ubuntu in 64 bit for Intel processor which one should I download from this site.

---

### Post by Temposs on 2009-09-21
You should get the AMD 64-bit version. It will work fine on your computer. The AMD part does not mean that it only works with AMD processors. It will work with Intel or AMD 64-bit processors.

---

### Post by scorp123 on 2009-09-21
> **vipin.balakrishnan said:**
>  When I went to ubuntu site for downloading 64 bit. It shows  only for AMD 64 bit "AMD 64-bit" here means the 64-bit instruction set originally designed by AMD. Modern Intel CPU's implement this instruction set too.

This is used to differentiate it from Intel's horrible 64-bit design "IA64" that is used in the IA-64 "Itanium" class of CPU's. Why is it "horrible"? Well: IA64 chips can only execute 32-bit code with a severe performance penalty.

That's why AMD back in 2001 or so designed their own instruction code which does not have such serious drawbacks, e.g. AMD64 chips should do equally well no matter whether you execute 32-bit code or 64-bit code. Intel had no choice but to follow, so all non-Itanium 64-bit chips from Intel such as the late Pentium-4, Xeon, Core2Duo, Centrino2Duo etc. implement and use this instruction set as well.

As was already pointed out to you: You should use the "AMD 64-bit" image, no matter what it says on your CPU. It's about the instruction set, not the manufacturer.

---

### Post by rlogan on 2009-09-21
In my opinion use the 64 bit version and use all the RAM you like.

I am using 64bit Jaunty and have found it to be wonderful and stable. Would not go back to 32 bit now.

My 4Gb of RAM shows as 3.8Gb under System Monitor.

---

### Post by Maravilha on 2009-09-21
I think it is worth to mention that Windows Vista and 7 will report that there is 4 GB available but will be able to use only 3-3.5 depending on your setup.

If you have a 64 bit version of the OS it would also mean that every application will consume more memory (due to longer addressing) and that mean that there will be more data transferred from your hard drive and processed by the CPU. 

I think its worth switching to 64bit only when you have 6 and more GB of memory available.

---

### Post by webwiller on 2009-09-21
> **scorp123 said:**
> Do you have an Nvidia card? In that case you probably also need this package:

```
sudo apt-get install linux-restricted-modules-server
```

I actually have an ATI graphic card, but I'm sure it is because of linux-server package that my screen crashed. I did a fresh install and as soon as I reinstalled linux-server it crashed again!

Could I work it round with linux-restricted-modules-server also with an ATI graphic card or not?

Ty ;)

---

### Post by scrooge_74 on 2009-09-21
ATI has it own drivers also, you should check for instructions for your particular card

---

### Post by webwiller on 2009-09-21
> **scrooge_74 said:**
> ATI has it own drivers also, you should check for instructions for your particular card

But...does ATI have a specific server driver? Because I already installed the proprietary graphic card driver...I had to in order to have 3D effects activated, but screen crashed anyway! ;)

---

### Post by scorp123 on 2009-09-21
> **webwiller said:**
>  Could I work it round with linux-restricted-modules-server also with an ATI graphic card or not? That package is not specific to Nvidia or ATI. It pretty much contains what it says: "restricted modules", e.g. device drivers for "not yet fully open" hardware, ranging from Atheros WiFi cards to ... whatever. The package will install special "hooks" so that proprietary hardware drivers can "hook-in" and talk to the Linux kernel. So NVidia and ATI cards might very much benefit from that package as it provides the infrastructure those proprietary drivers might need to function.

I have another suggestion for you. You still have the "normal" 32-bit kernel on your system, right? Do this then:
```
dpkg -l 'linux*' | grep ii
```

If I do this on my 32-bit laptop I get these results:
```
ii  linux-generic                                               2.6.28.15.20                                     Complete Generic Linux kernel
ii  linux-headers-2.6.28-15                                     2.6.28-15.52                                     Header files related to Linux kernel version
ii  linux-headers-2.6.28-15-generic                             2.6.28-15.52                                     Linux kernel headers for version 2.6.28 on x
ii  linux-headers-generic                                       2.6.28.15.20                                     Generic Linux kernel headers
ii  linux-image-2.6.28-15-generic                               2.6.28-15.52                                     Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                                         2.6.28.15.20                                     Generic Linux kernel image
ii  linux-libc-dev                                              2.6.28-15.52                                     Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.28-15-generic                  2.6.28-15.20                                     Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common                             2.6.28-15.20                                     Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic                            2.6.28.15.20 
```

Now, if you use the "linux-server" package, you should have the same list as above, except that the packages should be named e.g. "linux-image-2.6.28-15**-server**" instead of "linux-image-2.6.28-15**-generic**" and "linux-restricted-modules**-server**" instead of "linux-restricted-modules**-generic**" and so on.

So in your case when you do above command ... 
```
dpkg -l 'linux*' | grep ii
```
... it should list all packages related to the Linux kernels, both the "normal" and the "server" ones. My guess is that in your case one relevant "linux-server" package is missing. So I'd recommend you try and compare the list ...

If everything is correct then you should have the same number of *linux-blabla-something-generic* packages as *linux-blabla-something-server* packages ...  If something is not right then there will be far fewer ***-server** packages than ***-generic** pacakges. So the fix would be to tell your system via "sudo apt-get install ... " to go and fetch the missing package, e.g. 
```
sudo apt-get install linux-restricted-modules-server
```

---

### Post by webwiller on 2009-09-23
> **scorp123 said:**
> That package is not specific to Nvidia or ATI. It pretty much contains what it says: "restricted modules", e.g. device drivers for "not yet fully open" hardware, ranging from Atheros WiFi cards to ... whatever. The package will install special "hooks" so that proprietary hardware drivers can "hook-in" and talk to the Linux kernel. So NVidia and ATI cards might very much benefit from that package as it provides the infrastructure those proprietary drivers might need to function.

I have another suggestion for you. You still have the "normal" 32-bit kernel on your system, right? Do this then:
```
dpkg -l 'linux*' | grep ii
```

If I do this on my 32-bit laptop I get these results:
```
ii  linux-generic                                               2.6.28.15.20                                     Complete Generic Linux kernel
ii  linux-headers-2.6.28-15                                     2.6.28-15.52                                     Header files related to Linux kernel version
ii  linux-headers-2.6.28-15-generic                             2.6.28-15.52                                     Linux kernel headers for version 2.6.28 on x
ii  linux-headers-generic                                       2.6.28.15.20                                     Generic Linux kernel headers
ii  linux-image-2.6.28-15-generic                               2.6.28-15.52                                     Linux kernel image for version 2.6.28 on x86
ii  linux-image-generic                                         2.6.28.15.20                                     Generic Linux kernel image
ii  linux-libc-dev                                              2.6.28-15.52                                     Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.28-15-generic                  2.6.28-15.20                                     Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common                             2.6.28-15.20                                     Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic                            2.6.28.15.20 
```

Now, if you use the "linux-server" package, you should have the same list as above, except that the packages should be named e.g. "linux-image-2.6.28-15**-server**" instead of "linux-image-2.6.28-15**-generic**" and "linux-restricted-modules**-server**" instead of "linux-restricted-modules**-generic**" and so on.

So in your case when you do above command ... 
```
dpkg -l 'linux*' | grep ii
```
... it should list all packages related to the Linux kernels, both the "normal" and the "server" ones. My guess is that in your case one relevant "linux-server" package is missing. So I'd recommend you try and compare the list ...

If everything is correct then you should have the same number of *linux-blabla-something-generic* packages as *linux-blabla-something-server* packages ...  If something is not right then there will be far fewer ***-server** packages than ***-generic** pacakges. So the fix would be to tell your system via "sudo apt-get install ... " to go and fetch the missing package, e.g. 
```
sudo apt-get install linux-restricted-modules-server
```


TX a lot mate! I dont know why, but with command "sudo apt-get install linux-server" plus command "sudo apt-get-install linux-restricted-modules-server" I kept missing linux-headers-server. I compared lists as you said and voilà, done perfectly! Now I have my 4gigs showing up in SysMonitor and a gorgeous running system! ;)
Ty!!!!
:guitar:

---

