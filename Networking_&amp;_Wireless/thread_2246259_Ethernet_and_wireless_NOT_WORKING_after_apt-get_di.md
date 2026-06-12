---
title: "Ethernet and wireless NOT WORKING after apt-get dist-update"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by pbjune on 2014-09-29
Hallo,

I have a problem with my 01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13) 
AND 
05:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01) on my Acer Aspire E-522- 65204G1TMnkk, 

My OS is Linux Mint 13 Maya. Kernel version is 3.2.0-69-generic (x86-64).

When I installed the system I had both the ethernet and the wirells card not working, but I solved the problem following this steps: 

"Download compat-drivers source code [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/04/compat-drivers-2013-03-04-u.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/04/compat-drivers-2013-03-04-u.tar.bz2)

Extract the tarball and type the following commands on a terminal:

cd [path-to-extracted-driver] ./scripts/driver-select alx make sudo make install Reboot the system"

the ethernet connection worked well. But still no wireless.

After that, I followed these suggestions for the wireless adapter:

"sudo apt-get install linux-headers-generic build-essential wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2)
tar xvf compat*
cd compat-wireless-3.6.6-1-snpc
sudo su
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit"

And it worked.


Now, a few days ago I made an "apt-get dist-upgrade" command and again here I am with both no ethernet nor wireless working. For the wireless I did: 

paolo-NC-E1-522-65204G1TMNKK compat-wireless-3.6.6-1-snpc # ./scripts/driver-select ath9k
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: drivers/net/wireless/ath/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/bcma/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
paolo-NC-E1-522-65204G1TMNKK compat-wireless-3.6.6-1-snpc # make
./scripts/gen-compat-autoconf.sh /home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/.config /home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-69-generic/build M=/home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.2.0-69-generic"
  CC [M]  /home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/compat/main.o
In file included from /home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/include/linux/compat-3.4.h:32:21: error: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here
make[3]: *** [/home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/compat/main.o] Errore 1
make[2]: *** [/home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc/compat] Errore 2
make[1]: *** [_module_/home/paolo/Scrivania/compat-wireless-3.6.6-1-snpc] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.2.0-69-generic"
make: *** [modules] Errore 2

which reported some errors, as you can see.

Now, how can I solve this?

Thanks a lot.

---

### Post by varunendra on 2014-10-01
> **pbjune said:**
> Now, how can I solve this?

Instead of trying to solve 'this', install one of the latest supported versions. Kernel version 3.8 and later natively support your ethernet card, and ath9k driver may work better too. Both your ethernet and wireless will work out-of-box with any currently supported kernel/OS.

---

