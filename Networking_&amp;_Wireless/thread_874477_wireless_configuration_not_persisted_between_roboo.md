---
title: "wireless configuration not persisted between roboots"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by donahuejw on 2008-07-30
I'm a linux newbie and I just installed 8.0.4 on a Dell Inspiron 8100 that has a linksys wrt54G v3 wireless card installed.

I've installed ndiswrapper and the drivers for the linksys card.  By clicking on the network manager applet and choosing the "connect to other wireless networks..." option I can successfully connect to my wireless router, but as soon as I reboot I lose the settings and have to redo the connection.  How do I get the settings to stick?

---

### Post by donahuejw on 2008-08-26
Replying to get my message back to the top in hopes of getting an answer from someone.

Apologies if this is considered bad form.

---

### Post by donahuejw on 2008-09-02
I found the solution to this.  I needed to add the following to my /etc/network/interfaces file:

auto wlan0
iface wlan0 inet dhcp

wpa-driver wext
wpa-ssid <my_SSID>
wpa_ap_scan 2
wpa_proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <my_passphrase_in_hex>

Then I created an shell script containing the following command:

  /etc/init.d/networking restart

and made it executable: 

  sudo chmod +x /etc/init.d/wireless-network.sh 

Finally, I created a symbolic link to this script:

  sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S40wireless-network 

and then restart.

Hope this helps someone else.

---

