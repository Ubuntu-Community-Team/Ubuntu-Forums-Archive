---
title: "Wireless set up in a thinkpad using wpa_supplicant"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by anupamme on 2007-08-21
Hi, 

I am setting up wireless on Lenovo T42 thinkpad. I was following everything at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) and also read some of the related posts.

I installed wpa_supplicant and created (It wasnt present) a file /etc/wpa_supplicant.conf to add my network details in this form:

network={
        ssid="NetworkEssid"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=945609a382413e64d57daef00eb5fab3ae228716e1e440981c004bc61dccc98c
  }

Then I ran this command:  sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w. What I am getting as output is:

Trying to associate with <my_router's_hardware_address> (SSID='fightglobalwarming' freq=0 MHz)
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.

It repeats itself. I see the wireless network in System-Admin->Networking but its status is disconnected.

Can anyone suggest something?

thanks
pompey

---

### Post by wirelessmonkey on 2007-08-21
Try
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf

---

### Post by Darkhack on 2007-08-21
When running wpa_supplicant try "-Dwext" instead of "Dipw".  If that doesn't work, there is a tutorial specifically for your wireless device.

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by anupamme on 2007-08-23
Thanks both of you for replying. It helped and I was wireless as a result.

-p

---

