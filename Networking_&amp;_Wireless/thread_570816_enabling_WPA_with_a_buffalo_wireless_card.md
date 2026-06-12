---
title: "enabling WPA with a buffalo wireless card"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by dooglex on 2007-10-08
HI, I am using fiesty and can make my PCI wifi card see my WPA encrpyted network and attempt to connect but am only offered WEP and not WPA options for the key, 

I have setup a wpa_supplicant.conf in /etc/ and added my SID and WPA key.
When i type

sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf

i get 

CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported

 and when i break i get
Failed to disable WPA in the driver.

Which i think means WPA is running correctly but still wont show up in the list.

The guide i was trying to follow was: [http://ubuntuforums.org/showthread.php?t=569746&highlight=wpa+supplicant](http://ubuntuforums.org/showthread.php?t=569746&highlight=wpa+supplicant)

---

