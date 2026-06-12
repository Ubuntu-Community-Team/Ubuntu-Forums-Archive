---
title: "WiFI drops connection 1-10 seconds after authenticating to AP"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by smurphy_it on 2008-09-01
Good day.  Here is something I have been noticing as of later.  After I successfully connect to the AP, it suddenly drops the connection 1-10 seconds afterwords.

After two to three attempts it will finally maintain the connection.

Here is an exerpt from dmesg (hid the mac because I am nuts)

[ 1590.236628] wlan0: associated
[ 1590.375087] wlan0: no IPv6 routers present
[ 1591.080921] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=15)
[ 1591.080929] wlan0: deauthenticated
[ 1591.080943] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080949] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080954] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080959] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080963] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080968] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)[ 1591.080987] wlan0: authenticate with AP 00:01:02:03:04:05 (Mac address not disclosed)
[ 1591.083367] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.084130] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080973] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080977] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)
[ 1591.080982] wlan0: RX deauthentication from 00:01:02:03:04:05 (Mac address not disclosed) (reason=7)

Here is another tidbit I snaked from the kernel.log

wlan0: authentication frame received from 00:01:02:03:04:05 (Mac address not disclosed), but not in authenticate state - ignored
wlan0: RX ReassocResp from 00:01:02:03:04:05 (Mac address not disclosed) (capab=0x411 status=0 aid=1)


Anyone got any ideas, or would like more info ?

---

### Post by nicedude on 2008-09-01
Please post what model of wifi adapter you are using? This is probably a wifi driver error, but since this is a bunch of deauth messages are you resonably sure no one living nearby is a big jerk who would be sending deauth packets to kick you off your AP. I do it to my friends sometimes kiddin around but it is super simple to do :-)


Also try googling the error without your mac addresses and you will find many such posts on different forums but they are adapter specific problems so you will need to look for your adapter etc.

EDIT

snap I must be blind , I looked at your outputs again and it just jumped at me this time, this is a IPv6 error, your ubuntu is trying to use IPv6 and your router only supports IPv4 IP routing standard. So just look up how to set your wifi to use IPv4 instead of IPv6 and it will work.


Hope that helps

---

### Post by smurphy_it on 2008-09-01
Easy enough, I'll disable IPV6 in the hosts file.

Already done... Will look elsewhere.... See what the router config is.

---

### Post by nicedude on 2008-09-01
Heres a link to how to do it from these forums.

[http://ph.ubuntuforums.com/showthread.php?t=789357](http://ph.ubuntuforums.com/showthread.php?t=789357)


Goodluck

---

### Post by smurphy_it on 2008-09-01
NiceDude:  Thanks.  I forgot about displaying IPv6 that way.  On a new laptop, so some of the things I had off by default on my old lappy of course aren't done here.

---

