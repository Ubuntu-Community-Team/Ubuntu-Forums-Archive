---
title: "Ubuntu 21.04 wifi repeatedly disconnects, stuck in a cycle"
date: 2021-05-09
forum: Networking &amp; Wireless
---

### Post by notfossa on 2021-05-09
Here is my wireless-info: [URL="https://paste.ubuntu.com/p/vZmfsqbFVw/"]https://paste.ubuntu.com/p/vZmfsqbFVw/
[/URL]I recently replaced Manjaro with Ubuntu 21.04 on my laptop. I am  trying to connect to a wifi network that used to give me no trouble, and  it looks like wpa_supplicant is repeatedly connecting and  disconnecting. If I have my wifi on and listen with journalctl -f, I get  something like the following:
```

May 08 23:32:52 wpa_supplicant[651]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD 
May 08 23:32:52 NetworkManager[610]: <info>  [1620534772.6130]  device (wlo1): supplicant interface state: completed -> disconnected 
May 08 23:32:53 NetworkManager[610]: <info>  [1620534773.2020]  device (wlo1): supplicant interface state: disconnected -> scanning 
May 08 23:32:54 wpa_supplicant[651]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN 
May 08 23:32:56 wpa_supplicant[651]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN 
May 08 23:32:57 wpa_supplicant[651]: wlo1: SME: Trying to authenticate  with <MAC 'Swiftel4985' [AN18]> (SSID='Swiftel4985' freq=2412 MHz)  
May 08 23:32:57 kernel: wlo1: authenticate with <MAC 'Swiftel4985' [AN18]> 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.6922]  device (wlo1): supplicant interface state: scanning -> authenticating  
May 08 23:32:57 kernel: wlo1: send auth to <MAC 'Swiftel4985' [AN18]> (try 1/3) 
May 08 23:32:57 kernel: wlo1: authenticated 
May 08 23:32:57 wpa_supplicant[651]: wlo1: Trying to associate with  <MAC 'Swiftel4985' [AN18]> (SSID='Swiftel4985' freq=2412 MHz) 
May 08 23:32:57 kernel: rtw_8821ce 0000:01:00.0 wlo1: disabling HT/VHT/HE as WMM/QoS is not supported by the AP 
May 08 23:32:57 kernel: wlo1: associate with <MAC 'Swiftel4985' [AN18]> (try 1/3) 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.6988]  device (wlo1): supplicant interface state: authenticating ->  associating 
May 08 23:32:57 wpa_supplicant[651]: wlo1: Associated with <MAC 'Swiftel4985' [AN18]> 
May 08 23:32:57 wpa_supplicant[651]: wlo1: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0 
May 08 23:32:57 kernel: wlo1: RX AssocResp from <MAC 'Swiftel4985' [AN18]> (capab=0x11 status=0 aid=9) 
May 08 23:32:57 kernel: rtw_8821ce 0000:01:00.0: sta <MAC 'Swiftel4985' [AN18]> joined with macid 0 
May 08 23:32:57 kernel: wlo1: associated 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7082]  device (wlo1): supplicant interface state: associating -> associated 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7083] device (wlo1): DHCPv6 lease renewal requested 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7083] dhcp6 (wlo1): canceled DHCP transaction 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7083] dhcp6 (wlo1): state changed unknown -> done 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7087]  dhcp6 (wlo1): activation: beginning transaction (timeout in 45 seconds) 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7138]  device (wlo1): supplicant interface state: associated ->  4way_handshake 
May 08 23:32:57 wpa_supplicant[651]: wlo1: WPA: Key negotiation  completed with <MAC 'Swiftel4985' [AN18]> [PTK=CCMP GTK=CCMP] 
May 08 23:32:57 wpa_supplicant[651]: wlo1: CTRL-EVENT-CONNECTED -  Connection to <MAC 'Swiftel4985' [AN18]> completed [id=0 id_str=] 
May 08 23:32:57 NetworkManager[610]: <info>  [1620534777.7265]  device (wlo1): supplicant interface state: 4way_handshake ->  completed 
May 08 23:33:00 wpa_supplicant[651]: wlo1: CTRL-EVENT-BEACON-LOSS 
May 08 23:33:00 wpa_supplicant[651]: wlo1: CTRL-EVENT-DISCONNECTED  bssid=<MAC 'Swiftel4985' [AN18]> reason=4 locally_generated=1 
May 08 23:33:00 kernel: rtw_8821ce 0000:01:00.0: sta <MAC 'Swiftel4985' [AN18]> with macid 0 left 
May 08 23:33:00 wpa_supplicant[651]: wlo1: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD

```
It repeats indefinitely like this. What can I do to stay connected?

---

### Post by chili555 on 2021-05-09
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

   ```
 sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```
Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

