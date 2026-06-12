---
title: "WiFi authentication problems with RTL8192CU USB dongle"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by Toitovna on 2016-01-30
Hello,

I held off as long as possible making a post of my own, since I know that the answer to my question must be out there somewhere. I also know that this board is full of "halp wifi not working" posts. However, after crawling through dozens of forum threads and bits of advice, I've gotten no further than where I started.

My basic info:
```
Kernel        : Linux 3.13.0-76-generic (x86_64)
Compiled        : #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 
Distribution        : Ubuntu 14.04.3 LTS  (LX Desktop Environment)
```

I recently moved to a new house in which I am unable to access the router by even my longest ethernet cord, so I went out and bought a TP-Link (TL-WN821N) USB WiFi adapter. It runs the RTL8192CU driver, with which I had initial problems but quickly fixed.

To start with, I run
```
sudo ifconfig wlan0 up
iwlist wlan0 scan
```
and it returns```

    wlan0     Scan completed :
          Cell 01 - Address: 00:60:64:5F:74:33
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Home Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e74e4b841
                    Extra: Last beacon: 1740ms ago
                    IE: Unknown: 00104E6574436F6D6D20576972656C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

So I know that my driver is, at least, working, and the device is actually able to detect the network. For a short time, using the default network-manager, I would be able to connect to the network very briefly, but would get dropped within ten minutes. My symptoms were almost identical to bug #[548992]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992") and it was often suggested in that thread that network-manager was responsible. After fiddling with /etc/network/interfaces, turning off power management and checking for multiple instances, I (somewhat desperately) uninstalled network-manager, which has now completely cut me off from the internet. Since then I have been trying, without any success, to use wpa_supplicant to connect to the network.

My wpa.conf file looks like this:```

    network={
        ssid="Home Network"
        scan_ssid=1
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk="plaintext-passphrase"
        psk=hex-passphrase
    }
```

But when I run```

    sudo wpa_supplicant -Dwext -iwlan0 -c/etc/network/wpa.conf
```
It returns the following:```

Successfully initialized wpa_supplicant
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Trying to associate with 00:60:64:5f:74:33 (SSID='Home Network' freq=2412 MHz)
ioctl[SIOCSIWFREQ]: Device or resource busy
wlan0: Association request to the driver failed
wlan0: Authentication with 00:60:64:5f:74:33 timed out.
wlan0: CTRL-EVENT-DISCONNECTED bssid=00:60:64:5f:74:33 reason=3 locally_generated=1
wlan0: Trying to associate with 00:60:64:5f:74:33 (SSID='Home Network' freq=2412 MHz)
ioctl[SIOCSIWFREQ]: Device or resource busy
wlan0: Association request to the driver failed
wlan0: Authentication with 00:60:64:5f:74:33 timed out.
wlan0: CTRL-EVENT-DISCONNECTED bssid=00:60:64:5f:74:33 reason=3 locally_generated=1
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Home Network" auth_failures=1 duration=10
ioctl[SIOCSIWSCAN]: Device or resource busy
ioctl[SIOCSIWSCAN]: Device or resource busy
ioctl[SIOCSIWSCAN]: Device or resource busy
wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="Home Network"
wlan0: Trying to associate with 00:60:64:5f:74:33 (SSID='Home Network' freq=2412 MHz)
ioctl[SIOCSIWFREQ]: Device or resource busy
wlan0: Association request to the driver failed
wlan0: Authentication with 00:60:64:5f:74:33 timed out.
wlan0: CTRL-EVENT-DISCONNECTED bssid=00:60:64:5f:74:33 reason=3 locally_generated=1
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Home Network" auth_failures=2 duration=20
ioctl[SIOCSIWSCAN]: Device or resource busy
ioctl[SIOCSIWSCAN]: Device or resource busy
```

This deauthentication for reason=3 is the same thing that I was finding in dmesg back when network-manager kept dropping me every ten minutes (see the bug thread). From what I can tell this message means that the AP has gone offline, but I'm accessing the wifi from two other devices  so it's definitely not a router problem.

I ran the wireless-info script, the results of which I've put up [here]("http://pastebin.com/aB3UBMFG"). I'm just not able to interpret it beyond the config files that it copies out and the dmesg output. (When the script runs iwlist scan for some reason wlan0 fails, but I can assure you that when I run it in terminal it finds the network, as described above.)

I'm just tied up in knots now, I don't know whether to try re-installing network-manager or having a go with wcid (both of which would involve manually installing from a .deb); or whether I can't make this wpa_supplicant method work. It seems like any of them ought to be able to do what I want, but none of them are! I can see the network, right there on iwlist scan!

Could it be that multiple network managers are conflicting with one another? (I've checked my processes and there's nothing there.) Did I do something wrong writing my wpa.conf? Do I need to revert to an older kernel or something? Is my /etc/network/interfaces file interfering? (Whenever I boot, now, it makes me wait at the splashpage while it tries and fails to connect to the network.)

Sorry for such a verbose post, I will appreciate any and all help that you can provide!

---

### Post by jeremy31 on 2016-01-30
Can you change the wifi router encryption to WPA2 only with no TKIP, no WEP and Network Manager should work

The wpa.conf may be wrong as it should just have TKIP under ```
group=
```

There is some strange things in the wireless-info file, why do you have rtl8192cu module being loaded from /etc/modules?  And why does rc.local have [COLOR=#333333][FONT=Consolas]echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id?  Is this another wifi card you have?

I would follow installation instructions from [/FONT][/COLOR]https://github.com/pvaret/rtl8192cu-fixes as that module seems to function better than the kernel modules from 3.13

---

### Post by Toitovna on 2016-01-30
Thanks for replying, Jeremy,

I wasn't able to follow the pvaret  fix when I first plugged the USB in because I had no internet access  whatsoever. Therefore, when I read [this thread]("http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver"), I  followed the second answer, which didn't require any internet -- and it  worked, inasmuch as the driver functioned and allowed me to access  wlan0. That explains those weird lines that you pointed out.

Well,  to see whether pvaret's fix would work, I commented-out the relevant  line in rc.local, then downloaded a .zip of the fix and followed their  instructions, finishing with a reboot. The driver doesn't work at all  now -- I look for it by running:
```
ifconfig -a
```
and wlan0 doesn't even show up. It's still sitting there on lsusb, but now device and driver are completely incommunicado. I assume because pvaret's fix has blacklisted the last driver I was using.

So now I'm in an even worse position ...

---

### Post by jeremy31 on 2016-01-31
Can you upload new results for the wirless script, should just need to ```
./wireless-info
``` to run it

---

