---
title: "Intermittent Wifi: Realtek RTL8188EE, Toshiba Satellite S55-A5295, Ubuntu 13.10"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by yisraell on 2014-01-06
I am having some very strange behavior with my wifi:

[LIST]
[*]On some wifi access points it connects and then intermittently looses internet access for a few minutes (i.e. it shows that it is still connected, but can't access the network at all) - sometimes it restores by itself, sometimes it        doesn't
[*]On other wifi access points (for example tethering to my phone), it almost never connects - but sometimes does - and then has the above behavior.
[*]The signal strength fluctuates greatly - even when right next to the router - sometimes high strength sometimes very low.
[*]When booting in Windows 8.1, wifi works fine - so it is not a hardware problem
[/LIST]

*Computer status and history:*
[LIST]
[*]Originally installed 13.04 (didn't have support for this wifi card) - got it to work with [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) (I don't remember it being intermittent then, but perhaps it was)
[*]Upgraded to 13.10 - continued to work (again - intermittently)
[*]I have now installed backports-3.12.2-1 and linux-firmware_1.119_all to make sure I have the latest of everything and am still seeing the same behavior.
[/LIST]

When it is trying (and failing) to connect to wifi I see this looping in syslog:
```
Jan  6 11:01:50 Satellite-S55-A kernel: [ 3034.156439] wlan0: authenticate with 84:00:d2:56:ca:bbJan  6 11:01:50 Satellite-S55-A wpa_supplicant[1188]: wlan0: SME: Trying to authenticate with 84:00:d2:56:ca:bb (SSID='ExperiaArc5' freq=2462 MHz)
Jan  6 11:01:50 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Jan  6 11:01:50 Satellite-S55-A kernel: [ 3034.175776] wlan0: direct probe to 84:00:d2:56:ca:bb (try 1/3)
Jan  6 11:01:50 Satellite-S55-A kernel: [ 3034.379594] wlan0: send auth to 84:00:d2:56:ca:bb (try 2/3)
Jan  6 11:01:51 Satellite-S55-A kernel: [ 3035.724665] wlan0: send auth to 84:00:d2:56:ca:bb (try 3/3)
Jan  6 11:01:52 Satellite-S55-A kernel: [ 3036.725490] wlan0: authentication with 84:00:d2:56:ca:bb timed out
Jan  6 11:01:52 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  6 11:01:53 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  6 11:01:54 Satellite-S55-A wpa_supplicant[1188]: wlan0: SME: Trying to authenticate with 84:00:d2:56:ca:bb (SSID='ExperiaArc5' freq=2462 MHz)
Jan  6 11:01:54 Satellite-S55-A kernel: [ 3038.091836] wlan0: authenticate with 84:00:d2:56:ca:bb
Jan  6 11:01:54 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  6 11:01:54 Satellite-S55-A kernel: [ 3038.101032] wlan0: direct probe to 84:00:d2:56:ca:bb (try 1/3)
Jan  6 11:01:54 Satellite-S55-A kernel: [ 3038.302861] wlan0: send auth to 84:00:d2:56:ca:bb (try 2/3)
Jan  6 11:01:55 Satellite-S55-A kernel: [ 3039.716090] wlan0: send auth to 84:00:d2:56:ca:bb (try 3/3)
Jan  6 11:01:56 Satellite-S55-A kernel: [ 3040.680916] wlan0: authentication with 84:00:d2:56:ca:bb timed out
Jan  6 11:01:56 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  6 11:01:57 Satellite-S55-A NetworkManager[953]: <info> (wlan0): supplicant interface state: disconnected -> scanning
```

I have attached the results of the wifi script for analysis: [ATTACH]249261[/ATTACH]

I saw a similar post [[http://askubuntu.com/questions/395393/wireless-not-working-on-toshiba-s55-a5294-rtl8188ee](http://askubuntu.com/questions/395393/wireless-not-working-on-toshiba-s55-a5294-rtl8188ee)] which suggested changing channels of your router - but that is not a good solution since often the router is not yours and you can't just change the channel.

Any help you give would be *greatly** appreciated*! I am wasting so much time on this! [CENTER][COLOR=#000000]](*,)[/COLOR][/CENTER]

---

### Post by skliarie on 2014-01-06
There are couple suggestions here: [http://askubuntu.com/questions/342637/wifi-connect-problem](http://askubuntu.com/questions/342637/wifi-connect-problem)

---

### Post by yisraell on 2014-01-06
Good link.

I do have linux TLP [ [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html) ] installed - but it seems that my power saving is already off - maybe there is something else taht that does that would cause my connection to be bad?

```
 $sudo iw wlan0 get power_save
Power save: off 
```

I don't think it's an ipv6 issue since (when it is not connecting at all) it isn't even getting to that stage...  perhaps the ipv6 may be related to the intermittent drop outs once it is connected...

other ideas?

---

### Post by yisraell on 2014-01-09
Does anybody have any other ideas on how to solve this?

It's strange - it will get better for a few days and connect fairly reliably, and then it will just refuse.  But I know it isn't a hardware issue, b/c I can still use it in windows even when linux flat out refuses.

Any gurus out there have any ideas?  The laptop is pretty useless without wifi....

---

