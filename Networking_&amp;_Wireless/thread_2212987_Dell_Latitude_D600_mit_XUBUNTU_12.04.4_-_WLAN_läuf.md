---
title: "Dell Latitude D600 mit XUBUNTU 12.04.4 - WLAN läuft nich"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by bebo2 on 2014-03-24
Hi All,

bin nun versuchsweise mit meinem alten Laptop Dell Latitude D600 von Win XP auf XUBUNTU 12.04.4 umgestiegen. Neuere Versionen starteten nicht, wohl wegen fehlender CPU Unterstützung.
*now I switched from WinXP over to XUBUNTU 12.04.4 with my old Laptop Dell Latitude D600. Younger versions do not work because of missing cpu support.*
Installation ist problemlos durchgelaufen + ich kann mich stressfrei anmelden. Updates habe ich auf die Anforderungen hin eingespielt. Dann neu gestartet.
*Installation was without any problems. All required updates have been installed (XUBUNDU told me to do so).*
LAN Internetzugang geht problemlos.
*LAN cable network is working without any problems.*
Nur wollte ich das Teil an mein WLAN hängen. Das ist mir bis dato leider nicht gelungen.
*Now I wanted to connect to my WLAN. Here I didn' succeed.*
In der Taskleiste oben gibt es kein Sysmbol für den Network-Manager. Beim Aufruf desselben (Netzwekverbindungen) über das Menü sind im Reiter Funknetzwerk keine Einträge.
*There is no icon in the upper taskbar for Wifi (network-manager). When I'm starting it, there is nothing in the Window (no wireless networks are to be seen)*

Nach zwei Tagen Recherche bin ich nun zwar etwas schlauer,  aber gelöst habe ich das Problem leider noch nicht.
*After two days of reading and a lot of research, I'm now better involved, but could not solve the problem yet.*

Was habe ich bisher versucht:
*What I tried up to today:*

Mittels  &#65279;/ *With*
sudo apt-get install firmware-b43-installer
habe ich den b43 Treiber nachinstalliert (lt. Anleitung unter [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43))
*I installed the b43 driver (see [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43))*
Lief alles problemlos durch.
*Everything has gone without complaints.*

Dennoch keine Funktion (Auch nicht nach Neustart)
*But still no function - not even after restart*

Auch die Tastenkombination Fn-F2 tut Nichts. Kein Icon in der Taskleiste und kein Eintrag im Network-Manager.
*Button combination Fn-F2 (should switch on/off Wifi) changed nothing. No icon in task bar and nothing in network-manager.*

folgende Analysen habe ich anzubieten:
*here my analysis of the system:*

lspci | grep -i net
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lsmod | grep b43
b43                   342801  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off        
eth0      no wireless extensions.

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

dieses ändert sich nach Betätigen der Tastenkombination Fn-F2 in:
*this changes after pressing Fn-F2 towards:*

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Also geht die Tastenkombination wohl schon.
*So function key seems to work*

Hier bin ich nun vor einer Wand -komme wohl ohne Hilfe hier nicht mehr weiter.
*At this point I'm standing in front of a wall - without help I'm run out of my posibillities.*

Hat jemand einen Tip / noch besser die Lösung für mich?
[I]Is someonr out here with a solution?

[/I]Beste Grüße an Alle[I]
best regards in advance 
[/I]

---

### Post by varunendra on 2014-03-24
If you can understand English -

