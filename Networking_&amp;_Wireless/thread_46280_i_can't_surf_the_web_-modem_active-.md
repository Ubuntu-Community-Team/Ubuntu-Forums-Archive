---
title: "i can't surf the web -modem active-"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by fedemw on 2005-07-04
hi friends, thanks a lot for you help.  i had my eagle usb adsl modem up, but can't surf. 

i do startadsl but no way to surf.


take a look:


CONNECTION PROBLEMS

root@lenin:/home/federico # eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.0.0 Chipset: Eagle0
Vendor ID : 0x1110 Product ID : 0x9021 Rev: 0x500b
USB Bus : 001 USB Device : 004 Dbg mask: 0x0
Ethernet Interface : eth1
MAC: 00:60:4c:4e:79:ed
Tx Rate 128 Rx Rate 512
FEC 0 Margin 25 Atten 41 dB
VID-CPE 0 VID-CO 28 HEC 0
VPI 8 VCI 35 Delin GOOD
Cells Tx 272 Cells Rx 174
Pkts Tx 226 Pkts Rx 174
OAM 0 Bad VPI 0 Bad CRC 0
Oversiz. 0

Modem is operational

(light of sincronization is turned ON)



root@lenin:/home/federico # eaglediag
Diagnostic (1.13 2004/08/29) driver eagle-usb 20050703235319
# System Information
Linux lenin 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
3.1
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
gcc versión 3.3.5 (Debian 1:3.3.5-8ubuntu2) used : 3.3.4 (Debian 1:3.3.4-9ubuntu5)
# module loaded ? [ OK ]
# modem operational ? [ OK ]
# Config vpi/vci/encapsulation/isp : 8 23 6 (pppoa) ES03
# pppd launched ? [ KO ]
# ping IP ? [ KO ]
# test DNS resolution ? [ KO ]
Complete diagnostic has been saved on /var/log/eagle-usb/eagle_diag_20050703235319.txt
Please keep only relevant data and remove personal informations.


--> i think pppd is not launched. ¿what can i do?


See configuration files:


more /etc/eagle-usb/eagle-usb.conf

#POTS FOR EAGLE
OPTN0=80020066
# OPTN2=23700000
# OPTN3=00000000
OPTN4=00000000
# OPTN5=00000000
# OPTN6=00000000
# OPTN7=02CD8044
# OPTN15=09090909
VPI=00000008
VCI=00000023

#The following values are valid for encapsulation :
#MPOA_MODE_BRIDGED_ETH_LLC ----> 1
#MPOA_MODE_BRIDGED_ETH_VC ----> 2
#MPOA_MODE_ROUTED_IP_LLC ----> 3
#MPOA_MODE_ROUTED_IP_VC ----> 4
#MPOA_MODE_PPPOA_LLC ----> 5
#MPOA_MODE_PPPOA_VC ----> 6
Encapsulation=00000006

Linetype=00000001
RatePollFreq=00000009
</eaglectrl>
STATIC_IP=none
ISP=ES03
LANG=es
ASYNCHRONOUS_START=1



root@lenin:/home/federico # more /etc/resolv.conf
62.36.225.150
62.37.228.20
nameserver 62.36.225.150
nameserver 62.37.228.20
root@lenin:/home/federico #




Thanks a lot for your help I hope i can surf from ubuntu next connection!

---

### Post by alastair on 2005-07-04
I'm sorry. I would love to help - but the above does not mean much to me at all.

You would be better off :

a) typing "sagem" in the search box and reading what others have said
b) continuing the thread here : [http://www.ubuntuforums.org/showthread.php?t=45974](http://www.ubuntuforums.org/showthread.php?t=45974)
because "coolclassic" seems to know the h/w
c) getting an external non-USB ADSL modem ...

Sorry.

---

