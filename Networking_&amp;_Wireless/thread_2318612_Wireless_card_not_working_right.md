---
title: "Wireless card not working right"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by michael363 on 2016-03-27
Hello,

I have just installed ubuntu 14.04.4LTS on my desktop with a Qualcomm Atheros Wireless adapter (AR5416)
So far I never had problems with the internet on any of my machines, but this one just does not want to connect to my wireless network. Phones, TVs, other ubuntu machines, everything is running on the network, just my desktop refuses to work, so I think it is a problem with the drivers.

Any ideas what is wrong? If you need me to post any output from commands, please keep it to the minimum so I don't have to copy that much by hand :D

All help is greatly appreciated.

Cheers,
Michael

---

### Post by jeremy31 on 2016-03-27
Atheros wifi in Linux absolutely hates WEP/TKIP encryption, if you can change encryption change it to WPA2-AES

---

### Post by michael363 on 2016-03-27
AFAIK the network is WPA2. In the Wi-Fi Security settings I set WPA & WPA2 Personal.
Just found this tutorial: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5890620#post5890620](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5890620#post5890620)
Will this work?
Also, how am I supposed to download without network access? Can I download a tarball or something on my laptop, put it on a USB and then install from the USB?

---

### Post by jeremy31 on 2016-03-27
Do not download that!!  Check ```
iwlist scan | egrep -i 'ssid|cipher'
``` and see if the results below your wireless access point says CCMP or a mix of TKIP and CCMP

---

### Post by michael363 on 2016-03-27
Alright, so running this command gave me
eth0:  Interface doesn't support scanning
lo: Interface doesn't support scanning

When I tried to connect to my network again, the output of lo changed to
```

lo: Interface doesn't support scanning
     ESSID:""
     some stuff
     ESSID:"My wireless"
     Group Cipher: TKIP
     Pairwise Ciphers (2) : TKIP CCMP
     Group Cipher: TKIP
     Pairwise Ciphers (2) : TKIP CCMP

```
but running it another time, my wireless does not appear again.

EDIT:
I'm also confused as to the act that my wireless appears in lo instead of wlan0. When I run iwconfig, I see wlan0 with some information and lo says there is no wireless extensions.

---

### Post by jeremy31 on 2016-03-27
I would change the name of the access point to something with no spaces and definitely find a way to remove TKIP from those results.  Do not use a hidden ESSID as a way to make it more secure, it is better to broadcast

---

### Post by michael363 on 2016-03-27
1. The wireles has no spaces, the actual name is "Home_Wifi"

2. The network is not hidden

3. How do I remove TKIP?

Thanks for the help so far!

---

### Post by jeremy31 on 2016-03-27
> **michael363 said:**
> 1. The wireles has no spaces, the actual name is "Home_Wifi"

2. The network is not hidden

3. How do I remove TKIP?

Thanks for the help so far!

That answer depends on your wifi router, the encryption might be called WPA2-PSK, WPA2 only, WPA2-AES and TKIP could be hidden behind backwards compatibility or similar

---

### Post by michael363 on 2016-03-27
I have an xfinity router, I'll go see what of the options you stated are active on there and try to find and disable TKIP, give me a few minutes.

Alright, found the setting, changed it to WPA2-PSK (AES).

However, I still don't get a connection :(

Now the output is 
ESSID: "Home_Wifi"
      Group Cipher: CCMP
      Pariwise Ciphers (1): CCMP

---

### Post by jeremy31 on 2016-03-28
Is the laptop on a MAC blacklist on the router?  Do you have a USB thumb drive that you can copy files with?

---

### Post by michael363 on 2016-03-28
The router has nothing blacklisted. I have a USB drive that I can copy stuff with.

Also, after a reboot, the WiFi now connects, but disconnects after a short time. Running the Additional Drivers found drivers for the graphics card but not for the wireless.

---

