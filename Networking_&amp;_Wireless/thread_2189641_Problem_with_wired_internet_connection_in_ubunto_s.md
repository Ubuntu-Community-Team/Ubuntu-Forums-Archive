---
title: "Problem with wired internet connection in ubunto studio 12.04"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by calimastrusia on 2013-11-23
Hello, I recently installed Ubuntu studio in a Medion Laptop, and I can´t connec to the internet over ethernet. The wireless card are also not recognized. I also tried with the same modem with USB, also without success. 
I looked in this forum for answers, tried a couple of things but nothing worked so far.

---

### Post by praseodym on 2013-11-23
Please show the terminal outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by calimastrusia on 2013-11-23
Thanks for your answer, the commands:

uname -a
```
Linux maxi-MAM2150 3.2.0-52-lowlatency-pae #54-Ubuntu SMP PREEMPT Tue Aug 6 02:02:19 UTC 2013 i686 athlon i386 GNU/Linux
```

lspci -nnk | grep -ia2 net
```
Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
00:15.0 Ethernet controller [0200]: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC [1050:0033]
    Subsystem: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC [1050:0033]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
--
00:19.0 PCI bridge [0604]: ALi Corporation M5249 HTT to PCI Bridge [10b9:5249]
    Kernel modules: shpchp
00:1b.0 Ethernet controller [0200]: ALi Corporation ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 50)
    Subsystem: Mitac Device [1071:8351]
    Kernel driver in use: uli526x
```

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lsmod:
```
Module                  Size  Used by
joydev                 17322  0 
snd_intel8x0           33423  3 
snd_ac97_codec        106117  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
radeon                738016  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65349  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197602  4 radeon,ttm,drm_kms_helper
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38063  0 
bnep                   17830  2 
psmouse                86546  0 
parport_pc             32114  0 
i2c_ali15x3            12878  0 
bluetooth             158093  10 rfcomm,bnep
pcmcia                 43922  0 
ppdev                  12849  0 
serio_raw              13027  0 
soundcore              14635  1 snd
i2c_ali1535            12777  0 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12905  0 
shpchp                 32265  0 
ati_agp                13242  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40904  3 parport_pc,ppdev,lp
pata_ali               13562  2 
uli526x                22402  0 
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by calimastrusia on 2013-11-23
rfkill list produced no output

---

### Post by praseodym on 2013-11-24
Ok, lets see:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```
Do you use the network-manager? Please install this package by double-click and show
```

sudo ethtool eth0
```

[http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.1-1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.1-1_i386.deb)

Your wireless card has no native Linux driver, it could work with Ndiswrapper, but I dont know...Driver here:

[http://media.cdn.ubuntu-de.org/forum/attachments/18/25/2465970-Winbond89C33D_modified_01.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/18/25/2465970-Winbond89C33D_modified_01.tar.gz)

---

### Post by calimastrusia on 2013-11-24
cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

cat /etc/resolv.conf:
```
cat: /etc/resolv.conf: No existe el archivo o el directorio
```

route -n
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
```

I tried to install the ethtool package by doubleclicking on it, it gets the software manager open, but the install option is not aviable. (the button is not clickable, and file-> install doesn´t work either)

How do I install the Ndiswrapper's driver?

Thanks

---

### Post by praseodym on 2013-11-24
Save the DEB file in "Downloads" and install via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo touch /etc/resolv.conf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
sudo ethtool eth0
```

---

### Post by calimastrusia on 2013-11-24
Sooo.. ethtool installed, thanks!!

the rest:

sudo touch /etc/resolv.conf:
no output

echo -e nameserver 8.8.8.8\nnameserver 8.8.4.4 | sudo tee -a /etc/resolv.conf:
```
nameserver 8.8.8.8nnameserver 8.8.4.4
```

sudo /etc/init.d/networking restart:
```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

sudo ethtool eth0:
```
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Link detected: no
```

---

### Post by praseodym on 2013-11-24
**    Link detected: no**

Checked the cable?

---

### Post by calimastrusia on 2013-11-24
Yes, I use the cable to connect with my window's laptop and everything works just fine. 
The computer recongizes the cable, the indicator ligth is on.

---

### Post by praseodym on 2013-11-24
Try
```

sudo ethtool -s eth0 speed 100 autoneg off
sudo /etc/init.d/networking restart
sudo ethtool eth0
```

---

### Post by calimastrusia on 2013-11-24
I also tried to connect to the same modem via usb, it gets also recongnized but I cann´t get connected. I had the same problem with Fedora and CentOs.

---

### Post by praseodym on 2013-11-24
Check the file

```
cat /etc/resolv.conf
```
You copied a typo:
```
 echo -e nameserver 8.8.8.8[COLOR="#FF0000"]\[/COLOR]nnameserver 8.8.4.4 | sudo tee -a /etc/resolv.conf:
```

---

### Post by calimastrusia on 2013-11-24
cat /etc/resolv.conf

```
nameserver 8.8.8.8
ameserver 8.8.4.4
nameserver 8.8.8.8nnameserver 8.8.4.4
nameserver 8.8.8.8
ameserver 8.8.4.4
nameserver 8.8.8.8\ nameserver 8.8.4.4
```

---

### Post by praseodym on 2013-11-24
Clean up the file
```

gksudo gedit /etc/resolv.conf
```
It should read only```

nameserver 8.8.8.8
nameserver 8.8.4.4
```
Save, close the editor and restart the network
```

sudo /etc/init.d/networking restart
```
Which networking GUI is in use?

---

### Post by calimastrusia on 2013-11-24
I cleaned the file, now cat /etc/resolv.conf outputs:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

but sudo /etc/init.d/networking restart:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

The networking GUI in use is the network manager from Ubuntu

---

### Post by praseodym on 2013-11-25
Go to your network manager profile and set "Ignore" in "IPv6-settings"

---

### Post by calimastrusia on 2013-11-25
tried, still can't connect.

---

