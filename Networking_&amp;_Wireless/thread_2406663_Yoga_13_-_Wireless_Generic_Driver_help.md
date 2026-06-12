---
title: "Yoga 13 - Wireless Generic Driver help"
date: 2018-11-23
forum: Networking &amp; Wireless
---

### Post by Shukero on 2018-11-23
Hello everyone,

I recently installed Ubuntu 18.04; and unfortunately it installed a generic wireless driver for my laptop; that is not very stable, and has a max speed of 1mbps. After puling some information from lshw, I found the below:

```
shukero@Shukero-Laptop:~$ sudo lshw -class network
  *-network                 
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.4
       logical name: wlx2cd05ae66d57
       serial: 2c:d0:5a:e6:6d:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-39-generic firmware=N/A ip=192.168.0.221 link=yes multicast=yes wireless=IEEE 802.11

```

From what I've read on the forum, the "rtl8xxxu" driver is a generic driver. Can someone please confirm this and possibly point me in the right direction for the correct wireless driver?

Thanks,
~mike

---

### Post by chili555 on 2018-11-24
> From what I've read on the forum, the "rtl8xxxu" driver is a generic driver. Can someone please confirm this Absolutely not true. It is a driver for very specific devices and none other.

This driver is often problematic as the specific usb.ids are also used in another driver, rtl8192cu. Both drivers load and conflict. If that is your case, it is likely that blacklisting rtl8192cu will fix your problem.

Let's see if both are loaded. Please run and post:```
lsmod | grep rtl
```

---

### Post by Shukero on 2018-11-24
> **chili555 said:**
> Absolutely not true. It is a driver for very specific devices and none other.

This driver is often problematic as the specific usb.ids are also used in another driver, rtl8192cu. Both drivers load and conflict. If that is your case, it is likely that blacklisting rtl8192cu will fix your problem.

Let's see if both are loaded. Please run and post:```
lsmod | grep rtl
```

Appreciate the help:

```
shukero@Shukero-Laptop:~$ lsmod | grep rtl
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
btrtl                  16384  1 btusb
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm

```

Thanks,
~mike

---

### Post by chili555 on 2018-11-24
So far, so good. Only one driver is loaded. > 
not very stable, and has a max speed of 1mbps. 
Let's have a look at the settings in the router. Please run and post:```
sudo iwlist scan
```You only need show the router you are connected to. Please redact the MAC address like this:> 
Cell 02 - Address: [COLOR="#FF0000"]xxxx[/COLOR]
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014845cbb17
                    Extra: Last beacon: 4152ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK



---

### Post by Shukero on 2018-11-24
Thank for the continued help:

```
lo        Interface doesn't support scanning.

wlx2cd05ae66d57  Scan completed :
          Cell 01 - Address: xxxxx
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000813882f24a
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 0009000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400030180
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050800900000
                    IE: Unknown: 2D1AAD0117FFFFFF0000000000000000000000000000001804011100
                    IE: Unknown: 3D160A080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500000000000040
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C005000A000000C3020002
                    IE: Unknown: DD090010180208009C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: xxxxx
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"frankhome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008138852535
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00096672616E6B686F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050800900000
                    IE: Unknown: 2D1AAD0117FFFFFF0000000000000000000000000000001804011100
                    IE: Unknown: 3D160A080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500000000000040
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C005000A000000C3020002
                    IE: Unknown: DD090010180208009C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 03 - Address: xxxxx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Linksys10479"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000126bb22a006
                    Extra: Last beacon: 5220ms ago
                    IE: Unknown: 000C4C696E6B7379733130343739
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6F0017FFFFFF0001000000000000000000000000001FFF071800
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F080100000000000000
                    IE: Unknown: BF0C30798333EAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: DD1E00904C336E0017FFFFFF0001000000000000000000000000001FFF071800
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120

```

Thanks again,
~Mike

---

### Post by chili555 on 2018-11-24
> Cell 01 - Address: xxxxx
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:[COLOR="#FF0000"]"\x00\x00\x00\x00\x00\x00\x00\x00\x00"[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000813882f24a
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 0009000000000000000000
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                   <snip>Is this a hidden SSID? I suggest that you revert to an unhidden SSID name. It serves no useful purpose. The hardcore hackers and crackers will have no trouble seeing it. Their biggest difficulty will be a WPA2 password that is not in the usual dictionary lists. For example, fluffy123 is likely in the widely used lists; i10v3w4rmb33r is probably not.

Also, did you pick channel 10 because you know it's an overlapped channel and you welcome interference and congestion; or did the router autoselect it? Please check here:  [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor. After making these changes, reboot and tell us if there is any improvement.

---

### Post by Shukero on 2018-11-24
I figured it out... it was the family router... it's on it's way out. After getting a new one; the speeds are now good :).

Thanks,
~mike

---

