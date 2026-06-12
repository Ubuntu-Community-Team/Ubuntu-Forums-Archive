---
title: "Problems with BCM43142 802.11b/g/n [14e4:4365] (rev 01)"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by tjkotula-m on 2015-12-12
First a disclaimer: I'm a networking noob.

With that out of the way I'm having intermittent problems with my wireless. Browsing the web via Firefox as well as sending/getting emails via Thunderbird is snappy at times and at other times I have to keep hitting "reload" or "cancel followed by send", respectively. All ubuntu updates seem to download without any problems - I think. The same laptop works fine when I boot into Win10 (don't hold it against me - I don't do it often :-).

Some details: I'm running Ubuntu 14.04.3 LTS with the latest 3.13.0-71 kernel. The network card is Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01). The laptop is HP-Pavilion-15 with an i5-5200U.

What I've found so far:
1. It's not related to distance because it happens when I'm right next to the router
2. I pinged my router at the same time (and not) from two laptops, running the same ubuntu. The one with BCM43142 looses 7% of packets and has a number of ping times even as high as 130ms. The other (Qualcomm QCA9565) has a zero loss and a ping time of less than 2ms for 98% of all packets (with one instance of 12ms).

PS. I've read through chili555's post ([http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)), but I think I need some specific pointers.

Any pointers will be greatly appreciated.

Thanks a lot

tomasz

---

### Post by chili555 on 2015-12-12
> Some details: I'm running Ubuntu 14.04.3 LTS with the latest 3.13.0-71 kernel. However, 14.04.3 LTS now ships with the much newer 3.19.0-xx kernel: [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)> By default, the 14.04.3 point release will ship with a newer 3.19 Linux kernel from Ubuntu 15.04, and a matching X.org stack. I think I'd try to get the later kernel version installed first. I suspect that a later and better *bcmwl-kernel-source* driver package will be installed, as well.```
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid

```Reboot and see if bcmwl is updated, too.```
sudo apt-get update 
sudo apt-get dist-upgrade
```Reboot and tell us if the wireless issue remains.

---

### Post by tjkotula-m on 2015-12-14
Hi chili555,

Thanks for trying to help me. I updated to the latest kernel (3.19.0-39. Boy that was a mammoth job - it took all of three minutes) and verified that *bcmwl-kernel-source *wasn't listed by apt-get dist-upgrade (which I ended up running in the end). It's different - but unfortunately worse different. Ping's packet loss is 25% and the longest time is 499ms. 

What I forgot to mention in my original email was that I tried (booting from a USB stick) 15.04 and 15.10 when they came out - and on both occasions I had to give up because the wireless icon wasn't showing any networks.

Any ideas what I can try now?

Thanks a lot

tomasz.

---

### Post by chili555 on 2015-12-14
Usually, the Broadcom proprietary driver is pretty solid. I wonder if interaction with the router or access point is a problem.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by tjkotula-m on 2015-12-15
> **chili555 said:**
> 
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. 
Unfortunately the only options I have are: WEP or WPA/WPA2-802.1x or WPA/WPA2-PSK. I've got the last one selected. I will ring up my ISP and see if they can upgrade the firmware.

> 
Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 
I've already had it setup like this (n+g+b, 20MHz, channel 11).

> 
Next, I recommend that your regulatory domain be set explicitly. 

Done that, set it to NZ. 

> 
Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.
Done that. Sadly it didn't make it any better - but not worse either. Note that after I changed the regulatory domain the first lot of pings had a 0% loss - and I thought that's great, however running subsequent groups of pings had a loss rate in the 20's. Looks like it's quite random.

---

### Post by chili555 on 2015-12-16
Are there any clues in the logs?```
cat /var/log/syslog | grep -e wl -e etwork
```

---

