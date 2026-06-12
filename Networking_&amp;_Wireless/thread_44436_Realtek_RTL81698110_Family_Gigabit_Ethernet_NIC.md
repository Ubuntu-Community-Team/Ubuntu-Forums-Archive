---
title: "Realtek RTL8169/8110 Family Gigabit Ethernet NIC"
date: 2005-06-26
forum: Networking &amp; Wireless
---

### Post by tbresson on 2005-06-26
Hi.

I'm having problems with my samba and I though it might be related to my network driver, so I want to upgrade it.

My network chipset is : Realtek RTL8169/8110 Family Gigabit Ethernet NIC
and I found a new driver for it here: [ftp://152.104.238.194/cn/nic/rtl8169rtl8169sbrtl8110sb/linux-8169(221).zip](ftp://152.104.238.194/cn/nic/rtl8169rtl8169sbrtl8110sb/linux-8169(221).zip)

It's for kernel 2.6.x and my Hoary box is 2.6.10-5.

When trying to do a "make clean modules" as described in the readme, I get an error:
/lib/modules/2.6.10-5-386/build: No such file or directory

So I searched the net and found out I need to install the linux sources first. So I open up my Synaptic and I find: kernel 2.6.10-34 

Now I'm not sure if I should install/download this kernel since there's  version difference, and I can't force version on that package.

Is it okay to use the other build?

UPDATE: I downloaded the new code and extracted the new code to /usr/src/linux-source-2.6.10/ but I see no "Build" dir in here, so I'm kinda stuck now.

---

### Post by tbresson on 2005-06-27
Hmm.. I tried to install an Ubuntu on another computer and my samba is working as it should which means it's the network driver that's acting up. The driver works fine for internet connection, and passes the tests and such but the driver is not the best driver for the card. Larger size files copied over LAN doesn't work, and I believe it might have been a problem on Windoze to.. one time in the past. But upgrading the driver should sovle the problem.

But I don't know how to upgrade my network card.

As described above, I found the driver but I can't install it since there needs to be some sort of build dir with the sources of the linux kernel.

Can someone PLEASE help me with this? ...

---

### Post by tbresson on 2005-07-09
Here's the problem:

When trying "make clean modules" on RealTek's newest driver for Linux 2.6.x I get this:

// ... stuff ...
make[2]: Entering directory '/usr/src/linux-headers-2.6.10-5-386'
  CC [M]   /home/cs/RealTek/src/r8169_n.o
/home/cs/RealTek/src/r8169_n.c: In function 'rtl8169_init_ring':
/home/cs/RealTek/src/r8169_n.c:1342: warning: implicit declaration of function 'pci_dma_sync_single'
  LD [M]   /home/cs/RealTek/src/r8169.o
  Building modules, stage 2.
  MODPOST
*** Warning *pci_dma_sync_single* [/home/cs/RealTek/src/r8169.ko] undefined!
  CC      /home/cs/RealTek/src/r8169.mod.o
  LD [M]  /home/cs/RealTek/src/r8169.ko
// ... stuff ...

What should I do ???

---

### Post by kleeman on 2005-07-09
It may be that you need to install the kernel-headers package for your particular kernel as well. On my box the subdirectory you show as missing is present and linked to /usr/src/linux-headers-2.6......

---

### Post by tbresson on 2005-07-10
Yes, the problem at first was the missing linux-headers .. and for the correct version aswell.

But I did that .. and I got the link on the "build" dir to the linux-headers and now I don't get the error about the missing dir, but the error about dma as you can see above.

---

### Post by kleeman on 2005-07-10
I downloaded and compiled your driver and got the warning you got. It doesn't look serious to me... Did you install and load the module (make install    depmod -a    insmod  r8169)?

---

### Post by tbresson on 2005-07-11
I did like this:

make clean modules
make install 
depmod -a 

rebooted and then there was no traffic at all on the network card.

I didn't do "insmod r8169" ... perhaps I should have?

---

### Post by kleeman on 2005-07-11
Check whether it is loaded or not with

lsmod | grep r816

If not load it with insmod.
If it is loaded try to see what went wrong with 

dmesg | grep eth

If you load it then bring the network up with
sudo ifconfig eth0 up
sudo dhclient eth0

I am assuming here that your interface is called eth0 and you are using dhcp to set network parameters. This may not be correct  :smile:

---

### Post by tbresson on 2005-07-11
Thanks.

I'll try it as soon as possible :o) and yes it's called eth0 and I'm using dhcp

---

