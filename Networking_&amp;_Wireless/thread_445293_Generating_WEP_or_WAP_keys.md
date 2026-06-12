---
title: "Generating WEP or WAP keys"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by b_chris on 2007-05-15
What do you type to generate the WPA of WEP keys??

Regards.

---

### Post by spd106 on 2007-05-17
Generally you think up your own WEP keys, as this will directly match the same one in your access point. For the hex version they must be either 10 or 26 digits long or if you are using ascii then it is either 5 or 13 digits as each ascii digit == 2 hex.

For WPA you need both the ssid (network name) and a passphrase to calculate the key. It is generally recommended that the passphrase is at least 25 digits in length.
Once you have decided on a passphrase use the wpa_passphrase tool to generate a wpa_supplicant.conf which will contain the key.
e.g.
```
~$ wpa_passphrase 'essid' 'passphrase'
network={
        ssid="essid"
        #psk="passphrase"
        psk=85549a1b5442e3fe7841e89ec8efb4620798a7d6b0e6422a2e5fe8790525663d
}

```

Then copy this into a conf file. 

If you use network manager this will all be calculated for you, so you only need to enter the passphrase.

If you can't think of a passphrase or key yourself or you want to generate a random one, then there are various webpages that will do this for you.

---

