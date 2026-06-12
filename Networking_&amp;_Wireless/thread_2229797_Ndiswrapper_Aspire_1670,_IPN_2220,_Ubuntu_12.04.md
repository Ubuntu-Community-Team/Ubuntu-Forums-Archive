---
title: "Ndiswrapper Aspire 1670, IPN 2220, Ubuntu 12.04"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by rafiqcombrinck on 2014-06-15
Hi All

I have revived my old Acer Aspire 1670 only to be reminded of the wireless troubles it gave me back in the day.

I did a fresh 12.04 install and then after reading quite a few ndiswrapper posts, I installed ndisgtk with all the little bits (source, dkms etc.) that go along with it.

When following this to do list, as per ([http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)) ... 

sudo make
sudo make install
sudo modprobe ndiswrapper
gksudo gedit /etc/modprobe.d/ndiswrapper.conf
<< delete all the entries here. it will re create it>>
sudo ndiswrapper -m
lsmod | grep ndiswrapper
<<it should list your module>>
gksu gedit /etc/modules
<< add *ndiswrapper* to the end of this file>>
sudo reboot

When running the "sudo make" command, I end up with an error about not finding some .config file, but that seems to be because it is looking at the wrong kernel. If I specify the right kernel in the "Makefile" it starts to do it's thing, but then returns even more errors ...

/usr/src/modules/ndiswrapper$ sudo make
make -C /usr/src/linux-headers-3.2.0-64-generic M=/usr/src/modules/ndiswrapper
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-64-generic'
  CC [M]  /usr/src/modules/ndiswrapper/proc.o
/usr/src/modules/ndiswrapper/proc.c:37:54: error: unknown type name ‘kuid_t’
/usr/src/modules/ndiswrapper/proc.c:37:66: error: unknown type name ‘kgid_t’
/usr/src/modules/ndiswrapper/proc.c:64:9: error: unknown type name ‘kuid_t’
/usr/src/modules/ndiswrapper/proc.c:64:21: error: unknown type name ‘kgid_t’
/usr/src/modules/ndiswrapper/proc.c: In function ‘wrap_procfs_add_ndis_device’:
/usr/src/modules/ndiswrapper/proc.c:505:2: error: implicit declaration of function ‘proc_set_user’ [-Werror=implicit-function-declaration]
/usr/src/modules/ndiswrapper/proc.c:507:2: error: implicit declaration of function ‘do_proc_make_entry’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/usr/src/modules/ndiswrapper/proc.o] Error 1
make[1]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-64-generic'
make: *** [modules] Error 2

Any ideas as to what this means?

Thanks,
R

---

### Post by Bucky Ball on 2014-06-15
Why have you decided to leap at the outdated and problematic ndiswrapper? Please provide the output of this command:

```
sudo lshw -C network
```

Thanks. ;)

PS: Please use [code] tags for terminal output. Much neater and easier to read.

---

### Post by rafiqcombrinck on 2014-06-15
Hi 

 From everything I have read, this card IPN 2220 is and will never be supported in linux, so that only leaves the messy way :rolleyes:

 ```
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:a480(size=32) memory:e8201000-e820101f memory:e8200800-e8200fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:5e:62:55
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:a000(size=256) memory:e8201400-e82014ff
```

Thanks,
R

---

### Post by Bucky Ball on 2014-06-15
Now we actually know what card you're using I think you're right about ndiswrapper being the only alternative. I could find no other. All I can suggest is a little advice from post #3 here regarding the correct driver:

[http://ubuntuforums.org/showthread.php?t=2041194](http://ubuntuforums.org/showthread.php?t=2041194)

Good luck. I have no experience with ndiswrapper (since 8.04 LTS, and then only briefly, so don't remember anything about it) so can't really help any further, sorry. :-k

---

### Post by rafiqcombrinck on 2014-06-24
I finally solved the issue. Seems I royally messed up my Ubuntu install. I tried installing via Unetbootin, using my hard drive and that ended me up with some sort of live session/install abortion. After reinstalling from a DVD, I got ndiswrapper to function properly, well sort of. It would work fine for a few minutes and then stop transferring any data (even though it showed it was still connected).   I ended up just using a usb wifi dongle that I had lying around, connected in about 5 seconds ;)

---

