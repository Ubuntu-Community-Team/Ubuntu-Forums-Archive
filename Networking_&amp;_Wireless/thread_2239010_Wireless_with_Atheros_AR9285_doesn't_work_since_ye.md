---
title: "Wireless with Atheros AR9285 doesn't work since yesterday"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by SiLiKhon on 2014-08-11
Hi all!
I've been experiencing problems with my Atheros AR9285 wireless card in Ubuntu for long time (like frequent disconnects during weak/busy network environment).
However since yesterday evening I am unable to use it at all: network manager takes quite a lot of time to connect to a network, but I have no Internet access after this connection is established (I cannot even ping the access point itself).
I thought this was a driver issue, so I tried to switch from ath9k (which I've been using always before) to ndiswrapper - it performs exactly the same.
The access point works for other devices. Even on this laptop wireless works in Windows and (!!!) with Ubuntu Live usb - the one that I used to install this os ~three months ago.
It looks like this is related to encryption: I was able to connect to an open AP once (although I was not able to do this again some time later).

I attach the output of  wireless_script (I ran it twice with the two drivers set up) to this post.
Would appreciate any help!

Thanks!

---

### Post by SiLiKhon on 2014-08-11
Small update:
I tried to *apt-get purge network-manager* and set up connection manually.
I was able to connect to an open access point (by *sudo iwconfig wlan0 essid <NETWORK_NAME>* and then doing *dhclient wlan0*).
However for WPA and WPA2 networks I tried:
```
[I]wpa_passphrase <NETWORK_NAME> <PASSKEY> > file.conf
sudo wpa_supplicant -B -i wlan0 -Dwext -c file.conf # there was this output from this command:[/I]
    Successfully initialized wpa_supplicant
    ioctl[SIOCSIWENCODEEXT]: Invalid argument
    ioctl[SIOCSIWENCODEEXT]: Invalid argument
*# but it didn't return (I could see it running in background using ps -e)*
*sudo dhclient wlan0* # this hang forever
```

In all of these cases *iwconfig wlan0* showed that it did have an associated access point
Also my LED WiFi indicator on the laptop behaved weird in all of the cases: it went on and off with constant frequency, while usually it simply glows constantly. This however might be related to ndiswrapper, I have never used it before.

*Upd.*
Yes. with ath9k my LED indicator glows constantly. Even dhclient returns after 10-20 seconds, however the IP that I get is weird:
```
wlan0     Link encap:Ethernet  HWaddr <MY_MAC_ADDRESS>  
          inet addr:192.168.0.255  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:fed2:c1e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58413 (58.4 KB)  TX bytes:11152 (11.1 KB)
```
Of course I cannot ping anything with afterwards.

---

### Post by SiLiKhon on 2014-08-15
Does anyone have any suggestions?

---

### Post by SiLiKhon on 2014-08-18
I tried a USB WiFi module and it works. I don't understand why: the internal one works on clean Ubuntu 14.04 (from live USB) and in Windows, but doesn't work with either of the two drivers (ath9k and ndiswrapper) on my current system...
The usb module is:
```
 D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]
```
Any suggestions?

---

### Post by varunendra on 2014-08-19
The ndiswrapper thing is our last resort and AR9285 certainly doesn't need that.

Please completely purge ndiswrapper and install network-manager, network-manager-gnome packages again.

To fix the problem, please set the encryption type in the router to pure WPA2-PSK with AES (CCMP). No WPA/WPA2 mixed mode, no TKIP. Reboot the router after saving the change.

If this doesn't fix the problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) . Please note that it is a different script than the one you posted output of. This one provides slightly more info that may be useful.

---

