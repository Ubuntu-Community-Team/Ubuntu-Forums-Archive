---
title: "installing Broadcom 802.11 Linux STA driver"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by hndaklr8480 on 2008-10-19
Hello friends first i would like to thank anyone for the help that is offered here.

I just installed Ubuntu Hardy Heron 8.04 running 2.6.24-19-generic kernel. I have a acer aspire 3600 with bcm411 mini-pci wifi card.
Broadcom released a driver for this and others the STA driver. I like to try and troubleshoot things the best I can before I post but I got to give up in this one. So, I have downloaded the .tar.gz and have completed step 1:

On the target machine, setup the source/hybrid/build directory

1.  Create a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             
tar -xzf <path>/hybrid-portsrc.tar.gz (I know run command in hybrid_wl directory)

After untar'ing you should have a src and lib sub directory plus a Linux 2.6 "kbuild" external makefile (Makefile).

!success!

on to step two:

You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable
kernel module (LKM):

On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                 
 make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:
 make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
(I also know drop the "<,>'s" and put my complete kernel vers in)
(Im such a noob rofl)
You should now have a LKM, wl.ko inside this directory.

k this is where i get stuck
ran command in the right directory i promise:
sudo make -C /lib/modules/2.6.24-19-generic/build M='pwd'


response:



make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

scripts/Makefile.build:41: /usr/src/linux-headers-2.6.24-19-generic/pwd/Makefile: No such file or directory

make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.24-19-generic/pwd/Makefile'.  Stop.

make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

I also promised that i search this too.  I am pretty sure that this driver is fairly new or newer newayz, (once again still a noob and could be wrong) but couldn't find anyone with the same problem so i must me missing something. I appreciate any help and i will keep searching. If there is any info you need from me i will provide just please let me know the proper command to get for you.

---

### Post by hndaklr8480 on 2008-10-19
hey people sorry for the double post i just got tired of searching and decided i was going to plug directly into the router. got a connection got all the up dates and STA driver was included. Everything works and i am posting this with ubuntu. Just one thing.  I boot up computer and wifi light worked lit right up. But wait i made a simple discovery.  I did scan and couldn't find router. everything else has been kinda backward so i did what i thought was turn off the router and did another scan bingo it worked so with my computer (acer 3680 and STA driver for wifi) off is actually on

---

