---
title: "Wifi extremly slow - xubuntu 18.04"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by ludwig00 on 2018-09-24
I just installed xubuntu 18.04 from the official site through an usb installation key. Everything is fine and working except for the wifi speed. I tried with Windows 10, I'm at 20mbps minimum. With Xubuntu, I'm at 0.5 mbps. 

I tried to switch antenna, to no avail, the results is the same. I also tried with Tn-link usb wifi dongle, results are the same... 

Here's the pastbin script I run : 

[https://paste.ubuntu.com/p/7wGxN98vrC/](https://paste.ubuntu.com/p/7wGxN98vrC/)

Any help would be greatly appreciated. Thanks in advance =D

---

### Post by chili555 on 2018-09-24
> rtl8723be              98304  0
btcoexist             135168  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
iwlwifi               282624  0
r8188eu               421888  0
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  6 rt2800lib,rt2x00pci,rtl_pci,rt2x00lib,rtlwifi,rtl8723be
hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              622592  5 iwlwifi,rt2x00lib,mac80211,r8188eu,rtlwifi
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  2 wmi_bmof,hp_wmi

Wow! You have a lot of probably conflicting wireless drivers loaded here! Please reboot with all the USBs detached so that only the rt2xxx suite is loaded. Confirm with:

```
lsmod
```

We don’t want any rtl or r8188eu or iwl stuff there at all.

Next, we see:

> Cell 01 - Address: <MAC 'Livebox-C00C' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Livebox-C00C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005e14ee09
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

Your wireless driver and old Chili don’t like auto channel select, TKIP or WPA and WPA2 mixed mode at all!

Please check here: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Proofread carefully, save and close the text editor.

Reboot. Any improvement?

---

### Post by ludwig00 on 2018-09-25
> Wow! You have a lot of probably conflicting wireless drivers loaded  here! Please reboot with all the USBs detached so that only the rt2xxx  suite is loaded.

The problem is I have no USB attached to it and it's giving me same results. Maybe it's because I tried a lot of "fix" I found on the web and I did install a lot of drivers by doing so ? Can I still apply the rest of your fix with so many drivers installed on my laptop or do I have to solve that before trying anything further ?

---

### Post by jeremy31 on 2018-09-25
I would just follow the instructions and reboot.  You may not have any USB devices connected but some of the modules loaded were for USB wifi devices

---

### Post by chili555 on 2018-09-25
> **ludwig00 said:**
> The problem is I have no USB attached to it and it's giving me same results. Maybe it's because I tried a lot of "fix" I found on the web and I did install a lot of drivers by doing so ? Can I still apply the rest of your fix with so many drivers installed on my laptop or do I have to solve that before trying anything further ?
Do you mean that when you reboot with none of the USB wireless devices inserted at all, that the drivers load anyway?

May we see:```
cat /etc/modules
ls  /etc/modprobe.d
```Thanks.

---

### Post by ludwig00 on 2018-09-26
Yes, that's what I meant. Here are the results without any usb attached to my laptop : [http://paste.ubuntu.com/p/ZfgvqkWRx4/](http://paste.ubuntu.com/p/ZfgvqkWRx4/) From what I can tell, everything is the same as the first time. 

Here's the output of commands you suggested me in this post : 

cat /etc/modules : 

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ls /etc/modprobe.d : 

> alsa-base.conf                  blacklist-modem.conf
amd64-microcode-blacklist.conf  blacklist-oss.conf
blacklist-ath_pci.conf          blacklist-rare-network.conf
blacklist.conf                  dkms.conf
blacklist-firewire.conf         intel-microcode-blacklist.conf
blacklist-framebuffer.conf      iwlwifi.conf

---

### Post by chili555 on 2018-09-26
Before:> [COLOR="#FF0000"]rtl8723be[/COLOR]              98304  0
btcoexist             135168  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
[COLOR="#FF0000"]iwlwifi [/COLOR]              282624  0
[COLOR="#FF0000"]r8188eu     [/COLOR]          421888  0
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  6 rt2800lib,rt2x00pci,rtl_pci,rt2x00lib,rtlwifi,rtl8723be
hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              622592  5 iwlwifi,rt2x00lib,mac80211,r8188eu,rtlwifi
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  2 wmi_bmof,hp_wmi
And now after:> rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              622592  2 rt2x00lib,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  2 wmi_bmof,hp_wmiSo, no, all the wrong modules don't load automagically.

Will you please now undertake the router changes I recommend above?

---

