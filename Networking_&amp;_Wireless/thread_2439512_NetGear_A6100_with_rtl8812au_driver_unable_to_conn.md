---
title: "NetGear A6100 with rtl8812au driver unable to connect to wireless network on 18.04"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by usernumber92 on 2020-03-28
I have been using the NetGear A6100 USB Wifi Adapter with 16.04 for the past couple of years.  Recently decided to upgrade to 18.04.  Upon installation, I updated the rtl8812au driver for the adapter.  I am able to see all networks but when I attempt to connect, I am asked to authenticate multiple times before the request fails.  I reinstalled the driver multiple times and attempted installing the most recent driver (5.6.4.2) which turned out to not be compatible with the adapter.  I also attempted to connect after turning off the security measures on the modem.  This was also unsuccessful.  I am able to connect to the internet by tethering my computer to my phone.

The wireless-info script results are contained in this link:
[https://pastebin.com/6xyzbBXQ](https://pastebin.com/6xyzbBXQ)

I'm not sure of any other measures I could take.  Any help would be much appreciated.

---

### Post by chili555 on 2020-03-28
> 
Cell 01 - Address: <MAC 'Mandzy Home' [AC1]>
                    ESSID:"Mandzy Home"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=94/100  
                    Extra:fm=0003
Yikes!!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Many Linux drivers and old Chili hate hate hate TKIP.

I would also rename the SSID or router name to one without a space in the name, MandzyHome, for example.

Any improvement?

---

### Post by usernumber92 on 2020-03-28
I changed the security from WPA/WPA2 to WPA2 only.  The modem didnt give me an option to change channel width.  I fixed the channel to 11 and made sure it was using b/g/n speeds.  Changed the SSID to a single word and rebooted.  Still no luck.  Ubuntu asks for my password twice and quits trying.  I've also tried disabling NetworkManager and using wpa_supplicant to connect on the terminal with no success.

---

### Post by chili555 on 2020-03-29
Let's see what the log says. Please try to connect and then run and post:

```
dmesg | grep -e wlx -e etwork
```

---

### Post by usernumber92 on 2020-03-29
Turns out tethering is prohibited on my cellular plan.  Theres 5 different lines outputted by:

```
dmesg | grep -e wlx -e etwork
```

First 3 lines:

```
rtl8812au 1-4:1.0 wlx(MACaddr): renamed from wlan0
audit:  type=1400 audit(1585426203.770:7):  apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1086 comm="apparmor_parser"
audit:  type=1400 audit(1585426203.770:8):  apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1086 comm="apparmor_parser"
```[LEFT][COLOR=#222222][FONT=Verdana]

The remaining hundred or so lines consist of the following two lines repeating:

```
IPv6:  ADDRCONF(NETDEV_UP): wlx(MACaddr): link is not ready
RTL871X:  rtw_set_802_11_connect(wlx(MACaddr))  fw_state=0x00000008
```[/FONT][/COLOR][/LEFT]

---

### Post by usernumber92 on 2020-03-29
Found the solution here:
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/312[/FONT]

---

