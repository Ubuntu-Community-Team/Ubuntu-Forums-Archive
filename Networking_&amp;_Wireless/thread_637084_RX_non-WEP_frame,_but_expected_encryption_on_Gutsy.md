---
title: "RX non-WEP frame, but expected encryption on Gutsy Gibbon with DWL-G630"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by dandubois on 2007-12-10
Hi,

I am using a D-Link DWL-G630 which connects to my WPA network successfully. However, every second I get the following message in /var/log/syslog:

---
Dec 10 20:01:00 dell kernel: [10147.775722] wlan0: RX non-WEP frame, but expected encryption
---

My /etc/network/interfaces file is configured as follows:

---
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-proto WPA
wpa-key-mgmt WPA-PSK
wpa-pairwise TKIP
wpa-ssid MYSSID
wpa-psk mypsk

---

Can anyone give me more insight into what is going on and how I can stop the kernel complaining?

Thanks,
Dan

---

### Post by dandubois on 2007-12-19
Some more information:

My router is a Netgear WPN824 and I have tried changing it to use WEP, WPA and WPA2 with the same "RX non-WEP frame, but expected encryption" results.

I would be grateful for any ideas or pointers!

Thanks,
Dan

---

### Post by lookitseman on 2008-03-18
You didn't by chance figure this out did you?

I've got a WPN824 as well with the exact same issue, and I'm trying to get this figured out at [this thread]("http://ubuntuforums.org/showthread.php?t=693099") over yonder.

---

### Post by miles_lane on 2008-04-13
Here is a patch from one of the wireless developers:

"Some people are getting this message a lot, and we have traced it to
broken access points that much too often send completely empty frames
(all bytes zeroed, which they shouldn't do at all.)"

"Since we cannot do anything about such frames in any case except the
special case where we're debugging an AP, just remove the message."

Signed-off-by: Johannes Berg <johannes@sipsolutions.net>
---
2.6.25 or -stable candidate.

 net/mac80211/rx.c |    7 ++-----
 1 file changed, 2 insertions(+), 5 deletions(-)

--- everything.orig/net/mac80211/rx.c   2008-04-13 10:07:47.000000000 +0200
+++ everything/net/mac80211/rx.c        2008-04-13 10:09:50.000000000 +0200
@@ -1078,12 +1078,9 @@ ieee80211_drop_unencrypted(struct ieee80
       if (unlikely(!(rx->fc & IEEE80211_FCTL_PROTECTED) &&
                    (rx->fc & IEEE80211_FCTL_FTYPE) == IEEE80211_FTYPE_DATA &&
                    (rx->fc & IEEE80211_FCTL_STYPE) != IEEE80211_STYPE_NULLFUNC &&
-                    (rx->key || rx->sdata->drop_unencrypted))) {
-               if (net_ratelimit())
-                       printk(KERN_DEBUG "%s: RX non-WEP frame, but expected "
-                              "encryption\n", rx->dev->name);
+                    (rx->key || rx->sdata->drop_unencrypted)))
               return -EACCES;
-       }
+
       return 0;
 }

---

### Post by lookitseman on 2008-04-15
thank you miles!

Since I do claim to use Linux, I should probably figure out how to compile code that I didn't write from the source.  No better time than the present I guess.

Thank you again!

---

