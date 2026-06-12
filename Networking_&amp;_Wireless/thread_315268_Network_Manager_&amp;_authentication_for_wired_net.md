---
title: "Network Manager &amp; authentication for wired network"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by ottestad on 2006-12-08
I am connecting to a wired network that requires authentication and I have gotten this to work with wpa_supplicant. To use wpa_supplicant, I include a reference to it in /etc/network/interfaces.

If I boot up with Ubuntu 6.10 and the default /etc/network/interfaces-file, Network Manager works fine. I can then edit this file and add the reference to wpa_supplicant, and Network Manager continues to work.

If I then reboot, Network Manager stops working. I can still use wireless networks, but the program will no longer handle my wired connection. If I then remove the reference to wpa_supplicant in /etc/network/interfaces Network Manager works fine. I can then add the reference to wpa_supplicant back in /etc/network/interfaces and Network Manager continues to work.

I therefore suspect that Network Manager only works at boot if the /etc/network/interfaces-file is the default file. Is this true? Is there any way I can get around this?

My /etc/network/interfaces-file looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf 

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

My /etc/wpa_supplicant/wpa_supplicant.conf-file looks like this:

```
ctrl_interface=/var/run/wpa_supplicant 
ctrl_interface_group=wheel
ap_scan=0 
network={
	 key_mgmt=IEEE8021X 
	 identity="xxxxxx"
	 password="xxxxxx"
}
```

---

### Post by ottestad on 2006-12-11
I solved the problem!

Since Network Manager in Ubuntu Edgy does not manage interfaces set up in /etc/network/interfaces (read this on the mailing-list), it instead has the ability to read scripts in /etc/NetworkManager/dispatcher.d. In this folder there is a script called 0ifupdown that calls scripts in 4 subfolders of /etc/network/.

The interesting folder in my case is /etc/network/if-pre-up.d since the scripts in this folder will be called before the interface goes up. I therefore did the following:

```

cd /etc/network/if-pre-up.d
sudo touch wired-authentication
sudo chmod +x wired-authentication
sudo pico wired-authentication

```

I then added the following code to the file /etc/network/if-pre-up.d/wired-authentication:

```

#!/bin/sh

WPA_SUPPLICANT=/sbin/wpa_supplicant

if [ "$IFACE" = eth0 ]; then
  $WPA_SUPPLICANT -i eth0 -D wired -B -c /etc/wpa_supplicant/wpa_supplicant.conf
fi


```

Press Ctrl + X to quit and press y to save when asked.

This script will run wpa_supplicant with the config-file shown in the previous post just before eth0 is brought up.

Now NetworkManager works prefectly.

If you want to close wpa_supplicant when the interface goes down, you can just add a similar script to the folder if-post-down.d.

---