### Post by tjkotula-m on 2016-01-03
Hi chili555 and happy new year, 
I got a new router a week ago and was hoping that the problem was simply going to disappear. Well no so - it's still very intermittent - sometimes it's better and sometimes it's worse. You've asked about the logs. Here is a snap-shot when the connection is established (as a result of me changing one of the router options). 

  ```

11:28:53  wpa_supplicant[918]: wlan0: CTRL-EVENT-SCAN-STARTED 
11:28:54  wpa_supplicant[918]: wlan0: Trying to associate with 18:f1:45:2c:d1:88 (SSID='TJHEN' freq=2462 MHz)
11:28:54  NetworkManager[904]: <info> (wlan0): supplicant interface state: scanning -> associating
11:28:54  NetworkManager[904]: <info> (wlan0): roamed from BSSID 18:F1:45:2C:D1:88 (TJHEN) to (none) ((none))
11:28:54  wpa_supplicant[918]: wlan0: CTRL-EVENT-DISCONNECTED bssid=18:f1:45:2c:d1:88 reason=0
11:28:54  NetworkManager[904]: <info> (wlan0): supplicant interface state: associating -> disconnected
11:28:54  wpa_supplicant[918]: wlan0: CTRL-EVENT-SCAN-STARTED 
11:28:54  NetworkManager[904]: <info> (wlan0): supplicant interface state: disconnected -> scanning
11:28:55  wpa_supplicant[918]: wlan0: Trying to associate with 18:f1:45:2c:d1:88 (SSID='TJHEN' freq=2462 MHz)
11:28:55  NetworkManager[904]: <info> (wlan0): supplicant interface state: scanning -> associating
11:28:55  wpa_supplicant[918]: wlan0: Associated with 18:f1:45:2c:d1:88
11:28:55  NetworkManager[904]: <info> (wlan0): supplicant interface state: associating -> associated
11:28:55  NetworkManager[904]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
11:28:55  wpa_supplicant[918]: wlan0: WPA: Key negotiation completed with 18:f1:45:2c:d1:88 [PTK=CCMP GTK=CCMP]
11:28:55  wpa_supplicant[918]: wlan0: CTRL-EVENT-CONNECTED - Connection to 18:f1:45:2c:d1:88 completed [id=0 id_str=]
11:28:55  NetworkManager[904]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
11:28:55  NetworkManager[904]: <info> (wlan0): roamed from BSSID (none) ((none)) to 18:F1:45:2C:D1:88 (TJHEN) 
```

Do you any other suggestions for me to try?

Thanks a lot

tomasz

---

### Post by chili555 on 2016-01-04
May I assume that the new router is set up according to my suggestions in post #4? If unsure, please check and reset.

The log looks like a perfect connection. I'd really rather see a log as it disconnects and reconnects, if possible.

---

