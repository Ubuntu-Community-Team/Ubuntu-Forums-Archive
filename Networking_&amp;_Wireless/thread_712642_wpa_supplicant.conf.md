---
title: "wpa_supplicant.conf"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by grumpylad77 on 2008-03-01
Trying to configure wpa_supplicant to connect to school network...
This is what I currently have in my wpa_supplicant.conf file, do I just need to fill in the blanks and save, or is there more that I need to put in the file?

# IEEE 802.1X with dynamic WEP keys using EAP-PEAP/MSCHAPv2

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="ssid"
	key_mgmt=IEEE8021X
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="username"
	password="password"
	ca_cert="/etc/cert/ca.pem"
}

---

### Post by kevdog on 2008-03-02
Try saving it in a file.  You might however have to play with the settings.

---

### Post by grumpylad77 on 2008-03-02
I have already spoken to the IT at school.... so I know for sure that the settings
EAP=PEAP
and MASCHAPv2

are correct. So are there anymore settings that would have to change?

---

### Post by CodeAlias on 2008-03-02
How did you generate the file  /etc/cert/ca.pem ?

---

### Post by grumpylad77 on 2008-03-03
i just used the example in /usr/share/doc/wpa_supplicant/examples
I used that one because it matches what my school uses so I don't know for sure what everything means

---

### Post by Whiffle on 2008-03-03
what happens when you try to use it ?

---

### Post by grumpylad77 on 2008-03-03
nothing.....

One time i tried to connect and it just came back as invalid username and password.... I know the username and password are correct because I could connect when i had windows on my laptop.

but every other time nothing has happened

---

### Post by Whiffle on 2008-03-03
How are you using it?  If you try it from the command line, it should give you some meaningful output.

---

### Post by scottro on 2008-03-03
If you try with a very simplified file, it sometimes works when the more complex one doesn't. 

Usually, you can get by with something like. 
```

network={
        ssid="mynetwork"
        psk="thisismypass"
}

```
If the wireless network does NOT broadcast its SSID (to not broadcast is the default with some wireless routers) then insert scan_ssid=1 so it would read
```

network={
         scan_ssid=1
        ssid="mynetwork"
        psk="thisismypass"
}

```

Of course, replace mynetwork with the network's SSID and thisismypass with your password.

Then, if your wireless card is wlan0 and the driver is the generic wext, run it from command line with
```

sudo wpa_supplicant -c /etc/wpa_supplicant.conf -Dwext -iwlan0 -d

```

Hrrm, I'm not in Ubuntu right now, and don't remember if they put wpa_supplicant.conf in /etc or in /etc/wpa_supplicant.  If the latter, then change the above to -c /etc/wpa_supplicant/wpa_suppliant.conf

Hopefully, you'll get some revealing error messages.

---

### Post by grumpylad77 on 2008-03-03
I will try that tomorrow between classes,

---

