---
title: "Can't install Ndiswrapper without internet connection following instruction"
date: 2015-07-29
forum: Networking &amp; Wireless
---

### Post by morbo2 on 2015-07-29
This is my first day using Ubuntu 

I installed Ubuntu 14.04 from a file initialized with a USB drive.  The Belkin F7D2101v1 wireless adapter is able to work with a very low connection speed. 
 I am trying to install Ndiswrapper without a connection but keep getting an error message while I follow the instruction from a file named INSTALL of ndiswrapper-1.59

Below is the result from the "make uninstall" command I put into the terminal in the ndiswrapper directory



rex@rex-System-Product-Name:~/&#19979;&#36617;/ndiswrapper-1.59$ make uninstall
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/home/rex/&#19979;&#36617;/ndiswrapper-1.59/driver'
rm -f /lib/modules/3.16.0-30-generic/misc/ndiswrapper.ko
/sbin/depmod -a 3.16.0-30-generic
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.dep.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.dep.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.alias.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.alias.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.softdep.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.symbols.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.symbols.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.builtin.bin.tmp, 1101, 644): Permission denied
depmod: ERROR: openat(/lib/modules/3.16.0-30-generic, modules.devname.tmp, 1101, 644): Permission denied
make[1]: Leaving directory `/home/rex/&#19979;&#36617;/ndiswrapper-1.59/driver'
make -C utils uninstall
make[1]: Entering directory `/home/rex/&#19979;&#36617;/ndiswrapper-1.59/utils'
rm -f /sbin/loadndisdriver
rm -f /usr/sbin/ndiswrapper
rm -f /usr/sbin/ndiswrapper-buginfo
make[1]: Leaving directory `/home/rex/&#19979;&#36617;/ndiswrapper-1.59/utils'


Can anyone help me to install Ndiswrapper so I could possibly fix my slow connection speed?
I can't wait to experience this OS, thank you for your time and patience ):P

---

### Post by wildmanne39 on 2015-07-29
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2015-07-30
You say:> I am trying to install Ndiswrapper Yet your command is:```
make uninstall
```Are you trying to install it or uninstall it??

In order to install or uninstall anything on your system requires administrator privileges; casual passers-by, children, spouses, etc. are not allowed to install Angry Birds! Therefor, your command should be:```
sudo make uninstall
```'sudo' means, roughly, Super User DO. You will be challeged for the password which, ideally, the children do not know, and, if correct, your command will execute.

I sincerely doubt that installing an older, dodgy driver will help in any way your low connection speed. I'd be happy to help troubleshoot the native driver; r8712u, I assume.

---

### Post by morbo2 on 2015-08-04
I ended up reinstalled my Ubuntu 14.04 all over and got a wireless adapter works out of box (Belkin F7D2101)
Thanks for your help nonetheless

---

### Post by Vladlenin5000 on 2015-08-04
[https://wikidevi.com/wiki/Belkin_F7D2101](https://wikidevi.com/wiki/Belkin_F7D2101)

---

### Post by weatherman2 on 2015-08-04
And if you find that the Realtek 8192CU chipset in that dongle isn't working reliably, come back and install the manufacturer driver for it, this way:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

---

### Post by morbo2 on 2015-08-07
my wireless adapter comes with a different chipset as the page mentioned though

Bus 002 Device 004: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]

---

### Post by chili555 on 2015-08-07
> **morbo2 said:**
> my wireless adapter comes with a different chipset as the page mentioned though

Bus 002 Device 004: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]Then you won't need ndiswrapper at all. The driver r8712u, included by default in all recent Ubuntu versions, covers your device. Let's load it and see if the device comes to life:```
sudo modprobe r8712u
```Was a wireless interface created, ideally wlan0?```
iwconfig
```Are there any interesting messages in the log?```
dmesg | grep -e wlan -e r8712u
rfkill list all
```

---

