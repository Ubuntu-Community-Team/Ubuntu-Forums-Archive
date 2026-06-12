---
title: "Can't quite get my wireless card working"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by I Use Dial on 2008-09-20
I use WiCD Manager to manage my network connections on my laptop.

The PCMCIA wireless card is a Linksys WPC55AG.

When I put the card in and hit refresh, WiCD can see the Wireless card and the wireless network that is available, but when I try to connect to it I don't get an IP address.

The network is WPA encrypted.  In Network Settings I have entered the password for this network.  Also, Network Settings sees the network as well.

What am I doing wrong?

---

### Post by I Use Dial on 2008-09-23
Polite "bump".

---

### Post by willca on 2008-09-23
Hi

For some odd reason, wicd does the same thing to my laptop sometimes...so I dumped it and went configured this manually.

Follow this and it will work everytime you bootup.

    * Install wpasupplicant first.

sudo apt-get install wpasupplicant

    * Create a file called /etc/wpa_supplicant.conf, and paste in the following. Modify the ssid and psk values. 

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

   * Run the following code to test it and make sure your router is broadcasting its SSID. 

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

If this works...then edit /etc/network/interfaces


If you are using static IP:

auto wlan0
iface wlan0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

or this, if you are using dhcp.

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Lastly..
sudo /etc/init.d/networking restart

---

### Post by I Use Dial on 2008-09-24
I ran  sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
and got this:

> Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

I copied and pasted your file example and only changed the ssid and psk values.

What have I done wrong?

---

### Post by I Use Dial on 2008-09-26
This wireless card issue is the last hurdle I have to overcome to get Ubuntu running on my laptop.  Can anyone help me here?  Doesn't seem like it should be so difficult.

---

