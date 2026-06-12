---
title: "Dell 1390 and HP Laptop"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by iLucid on 2008-07-01
Alright guys so what im doing here is trying to i guess change the vendor id or fake it but im having a problem with one of the steps.

THIS IS WHAT IM TRYING TO DO>

> You have a HP laptop and there is no driver for your miniPCI express card ?
You bought a 15$ dell 1390 card but you can't use it because of the "104 unsupported network device" ?
You don't want to hack your BIOS (but the card SPROM) ?

Here is the howto you need !
(I hope so...)

!!! WARNING, this howto comes with ABSOLUTELY NO WARRANTY, blah, blah, blah !!!

What do I need ?

- An HP notebook with a non friendly miniPCIe wireless card (mine was an Intel Pro Wireless 3945ABG).
- A Dell 1390 miniPCe wireless card (with the bcm4311 chip).
- A GNU/Linux based OS.
- Some hands.

Great. Now how do I get the 1390 card working ?

1. Remove the miniPCI-e card.

2. Start your notebook. After the BIOS check but before the boot of your favorite linux OS (by pausing GRUB for example), put the 1390 card in the miniPCIe slot (be really careful !).

3. Boot up the linux based OS.

4. Check that the bcm43xx linux module is present:
> sudo modprobe bcm43xx
Now, we need the chip firmware:
> wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
We have to extract it to /lib/firmware with the tool bcm43xx-fwcutter
> wget [http://prdownload.berlios.de/bcm43xx/bcm43...ter-006.tar.bz2](http://prdownload.berlios.de/bcm43xx/bcm43...ter-006.tar.bz2)
> tar xvf bcm43xx-fwcutter-006.tar.bz2
> cd bcm43xx-fwcutter-006
> make
> sudo ./bcm43xx-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
Then, reload the module
> sudo rmmod bcm43xx
> sudo modeprobe bcm43xx
Now, turn on the card and try it:
> sudo ifconfig eth1 up
> sudo iwlist eth1 scan
(! the card may not be eth1)
If you get a list of available networks, the card works fine !

(These instructions may not work with special kernel/config/... If so, see [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to get the card working on linux.)

5. Time to hack the card SPROM.
The BIOS checks the subsystem vendor id and product id of the card. So they have to be in the HP whitelist. Here we are lucky: some HP notebooks have a broadcom 4311 based card. The subsystem vendor id is 0x103c (HP) and the subsystem product id is 0x1363. We just need to change these values in the dell card's SPROM.
the tool we need:
> wget [http://linuxwireless.org/download/bcm43xx/...x-sprom.tar.bz2](http://linuxwireless.org/download/bcm43xx/...x-sprom.tar.bz2)
> tar xvf bcm43xx-sprom.tar.bz2
> cd bcm43xx-sprom
> make
Now, hack
> sudo iwpriv eth1 read_sprom > card_sprom
(If eth1 is the dell card)
> ./ssb-sprom -i card_sprom --subv 0x103c --subp 0x1363 > new_sprom
> sudo iwpriv eth1 write_sprom $(cat new_sprom)
We check that's all good
> sudo iwpriv eth1 read_sprom > sprom_check
> ./ssb-sprom -i sprom_check -P
and look at the subsystem vendor/product ID.

6. Reboot and enjoy !

im running a live ubuntu cd.
Ubuntu finds the dell 1390 broadcom driver and scans everything and connects.
when i get to  sudo iwpriv wlan0 read_sprom > card_sprom
I Keep getting wlan0 no private ioctls
i type in only iwpriv i get no private ioctls

how can i pass that no ioctls so i can continue on and get this broadcom to work on my HP Laptop because HP keeps giving me 104 error unsupported network card.

My last place for help

---

### Post by iLucid on 2008-07-01
Anybody out there why am i getting that no ioctls??

---

### Post by iLucid on 2008-07-03
anybody please?

---

