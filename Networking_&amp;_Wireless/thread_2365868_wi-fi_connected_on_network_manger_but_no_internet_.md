---
title: "wi-fi connected on network manger but no internet  on ubuntu 16.04 lts"
date: 2017-07-11
forum: Networking &amp; Wireless
---

### Post by aliole4731 on 2017-07-11
The network manager shows that I'm connected to the wi-fi but when I open any website it says there is no internet connection.This usually happens when I stop browsing the Internet for some time. The same wi-fi connection works fine on other devices.I have to reboot my HP laptopt get the Internet working again.

---

### Post by BenginM on 2017-07-11
[FONT=Courier New] Salutations!
 
is this a home WLAN network or some coffee shop / university !

what is the ipv4 & ipv6 settings in network manger ... is it set to manual or automatic (DHCP) !

What's the outout of

$ ifconfig -a

and 

$ sudo cat /etc/network/interfaces

[/FONT]

---

### Post by aliole4731 on 2017-07-12
hello.
Mine is a home WLAN network.I'm sorry I don't know if my ip4 and ip6 are manual or not.

---

### Post by BenginM on 2017-07-12
[FONT=Courier New]   Ok, Go to system settings -> Network -> WiFi , click the configuration icon in front of your wifi ESSID, in the new window at the left select IPv4 .

## am unable to extract your attachment zip files,they might be corrupted .. could you compress them into tar.xz, or tar.gz with no spaces within the names!

Also, please run the wierless info scrip from [URL="https://ubuntuforums.org/showthread.php?t=370108"]https://ubuntuforums.org/showthread.php?t=370108
[/URL]
and paste the whole result here using the code tag , like so:

[PHP]

```


Report from: 13 Jul 2017 13:27 CEST +0200

Booted last: 13 Jul 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################


```

[/PHP]


[/FONT]

---

