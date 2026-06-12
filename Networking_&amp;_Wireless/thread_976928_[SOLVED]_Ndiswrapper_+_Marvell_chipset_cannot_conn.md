---
title: "[SOLVED] Ndiswrapper + Marvell chipset cannot connect in 8.10"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Bolverk on 2008-11-09
I have an internal wireless PCI card from Linkskey. It's a Marvell Libertas chipset. Ndiswrapper is installed, the driver is installed, and the card can see the available wireless networks. However, it cannot connect. This is a dual-boot machine and the card works under Windows, and I used the same driver for ndiswrapper. On top of that, this card worked in 8.04.

lspci:
```
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

lspci -n:
```
00:00.0 0580: 10de:005e (rev a3)
00:01.0 0601: 10de:0050 (rev a3)
00:01.1 0c05: 10de:0052 (rev a2)
00:02.0 0c03: 10de:005a (rev a2)
00:02.1 0c03: 10de:005b (rev a3)
00:04.0 0401: 10de:0059 (rev a2)
00:06.0 0101: 10de:0053 (rev a2)
00:07.0 0101: 10de:0054 (rev a3)
00:08.0 0101: 10de:0055 (rev a3)
00:09.0 0604: 10de:005c (rev a2)
00:0a.0 0680: 10de:0057 (rev a3)
00:0b.0 0604: 10de:005d (rev a3)
00:0c.0 0604: 10de:005d (rev a3)
00:0d.0 0604: 10de:005d (rev a3)
00:0e.0 0604: 10de:005d (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:07.0 0200: 11ab:1faa (rev 03)
05:00.0 0300: 10de:0641 (rev a1)
```

ndiswrapper -l:
```
mrv8000c : driver installed
	device (11AB:1FAA) present
```

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 08:10:74:16:80:8f  
          inet6 addr: fe80::a10:74ff:fe16:808f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66680 (66.6 KB)  TX bytes:28882 (28.8 KB)
          Interrupt:17 Memory:fe9e0000-fe9f0000 
```

iwconfig:
```
wlan0     IEEE 802.11g  ESSID:"Home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:EE:44:D2   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:EE:44:D2
                    ESSID:"Frontier"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```


I have not compiled ndiswrapper from source. I have installed and removed the ndiswrapper driver using commandline and ndisgtk. ndisgtk cannot find a network configuration tool, but installs the driver. Any help in getting this thing to connect would be greatly appreciated.

---

### Post by Bolverk on 2008-11-09
More information:

Did not know of the lshw -C command until I read the [Manual Configuration]("http://ubuntuforums.org/showthread.php?t=571188") thread. 

lshw -C network:
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
```

According to that thread, it's probably an ndiswrapper problem. So I've been reading the [Troubleshooting Ndiswrapper]("http://ubuntuforums.org/showthread.php?t=538448") thread and the only piece of advice it could offer was to compile ndiswrapper from source. Well, the compilation from source on 1.53 and 1.52 fails on the same error:
```
iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
```

I'm going to reinstall ndiswrapper from synaptic and if that doesn't work I'll try to compile it again. Any ideas?

---

### Post by Bolverk on 2008-11-09
Even more information:

Found out that ndiswrapper has to be patched to compile with the 8.10 kernel. Patched it, but needed to use -p0 instead of -p1: 

*patch -p0 < ndiswrapper_kernel_2.6.27.patch*

So now output of lshw -C network is:
```
  *-network DISABLED      
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wlan1
       version: 03
       serial: 08:10:74:16:80:8f
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.53+Marvell,02/22/2005,3.1.1.7 latency=32 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

But it still won't connect. I'm giving up for the night.

---

### Post by Bolverk on 2008-11-15
Well, I tried Fedora 9 and had the same problem: ndiswrapper sees the card, the driver is properly installed, the network is visible, but the computer can't connect to the network. The only thing I can think of is that the problem is linked to the 2.6.27 kernels. I could *really* use some help here. Any ideas?

---

### Post by caljohnsmith on 2008-11-15
Are you using Ubuntu Intrepid 32-bit? If so, I also have a wireless card that uses the Libertas 8335 chipset, and it works great; you could give my driver a shot and see if it makes any difference. I've attached it to this post. Let me know how it goes.

---

### Post by Bolverk on 2008-11-16
Well, your driver worked. Excuse me while I pound my head on the desk here for a minute. I never thought it would be the driver, since I grabbed the driver off the CD I used to install the driver on Windows. :confused:

TYVM!  ):P

---

### Post by caljohnsmith on 2008-11-16
That's great news, I'm glad it worked; cheers and have fun with Ubuntu. :)

---

### Post by irishrm on 2008-11-16
A big thank you from irshrm for your help.  I'm another head banger whose being trying to solve this problem for ages using the driver which works with windows. thanks again.

---

