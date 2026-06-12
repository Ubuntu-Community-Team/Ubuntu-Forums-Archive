---
title: "Wireless breaks down on printing"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by kaiben on 2013-10-22
I Use Kubuntu 12.04 (and previous versions) for a long time now on my netbook Asus Eee PC 901. Printing over wireless worked fine the whole time. The printer is connected to my FritzBox router, which provides it as a network printer.

Since recently the wireless connections breaks always down while printing. The first messages in the system log are than:

20.10.2013 11:59:39    mini    kernel    [  694.504141] ieee80211 phy0: wlan0: No  probe response from AP 9c:c7:a6:07:7c:7d after 500ms, disconnecting.
20.10.2013 11:59:39    mini    wpa_supplicant[854]    CTRL-EVENT-DISCONNECTED  bssid=9c:c7:a6:07:7c:7d reason=4 
20.10.2013 11:59:40    mini    kernel    [  694.901749] cfg80211: All devices are  disconnected, going to restore regulatory settings 
20.10.2013 11:59:40    mini    kernel    [  694.901766] cfg80211: Restoring  regulatory settings 
20.10.2013 11:59:40    mini    kernel    [  694.901779] cfg80211: Calling CRDA to  update world regulatory domain 
20.10.2013 11:59:40    mini    NetworkManager[764]    <info> (wlan0): supplicant  interface state: completed -> disconnected

Without printing, wireless works fine for hours. Printing works fine if directly connected via ethernet cable. It seems just to be this combination.

Any idea what suddenly cause this problem? Was there an update introducing this problem?

Many thanks in advance

---

