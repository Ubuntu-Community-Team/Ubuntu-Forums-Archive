---
title: "wpasupplicant help"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by grumpylad77 on 2008-02-28
I have been trying to get WPA_SUPPLICANT configured but all of the tutorials that I have found aren't helping much.
Does anyone have any experience setting up WPA_SUPPLICANT in Gutsy?

---

### Post by rajj on 2008-02-28
well depends on what you are trying to accomplish. Please try to be specific.
Generally, you can look at formats for the wpa_supplicant.conf under /usr/share/doc/wpa_supplicant/examples.
 Once you create the file(/etc/wpa_supplicant.conf) that meets your wireless network requirements, you can run wpa_supplicant as daemon by using:
wpa_supplicant -wB -i<interface> -c/etc/wpa_supplicant.conf
or in foreground:
wpa_supplicant -wd -i<interface> -c/etc/wpa_supplicant.conf

---

### Post by grumpylad77 on 2008-02-28
thanks,,, I think that will help,

---

### Post by grumpylad77 on 2008-02-28
I'm trying to connect to my schools wireless network that uses 802.1x

I copied and pasted this

# IEEE 802.1X with dynamic WEP keys using EAP-PEAP/MSCHAPv2

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="example 802.1x network"
	key_mgmt=IEEE8021X
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="user name"
	password="password"
	ca_cert="/etc/cert/ca.pem"
}


I copied and pasted that to /etc/wpa_supplicant.conf

Do I just need to fill in the blanks and save now?

Or is there more?

---

### Post by rajj on 2008-03-05
yup, change the file accordingly, save it and start the wpa_supplicant as I mentioned earlier.
then do this:
sudo dhclient <interface>, for example:
sudo dhclient eth1
In case of issues, run wpa_supplicant in non-daemon mode and try to follow the output to debug it.
another thing to check is ifconfig -a", see if interface is up and running.

---

