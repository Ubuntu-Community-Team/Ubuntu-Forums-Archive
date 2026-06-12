---
title: "Broadcom (bcm43xx) inll problem in Gutsy"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by cokehabit on 2007-07-22
the fwcutter for my bcm43xx broadcom wireless card seems to fail on the install in Gutsy. Feisty is fine.

```
Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum a58843b5ee79d015adf8c54178186487.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 any ideas?

---

### Post by Sollen on 2007-09-19
I have the same problem, please help.

---

### Post by Xeora on 2007-10-08
use the .sys file that you downloaded from elseware... all else fails... here

download attached tar bell
extract into your home folder
open xterm/konsole
and type...

```

sudo bcm43xx-fwcutter -w /lib/firmware/ /home/**{YOUR NAME}**/bcm*.sys

```

---

### Post by michael37 on 2007-10-08
Did not work for me.  I have a Dell Wireless 1390 card, which is 4311 chip.

I tried your firmware package, driver loads and "no scan results".

I downloaded Dell driver from support.dell.com, then unzipped the .EXE and found two .sys files: bcmwl564.sys for 64-bit Windows and bcmwl5.sys for 32-bit Windows.  I have 64-bit Ubuntu.

I tried to use both files from the Dell package (rmmod bcm43xx, delete old firmware, run fwcutter to put new firmware in /lib/firmware, modprobe bcm43xx), and both return with error 

[  343.859567] bcm43xx: Firmware: no support for microcode extracted from version 4.x binary drivers.

Any ideas?

---

### Post by Nerd_bloke on 2007-10-08
I have a similar issue with a BCM4309 card, if i use the 32bit windows xp driver from the Dell site (bcmwl5.sys) through the restricted driver manger,

The card will work ok if wl_apsta.o is used with bcm43xx-fwcutter through the restricted driver manager.

Does this version of bcm43xx-fwcutter no longer support bcmwl5.sys? Documentation is a bit tricky to find.

---

### Post by jonathanmotes on 2007-10-08
My hardware (BCM4311) also uses the bcmwl5.sys file. The install didn't work for me either. It actually took me about 30 minutes to disable it because it slowed my computer down so much! I resorted to downloading Ndiswrapper version 1.48 from Sourceforge.net and compiling it. It works very well.

---

### Post by spd106 on 2007-10-08
It is recommended by the authors that you use the firmware they link to on the Linux Wireless website, [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) because it has been tested the most.

As Ubuntu uses the softmac stack by default, you will have to use version 3 firmware.

Other firmware may work, but it's probably a good idea to stick with these if you want the best results.

---

### Post by michael37 on 2007-10-09
> **spd106 said:**
> It is recommended by the authors that you use the firmware they link to on the Linux Wireless website, [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) because it has been tested the most.

As Ubuntu uses the softmac stack by default, you will have to use version 3 firmware.

Other firmware may work, but it's probably a good idea to stick with these if you want the best results.

OK I uninstalled anything that had any remote connection to bcm43xx and its firmware, and made sure no rogue firmware was in /lib/firmware.

Then, I went into Restricted Driver Manager and enabled bcm43xx Firmware.

Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 158815 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-3_amd64.deb) ...
Setting up bcm43xx-fwcutter (1:006-3) ...

It asked for me which package I want to use, and I pointed it to the "blessed" v3 firmware version which I downloaded from [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware).

After that, only one .fw file popped up in /lib/firmware and the rest of the .fw files were placed in /lib/firmware/2.6.22-13-generic/

Scary stuff: the files are different
~$ diff /lib/firmware/bcm43xx_microcode11.fw /lib/firmware/2.6.22-13-generic/bcm43xx_microcode11.fw 
Binary files /lib/firmware/bcm43xx_microcode11.fw and /lib/firmware/2.6.22-13-generic/bcm43xx_microcode11.fw differ

I loaded bcm43xx driver and it loaded fine.

[79783.147475] bcm43xx driver
[79783.148391] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[79783.148427] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[79785.557052] ADDRCONF(NETDEV_UP): eth0: link is not ready

~$ sudo iwlist eth0 scan
eth0      No scan results

~$ uname -a
Linux longisland 2.6.22-13-generic #1 SMP Thu Oct 4 17:52:26 GMT 2007 x86_64 GNU/Linux

Any other ideas?  As I mentioned earlier, this used to work in Feisty.

---

