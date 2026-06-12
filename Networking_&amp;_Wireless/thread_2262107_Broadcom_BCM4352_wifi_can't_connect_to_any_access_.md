---
title: "Broadcom BCM4352 wifi can't connect to any access point"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by polochamps on 2015-01-23
Hi,

I am having problems on making my wifi connect to any access point.
Currently running Ubuntu 15.04 but also tested it on Ubuntu 14.10 with the same result.

```
Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
```

Looking forward for your kind response.

Thank you

---

### Post by chili555 on 2015-01-23
Please be more specific than, "...having problems." Does it see networks, including yours? When you click on yours, does it try to connect and fail? If it connects, does it drop immediately? In five minutes? Or...?

---

### Post by polochamps on 2015-01-23
> **chili555 said:**
> Please be more specific than, "...having problems." Does it see networks, including yours? When you click on yours, does it try to connect and fail? If it connects, does it drop immediately? In five minutes? Or...?

Hi,

Yes it does see networks (mine included) and when it is attempting to connect it ends up with a window - "authentication required for password".
Usually it takes 20-30 seconds when connecting before the "authentication for password" window appears.
I did test the wifi with a elementaryos freya beta and it just works, makes me think that there is a problem on 14.10 and 15.04 which didn't exist on ubuntu 14.04.

Thank you

---

### Post by chili555 on 2015-01-23
Let's have a look at:```
sudo dpkg -s bcmwl-kernel-source | head -n9
sudo iwlist wlan0 scan
```Please omit all the networks except yours and disguise the MAC address, something like: xx:D7:19:41:54:xx.

---

### Post by polochamps on 2015-01-23
> **chili555 said:**
> Let's have a look at:```
sudo dpkg -s bcmwl-kernel-source | head -n9
sudo iwlist wlan0 scan
```Please omit all the networks except yours and disguise the MAC address, something like: xx:D7:19:41:54:xx.

Hi,

```
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7850
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu2
```

```
wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"PLDTHOMEDSLshiro"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0010504C4454484F4D4544534C736869726F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160

```

---

### Post by chili555 on 2015-01-23
> IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKFirst, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. > Source: bcmwl
Version: [COLOR="#FF0000"]6.30.223.248[/COLOR]+bdcom-0ubuntu2> makes me think that there is a problem on 14.10 and 15.04 which didn't exist on ubuntu 14.04.The version in 14.04 is 6.30.223.141. I would be quite surprised that reverting to an older version of the driver would be useful, but let's see where we stand after the changes in the router.

---

### Post by polochamps on 2015-01-23
Hi,

I just tried again the elementaryos live usb and yes it is 6.30.223.141 and working. 
I don't have access to the router at this moment but can we try reverting the driver? I do hope it won't affect the bluetooth because it only works in 15.04.

Thank you

---

### Post by chili555 on 2015-01-24
We can try, but I have no idea if it will be successful. Actually, I will be quite astounded if it does! ```
sudo apt-get purge bcmwl-kernel-source
wget http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb
```...assuming yours is a 64-bit system...```
sudo dpkg -i bcmwl*.deb
```Reboot.

Post any errors, warnings, etc.

I am still convinced that TKIP is the problem.

---

