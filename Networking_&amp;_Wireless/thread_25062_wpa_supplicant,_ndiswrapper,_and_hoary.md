---
title: "wpa_supplicant, ndiswrapper, and hoary"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by benkorkor on 2005-04-09
I need help setting up WPA on my wireless network. I've successfully set up ndiswrapper to my WEP, but now I want to use WPA since it's way more secure. 
I installed wpa_supplicant via apt-get and made my self a wpa_supplicant.conf file(stored in /etc), but when I entered:

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -d ndiswrapper

in console, it gave me a plethora of erros:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='localnetwork'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:09:5b:8a:8e:11
wpa_driver_hostap_set_wpa: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
Failed to enable WPA in the driver.
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
Failed to disable WPA in the driver.
wpa_driver_hostap_set_drop_unencrypted: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
wpa_driver_hostap_set_countermeasures: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
rmdir[ctrl_interface]: Bad address

Here's my wpa_supplicant.conf in /etc:

# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
ssid="localnetwork"
scan_ssid=1
key_mgmt=WPA-PSK
proto=WPA
pairwise=CCMP TKIP
group=CCMP TKIP
key_mgmt=WPA-PSK
psk="paraphrase"
}

I have no idea what or why I'm having these problems because there isn't a lot of documentation that are newbie-friendly. I read the wiki but didn't quite understand what to do. I don't even know if I'm approaching this process in correct order. Can someone help? It would be great if someone wrote a nice guide on how to set this up.

---

### Post by joshmachine on 2005-04-09
Are you sudoing it?

i.e. 
sudo wpasupplicant ....

---

### Post by benkorkor on 2005-04-09
Forgot to add it in the post. Yes, sudo was used.

---

### Post by joshmachine on 2005-04-10
[QUOTE=benkorkor]Forgot to add it in the post. Yes, sudo was used.[/QUOTE]
 What's your hardware set-up?

---

### Post by benkorkor on 2005-04-10
Netgear ma521 pc card, Netgear mr814 router.

---

### Post by goal_joel on 2005-04-12
> Netgear ma521 pc card
I also have a Netgear MA521 pc card, and according to the box it does not support WPA (only WEP).

Since ndiswrapper uses Netgear's WEP-only Windows drivers for your card, I don't think you can do WPA.  I don't entirely understand what wpa_supplicant does but in reading some of its documentation it appears it requires a WPA-capable driver.

Unfortunately, it looks to me that you are stuck with WEP.

I haven't set up my MA521 pc card with Hoary (yet) but I've got it going with SimplyMEPIS through ndiswrapper with WEP encryption.

---

### Post by benkorkor on 2005-04-12
I think it does suport WPA, not full WPA but WPA-PSK. I tried it on WIndows and didn't have a problem with it.

---

### Post by goal_joel on 2005-04-12
> I think it does suport WPA, not full WPA but WPA-PSK. I tried it on WIndows and didn't have a problem with it.
That is nice to know, thanks.  I will have to look into trying WPA eventually when time is free.

Sorry that I can't give you any other potential insight.

---

### Post by benkorkor on 2005-04-12
No problem, let me know if you find anything helpful. I would really want to get this set up as soon as possible. In the meantime, back to cables.

---

### Post by luca_linux on 2005-04-12
Try: "sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -d".
Note that "-D" is a capital letter.

---

### Post by benkorkor on 2005-04-15
Tried that and it gave me the following, repeating every 5 seconds:
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 607 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:0f:b5:1b:51:c0 ssid='' wpa_ie_len=24 rsn_ie_len=0
   skip - SSID mismatch
1: 00:06:25:7b:cd:e7 ssid='Jasieniuk' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     6c 6f 63 61 6c 6e 65 74 77 6f 72 6b               localnetwork
ioctl[SIOCSIWSCAN{,EXT}]: No such device
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
Received 607 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:0f:b5:1b:51:c0 ssid='' wpa_ie_len=24 rsn_ie_len=0
   skip - SSID mismatch
1: 00:06:25:7b:cd:e7 ssid='Jasieniuk' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
No suitable AP found.

It seems like it can't find the AP(SSID is not set to broadcast) even though I supplied it in the wpa_supplicant.conf. Or is it totally necessary to have SSID broadcast?

---

### Post by luca_linux on 2005-04-15
I can't help you because I don't use ndiswrapper but ipw2200...anyway I've read something about your problem in this forum...try to search.

---

### Post by jackson on 2005-04-15
I have the exact same problem with my dell 700m.  ndiswrapper loads the drivers fine and I can access with WEP.  I have configured wpa_supplicant the way I normally do on other distros and it scans but can't connect to the AP.  I have tried with essid broadcast and without and no difference.

Any help would be great!  

Thanks!

---

### Post by benkorkor on 2005-04-22
Anyone?

---

### Post by dejitarob on 2005-04-23
You don't need SSID broadcast on, I am using it just fine with it off. Can you find the AP when you are not using wpa_supplicant? Is Jasieniuk your SSID? If so, wpa_supplicant is reporting that it does not support WPA.

---

### Post by benkorkor on 2005-04-23
No, Jasieuk is not my SSID. Yes, it can find my SSID even when it's not set to braodcast when using WEP(not using wpa_supplicant).

---

