---
title: "Failed to fetch"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by Vasilen on 2015-11-17
Hi , first of all let me say I am new to Linux and Ubuntu.Now - I have installed Ubuntu server 14.04  but  I cannot seem to install my desktop . So when I try "sudo apt-get install ubuntu-desktop/xinit/etc." I get a series of errors "Failed to fetch [http://bg.archive.Ubuntu.com/ubuntu/pool/main/x//server](http://bg.archive.Ubuntu.com/ubuntu/pool/main/x//server)......
I thought it is from the Internet - I have an intent of using WiFi for the moment so I checked my adaptor and if it has a driver installed - Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe ........driver in use : rt2800pci . iwconfig shows me next to wlan0 text like this (I'll skip the first row) "Mode:Managed Access Point:NotAssociated Tx-Power=20 dBm" , it says that Encryption key is off and Power Management as well.....when run "ifconfig wlan0 up" On root does nothing and on my account says "Operation not permitted". 

So thank you for reading .If you have anuy questions towards a me - shoot .

Regards

---

### Post by Vasilen on 2015-11-18
Bump

---

### Post by QIII on 2015-11-18
Hello!

So far as I am aware, there is no package by that name.

Although it is not generally a particularly good idea to add a desktop environment to a server, we'll set that aside for the moment and help you do what you want to do.

But first, would you please use the terminal to attempt the command  

```
sudo apt-get update
```

and post the results back here?

Please use code tags to enclose the results of the command:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by howefield on 2015-11-18
It is best if you post the exact commands and output between code tags for the benefit of anyone wanting to help you.

Is your internet connection working, eg, can you ping google.com ?

```
ping 8.8.8.8
```

---

### Post by Vasilen on 2015-11-18
Hi,sorry for that I will have it in mins for future , thank you!
Now when I run sudo apt-get update I get series of errors like this: 
```
Err http://bg.archive.ubuntu.com trusty-security InRelease
```
After those , there is series of errors like this one:
```
W: Failed to fetch http://bg.archive.ubuntu.com/Ubuntu/costs/trusty/InRelease
```
Ping 8.8.8.8 resolves in 
```
connect: Network is unreachable
```

---

### Post by howefield on 2015-11-18
Looks like you have no internet connection, have you configured /etc/network/interfaces with your network details ?

Incidentally, if this machines primary purpose is that of a server, there are better (lighter and less resource hungry) desktops than ubuntu-desktop to consider. Just saying.

---

### Post by Vasilen on 2015-11-18
I have tried 4-5 different types of desktop packages but it just  cannot  download them (the same error "cannot fetch").
I haven't tried configuring for the simple reason I don't know how to do it from the command line.If you could tell me I will appreciate it much!

Okey so I've edited my /etc/network/interfaces - I'm using dhcp.Now when I run iwconfig for wlan0 
```
IEE 802.11bgn ESSID:"_chery"
Mode:Managed Access Point : Not associated Tx-power=20 dBm 
Encryption key:off 
Power Management :off
``` 
_Chery is my WiFi connection , the one I wanted to connect to.When I run lshw -class network it gives me
```
*-network
description: Wireless interface
product: RT5390 Wireless 802.11n 1T/1R PCIe
```

But when I ping 8.8.8.8 
```
connect: Network is unreachable
```

When I try pinging 192.168.1.1 (I'm pretty sure that's my default gateway) I get the same as above.

---

### Post by QIII on 2015-11-18
*Moved to **Networking & Wireless***

---

### Post by Vasilen on 2015-11-18
I have solved the problem.I will post what i did just in case someone needs it , like me.
So - fistly i delete everything i had written in my /etc/network/interfaces as it slowed down when i rebooted the system.I left only 
```
auto lo
iface lo inet loopback 
```
 So once i had made sure 
```
sudo ifconfig wlan0 up
```
Then checked if it had connected something 
```
sudo iwconfig wlan0
```
It hadn't (and it's normal) so i connected it using wpa_supplicant
```
sudo su 
 wpa_passphrase SSID PASSPHRASE >> /etc/wpa_supplicant.conf
exit
```
Then
```
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf 
```
It gave me hard time "unsupported server" here so i just missed the "-D wext" and it auto-detected my driver.
So it connected , then 
```
sudo dhclient wlan0
```
This gave me my IP - and that is it. Thanks to all who helped me!

---

