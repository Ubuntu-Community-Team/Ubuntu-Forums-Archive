---
title: "Can Ubuntu 14.04 connect to an EAP-TTLS connection with an external 5ghz adapter"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by michaelenda372 on 2014-08-18
I know this is convoluted but I'm running Ubuntu 14.04 with a Belkin model F9L1108 external wifi adapter using rtl8192du-kernal-version drivers. The reason I'm running with an external adapter is that my school's wireless is only 5ghz, something my computer cannot connect to. The schools EAP method is EAP-TTLS and the phase 2 authentication is MSCHAPv2.


When I try to connect to the wireless my network manager says that my credentials are invalid.


Any help would be greatly appreciated as I would hate having to boot up into my ****** windows partition.

---

### Post by varunendra on 2014-08-19
Have you got any CA-Certificates to use with wireless from you school authorities? If not, ask for it. If yes, and you have used it, can you post a screenshot of wireless settings box showing "Wireless Security" tab? Of course obscure the parts you may consider sensitive (like 'username').

An alternative method to ignore ca-certificate requirement is to change the value of "system-ca-certs" line in connection profile from "true" to "false", or delete this line altogether. These connection profiles (also called "key-files") are located in "/etc/NetworkManager/system-connections" directory by default. You can edit them with your GUI text editor program (like gedit in default Ubuntu installation), running it with root-privilege (e.g. "gksu gedit"). Or you can use a single command in terminal -
```
sudo sed -i '/ca-cert/ s/true/false/' /etc/NetworkManager/system-connections/*[COLOR="#0000FF"]<your connection's key-file name>[/COLOR]*
```

---

### Post by michaelenda372 on 2014-08-19
I don't have a "system-ca-certs" line. Here is the code in the file for the wireless I'm trying to connect to.

```
 [ipv6]method=ignore


[connection]
id=******
uuid=19ab5e9b-3bfc-41a6-af32-3c4d9ebc841c
type=802-11-wireless


[802-11-wireless-security]
key-mgmt=wpa-eap


[802-11-wireless]
ssid=*****
mode=infrastructure
mac-address=******
security=802-11-wireless-security


[802-1x]
eap=peap;
identity=****
phase2-auth=mschapv2
password-flags=2


[ipv4]
method=auto



```

---

### Post by varunendra on 2014-08-21
Sorry for a late response - I'm afraid I don't have much time to dig deeper into this.

I suggest you seek help from other experts about your problem (via PM or just bumping your thread). Or, just post a fresh wireless_script report and wait till I get some free time to take a dive again.. :|

---

