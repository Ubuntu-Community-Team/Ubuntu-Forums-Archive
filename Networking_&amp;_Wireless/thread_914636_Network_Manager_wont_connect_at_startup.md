---
title: "Network Manager wont connect at startup"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by blazemore on 2008-09-09
I am a fair distance away from my router, but close enough to ensure a consistant connection.

However, EVERY LOGIN, [I]without fail,[I] Network manager asks me for a WPA key for my wireless network. The field is already filled in (With the long version of the correct key), and I have to press connect maybe up to 4 or 5 times in a row to finally get it to connect.

Is there a way to ensure the Network Manager attempts to reconnect by itsself?

---

### Post by blazemore on 2008-09-23
1 week, bump

---

### Post by beameup on 2008-09-23
I've been having the same issue. And when it does connect, it disconnects in a minute or so. I don't know what happened to cause this. It's worked flawlessly forever. I removed it, deleted the config file in /opt then reinstalled it, but nothing changed. Not sure if I can call it a bug yet, could be PEBKAC.  :)

I switched to WICD  [http://wicd.net](http://wicd.net) and haven't had a problem since. You'll have to remove Network Manager to install this. 

I've just upgraded to the Intrepid Alpha hoping that might help but I get the same thing so I'm sticking with WICD until I figure it out.

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

### Post by lisati on 2008-09-23
Threads that might include useful information include the following:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
[http://ubuntuforums.org/showthread.php?t=748934](http://ubuntuforums.org/showthread.php?t=748934)

---

### Post by beameup on 2008-09-23
Thanks for the info. BTW: My wifi card is the Intel PRO/Wireless 2200BG 

I can't reply to post 748934 but I know the reason why he/she had to enter the keyring password everytime.

If you set Ubuntu to autologin it will always ask for the keyring code when connecting to wireless. If you login normally, it won't ask.

---

### Post by lisati on 2008-09-23
> **beameup said:**
> 

If you set Ubuntu to autologin it will always ask for the keyring code when connecting to wireless. If you login normally, it won't ask.

I was able to work round being asked for the keyring password with the libpam-keyring tweaks mentioned in the thread at [http://ubuntuforums.org/showthread.php?t=463621](http://ubuntuforums.org/showthread.php?t=463621)

---

