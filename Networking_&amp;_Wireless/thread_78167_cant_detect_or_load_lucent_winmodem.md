---
title: "cant detect or load lucent winmodem"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by GeorgesD on 2005-10-17
Hi I'm having problems getting my winmodem to work on a 'older' Toshiba Satellite 4080xcdt using breezy. I have followed the WinModemLucent how to for hoary ( [https://wiki.ubuntu.com/WinModemLucent](https://wiki.ubuntu.com/WinModemLucent) ) but cant find the ltmodem module in breezy

I have installed Kubuntu 5.10 from the release CD, added the 686 kernel, and restricteded kernels  (both386 and 686) and  downloaded and installed latest updates. Below are listings for my laptop:

georges@Toshiba:~$ uname -a
Linux Toshiba 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux

georges@Toshiba:~$ sudo lspci -v
...
0000:00:07.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
        Subsystem: Toshiba America Info Systems Internal V.90 Modem
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at ffefff00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 02f8 [size=8]
        I/O ports at 1c00 [size=256]
        Capabilities: [f8] Power Management version 2
...

georges@Toshiba:~$ apt-cache policy linux-restricted-modules-2.6.12-9-686
linux-restricted-modules-2.6.12-9-686:
  Installé*: 2.6.12.4-11
  Candidat*: 2.6.12.4-11
 Table de version*:
 *** 2.6.12.4-11 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
        100 /var/lib/dpkg/status


so ltmodem should be there its even listed in the description of the restricted kernel but oddly not in the files when I look in Synaptic, that said its not in kernel drivers as expected in the how to ( or atleast I cant find it ;-(  )

georges@Toshiba:~$ ls -l /lib/modules/2.6.12-9-686/kernel/drivers/char/lt*
ls: /lib/modules/2.6.12-9-686/kernel/drivers/char/lt*: Aucun fichier ou répertoire de ce type <- thats no such file or folder in french ...

and of course modprobe does not work ...

georges@Toshiba:~$ sudo modprobe lt_modem
Password:
FATAL: Module lt_modem not found.
georges@Toshiba:~$ sudo modprobe ltmodem
FATAL: Module ltmodem not found.

Where did I go wrong ? What should I do next ?

Thanks in advance for any help, regards Georges

---

### Post by blastus on 2005-10-17
There have been a number of posts stating that the precompiled Lucent modules are nowhere to be found in Breezy. I haven't tried to install the precompiled modules as the only way I know how to install them is to compile them from source. I can compile them Hoary but [I can't compile them in Breezy.](http://ubuntuforums.org/showthread.php?t=77537) So as I understand, in Breezy there are no precompiled Lucent modules and you can't compile them either!

---

