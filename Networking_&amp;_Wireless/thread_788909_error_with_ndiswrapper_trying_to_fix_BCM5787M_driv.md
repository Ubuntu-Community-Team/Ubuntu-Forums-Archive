---
title: "error with ndiswrapper trying to fix BCM5787M driver"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by bardu0708 on 2008-05-10
Hey

I'm a total newbie at Linux and didn't understand any terminal language at first but know the basics now.
I've installed Ubuntu 8.04 on a HP Compaq 6715b (using Wubi from Windows Vista)

The problem I have is that the wireless connection won't work. The 'Wireless Networks' window shows no possible connections.

Now I've browsed countless forums searching for this problem and some of them contain more or less the same. Though, every solution given there didn't work for me. 

I'm dual booting it with Windows Vista (and switching constantly because wireless works on Vista)
It has a  NetLink BCM5787M Gigabit Ethernet PCI Express and the driver isn't supported by Linux and therefore downloaded NDISwrapper. (windowsdriver: C:\Windows\system32\DRIVERS\b57nd60x.sys)
I downloaded  ndiswrapper-1.52

The install read file states:
''You need a recent kernel, at least 2.6.6 or 2.4.26, with header files 
for the kernel. Make sure there is a link to the kernel source from 
the modules directory. The command 

  ls /lib/modules/`uname -r`/build 

should have at least 'include' directory and '.config' file.''

First of all, where do I need to make this link? From which directory?
In the directory where I will extract the .tar.gz? (in my case ~/Termhelp, so when I have extracted the file it will be placed in ~/Termhelp/ndiswrapper-1.52)

This is what I did:
*
osiris@osiris-laptop:~/Termhelp$  ls /lib/modules/2.6.24-16-generic/build 
arch    Documentation  include  Kbuild  Makefile        net      security 
block   drivers        init     kernel  mm              samples  sound 
crypto  fs             ipc      lib     Module.symvers  scripts  usr 
*

Secondly, I'm a lit unclear whether what I did was correct. 
(by the way, it also says that I ''should have at least 'include' directory and '.config' file'', the 'include' directory is present but the '.config' file is absent)

When I move on (following the install read file) this happens:
*
osiris@osiris-laptop:~/Termhelp$ cd ndiswrapper-1.52 
osiris@osiris-laptop:~/Termhelp/ndiswrapper-1.52$ make uninstall 
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places. 
Run uninstall as many times as necessary until no "removing" messages appear below. 
osiris@osiris-laptop:~/Termhelp/ndiswrapper-1.52$ make 
make -C driver 
make[1]: Entering directory `/home/osiris/Termhelp/ndiswrapper-1.52/driver' 
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/osiris/Termhelp/ndiswrapper-1.52/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
  LD      /home/osiris/Termhelp/ndiswrapper-1.52/driver/built-in.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/crt.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/hal.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/iw_ndis.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/loader.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/ndis.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/ntoskernel.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/ntoskernel_io.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/pe_linker.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/pnp.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/proc.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/rtl.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/wrapmem.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/wrapndis.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/wrapper.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/usb.o 
  CC [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/divdi3.o 
  LD [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/ndiswrapper.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/osiris/Termhelp/ndiswrapper-1.52/driver/ndiswrapper.mod.o 
  LD [M]  /home/osiris/Termhelp/ndiswrapper-1.52/driver/ndiswrapper.ko 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make[1]: Leaving directory `/home/osiris/Termhelp/ndiswrapper-1.52/driver' 
make -C utils 
make[1]: Entering directory `/home/osiris/Termhelp/ndiswrapper-1.52/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
##(here there is big list of errors and warnings, that make up 6 pages in total in Openoffice.org)
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/home/osiris/Termhelp/ndiswrapper-1.52/utils' 
make: *** [all] Error 2 
osiris@osiris-laptop:~/Termhelp/ndiswrapper-1.52$ 
*

Can somebody please tell what went wrong / what I'm doing wrong and how to do it in a correct way.

Please explain step-by-step and with the commands written if possible because if you write 'you have to do this and this' without showing the commands for it I won't understand.
(and if possible as well what I have to do after this with commands so that I won't get stuck there as well)

Alternatively:
I also tried to install the linux driver from here: [http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php](http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php)
Though I got an error as well when I gave the command 'make'
(and I can't run the rpm because it's not installed and the package is not available)

Thanks for you attention.

---

### Post by Ayuthia on 2008-05-10
For ndiswrapper, make sure that you have installed build-essential and linux-headers-`uname -r`.

I am sure that build-essential is on the live CD, but I thought that linux-headers was already installed, but I could be wrong.

---

### Post by bardu0708 on 2008-05-10
I installed ndiswrapper by following the first step from this guide: [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

In that way you just install it from the disk in stead of from the source. Very handy for me becausing my problem was with installing from the source.

I still have problems with the driver (don't know whether I have the right one)

osiris@osiris-laptop:~$ lspci -nn | grep 14e4 
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02) 
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02) 

osiris@osiris-laptop:~$ ndiswrapper -l 
b57win32 : driver installed 
	device (14E4:1693) present (alternate driver: tg3) 

Do you know whether I have the right driver (got it here: [http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php](http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php))
or maybe I should blacklist the alternate driver?

Thanks for replying anyway and I hope you can help me further.

---

### Post by Ayuthia on 2008-05-10
> **bardu0708 said:**
> I installed ndiswrapper by following the first step from this guide: [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

In that way you just install it from the disk in stead of from the source. Very handy for me becausing my problem was with installing from the source.

I still have problems with the driver (don't know whether I have the right one)

osiris@osiris-laptop:~$ lspci -nn | grep 14e4 
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02) 
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02) 

osiris@osiris-laptop:~$ ndiswrapper -l 
b57win32 : driver installed 
	device (14E4:1693) present (alternate driver: tg3) 

Do you know whether I have the right driver (got it here: [http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php](http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php))
or maybe I should blacklist the alternate driver?

Thanks for replying anyway and I hope you can help me further.

I am not familiar with the ethernet card, but as long as it is an XP version, I am sure that it is fine.  The driver says that it is present which is usually a good side.  Most likely, you will need to blacklist tg3 since it is listed as an alternate driver.

---

### Post by bardu0708 on 2008-05-10
How do I perform a blacklist?

I'm a total newbie at terminals so step for step command would be really helpfull

---

### Post by Ayuthia on 2008-05-10
The easy way to do this is to check to see if the module is blacklisted:
```
cat /etc/modprobe.d/blacklist* |grep tg3
```
This will go through all the blacklist files and see if anything matches tg3.  If the prompt just comes back or shows up with #blacklist tg3, then it is not blacklisted.  If it comes up with blacklist tg3 then it is blacklisted.

If it is not blacklisted:
```
echo blacklist tg3|sudo tee -a /etc/modprobe.d/blacklist
```
This is the easy way to add the module to the list.

Another way is to edit the file:
```
gksu gedit /etc/modprobe.d/blacklist
```Look through the file and if you do not see blacklist tg3, then add it to the end of the list.

---