Possibly a better place to post your problem : [http://forum.ubuntuusers.de/forum/netzwerkkonfiguration/](http://forum.ubuntuusers.de/forum/netzwerkkonfiguration/)

Possibly the best helper who can help you there *(known as user "**praseodym**" here)* : **[elektronenblitz63]("http://ubuntuusers.de/user/elektronenblitz63/")**

I have PM'd "praseodym" to take a look at your post, so you may be able to get some good help here as well.

---

### Post by bebo2 on 2014-03-24
Thanks a lot Varun, and I'M sorry for wrong posting - may be it's why I'm not very experienced in forum writing.

Hope to get some answers instead of my mismatching

Bebo

---

### Post by bebo2 on 2014-03-24
I would try to change it to the other thread, but I couldn't find out how to manage that.

Bebo

---

### Post by praseodym on 2014-03-24
Hi,

you need the file "linux-firmware-nonfree". Checked the German ubuntuusers.de?

[http://ubuntuusers.de/](http://ubuntuusers.de/)

[http://wiki.ubuntuusers.de/WLAN/Karten/Broadcom](http://wiki.ubuntuusers.de/WLAN/Karten/Broadcom)

---

### Post by bebo2 on 2014-03-24
Hi Praseodym,

thanks for tip- I tried it with
sudo apt-get install linux-firmware-nonfree
it went through all  points and finalized well, but then nothing seemed to be different from before

I had a look at the German board, but thought I would get faster and sooner reply here.
Should I post my question again there?

very best regards

Bebo

---

### Post by bebo2 on 2014-03-24
Hi,

what I just now remarked is, that the folder b43 under lib/firmware is protected, so that I can't access it. Window with remark: "Could not open folder" "No rights" (but in German language).
May this be something helpful to get nearer to the solution?

LG (as we say in German)

Bebo

---

### Post by praseodym on 2014-03-24
Lets check```


lspci -nnk | grep -iA2 net
lsmod #total
iwconfig
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by varunendra on 2014-03-24
@ bebo2,

praseodym is already one of the best here and I believe 'there' too, so you are already getting the best kind of help. Although I, or someone else would have started right away had your first post been in English. :)

I hope praseodym won't mind me filling-in while he is away..

I don't think this should matter -
> **bebo2 said:**
> what I just now remarked is, that the folder b43 under lib/firmware is protected, so that I can't access it. Window with remark: "Could not open folder" "No rights" (but in German language).
..because the driver and firmware etc. are accessed as 'root' when system loads them automatically.

I recommend you to please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will contain all the information (command outputs) that praseodym asked for, plus a lot more, except the "ifconfig" part and the "total" output of "lsmod".

So along with the report generated by the script, please post the outputs of "ifconfig" and "lsmod" separately.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

This card shouldn't be too difficult to troubleshoot. In fact, it is usually as easy as running only these two commands -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
..where even the first command is not always needed. :)

---

### Post by bebo2 on 2014-03-25
Thanks a lot both of you!

Now I try to generate the required output.
First ifconfig -a output in total (it is the same as ifconfig without -a):
```

ifconfig -a
eth0      Link encap:Ethernet  Hardware Adresse 00:12:3f:08:a5:4c  
          inet Adresse:192.168.0.51  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::212:3fff:fe08:a54c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:1963 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:1694 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:1604360 (1.6 MB)  TX-Bytes:301643 (301.6 KB)
          Interrupt:11 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX-Pakete:208 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:208 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:18204 (18.2 KB)  TX-Bytes:18204 (18.2 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:90:96:ac:40:23  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)

```

Now lsmod #total:
```

lsmod #total
Module                  Size  Used by
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39826  0 
b43                   342801  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
yenta_socket           27428  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18367  1 yenta_socket
mac80211              436493  1 b43
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17393  0 
radeon                738089  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
video                  19115  0 
cfg80211              178877  2 b43,mac80211
dcdbas                 14098  0 
bcma                   25651  1 b43
ppdev                  12849  0 
mac_hid                13077  0 
parport_pc             32114  1 
psmouse                96744  0 
shpchp                 32265  0 
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41937  0 
hid                    81731  1 usbhid
tg3                   141465  0 
ssb                    50691  1 b43

```

And now Varuns' two codes:
```

sudo apt-get purge bcmwl-kernel-source
[sudo] password for bebo: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Paket bcmwl-kernel-source ist nicht installiert, wird also auch nicht entfernt.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

and second (this did I after the upper advice of praseodym yet):
```

sudo apt-get install linux-firmware-nonfree
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut        
Statusinformationen werden eingelesen... Fertig
linux-firmware-nonfree ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

may be, that for praseodym the other orders he mentioned could be interesting. So here they are as well, without ifconfig and lsmod:
```

lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
    Subsystem: Dell Latitude D400 [1028:865d]
    Kernel driver in use: tg3
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
    Kernel driver in use: b43-pci-bridge

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search fritz.box

```

And now - finaly the scripts' output:
```

wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-03-25 09:34:23--  http://dl.dropbox.com/u/57264241/wireless_script
Auflösen des Hostnamen »dl.dropbox.com (dl.dropbox.com)«... 23.23.251.149
Verbindungsaufbau zu dl.dropbox.com (dl.dropbox.com)|23.23.251.149|:80... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 302 FOUND
Platz: http://dl.dropboxusercontent.com/u/57264241/wireless_script [folge]
--2014-03-25 09:34:23--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Auflösen des Hostnamen »dl.dropboxusercontent.com (dl.dropboxusercontent.com)«... 54.225.161.64, 23.21.154.121, 23.21.160.18, ...
Verbindungsaufbau zu dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.161.64|:80... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 4353 (4,3K) [text/plain]
wireless_script: Keine Berechtigung

Kann nicht nach »»wireless_script«« schreiben (Keine Berechtigung).

```
"Keine Berechtigung" in German means - no rights / not able to write to wireless_script

So I copied the script acc. your informations to the desktop, made it executable and started it then by hand. Seemed that it worked well.
Here is the output file content of wireless-info.txt it generated:
```

######### wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux Latitude-D600 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:55:18 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
    Subsystem: Dell Latitude D400 [1028:865d]
    Kernel driver in use: tg3

02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
    Kernel driver in use: b43-pci-bridge

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro
"
PRODID_2="SmartCardBus Reader
"
PRODID_3="V1.0
"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.250   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search fritz.box

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLANBB:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA
    WLANBB:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA
    Hasan:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.51
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.250

    DNS:             192.168.0.250

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"WLANBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000359035234
                    Extra: Last beacon: 840ms ago
                    IE: Unknown: 0006574C414E4242
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"WLANBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000358e28246
                    Extra: Last beacon: 1192ms ago
                    IE: Unknown: 0006574C414E4242
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Hasan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012fa28de234
                    Extra: Last beacon: 11240ms ago
                    IE: Unknown: 0005486173616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

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

##### lsmod #####

b43                   342801  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     86DC7EAD5064E99821DBACC
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 686 

##### modules #####

lp

##### blacklist #####

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

##### udev rules #####

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    1.526146] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    1.526186] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.526193] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.526200] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.526208] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.526215] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.566816] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    9.780504] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.642368] Registered led device: b43-phy0::tx
[   10.642406] Registered led device: b43-phy0::rx
[   10.642440] Registered led device: b43-phy0::radio
[   21.716065] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   21.771067] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.772457] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

