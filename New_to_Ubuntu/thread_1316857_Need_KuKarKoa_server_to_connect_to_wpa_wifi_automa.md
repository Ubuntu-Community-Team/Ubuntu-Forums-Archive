---
title: "Need KuKarKoa server to connect to wpa wifi automagically"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by coverslide on 2009-11-06
OK so here's the story. I have a Kubuntu Karmic desktop which I'd like to double as a server machine, so I can reboot it for maintainence and be connected without having to log in. Logging in using kde's network manager works great, no trouble there, but getting it to start up with wireless seems to be a fruitless endeavor. The device is a DWA-130 Rev A which requires ndiswrapper. This seems to be fine as I see the device blinking before logging in whereas before it sat there dead. I've looked at several other guides which tell me to use wpa_supplicant.
 
I've tried using this:
 
```
 
wpa_passphrase <ssid> [passphrase]

```
 
which gets me this
 
```
 
network={
  ssid="my_ssid"
  #psk="pw_entered"
  psk=74793ea19937727818f06e6050a2d99e66c1bab205b0287084491a9b22399b76
}

```
 
which i copy to /etc/wpa_suopplicant/wpa_supplicant.conf.
I then changed my /etc/network/interfaces file to say this:
 
```
 
auto lo
iface lo inet loopback
 
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```
 
That's about as far as I've gotten. A reboot gets me a blinking adapter but no connection, I don't see it on my lan. I log into kde and still nothing. I then load it manually with the connection settings ui and it works fine. I don't want to have to do that every time, or have to rely on logging into kde since I am usually going to work on the machine remotely. Any help would be most appreciated.

---

### Post by coverslide on 2009-11-06
Sorry for the bump I'd just really like to have an answer to this

---

