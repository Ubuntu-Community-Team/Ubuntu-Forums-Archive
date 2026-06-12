---
title: "WPA with Broadcom"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by ninjapenguin on 2008-06-19
Hello,

I have set up my broadcom driver with ndiswrapper, and I can view different networks, but when I try to access my WPA encrypted network, it never actually connects and keeps asking me for my password ever minute.  So I tried setting up WPA_supplicant by having this as my .config file:

network={
ssid="Obel"
proto=WPA
key_mgmt=WPA-PSK
psk=f631f1d60aeee81ef8a9786f9dd00faad9fced38889b7d 580b756ba3db56067d
}

and when I tested it this is what I typed and got back:

obel@Linux-Ubuntu:~$ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w
Trying to associate with 00:1e:52:7c:62:c6 (SSID='Obel' freq=2452 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

So if some one can give me some suggestions of what I can do to get it working, it would be much appreciated.

---

### Post by s1337m on 2008-06-20
> **ninjapenguin said:**
> Hello,

I have set up my broadcom driver with ndiswrapper, and I can view different networks, but when I try to access my WPA encrypted network, it never actually connects and keeps asking me for my password ever minute.  So I tried setting up WPA_supplicant by having this as my .config file:

network={
ssid="Obel"
proto=WPA
key_mgmt=WPA-PSK
psk=f631f1d60aeee81ef8a9786f9dd00faad9fced38889b7d 580b756ba3db56067d
}

and when I tested it this is what I typed and got back:

obel@Linux-Ubuntu:~$ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w
Trying to associate with 00:1e:52:7c:62:c6 (SSID='Obel' freq=2452 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

So if some one can give me some suggestions of what I can do to get it working, it would be much appreciated.

I am having the same trouble as you, on a bcm4328 card. 

EDIT:  I too have ndiswrapper installed but I tried using the wext driver for that wpa_supplicant command, and got the following output:

Trying to associate with 00:13:10:04:e0:a0 (SSID='fdsfs' freq=2412 MHz)
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:18:39:fd:84:13
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Authentication with 00:00:00:00:00:00 timed out.
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Trying to associate with 00:13:10:04:e0:a0 (SSID='domo' freq=2412 MHz)
Associated with 00:13:10:04:e0:a0
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
Associated with 00:13:10:04:e0:a0
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
Associated with 00:13:10:04:e0:a0
Associated with 00:13:10:04:e0:a0
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK

However, I still cant connect... the only difference was I was prompted for my password every minute

---

### Post by aladagemre on 2008-06-28
I have the same problem, with bcm4328 card. My ndiswrapper driver didn't work for Ubuntu 8 (it was ok in 7.04). The wireless light even did not lit on. Then I realized a balloon saying that there's a suitable driver for it (b43, ssb). I let it install those (they removed ndiswrapper from the startup modprobe initialization) and the light was lit on. Then tried to connect internet with 

wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf&
dhclient wlan0

I saw that it could not get IP address while the association timed out. Then I used
rmmod b43
rmmod ssb
modprobe b43
modprobe ssb

Then I tried the same thing and was successful. The difference was the EAPOL warnings below. Now it connects and disconnects frequently(every 5-10sec). But I try to surf although it is slow. 


Associated with 00:12:bf:60:06:b1
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
Authentication with 00:12:bf:60:06:b1 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
Trying to associate with 00:12:bf:60:06:b1 (SSID='TITANIC' freq=2437 MHz)
Associated with 00:12:bf:60:06:b1

Does anyone have any idea? How rmmod and modprobe can change this?

---

### Post by edenuccio on 2008-08-21
I have the same problem... I've followed every guide referencing similar connectivity issues and always see the same thing as the people here. I wanted to use ubuntu on my macbook because I can't stand OS X but if I can't connect to my wireless router at home (airport extreme) then I have to give it up.

---

