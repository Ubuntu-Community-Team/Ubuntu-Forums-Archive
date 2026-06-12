---
title: "problems setting up a Belkin/Realtec Network card"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by sebwin on 2006-11-05
I recently installed Ubuntu 6.10.
Unfortunately, the network card, a Belkin/Realtek RTL8139 doesn't seem to have gotten installed propperly.
It is recognized and appears in the network controll panel and the hardware manager, but it just doesn't comunicate with the ADSL modem. Also when running the hardware databank wizard from the hardware manager, it gets stuck when it comes to the network section.

So I decided to try and install the Linux driver that came (unsupported) with the card.
The instructions go like this:
```
<F5D5000 Linux kernel driver>

  Version: 2.0.0
  Date:    2004-04-16

  This is the Linux kernel driver released for 
  BELKIN F5D5000 Fast Ethernet Controller.	


<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

Copy the Linuxdrv folder from the CD provided to your hard drive

Create a folder called src in the linux src directory:
	mkdir /usr/src/linux-2.6.13-15/src

Copy Makefile, Makefile_linux24x, Makefile_linux26x, and F5D5000.n into /usr/src/linux-2.6.13-15/src/


  Change to the directory:
	Linuxdrv/

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a
```
Everything went fine up to running 'make clean modules', at which poit I got
```
daniel@computador-da-casa:~/Desktop/Linuxdrv$ sudo make clean modules
make -C src/ clean
make[1]: Entrando no diretório `/home/daniel/Desktop/Linuxdrv/src'
rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
make[1]: Saindo do diretório `/home/daniel/Desktop/Linuxdrv/src'
make -C src/ modules
make[1]: Entrando no diretório `/home/daniel/Desktop/Linuxdrv/src'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/daniel/Desktop/Linuxdrv/src modules
make[2]: Entrando no diretório `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.o
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:694: error: expected ‘)’ before string constant
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:695: error: expected ‘)’ before string constant
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:696: error: expected ‘)’ before string constant
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:697: error: expected ‘)’ before string constant
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:772:5: warning: "MMIO_FLUSH_AUDIT_COMPLETE" is not defined
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c: In function ‘rtl8139_init_board’:
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:1086: error: ‘struct pci_dev’ has no member named ‘slot_name’
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:1087: error: ‘struct pci_dev’ has no member named ‘slot_name’
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:2340:5: warning: "RTL8139_DEBUG" is not defined
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c: In function ‘rtl8139_close’:
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:2826: error: too few arguments to function ‘synchronize_irq’
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c: In function ‘rtl8139CP_close’:
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:2870: error: too few arguments to function ‘synchronize_irq’
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c: At top level:
/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.c:3113: warning: initialization from incompatible pointer type
make[3]: ** [/home/daniel/Desktop/Linuxdrv/src/F5D5Too_n.o] Erro 1
make[2]: ** [_module_/home/daniel/Desktop/Linuxdrv/src] Erro 2
make[2]: Saindo do diretório `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: ** [modules] Erro 2
make[1]: Saindo do diretório `/home/daniel/Desktop/Linuxdrv/src'
make: ** [modules] Erro 2
daniel@computador-da-casa:~/Desktop/Linuxdrv$ 

```
(Sorry, the machine speaks Portuguese!)
I examined line 694 in F5D5Too_n.c and it seems absolutely inoffensive to me.
Lines 692 - 697:
```
MODULE_AUTHOR ("Jeff Garzik <jgarzik@mandrakesoft.com>");
MODULE_DESCRIPTION ("RealTek RTL-8139CP Fast Ethernet driver");
MODULE_PARM (multicast_filter_limit, "i");
MODULE_PARM (max_interrupt_work, "i");
MODULE_PARM (media, "1-" __MODULE_STRING(MAX_UNITS) "i");
MODULE_PARM (full_duplex, "1-" __MODULE_STRING(MAX_UNITS) "i");

```
Can anybody help me out here?

---

### Post by DaveBorealis on 2006-11-05
Hello,

Could you translate 'Entrando no diretório'?  Is it finding the directories it's looking for?

Anyway, it might be easier to find a precompiled binary of the driver that matches your machine's architecture than to debug the program.  Have you tried googling for one?

As an aside, those missing ')' errors are probably not caused by those particular lines of code but by something amiss before them, which could be several lines up, or even in some other part of the program that was fed garbage input, for instance, that it didn't make sense out of.

Best regards,
Dave

---

### Post by sebwin on 2006-11-07
'Entrando' and 'Saindo' mean 'entering' and 'leaving' (the directory) respectively.

I did search for other drivers on the net, but only found another uncompiled version, which I haven't tried yet.

A binary installer would by a blessing in deed!

---

### Post by Lou Gifeth BSc on 2007-02-04
HI, I am new to Ubuntu/Linux and had the same problem.
It's fixed now, here is how in case it helps.

Search on google for "Ubuntu Belkin F5D5000" found the link to [http://www.mepis.org/node/2998](http://www.mepis.org/node/2998) which gave me a clue.
System/Administration/Networking showed my card but not configured.
I configured it using a static IP address, subnet mask and gateway address.
I have ADSL router BT Voyager 2100, got these values from the configuration manager on 192.168.1.1 - expect this is similar on other routers, check your documentation.
e.g.
Configuration = Static IP address
IP address = 192.168.1.5
Subnet mask = 255.255.255.0
Gateway address = 192.168.1.1

Then on the DNS tab I entered the DNS server primary and secondary IP addresses as provided by my ISP - these were also found in the router config manager.

Cheers,
Lou - using newly configured network card.

---

