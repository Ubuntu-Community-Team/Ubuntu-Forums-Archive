---
title: "Signal but wont connect."
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by englishmen on 2006-10-13
In response to my previous post

[http://ubuntuforums.org/showthread.php?t=276247&highlight=baffled](http://ubuntuforums.org/showthread.php?t=276247&highlight=baffled)

My wifi was switched off when ubutu was installing now ive reinstalled i can connect to the internet if i plug it in with a cable. The strange thing is that if i go to network setting, under wireless connections it lists 3 wifi signals, my one and im guessing my neighbors. However i cant connect to any of them, my signal shows up with a square icon with a eiffel tower type symbol in the middle the others with a shield type icon.

I copied and pasted my WEP key so its correct yet it still does not connect. The light on my laptop which indicated wifi activity does flash but still nothing.

---

### Post by englishmen on 2006-10-13
I just managed to connect to a neighbors wifi signal, which doesnt required a wep key. It worked perfectly, so my hardware on my laptop is working but i still cant connect to my own signal.

Any suggestions?

Thanks.

---

### Post by englishmen on 2006-10-13
I just changed Encryption from WPA-PSK Encryption to WEP Encryption on my router and i can now connect. Does ubuntu not support WPA-PSK Encryption?

---

### Post by wieman01 on 2006-10-13
It does but you either configure it manually or have to install additional tools such as Wifi-Radar or NetworkManager in connection with "wpa_supplicant". I am running WPA(2) (AES) but I chose the manual approach. The tools are insufficient for my needs (Static IP, no broadcast of ESSID, etc.).

---

### Post by englishmen on 2006-10-13
So i can use WPA-PSK Encryption if i get one of the apps you suggested, correct?

If so do you know where i can get Wifi-Radar because i searched in synaptic package manager with no luck?

Thanks

---

### Post by wieman01 on 2006-10-13
The package is called "wifi-radar" and can be found in the repositories. Make sure your source-list disposes of these lines.
Open source-list:
> sudo gedit /etc/apt/sources.list
Then paste:
> # Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

