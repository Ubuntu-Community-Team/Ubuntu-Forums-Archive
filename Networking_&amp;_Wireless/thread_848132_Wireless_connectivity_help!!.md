---
title: "Wireless connectivity help!!"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by pawantahiliani on 2008-07-03
hey everyone..

i use an hp dv 9000 (two 120 gb SATA hdd and hd dvd drive for the least...)...i just got ubuntu in yesterday...total n00b and it doesn't detect my wireless connection...

can anyone please help? posted below are the lspci and lshw -C network which are useful i guess:S

pawan@pawan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


pawan@pawan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:a2:47:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:1e:68:2a:11:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 ip=192.168.1.106 latency=0 module=e1000 multicast=yes


....?

---

### Post by chili555 on 2008-07-03
Network Manager, which is installed by default, will not allow your wireless to connect, as long as you have a good wired ethernet connection and an IP address, which you do:> ip=192.168.1.106 Please see: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager) especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedPlease unplug the wire and see if your wireless works.

---

### Post by karlatsaic on 2008-07-03
> **pawantahiliani said:**
> hey everyone..
pawan@pawan-laptop:~$ lspci
...
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
...
pawan@pawan-laptop:~$ lshw -C network
...
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

I have a Dell XPS M1330N laptop with the same network card as you and the same driver state via lshw -C network. My card was not connecting either. Since I had a first generation Linksys 802.11b wireless router and had been intending to upgrade anyway, the wifi now works perfectly with a Linksys WRT160N (802.11n) router. It's as if either Network Manager or the driver itself refused to switch to 802.11b and insisted on 802.11g. I know upgrading h/w is not a satisfactory answer (the old days of Microsoft) but it may work for you and it may give the hard-working folks who provide the open source software a clue as to what needs fixing. I have another, older laptop where wifi is completely busted as well. - trying hard to not go the ndiswrapper route.

---

### Post by pawantahiliani on 2008-07-13
hey...i think i have a linksys wireless 802.11b router...

but ive checked all other forums..apparently intel pro/wireless 3945 has driver issues? can you tell me how to get it to work, ASSUMING there is a valid wireless?:S...

to answer chili555's post, yes i tried..i did the manual wire connected as a desperate attempt to work something out, i was trying to work out the wireless..

ive uninstalled ubuntu and reformatted my pc until this issue is theoretically solved..or ill probably ask a professor when im at umich this fall...

---

### Post by pawantahiliani on 2008-07-13
by the way...i forgot to mention this i guess

the wireless can be located, it does detect the wireless connection, but it asks for the code

now..usually linksys has 192.168.1.1 and the user id and password as "admin" (both)....

for some reason my gateways password is NOT admin and i cannot access the wireless configuration..so im stuck...i dont remmber the code...its a 10 digit code..i think WEP:S...

i enter the code..it keeps asking for the code again and again...and never connects to linksys...

any help now?

---

