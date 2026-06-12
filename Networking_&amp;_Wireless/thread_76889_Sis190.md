---
title: "Sis190"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by Ollie on 2005-10-15
Hi.

I have a system with ASRock 939S56-M motherboard with an AMD64 processor and integrated LAN basen on Sis190 chip. Ubuntu 5.10 does not recognize my LAN. Is there any easy way to fix this problem?

---

### Post by ram1 on 2005-10-29
I had the same problem with my ASUS K8S-MX with SiS190 NIC on it. However, I found a solution. SiS provides a linux driver on their homepage, and I found myself two ways to make use of this driver.

1. Compile a custom kernel (which SiS suggested in their readme file bundled with the driver).

2. Compile the driver as a module to use with the existing kernel.

 I choosed the latter alternative. Ubuntu breezy badger is shiped with gcc version 4. Sadly, the kernel is compiled with gcc version 3.4, which has to be downloaded to proceed with this solution. Hopefully you have another NIC to use when downloading, some USB-drive/Mp3-player or similar to move the required files to your ubuntu system (in my case an mp3-player).
Of course you need the driver as well, download it from [www.sis.com](www.sis.com).

You will also need the headers for your existing kernel, found on the installation CD. Use aptitude or whatever you prefer, install the package called: linux-headers-´uname -r´
(uname -r prints the kernel release, run it first) 

Unpack the driver tarball. You should now have a file called sis190.c. To compile this one we have to write a makefile. 
```

obj-m   := sis190.o
KDIR    :=/lib/modules/$(shell uname -r)/build
PWD     :=$(shell pwd)

default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules


```
Save it as Makefile in the same directory as the sis190.c file.

In this directory, type "make" and pray. If it compiles succesfully (you get no error messages), proceed with the install.sh script.

You can use this script to install the module:
```

#!/bin/sh
install -m 644 sis190.ko /lib/modules/`uname -r`/kernel/drivers/sis190.ko
/sbin/depmod -a

```

Save it as whatever in the very same directory as the other files, make it executeable and run it! 


Now, run: modprobe sis190.

If no problems are reported, you should now have a working SiS 191/190 NIC. Type ifconfig eth0 to verify.

Hope this helped you, im just a layman. :)

---

### Post by bort1002000 on 2005-11-24
Hello,

I found this thread in google but I still had a problem.
How can I get a working gcc 3.4?

I tried again a search at google and downloaded some *.deb files (gcc-3.4_3.4.2-2ubuntu1_i386.deb, gcc-3.4_3.4.2-2ubuntu1_i386.deb, gcc-3.4_3.4.2-2ubuntu1_i386.deb) but when I try to run the makefile I get the error: gcc-3.4: installation problem, cannot exec 'as', ...

I'm a linux newbie and had my problems to find the solution. It would be great if you could complete your guide ;)

Working without NIC isn't really easy, because apt doesn't work and I have to reburn my CD every time.

Many thanks
Simon

---

### Post by ram1 on 2005-12-02
I dont know really but you are probably missing som package?
However, another approach you maybe prefer is to grab the latest kernel from kernel.org (im currently using 2.6.14) this one will have support for your NIC and  it may fix other issues with your not very well supported SiS motherboard.

I know there is lots of info about compiling your own kernel in this forum, just use the search function :)

---

### Post by s_p_a_r_k_y on 2005-12-02
GCC 3.4 is a package. Use synaptic to install gcc 3.4 under System->Administration->Synaptic


[QUOTE=bort1002000]Hello,

I found this thread in google but I still had a problem.
How can I get a working gcc 3.4?

I tried again a search at google and downloaded some *.deb files (gcc-3.4_3.4.2-2ubuntu1_i386.deb, gcc-3.4_3.4.2-2ubuntu1_i386.deb, gcc-3.4_3.4.2-2ubuntu1_i386.deb) but when I try to run the makefile I get the error: gcc-3.4: installation problem, cannot exec 'as', ...

