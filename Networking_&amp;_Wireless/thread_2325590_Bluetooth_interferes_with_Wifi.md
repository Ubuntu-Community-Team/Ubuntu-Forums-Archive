---
title: "Bluetooth interferes with Wifi"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by MoebusNet on 2016-05-23
Using Chrome, streaming from Netflix via my iPhone 6S Plus to my System76 Serval Pro 7: If audio output is analog stereo to my notebook speakers, WiFi speed stays at a reasonable level (non-HD) and the movie plays on. If however I use Bluetooth to stream to my headset, WiFi speed slows to a crawl then eventually to a stop. Disabling Bluetooth seems to remedy the situation; problem is speaker volume is so low as to be barely audible with everything turned to max. Bluetooth volume to headset is fine. Bluetooth in Ubuntu is currently subject to Bug #128003 which just added xenial to its list of affected versions. That's one of the reasons I'm still running 14.04.

Any suggestions? Or is this a case of needing to wait until a bug fix for Bluetooth (hopefully) fixes the WiFi issue? I haven't read much recently of Bluetooth affecting WiFi.

---

### Post by jeremy31 on 2016-05-23
You could try disabling the bluetooth coexistence parameter in iwlwifi to see if it makes an improvement
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=N
```

For some reason I do not see any bluetooth device present in the wireless script results

---

### Post by MoebusNet on 2016-05-24
@jeremy31 - You're right; I had disconnected Bluetooth to have WiFi connectivity. Here is the script results with Bluetooth & WiFi dropping in & out while streaming Netflix as before:

---

### Post by MoebusNet on 2016-05-24
BTW, changing the bluetooth coexistence parameter to 'N' immediately killed WiFi, only way I could get it back was to reboot. Did the commands make bluetooth coexistence 'N' permanent, or just for the session?

---

### Post by jeremy31 on 2016-05-24
That command should only be for the session.  You may want to put wifi on a different channel and see if one works better than others.  I have my wifi on channel 6

---

### Post by MoebusNet on 2016-05-24
Thanks, I'll try to find out if my iPhone can manually set the Hotspot channel.

---

