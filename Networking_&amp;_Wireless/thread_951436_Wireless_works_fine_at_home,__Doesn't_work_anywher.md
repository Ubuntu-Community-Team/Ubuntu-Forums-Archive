---
title: "Wireless works fine at home,  Doesn't work anywhere else though !"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Contess on 2008-10-18
Hi

Ubuntu 8.04 Hardy Heron
on, HP Pavilliaon HDX.
-------

Searched the net and this forum without success.

-------

My problem is that Wireless LAN works perfect at home, but whenever I am out of home near a hotspot, regardless what kind, open, encrypted, they are not recognized. The network connection symbol just shows offline.

I have also tried to search for networks using the KWifiManager. Also there no success to find any network even though the guys next to me were surfing the net just fine (on XP ).

I did notice that the network icon never "refreshes" itself. By refreshing, I mean the two blue arrows when searching for network.

Your advice will be greatly appreciated.

thank you

---

### Post by Contess on 2008-10-22
Bump

Does anyone have an idea why I can only WiFi at home but no other places ?

---

### Post by panhandle on 2008-10-22
When you are at the hotspot, what have you done to get your NIC working?

Have you put your card into what the network manager often calls "roaming mode?"

---

### Post by NE Key on 2008-10-22
Not sure if this will help but this is what I do;

At the "strange" place (i.e. away from the home wireless network), boot up.

The network icon shows two monitors. Left click on the icon and it should you the networks it can detect. Choose one and drive on.

If it does not show any networks; Left click and choose Connect to other wireless network.

It will then ask you for a name, which you don't know. Leave it blank and press cancel. (but if you do know the name or ESSID then enter it).This seems to trigger the network manager to look for the available networks. Try the icon again and it should show you the available networks.

I make it work on the basis of "the monkey keeps hitting the keys until something happens". Clicking on the icon and choosing options until it kicks into gear and shows the available networks.

Also left click on the icon, choose manual connection, select connections tab, and check it say "Roaming Mode enabled" under the wireless.

---

### Post by Contess on 2008-10-23
If I click the icon, it does not show any networks.
There is no option that says: Connect to other networks
  It only says: Connection Properties:  two Tabs: General  / Support
when I press "configure" I get an error pop up Saying: The interface does not exist, Check that it is correctly typed and that it is supported by
your system  (By the way, I get this error also at home with functiong Wlan)

<sigh> 





> **NE Key said:**
> 
The network icon shows two monitors. Left click on the icon and it should you the networks it can detect. Choose one and drive on.

If it does not show any networks; Left click and choose Connect to other wireless network.

It will then ask you for a name, which you don't know. Leave it blank and press cancel. (but if you do know the name or ESSID then enter it).This seems to trigger the network manager to look for the available networks. Try the icon again and it should show you the available networks.

I make it work on the basis of "the monkey keeps hitting the keys until something happens". Clicking on the icon and choosing options until it kicks into gear and shows the available networks.

Also left click on the icon, choose manual connection, select connections tab, and check it say "Roaming Mode enabled" under the wireless.

---

### Post by handydan918 on 2008-10-23
Try installing a wireless manager like wlassistant or wicd.

---

### Post by kevdog on 2008-10-23
It seems like you are working through Network Manager.  The Gui interface is good, but it doesnt allow for troubleshooting.  In order to troubleshoot, can you do the following:

Post your:
/etc/network/interfaces

Show me the results of:
iwlist scan

from both at home and then outside of your house (like at cafe).

---

### Post by gjoellee on 2008-10-23
I am not sure but there might be a fix with Network Manager 0.7 (found in Intrepid Ibex)

---

### Post by Contess on 2008-10-23
#############
At home:

suwan@engineering:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

-------

suwan@engineering:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
##########################

I will check the hotspot and update this post

Thanks a bunch

PS: Still waiting for a chance to visit the hotspot, sorry for the delay

---

### Post by Contess on 2008-12-02
Hello Kevdog

I have done the iwlist scan in the hotspots and at home. Here the results:


###########
in Hotspot:
###########

suwan@engineering:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

suwan@engineering:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower checked this
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
suwan@engineering:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


######################


##########
at Home:
##########

suwan@engineering:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

suwan@engineering:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
suwan@engineering:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

suwan@engineering:~$ 


##################


Any ideas ?

---

### Post by Contess on 2008-12-03
All right, here the output at home:

--------
suwan@engineering:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:C0:13:15
                    ESSID:"MyHome"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=-38 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002b54d872fd3
-------

The results from the hotspot will follow soon

---

### Post by kevdog on 2008-12-03
Ok it picks up one network at your house that is encrypted.  I'm guessing WEP.

Can you post also the following
lspci -nn

Also specifically how are you trying to connect?

---

### Post by Contess on 2008-12-04
> **kevdog said:**
> Ok it picks up one network at your house that is encrypted.  I'm guessing WEP.

Can you post also the following
lspci -nn

Also specifically how are you trying to connect?

Hi

1.
yes, you are correct, the home connection is WEP and there is only one access point, no neighbors around.


2.
>>Also specifically how are you trying to connect?

Well, I don't do anything to connect. I simply boot up the machine and at home Ubuntu finds the network itself through the network manager. 
In any other location than home, the network manager does not find any access points (Wired LAN works fine though), nor do the WiFi scan tools.
When I click the network manager icons (the two black monitors) in the task bar and then click "configure", a warning pops up saying: 
>>
The Interface does not exist. Check that it is correctly typed and that it is correctly supported by your system.
>>
..this also happens at home with the functioning wireless network.

If I go to "System"--"Administration"--"Network" it shows that Roaming mode on Wireless connection (wlan0) and Wired connection is enabled





3.
I will check again the results in a public place, as specified by you tomorrow and I will also try to see if anything is shown in Etherape.

Here the output of sudo lspci -nn in home:

suwan@engineering:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800M GTS [10de:0609] (rev a2)
02:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:06.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:06.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:06.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
20:00.0 Mass storage controller [0180]: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller [1095:3531] (rev 01)
28:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
suwan@engineering:~$

---

### Post by Contess on 2008-12-12
Hi

I did do the 

~$ iwlist wlan0 scan
wlan0     No scan results

in the hotspot but I forgot to do it as sudo, the test did not reveal a result. I will have to go back there again.

However though, I notided that when I do a: sudo lshw -C network
the logical name is wmaster0. Shouldn't it be wlan0 ???


I also used etherape in the hotspot, capturing all interfaces but there was NOTHING AT ALL shown. 

The guys around me were all surfing the net with their Microsoft OS's
on the open unencrypted wireless network.


I also used System-Administration-Network  and Network tools to connect, but I failed.
I also did a manual network restart:  sudo lshw -C network ..which always works at home but it failed to connect.
I also tried the KWiFiManager, scanned for networks but  :(

Can you help from here or do we have to wait until I try the 
sudo sudo iwlist scan  in the hotspot again ?

Please..



#################
IN HOTSPOT

suwan@engineering:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:2b:84:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:28:00.0
       logical name: eth0
       version: 13
       serial: 00:1c:c4:cb:63:f7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
suwan@engineering:~$ 




############
AT HOME:
suwan@engineering:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:2b:84:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.100 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:28:00.0
       logical name: eth0
       version: 13
       serial: 00:1c:c4:cb:63:f7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
suwan@engineering:~$

---

