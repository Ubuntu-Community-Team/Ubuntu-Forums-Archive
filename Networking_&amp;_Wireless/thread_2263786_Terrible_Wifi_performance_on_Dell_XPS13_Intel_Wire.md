---
title: "Terrible Wifi performance on Dell XPS13 Intel Wireless-AC 7260"
date: 2015-02-03
forum: Networking &amp; Wireless
---

### Post by ubu_Leno on 2015-02-03
Hello Ubuntu Forms.

I have a Dell XPS 13 (9333) with an Intel Wireless-AC 7260 5G running Ubuntu 14.0.1.   I am getting terrible internet connectivity off the wifi on any network I connect to (mostly 2.4Ghz G).

What I have noticed.   On a fresh install of Ubuntu 14.0.1 before doing any upgrades the network connection is rock solid, no dropped packets and low and consistent ping times.   As soon as I do all the necessary upgrades, the wifi connection becomes terrible, dropping packets and ping times going anywhere from single digit ms all the way up into the high (800-900)ms

I have also tried other suggestions namely:

vi /etc/pm/power.d/wireless
```

#!/bin/sh
/sbin/iwconfig wlan0 power off

```

```

chmod 755 /etc/pm/power.d/wireless

```

```

echo "options iwlwifi 11ac_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

```

```

sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo reboot

```

Following the reboot there is little to no improvement, still seeing packetloss and high ping times

Any help would be appreciated

I include 3 outputs from the wifi info gathering script:

