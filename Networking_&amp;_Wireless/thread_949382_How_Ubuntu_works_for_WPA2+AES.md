---
title: "How Ubuntu works for WPA2+AES?"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by wolfteeth on 2008-10-16
Dear All,

I read the post here for how to configure Wireless security, but sorry, I am still not able to get it works, :(.

My steps are:
1. Wpa-supplicant is latest updated
2. iwconfig can detect wlan0
3. iwlist scan can detect wireless
4. gedit /etc/network/interfaces
5. What encounter are:
   1. auto wlan0
   2. iface wlan0 inet dhcp
   3. wpa-driver wext
   4. wpa-ssid PENet
   5. wpa-ap-scan 2 (hidden broadcast)
   6. wpa-proto RSN WPA (WPA2)
   7. wpa-pairwise CCMP TKIP (AES)
   8. wpa-group CCMP TKIP
   9. wpa-key-mgmt WPA-EAP (WPA Enterprise authentication)
   10.wpa-eap PEAP (Protected EAP)
   11.wpa-identity chouma
   12.wpa-identity password (how to encrypt this password?)
   13.wpa-phase1 fast_provisioning=1
   14.wpa-pac-file /path/to/eap-pac-file

and then do: networking restart...
but DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3,5,9,11... no DHCPOFFERS received...
no working leases in persistent database -sleeping...

may we know if anyone can guide me in details? thanks...

and once I tried to iwlist scan several times, I found I lost the updates in /etc/network/interfaces, why?

---

### Post by wolfteeth on 2008-10-16
any?

---

### Post by wolfteeth on 2008-10-16
network authentication: wpa2
data encryption: aes - ccmp
authentication type: peap
authentication protocol: MS-CHAP-V2
user credentials: use windows logon
roaming identity: domain\user name
validate server certificate: (box checked)
(sub menu) certificate issuer: any trusted ca

---

### Post by wolfteeth on 2008-10-16
network authentication: wpa2
data encryption: aes - ccmp
authentication type: peap
authentication protocol: MS-CHAP-V2
user credentials: use windows logon
roaming identity: domain\user name
validate server certificate: (box checked)
(sub menu) certificate issuer: any trusted ca

:guitar:

---

### Post by kevdog on 2008-10-16
I know you want to get this figured out ASAP, but please allow some people to digest the information.  It sometimes takes about 24 hours to get a decent response.  Reposting the same info again and again doesnt help the situation.

---

### Post by wolfteeth on 2008-10-21
Finally, I found Network Manger + Intel 3945ABG works for WPA2+AES...

---

