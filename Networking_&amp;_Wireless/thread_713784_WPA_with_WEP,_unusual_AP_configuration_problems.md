---
title: "WPA with WEP, unusual AP configuration problems"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by elver on 2008-03-03
I recently moved to a new place where there's no long-term option of getting connected via ethernet cable. My laptop has the Intel 2200BG card in it. Usually works fine with the ipw2200 driver. However the network configuration here is kinda odd:

```

root@daedalus:~# iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:1A:70:DF:5D:CB
                    ESSID:"katleri"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-65 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 280ms ago

```

I've tried different guides on the net and the closest I've gotten to actually connecting to the network is clicking on the gnome panel thingie, choosing the wireless network, and it prompting me for the passphrase and encryption method. When that window pops up, iwconfig shows eth0 as associated.

However, that window only gives 3 encryption options: wpa personal, wpa2 personal, leap. And if I choose any of the first two and enter the passphrase, the window goes away and comes up again in a few seconds, asking the same question. And while iwconfig still shows the interface as associated, dhclient won't get an IP.

So, basically, I'd like to know which settings I need to use to connect to a network like that. Because that WEP-40 part seems odd and out of place to me and I've only seen it mentioned once in passing in the depths of the wpa_supplicant documentation. The passphrase I was given is a 10-digit hex string.

If someone could write a wpa_supplicant.conf file based on the above information or tell me what I need to install or configure in order to get connected, that would be much appreciated. Thanks!

---

### Post by pestilence on 2008-03-03
I am having the same problems with the same card (see my post) It seems this is a ipw2200 problem with WPA enabled networks.
Changing security to WEP does work for my networks, but I am unable to connect to any WPA networks.

---

### Post by pestilence on 2008-03-03
Also I found this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

Seems the incompatibility still exists.

---

### Post by elver on 2008-03-03
I think the difference is that in my case the SSID is broadcast, but it still won't connect to the network with WPA here.

While your bug is very similar to my bug (though I haven't tested things with WEP) our bugs don't seem to be very similar to the linked bug (which is about broadcasting or not broadcasting SSID)

---

### Post by pestilence on 2008-03-03
Haven't checked out with the broadcasting of the ssid (I am at work and wireless at home) but I surely can't connect to any WPA networks for some reason :(

---

