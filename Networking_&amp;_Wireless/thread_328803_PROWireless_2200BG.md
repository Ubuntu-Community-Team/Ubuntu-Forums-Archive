---
title: "PRO/Wireless 2200BG"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by jonnymccullagh on 2006-12-31
I have just installed Ubuntu 6.06 (on Dell Latitude D810) and I am trying to get the wireless connection working but it does not seem to work.
The wireless device is in the Device Manager as Intel PRO/Wireless 2200BG, and when I visit System->Administration->Networking I have 3 options: Wireless (eth1), wired (eth0) and Modem.
I have tried configuring the Wireless network and the ESSID of my wireless network appeared in the drop down so I thought it should work well. I left it as DHCP and entered the WEP key and click OK. However the network connection never seems to work.
I have tried the WEP key as plain text and hexadecimal. I have tried it with no spaces and with hyphens after each 4 digits (xxxx-xxxx-xxxx-xxxx-xx) but nothing seems to work.

Am I missing something obvious?
Thanks in advance,
jonny

p.s. I remember setting up Kubuntu Breezy on a laptop and entering the WEP key during the install and everything ran so smoothly but I've had trouble with 6.06 and 6.10 getting wireless working.

p.p.s I have got the wireless connection working on my network from a Win XP installation so I don't think it is a problem with the router.

---

### Post by SugarDaddy on 2006-12-31
The first thing to check is that your WiFi card sees your router. Type the following command in a terminal:
```
iwlist scan
```Assuming that eth1 is your WiFi card you should get output similar to this:
```
eth1      Scan completed :
          Cell 01 - Address: <removed>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 892ms ago
```My router uses WPA2 with AES encryption so your router, which is WEP, will obviously be different.

If you get output, then post the contents of your /etc/network/interfaces file by typing the following command:
```
sudo gedit /etc/network/interfaces
```You should also specify what applets you are using:  network manager, WiFi radar, etc.

I don't have any experience with connecting to WEP routers (this is an older, less secure encryption protocol) but somebody probably will be able to help.

---

### Post by haiku99 on 2006-12-31
the network tool can do funny things to the interfaces file, in my case it put a -s in front of the WEP 
key...but you can edit the file manually with the correct essid and key, reboot, and it should work.
In any case, looking at the file should give you a better idea of what is happening as was said...

---

### Post by jonnymccullagh on 2007-01-03
Thanks for the help, the iwlist command gives me the following:
```
eth1      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"WANADOO-xxxx"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=93/100  Signal level=-35 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 10ms ago

```

My /etc/network/interfaces for eth1:
```
auto eth1
iface eth1 inet dhcp
wireless-essid WANADOO-xxxx
wireless-key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx

```

The WEP key appears as I entered it into System -> Administration -> Networking although I am happy to edit the file directly(but if I make a change how do I restart networking).
The only applet I think I have is Network Monitor and Network Manager Applet 0.6.2. This is the first time I have tried gnome as I usually prefer Kubuntu.
Based on the outputs above should the wireless connection work? Or what could be the problem?
Thanks for the help,
jonny

---

### Post by SugarDaddy on 2007-01-03
Well your wireless card sees your router so that's good! However, it appears that the router encryption is WPA, not WEP. So you have two choices:

1. Reconfigure your router for WEP (not recommended, WEP is an older, less secure encryption standard that is easily cracked.)
2. Download and install wpasupplicant so you can connect to WPA encrypted routers (unfortunately, WPA is not supported standard by Ubuntu out of the box).

Fortunately, configuring your wireless card for WPA is not too difficult. However, you can't use network manager, which is usually not a big deal if you are only connecting to one network. So if you decide to go the WPA route, which I encourage, the following links will step you through the process. The first is the Sticky HowTo at the top of this forum. The second is a good walkthrough on how to install wpa_supplicant and configure it within the wpa_supplicant.conf file as well as troubleshooting techniques.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[URL="http://ubuntuforums.org/showthread.php?t=263136"]http://ubuntuforums.org/showthread.php?t=263136
[/URL]
Hope this helps! :)

---

### Post by jonnymccullagh on 2007-01-15
Thanks for the help. The following tutorial sorted me out:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

But I also needed to press the "1" button on my Wanadoo/Orange Access Point (Livebox) (doh)

Thanks again,
jonny

---

### Post by SugarDaddy on 2007-01-15
Glad to see you got things working and didn't give up on WPA!

---

