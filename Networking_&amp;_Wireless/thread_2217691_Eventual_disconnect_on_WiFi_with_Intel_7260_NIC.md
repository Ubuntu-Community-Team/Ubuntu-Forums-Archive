---
title: "Eventual disconnect on WiFi with Intel 7260 NIC"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by MarkFrancis905 on 2014-04-18
Hello all,

I having issues with disconnects after a while. I'm running Ubuntu 14.04 (same issues with 13.10, which I hoped would be fixed via the update).

I can connect to a WifF point fine, it will work for about 20-30 mins and then disconnect. The WiFi access point is no longer listed as available. I know it is because I have other connected devices (android phone).

Im not sure where to start, I have the "iwlwifi-7260-8.ucode" driver in /lib/firmware but I'm not sure where else to look to start troubleshooting.

All forum posts I can find don't describe my problem. I can work on WiFi fine for a set amount of time, then is drops. Any help would be great.

---

### Post by chili555 on 2014-04-18
Which firmware is actually being loaded?```
dmesg | grep iwl
```Also please show us:```
ls -al /lib/firmware | grep 7260
lspci -nn | grep 0280
```Thanks.

---

### Post by MarkFrancis905 on 2014-04-18
Thanks for your help, heres the output you have asked for:

```
mark@UbuntuLaptop:/root$ dmesg | grep iwl
[   12.256760] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[   12.256973] iwlwifi 0000:06:00.0: irq 52 for MSI/MSI-X
[   12.262778] iwlwifi 0000:06:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   12.320792] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   12.323103] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   12.323358] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   12.524644] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.626020] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   12.626273] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
```


```
mark@UbuntuLaptop:/root$ sudo ls -al /lib/firmware | grep 7260
-rw-r--r--  1 root root  679780 Mar  5 15:45 iwlwifi-7260-8.ucode
```


```
mark@UbuntuLaptop:/root$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
```

---

### Post by chili555 on 2014-04-18
It is, obviously, loading the only firmware you have:> iwlwifi 0000:06:00.0: loaded firmware version 22.24.[COLOR="#FF0000"]8[/COLOR].0 op_mode iwlmvmMysteriously, the driver thinks it wants -7:```
$ modinfo iwlwifi
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
firmware:       iwlwifi-7260[COLOR="#FF0000"]-7[/COLOR].ucode
srcversion:     1E6912E109D5A43B310FB34
<snip>
```That may be a typo in the driver code. It would be interesting to see what might happen if the -7 code were available. Would it load in preference to the -8? Would it be stable? Before we try that, here are some other things you might try. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

Is stability improved?

---

