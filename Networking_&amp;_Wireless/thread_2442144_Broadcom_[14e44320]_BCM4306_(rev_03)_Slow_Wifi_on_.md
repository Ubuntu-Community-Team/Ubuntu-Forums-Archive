---
title: "Broadcom [14e4:4320] BCM4306 (rev 03) Slow Wifi on Ubuntu Server 18.04.4"
date: 2020-04-30
forum: Networking &amp; Wireless
---

### Post by roughlea on 2020-04-30
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]Hi,[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]I am experiencing slow wifi with a Linksys WMP54GS v1.0 wireless PCI card, [/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]e.g. apt-get has taken 18 minutes 41 seconds to fetch 459Kb.[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]I am running Ubuntu Server 18.04.4 LTS on an old 32 bit machine,[/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]upgraded from Ubuntu artful 17.10.1 using do-release-upgrade. The issue was [/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]still present on Ubuntu 17.10.1. Posting here in the hope that somebody can[/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]help. The upgrade from Ubuntu 17.10.1 was performed using a Ethernet cable[/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]with a home plug adapter, required for use in the home TV.[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]Using the [wireless-info]("https://ubuntuforums.org/showthread.php?t=370108") tool [/COLOR][COLOR=#000000]the wireless system configuration is: [/COLOR][/FONT][/COLOR]

[SIZE=2][https://pastebin.com/gfzmN9ba](https://pastebin.com/gfzmN9ba)[/SIZE]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]Following the advice from [here]("https://ubuntuforums.org/showthread.php?t=2214110"), I have installed [/COLOR][COLOR=#000000]the *firmware-b43-installer* 
package. The card is recognised [/COLOR][COLOR=#000000]and allocated an IP. However, it is very slow.
I have also tried installing [/COLOR][COLOR=#000000]the firmware from [here]("https://www.lwfinger.com/b43-firmware/no_net_install_bcm43xx_firmware.tar.bz2") but the issue remains.
[/COLOR][/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]After removing the b43 modules and firmware, I tried using *ndiswrapper* with [/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]WMP54GS windows drivers.[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]I can see that the drivers are installed by issuing:[/COLOR][/FONT][/COLOR]

[COLOR=#D4D4D4][FONT=Menlo]*[COLOR=#000000]ndiswrapper -l[/COLOR]*[/FONT][/COLOR]

[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]Device 14E4:4320 is present with an alternate[/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]driver: ssb.[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]I blacklisted *b43* and *ssb *modules and rebooted before [/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]issuing the following commands:[/COLOR][/FONT][/COLOR][COLOR=#D4D4D4][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo]*[COLOR=#000000]ndiswrapper -m[/COLOR]*[/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo]*[COLOR=#000000]modprobe ndiswrapper[/COLOR]*[/FONT][/COLOR]

[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]This gives the kernel error message : *Kernel tried to*[/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]*execute NX-protected page - exploit attempt?*[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]Has anybody managed to get the Linksys WMP54GS v1.0 card working [/COLOR][/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=Menlo][COLOR=#000000]on Ubuntu Server 18.04.4+ using b43 drivers or ndiswrapper?[/COLOR][/FONT][/COLOR]

---

