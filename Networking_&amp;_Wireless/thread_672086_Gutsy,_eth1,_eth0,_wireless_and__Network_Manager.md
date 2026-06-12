---
title: "Gutsy, eth1, eth0, wireless and  Network Manager"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by pgiraudo on 2008-01-19
I have moved from Feisty to Gutsy and cannot find solution to the following trouble:

In the Network Manager, the connexion eth0 (formelly wireless in Feisty) appears under the name 'etho-rena' but ethernet (in Gutsy). No wireless connexion pops up here. Moreover, in the connexion menu (small red telephone in the menu bar), a wireless connexion 'eth0_rename' has appeared (but is just working receiving network signals, here hpsetup, a wireless network from a printer - to which I can send nothing !).

Has somebody an idea about what is going wrong ?

Thanks in advance...

Patrick


Below my current parameters:

```
cat etc/network/interfaces

auto lo
iface lo inet loopback

giraudoux@giraudoux-laptop:~$ ifconfig

eth1      Lien encap:Ethernet  HWaddr 00:A0:D1:42:EF:AA  
          inet adr:10.0.0.4  Bcast:10.0.0.255  Masque:255.255.255.0
          adr inet6: fe80::2a0:d1ff:fe42:efaa/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:805 erreurs:0 :0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:100 
          Octets reçus:55909 (54.5 KB) Octets transmis:41819 (40.8 KB)
          Adresse de base:0x3000 Mémoire:f8600000-f8620000 

eth0_rena Lien encap:Ethernet  HWaddr 00:13:02:2C:5B:C6  
         adr inet6: fe80::213:2ff:fe2c:5bc6/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         Packets reçus:31 erreurs:0 :141 overruns:0 frame:0
         TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:9709 (9.4 KB) Octets transmis:4000 (3.9 KB)
          Interruption:18 Adresse de base:0x4000 Mémoire:f8900000-f8900fff 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2 erreurs:0 :0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:100 (100.0 b) Octets transmis:100 (100.0 b)


giraudoux@giraudoux-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0_rename  IEEE 802.11b  ESSID:"hpsetup"  Nickname:"hpsetup"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 4A:B4:AA:5D:AD:12   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-29 dBm  Noise level=-30 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:85   Missed beacon:0

ppp0      no wireless extensions.
```

---

### Post by pgiraudo on 2008-01-19
I may have found the way out. Actually moving from Feisty to Gutsy converts  /etc/iftab on upgrade. This has added the command:

```

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:d1:3c:66:73", ATTRS{type}=="1", NAME="eth0"

```

into the file /etc/udev/rules.d/70-persistent-net.rules, which seems to interfere with the following commands:

```

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:13:02:2c:5b:c6", NAME="eth1"

# PCI device 0x8086:0x109a (e1000)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:d1:42:ef:aa", NAME="eth1"
```

Just quoting (or removing later) the converted command and replacing eth1 with eth0 in the wireless address put the things back to normal at reboot.

This reads:

```

giraudoux@giraudoux-laptop:/etc/udev/rules.d$ cat 70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
##SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:d1:3c:66:73", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:13:02:2c:5b:c6", NAME="eth0"

# PCI device 0x8086:0x109a (e1000)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:d1:42:ef:aa", NAME="eth1"

```

Any comment on anticipated undesirable side effect of this welcome !

Cheers,

Patrick

---

