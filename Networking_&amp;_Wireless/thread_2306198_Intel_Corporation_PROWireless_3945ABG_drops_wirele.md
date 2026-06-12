---
title: "Intel Corporation PRO/Wireless 3945ABG drops wireless connection on 14.04 LTS"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by rete2 on 2015-12-13
Hello,

I´ve been having wireless connection issues on my Thinkpad x60 after upgrading to 14.04 LTS. I´ve been using a cable since then which works fine at home, but I´d like to have my wireless working again for traveling...
So I´ve searched the forum and tried this solution [http://ubuntuforums.org/showthread.php?t=2121599](http://ubuntuforums.org/showthread.php?t=2121599) but it didn´t work. 
Here´s the wireless script output:
```
########## wireless info START ##########

Report from: 13 Dec 2015 12:03 CET +0100

Booted last: 13 Dec 2015 11:25 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:35:20 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad X60s [17aa:207e]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad T60/R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              546118  2 iwl3945,iwlegacy
cfg80211              409394  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.178.51  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10133 errors:0 dropped:3 overruns:0 frame:0
          TX packets:9237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8970241 (8.9 MB)  TX bytes:1302550 (1.3 MB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39396 (39.3 KB)  TX bytes:41275 (41.2 KB)

##### iwconfig ##########################

irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       757     1  0 11:25 ?        00:00:08 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

```

---

### Post by praseodym on 2015-12-13
Please show the outputs of
```
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
```
with the cable unplugged

---

### Post by rete2 on 2015-12-13
Now, when I unplugged the cable it couldn´t find any network. That´s different from before. then it would connect, but after a few minutes disconnect again. then I would have to disconnect manually and connect manually and it would work again for a few minutes...

Here´s the result with the cable unplugged:

```
ana@ana-ThinkPad-X60:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

ana@ana-ThinkPad-X60:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d3:3c:69:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19831 errors:0 dropped:3 overruns:0 frame:0
          TX packets:19520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13112418 (13.1 MB)  TX bytes:2995860 (2.9 MB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:305214 (305.2 KB)  TX bytes:305214 (305.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:98:34:bd  
          inet6 addr: fe80::219:d2ff:fe98:34bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41836 (41.8 KB)  TX bytes:49299 (49.2 KB)

ana@ana-ThinkPad-X60:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
ana@ana-ThinkPad-X60:~$ route -n

```

---

### Post by praseodym on 2015-12-13
Please run:
```

sudo apt-get remove --purge resolvconf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4\nnameserver 192.168.178.1" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by rete2 on 2015-12-13
I did that, but the wireless connection is still not working :( it says this: 

```

ana@ana-ThinkPad-X60:~$ sudo apt-get remove --purge resolvconf
[sudo] password for ana: 
Sorry, try again.
[sudo] password for ana: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  fonts-linuxlibertine libmpdec2 libquvi-scripts libquvi7
  linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic
  linux-image-3.13.0-62-generic linux-image-extra-3.13.0-62-generic
  printer-driver-hpijs unity-2d-shell
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  resolvconf* ubuntu-minimal*
0 aktualisiert, 0 neu installiert, 2 zu entfernen und 17 nicht aktualisiert.
Nach dieser Operation werden 312 kB Plattenplatz freigegeben.
Möchten Sie fortfahren? [Y/n] Y
(Lese Datenbank ... 421953 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von ubuntu-minimal (1.325) ...
Entfernen von resolvconf (1.69ubuntu1.1) ...
resolvconf stop/waiting
resolvconf.postrm: Reboot recommended
Löschen der Konfigurationsdateien von resolvconf (1.69ubuntu1.1) ...
Trigger für man-db (2.6.7.1-1ubuntu1) werden verarbeitet ...
ana@ana-ThinkPad-X60:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4\nnameserver 192.168.178.1"
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 192.168.178.1
ana@ana-ThinkPad-X60:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4\nnameserver 192.168.178.1" | sudo tee /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 192.168.178.1
ana@ana-ThinkPad-X60:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 4608


```

I don´t know what most of this means :( Sorry! Should it be working now?

---

### Post by praseodym on 2015-12-13
Please run the wireless-script again.

---

### Post by rete2 on 2015-12-13
thank you so much for your quick responses and help. Here´s the output  of the wireless script. I ran it while the cable was connected. let me  know if I need to do it again without the cable. THANKS again!


```
########## wireless info START ##########

Report from: 13 Dec 2015 16:40 CET +0100

Booted last: 13 Dec 2015 16:14 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:35:20 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad X60s [17aa:207e]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad T60/R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              546118  2 iwl3945,iwlegacy
cfg80211              409394  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.178.51  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3137 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1232375 (1.2 MB)  TX bytes:431240 (431.2 KB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76824 (76.8 KB)  TX bytes:99581 (99.5 KB)

##### iwconfig ##########################

irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

domain fritz.box
search fritz.box
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       665     1  0 16:14 ?        00:00:09 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
```

---

### Post by praseodym on 2015-12-13
Pleas run it again without cable, plus:

```
iwlist chan
sudo iwlist scan
```

---

### Post by rete2 on 2015-12-13
it doesn´t connect at all anymore :( So I can´t run the script... It keeps trying to connect but cannot somehow. And the connection sign in the upper right disappeared completely. should I still run the other code you stated? with the cable? 

```
ana@ana-ThinkPad-X60:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
--2015-12-13 17:20:46--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... failed: Name or service not known.
wget: unable to resolve host address ‘github.com’
ana@ana-ThinkPad-X60:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
--2015-12-13 17:21:19--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... failed: Name or service not known.
wget: unable to resolve host address ‘github.com’

```

---

### Post by weatherman2 on 2015-12-13
FYI, you don't have to keep downloading the script each time (wget) - that one line is several commands on one line (joined by the &&).  Just run the ./wireless-info script you've already downloaded, unless you've erased it.

```
./wireless-info
```

And then, re-connect with the cable and paste the results here.

If you think you've lost or erased wireless-info (the script itself), run the command above in two steps:

(With cable plugged in :  )

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info
```

(Unplug the cable, then run the script : )

```
./wireless-info
```

Then plug the cable back in so you get internet again and post the results.

---

### Post by rete2 on 2015-12-13
Oh, thanks! I didn´t think about that. :( So now I ran the script again without the cable... Any idea what the problem could be? 


```
########## wireless info START ##########

Report from: 13 Dec 2015 23:16 CET +0100

Booted last: 13 Dec 2015 23:05 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:35:20 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad X60s [17aa:207e]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad T60/R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              546118  2 iwl3945,iwlegacy
cfg80211              409394  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1943 errors:0 dropped:3 overruns:0 frame:0
          TX packets:2178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764377 (764.3 KB)  TX bytes:343243 (343.2 KB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37087 (37.0 KB)  TX bytes:57663 (57.6 KB)

##### iwconfig ##########################

irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       737     1  1 23:05 ?        00:00:08 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    mephisto32:      Infra, <MAC 'mephisto32' [AC4]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Weserlan:        Infra, <MAC 'Weserlan' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    FRITZ!Box 7272:  Infra, <MAC 'FRITZ!Box 7272' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Hagis WLAN-Netzwerk: Infra, <MAC 'Hagis WLAN-Netzwerk' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    HITRON-0530:     Infra, <MAC 'HITRON-0530' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Vodafone Hotspot:Infra, <MAC 'Vodafone Hotspot' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    Hagis WLAN-Netzwerk: Infra, <MAC 'Hagis WLAN-Netzwerk' [AC3]>, Freq 5500 MHz, Rate 54 Mb/s, Strength 45 WPA2
    mephisto32:      Infra, <MAC 'mephisto32' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Hitron-2340:     Infra, <MAC 'Hitron-2340' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    FRITZ!Box 7330 SL: Infra, <MAC 'FRITZ!Box 7330 SL' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Halle5_2]] (600 root)
[connection] id=Halle5_2 | type=802-11-wireless
[802-11-wireless] ssid=Halle5_2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN-53B185]] (600 root)
[connection] id=WLAN-53B185 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-53B185 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Air France Lounge 1]] (600 root)
[connection] id=Air France Lounge 1 | type=802-11-wireless
[802-11-wireless] ssid=Air France Lounge 1 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Kaiserstr42]] (600 root)
[connection] id=Kaiserstr42 | type=802-11-wireless
[802-11-wireless] ssid=Kaiserstr42 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN-178526]] (600 root)
[connection] id=WLAN-178526 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-178526 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TeliaGateway08-76-FF-C7-A4-8A]] (600 root)
[connection] id=TeliaGateway08-76-FF-C7-A4-8A | type=802-11-wireless
[802-11-wireless] ssid=TeliaGateway08-76-FF-C7-A4-8A | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SJ]] (600 root)
[connection] id=SJ | type=802-11-wireless
[802-11-wireless] ssid=SJ | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/blablu]] (600 root)
[connection] id=blablu | type=802-11-wireless
[802-11-wireless] ssid=blablu | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/anromo]] (600 root)
[connection] id=anromo | type=802-11-wireless
[802-11-wireless] ssid=anromo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/o2-WLAN39]] (600 root)
[connection] id=o2-WLAN39 | type=802-11-wireless
[802-11-wireless] ssid=o2-WLAN39 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7113]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7113 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7113 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CC WLAN]] (600 root)
[connection] id=CC WLAN | type=802-11-wireless
[802-11-wireless] ssid=CC WLAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Steffens iPhone 4G]] (600 root)
[connection] id=Steffens iPhone 4G | type=802-11-wireless
[802-11-wireless] ssid=Steffens iPhone 4G | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/EasyBox-CF1B08]] (600 root)
[connection] id=EasyBox-CF1B08 | type=802-11-wireless
[802-11-wireless] ssid=EasyBox-CF1B08 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LindncafeBuero]] (600 root)
[connection] id=LindncafeBuero | type=802-11-wireless
[802-11-wireless] ssid=LindncafeBuero | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Supertomate]] (600 root)
[connection] id=Supertomate | type=802-11-wireless
[802-11-wireless] ssid=Supertomate | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RoteHarfe]] (600 root)
[connection] id=RoteHarfe | type=802-11-wireless
[802-11-wireless] ssid=RoteHarfe | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Inteno-B27D]] (600 root)
[connection] id=Inteno-B27D | type=802-11-wireless
[802-11-wireless] ssid=Inteno-B27D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZLB_WLAN1]] (600 root)
[connection] id=ZLB_WLAN1 | type=802-11-wireless
[802-11-wireless] ssid=ZLB_WLAN1 | mac-address=0:19:d2:98:34:bd
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Geschwister-Nothaft-Cafe]] (600 root)
[connection] id=Geschwister-Nothaft-Cafe | type=802-11-wireless
[802-11-wireless] ssid=Geschwister-Nothaft-Cafe | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box 7330 SL]] (600 root)
[connection] id=FRITZ!Box 7330 SL | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7330 SL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Kollektivet]] (600 root)
[connection] id=Kollektivet | type=802-11-wireless
[802-11-wireless] ssid=Kollektivet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7113 1]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7113 1 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7113 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TeliaGateway08-76-FF-C7-A4-8A_EX]] (600 root)
[connection] id=TeliaGateway08-76-FF-C7-A4-8A_EX | type=802-11-wireless
[802-11-wireless] ssid=TeliaGateway08-76-FF-C7-A4-8A_EX | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KHL1]] (600 root)
[connection] id=KHL1 | type=802-11-wireless
[802-11-wireless] ssid=KHL1 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/rainbow]] (600 root)
[connection] id=rainbow | type=802-11-wireless
[802-11-wireless] ssid=rainbow | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOTSPLOTSNathanBibliothek]] (600 root)
[connection] id=HOTSPLOTSNathanBibliothek | type=802-11-wireless
[802-11-wireless] ssid=HOTSPLOTSNathanBibliothek | mac-address=0:19:d2:98:34:bd
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Die drei kleinen Schweinchen]] (600 root)
[connection] id=Die drei kleinen Schweinchen | type=802-11-wireless
[802-11-wireless] ssid=Die drei kleinen Schweinchen | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rapidograph_Anthem]] (600 root)
[connection] id=Rapidograph_Anthem | type=802-11-wireless
[802-11-wireless] ssid=Rapidograph_Anthem | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Kollektivet 1]] (600 root)
[connection] id=Kollektivet 1 | type=802-11-wireless
[802-11-wireless] ssid=Kollektivet | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOTSPLOTSNathanBiblioAP1]] (600 root)
[connection] id=HOTSPLOTSNathanBiblioAP1 | type=802-11-wireless
[802-11-wireless] ssid=HOTSPLOTSNathanBiblioAP1 | mac-address=0:19:d2:98:34:bd
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ch13.freifunk.net]] (600 root)
[connection] id=ch13.freifunk.net | type=802-11-wireless
[802-11-wireless] ssid=ch13.freifunk.net | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WWNET]] (600 root)
[connection] id=WWNET | type=802-11-wireless
[802-11-wireless] ssid=WWNET | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Abraxas]] (600 root)
[connection] id=Abraxas | type=802-11-wireless
[802-11-wireless] ssid=Abraxas | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SCHLAFGUT]] (600 root)
[connection] id=SCHLAFGUT | type=802-11-wireless
[802-11-wireless] ssid=SCHLAFGUT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ekfc]] (600 root)
[connection] id=ekfc | type=802-11-wireless
[802-11-wireless] ssid=ekfc | mac-address=0:19:d2:98:34:bd
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Snoozecube]] (600 root)
[connection] id=Snoozecube | type=802-11-wireless
[802-11-wireless] ssid=Snoozecube | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/selbstuniversitaet]] (600 root)
[connection] id=selbstuniversitaet | type=802-11-wireless
[802-11-wireless] ssid=selbstuniversitaet | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wasserkocher]] (600 root)
[connection] id=Wasserkocher | type=802-11-wireless
[802-11-wireless] ssid=Wasserkocher | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CCRR-2013-WLAN]] (600 root)
[connection] id=CCRR-2013-WLAN | type=802-11-wireless
[802-11-wireless] ssid=CCRR-2013-WLAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FDCL]] (600 root)
[connection] id=FDCL | type=802-11-wireless
[802-11-wireless] ssid=FDCL | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ALICE-WLAN]] (600 root)
[connection] id=ALICE-WLAN | type=802-11-wireless | permissions=user:ana:;
[802-11-wireless] ssid=ALICE-WLAN | bssid=0:16:e3:78:e3:d | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/katulki]] (600 root)
[connection] id=katulki | type=802-11-wireless
[802-11-wireless] ssid=katulki | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/homeahuette]] (600 root)
[connection] id=homeahuette | type=802-11-wireless
[802-11-wireless] ssid=homeahuette | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ditdat]] (600 root)
[connection] id=Ditdat | type=802-11-wireless
[802-11-wireless] ssid=Ditdat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/kfetisch.freifunk-ap]] (600 root)
[connection] id=kfetisch.freifunk-ap | type=802-11-wireless
[802-11-wireless] ssid=kfetisch.freifunk-ap | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7390]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7390 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7390 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bellinis]] (600 root)
[connection] id=bellinis | type=802-11-wireless
[802-11-wireless] ssid=bellinis | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Supertomate 2.0]] (600 root)
[connection] id=Supertomate 2.0 | type=802-11-wireless
[802-11-wireless] ssid=Supertomate 2.0 | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/freifunk-leuchtstoff]] (600 root)
[connection] id=freifunk-leuchtstoff | type=802-11-wireless
[802-11-wireless] ssid=freifunk-leuchtstoff | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Hagis WLAN-Netzwerk]] (600 root)
[connection] id=Hagis WLAN-Netzwerk | type=802-11-wireless
[802-11-wireless] ssid=Hagis WLAN-Netzwerk | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tele2Internet-9F722]] (600 root)
[connection] id=Tele2Internet-9F722 | type=802-11-wireless
[802-11-wireless] ssid=Tele2Internet-9F722 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/cafe langereis]] (600 root)
[connection] id=cafe langereis | type=802-11-wireless
[802-11-wireless] ssid=cafe langereis | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HNEE ITSZ]] (600 root)
[connection] id=HNEE ITSZ | type=802-11-wireless
[802-11-wireless] ssid=HNEE ITSZ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WERKHOF]] (600 root)
[connection] id=WERKHOF | type=802-11-wireless
[802-11-wireless] ssid=WERKHOF | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/viegas]] (600 root)
[connection] id=viegas | type=802-11-wireless
[802-11-wireless] ssid=viegas | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RadialsystemV]] (600 root)
[connection] id=RadialsystemV | type=802-11-wireless
[802-11-wireless] ssid=RadialsystemV | mac-address=0:19:d2:98:34:bd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN-D1BB43]] (600 root)
[connection] id=WLAN-D1BB43 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-D1BB43 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

irda0     no frequency information.

lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz

##### iwlist scan #######################

irda0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FRITZ!Box 7272' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033854901150
                    Extra: Last beacon: 2724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Hagis WLAN-Netzwerk' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Hagis WLAN-Netzwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010328df9c85
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Hagis WLAN-Netzwerk' [AC3]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Hagis WLAN-Netzwerk"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000103253f618f
                    Extra: Last beacon: 1164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'mephisto32' [AC4]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"mephisto32"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000042c83bf03b
                    Extra: Last beacon: 2172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Weserlan' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Weserlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000394dfd495
                    Extra: Last beacon: 3072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Hitron-2340' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Hitron-2340"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a25279157
                    Extra: Last beacon: 12432ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Vodafone Hotspot' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000116925bb62
                    Extra: Last beacon: 23168ms ago
          Cell 08 - Address: <MAC 'mephisto32' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"mephisto32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000042c709b780
                    Extra: Last beacon: 12716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'FRITZ!Box 7330 SL' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7330 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ab5a836bf
                    Extra: Last beacon: 3072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.13.0-71-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     63597F7C72B07A97B142DC2
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-71-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        65:5F:BF:BC:18:C8:19:B0:F7:46:AC:96:CA:27:39:05:6C:CE:87:C5
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-71-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     A847A747E4E6066D74E1D6A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-71-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        65:5F:BF:BC:18:C8:19:B0:F7:46:AC:96:CA:27:39:05:6C:CE:87:C5
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-71-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C8432FAB97804E8F7A8FB0F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-71-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        65:5F:BF:BC:18:C8:19:B0:F7:46:AC:96:CA:27:39:05:6C:CE:87:C5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-71-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-71-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        65:5F:BF:BC:18:C8:19:B0:F7:46:AC:96:CA:27:39:05:6C:CE:87:C5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 0

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwl3945.conf]
options iwl3945 swcrypto=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x109a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x04e8:0x6662 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0bda:0x8171 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  459.416187] e1000e: eth0 NIC Link is Down
[  464.462990] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  475.369060] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  475.369227] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  535.225607] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  535.234303] wlan0: send auth to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  535.243753] wlan0: authenticated
[  535.248047] wlan0: associate with <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  535.257889] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7330 SL' [AC9]> (capab=0x431 status=0 aid=2)
[  535.262172] wlan0: associated
[  581.217729] wlan0: deauthenticating from <MAC 'FRITZ!Box 7330 SL' [AC9]> by local choice (reason=3)
[  584.381158] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  584.385820] wlan0: send auth to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  584.394006] wlan0: authenticated
[  584.396245] wlan0: associate with <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  584.406262] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7330 SL' [AC9]> (capab=0x431 status=0 aid=2)
[  584.407714] wlan0: associated
[  630.220105] wlan0: deauthenticating from <MAC 'FRITZ!Box 7330 SL' [AC9]> by local choice (reason=3)
[  633.408883] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  633.412659] wlan0: send auth to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  633.439014] wlan0: authenticated
[  633.440056] wlan0: associate with <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  633.465360] wlan0: RX AssocResp from <MAC 'FRITZ!Box 7330 SL' [AC9]> (capab=0x431 status=0 aid=2)
[  633.468766] wlan0: associated
[  681.218572] wlan0: deauthenticating from <MAC 'FRITZ!Box 7330 SL' [AC9]> by local choice (reason=3)
[  686.200194] e1000e: eth0 NIC Link is Down
[  688.225113] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  688.229274] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  688.432060] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 2/3)
[  688.636051] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 3/3)
[  688.840058] wlan0: authentication with <MAC 'FRITZ!Box 7330 SL' [AC9]> timed out
[  690.203158] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  700.176873] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  700.178646] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  700.380070] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 2/3)
[  700.584051] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 3/3)
[  700.788056] wlan0: authentication with <MAC 'FRITZ!Box 7330 SL' [AC9]> timed out
[  704.417442] wlan0: authenticate with <MAC 'FRITZ!Box 7330 SL' [AC9]>
[  704.420542] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 1/3)
[  704.624070] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 2/3)
[  704.828075] wlan0: direct probe to <MAC 'FRITZ!Box 7330 SL' [AC9]> (try 3/3)
[  705.032074] wlan0: authentication with <MAC 'FRITZ!Box 7330 SL' [AC9]> timed out

########## wireless info END ############


```

---

### Post by tgalati4 on 2015-12-13
I have a similar card in my T43p.  That card generally works pretty well, so I suspect a hardware problem.  The card might need to be reseated in it's slot.  Not sure how easy it is to get to in the X60.  Sometimes the antenna wires wear out, since they snake through the hinges of the laptop.  

There are only a few switches to play with:

> parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)


Take the battery out for 1/2 an hour, unplug the AC cord, then put the battery back in.  Sometimes this will reset the firmware in the wireless card.

If that doesn't work, then use the switches above and flip one at a time to see if there is a change in behavior.  There are 2 antennae, so turning one off can isolate a bad wire.

---

### Post by weatherman2 on 2015-12-13
You said you upgraded to 14.04 LTS.  Were you using a previous version of Ubuntu and the card used to work?  If so, can you go back and boot live (USB or CD) and try WiFi again?  If that works fine, then I think you can rule out a hardware problem.

---

