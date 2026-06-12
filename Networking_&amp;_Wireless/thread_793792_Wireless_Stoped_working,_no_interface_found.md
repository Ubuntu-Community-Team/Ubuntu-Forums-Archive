---
title: "Wireless Stoped working, no interface found"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by CleverJake on 2008-05-14
so, I had problems with my wifi card to begin with, but ndiswrapper seemed to solve all of that, but the other day, my wireless card seemed to just through a tantrum and leave


I go to the networkmanager, and try to type in my connection (wlan0) and hit configre, it returns 

the interface does not exist, check that it is typed correctly and it is supproted by your system

sudo ndiswrapper -l gives


```
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)
```

so the card is being seen by ndiswrapper

iwconfig gives

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

so i know that the card is being seen

**iwlist wlan0 scan** returns all the access points around me, so I know that its receiving signals

i try sudo iwconfig wlan essid (the ssid) key (the key) and..

```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```


any help would be greatly appreciated

---

### Post by chili555 on 2008-05-14
> "Set Encode" (8B2A) :This is Linux-speak for 'I don't like your key, young grasshopper.' Is this a WEP key? Is it Hex or ASCII? If it's ASCII, is it 5 or 13 characters and prepended with **s:**? If it's Hex, is it 10 or 26 characters?

Valid key lengths are 5 (ASCII) and 10 (Hex) for 64-bit, 13 (ASCII) and 26 (Hex) for 128-bit WEP encryption.

---

### Post by CleverJake on 2008-05-14
I believe its hex, its a 64 digit key though,
 wpa tkip

---

### Post by chili555 on 2008-05-14
The command *sudo iwconfig wlan0 key <ur_key>* is for WEP, not WPA. To configure WPA the manual method, please see: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by CleverJake on 2008-05-14
[IMG]http://blogsap.files.wordpress.com/2006/10/nbc_the_more_you_know.jpg[/IMG]


thanks mate

---