### Post by PiErRoT_ on 2009-01-21
I`m with other trouble...

my PCI wireless card is the same of you. Marvell 88w8335.

I have installed it with ndiswrapper. 

The problem is that I can CONNECT with my WEP wireless, but I can`t surf into the web.

Any ideas?

thank you!

---

### Post by caljohnsmith on 2009-01-21
PiErRoT_, have you tried connecting without encryption (set your router to be an open WLAN)? If so, does that work? How about also posting:
```
ifconfig
iwconfig
ndiswrapper -l
lsmod | grep ndiswrapper
dmesg | grep -ie wlan0 -ie ndiswrapper
```

---

### Post by PiErRoT_ on 2009-01-23
First, sorry for the time I was offline.

So, there's go my lists

#ifconfig
```
eth0      Link encap:Ethernet  Endereço de HW 00:1a:92:9e:aa:3d  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:23 Endereço de E/S:0x4000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:245 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:245 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:15440 (15.4 KB) TX bytes:15440 (15.4 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:03:2f:3c:5e:73  
          inet end.: 10.1.1.8  Bcast:10.255.255.255  Masc:255.0.0.0
          endereço inet6: fe80::203:2fff:fe3c:5e73/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:36 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:4552 (4.5 KB)
          IRQ:17 Memória:f9fe0000-f9ff0000 


```

#iwconfig
```
wlan0     IEEE 802.11g  ESSID:"GUEDES"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:45:01:0F   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

#ndiswrapper -l
```
mrv8335 : driver installed
	device (11AB:1FAA) present

```

#lsmod | grep ndiswrapper
```
ndiswrapper           196380  0 
usbcore               148848  7 usb_storage,libusual,ndiswrapper,usblp,uhci_hcd,ehci_hcd

```

#dmesg | grep -ie wlan0 -ie ndiswrapper

```
[   19.864827] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.972070] ndiswrapper: driver mrv8335 (TRENDnet,08/22/2005,3.2.1.3) loaded
[   19.972452] ndiswrapper 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.975244] ndiswrapper: using IRQ 17
[   20.242668] wlan0: ethernet device 00:03:2f:3c:5e:73 using NDIS driver: mrv8335, version: 0x3020002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   20.242697] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.257720] usbcore: registered new interface driver ndiswrapper
[  125.012018] wlan0: no IPv6 routers present

```

The strange in my case is that I can't configure my network... It seems connect, but I can't surf into the web.

Here, the connection is by one fixed IP, and in trough the router D-Link is distributed by DHCP for other machines in this Network.

The most strange is when I atribute an IP, it connects but it cant take a Adress :

#syslog.conf
```
Jan 16 13:46:58 truncatus syslogd 1.5.0#2ubuntu6: restart.
Jan 16 13:46:58 truncatus anacron[5090]: Job `cron.daily' terminated
Jan 16 13:46:58 truncatus anacron[5090]: Normal exit (1 job run)
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) starting connection 'Auto GUEDES' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto GUEDES' has security, but secrets are required. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto GUEDES' has security, and secrets exist.  No new secrets needed. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'ssid' value 'GUEDES' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'wep_key1' value '<omitted>' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 13:49:05 truncatus NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Jan 16 13:49:05 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): device state change: 5 -> 3 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) starting connection 'Auto GUEDES' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto GUEDES' has security, and secrets exist.  No new secrets needed. 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'ssid' value 'GUEDES' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'wep_key1' value '<omitted>' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 13:49:10 truncatus NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 16 13:49:10 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan 16 13:49:12 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Jan 16 13:49:17 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 3 
Jan 16 13:49:17 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Jan 16 13:49:17 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Jan 16 13:49:17 truncatus NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'GUEDES'. 
Jan 16 13:49:17 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 16 13:49:17 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Jan 16 13:49:17 truncatus NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Jan 16 13:49:17 truncatus NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Jan 16 13:49:17 truncatus dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jan 16 13:49:17 truncatus dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 16 13:49:17 truncatus dhclient: All rights reserved.
Jan 16 13:49:17 truncatus dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 16 13:49:17 truncatus dhclient: 
Jan 16 13:49:17 truncatus NetworkManager: <info>  dhclient started with pid 7157 
Jan 16 13:49:17 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 16 13:49:17 truncatus NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Jan 16 13:49:17 truncatus dhclient: Listening on LPF/wlan0/00:03:2f:3c:5e:73
Jan 16 13:49:17 truncatus dhclient: Sending on   LPF/wlan0/00:03:2f:3c:5e:73
Jan 16 13:49:17 truncatus dhclient: Sending on   Socket/fallback
Jan 16 13:49:21 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan 16 13:49:28 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan 16 13:49:38 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan 16 13:49:48 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Jan 16 13:50:02 truncatus NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Jan 16 13:50:02 truncatus NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 7157 
Jan 16 13:50:02 truncatus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan 16 13:50:02 truncatus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Jan 16 13:50:02 truncatus NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'Auto GUEDES'. 
Jan 16 13:50:02 truncatus NetworkManager: <info>  (wlan0): device state change: 7 -> 6 
Jan 16 13:50:02 truncatus NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Jan 16 13:50:02 truncatus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 13:50:11 truncatus NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 13:50:11 truncatus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto GUEDES' has security, and secrets exist.  No new secrets needed. 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'ssid' value 'GUEDES' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'wep_key1' value '<omitted>' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Jan 16 13:50:11 truncatus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 13:50:15 truncatus NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan 16 13:50:15 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Jan 16 13:50:15 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan 16 13:50:17 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Jan 16 13:50:22 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 3 
Jan 16 13:50:22 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Jan 16 13:50:22 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Jan 16 13:50:22 truncatus NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Jan 16 13:50:22 truncatus NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'GUEDES'. 
Jan 16 13:50:22 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 16 13:50:22 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Jan 16 13:50:22 truncatus NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Jan 16 13:50:22 truncatus NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Jan 16 13:50:22 truncatus dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jan 16 13:50:22 truncatus dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 16 13:50:22 truncatus dhclient: All rights reserved.
Jan 16 13:50:22 truncatus dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 16 13:50:22 truncatus dhclient: 
Jan 16 13:50:22 truncatus NetworkManager: <info>  dhclient started with pid 7205 
Jan 16 13:50:22 truncatus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 16 13:50:22 truncatus NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Jan 16 13:50:22 truncatus dhclient: Listening on LPF/wlan0/00:03:2f:3c:5e:73
Jan 16 13:50:22 truncatus dhclient: Sending on   LPF/wlan0/00:03:2f:3c:5e:73
Jan 16 13:50:22 truncatus dhclient: Sending on   Socket/fallback
Jan 16 13:50:22 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jan 16 13:50:26 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan 16 13:50:33 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jan 16 13:50:48 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jan 16 13:51:04 truncatus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jan 16 13:51:07 truncatus NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Jan 16 13:51:07 truncatus NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 7205 
Jan 16 13:51:07 truncatus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
```