### Post by MarkFrancis905 on 2014-04-18
My apologies but I forgot I did certain things when troubleshooting. I noticed I had -7 and -8 versions of the code. I removed -7 from /lib/firmware, **which I have now replaced. I also blacklisted 802.11n in the iwlwifi.config file. I have also reverted this. **Now we should be on a default config.
I have set my router to 802.11b/g as apposed to b/g/n. It's also set to WPA2 only instead of WPA/WPA2 mixed and the channel to 6. That's all I can configure on this device. (ISP provided router, one day I will set up a dedicated pfSence box, but that's a story for another day ;)).

I have set my country code, rebooted (in-case the previous changes need applying).

Here are the previous outputs now all changes you recommended have been applied:


```
mark@UbuntuLaptop:~$ dmesg | grep iwl[   42.938434] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[   42.939773] iwlwifi 0000:06:00.0: irq 52 for MSI/MSI-X
[   42.943996] iwlwifi 0000:06:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   42.969241] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   42.969327] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   42.969603] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   43.177776] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   43.326649] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S
[   43.326902] iwlwifi 0000:06:00.0: L1 Enabled; Disabling L0S


mark@UbuntuLaptop:~$ ls -al /lib/firmware/ | grep 7260
-rw-r--r--  1 root root  683236 Mar  5 15:45 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 Mar  5 15:45 iwlwifi-7260-8.ucode


mark@UbuntuLaptop:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
```

My issue is disconnects after a while, so I will try to simulate this. I will update with my findings. Thank you again for your help.

---

### Post by MarkFrancis905 on 2014-04-18
Update: I got disconnected within 100 pings, prompted for a password and connected again.

---

### Post by chili555 on 2014-04-18
> **MarkFrancis905 said:**
> Update: I got disconnected within 100 pings, prompted for a password and connected again.Is power management on or off?```
iwconfig
```Does the syslog hold any clues?```
cat /var/log/syslog | grep -e iwl -e 80211 | tail -n25
```Ideally run just after a disconnect.

It seems that, even in the presence of the -7 firmware, the driver grabs -8.

---

### Post by MarkFrancis905 on 2014-04-18
As soon as I stopped the pings to run the commands, I was prompted for the password for my wifi again. It's still populated with the correct one, and clicking connect reconnects it. I'm not sure if that information is any help, but the more you know the better.

Power management is off.

I may need to expand the amount of lines i pull from the logs, but below are the significant information I managed to pull back. Is this any help?


```

UbuntuLaptop dbus[596]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'$
Apr 18 17:57:59 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: disconnected -> inactive$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <warn> No agents were available for this request.$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> NetworkManager state is now DISCONNECTED$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> Marking connection 'BTHub3-8HJJ 1' invalid.$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <warn> Activation (wlan0) failed for connection 'BTHub3-8HJJ 1'$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): deactivating device (reason 'none') [0]$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4423$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Withdrawing address record for fe80::7e7a:91ff:fe27:c03b on wlan0.$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::7e7a:91ff:fe27:c03b.$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Interface wlan0.IPv6 no longer relevant for mDNS.$
Apr 18 17:59:59 UbuntuLaptop kernel: [ 2775.903156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Withdrawing address record for 192.168.1.101 on wlan0.$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.$
Apr 18 17:59:59 UbuntuLaptop avahi-daemon[731]: Interface wlan0.IPv4 no longer relevant for mDNS.$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <warn> DNS: plugin dnsmasq update failed$
Apr 18 17:59:59 UbuntuLaptop NetworkManager[1007]: <info> Removing DNS information from /sbin/resolvconf$
Apr 18 17:59:59 UbuntuLaptop dnsmasq[2098]: setting upstream servers from DBus$
Apr 18 17:59:59 UbuntuLaptop wpa_supplicant[1111]: wlan0: CTRL-EVENT-SCAN-STARTED $


mark@UbuntuLaptop:~$ cat /var/log/syslog | grep -e iwl -e 80211 | tail -n25
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.247571] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.247595] cfg80211: Calling CRDA for country: GB
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253011] cfg80211: Regulatory domain changed to country: GB
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253019] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253024] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253027] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253031] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253034] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Apr 18 17:57:55 UbuntuLaptop kernel: [ 2651.253037] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.545950] cfg80211: Calling CRDA to update world regulatory domain
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553352] cfg80211: World regulatory domain updated:
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553359] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553364] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553368] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553372] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553375] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553378] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.553410] cfg80211: Calling CRDA for country: GB
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560765] cfg80211: Regulatory domain changed to country: GB
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560773] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560777] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560781] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560785] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560788] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Apr 18 17:57:59 UbuntuLaptop kernel: [ 2655.560791] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)


Apr 18 17:53:57 UbuntuLaptop wpa_supplicant[1111]: wlan0: CTRL-EVENT-SCAN-STARTED $
Apr 18 17:53:57 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: disconnected -> scanning$
Apr 18 17:54:00 UbuntuLaptop wpa_supplicant[1111]: wlan0: SME: Trying to authenticate with 00:03:d8:06:d9:3a (SSID='BTHub3-8HJJ' freq=2437 MHz)$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.194225] wlan0: authenticate with 00:03:d8:06:d9:3a$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.195862] wlan0: send auth to 00:03:d8:06:d9:3a (try 1/3)$
Apr 18 17:54:00 UbuntuLaptop wpa_supplicant[1111]: wlan0: Trying to associate with 00:03:d8:06:d9:3a (SSID='BTHub3-8HJJ' freq=2437 MHz)$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.197818] wlan0: authenticated$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.200626] wlan0: associate with 00:03:d8:06:d9:3a (try 1/3)$
Apr 18 17:54:00 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: scanning -> associating$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.209722] wlan0: RX AssocResp from 00:03:d8:06:d9:3a (capab=0x431 status=0 aid=2)$
Apr 18 17:54:00 UbuntuLaptop kernel: [ 2416.210950] wlan0: associated$
Apr 18 17:54:00 UbuntuLaptop wpa_supplicant[1111]: wlan0: Associated with 00:03:d8:06:d9:3a$
Apr 18 17:54:00 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: associating -> associated$
Apr 18 17:54:00 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake$
Apr 18 17:54:00 UbuntuLaptop wpa_supplicant[1111]: wlan0: WPA: Key negotiation completed with 00:03:d8:06:d9:3a [PTK=CCMP GTK=TKIP]$
Apr 18 17:54:00 UbuntuLaptop wpa_supplicant[1111]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:03:d8:06:d9:3a completed [id=0 id_str=]$
Apr 18 17:54:00 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed$
```

---

### Post by MarkFrancis905 on 2014-04-18
Here are some more logs right after a disconnect, bolded are things I think look significant:

```
UbuntuLaptop NetworkManager[1007]: <info> (wlan0): supplicant interface state: disconnected -> scanning$Apr 18 19:17:01 UbuntuLaptop CRON[5146]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)$
**Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <warn> (wlan0): link timed out.$**
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): device state change: activated -> failed (**reason 'SSID not found'**) [100 120 53]$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> NetworkManager state is now DISCONNECTED$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <warn> Activation (wlan0) failed for connection 'BTHub3-8HJJ 1'$
Apr 18 19:16:13 UbuntuLaptop whoopsie[1287]: online$
Apr 18 19:17:03 UbuntuLaptop whoopsie[1287]: offline$
Apr 18 19:17:03 UbuntuLaptop dbus[596]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): deactivating device (reason 'none') [0]$
Apr 18 19:17:03 UbuntuLaptop dbus[596]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 5003$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Withdrawing address record for fe80::7e7a:91ff:fe27:c03b on wlan0.$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::7e7a:91ff:fe27:c03b.$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Interface wlan0.IPv6 no longer relevant for mDNS.$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Withdrawing address record for 192.168.1.101 on wlan0.$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.$
Apr 18 19:17:03 UbuntuLaptop avahi-daemon[731]: Interface wlan0.IPv4 no longer relevant for mDNS.$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <warn> DNS: plugin dnsmasq update failed$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <info> Removing DNS information from /sbin/resolvconf$
Apr 18 19:17:03 UbuntuLaptop dnsmasq[2098]: setting upstream servers from DBus$
Apr 18 19:17:03 UbuntuLaptop kernel: [ 7403.998547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready$
Apr 18 19:17:03 UbuntuLaptop NetworkManager[1007]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.$
```

---

### Post by chili555 on 2014-04-19
I think your observation is correct. This suggests that the wireless radio in your computer could no longer hear a beacon response from the wireless router and disconnected. There are a few things you can do at the router and a few things you can do at the driver. 

Some routers allow for changes to transmit power. Please see attached. You may have some luck increasing the power just a bit. Be careful as increasing the power excessively increases heat and reduces life expectancy. Second, you might experiment with the orientation of the router. Sometimes, a move a few inches left or right, front or back or even orienting the router vertically or at an angle can be helpful. After experimenting with a change, check:```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: xx:D7:19:41:54:xx
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=**52**/70[/COLOR]  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Next, we can ask the driver suite to wait a bit longer before giving up and hanging up:```
sudo -i
echo "options mac80211 probe_wait_ms=3000"  >  /etc/modprobe.d/mac80211.conf
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

We notice that your SSID name has a space in it:> Activation (wlan0) failed for connection '[COLOR="#FF0000"]BTHub3-8HJJ 1[/COLOR]'If BT allows you to make a change in the device, you might change it to something a bit simpler, like 'ilovecoldbeer.' 

The 7260 is a very new device and there have already been three firmware updates so this is very much experimental. Thank you for being a helpful tester.

---

### Post by MarkFrancis905 on 2014-04-19
I'm unable to change the transmit power, but I have moved it around and can get a link quality of around 50/70.

The SSID name is some kind of second profile generated while I was troubleshooting. I have changed the SSID anyway to all lower case to eliminate that as a possible issue.

I disconnected after around 10 mins after these changes. It seems to think the password is incorrect. That would explain why it's prompting me for a password when it disconnects now. Is there any way to tell it to keep retrying with the password it already knows?

```
Apr 19 16:09:35 UbuntuLaptop kernel: [  974.920296] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)$Apr 19 16:09:35 UbuntuLaptop kernel: [  974.920299] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)$
Apr 19 16:09:35 UbuntuLaptop kernel: [  974.920302] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)$
Apr 19 16:09:35 UbuntuLaptop kernel: [  974.920306] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)$
Apr 19 16:09:35 UbuntuLaptop wpa_supplicant[1136]: wlan0: CTRL-EVENT-SCAN-STARTED $
Apr 19 16:09:35 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: disconnected -> scanning$
Apr 19 16:09:38 UbuntuLaptop wpa_supplicant[1136]: wlan0: SME: Trying to authenticate with 00:03:d8:06:d9:3a (SSID='awesomerouter' freq=2437 MHz)$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.963870] wlan0: authenticate with 00:03:d8:06:d9:3a$
Apr 19 16:09:38 UbuntuLaptop wpa_supplicant[1136]: wlan0: Trying to associate with 00:03:d8:06:d9:3a (SSID='awesomerouter' freq=2437 MHz)$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.966100] wlan0: send auth to 00:03:d8:06:d9:3a (try 1/3)$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.969407] wlan0: authenticated$
Apr 19 16:09:38 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: scanning -> authenticating$
Apr 19 16:09:38 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: authenticating -> associating$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.973626] wlan0: associate with 00:03:d8:06:d9:3a (try 1/3)$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.976483] wlan0: RX AssocResp from 00:03:d8:06:d9:3a (capab=0x431 status=0 aid=1)$
Apr 19 16:09:38 UbuntuLaptop kernel: [  977.977392] wlan0: associated$
Apr 19 16:09:38 UbuntuLaptop wpa_supplicant[1136]: wlan0: Associated with 00:03:d8:06:d9:3a$
Apr 19 16:09:38 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: associating -> associated$
Apr 19 16:09:38 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake$
Apr 19 16:09:43 UbuntuLaptop wpa_supplicant[1136]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:03:d8:06:d9:3a reason=4 locally_generated=1$
Apr 19 16:09:43 UbuntuLaptop wpa_supplicant[1136]: wlan0: **WPA: 4-Way Handshake failed - pre-shared key may be incorrect$**
Apr 19 16:09:43 UbuntuLaptop wpa_supplicant[1136]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="awesomerouter" auth_failures=1 duration=10$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <warn> Connection disconnected (reason -4)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.359881] cfg80211: Calling CRDA to update world regulatory domain$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <info> (wlan0): device state change: activated -> need-auth (reason 'supplicant-disconnect') [100 60 8]$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367085] cfg80211: World regulatory domain updated:$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367092] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367098] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367102] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367105] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367109] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367112] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.367152] cfg80211: Calling CRDA for country: GB$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <info> NetworkManager state is now CONNECTING$
Apr 19 15:53:44 UbuntuLaptop whoopsie[1302]: online$
Apr 19 16:09:43 UbuntuLaptop whoopsie[1302]: offline$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373593] cfg80211: Regulatory domain changed to country: GB$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373603] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373610] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373616] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373621] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373627] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)$
Apr 19 16:09:43 UbuntuLaptop kernel: [  982.373632] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)$
Apr 19 16:09:43 UbuntuLaptop dbus[693]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)$
Apr 19 16:09:43 UbuntuLaptop dbus[693]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'$
Apr 19 16:09:43 UbuntuLaptop NetworkManager[997]: <info> (wlan0): supplicant interface state: disconnected -> inactive$
Apr 19 16:09:43 UbuntuLaptop dbus[693]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)$
Apr 19 16:09:43 UbuntuLaptop dbus[693]: [system] Successfully activated service 'org.freedesktop.hostname1'$

```

---

### Post by psemeano on 2014-04-20
I'm having exactly the same problem with Xubuntu 14.04. Here's some info:

**lsusb**
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[B]lspci -nn | grep 0280
[/B]> 05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

[B]ls -al /lib/firmware | grep 7260
[/B]> -rw-r--r-- 1 root root 683236 Mar 5 15:45 iwlwifi-7260-7.ucode
-rw-r--r-- 1 root root 679780 Mar 5 15:45 iwlwifi-7260-8.ucode

[B]dmesg | grep iwl
[/B]> [ 17.954322] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s[ 17.954328] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 17.954384] iwl3945 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 18.107544] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 18.107552] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 18.107632] iwl3945 0000:05:00.0: irq 45 for MSI/MSI-X
[ 18.176920] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 21.601367] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[ 471.676061] iwl3945 0000:05:00.0: Queue 2 stuck for 2128 ms.
[ 471.676069] iwl3945 0000:05:00.0: On demand firmware reload
[ 504.280237] iwl3945 0000:05:00.0: Queue 2 stuck for 2168 ms.
[ 504.280246] iwl3945 0000:05:00.0: On demand firmware reload
[ 542.380032] iwl3945 0000:05:00.0: Queue 2 stuck for 2220 ms.
[ 542.380041] iwl3945 0000:05:00.0: On demand firmware reload
[ 636.992048] iwl3945 0000:05:00.0: Queue 2 stuck for 2256 ms.
[ 636.992061] iwl3945 0000:05:00.0: On demand firmware reload
[ 649.596063] iwl3945 0000:05:00.0: Queue 2 stuck for 2488 ms.
[ 649.596075] iwl3945 0000:05:00.0: On demand firmware reload
[ 726.840032] iwl3945 0000:05:00.0: Queue 2 stuck for 2196 ms.
[ 726.840041] iwl3945 0000:05:00.0: On demand firmware reload
[ 786.944021] iwl3945 0000:05:00.0: Queue 2 stuck for 2448 ms.
[ 786.944030] iwl3945 0000:05:00.0: On demand firmware reload
[ 907.728047] iwl3945 0000:05:00.0: Error sending C_TX_PWR_TBL: time out after 500ms.
[ 908.552050] iwl3945 0000:05:00.0: Queue 2 stuck for 2412 ms.
[ 908.552072] iwl3945 0000:05:00.0: On demand firmware reload
[ 979.160046] iwl3945 0000:05:00.0: Queue 2 stuck for 2408 ms.
[ 979.160058] iwl3945 0000:05:00.0: On demand firmware reload
[ 996.760049] iwl3945 0000:05:00.0: Queue 2 stuck for 2168 ms.
[ 996.760059] iwl3945 0000:05:00.0: On demand firmware reload
[ 1078.220044] iwl3945 0000:05:00.0: Queue 2 stuck for 2356 ms.
[ 1078.220057] iwl3945 0000:05:00.0: On demand firmware reload
[ 1145.320055] iwl3945 0000:05:00.0: Queue 2 stuck for 2260 ms.
[ 1145.320067] iwl3945 0000:05:00.0: On demand firmware reload
[ 1355.428036] iwl3945 0000:05:00.0: Queue 2 stuck for 2228 ms.
[ 1355.428045] iwl3945 0000:05:00.0: On demand firmware reload
[ 1448.720056] iwl3945 0000:05:00.0: Queue 2 stuck for 2408 ms.
[ 1448.720068] iwl3945 0000:05:00.0: On demand firmware reload
[ 1574.820047] iwl3945 0000:05:00.0: Queue 2 stuck for 2024 ms.
[ 1574.820059] iwl3945 0000:05:00.0: On demand firmware reload
[ 1597.924063] iwl3945 0000:05:00.0: Queue 2 stuck for 2088 ms.
[ 1597.924075] iwl3945 0000:05:00.0: On demand firmware reload
[ 1680.640055] iwl3945 0000:05:00.0: Queue 2 stuck for 2180 ms.
[ 1680.640067] iwl3945 0000:05:00.0: On demand firmware reload
[ 1777.252051] iwl3945 0000:05:00.0: Queue 2 stuck for 2296 ms.
[ 1777.252072] iwl3945 0000:05:00.0: On demand firmware reload
[ 1785.852032] iwl3945 0000:05:00.0: Queue 2 stuck for 2292 ms.
[ 1785.852040] iwl3945 0000:05:00.0: On demand firmware reload
[ 1839.592076] iwl3945 0000:05:00.0: Error sending C_RXON: time out after 500ms.
[ 1839.592090] iwl3945 0000:05:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[ 1840.496076] iwl3945 0000:05:00.0: Error sending C_RXON: time out after 500ms.
[ 1840.496089] iwl3945 0000:05:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[ 1841.400081] iwl3945 0000:05:00.0: Error sending C_RXON: time out after 500ms.
[ 1841.400095] iwl3945 0000:05:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[ 1841.452044] iwl3945 0000:05:00.0: Queue 4 stuck for 2500 ms.
[ 1841.452064] iwl3945 0000:05:00.0: On demand firmware reload
[ 1880.056050] iwl3945 0000:05:00.0: Queue 4 stuck for 2500 ms.
[ 1880.056072] iwl3945 0000:05:00.0: On demand firmware reload
[ 2425.660046] iwl3945 0000:05:00.0: Queue 2 stuck for 2260 ms.
[ 2425.660059] iwl3945 0000:05:00.0: On demand firmware reload
[ 3031.756055] iwl3945 0000:05:00.0: Queue 2 stuck for 2500 ms.
[ 3031.756067] iwl3945 0000:05:00.0: On demand firmware reload
[ 3059.364040] iwl3945 0000:05:00.0: Queue 2 stuck for 2448 ms.
[ 3059.364054] iwl3945 0000:05:00.0: On demand firmware reload
[ 3100.476041] iwl3945 0000:05:00.0: Queue 2 stuck for 2396 ms.
[ 3100.476051] iwl3945 0000:05:00.0: On demand firmware reload
[ 3294.584053] iwl3945 0000:05:00.0: Queue 2 stuck for 2320 ms.
[ 3294.584067] iwl3945 0000:05:00.0: On demand firmware reload
[ 3301.684050] iwl3945 0000:05:00.0: Queue 2 stuck for 2068 ms.
[ 3301.684063] iwl3945 0000:05:00.0: On demand firmware reload
[ 3723.172057] iwl3945 0000:05:00.0: Queue 2 stuck for 2500 ms.
[ 3723.172069] iwl3945 0000:05:00.0: On demand firmware reload
[ 3775.780067] iwl3945 0000:05:00.0: Queue 2 stuck for 2452 ms.
[ 3775.780090] iwl3945 0000:05:00.0: On demand firmware reload
[ 4123.392042] iwl3945 0000:05:00.0: Queue 2 stuck for 2500 ms.
[ 4123.392051] iwl3945 0000:05:00.0: On demand firmware reload
[B]
cat /var/log/syslog | grep -e iwl -e 80211 | tail -n25 [/B](I've highlighted the weird parts)
> Apr 20 20:21:40 semeano-laptop kernel: [ 3295.459225] cfg80211: (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)Apr 20 20:21:40 semeano-laptop kernel: [ 3295.459228] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.459231] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.459235] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[B]Apr 20 20:21:40 semeano-laptop kernel: [ 3295.471818] cfg80211: Calling CRDA for country: US
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478689] cfg80211: Regulatory domain changed to country: US[/B]
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478697] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478700] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478704] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478707] cfg80211: (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478710] cfg80211: (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478713] cfg80211: (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478717] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Apr 20 20:21:40 semeano-laptop kernel: [ 3295.478720] cfg80211: (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[B]Apr 20 20:21:47 semeano-laptop kernel: [ 3301.684050] iwl3945 0000:05:00.0: Queue 2 stuck for 2068 ms.
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.684063] iwl3945 0000:05:00.0: On demand firmware reload
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.722924] ieee80211 phy0: Hardware restart was requested
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.972640] cfg80211: Calling CRDA to update world regulatory domain
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978812] cfg80211: World regulatory domain updated:[/B]
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978821] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978825] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978829] cfg80211: (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978832] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 20 20:21:47 semeano-laptop kernel: [ 3301.978835] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)



