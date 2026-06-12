---
title: "connect to PEAP network"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by jbrown96 on 2007-06-28
I'm fairly new to Linux (<1 year) but love it. Working in an IT department for my university, which has landed me the great job of writing manuals to have Linux support for wireless. I have managed to get wireless working on our department's laptop (IBM t60) and can connect to the unsecured wireless network, but I am totally lost trying to connect to the secured one.

Our network uses PEAP authentication and EAP-MSCHAPv2 as the inner protocol. Our outdated instructions use xsupplicant, but I have had no success finding directions for it. Wpa_supplicant seems more promising, but I don't know how to configure it. I have tried to install wpa_gui, thinking it would be easier; however, it has uninstalled knetworkmanager, which is a disaster. 

System details:
Network
[LIST]
[*]PEAP
[*]802.11g
[/LIST]
Hardware
[LIST]
[*]IBM T60
[*]Intel Pro/Wireless 3945ABG
[/LIST]

Any help would be greatly appreciated. Thanks

---

### Post by wirelessmonkey on 2007-08-28
If you are still interested, It's my current job to make this exact setup work for 15,000 people, and honestly I no longer consider it difficult. I'd be happy to help out!

---

### Post by edwinlke on 2008-01-23
Hi, 

I am new to Linux and would like some help with my wireless connection to a secured network using WPA, PEAP. 

Cheers,
Edwin

---

### Post by Alucard13mm on 2008-01-29
I am also having trouble when I connect to the TTU campus wifi that uses PEAP authentication and EAP-MSCHAPv2.  Any new info on this would help a bunch.

---

### Post by Whiffle on 2008-01-29
I use WICD for connecting to the LEAP connection here.  It basically is a frontend for wpa_supplicant, and uses templates found in /opt/wicd/encryption/templates/ to generate a wpa_supplicant configuration.  The ones it comes with don't cover the situation I am in, but they might work for you, so try them.  If not, you can modify them to work for your situation.  I would recommend using wpa_supplicant to figure out what options you need to use, and then put those options in a wicd template.   This is the one that I use:

```

name = LEAP with WEP
author = Adam Blackburn
version = 1
require username *Username password *Password
-----
network={
        ssid="$_ESSID"
        scan_ssid=$_SCAN
        eap=PEAP
        key_mgmt=WPA-EAP
        identity="$_USERNAME"
        password="$_PASSWORD"
}

```


I attempted to use networkmanager back in the day and it sort of kind of worked sometimes, but WICD has been much much more reliable.

---

### Post by jbrown96 on 2008-02-06
I have since gotten my wireless working using Network Manager. I don't need to do edit any config files. I simply told it to connect to another wireless network, filled in all the settings (network name, WPA enterprise, EAP method, key type, phase 2 type, identity, password, and anonymous identity). 

It now connects automatically anywhere on campus. I disabled ipv6 (originally to speed up firefox - I don't notice any benefit), and it greatly helps me connect. I think that is a flaw with this specific network, but it may be worth trying.
I edited 
/etc/modprobe.d/aliases
changing 
> alias net-pf-10 ipv6
to
> alias net-pf-10 off

---

### Post by Alucard13mm on 2008-02-19
Well, I figured out how wifi works on campus now.  It was pretty simple.  All I had to do was to was choose the 'Connect to other Wireless network' enter TTUnet as the network name and change the wireless security to LEAP and enter my eraider account information.  :)

---

### Post by baosheng on 2008-07-17
Hi, I am also a Texas Tech guy. I wrote a shot article about how to do this. Maybe u can show it to any other Red Raiders using Linux. [http://narnia.cs.ttu.edu/drupal/node/147](http://narnia.cs.ttu.edu/drupal/node/147)

BTW, I am gonna start up a Linux user group, are you interested on it?

---