### Post by tjkotula-m on 2016-01-09
Hi chili555,
> May I assume that the new router is set up according to my suggestions in post #4? If unsure, please check and reset.
That's correct. WPA2-PSK/AES, 2.4GHz, ch11, BW=20MHz, 802.11n/EWC=AUTO.
> I'd really rather see a log as it disconnects and reconnects, if possible.
Sounds like you are in luck. Very occasionally the wireless just totally drops out (wifi icon doesn’t show any 'bars' and I have to disconnect and connect to restore it). Well this happened and here is [FONT=courier new]/var/log/syslog[/FONT]. Please note that when the wireless is intermitant (as per my original post), there are no related log entries.
```
&#65279;16:27:14 dbus[728]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
16:27:14 dbus[728]: [system] Successfully activated service 'org.freedesktop.hostname1'
16:27:14 kernel: [22269.852124] systemd-hostnamed[16199]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
16:26:20 wpa_supplicant[923]: message repeated 77 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
16:27:48 wpa_supplicant[923]: wlan0: CTRL-EVENT-DISCONNECTED bssid=18:f1:45:2c:d1:88 reason=0
16:27:48 kernel: [22303.349766] cfg80211: Calling CRDA to update world regulatory domain
16:27:48 kernel: [22303.351760] cfg80211: World regulatory domain updated:
16:27:48 kernel: [22303.351763] cfg80211:  DFS Master region: unset
16:27:48 kernel: [22303.351764] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
16:27:48 kernel: [22303.351766] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:27:48 kernel: [22303.351767] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:27:48 kernel: [22303.351769] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
16:27:48 kernel: [22303.351770] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:27:48 kernel: [22303.351771] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:27:48 kernel: [22303.351920] cfg80211: Calling CRDA for country: NZ
16:27:48 NetworkManager[909]: <info> (wlan0): supplicant interface state: completed -> disconnected
16:27:48 kernel: [22303.353828] cfg80211: Regulatory domain changed to country: NZ
16:27:48 kernel: [22303.353830] cfg80211:  DFS Master region: unset
16:27:48 kernel: [22303.353832] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
16:27:48 kernel: [22303.353833] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
16:27:48 kernel: [22303.353835] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (N/A)
16:27:48 kernel: [22303.353836] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (0 s)
16:27:48 kernel: [22303.353837] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm), (N/A)
16:27:48 wpa_supplicant[923]: wlan0: CTRL-EVENT-SCAN-STARTED 
16:27:48 NetworkManager[909]: <info> (wlan0): supplicant interface state: disconnected -> scanning
16:27:49 wpa_supplicant[923]: wlan0: Trying to associate with 18:f1:45:2c:d1:88 (SSID='TJHEN' freq=2462 MHz)
16:27:49 NetworkManager[909]: <info> (wlan0): supplicant interface state: scanning -> associating
16:27:49 wpa_supplicant[923]: wlan0: CTRL-EVENT-ASSOC-REJECT bssid=18:f1:45:2c:d1:88 status_code=16
16:27:49 NetworkManager[909]: <info> (wlan0): supplicant interface state: associating -> disconnected
16:27:49 wpa_supplicant[923]: wlan0: CTRL-EVENT-SCAN-STARTED 
16:27:49 NetworkManager[909]: <info> (wlan0): supplicant interface state: disconnected -> scanning
16:27:50 wpa_supplicant[923]: wlan0: Trying to associate with 18:f1:45:2c:d1:88 (SSID='TJHEN' freq=2462 MHz)
16:27:50 NetworkManager[909]: <info> (wlan0): supplicant interface state: scanning -> associating
16:27:50 wpa_supplicant[923]: wlan0: Associated with 18:f1:45:2c:d1:88
16:27:50 NetworkManager[909]: <info> (wlan0): supplicant interface state: associating -> associated
16:27:50 NetworkManager[909]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
16:28:00 wpa_supplicant[923]: wlan0: Authentication with 18:f1:45:2c:d1:88 timed out.
16:28:00 wpa_supplicant[923]: wlan0: CTRL-EVENT-DISCONNECTED bssid=18:f1:45:2c:d1:88 reason=3 locally_generated=1
16:28:00 wpa_supplicant[923]: wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
16:28:00 wpa_supplicant[923]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="TJHEN" auth_failures=1 duration=10
16:28:00 wpa_supplicant[923]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="TJHEN" auth_failures=2 duration=20
16:28:00 NetworkManager[909]: <warn> Connection disconnected (reason -3)
16:28:00 wpa_supplicant[923]: nl80211: Was expecting local disconnect but got another disconnect event first
16:28:00 NetworkManager[909]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
16:28:00 NetworkManager[909]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
16:28:00 NetworkManager[909]: <info> (wlan0): device state change: activated -> need-auth (reason 'supplicant-disconnect') [100 60 8]
16:28:00 kernel: [22315.814149] cfg80211: Calling CRDA to update world regulatory domain
16:28:00 kernel: [22315.816164] cfg80211: World regulatory domain updated:
16:28:00 kernel: [22315.816167] cfg80211:  DFS Master region: unset
16:28:00 kernel: [22315.816168] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
16:28:00 kernel: [22315.816170] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:28:00 kernel: [22315.816171] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:28:00 kernel: [22315.816172] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
16:28:00 kernel: [22315.816173] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:28:00 kernel: [22315.816174] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
16:28:00 kernel: [22315.816196] cfg80211: Calling CRDA for country: NZ
16:28:00 kernel: [22315.818315] cfg80211: Regulatory domain changed to country: NZ
16:28:00 kernel: [22315.818317] cfg80211:  DFS Master region: unset
16:28:00 kernel: [22315.818319] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
16:28:00 kernel: [22315.818320] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
16:28:00 kernel: [22315.818322] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (N/A)
16:28:00 kernel: [22315.818323] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (0 s)
16:28:00 kernel: [22315.818324] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm), (N/A)
16:28:00 NetworkManager[909]: <info> NetworkManager state is now CONNECTING
16:28:00 whoopsie[1127]: offline
16:28:00 dbus[728]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
16:28:00 dbus[728]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
16:28:00 NetworkManager[909]: <info> (wlan0): supplicant interface state: disconnected -> inactive
16:28:03 NetworkManager[909]: <warn> No agents were available for this request.
16:28:03 NetworkManager[909]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
16:28:03 NetworkManager[909]: <info> NetworkManager state is now DISCONNECTED
16:28:03 NetworkManager[909]: <info> Marking connection 'TJHEN' invalid.
16:28:03 NetworkManager[909]: <warn> Activation (wlan0) failed for connection 'TJHEN'
16:28:03 NetworkManager[909]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
16:28:03 NetworkManager[909]: <info> (wlan0): deactivating device (reason 'none') [0]
16:28:03 NetworkManager[909]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 15569
16:28:03 avahi-daemon[791]: Withdrawing address record for 192.168.20.4 on wlan0.
16:28:03 avahi-daemon[791]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.20.4.
16:28:03 avahi-daemon[791]: Interface wlan0.IPv4 no longer relevant for mDNS.
16:28:03 NetworkManager[909]: <warn> DNS: plugin dnsmasq update failed
16:28:03 NetworkManager[909]: <info> Removing DNS information from /sbin/resolvconf
16:28:03 dnsmasq[1132]: setting upstream servers from DBus
16:28:03 wpa_supplicant[923]: wlan0: CTRL-EVENT-SCAN-STARTED 
```

