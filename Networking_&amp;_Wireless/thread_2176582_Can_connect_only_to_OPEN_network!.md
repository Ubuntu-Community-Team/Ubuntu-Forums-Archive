---
title: "Can connect only to OPEN network!"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by jimcoun on 2013-09-25
Hi all,

yesterday I installed Ubuntu 13.04 on my mother's netbook[FONT=arial, sans-serif], Samsung NP-NC210 ([/FONT]http://www.samsung.com/in/support/model/NP-NC210-A01BD).

The problem is that it connects to my WLAN router only when I have disabled security. When I enable my WPA+WPA2 password, I cannot get the netbook connected.
I have tried changing the channel but the problem continues.

Any help would be very appreciated!

Thank you very much,
Dimitris

---

### Post by varunendra on 2013-09-25
Hello Dimitris, Welcome to the forums !

Please open a terminal (Ctrl-Alt-T) and post back the output of following commands -
```
lspci -nnk | grep -iA2 net
iwconfig
nm-tool
```

---

### Post by jimcoun on 2013-09-25
Hi, thanks for replying.
This is what I get:
```

pc@pc-NC210-NC110:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7179]
    Kernel driver in use: wl
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a8]
    Kernel driver in use: r8169
pc@pc-NC210-NC110:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
pc@pc-NC210-NC110:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:11:32:7A:98:92

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        E0:CA:94:57:33:F0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FRITZ!Box:       Infra, 00:1C:4A:A3:10:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    CYTA 483A:       Infra, DC:0B:1A:24:48:3A, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    OTE8249:         Infra, 00:15:56:D0:13:3C, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    falconight:      Infra, 58:98:35:4D:AA:FC, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    HOL ALU WLAN:    Infra, 66:AB:25:7C:D0:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    falakros-praktor:Infra, 94:44:52:B4:9A:19, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    open:            Infra, 00:05:59:0A:3D:B9, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    dkof:            Infra, BC:F6:85:3F:50:4A, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SABBAS:          Infra, B0:75:D5:8F:C0:F3, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA
    chadji wifi:     Infra, 00:17:C2:EE:B7:C1, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WEP

```

---

### Post by varunendra on 2013-09-25
First of all, please edit your above post to wrap the outputs within 'Code' tags (follow the "Using Code Tags" link in my signature to see how). It will preserve its formatting and will make it more readable (besides getting rid of those cute smileys ;))

Now the card you have does not have too many options to try. One thing you may try is to turn the power management off on the wireless interface, although I don't think it may help in authentication issues -
```
sudo iwconfig eth1 power off
```
Then check with "iwconfig" to see if it really turned off.

About the WPA+WPA2 security (I should have said this in my first post) - This combination has very bad reputation in Linux, it simply does not work very well with linux drivers. It is highly recommended to use pure WPA2-PSK encryption with AES algorithm (not TKIP). If it is not a problem for you, please try that and let us know the result.

---

### Post by kostkon on 2013-09-25
> **varunendra said:**
> About the WPA+WPA2 security (I should have said this in my first post) - This combination has very bad reputation in Linux, it simply does not work very well with linux drivers. It is highly recommended to use pure WPA2-PSK encryption with AES algorithm (not TKIP). If it is not a problem for you, please try that and let us know the result.
+1
Just change the security from WPA+WPA2 to just WPA2 (with AES obviously) and you should be fine.

---

### Post by jimcoun on 2013-09-25
I changed my router's authentication to WPA2(CCMP??). It was the only option it gave me. However, it then informed me that this is the AES algorithm. Anyway, the netbook still cannot connect to the network..

I also tried switching power management off, still no luck.

---

### Post by jimcoun on 2013-09-25
FIXED! Worked only with WPA and TKIP algorithm. Thank you very much ;)

---

### Post by varunendra on 2013-09-25
> **jimcoun said:**
> FIXED! Worked only with WPA and TKIP algorithm. Thank you very much ;)

Ugh, TKIP (infamous for inefficiency resulting in slow speeds) ! But thanks for the feedback :D

---

### Post by jimcoun on 2013-09-26
Maybe the driver is not correct. Is there a website where I can download drivers for Linux, for specific hardware? 

Thanks once again ;)

---

### Post by varunendra on 2013-09-26
> **jimcoun said:**
> Maybe the driver is not correct. Is there a website where I can download drivers for Linux, for specific hardware? 

Thanks once again ;)
You're welcome !

Downloading drivers from third party resources is probably the worst choice and often takes a lot of manual configuration to make it work. The latest version of the driver you are using is already available in the repositories, albeit not the default ones for 13.04 as yet.

To see which version is currently in use, you can use command -
```
dpkg -s bcmwl-kernel-source | grep Version
```
If it shows **6.20**.... then you may be able to get some better performance with the newer version which is **6.30**.. To install this version, update your system first -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then download the latest (6.30...) .deb package suitable to your kernel (32 or 64 bit) from here : [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

Now before installing this package, it would be a good idea to purge the current one -
```
sudo apt-get purge bcmwl-kernel-source
```
Then double-click the downloaded one to install it with your package manager.

Another driver that often works better with this card for some people is the native brcmsmac driver. To try it, just purge the current one with the "apt-get purge" command told above, and **don't** install the latest one you just downloaded. Just reboot and it (the native brcmsmac driver) should automatically load on next boot. Check that with -
```
lsmod | grep -e brcm -e wl
```
You should only see brcmsmac and some related lines, NOT wl in the output. If so, then the native one is in use. See if it gives you any better performance as it does for many others. If not, then just double-click the above downloaded one to install it. Reboot and you'll have the proprietary one (wl) loaded once again, only the latest version this time.

Let us all know about the performance difference (if any) with both these variations. Thanks !

**PS:**
Like I mentioned previously, WEP+TKIP is not good for performance/speed. So try the WPA2 (AES) with both drivers (brcmsmac and the latest wl one) to see if any of them can get better performance with it.

---

