---
title: "No wireless or internet with hardy heron"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by dr-spangle on 2008-05-14
A couple weeks ago I upgraded my dell inspiron 6400 laptop (bought with vista, formatted and gutsy gibbon installed) to Hardy Heron, I had tried the beta out on live disc a few times before and it seemed fine but when i upgraded to hardy heron i immediately noticed that the internet speed seemed at least 10 times slower.
I heard about ndiswrapper from a friend who uses ubuntu and thought it might fix it so i installed it and got some driers from dell and tried to use them... when i used them the internet slowed to a stop so i restarted and it wouldn't boot up, just flashing the caps lock and scroll lock LEDs once a second, as i had everything backed up to an external hard drive I formatted my hard drive and installed ubuntu again, but it won't connect to the internet now, with wireless or with a cable attached, it just asks for the wep key, loads and then asks again a couple minutes later...


my wireless card is an intel PRO/Wireless 3945abg Network connection and my ethernet controller is a Broadcom BCM4401-BO 100Base-TX.

I read somewhere to put "dmesg | grep iw" into terminal... here's the output:

```

r007@r007-laptop:~$ dmesg | grep iw
[   21.433565] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   21.433569] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   21.433756] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.462532] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   22.462948] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   52.964917] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   52.964935] iwl3945: Error Reply type 0x00000001 cmd UNKNOWN (0x40) seq 0x0000 ser 0x00000040
[   52.965597] iwl3945: Error setting Tx power (-5).
[   53.958750] iwl3945: Can't stop Rx DMA.
[ 2868.904098] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 2868.904114] iwl3945: Error Reply type 0x00000001 cmd UNKNOWN (0x40) seq 0x0000 ser 0x00000040
[ 2869.897956] iwl3945: Can't stop Rx DMA.
[ 2872.603990] iwl3945: Error sending REPLY_ADD_STA: time out after 500ms.
[ 2870.556883] iwl3945: Read index for DMA queue txq id (4), index 66, is out of range [0-256] 1 0.
[ 2870.570115] iwl3945: Microcode HW error detected.  Restarting.
[ 2871.069672] iwl3945: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2871.569160] iwl3945: Error sending REPLY_BT_CONFIG: time out after 500ms.
[ 2872.068674] iwl3945: Error sending REPLY_RXON: time out after 500ms.
[ 2872.068682] iwl3945: Error setting new configuration (-110).
[ 2872.568153] iwl3945: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[ 2873.561437] iwl3945: Can't stop Rx DMA.
[ 2876.268325] iwl3945: Error sending REPLY_ADD_STA: time out after 500ms.
[ 2874.220818] iwl3945: Read index for DMA queue txq id (4), index 2, is out of range [0-256] 1 0.
[ 2874.222135] iwl3945: Read index for DMA queue txq id (4), index 3, is out of range [0-256] 1 0.
[ 2874.234457] iwl3945: Microcode HW error detected.  Restarting.
[ 2874.734006] iwl3945: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2875.233523] iwl3945: Error sending REPLY_BT_CONFIG: time out after 500ms.
[ 2875.733001] iwl3945: Error sending REPLY_RXON: time out after 500ms.
[ 2875.733011] iwl3945: Error setting new configuration (-110).
[ 2881.435144] iwl3945: Error sending REPLY_ADD_STA: time out after 500ms.
[ 2879.387675] iwl3945: Read index for DMA queue txq id (4), index 2, is out of range [0-256] 1 0.
[ 2879.388906] iwl3945: Read index for DMA queue txq id (4), index 3, is out of range [0-256] 1 0.
[ 2879.401293] iwl3945: Microcode HW error detected.  Restarting.
[ 2879.900837] iwl3945: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2880.400331] iwl3945: Error sending REPLY_BT_CONFIG: time out after 500ms.
[ 2880.899835] iwl3945: Error sending REPLY_RXON: time out after 500ms.
[ 2880.899845] iwl3945: Error setting new configuration (-110).

```

If you need any other information I will provide it as fast as possible.


Please and thank you.

---

### Post by balagosa on 2008-05-15
not that this might help, but i surely have some issues with intel 3945ABG.

what might be your laptop? Asus, Compaq, Lenovo, etc?

coz i got this issue where specs on the internet lists my laptop as having 3945ABG Wireless Adapter but when i ```
lspci
``` i get Atheros AR5006

---

### Post by Ayuthia on 2008-05-15
> **dr-spangle said:**
> my wireless card is an intel PRO/Wireless 3945abg Network connection and my ethernet controller is a Broadcom BCM4401-BO 100Base-TX.

You might try installing linux-backports-modules-hardy-generic.  There are some things out there for your wireless card.

---

### Post by dr-spangle on 2008-05-15
I tried internet with the cable again and it started working, but wireless doesn't work yet...


@balagosa: Dell, Inspiron 6400


@Ayuthia: ok... I've installed that via apt-get... I'll restart now to see if it works.

---

### Post by dr-spangle on 2008-05-15
It didn't work, it just made the computer really laggy... so I uninstalled it again...

---

### Post by dr-spangle on 2008-05-16
I tried it again today, same effect in that it didn't effect the wireless but made my keyboard and mouse jumpy...


sorry...

our only LAN cable is 150cm long and i have to unplug the desktop to get it... 

if no one knows how to fix it i'll just go back to Ubuntu 7.10 :)

---

### Post by simmcrd on 2008-05-19
Type "ifconfig", and "route -n". This will reveal why your computer is buggy when you plug in you UTP (unshielded twisted-pair).

If you want to use the UTP port instead of WiFi, try issuing "ifconfig wlan0 down" so your computer will know not to try to route packets through the air.

If that doesn't work, try "/etc/init.d/networking restart", then "ifconfig wlan0 down" again.

These steps will NOT fix your WiFi, but should enable you to work with a cable.

IHTH (I hope this helps).

---