EDIT: I've found this thread ([https://bbs.archlinux.org/viewtopic.php?id=148477](https://bbs.archlinux.org/viewtopic.php?id=148477)), and it seems that disabling the queue watchdog in iwlwifi (create /etc/modprobe.conf file with "options iwlwifi wd_disable=1") will solve it. I'm going to try.

EDIT 2: It didn't work.

EDIT 3: Nor creating /etc/modprobe.d/iwlwifi.conf file with "options iwlwifi wd_disable=0 bt_coex_active=0 11n_disable=1"
or
creating /etc/modprobe.d/iwl3945.conf file with "options iwlwifi wd_disable=0 bt_coex_active=0 11n_disable=1"

:(

---

### Post by chili555 on 2014-04-20
> **psemeano said:**
> I'm having exactly the same problem with Xubuntu 14.04. Here's some info:


<snip>

:(Since you have an iwl3945 and the title of this thread is Intel 7260, an entirely different device, i suggest you start your own new thread.

---

### Post by psemeano on 2014-04-21
Will do. Thanks.

---

### Post by csaorl on 2014-04-21
Hello,

I'm also having trouble with Ubuntu 14.04 and Intel 7260. The problems are very similar to the ones MarkFrancis905 has described: usually I can connect to some network, but after a while it starts disconnecting. Sometimes it takes several tries from the beginning to connect.

My output from dmesg | grep iwl

```
[    7.535594] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    7.673244] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[    7.673308] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    7.673526] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    7.943240] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   15.693201] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   15.693431] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 5657.520384] iwlwifi 0000:02:00.0: no hotplug settings from platform
[ 5657.954897] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 5657.955143] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6661.747799] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6661.748038] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6716.851998] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6716.852240] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6720.642671] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6720.642915] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6756.126272] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6756.126520] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6770.707725] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6770.707968] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6840.307991] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6840.308221] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
```

from ls -al /lib/firmware | grep 7260:

```
-rw-r--r--  1 root root  683236 mar  5 09:45 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 mar  5 09:45 iwlwifi-7260-8.ucode
```

and finally from lspci -nn | grep 0280:
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
```

Power management is on, any help on what can I do to stabilize the connection would be much appreciated.

---

### Post by MarkFrancis905 on 2014-04-22
> **csaorl said:**
> Hello,

I'm also having trouble with Ubuntu 14.04 and Intel 7260. The problems are very similar to the ones MarkFrancis905 has described: usually I can connect to some network, but after a while it starts disconnecting. Sometimes it takes several tries from the beginning to connect.
 ... 

I'd recomend grabbing some logs right after a disconnect happens:

> [COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/syslog | grep -e iwl -e 80211 | tail -n25[/FONT][/COLOR]

---

### Post by chili555 on 2014-04-22
I am starting to suspect that we have a full-fledged bug here. Is this post either of you? [http://askubuntu.com/questions/452075/intel-wireless-ac-7260-rev-73-connection-speed-unstable-in-ubuntu-14-04](http://askubuntu.com/questions/452075/intel-wireless-ac-7260-rev-73-connection-speed-unstable-in-ubuntu-14-04)

---

### Post by MarkFrancis905 on 2014-04-22
> **chili555 said:**
> I am starting to suspect that we have a full-fledged bug here. Is this post either of you? [http://askubuntu.com/questions/452075/intel-wireless-ac-7260-rev-73-connection-speed-unstable-in-ubuntu-14-04](http://askubuntu.com/questions/452075/intel-wireless-ac-7260-rev-73-connection-speed-unstable-in-ubuntu-14-04)

It's not me, but I'm willing to help in any way possible.

---

### Post by chili555 on 2014-04-22
So we have three cases of 'my 7260 doesn't perform as expected in 14.04.' Generally, driver dawgs like me and a few others around here look at the logs and try to decode what's going wrong and then try to fix it. Your logs really don't contain anything alarming (read: fixable). Even this isn't anything I know how to fix from outside the driver/firmware/hardware:> wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect$That just suggests to me that Network Manager offered the password and heard nothing from the router thereafter; essentially a variation of this:> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]$Again, we don't hear any reply from the router.

The rumor is that Intel undertook a big rewrite as of kernel 3.13; i.e. Ubuntu 14.04. That seems reasonable because a newer firmware also appears:> loaded firmware version 22.24.[COLOR="#FF0000"]8[/COLOR].0 op_mode iwlmvmThat corresponds to iwlwifi-7260-[COLOR="#FF0000"]8[/COLOR].ucode which first appeared in 14.04.

Do either of you have an earlier kernel installed, say 3.11.0-xx, that you can boot into at the GRUB menu? I wonder if the behavior is the same, better or worse.

---

### Post by garet jax on 2014-04-22
For the record, I am also having issues on 14.04.

> 
06:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260


What I get from syslog when disconnecting is:

> 
Apr 22 22:55:10 host wpa_supplicant[879]: wlan0: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=4 locally_generated=1
Apr 22 22:55:10 host NetworkManager[820]: <warn> Connection disconnected (reason -4)


I tried to disable power saving via:

> 
sudo iwconfig wlan0 power off


but the issue remained.

What is the official and recommended way to submit a bug in order to try to speed up resolution of these problems ?

Thanks!

---

### Post by chili555 on 2014-04-22
Power saving is off by default; from *modinfo*:```
$ modinfo iwlwifi
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
parm:           power_save:enable WiFi power management ([COLOR="#FF0000"]default: disable[/COLOR]) (bool)

```All of you, please register and add to the bug that garet jax is going to file; I ask that you give us the link here.

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by csaorl on 2014-04-22
I just had a chance to reply, the other post isn't mine either. I'll register right away on launchpad. Here's my output: 

```
Apr 22 22:02:30 Meraxes wpa_supplicant[903]: wlan0: WPA: Key negotiation completed with c0:4a:00:7c:e5:c8 [PTK=CCMP GTK=TKIP]
Apr 22 22:02:30 Meraxes wpa_supplicant[903]: wlan0: CTRL-EVENT-CONNECTED - Connection to c0:4a:00:7c:e5:c8 completed [id=0 id_str=]
Apr 22 22:02:30 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 22 22:02:30 Meraxes NetworkManager[817]: <info> (wlan0): roamed from BSSID (none) ((none)) to C0:4A:00:7C:E5:C8 (Nosgoth)
Apr 22 22:02:31 Meraxes wpa_supplicant[903]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c0:4a:00:7c:e5:c8 reason=4 locally_generated=1
Apr 22 22:02:31 Meraxes NetworkManager[817]: <warn> Connection disconnected (reason -4)
Apr 22 22:02:31 Meraxes kernel: [ 6254.576648] cfg80211: Calling CRDA to update world regulatory domain
Apr 22 22:02:31 Meraxes kernel: [ 6254.579204] cfg80211: World regulatory domain updated:
Apr 22 22:02:31 Meraxes kernel: [ 6254.579208] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 22 22:02:31 Meraxes kernel: [ 6254.579210] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 22 22:02:31 Meraxes kernel: [ 6254.579212] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 22 22:02:31 Meraxes kernel: [ 6254.579213] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 22 22:02:31 Meraxes kernel: [ 6254.579215] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 22 22:02:31 Meraxes kernel: [ 6254.579216] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 22 22:02:31 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 22 22:02:31 Meraxes wpa_supplicant[903]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 22 22:02:31 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 22 22:02:35 Meraxes wpa_supplicant[903]: wlan0: SME: Trying to authenticate with c0:4a:00:7c:e5:c8 (SSID='Nosgoth' freq=2462 MHz)
Apr 22 22:02:35 Meraxes kernel: [ 6258.335069] wlan0: authenticate with c0:4a:00:7c:e5:c8
Apr 22 22:02:35 Meraxes kernel: [ 6258.336796] wlan0: send auth to c0:4a:00:7c:e5:c8 (try 1/3)
Apr 22 22:02:35 Meraxes wpa_supplicant[903]: wlan0: Trying to associate with c0:4a:00:7c:e5:c8 (SSID='Nosgoth' freq=2462 MHz)
Apr 22 22:02:35 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 22 22:02:35 Meraxes kernel: [ 6258.339147] wlan0: authenticated
Apr 22 22:02:35 Meraxes kernel: [ 6258.342606] wlan0: associate with c0:4a:00:7c:e5:c8 (try 1/3)
Apr 22 22:02:35 Meraxes kernel: [ 6258.345641] wlan0: RX AssocResp from c0:4a:00:7c:e5:c8 (capab=0x431 status=0 aid=2)
Apr 22 22:02:35 Meraxes wpa_supplicant[903]: wlan0: Associated with c0:4a:00:7c:e5:c8
Apr 22 22:02:35 Meraxes kernel: [ 6258.349932] wlan0: associated
Apr 22 22:02:35 Meraxes kernel: [ 6258.350026] cfg80211: Calling CRDA for country: MX
Apr 22 22:02:35 Meraxes kernel: [ 6258.352981] cfg80211: Regulatory domain changed to country: MX
Apr 22 22:02:35 Meraxes kernel: [ 6258.352984] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 22 22:02:35 Meraxes kernel: [ 6258.352986] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Apr 22 22:02:35 Meraxes kernel: [ 6258.352988] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Apr 22 22:02:35 Meraxes kernel: [ 6258.352990] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2300 mBm)
Apr 22 22:02:35 Meraxes kernel: [ 6258.352991] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Apr 22 22:02:35 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Apr 22 22:02:35 Meraxes wpa_supplicant[903]: wlan0: WPA: Key negotiation completed with c0:4a:00:7c:e5:c8 [PTK=CCMP GTK=TKIP]
Apr 22 22:02:35 Meraxes wpa_supplicant[903]: wlan0: CTRL-EVENT-CONNECTED - Connection to c0:4a:00:7c:e5:c8 completed [id=0 id_str=]
Apr 22 22:02:35 Meraxes NetworkManager[817]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 22 22:03:09 Meraxes wpa_supplicant[903]: wlan0: CTRL-EVENT-SCAN-STARTED 

```

---

### Post by Thomas Uhl on 2014-04-24
I had the same problems with Dell XPS 13 and LTS 14.04 - the problems went away after setting the options for the two kernel modules!

---

### Post by launchpad-mfraz on 2014-04-24
Installed Kubuntu 14.04 on a new laptop from PCSpecialist. Today, I moved the laptop from right over the router to where it is going to be used and it keeps disconnecting. According to lspci, this laptop also has an Intel 7260 NIC.

Please let me know when the bug has been reported on Launchpad.

---

### Post by MarkFrancis905 on 2014-04-24
To confuse the situation more, I ran my laptop on my work wifi network (beefier access points, also closer to me) and it ran for over 3 hours without a disconnect. This might be luck but I'm going to setup my laptop overnight next to my home router and see what happens. 

Can some one recommend a better way of testing the connectivity?

---

### Post by MarkFrancis905 on 2014-04-29
What happened with this? Was a bug raised? I can't find it on Launchpad.
 
I would really like to get this correctly raised as an issue.

---

### Post by chili555 on 2014-04-29
> **MarkFrancis905 said:**
> What happened with this? Was a bug raised? I can't find it on Launchpad.
 
I would really like to get this correctly raised as an issue.I am not aware that a bug has yet been raised. I therefore suggest you register and do so and leave the link here so all can add to it.

---

### Post by rugiland on 2014-04-29
I have the same problems with Dell XPS 13 Ubuntu 14.04.

dmesg | grep iwl
```

[    2.642313] iwlwifi 0000:02:00.0: irq 59 for MSI/MSI-X
[    2.674070] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    2.701832] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.701918] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.702159] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.922099] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   28.358036] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   28.358283] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   78.220096] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  565.518758] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[  566.217197] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  566.218254] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  566.219172] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  566.454431] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  566.454700] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  570.152969] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  680.922693] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  681.235656] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  686.766031] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  693.214349] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  693.475624] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  694.800030] iwlwifi 0000:02:00.0: No association and the time event is over already...
[  700.620636] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  711.659237] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  938.863787] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[  939.557488] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  939.558541] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  939.564231] iwlwifi 0000:02:00.0: no hotplug settings from platform
[  940.136771] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  940.137044] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  947.345836] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  947.610600] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  947.908940] iwlwifi 0000:02:00.0: Time Event end notification failure
[ 1119.039337] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1797.504952] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1889.354575] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1947.202534] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3157.309741] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use