- right after a fresh install: [http://pastebin.com/wnNEz6zr](http://pastebin.com/wnNEz6zr)
- after apt-get dist-upgrade:  [http://pastebin.com/xE4BzTLM](http://pastebin.com/xE4BzTLM)
- after the above changes to iwlwifi.conf and script creation: [http://pastebin.com/6z8KdwjC](http://pastebin.com/6z8KdwjC)

I have changed the name of the SSIDs and MAC addresss in the first pastebin link.

---

### Post by jeremy31 on 2015-02-03
You may want to edit /etc/modprobe.d/iwlwifi.conf to change parameters ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` and change ```
11n_disable=1
``` to ```
11n_disable=8
``` and delete the 11ac_disable line as it isn't valid, save, exit reboot

And what country are you in?  It is so that regulatory info can be set as ```
iw reg get
``` shows a default country code of 00

---

### Post by ubu_Leno on 2015-02-03
Hi jeremy31

What does the "8" option do?   

Country depends on the day of the week as I travel world wide, though looking at other laptops I have all are set to "00" as default

---

### Post by jeremy31 on 2015-02-03
11n_disable=8 enables agg tx, it should increase speed and I have to have it on my intel card to connect to networks that are wireless n only

---

### Post by ubu_Leno on 2015-02-03
Hmmm it looks to have stopped the packet loss though ping times are still bouncing around the place. A little unsure of how this is relevant change if I'm only connecting to g networks

---

### Post by jeremy31 on 2015-02-04
I wonder if it is a firmware issue ```
sudo cp /lib/firmware/iwlwifi-7260-8.ucode /lib/firmware/iwlwifi-7260-8.ucode.bak  && sudo rm /lib/firmware/iwlwifi-7260-8.ucode
```
Reboot and see if it is better, if it gets worse or doesn't want to work at all reverse the above with ```
sudo cp /lib/firmware/iwlwifi-7260-8.ucode.bak /lib/firmware/iwlwifi-7260-8.ucode
```

I can't know for sure what firmware was loaded before any updates as the script was cut short.  An option to the above commands would be to reboot and hold the shift key down until the grub menu appears, then select previous versions or advanced options and select the option with the 3.13.0-24 kernel and see if it works the same or better

---

### Post by ubu_Leno on 2015-02-17
> **jeremy31 said:**
> I wonder if it is a firmware issue ```
sudo cp /lib/firmware/iwlwifi-7260-8.ucode /lib/firmware/iwlwifi-7260-8.ucode.bak  && sudo rm /lib/firmware/iwlwifi-7260-8.ucode
```
Reboot and see if it is better, if it gets worse or doesn't want to work at all reverse the above with ```
sudo cp /lib/firmware/iwlwifi-7260-8.ucode.bak /lib/firmware/iwlwifi-7260-8.ucode
```


I did that and wifi just fails, it does not use the older 7260-7 at all and detects no wifi device.

I did install the LTSEnablementStack for 14.04 (bringing it to kernel 3.16.0-30 and firmware iwlwifi-7260-9.ucode) and this produced some new results. far less packetloss but now instead we get random disconnects after a few hours of use

```
Feb 16 08:19:28 xps13 kernel: [70677.523869] wlan0: deauthenticated from 00:22:22:22:22:22 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Feb 16 08:19:28 xps13 wpa_supplicant[1052]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:22:22:22:22:22 reason=7
Feb 16 08:19:28 xps13 NetworkManager[907]: <warn> Connection disconnected (reason 7)
Feb 16 08:19:28 xps13 kernel: [70677.544012] cfg80211: Calling CRDA to update world regulatory domain
Feb 16 08:19:28 xps13 kernel: [70677.546363] cfg80211: World regulatory domain updated:
Feb 16 08:19:28 xps13 kernel: [70677.546366] cfg80211:  DFS Master region: unset
Feb 16 08:19:28 xps13 kernel: [70677.546367] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 16 08:19:28 xps13 kernel: [70677.546369] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Feb 16 08:19:28 xps13 kernel: [70677.546371] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Feb 16 08:19:28 xps13 kernel: [70677.546372] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Feb 16 08:19:28 xps13 kernel: [70677.546373] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Feb 16 08:19:28 xps13 kernel: [70677.546375] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Feb 16 08:19:28 xps13 NetworkManager[907]: <info> (wlan0): supplicant interface state: completed -> disconnected
Feb 16 08:19:28 xps13 NetworkManager[907]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Feb 16 08:19:44 xps13 NetworkManager[907]: <warn> (wlan0): link timed out.
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> NetworkManager state is now DISCONNECTED
Feb 16 08:19:44 xps13 NetworkManager[907]: <warn> Activation (wlan0) failed for connection 'mywifi'
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 16 08:19:44 xps13 dbus[544]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 16 08:19:44 xps13 dbus[544]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1773
Feb 16 08:19:44 xps13 avahi-daemon[666]: Withdrawing address record for 192.168.1.222 on wlan0.
Feb 16 08:19:44 xps13 avahi-daemon[666]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.222.
Feb 16 08:19:44 xps13 avahi-daemon[666]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb 16 08:19:44 xps13 NetworkManager[907]: <warn> DNS: plugin dnsmasq update failed
Feb 16 08:19:44 xps13 NetworkManager[907]: <info> Removing DNS information from /sbin/resolvconf
Feb 16 08:19:44 xps13 dnsmasq[1776]: setting upstream servers from DBus
Feb 16 08:19:44 xps13 NetworkManager[907]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
```

To get wifi back up and running I have to either reboot or toggle the hardware switch.


[http://pastebin.com/phep89hZ](http://pastebin.com/phep89hZ) - output of wifi script after WiFi drops

[http://pastebin.com/1AB7v5Ks](http://pastebin.com/1AB7v5Ks) - output of wifi script with wifi working on 3.16.0-30 kernel

---

### Post by jeremy31 on 2015-02-17
Can you change your router to channel 11 or 13, it is currently on channel 6 along with quite a few others

---

### Post by ubu_Leno on 2015-02-17
I will try shortly and report back but it is the only network I have control of out of many that the laptop connects to. airports, hotels, cafes, other offices, e.t.c.

---

### Post by tgalati4 on 2015-02-17
There are several switches for that wifi module:

```
modinfo iwlwifi
```

I would play with each one and take notes of the performance differences.

> 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


Are you using any bluetooth devices?  If so, turn off bluetooth on the computer and see if the network connection is any better.

---

### Post by ubu_Leno on 2015-03-08
What fixed this in the end was a fresh install with 14.04.2.  Not sure what differs from the LTSenablementstack which I also tried and the fresh install

---

