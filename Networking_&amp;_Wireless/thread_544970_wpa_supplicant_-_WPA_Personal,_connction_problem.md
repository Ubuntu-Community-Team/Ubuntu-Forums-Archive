---
title: "wpa_supplicant - WPA Personal, connction problem"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by ittiam on 2007-09-07
I have been using wpa_supplicant successfully for almost an year now. But 2 days ago my router was reset and I am not able to connect to my wireless network after that. But i can connect using my Knetworkmanager.

when i run

```
ittiam@Inspiron-e1505:~$ sudo wpa_supplicant ~D ndiswrapper -i eth1 -c /etc/wpa_supplicant.conf -B &
[1] 9674
ittiam@Inspiron-e1505:~$ ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported

```

I have tried killing wpa_supplicant, modprobing ndiswrapper again and again...trying wext instead of ndiswrapper nothing works. but knetworkmanager works like magic.

I googled to find out that in my linksys WRT54G has nothing called WPA Pre-shared key option for wireless security but has WPA personal. I dont remember what was the setting before reset. 

my wpa_supplicant.conf

```
network={
       ssid="my_essid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk=my_key
}

```

> 
ittiam@Inspiron-e1505:~$ sudo cat /proc/net/ndiswrapper/eth1/hw
status=ready
mac: 00:18:f3:00:7f:6b
beacon_period=100 msec
atim_window=0 msec
frequency=2437000 kHZ
hop_pattern=0
hop_set=0
dwell_time=0 msec
tx_power=1496 mW
bit_rate=54000 kBps
rts_threshold=2347 bytes
frag_threshold=2346 bytes
power_mode=always_on
encryption_modes=WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

any help will be appreciated.

---

### Post by theonlyrealperson on 2007-09-07
Did you check your settings on your router? When the power goes out or my router is reset, the router itself loses all it's settings. When you connect using KNetworkmanager, do you have to put in your passkey?

Sorry if these seem like beginner's questions, but you didn't specify in your original posting. 

KNetworkmanager could be connecting to your now open wireless broadcast. And it would also explain why you can't connect using wpa_supplicant. It seems to fit the error messages too...

---

### Post by ittiam on 2007-09-07
Yes yes I had all the settings done in my router. It is set to use WPA personal and TKIP. Yes knetworkmanager did ask me for the password and i entered, voila magic! 

my wpa_supplicant.conf actually looks like this. sorry for the wrong thing in my first post

> ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="my_essid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       group=CCMP TKIP
       pairwise=CCMP TKIP
       psk=my_psk
}


---

### Post by theonlyrealperson on 2007-09-07
Personally, I think there is a setting that's changed on the router itself. That is what was reconfigured in the first place, your settings on wpa_supplicant have remained static. So, I guess that's where I would start.

That theory still works with KNetworkManager working and not wpa_supplicant. With KNetworkManager you are choosing an existing wireless broadcast and tuning your computer to it. With wpa_supplicant you are broadcasting something preconfigured. 

I'd fiddle with some options on your router to see if it will connect. 

Sorry I couldn't be more helpful. :(

---

