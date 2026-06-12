---
title: "Atheros Wireless card, Please Help !"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by sunethpr on 2006-09-16
All,
  My laptop has a atheros wireless card/running drapper drake. The drivers seem to be loaded. I can scan access points using iwlist. It can see my access point. I tried setting it using network manager, but it doesn't pick anything up. I have WPA for encryption. Please can anybody point me to a good doc for setting up wireless with wpa/without network manager. Any help would be greatly appreciated. Thank in advance.

---

### Post by crazedgremlin on 2006-09-16
try this:

sudo ifconfig ath0 up

then reconfigure your card in Network Settings (System > Administration > Network Settings)

Good Luck 8-)

---

### Post by wieman01 on 2006-09-16
There is a solution for WPA(1) for Atheros:

[http://www.ubuntuforums.org/showthread.php?t=225290&page=11]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11")

WPA(2) will be slightly different, you can try this but if you need help, we can guide you through it. 

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Try the first link and see how it goes.

---

### Post by sunethpr on 2006-09-17
All,
  Sorry for the delay guys. I will try your suggestions and let you know. Thanks for the help.

---

### Post by karamba_kid on 2006-09-17
Here is what I did for my Atheros chipset. I installed the wpasupplicant package then i uninstalled the network-manager package, because with wpa_supplicant running; my connection would cut out ever couple of minutes or so.  But anyways basically I just added this to my /etc/network/interfaces. 
#Madwifi
auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ap-scan 1
wpa-scan-ssid 1
wpa-ssid OpenWrt
wpa-bssid xx:xx:xx:xx:xx:xx
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

That setup works for me, but for the wpa-psk entry it's actually not the actual psk it's the passphrase logic generated with the wpa_passphrase command.  To generate your own logic with this just do 
karamba_kid@ubuntu:~$ wpa_passphrase thenetworksssid
press enter, then enter the actual psk and press enter again and it will spit out the wpa-psk logic to use. Good Luck.

---

### Post by crazedgremlin on 2006-09-23
so did it work?

---

