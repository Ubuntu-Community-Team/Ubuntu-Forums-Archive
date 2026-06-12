---
title: "Wireless network setup issues"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by Arcet on 2007-01-12
Hi,

I'm trying to set up my laptop(Acer aspire 1801) for wireless internet.

lspci says:

0a:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
0a:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

I installed ndiswrapper and the corresponding driver using this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

iwconfig gives this output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WRBUR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:06:25:DF:8C:BD   
          Bit Rate:11 Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-24 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The gnome-networking applet says the signal strength is 100%, packets are being sent, but none received.

When i try to set up the WEP password, i get an error message:

```

$ sudo iwconfig wlan0 key <my 10-character wep key>
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

I really have no idea of what to do next... anyone an idea???

---

### Post by chettyk on 2007-01-12
Mercifully, all Ubuntu releases have recognised my laptop's wireless card on installation and configured it correctly. So I have not had to use ndiswrapper.

But I have a suggestion. Do you want to consider disabling WEP encryption on the wireless access point that you are using and then see if your laptop is able to link up correctly without any WEP key required?

---

### Post by joneberger on 2007-01-12
i agree with chettyk.  completely unsecure your router (only for now!) to see if you can connect otherwise.  then begin adding securities (MAC filter, WEP, etc.).  you might also consider trying to set the WEP key in your interfaces file

---

### Post by Arcet on 2007-01-12
EDIT: IT WORKS !!!

Now, where do I find the interface file. I don't want to leave the network unsecure for long, My neighbours tend to use my network...

---

### Post by Vox754 on 2007-02-13
Look here
[http://ubuntuforums.org/showthread.php?t=324967](http://ubuntuforums.org/showthread.php?t=324967)

[http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=339802&highlight=inprocomm)

---

### Post by HilliBilly on 2007-02-13
try something like this if your key is in ascii

sudo iwconfig wlan0 key s:XXXXXXXXXXXXX enc on
sudo dhclient wlan0

---

