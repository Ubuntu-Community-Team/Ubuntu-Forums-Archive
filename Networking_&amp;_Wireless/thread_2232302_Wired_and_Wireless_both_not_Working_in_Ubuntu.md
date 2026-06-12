---
title: "Wired and Wireless both not Working in Ubuntu"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by Venkata_Sai_Harsha on 2014-07-01
Hi I have just installed ubuntu 14.04 but both wired and wireless are not working.

Can any one please help me in setting up internet.

I have ran wireless script  with the help of signature on one of the fellow forum members.I am attaching same

```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux harsha-HP-ENVY-15-Notebook-PC 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


01:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2154]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader [10ec:5227] (rev 01)


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:1962]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b40d Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 0a5c:21fb Broadcom Corp. 
Bus 003 Device 006: ID 0951:1625 Kingston Technology DataTraveler 101 II
Bus 003 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####




##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####




##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####




##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####




##### nm-tool #####


NetworkManager Tool


State: connecting


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        A0:1D:48:FF:B7:CE


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on






##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####




##### iwlist channel #####




##### modinfo #####




##### modules #####




lp
rtc


##### blacklist #####



```

---

### Post by Venkata_Sai_Harsha on 2014-07-01
Can any one please help me in solving this issue? I have already ran the wireless script.
Please find the same in code tags above.

---

### Post by grahammechanical on 2014-07-01
You need to explain what you mean by "not working." Did you install Ubuntu with an Internet connection? Was it a wired connection? Do you see a Network Manager icon in the top panel on the right? Have you clicked it to see the menu? Does it list wireless access points in range? Is there a tick mark against Enable Networking and Enable Wireless? Have you tried to make a connection to the router?

You need to tell us what signs and messages Ubuntu gave when you tried these things.

From that printout I would say that both the wired (ethernet) adapter and the WiFi adapter are not working. There is no printout from  iwconfig or route, or nm-tool or iwlist or iwlist channel. And there should be something. This is what I get from iwlist with WiFi enabled or disabled

> Usage: iwlist [interface] scanning [essid NNN] [last]
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

Now iwlist channel with WiFi enabled

> eth0      no frequency information.


eth1      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)


Now with WiFi disabled

> eth0      no frequency information.


eth1      no frequency information.


lo        no frequency information.



wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz


Do you see what is missing. But in your case there is no output and there should be something if the ethernet and the WiFi adapters had power going to them.

Are WiFi and Ethernet switched off in the BIOS/UEFI boot system?

Regards.

---

