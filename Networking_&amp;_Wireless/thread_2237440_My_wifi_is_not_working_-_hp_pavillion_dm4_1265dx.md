---
title: "My wifi is not working - hp pavillion dm4 1265dx"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by Anderson_Terrazas on 2014-08-01
I have changed from windows 8 becuse the wifi was not working,but it isnt working on my ubuntu 14.04. Fingerprint is not working too.
chipset intel centrino advanced N +wimax 6250
Any help?

---

### Post by varunendra on 2014-08-04
Welcome to the forums Anderson!

Was Windows 8 preinstalled or you installed it later? It seems this model originally comes with Windows 7 : [http://www.pcmag.com/article2/0,2817,2383816,00.asp?tab=Specs](http://www.pcmag.com/article2/0,2817,2383816,00.asp?tab=Specs)

So, was the wifi working on windows 7 ?

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Anderson_Terrazas on 2014-08-04
```

======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

adriana-HP-Pavilion-dm4-Notebook-PC 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
Memory : 3753 MB
Uptime : 23:40:15 up 4 min,  2 users,  load average: 0,33, 0,54, 0,27


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:146a]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 10f1:1a28 Importek 
Bus 002 Device 003: ID 8086:0187 Intel Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: i2400m-usb:2-1.3:1.0: WiMAX      yes           no
1: hp-wifi: Wireless LAN            no            yes
2: hp-wwan: Wireless WAN            no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===========================o=======o============o=============o=========o===========o==============o===========
 Interface & ID            | Type  | Driver     | State       | Default | Speed     | Support      | HW Addr   
===========================o=======o============o=============o=========o===========o==============o===========
 wmx0                      | Wired | i2400m_usb | unavailable | no      |           |              | <MAC ID removed>
---------------------------+-------+------------+-------------+---------+-----------+--------------+-----------
 eth0  [Conexão cabeada 1]| Wired | r8169      | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.86.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.86.1
    DNS:             192.168.86.1
---------------------------+-------+------------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
0.0.0.0         192.168.86.1    0.0.0.0         UG    0      0        0 eth0
192.168.86.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.86.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.447/0.470/0.494/0.031 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.032/0.033/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "pt_BR.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=28b825ce-3f0c-4725-a78e-a430d380c54b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.073917] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.074256] audit: initializing netlink socket (disabled)
[    1.527117] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.931658] wmi: Mapper loaded
[   16.935856] i2400m_usb 2-1.3:1.0: firmware interface version 9.3.2
[   17.128273] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

```

---

### Post by Anderson_Terrazas on 2014-08-04
It originally came with windows 7 installed, everything worked just fine. I decided to give windows 8 a try and at first it did work, but sporadically it would fail until it got to the point when it stopped working at all.
Thank you for every help you can give me.

---

### Post by varunendra on 2014-08-05
I can't see any wireless device in the report, neither PCI, nor USB or PCMCIA.

Check your laptop's BIOS to make sure it is enabled from there, although even if it were disabled, it should have shown up in the lspci or lsusb.

To me it suggests that either your card is loose (not detected by the laptop) or has died. Either that or the BIOS has been stuck in some weird state. As such, if it is NOT an UEFI based installation (unlikely, since it is quite old system) try resetting the BIOS to factory defaults (there will be an option in the BIOS to do so).

If resetting doesn't help, and if you can access the card (usually it is located under a removable panel at the bottom), make sure it is not loose. Preferably, remove it > clean its contacts > re-seat making sure it is seated properly in the slot > boot and check -
```
lsusb
lspci | grep -i net
```
Does it appear in either outputs?

---

### Post by Anderson_Terrazas on 2014-08-05
```

adriana@adriana-HP-Pavilion-dm4-Notebook-PC:~$ lsusb
Bus 002 Device 004: ID 10f1:1a28 Importek 
Bus 002 Device 003: ID 8086:0187 Intel Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 001 Device 006: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
adriana@adriana-HP-Pavilion-dm4-Notebook-PC:~$ lspci | grep -i net
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
adriana@adriana-HP-Pavilion-dm4-Notebook-PC:~$ 


```

---

### Post by Anderson_Terrazas on 2014-08-05
bios info says that wlan is N/A
Ive reset the Bios
wlan still not working
Im tring the hardware cleaning
Thanks

---

### Post by jeremy31 on 2014-08-05
Try this in terminal ```
dmesg | grep -i bios
```

I have a Toshiba Satellite with the same card in it that works great.  The issue is, that even in Windows you cannot use the WiMax and wifi at the same time.  I have also noticed that I cannot get a different wifi card to work in that laptop other than the 6250 where my other laptops other than my Lenovo G710 work well with other wifi cards

---

### Post by Anderson_Terrazas on 2014-08-05
The hardware cleaning worked. Im tring it for 24h than i will consider it solved.
Thanks a lot

---

### Post by varunendra on 2014-08-08
You're welcome!

If it proves to be permanently fixed, please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

---