Hope this will help to get a better  view of the cause.

best regards for both of you

Bebo

---

### Post by varunendra on 2014-03-25
Please also post the outputs of -
```
dmesg | grep b43
sudo iwlist scan
nm-tool
```

I couldn't notice anything wrong in the outputs you posted so far, although praseodym may ask you to edit the **/etc/resolv.conf** file. That would should work if everything else is good.

And if it is easy enough for you, please also post the "wireless_script" report (follow the "Wireless Script" link in my signature if you haven't seen it already). It includes almost all the info you posted so far, plus a lot more.

---

### Post by bebo2 on 2014-03-25
Hi,

after havind read the script output, I think that the system should basicaly work, because I see my WLAN "WLANBB" in the output. So it should be able to detect this.
Stays only the problem how to connect with the built in network-manager (window is named "Netzwerkverbindungen"). There are no WLANs under the so called "Funknetzwerk" visible that I could choose.

I agree, that this has to be solved easy, but as far as I'm a quite new linuxian I can't help myself any more - sorry

As well there is still no icon up in the taskbar (in my German version called "Taskleiste)

very best regards

Bebo

---

### Post by bebo2 on 2014-03-25
Hi Varun,

here are the requested posts:
```

dmesg | grep b43
[    1.526146] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    9.780504] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.642368] Registered led device: b43-phy0::tx
[   10.642406] Registered led device: b43-phy0::rx
[   10.642440] Registered led device: b43-phy0::radio
[   21.716065] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
bebo@Latitude-D600:/$ sudo iwlist scan
[sudo] password for bebo: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:0E:D8:B1:87
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"WLANBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ac537234
                    Extra: Last beacon: 852ms ago
                    IE: Unknown: 0006574C414E4242
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1A:4F:8F:81:2F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"WLANBB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ac343245
                    Extra: Last beacon: 1096ms ago
                    IE: Unknown: 0006574C414E4242
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

bebo@Latitude-D600:/$ nm -tool
nm: 'a.out': No such file
bebo@Latitude-D600:/$ 

```

all o.k.?

Bebo

---

### Post by varunendra on 2014-03-25
the "nm-tool" command is not okay. :)

There is no space in "nm-tool", try it again please, and post back the output. Everything so far looks good. Firmware is installed, your wireless is active and able to scan available networks. Only thing that may be keeping you from being able to connect to internet is a proper configuration.

Also, although this may not be the main problem (or a problem at all), but you should change the encryption type in the router to WPA2 with AES (CCMP). Currently you are using WPA(1) which requires TKIP, and TKIP is something that should be avoided.

---

### Post by bebo2 on 2014-03-25
Hi again,

sorry - didn't think at all as it seems! Now new output generated by nm-tool:
```

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:90:96:AC:40:23

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLANBB:          Infra, 00:04:0E:D8:B1:87, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA
    WLANBB:          Infra, 00:1A:4F:8F:81:2F, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA
    Hasan:           Infra, 00:1A:4F:24:15:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP


- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:12:3F:08:A5:4C

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.51
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.250

    DNS:             192.168.0.250

```

I think, now it's better than before

About encryption - may be this is because of some systems I'm using do not understand other versions (e.g. TVs, internet-radios and so on). I will have to check that. Is it essential for solving the actual problem, or have I got some time to do this?

Bebo

---

### Post by varunendra on 2014-03-25
> **bebo2 said:**
> About encryption - may be this is because of some systems I'm using do not understand other versions (e.g. TVs, internet-radios and so on). I will have to check that. Is it essential for solving the actual problem, or have I got some time to do this?

It is not essential, but sometimes it may make a problem worse. But anyway, I think we can ignore it for now.

As you can see in the output of nm-tool yourself, the wireless is disconnected, so we can't see if it gets proper IP configuration or not when it connects (IF it connects).

Network Manager usually prefers wired connection if it is detected. So try disconnecting the wired connection > reboot > retry to connect to wireless (keep the ethernet cable unplugged all this while). Can you connect?

If yes, post the output of "nm-tool" again when it seems to be connected.

---

### Post by bebo2 on 2014-03-25
Dear Varun,

you are soooo perfect!! - It is working!

Here the output of nm-tool:
```

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [WLANBB] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:90:96:AC:40:23

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WLANBB:          Infra, 00:1A:4F:8F:81:2F, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA
    Hasan:           Infra, 00:1A:4F:24:15:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    *WLANBB:         Infra, 00:04:0E:D8:B1:87, Freq 2412 MHz, Rate 54 Mb/s, Strength 78 WPA

  IPv4 Settings:
    Address:         192.168.0.60
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.250

    DNS:             192.168.0.250


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:08:A5:4C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

Thanks so much for your efforts - I'm really proud to have got in contact with you.
All my family will be happy soon with this old new refurished system!

Again Thanks to all efforts here in the thead.

Can I come back with any help to this forum?

very best regards

Bebo

---

### Post by varunendra on 2014-03-25
> **bebo2 said:**
> Can I come back with any help to this forum?

Sure, you're always welcome to ask or offer help as you need or like! :)

We also have some non-support areas here which you may enjoy.

By the way, the output looks good. :) Please mark the thread as **[SOLVED] **now that it is.

---

### Post by mörgæs on 2014-03-25
In a year when your Xubuntu 12.04 is out of support you might be interested in this:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by bebo2 on 2014-03-25
So - after having enjoyed a lot of help - it's tome to close the thread and say goodbye

Bebo

---