Thanks for your help.

tomasz.

---

### Post by chili555 on 2016-01-09
> 16:28:00 NetworkManager[909]: <info> (wlan0): supplicant interface state: disconnected -> inactive
16:28:03 NetworkManager[909]: <warn> No agents were available for this request.
16:28:03 NetworkManager[909]: <info> (wlan0): device state change: need-auth -> failed ([COLOR="#FF0000"]reason 'no-secrets'[/COLOR]) [60 120 7]As far as I know, this means, roughly, we can't connect because we haven't supplied any encryption key. It is not that we have supplied the wrong key; we haven't supplied *any *key.

Further along:> 16:28:00 wpa_supplicant[923]: wlan0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
16:28:00 wpa_supplicant[923]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="TJHEN" [COLOR="#FF0000"]auth_failures[/COLOR]=1 duration=10
16:28:00 wpa_supplicant[923]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="TJHEN" auth_failures=2 duration=20
16:28:00 NetworkManager[909]: <warn> Connection disconnected (reason -3)That sounds, instead, like the wrong key.

Please confirm that you have the correct key included in Network Manager and that NM is set to connect automatically to your network. 

[ATTACH=CONFIG]266624[/ATTACH]

Also confirm that there is just one network TJHEN nearby and that the wireless card is not trying to roam to a different TJHEN causing the disconnect.```
sudo iwlist scan
```

---

### Post by tjkotula-m on 2016-01-09
> Please confirm that you have the correct key included in Network Manager  and that NM is set to connect automatically to your network.
Both are definitely correct.

> Also confirm that there is just one network TJHEN nearby and that the  wireless card is not trying to roam to a different TJHEN causing the  disconnect.
This is correct too. Actually there are very few other networks in this area. The most I can see with a Wifi Analyser is 3 other.

```
wlan0     Scan completed :
          Cell 01 - Address: 18:F1:45:2C:D1:88
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"TJHEN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 0005544A48454E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

All very strange. Would be nice to know what the bug is.

Thanks a lot

tomasz.

---

### Post by sanket8 on 2016-01-15
[URL="http://ubuntuforums.org/member.php?u=1845391"][COLOR=#000000]Hey,
I am using HP-PAvilion-15 laptop which came preloaded with windows 8.1
I[/COLOR][/URL] am facing issues with the BCM43142 driver, my wi-fi connection is unstable and intermittently drops packets after some time, i have to restart then it works.. I am very frustated..
Please let me know if you found a solution? Help..!

---

### Post by tjkotula-m on 2016-01-26
> **sanket8 said:**
> [URL="http://ubuntuforums.org/member.php?u=1845391"][COLOR=#000000]I am using HP-PAvilion-15 laptop which came preloaded with windows 8.1
I[/COLOR][/URL] am facing issues with the BCM43142 driver
Hi sanket,

Are you saying that you are having wifi issues when running windoze? I only have this problem when running Ubuntu (which is most of the time). Wifi on Win10 works fine.

---

### Post by tjkotula-m on 2016-02-05
Hi chili555,

I don't know how helpful this is going to be but I captured some traffic with Wireshark when I was pinging the router. What I noticed are the volleys between the router and my laptop.
In one instance there were 80 back to back frames: Request-to-send (from laptop to router) followed by Clear-to-send (from router to laptop), all in a space of about 100ms. In general Clear-to-send had a time delta of about 50us from a previous captured frame (Request-to-send). It seems that the driver is not getting these Clear-to-send.

Thanks a lot
tomasz.

---

### Post by tjkotula-m on 2016-02-05
Next update. This one hasn't been a successful one :-(

First I updated BIOS (from F33 to F42)
Then following **Important Note** found below Broadcom Wireless Table (Installing Broadcom Wireless Drivers, [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)) I did:
[LIST=1]
[*]sudo apt-get purge bcmwl-kernel-source 
[*]reboot 
[*]sudo apt-get install firmware-b43-installer 
[*]reboot 
[*]At this point the wireless wasn't even recognised, so it seemed firmware-b43-installer wasn't for me 
[*]sudo apt-get purge firmware-b43-installer 
[*]reboot 
[*]sudo apt-get install bcmwl-kernel-source 
[*]reboot 
[/LIST]
At that point it seemed that wireless was working much better - it certainly was much more responsive. Pinging the router wasn't loosing any packets and the times were mostly short (circa 1ms). However I did notice blocks of packets all with a similar and much longer times.

But all came to a screeching halt when I closed the lid and then opened it. No wireless at all and wireless-is-disabled-by-hardware-switch error.

```
$ sudo rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