I'm a linux newbie and had my problems to find the solution. It would be great if you could complete your guide ;)

Working without NIC isn't really easy, because apt doesn't work and I have to reburn my CD every time.

Many thanks
Simon[/QUOTE]

---

### Post by dj50 on 2006-03-31
[QUOTE=s_p_a_r_k_y]GCC 3.4 is a package. Use synaptic to install gcc 3.4 under System->Administration->Synaptic[/QUOTE]

Hello,

I've got the same problem, and GCC 3.4 is nowhere to be found in Synaptic (I'm stuggling with Ubuntu 5.10). So I've downloaded gcc-3.4_3.4.4-6ubuntu8.1_i386.deb from here: [http://packages.ubuntu.com/breezy/devel/gcc-3.4](http://packages.ubuntu.com/breezy/devel/gcc-3.4) and  (I hope) all the dependencies when I do sudo apt-get install gcc-3.4_3.4.4-6ubuntu8.1_i386.deb I keep getting:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

Have I missed some package? And how do I know which one?

Thanks

---

### Post by dj50 on 2006-04-04
Ok ... if no one knows, or can be bothered to answer ...

Back to Windows for me ... Linux for human beings my arse - when you have to compile drivers, kernels, apps or whatever you know you have a big problem.

---

### Post by RainbowSailorZ on 2006-04-05
Hello,

you could try to change the MTU of your Sis Card to 1492. This way it works in Fedora Core 5. And you don't need to (re)compile the kernel-module. If it works in Ubuntu, I don't know. But try it ;) 

As root type: "ifconfig eth0 mtu 1492" Et voila, your Card should run like hell. 

To change the MTU at boot time, edit as root the file "/etc/sysconfig/networking/devices/ifcfg-eth0" (path is from FC5) and add the line "MTU=1492" to the end of this file. 

I hope this works for you and other users of the sis190 :)

---

### Post by dj50 on 2006-04-07
Thanks, but unfortunatelly it doesn't work

$ sudo ifconfig eth0 mtu 1492
SIOCSIFADDR: No such device

---

### Post by Diego Antony on 2007-05-31
Hi,  i have a similar problem. I tried all of Ram1 posted but it still don´t work to me. I have ubuntu 6.06 with ltsp 4.2.

I had downloaded sis190 driver from sis website, i´ve unpacked file at /root/sis190_20041220, created the makefile on this folder:

(root@gandhi:~/sis190_20041220# ls -la
total 88
drwxr-xr-x  2 root root  4096 2007-05-31 09:43 .
drwxr-xr-x 26 root root  4096 2007-05-31 09:39 ..
-rwxrwxrwx  1 root root   150 2007-05-31 09:27 Makefile
-rw-r--r--  1 root root  1902 2004-12-20 01:32 readme.txt
-rw-r--r--  1 root root   254 2004-12-20 01:42 relnote.txt
-rwxr-xr-x  1 root root 62989 2004-12-20 03:12 sis190.c
root@gandhi:~/sis190_20041220# )

with the exactly same content posted here, and when i type make it show me whats above:

root@gandhi:~/sis190_20041220# make
make: Nada a ser feito para `default'.
root@gandhi:~/sis190_20041220# 


Does any one can help me?

PS.: i had to install make, linux headers and gcc 3.4, but nothing happened :(****

---

### Post by Diego Antony on 2007-06-01
Hey Guys, i typed #modeprobe sis190 and its gets no error message, but at my diskless client, linux try to install 3com 3c59x always, even with just my sis190 network enabled and plugued.

That make me think that i have to modify a configuration file, i tryed to modify /etc/dhcp3/dhcpd.conf like this

# Add these two lines to the host entry that needs kernel parameters

        option option-128     e4:45:74:68:00:00;       # NOT a mac address
        option option-129     "NIC=sis190 IO=0x300";


but i don´t know if it is correct...

my kernel is

root@gandhi:~# uname -r
2.6.15-26-386

any idea????

---