```

ls -al /lib/firmware | grep 7260
```

-rw-r--r--  1 root root  683236 &#1084;&#1072;&#1088;&#1090;&#1072;  5 19:45 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 &#1084;&#1072;&#1088;&#1090;&#1072;  5 19:45 iwlwifi-7260-8.ucode

```

lspci -nn | grep 0280
```

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)

```

By the way, there seems to be exactly the same bug at kernel.org: [https://bugzilla.kernel.org/show_bug.cgi?id=72601](https://bugzilla.kernel.org/show_bug.cgi?id=72601)

---

### Post by chili555 on 2014-04-29
> iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP useThat's easy enough to fix or at least try to fix. Check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. As long as you are in there, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

---

### Post by Holmen on 2014-04-29
For anyone else with issues about this wifi card, see my bug report and help by adding some heat: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1305305](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1305305)

---

### Post by 4fi-jon on 2014-04-29
Add another problem user with this same problem - my router actually creates two networks, a 2.4ghz one and a 5ghz one.  The 2.4ghz network is significantly more stable for me.  I have another box on 13.10 with a different wifi card that rocks on the network to further target the problem.

Will happily provide logs/etc. to support the resolution of this, and many thanks to everyone on this thread for the work already done!

---

### Post by chili555 on 2014-04-30
> **Holmen said:**
> For anyone else with issues about this wifi card, see my bug report and help by adding some heat: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1305305](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1305305)Thank you!

If I remember correctly, this device worked pretty well in Ubuntu 13.10 before Intel "improved" the driver and firmware! Do any of you have an older kernel, probably 3.11.0-xx, on your system? Can you select it at the GRUB menu, boot into it and tell us if the behavior is improved?

---

### Post by Justin_Evans on 2014-04-30
[SIZE=2][FONT=arial]I'm having the exact same issue.

[/FONT][/SIZE][h=1][SIZE=2][FONT=arial]Intel NUC D54250WYK w/ Intel 7260.HMWG on Ubuntu 14.04 -> Constant dropped connections.  I also can't seem to lock onto a 5GHz signal, but that's probably another issue altogether.[/FONT][/SIZE][/h][SIZE=2][FONT=arial]Intel NUC [/FONT][/SIZE][COLOR=#333333][FONT=arial]DC3217IYE w/ Intel [/FONT][/COLOR][COLOR=#333333][FONT=arial]6235AN.HMWWB on Ubuntu 14.04 -> Rock solid.[/FONT][/COLOR]

---

### Post by chili555 on 2014-04-30
Did you try my suggestions in post #4? Any better? Worse??

---

### Post by Justin_Evans on 2014-04-30
```
$ modinfo iwlwifi
```
firmware:       iwlwifi-7260-7.ucode

```
$ ls -al /lib/firmware | grep 7260
```
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode

Router:
WPA2 Personal / AES
Fixed 2.4 GHz channel / Fixed 5.0 GHz channel

```
$ sudo iw reg get
```
country 00:

```
$ sudo iw reg set US
```
Added 'iw reg set US' to /etc/rc.local -> Save -> Reboot

Now I cannot connect to any network.  Status stays at 'Connecting' for ~30 seconds and fails.

---

### Post by chili555 on 2014-04-30
> **Justin_Evans said:**
> ```
$ modinfo iwlwifi
```
firmware:       iwlwifi-7260-7.ucode

```
$ ls -al /lib/firmware | grep 7260
```
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode

Router:
WPA2 Personal / AES
Fixed 2.4 GHz channel / Fixed 5.0 GHz channel

```
$ sudo iw reg get
```
country 00:

```
$ sudo iw reg set US
```
Added 'iw reg set US' to /etc/rc.local -> Save -> Reboot

Now I cannot connect to any network.  Status stays at 'Connecting' for ~30 seconds and fails.I suggest you undo the change to /etc/rc.local and add to the bug report. I'm sorry I have no better suggestion.

---

### Post by bender1077 on 2014-05-02
Hello!  I have the exact same card/issue, except for the desktop card.  I also created a bug report for the desktop card if anyone would be able to review as well:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315202](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315202)

---

### Post by garet jax on 2014-05-13
Today on Ubuntu 14.04 there was an update that removed the firmware iwlwifi-7260-8.ucode, leaving version 7 (and adding firmware for 7265).

So far, no disconnections, so the old firmware seems to be far better than the new one.

I believe the update just deleted the faulty firmware file, leaving the old one in place.

Anyone else having got the update and seeing improvements ?

---

### Post by garet jax on 2014-05-13
Whole day without a disconnection.

This bug reports the "fix": [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569)

---

### Post by chili555 on 2014-05-13
> **garet jax said:**
> Whole day without a disconnection.

This bug reports the "fix": [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569)Great news! Thanks for your report.

---

### Post by Roasted on 2014-07-03
So, I see this is fixed, but I'm confused. I'm still having issues. At work, we run a WPA + WPA2 network. I am disconnecting a *lot* there. It says I'm still connected to the SSID, but actual network connectivity drops, as in my online services die off, ping doesn't work, etc. Only fix is to reconnect. Sometimes I go a day without issues, other times I'll drop connection 12 times in 15 minutes. It's obnoxious.

I'm on an XPS 13 with Ubuntu 14.04 fully updated. I ran a command in terminal that suggested I was on the -7 firmware. Even still I had these issues, but only at work. Only difference that I'm seeing is WPA + WPA2 at work versus just WPA2 at home (though I don't use multiple APs at home so maybe that's it?)

A co-worker of mine runs an identical laptop but with Arch. No problems at all. I've actually dropped connection multiple times sitting next to him while he had no issues at all.

Am I missing something? Is this *actually* fixed? Or am I seeing a new problem that wasn't part of the fix?

---

### Post by chili555 on 2014-07-03
[QUOTE ]though I don't use multiple APs at home so maybe that's it?[/QUOTE]I suspect that's exactly it; that your wireless is trying to roam to a 'better' access point. You might look at this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/)

---

### Post by Roasted on 2014-07-03
> **chili555 said:**
> I suspect that's exactly it; that your wireless is trying to roam to a 'better' access point. You might look at this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/)

That's just obnoxious given that I travel to a multitude of different buildings, and frequently, different areas of whatever building I'm in. I can understand that if I were in the same office all the time all day, but I'm not.

Be nice if there was an 'actual' fix. Given how much this card is used in Linux laptops, Dell, System76, etc., I wonder how many other people are having issues. Google suggests quite a few. :(

---

### Post by Roasted on 2014-07-05
Curious - if I put in the BSSID of the AP in network manager, does that mean that I lock onto that BSSID indefinitely, or that it'll simply be preferred?

i.e. if I'm downstairs most of the time connected to 00:11:22:33:44:55 with SSID "ubuntuforums", and I put that MAC of the BSSID in network manager, does that prevent me from connecting to the SAME wireless network upstairs to AP 55:44:33:22:11:00? I'm on networks with ~30 APs sharing the same SSID. While I may spend most of my time in location X, I don't want that entry in network manager to literally pervent me from going to location Y in the same building.

---

### Post by chili555 on 2014-07-05
> connected to 00:11:22:33:44:55 with SSID "ubuntuforums", and I put that MAC of the BSSID in network manager, does that prevent me from connecting to the SAME wireless network upstairs to AP 55:44:33:22:11:00? I believe the intent *is* to prevent it. Unfortunately, at this point in the world of Linux and Ubuntu, we live in an imperfect world. 

Having said that, I haven't tried the technique myself and we'd love to have you try and then report.

---

### Post by Roasted on 2014-07-05
We very well do live in an imperfect world. It's important to remember that no world is perfect. Often times similar issues on even the most "supported" setups still occur. I remember something nearly identical with a popular Intel chip and Windows not too long ago. We had about a thousand units with that combination. Oh the memories... :)

I'd be happy to report it. It'll just be a few days until I'm back on that network. Until then if anybody knows a solid answer, I'd be happy to hear. :)

---

### Post by Roasted on 2014-07-08
So here's what I found today. I checked nm-tool and found the MAC of the AP I was connected to. Sure enough, in about 5 seconds I disconnected. Go. Figure. (someone, please, help me pick up my jaw). I selected the MAC of the BSSID and connected accordingly. I walked down the hall. Eventually, I lost connection. I looked in "edit connections" and saw SSID listed. I then checked network manager and clicked on my SSID again. Oddly, it asked me for a password. I put in the password. This time it created a new entry, SSID 1.

So I have SSID with the MAC associated in the BSSID field for the AP I want to connect to, and SSID 1 without the entry whatsoever, allowing me to connect to any AP in the building.

What a mess. This laptop came with Ubuntu on it. What on earth?

---

### Post by Roasted on 2014-07-21
Well, an unfortunate update. I started using my laptop at home more in the evenings and this evening in particular I had nothing but problems. Clearly this is not an issue with my wireless card roaming to other APs, as I'm here at home with only one AP and I was getting disconnected consistently. I have the proposed repo enabled as I was testing some Unity bug fixes that haven't landed yet. I dug up the bug report ( [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569) ) that indicates that the 8.ucode was updated to reflect the fixed changes and was indeed in proposed. Unfortunately, I have it, and I'm still having a world of issues. I updated the report accordingly with my findings.

It's frustrating that this laptop came with Ubuntu and is having all of these problems, especially with an Intel chip. I understand that problems arise and whatnot, and truth be told, I've had my fair share of Windows and Mac problems when it comes to wireless, but it's just a bummer to see things like this. Here I am with an Ubuntu XPS 13 that came from Dell with Ubuntu on it and the wireless, half the time, is downright unusable. Other times it's flawless, but it's wildly unpredictable.

Has anybody at all has any sort of success as of recently with this chip? Unfortunately it looks like this chip is a unique shape (I'm actually on my 2nd wifi chip from Dell as originally it was thought to be a hardware issue), and I can't find any other chips in this particular shape that I could even swap with. A wireless chip swap takes all but 15 seconds but when no others are seemingly available in this form factor ( [http://www.pcp.ch/gfx435515new/Dual-Band-Wireless-AC-7260-2x2-BT-M2-435515.jpg](http://www.pcp.ch/gfx435515new/Dual-Band-Wireless-AC-7260-2x2-BT-M2-435515.jpg) ) it makes it difficult to really do anything about it. Anyway, if anybody has anything to chime in, I'm all ears.

Better grab my USB-to-ethernet dongle for tomorrow...

---

### Post by Roasted on 2014-07-24
Well, it sounds like this particular wireless card as a whole is not problematic with just Linux, but there are people on Windows 7, 8, 8.1 all having issues too. So this is something definitely hardware related isolated to this specific chip. I find it a little troubling that this wireless card has been out for almost a year and everybody is still having problems with it.

Some users are so bothered by it (as some people notated they spent 2.5k on a pair of his/her laptops, both with the 7260, and both having a multitude of problems), that they've discussed a class action lawsuit against Intel with this chip as nothing has changed in the nearly-year long span that this card has been on the market.

On one hand, I'm happy it's not just me using Linux. But on the other, dangit Intel, where's the fix?

---

### Post by michaeljs19902 on 2014-08-09
I have been playing around with this for about a full day now. Have read and tried just about everything except upgrading my kernel. I seem to have found a solution that is working well although I have only been testing it for about an hour now.

I moved the iwlwifi-7260-8.ucode into a iwlwifi.bak folder and restarted my computer. I have not had any packet loss, It connected right away instead of the usual 10 seconds it took before and pages are loading much faster.

```

