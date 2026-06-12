---
title: "DWL-G650 with MASTER wireless-mode"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by deadland on 2006-11-19
Hi there,

I want to setup a wireless router, so I followed the following wiki-entries:

[https://help.ubuntu.com/community/BridgingNetworkInterfaces]("https://help.ubuntu.com/community/BridgingNetworkInterfaces")

and 

[https://help.ubuntu.com/community/UbuntuWirelessRouter]("https://help.ubuntu.com/community/UbuntuWirelessRouter")

But I already get problems, when I want to setup my wireless device in the "Master"-Mode.

```
central@urouter:~$ sudo iwconfig ath0 mode Master
Password:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

```

Some more informations for you:

```
central@urouter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"UCENTRAL"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

br0       no wireless extensions.

```

```
central@urouter:~$ ifconfig
ath0      Protokoll:Ethernet  Hardware Adresse 00:80:C8:1A:09:E3  
          inet6 Adresse: fe80::280:c8ff:fe1a:9e3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

br0       Protokoll:Ethernet  Hardware Adresse 00:80:C8:1A:09:E3  
          inet Adresse:192.168.0.2  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::280:c8ff:fe1a:9e3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

eth0      Protokoll:Ethernet  Hardware Adresse 00:02:3F:72:C4:E0  
          inet Adresse:130.83.220.221  Bcast:130.83.220.255  Maske:255.255.255.128
          inet6 Adresse: fe80::202:3fff:fe72:c4e0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:907192 (885.9 KiB)  TX bytes:176177 (172.0 KiB)
          Interrupt:10 Basisadresse:0x8800 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-80-C8-1A-09-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:6
          TX packets:4500 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199 
          RX bytes:2545 (2.4 KiB)  TX bytes:225000 (219.7 KiB)
          Interrupt:10 Speicher:d0bc0000-d0bd0000 

```

my interfaces-config

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0
auto ath0
auto br0


# The internet network interface
iface eth0 inet dhcp


# The wireless side of the bridge
iface ath0 inet manual
  wireless-essid UCENTRAL
  wireless-key **********
  wireless-mode master

# The local network bridge
iface br0 inet static
  bridge_ports ath0 wifi0
  address 192.168.0.2
  netmask 255.255.255.0

```

Hope, someone can help my.

Thanks for any help.

---

### Post by deadland on 2006-11-19
Some more hardware information:

```
central@urouter:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:72:c4:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=130.83.220.221 multicast=yes
       resources: ioport:3000-30ff iomemory:d2004800-d20048ff irq:10
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@07:00.0
       logical name: wifi0
       version: 01
       serial: 00:80:c8:1a:09:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci multicast=yes wireless=IEEE 802.11g
       resources: iomemory:26000000-2600ffff irq:10
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: br0
       serial: 00:80:c8:1a:09:e3
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.0.2 multicast=yes

```

---

### Post by spd106 on 2006-11-19
It's not so easy with atheros cards, try [http://madwifi.org](http://madwifi.org). You will probably need to compile the latest version of madwifi-ng and use hostap.

---

### Post by deadland on 2006-11-19
I found this:

> Before bridging together the two interfaces we must put the wireless interface (in my case ath0; adjust it to match your setup) in hostap or Master mode. Usually this is as simple as running iwconfig ath0 mode Master, but since wlan support in Linux is not yet standardized, some drivers may need additional configuration. If you have an Atheros-based interface you also need to run the following: wlanconfig ath0 destroy; wlanconfig ath0 create wlandev wifi0 wlanmode ap before the iwconfig command. After that, running iwconfig ath0 will return mode:Master, among others.

But there is no wlanconfig ... ](*,)

---

### Post by deadland on 2006-11-19
@spd106 Thanks for this advice. I can find my Access Point now in the Network. But the clients can not aquire IP adresses.

---

### Post by Paris Heng on 2007-08-10
> **deadland said:**
> Hi there,

I want to setup a wireless router, so I followed the following wiki-entries:

[https://help.ubuntu.com/community/BridgingNetworkInterfaces]("https://help.ubuntu.com/community/BridgingNetworkInterfaces")

and 

[https://help.ubuntu.com/community/UbuntuWirelessRouter]("https://help.ubuntu.com/community/UbuntuWirelessRouter")

But I already get problems, when I want to setup my wireless device in the "Master"-Mode.

```
central@urouter:~$ sudo iwconfig ath0 mode Master
Password:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

```

Some more informations for you:

```
central@urouter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"UCENTRAL"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

br0       no wireless extensions.

```

```
central@urouter:~$ ifconfig
ath0      Protokoll:Ethernet  Hardware Adresse 00:80:C8:1A:09:E3  
          inet6 Adresse: fe80::280:c8ff:fe1a:9e3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

br0       Protokoll:Ethernet  Hardware Adresse 00:80:C8:1A:09:E3  
          inet Adresse:192.168.0.2  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::280:c8ff:fe1a:9e3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

eth0      Protokoll:Ethernet  Hardware Adresse 00:02:3F:72:C4:E0  
          inet Adresse:130.83.220.221  Bcast:130.83.220.255  Maske:255.255.255.128
          inet6 Adresse: fe80::202:3fff:fe72:c4e0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:907192 (885.9 KiB)  TX bytes:176177 (172.0 KiB)
          Interrupt:10 Basisadresse:0x8800 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-80-C8-1A-09-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:6
          TX packets:4500 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199 
          RX bytes:2545 (2.4 KiB)  TX bytes:225000 (219.7 KiB)
          Interrupt:10 Speicher:d0bc0000-d0bd0000 

```

my interfaces-config

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0
auto ath0
auto br0


# The internet network interface
iface eth0 inet dhcp


# The wireless side of the bridge
iface ath0 inet manual
  wireless-essid UCENTRAL
  wireless-key **********
  wireless-mode master

# The local network bridge
iface br0 inet static
  bridge_ports ath0 wifi0
  address 192.168.0.2
  netmask 255.255.255.0

```

Hope, someone can help my.

Thanks for any help.



Use for new Madwifi:-

wlanconfig ath0 destroy 
wlanconfig ath0 create wlandev wifi0 wlanmode ap
ifconfig ath0 up


Just now, your command is for old-madwifi....

---

