---
title: "NDdisWrapper help"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by louisd11 on 2007-11-13
I am trying to install drivers on ndiswrapper for a Xonet "zew1602" heres where i got so far.

> louis@louis-desktop:~$ sudo ndiswrapper -i mrv8335.inf
installing mrv8335 ...
louis@louis-desktop:~$ sudo ndiswrapper -l
mrv8335 : driver installed
        device (11AB:1FAA) present
louis@louis-desktop:~$ sudo modprobe ndiswrapper
louis@louis-desktop:~$ sudo ndiswrapper -m
module configuration contains directive install pci:v000011ABd00001FAAsv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 790, <MODPROBE> line 236.
module configuration contains directive install pci:v000011ABd00001FABsv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 790, <MODPROBE> line 237.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
louis@louis-desktop:~$ sudo iwconfig wlan0 essid "Lenco" mode Managed
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
louis@louis-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

louis@louis-desktop:~$ 




---

### Post by HermanAB on 2007-11-13
Go to the ndiswrapper web site on sourceforge.  The documentation is excellent.

---

### Post by SpiritIsReality on 2007-11-14
howdy
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
trails

---

