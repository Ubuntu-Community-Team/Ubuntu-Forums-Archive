---
title: "Upgraded to 24.04 and now wifi is gone.  How to fix?"
date: 2024-08-10
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2024-08-10
I just upgraded my folks' notebook to 24.04LTS and it was relatively smooth, except that now there's no wifi connection.  It's grayed out in the options when I right click on the "network connection" icon, doing a "Request Scan" does nothing, and only (thank god the laptop still has one!) when I plug in an Ethernet cable can I connect to the internet.

I've tried several fixes following threads online.  

I ran lshw and determined it has a Qualcomm Atheros QCA9565 / AR9565 wifi card without a physical ID (which I suspect is the issue...probably needs the right driver?).  

Apparently it had two versions of network-modules-extra installed, so (perhaps stupidly) I uninstalled the one that seemed older.  (Should I reboot?)

I don't want to continue messing around with things when I don't know what I'm doing.  The system is a Dell Inspiron 3542.  Kernel 6.6.9-060909, neofetch returns a Lubuntu version of 24.04 LTS x86_64

I'd love a simple walkthrough of what diagnostics I need to run to figure out more, and where I might begin to get a driver that works.  

(It still has the dual boot into Win7, and there the wifi is working fine, so I know it's not a hardware issue.)

Thank you!

---

### Post by jeremy31 on 2024-08-10
See the wireless script link in my signature and post results

---

### Post by goemonburo on 2024-08-10
Thank you @jeremy31. 

Here's the pastebin link:  [https://pastebin.com/j1fics36](https://pastebin.com/j1fics36)

---

### Post by jeremy31 on 2024-08-10
Reboot and run the wireless script again and post results

---

### Post by goemonburo on 2024-08-10
Sure thing, here's the new one after a reboot:  [https://pastebin.com/meqYV8Y7](https://pastebin.com/meqYV8Y7)

---

### Post by jeremy31 on 2024-08-10
You may want to reboot the wifi router and if you are trying to connect to the hidden network, I would change the encryption to WPA2 only with no TKIP

---

### Post by goemonburo on 2024-08-10
The "hidden" network isn't hidden, but since it was not finding any network on a scan, I added it manually.  Should I delete that entirely and see if a scan works?  (It doesn't.)

---

### Post by goemonburo on 2024-08-10
Have to give the laptop to my folks tomorrow, any chance there's a clue to get this wifi working?  Thank you so much!

---

### Post by currentshaft on 2024-08-10
cool

---

### Post by jeremy31 on 2024-08-11
Try ```
sudo ifconfig wlp6s0 up
```

---

### Post by goemonburo on 2024-08-11
Thanks @currentshaft.

What's "grayed out" is the "Wifi netork(s)" line.  Normally (at least as I remember from the past) that would be black (as is the Eth0) and there'd be a connection there.  Perhaps Ubuntu is different but I marked this as Lubuntu, and there is indeed (if you right click) an option "Wifi - request scan"

The nmcli command you shared returns 1 line with "Name AP [1]  SSID (null) SSID-Hex (null) BSSID (E8:12:C9:1E:FE:33 mac address looks like?) Mode (Infra) Chan (6) Freq (2437 Mhz) and Rate (405)

---

### Post by goemonburo on 2024-08-11
@jeremy31, sadly, the ifconfig command didn't seem to have any effect.  There was no terminal message, nothing changed in the little icon...I tried doing another scan for wifi, nothing.

---

### Post by jeremy31 on 2024-08-11
Can you post results for ```
sudo cat /etc/netplan/90-NM-acdf38ae-3483-42f1-b0bd-4117a2a7f696.yaml
sudo cat /etc/netplan/01-network-manager-all.yaml
```
Remove any passwords if they exist in those files

---

### Post by goemonburo on 2024-08-11
@jeremy31, the first command said "no file or directory"; the second had network: version 2, renderer NetworkManager.  

Any next steps?

---

### Post by jeremy31 on 2024-08-11
Any results for ```
ls /etc/netplan
```

The script results shows a hidden wifi network on channel 3 but the ESSID is jibberish

---

### Post by goemonburo on 2024-08-11
That gives "01-network-manager-all.yaml"

---

### Post by goemonburo on 2024-08-11
When you say the ESSID is jibberish, what does that mean?  I don't think there's any hidden networks that I'd be trying to connect to.  The 2.4 and 5Ghz ones are broadcasting, I believe.

(And is the ESSID that you mention the same as the BSSID from the "nmcli" command above?  Or unrelated?)

(And thank you again for trying to help.  I'm just so baffled by the network connections...usually they're pretty plug and play.  Not sure why this is such a nightmare.)

---

### Post by jeremy31 on 2024-08-11
```
wlp6s0    Scan completed :
          Cell 01 - Address: <MAC '' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ac067b9186
                    Extra: Last beacon: 908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```
It may be normal for the ESSID to be that way on a hidden network but it is the only one found.  One thing to try is to have the 2.4GHz set to channel 1, 6, or 11

---

### Post by goemonburo on 2024-08-11
Well, thanks to @jeremy31 sticking with this and mentioning "hidden network" and channels, I switched from the phone-based router app to the web browser version and discovered that for some reason unbenownst to me, my 2.4Ghz band was hidden.  I unticked the hidden, waited a few secs, requested a wifi scan, and there it was.  And since it's an old computer it wasn't seeing the 5Ghz band at all (which wasn't hidden).  So...it looks like the issue had nothing to do with Lubuntu or the system, but was just an issue of the router hiding the network.  

Thank you all!

---