Sadly trying to unblock didn't fix it.

```
 $ sudo rfkill unblock all
```

So now I have to shut it down every time or use a blue-string as is the case now.
 
Any ideas what went wrong or how I can log a bug against the broadcom driver.

Thanks a lot

tomasz.

---

### Post by chili555 on 2016-02-05
Just wow. Have you tried Ubuntu 15.10? You could certainly try a live session to see if the kernel and bcmwl-kernel-source work and play well together.

I recommend that you file or add to a bug here: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

I wish I had a better suggestion.

---

### Post by tjkotula-m on 2016-02-20
> Have you tried Ubuntu 15.10? You could certainly try a live  session to see if the kernel and bcmwl-kernel-source work and play well  together.
I tried 3 different versions: 12.04, 15.04 and 15.10. The general work-flow was as follow:
[LIST=1]
[*]boot from a USB to a respective Ubuntu version. Every time erased the USB drive. 
[*]sudo apt-get install bcmwl-kernel-source 
[*]connect to my wireless network 
[*]ping the router for a minute or two 
[*]close and open the lid 
[*]sudo rfkill list 
[/LIST]
And here are the results. I'm afraid they are all bad.

**12.04**
ping test: 1.0/11/828/0% (min/avg/max/packet loss)
when I closed the lid the fans sped up and after opening the lid laptop was totally unresponsive. kernel panic when the lid was closed I presume. Repeated it again with the same result.BTW I'm getting kernel panics from time to time when running my installed 14.04.

**15.04**
ping test: 1.0/43/178/0% (min/avg/max/packet loss)
closing and opening the lid kills the wireless. 
sudo rfkill list all -> shows brcmwl0: hard blocked: yes
sudo rfkill unblock all does nothing

**15.10**
ping test: 1.2/4/180/0% (min/avg/max/packet loss)
closing and opening the lid kills the wireless. 
sudo rfkill list all -> shows brcmwl0: hard blocked: yes
sudo rfkill unblock all does nothing

A few more observations (noted with 15.10 but I suspect also applies to 15.04):[INDENT]1. rfkill list all
[/INDENT]

[LIST=|INDENT=2]
[*] hci0: Bluetooth, soft blocked=no, hard blocked=no 
[*]phy0: wireless, soft blocked=no, hard blocked=no 
[*]brmwl-0: wireless, soft blocked=no, hard blocked=no 
[/LIST]
[INDENT]after closing and opening the lid, rfkill list all:
[/INDENT]

[LIST=|INDENT=2]
[*]phy0: wireless, soft blocked=no, hard blocked=no 
[*]brmwl-0: wireless, soft blocked=no, hard blocked=yes 
[/LIST]
[INDENT]bluetooth is **no longer** listed and its icon is gone and the wireless doesn't go

2. hitting F12 (airplane mode) turns, as expected, all soft blocked flags to yes
hitting it again reverts all soft blocked flags to no. hard blocked flag is still on and wireless doesn't go

3. sudo apt-get purge bcmwl-kernel-source
rfkill list all: **still** lists brmwl-0

4. sudo apt-get install bcmwl-kernel-source doesn't fix anything.[/INDENT]

I love Ubuntu but I hate it on this laptop :-(

---

### Post by tjkotula-m on 2016-11-30
I have finally fixed the problem, which got even worse after a BIOS update. Replaced BCM43142 card with another one (RTL8188EE) and voila! Should have done it years ago.

---

