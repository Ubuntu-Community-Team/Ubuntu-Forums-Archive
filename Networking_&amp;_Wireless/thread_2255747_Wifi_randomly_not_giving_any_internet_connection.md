---
title: "Wifi randomly not giving any internet connection"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by eeeeee2 on 2014-12-07
I'm under xubuntu 14.10, and my wifi keeps losing connection randomly. 
After 1 hour or so of browsing, my internet connection will not work anymore, however, the wifi is still connected.
If I disconnect from the wifi and reconnect again, the connection works.
It seems that it is not happening on any of the other devices I use (Android Tablet Nexus 7, OS X) 

Here's the result of the `wireless_script` which I got using: `wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script`

The result can be found on pastebin: [http://pastebin.com/uwJjz0KP](http://pastebin.com/uwJjz0KP)

Here's the same file before the crash: [http://pastebin.com/uu5pmPcs](http://pastebin.com/uu5pmPcs)

They seem to be a small difference at the end:

```
[ 1305.693454] wlan0: deauthenticating from <MAC 'Freebox_A93360' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1307.362474] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1307.370149] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1307.437900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1311.034443] wlan0: authenticate with <MAC 'Freebox_A93360' [AC1]>
[ 1311.038127] wlan0: send auth to <MAC 'Freebox_A93360' [AC1]> (try 1/3)
[ 1311.040783] wlan0: authenticated
[ 1311.044134] wlan0: associate with <MAC 'Freebox_A93360' [AC1]> (try 1/3)
[ 1311.048631] wlan0: RX AssocResp from <MAC 'Freebox_A93360' [AC1]> (capab=0x411 status=0 aid=4)
[ 1311.068805] wlan0: associated
[ 1311.068842] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Any idea why this is happening and how I could solve it ?

Thanks in advance for your help

---

### Post by praseodym on 2014-12-07
Deactivate the N-mode, the queue and the power management:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi [COLOR="#FF0000"]#if there is an error here, reboot then[/COLOR]
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
```

---