cd /lib/firmware
sudo mkdir iwlwifi.bak
sudo mv iwlwifi-7260-8.ucode /iwlwifi.bak/iwlwifi-7260-8.ucode
sudo shutdown -r now
```

Hope this will help anyone else who is having this issue.

Upon restart 22.1.7.0 loaded in as a fallback.

System Information:
Intel 7260 (ver 83)
Carbon X1 2nd Gen

EDIT:

After 3 Hours now and testing it on two different networks that were constantly dropping (every 5 minutes) It looks like that  has completely solved my issue.

EDIT 2:

After using the older driver for a day now I see it still has a few issues. However these only seem to come up when everyone at my place is using the wifi. So when 2 are watching netflix and one is playing an online game I was getting some drops. Will have to test further to see if this is the only time it happens. However unlike with the old driver I can reconnect and I am good to go where before I would have to reboot.

---

### Post by play_ on 2014-08-28
Personally bumping this to give chili555 a huge thanks.

And also to post what i did to fix my problems, as these drivers still have issues.


[PHP]dmesg | grep iwl[/PHP]

gave me
[INDENT]iwlwifi 0000:06:00.0: loaded firmware version 22.24.[COLOR="#FF0000"]9[/COLOR].0 op_mode iwlmvm[/INDENT]

However, just like the OP, driver wanted one version below.

[PHP]modinfo iwlwifi[/PHP]

[INDENT]firmware:       iwlwifi-7260-[COLOR="#FF0000"]8[/COLOR].ucode[/INDENT]

So i went in /lib/firmware and moved deleted (actually removed to a different dir, just in case) all iwlwifi drivers except [COLOR="#008000"]iwlwifi-7260-9-unicode[/COLOR]

went ahead and did

[PHP]iw reg set US[/PHP]

And now it's stable.

In my case what was happening was, i would connect, and the connection would be very strong at first.
I would do apt-get a package and it would start at a download speed of 800kbs, and gradually slow down to 0bps. (this would happen anytime between 30 and 60 secs). So i couldn't even finish installing a package

after this fix, speed would fluctuate between ~30kbs - 800kbps for a bit, then held at a steady 500-800 kbps


Thanks again, chili555.

---

