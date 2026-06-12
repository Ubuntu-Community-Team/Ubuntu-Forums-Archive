---
title: "Network Manager Keyring doesnt save"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by srafx on 2006-10-11
As of this thread I am having the same problem:
[http://www.ubuntuforums.org/showthread.php?t=124636&highlight=network+manager+key](http://www.ubuntuforums.org/showthread.php?t=124636&highlight=network+manager+key)
I'm created a new thread because I feel it should be under networking and wireless rather then desktop enviornment.  Plus, in that post I didnt find a solution.

Take a look at the attached screenshot to see what I mean.  Also, I think I need to add a line in /etc/network/interfaces..which contains the following:

```
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


iface eth0 inet dhcp

auto eth0

```

Then I took a look at /wpa_supplicant.conf and it has:

```
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="linksys_SES_18297"
psk="mywirelesskeyhere"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
}

```

Can anyone help me store this password for the keyring?  What is happening is that it pops up everytime i reboot.  If I just restartx it will keep it stored.  Is there a way to store is in a file?

---

### Post by srafx on 2006-10-11
Does anyone know the syntax for this in one of those files?

---

### Post by dalonso on 2006-11-17
I think that those interfaces that are going to be used through Network Manager should not be present in /etc/network/interfaces.

By the way, if I'm not wrong only fixed IP interfaces should be present.

For example, my /etc/network/interfaces only has the loopback interface:

```
auto lo
iface lo inet loopback
```

because all network interfaces (wired and wireless) are managed through Network Manager.

Hope it helps.

---

