---
title: "Same MAC address in different files inside /etc/NetworkManager/system-connections/?"
date: 2015-03-23
forum: Networking &amp; Wireless
---

### Post by Ulf_Dunkel on 2015-03-23
I am looking for any solution for the well-known issue that some Ubuntu machines repeatedly ask for the WLAN password although it has already been successfully entered and the WLAN connections persists.

Now I have checked the files written by NetworkManager into /etc/NetworkManager/system-connections/. I wonder what the identical MAC addresses in two of three files stand for and if they could be the cause of the repeating WLAN password question.

```
[connection]
id=inversWLAN
uuid=8a09c650-8054-49bd-866c-bf4e6b5e9b1a
type=802-11-wireless

[802-11-wireless]
ssid=inversWLAN
mode=infrastructure
mac-address=00:08:CA:A1:B4:FC
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
auth-alg=open
psk=***************

[ipv4]
method=auto

[ipv6]
method=auto


- - - - -

[connection]
id=Speedlink-307
uuid=d8529ac5-ea85-40a2-888e-74e37a96d974
type=802-11-wireless

[802-11-wireless]
ssid=Speedlink-307
mode=infrastructure
mac-address=00:08:CA:9E:C6:F2
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
auth-alg=open
psk=***************

[ipv4]
method=auto

[ipv6]
method=auto
- - - - -
[connection]
id=WLAN-4D3658
uuid=0243eb20-5f2a-4575-906a-6e4c1f6463fa
type=802-11-wireless

[802-11-wireless]
ssid=WLAN-4D3658
mode=infrastructure
mac-address=00:08:CA:9E:C6:F2
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
auth-alg=open
psk=***************

[ipv4]
method=auto

[ipv6]
method=auto

```

As you can see here, the WLAN connections "Speedlink-307" and "WLAN-4D3658" have the same MAC address. Can you please explain why?

---

### Post by gordintoronto on 2015-03-23
The MAC address is part of YOUR computer. The SSIDs are wireless routers which are not part of your computer.

---

### Post by Ulf_Dunkel on 2015-03-24
Thank you for your quick reply, gordintoronto. But why then does my computer have two different MAC addresses?

As you can see from my code snippet above, it has

ssid=inversWLAN
mac-address=00:08:CA:A1:B4:FC 

ssid=Speedlink-307
mac-address=00:08:CA:9E:C6:F2

ssid=WLAN-4D3658
mac-address=00:08:CA:9E:C6:F2

When does the MAC of a computer change?

---

### Post by gordintoronto on 2015-03-24
I'm sorry, but I don't know what produced your "code snippets." More information might help.

---

