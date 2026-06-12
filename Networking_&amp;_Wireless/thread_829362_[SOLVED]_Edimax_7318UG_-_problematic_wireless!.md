---
title: "[SOLVED] Edimax 7318UG - problematic wireless!"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by geezerone on 2008-06-14
Please help!

I did manage to get my Edimax 7318UG working in Hardy with built-in drivers and was working perfectly after login with no password messages and quick connection to wireless AP.

However, I was trying (and still am) to get a networked Windows XP printer working and thought to try an ethernet cable instead - Wrong!!! Since then the wireless has been very problematic with connection and now drops/times out on connection with no warning.

Typical ping to my router would be

11 packets transmitted, 2 received, 81% packet loss, time 10001ms

and noticed that I am being reconnected to access point as seen in my dmesg o/p:

```
[  770.200064] wlan0: authenticated
[  770.200067] wlan0: associate with AP 00:14:6c:53:56:54
[  770.214803] wlan0: RX ReassocResp from 00:14:6c:53:56:54 (capab=0x431 status=0 aid=2)
[  770.214812] wlan0: associated
[  770.214819] wlan0: switched to short barker preamble (BSSID=00:14:6c:53:56:54)
[  888.652578] wlan0: RX deauthentication from 00:14:6c:53:56:54 (reason=7)
[  888.652586] wlan0: deauthenticated
[  889.650484] wlan0: authenticate with AP 00:14:6c:53:56:54
[  889.652035] wlan0: RX authentication from 00:14:6c:53:56:54 (alg=0 transaction=2 status=0)
[  889.652040] wlan0: authenticated
[  889.652043] wlan0: associate with AP 00:14:6c:53:56:54
[  889.671384] wlan0: RX ReassocResp from 00:14:6c:53:56:54 (capab=0x431 status=0 aid=2)
[  889.671393] wlan0: associated
[  889.671400] wlan0: switched to short barker preamble (BSSID=00:14:6c:53:56:54
```As I say this is driving me around the twist and isn't something I want to spend a whole lot of time on as already spent hours on it:(

Slowness down to being reassociated as shown here from iwconfig:

```
 Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:6C:53:56:54   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=68/100  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I have a 90% signal strength + and now getting this?!

---

### Post by geezerone on 2008-06-15
I can see networks but getting authenctication messages.

I looked at the Edimax site and no driver link for Linux on the main download area:

[http://www.edimax.com/en/support_detail.php?pd_id=3&pl1_id=1&pl2_id=44](http://www.edimax.com/en/support_detail.php?pd_id=3&pl1_id=1&pl2_id=44)

There was a 1.0.4 driver a little time ago.

---

### Post by geezerone on 2008-06-21
Removed network manager icon which I had added to panel in addition to nm-applet and now connects at login without any prompting.

---

