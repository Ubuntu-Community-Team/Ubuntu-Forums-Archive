---
title: "can't install atheros ar8162 driver after upadating the kernel. kmalloc_array error"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by grecoalinoe on 2014-01-09
Hello all,
I'm running on xubuntu 12.04.03 LTS with a Lenovo g580 laptop
my NIC is an atheros ar8162
the kernel version is 3.2.0-57-generic 

I used to install the * compat-wireless-2012-09-01-pc.tar.bz2.* drivers after each update of the kernel 
in order to  make my NIC run
and it'd work just fine
but since the last three kernel updates
I can't manage to install it
the wirless still works fine
but the wired connection drivers won't install 
with the MAKE command I get this error
```
./scripts/gen-compat-autoconf.sh /home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/.config /home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-57-generic/build M=/home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-57-generic »
  CC [M]  /home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/compat/main.o
In file included from /home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/include/linux/compat-3.4.h:32:21: erreur: redefinition of &#8216;kmalloc_array&#8217;
include/linux/slab.h:243:21: note: previous definition of &#8216;kmalloc_array&#8217; was here
make[3]: *** [/home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/compat/main.o] Erreur 1
make[2]: *** [/home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc/compat] Erreur 2
make[1]: *** [_module_/home/alinoe/Documents/informatique/lenovo/ethernet/compat-wireless-2012-09-01-pc] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-57-generic »


```

as for the other command-lines

lshw -C network
```
  *-network NON-RÉCLAMÉ   
       description: Ethernet controller
       produit: AR8162 Fast Ethernet
       fabriquant: Qualcomm Atheros
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       version: 08
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       ressources: mémoire:d3500000-d353ffff portE/S:2000(taille=128)
  *-network DÉSACTIVÉ
       description: Interface réseau sans fil
       produit: BCM4313 802.11bgn Wireless Network Adapter
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:04:00.0
       nom logique: eth2
       version: 01
       numéro de série: 08:ed:b9:97:ca:2b
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       ressources: irq:17 mémoire:d3400000-d3403fff

```

ifconfig
```
lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:12 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:792 (792.0 B) Octets transmis:792 (792.0 B)

```cat  /etc/network/interfaces
```
auto lo
iface lo inet loopback

```sudo nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth2  [Liveboloss] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        08:ED:B9:97:CA:2B

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Livebox-6DBC:    Infra, C0:AC:54:81:6D:BC, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    orange:          Infra, 46:AC:0A:20:3F:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    orange:          Infra, C2:AC:54:81:6D:BC, Freq 2437 MHz, Rate 54 Mb/s, Strength 54
    *Liveboloss:     Infra, 4C:AC:0A:20:3F:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```

so I could use some help

---

### Post by chili555 on 2014-01-09
Please try my procedure here: [http://askubuntu.com/questions/378809/how-to-install-networkdriver](http://askubuntu.com/questions/378809/how-to-install-networkdriver)

---

### Post by grecoalinoe on 2014-01-09
fantastic, it works, thanks a lot !


well it first worked and when I rebooted it was gone
so I had to do again from make defconfig-alx 
then reboot and it was alright

would you please explain me what I did though through these commands ?
and will I have to do it all again after every kernel upadate ?

what about this redefinition of kmalloc_array, any idea what was that ?

---

### Post by chili555 on 2014-01-09
> will I have to do it all again after every kernel upadate ?Yes; and I'm pretty confident that's why it didn't stick the first time; Update Manager had a newer kernel on tap.> redefinition of kmalloc_array, any idea what was that ? Things get changed slowly but surely as the Linux kernel matures. Things that worked well in mid-2012 don't work at all in early 2014. My old IDE harddrive won't work in my Lenovo laptop. Technology moves on.> would you please explain me what I did though through these commands ?You simply plucked the alx driver out of all the possible ethernet and wireless drivers available from that package and compiled it to work with your current kernel version. 

The driver alx is built in to more recent Ubuntu versions. If your system is running well aside from that, I'd stick with 12.04.3 and recompile as needed.

---

### Post by grecoalinoe on 2014-01-09
well, couldn't find better help,
thanks again for your time and explanations

---

