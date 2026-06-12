---
title: "Panda Wireless N USB / Ubuntu 17.04 not connecting to Xfinity router"
date: 2017-12-29
forum: Networking &amp; Wireless
---

### Post by CKP on 2017-12-29
Hi,

I've been struggling to get an old wireless card working and gave up and bought a Panda USB adapter instead. Ubuntu 17.04 seems to have recognized it as soon as I plugged it in, but I can't get it to connect to our xfinity cable box. Several other computers in the house connect to the cable router box and comcast cheerfully tells me the router is working fine. I can see the correct SSID and can see the password for the wireless network is correct. I have the computer wired via ethernet so it's fairly close (1 meter?) to the router and I can access the internet. But I'd like to move this computer somewhere more convenient. At this point, I might "hail Mary" and upgrade to 17.10. Anyone see anything in the pastebin? Thanks for all your help!

[http://paste.ubuntu.com/26280892/](http://paste.ubuntu.com/26280892/)

---

### Post by praseodym on 2017-12-29
Why do we see manually configured /etc/network/interfaces file? Re-set it to default:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Additionally, there is a bug in the network manager applet:
```

echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by CKP on 2017-12-29
Wow! Thanks for the fast reply and the successful code! I apologize for being a tinkerer and having messed up those files. It works! Thanks again!

---