And when I let the wireless configuration to atributes an IP by DHCP it can't connect.

The sam results is given by the command
#dhclient wlan0

Thank you for all.

---

### Post by stustustu123 on 2009-01-27
For anyone struggling with a Netgear WG511v2 card with the Marvell chipset (made in China) - give the drivers a go that are posted in this thread.

I was about to throw the card through the window & as a last resort I tried the drivers posted here - the card suddenly came to life.  What a pleasant surprise!  :D

---

### Post by PiErRoT_ on 2009-01-31
Hi stustustu123.

Could you tell us how you did all the process to put up your marvell card?

I`m her getting connection too,but I can`t surf into the web.

post us your 

#ndiswrapper -l

Thank you all.

---

### Post by BallTongue50187 on 2009-02-19
Thanks so much for your driver. I was so upset about the wireless not working and then i found this thread. You saved me from insanity. LOL.

---

### Post by yeye_olive on 2009-05-01
Thank you for posting that driver caljohnsmith, another success story here. That driver made WPA work again, either manually through wpa_supplicant or with Network manager. Here is my setup in case someone experiences the same issues.

Kubuntu 9.04
Kernel 2.6.28-11-generic
ndiswrapper-common and ndiswrapper-utils-1.9 at version 1.53-2ubuntu1

Relevant output of lspci -vvv :
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
        Region 1: Memory at 34010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ndiswrapper

---

### Post by AI8W on 2009-08-05
@[[COLOR=#D40000]**caljohnsmith**[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/member.php?u=530779"):

Thanks for posting those drivers. Fixed my issue as well.

73 de AI8W

---

### Post by celiapgt on 2009-09-11
Thank you for posting THE functional Marvel driver. Mine, which came with the Windows disc, didn't worked. Thanks again,

Celita

---

### Post by abyssign on 2010-01-05
More than one year after the solution of this little Marvell wi-fi problem, another head banger to thank warmly [caljohnsmith]("http://ubuntuforums.org/member.php?u=530779") for the driver that works !

Now I can deploy Ubuntu 9.04 in my little company in Addis Ababa, Ethiopia, and stop using Winbug.

Thanks a lot guys.

---

### Post by stonegroover on 2010-03-08
I can't believe how much of my life has been wasted trying to get this wifi card to work- mine was in the guise of a Linksys WPC54G Ver 5. I feel like downloading 20 copies of those drivers posted in this thread and stashing them in various places. Stupid I know. Thanks again :-)

---

### Post by domi30 on 2012-07-27
thanks to for the 8335 driver

cameo Model: WLG-1101 11g wireless lan
for me

---

### Post by wildmanne39 on 2012-07-27
Old thread closed.

---

