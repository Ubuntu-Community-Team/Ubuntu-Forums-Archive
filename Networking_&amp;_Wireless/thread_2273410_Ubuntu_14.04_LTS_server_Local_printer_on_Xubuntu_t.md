---
title: "Ubuntu 14.04 LTS server: Local printer on Xubuntu thin client not detected"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by iwan-tan on 2015-04-13
Hi,
Can anybody help with thin client local printer? Server is running Ubuntu 14.04 LTS server, thin client running Xubuntu.
Printer is Epson LQ2170.

lts.conf as follow:
########################################################
# This lts.conf reside in /var/lib/tftpboot/ltsp/i386
########################################################
[default]
    X_COLOR_DEPTH = 16
    LOCALDEV = True
    SOUND = True
    PRINTER_0_DEVICE = /dev/lp0
    PRINTER_0_TYPE = P




#################################################
# WS02 - Enable serial mouse
#################################################
[00:01:03:27:60:BD]
    X_MOUSE_DEVICE = /dev/ttyS0
    X_MOUSE_PROTOCOL = Microsoft


################################################
# WS03
################################################
#[00:01:02:49:A6:71]


################################################
# WS04
################################################
#[00:01:03:21:CD:EA]




###############################################
# WS05 - Enable serial mouse
###############################################
[00:01:02:7C:FB:D5]
    X_MOUSE_DEVICE = /dev/ttyS0
    X_MOUSE_PROTOCOL = Microsoft


###############################################
# WS06
###############################################
#[00:01:02:3B:03:C2]

---

### Post by vsuojanen on 2015-04-13
[https://help.ubuntu.com/community/UbuntuLTSP/LocalAppsLucidPrinting?](https://help.ubuntu.com/community/UbuntuLTSP/LocalAppsLucidPrinting?) You need Cups and drivers In client chroot and configure printer in cups as shared in local network. Then ltsp server publish it to other thin clients.  If you are lucky the drivers are already in the cups package. Read the wiki

---

### Post by iwan-tan on 2015-07-31
Thank you vsuojanen, my apology for late reply due to office moving and just got chance to sit on this. I have applied as per your instruction, however new problem came up/discovered. DosEMU drive mapping does not work. After some tracing, I suspected due to FUSE module not loading, which was confirmed by lsmod fuse command. Therefore I cannot confirm yet whether the printer will work or not. Any thoughts? Thanks once again.

---

### Post by ramesh24 on 2016-03-05
The printer to be installed at LTSP server as HP Jet Direct interface printer. The printer should be pointed to with thin client using its IP number and port number (like 9100, 9101 etc). The printer driver also to be installed in server either by selecting make and model or providing correct printer PPD file.

---

### Post by iwan-tan on 2016-03-15
Hi Ramesh24,

Thanks for your advice, I will try and post the result.

---

