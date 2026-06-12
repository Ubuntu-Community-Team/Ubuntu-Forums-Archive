---
title: "Strange wireless problems with WUSB54GC"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by devosion on 2008-10-23
Im currently using Hardy and am using a WUSB54GC that is wonky all across the board lately. Before the last couple of updates to my system I was having no problem with my wireless card getting connected and staying connected. After an update about a month ago, I cant really nail which update it was now, my wireless connection would disconnect shortly after attempting to access the internet. When I viewed dmesg this would come up.

> phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19

After it dropping in and out several times it would eventually stabilize. Now after the latest batch of updates on the 18th it has become even more problematic. My internet connection will not work consistently. The connection will show active in the upper corner, but transfer rates will dip. Watching youtube videos used to be a smooth process, now I have to watch it load to a certain point, then take up to 30 seconds to download the next bit of the video. Viewing dmesg shows this.

> [29941.193301] wlan0: RX deauthentication from 00:1e:2a:70:89:b8 (reason=7)
[29941.193309] wlan0: deauthenticated
[29942.190484] wlan0: authenticate with AP 00:1e:2a:70:89:b8
[29942.192203] wlan0: RX authentication from 00:1e:2a:70:89:b8 (alg=0 transaction=2 status=0)
[29942.192209] wlan0: authenticated
[29942.192212] wlan0: associate with AP 00:1e:2a:70:89:b8
[29942.195159] wlan0: RX ReassocResp from 00:1e:2a:70:89:b8 (capab=0x411 status=0 aid=2)
[29942.195165] wlan0: associated
[29942.195171] wlan0: switched to short barker preamble (BSSID=00:1e:2a:70:89:b8)
[30036.323085] wlan0: switched to long barker preamble (BSSID=00:1e:2a:70:89:b8)
[30051.236324] wlan0: switched to short barker preamble (BSSID=00:1e:2a:70:89:b8)
[30455.321381] wlan0: switched to long barker preamble (BSSID=00:1e:2a:70:89:b8)
[30468.191673] wlan0: switched to short barker preamble (BSSID=00:1e:2a:70:89:b8)
[30634.892022] wlan0: switched to long barker preamble (BSSID=00:1e:2a:70:89:b8)
[30646.945070] wlan0: switched to short barker preamble (BSSID=00:1e:2a:70:89:b8

My wireless connection went from being excellent requiring no additional patches to being a shoddy mess. What can I do?

---

### Post by devosion on 2008-10-23
bump

---

### Post by devosion on 2008-10-24
bump again :(

---

