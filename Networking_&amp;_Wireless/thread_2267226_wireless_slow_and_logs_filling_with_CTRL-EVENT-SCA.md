---
title: "wireless slow and logs filling with: CTRL-EVENT-SCAN-STARTED"
date: 2015-02-28
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2015-02-28
I'm trying to track down some wireless problems.  The connection is often dreadfully slow.  I suspect the problem lies with the access point but here is what I get from the client logs:

```

# grep supplicant /var/log/syslog      
Feb 28 11:35:16 gazelle9 wpa_supplicant[869]: message repeated 30 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Feb 28 11:36:43 gazelle9 wpa_supplicant[869]: wlan0: WPA: Group rekeying completed with xx:xx:xx:xx:xx:xx [GTK=TKIP]
Feb 28 11:37:16 gazelle9 wpa_supplicant[869]: wlan0: CTRL-EVENT-SCAN-STARTED 
Feb 28 12:35:16 gazelle9 wpa_supplicant[869]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Feb 28 12:36:44 gazelle9 wpa_supplicant[869]: wlan0: WPA: Group rekeying completed with xx:xx:xx:xx:xx:xx [GTK=TKIP]
Feb 28 12:36:44 gazelle9 wpa_supplicant[869]: wlan0: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=16
Feb 28 12:36:44 gazelle9 NetworkManager[833]: <info> (wlan0): supplicant interface state: completed -> disconnected
Feb 28 12:36:44 gazelle9 wpa_supplicant[869]: wlan0: CTRL-EVENT-SCAN-STARTED 
Feb 28 12:36:44 gazelle9 NetworkManager[833]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Feb 28 12:36:48 gazelle9 wpa_supplicant[869]: wlan0: SME: Trying to authenticate with xx:xx:xx:xx:xx:xx (SSID='xxxxx' freq=2462 MHz)
Feb 28 12:36:48 gazelle9 wpa_supplicant[869]: wlan0: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxx' freq=2462 MHz)
Feb 28 12:36:48 gazelle9 NetworkManager[833]: <info> (wlan0): supplicant interface state: scanning -> associating
Feb 28 12:36:48 gazelle9 wpa_supplicant[869]: wlan0: Associated with xx:xx:xx:xx:xx:xx
Feb 28 12:36:48 gazelle9 wpa_supplicant[869]: wlan0: WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=TKIP]
Feb 28 12:36:48 gazelle9 wpa_supplicant[869]: wlan0: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed [id=0 id_str=]
Feb 28 12:36:48 gazelle9 NetworkManager[833]: <info> (wlan0): supplicant interface state: associating -> completed
Feb 28 12:37:16 gazelle9 wpa_supplicant[869]: wlan0: CTRL-EVENT-SCAN-STARTED 

```

iwconfig shows a strong, clear signal

```

wlan0     IEEE 802.11abgn  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

```

However, throughput seems to be 10% of what it was a while back.  What should I be looking at?

---

### Post by SeijiSensei on 2015-02-28
For the "CTRL-EVENT-SCAN-STARTED" syslog entries, I suggest reading this bug report:  [https://bugs.launchpad.net/ubuntu/+source/wpa/+bug/1323089](https://bugs.launchpad.net/ubuntu/+source/wpa/+bug/1323089).  There are a couple of suggestions for turning that off.

Other people in that thread report connectivity issues as well as the syslog spamming.  I've only encountered the latter problem myself.

I presume you've done the obvious things like rebooting the router/access point?

---

### Post by Lars Noodén on 2015-02-28
Thanks.  I've subscribed to the bug report.  

It's one of those troubling intermittent problems, I'm getting 26,3KB/s but was getting almost full speed earlier today.  It's been going on since late December and the access point has been through many reboots and even a few system upgrades since then to no avail.

Edit: if it's any help the wireless drops once or twice a day, always at the same time of day, down to the minute.  But if I reboot the netbook, then that time changes.

---

