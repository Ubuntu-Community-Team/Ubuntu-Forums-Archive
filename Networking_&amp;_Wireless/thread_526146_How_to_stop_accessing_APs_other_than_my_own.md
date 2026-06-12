---
title: "How to stop accessing APs other than my own ?"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Roswellgrey on 2007-08-15
Despite much searching, I cannot work this out ......

I am using scripts and wpa_supplicant to access my wifi  AP, rather than network-manager.
( as no SSID broadcast )

It works well, but for the life of me I cannot work out how to STOP it accessing open, unsecured networks if my AP is down or off...

I am sure i need to add to the wpa_supplicant confg file - I just cannot work out what ....

Start script
--------------

sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -dd
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

wpa_supplicant.conf
----------------------------

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
ssid="MyNetwork"
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="xxxxxxxxxxxxxxxxxxxxxxxxx"
}



So, what do I need to add to  stop it accessing networks that I haven't explicitly defined in wpa_supplicant.conf ?

TIA

---

### Post by kevdog on 2007-08-15
You could try this -- not sure if it will work, but worth a shot

In the line that states:

```
sudo iwconfig wlan0 mode managed
```

Try
```
sudo iwconfig wlan0 mode managed essid <"ESSID in Quotes"> ap <MAC Address of Router>
```

For some reason if the above statements doesnt work, I would then put the statement
```
sudo ifconfig wlan0 up
```
after the above statement:
```
sudo iwconfig wlan0 mode managed essid <"ESSID in Quotes"> ap <MAC Address of Router>
sudo ifconfig wlan0 up
```

rather than before as shown in your earlier post

Let me know if this works.

---

### Post by Roswellgrey on 2007-08-15
Thanks for that.
For some unknown reason ( i.e. I must have done something different ! ) 
it is behaving itself at the moment and very nicely not scanning / not connecting 
when my network is down.
If  / when it starts again, I will try your suggestions and let you know :)

---

