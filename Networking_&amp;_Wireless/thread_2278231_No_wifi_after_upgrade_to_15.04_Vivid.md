---
title: "No wifi after upgrade to 15.04 Vivid"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by jmkowske on 2015-05-14
Hi folks,

My wifi stopped working after upgrading from 14.10 to 15.04. Not sure what is going on. I've attached the results of the wireless script. Syslog shows a number of attempts and failure with:

```
May 14 17:07:18 terra kernel: [ 2192.368900] wlan0: authentication with c4:04:... be timed out
May 14 17:07:18 terra wpa_supplicant[940]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="gittybitty" auth_failures=1 duration=10
May 14 17:07:18 terra NetworkManager[834]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

```

What else is needed for troubleshooting? I've tried two different wifi networks. One with security and one without. I've also tried deleting and re-adding them... same problem.

---

### Post by actionmystique on 2015-05-15
There's clearly a WiFi problem with 15.04. This [**thread**]("http://ubuntuforums.org/showthread.php?t=2275970") might give you a workaround.

---

### Post by jmkowske on 2015-05-15
I found the solution to my problem in the System76 forum. Not sure if this is specific to their laptops or not:

[http://ubuntuforums.org/showthread.php?t=2275442](http://ubuntuforums.org/showthread.php?t=2275442)

---

