---
title: "Help getting Brodcom BCM4401-B0 working in feisty"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by earobinson on 2007-05-02
Anyone have a tutorial on how to get the  Brodcom BCM4401-B0 working in feisty.

my lspci output is
> 02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

Thanks

---

### Post by Kobalt on 2007-05-02
There is a kernel module to compile on the Broadcom website for your card : [http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php)
Instructions are inside the zip file.

I don't know if this hardware is supposed to be working out of the box with Feisty... ?

---

### Post by chili555 on 2007-05-02
I understand this is supposed to work with b44.ko. Did you try to modprobe it? You may need to alias it to eth0.

---

### Post by synogenes on 2007-05-04
> **Kobalt said:**
> There is a kernel module to compile on the Broadcom website for your card : [http://www.broadcom.com/support/ethernet_nic/4401.php](http://www.broadcom.com/support/ethernet_nic/4401.php)
Instructions are inside the zip file.

I don't know if this hardware is supposed to be working out of the box with Feisty... ?

I have no idea how to get this to compile.  I too have the same card on an Inspiron 1501 and I've downloaded the driver tar and extracted it.  It contains five files: b44.4, b44.c, b44.h, a Makefile, and the licence file.

Trying to run the gcc compiler on the .c file generates loads of errors presumaby because it can't find half of the headers?

Is there a compiled version of this thing anywhere or some clues as to how to compile it.  I'm new to Ubuntu after being a software developer for years and years on the dark side and I though I understood compilation.  This is tripping me up :(

---

### Post by chili555 on 2007-05-04
In order to compile this, you need two packages, *build-essential linux-headers*. If you have no other internet access, you can get these from your install CD:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
```That's the backtick, up by the 1 on your keyboard.

Of course, apt-get will complain mightily when it cannot reach the internet repositories. You can safely ignore it.

---

### Post by synogenes on 2007-05-06
> **chili555 said:**
> In order to compile this, you need two packages, *build-essential linux-headers*. If you have no other internet access, you can get these from your install CD:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
```That's the backtick, up by the 1 on your keyboard.

Of course, apt-get will complain mightily when it cannot reach the internet repositories. You can safely ignore it.

Thanks for the advice.  I've now installed the linux headers:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The directory I've expanded the tar into has, file b44.c, b44.h, b44.4, Makefile, and LICENSE.  I've gone into the directory using the console, ran sudo make and got a load of errors:

bob@alcala:~/linux-1.00g/linux/b44-1.00g$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/bob/linux-1.00g/linux/b44-1.00g modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/bob/linux-1.00g/linux/b44-1.00g/b44.o
/home/bob/linux-1.00g/linux/b44-1.00g/b44.c:10:26: error: linux/config.h: No such file or directory
/home/bob/linux-1.00g/linux/b44-1.00g/b44.c: In function ‘b44_open’:
/home/bob/linux-1.00g/linux/b44-1.00g/b44.c:1546: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/bob/linux-1.00g/linux/b44-1.00g/b44.c: In function ‘b44_resume’:
/home/bob/linux-1.00g/linux/b44-1.00g/b44.c:2563: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/bob/linux-1.00g/linux/b44-1.00g/b44.o] Error 1
make[1]: *** [_module_/home/bob/linux-1.00g/linux/b44-1.00g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2


Any further help will be greatly appreciated.  Thanks](*,)

---

### Post by chili555 on 2007-05-06
Please see this post: [http://www.linuxquestions.org/questions/showthread.php?t=506363](http://www.linuxquestions.org/questions/showthread.php?t=506363)

You might try installing linux-source from the CD to see if this helps.

However, as I perhaps not too clearly indicated above, b44.ko is built in the kernel you have now! Why compile? Why sweat? Why curse? Please try:```
sudo modprobe b44.ko
ifconfig -a
```Did your ethernet interface show up?

---

### Post by synogenes on 2007-05-07
I'm conscious of diverting this thread into my own personal help, for which apologies if others needing more urgent help.  I've scanned everything I can find about the Broadcom wireless issues.

The cabled card is fine which I think is the BCM4401-B0 100Base-Tx card.  I also have a Broadcom BCM4310 UART built in wireless and that's the one that just doesn't want to play.

Ubuntu is installed from the download disk.  I've since tried various attempts at the ndiswrapper including building 1.34, and also tried the fwcutter all to no avail.  I've tried downloading the driver again, using one of a windows system.

ifconfig lists three interfaces eth0 - the wired card, lo - loopback, and wlan0 which is the wireless card.

iwlist wlan0 scan gives me the details of the router with correct MAC, ESSID and protocol (IEEE 802.11g), mode: managed, and various details about the signal strength, so the card can see the router.

The icon on the panel shows two machines (one behind the other) with red square and white diagonal cross on it, and alongside, a single small orange diamond.  Calling up the connection properties, I see the static IP address I've configured, correct MAC, but the status says Disconnected and the signal strength is 0%.

The network/configure file contains:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.23
netmask 255.255.255.0
gateway 192.168.2.1

auto wlan0
iface wlan0 inet static
address 192.168.2.24
netmask 255.255.255.0
gateway 192.168.2.1    <- which is the router
wireless-ESSID BELKIN  <- not imaginative but there you are
wireless-key xxxxxxxxxx  <- 10 hex digits not separated


The wireless key works on two other non-Linux laptops

I can't ping either way, though via cable I can ping anything on the network both ways.

ndiswrapper -l gives me
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

I have a line in the blacklist file:
blacklist bcm43xx


I did at one point try plugging in a Belkin MIMO G+ USB stick which was detected as having the same chipset as the onboard wireless card - it's recognised as BCM4310 UART as well.  There seems to be no trace of it now in any of the config files and I'm not now trying to use it.

I really appreciate the help from you guys and I'm learning a lot so hopefully I'll be able to contribute help myself in future.

---

### Post by synogenes on 2007-05-10
I've made some progress by using the fwcutter method:
[http://ubuntuforums.org/showthread.php?t=434946&page=2]("http://ubuntuforums.org/showthread.php?t=434946&page=2")

I still can't ping the router but can now at least see it and get a signal. It looks like the problem is now something to do with the wep.

Thanks to everyone who has offered ideas.  This forum is remarkable for its goodwill and generosity.  I hope in future I can contribute in like manner.

---

