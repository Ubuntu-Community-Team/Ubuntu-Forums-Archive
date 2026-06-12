---
title: "wifi problem ubuntu 18.04"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by junior2412 on 2018-10-14
hello people 
my problem is the next install ubuntu-18.04.1-desktop-amd64 and I can not connect to the internet I use the wireless adapter tp link tlwn8200nd it detects all the networks but it does not let me connect to any it also makes me the same from the live cd I think it's a problem with the controller but I do not know how to solve it, I hope you can help me already thank you very much
sorry for my English

---

### Post by Autodave on 2018-10-15
Is this a laptop or a desktop machine?

---

### Post by junior2412 on 2018-10-15
desktop machine

---

### Post by junior2412 on 2018-10-20
please someone to help me I saw why you have to compile the driver that is for windows but do not do it

---

### Post by junior2412 on 2018-10-25
help i am new in ubuntu

---

### Post by chili555 on 2018-10-25
Please insert the device and open a terminal and run:```
lsusb
```And also:```
dmesg | grep rtl
```Reply with the result and we'll get you set up!

---

### Post by junior2412 on 2018-10-25
```

lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 2357:0100  
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0458:6001 KYE Systems Corp. (Mouse Systems) GF3000F Ethernet Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

dmseg grep rtl

Orden «dmseg» no encontrada. Quizá quiso decir:

  la orden «dmesg» del paquete deb «util-linux»
  la orden «mmseg» del paquete deb «sunpinyin-utils»

Pruebe con: sudo apt install <nombre del paquete deb>

sudo apt install  «util-linux»
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete «util-linux»

```

```

iwconfig
wlx7c8bca15fefd  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

enp4s0    no wireless extensions.

```

```

ifconfig

No se ha encontrado la orden «ifconfig», pero se puede instalar con:

sudo apt install net-tools

sudo apt install net-tools
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete net-tools no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente

E: El paquete «net-tools» no tiene un candidato para la instalación


```

---

### Post by chili555 on 2018-10-26
> dmseg grep rtlIt is instead:```
dmesg | grep rtl
```You didn't spell 'dmesg' correctly and you omitted the pipe symbol |.

Please try again.> 2357:0100  I suspect that you have two conflicting drivers loaded; let's blacklist one:```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if the wireless is working better.

---

### Post by junior2412 on 2018-10-26
```

dmesg | grep rtl

[   15.335108] rtl8192cu: Chip version 0x11
[   15.386114] rtl8192cu: Board Type 0
[   15.386239] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   15.386288] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   15.478455] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.478801] usbcore: registered new interface driver rtl8192cu
[   15.553197] usbcore: registered new interface driver rtl8xxxu
[   15.557697] rtl8192cu 7-2:1.0 wlx7c8bca15fefd: renamed from wlan0
[   26.679608] rtl8192cu: MAC auto ON okay!
[   26.703821] rtl8192cu: Tx queue select: 0x05


```

```

sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```
after this command


```

dmesg | grep rtl
[   15.359835] usb 7-2: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   15.359868] usb 7-2: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.669089] usbcore: registered new interface driver rtl8xxxu
[   16.672025] rtl8xxxu 7-2:1.0 wlx7c8bca15fefd: renamed from wlan0

```
but I still can not connect

---

### Post by junior2412 on 2018-10-26
```

blacklist.conf
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192cu

```

---

### Post by braznyc on 2018-10-26
Same thing happening to me after upgrading from Ubuntu 16.04 to 18.04.

I've tried everything posted here in the forums. Nothing worked!

I've invented my own "temporary solutions":


Solution 1- If you have a wifi switch in the front of the laptop, turn if off... Reboot the computer, log in, wait until everything loads and turn the switch back on manually. The wifi works again. I have the switch in the front of the computer. 



Solution 2- use a USB wifi adapter. I don't know why but after inserting one of them in the usb slot the laptop recognized the default built in adapter and the computer connected to the internet again. This is how I did it: I turn off the laptop, insert the USB wifi adapter, turn on the computer again and it just works. And I now have 2 wifi connections available. The USB is slower so I choose the default one. 



Still looking for the definitive solution for this issue.

I hope this helps someone.

---

### Post by chili555 on 2018-10-26
> **junior2412 said:**
> ```

dmesg | grep rtl

[   15.335108] rtl8192cu: Chip version 0x11
[   15.386114] rtl8192cu: Board Type 0
[   15.386239] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   15.386288] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   15.478455] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.478801] usbcore: registered new interface driver rtl8192cu
[   15.553197] usbcore: registered new interface driver rtl8xxxu
[   15.557697] rtl8192cu 7-2:1.0 wlx7c8bca15fefd: renamed from wlan0
[   26.679608] rtl8192cu: MAC auto ON okay!
[   26.703821] rtl8192cu: Tx queue select: 0x05


```

```

sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```
after this command


```

dmesg | grep rtl
[   15.359835] usb 7-2: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   15.359868] usb 7-2: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.669089] usbcore: registered new interface driver rtl8xxxu
[   16.672025] rtl8xxxu 7-2:1.0 wlx7c8bca15fefd: renamed from wlan0

```
but I still can not connectDoes it try but fail to connect? May we see: ```
sudo iwlist scan
```Just show us your network, not all the neighbors. Also, please redact your MAC address with xxxx like this:> Cell 01 - Address: [COLOR="#FF0000"]xxxxx[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025b76eeddf8
                    Extra: Last beacon: 428ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


---

### Post by junior2412 on 2018-10-27
```

sudo iwlist scan
Cell 02 - Address: xxxxxx
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"me"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ac5b51a4
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 000F576946692D41726E65742D64373478
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706415220010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 0504000100D0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601E4BEEDDB4F10103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```
I  use this wifi adapter in Windows and I'm fine. The problem is only in  Ubuntu. I found a guide that uses this NDISwrapper program to compile  the windows driver but I do not know what to download

---

### Post by junior2412 on 2018-10-27
Could it be that the dhcp is disabled?

---

