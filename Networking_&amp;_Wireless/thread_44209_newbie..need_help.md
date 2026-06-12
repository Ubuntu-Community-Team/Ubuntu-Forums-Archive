---
title: "newbie..need help"
date: 2005-06-24
forum: Networking &amp; Wireless
---

### Post by phyz on 2005-06-24
hello guys..

i've got problem which my detection wizard in ubuntu v5.04 were stuck during detect network card.There so i could not be able to connect any modem to internet using dail up...

Pentium 4 2.4G
780Mb DDRAM
netodragon pci modem
aztech external modem
graphic,sound&networkcard were onboard
compro gold tvcard

actually,i've installed this machine (dekstop)with  the free original cd ubuntu that i've ordered

what should i do to configure those hardware well in my machine?
pls help me!

-malaysian newbie linux-

---

### Post by Lunde on 2005-06-25
[QUOTE=phyz]hello guys..

i've got problem which my detection wizard in ubuntu v5.04 were stuck during detect network card.There so i could not be able to connect any modem to internet using dail up...

Pentium 4 2.4G
780Mb DDRAM
netodragon pci modem
aztech external modem
graphic,sound&networkcard were onboard
compro gold tvcard

actually,i've installed this machine (dekstop)with  the free original cd ubuntu that i've ordered

what should i do to configure those hardware well in my machine?
pls help me!

-malaysian newbie linux-[/QUOTE]
 Some cut & Paste from the net for you, I've never tried any of these drivers, so I'm not able to provide detailed help for you.

**netodragon pci modem:**
NetoDragon is from Winmodems family, so it doesn't work according to the manufacturer. But I've found out the driver that makes it work. You may download it at: [http://www.adrianstaffolani.com.ar/netodragon/slmdm-2.7.10_debug.tar.gz](http://www.adrianstaffolani.com.ar/netodragon/slmdm-2.7.10_debug.tar.gz)

**aztech external modem:**
[http://modem.free-driver-download.com/Aztech/13085/Aztech-Modem-USB-External-UM-9100-Driver-2.8.3-Linux.html](http://modem.free-driver-download.com/Aztech/13085/Aztech-Modem-USB-External-UM-9100-Driver-2.8.3-Linux.html)

**Modems in general:**
To configure the modems look at this wiki page for help
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

**Compro gold tvcard:**
[http://ubuntuforums.org/archive/index.php/t-104.html](http://ubuntuforums.org/archive/index.php/t-104.html)

---

### Post by phyz on 2005-06-30
dear lundle,

i've tried to $ make KERNEL_INCLUDES=/path/to/linux/inludes ... then terminal result  shows gcc:error(127)invalid '...'

then i've tried to $ make KERNEL_INCLUDES=/path/to/linux/inludes witout '...' and i've tried to put in KERNEL_INCLUDES=/path/to/linux/inludes into makefile..the same error comes out


while my external modem 56k aztech EM6800-U during internet connection were at 978/s in other words always under 1kb....i've used suse 9.1 with the same modem but the connection reach up to 48k-52k...

tvcard compro,i have'nt done yet because i need to speed up my internet connection first...


what should i do?

---

### Post by Lunde on 2005-07-01
[QUOTE=phyz]dear lundle,

i've tried to $ make KERNEL_INCLUDES=/path/to/linux/inludes ... then terminal result  shows gcc:error(127)invalid '...'

then i've tried to $ make KERNEL_INCLUDES=/path/to/linux/inludes witout '...' and i've tried to put in KERNEL_INCLUDES=/path/to/linux/inludes into makefile..the same error comes out


while my external modem 56k aztech EM6800-U during internet connection were at 978/s in other words always under 1kb....i've used suse 9.1 with the same modem but the connection reach up to 48k-52k...

tvcard compro,i have'nt done yet because i need to speed up my internet connection first...


what should i do?[/QUOTE]
 Just to clear something up first..
**KERNEL_INCLUDES=/path/to/linux/inludes**
should be:
**KERNEL_INCLUDES=/usr/src/linux-headers-2.6.10-5-686**
[B]
Note:[/B] The 2.6.10-5-686 you need to change to correct headers for your kernel, this you can find out by writing in terminal
**$ uname -r**

You may not have installed the Linux headers, you can do this with this command:
**$ sudo apt-get install linux-headers-`uname -r`**

Your external modem... If Suse can, so can Ubuntu.

---

