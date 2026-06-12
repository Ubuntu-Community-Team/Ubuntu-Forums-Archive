---
title: "Ubuntu NetworkManager cannot connect to wifi using WPA2-enterprise"
date: 2017-09-23
forum: Networking &amp; Wireless
---

### Post by zhuce6209 on 2017-09-23
[COLOR=#454545][FONT=&amp]I need some help with connecting my Ubuntu laptop to my university wifi. My laptop used to work OK with my university wifi, but slower and more unstable compared to my Windows/Mac laptops. Not it cannot connect at all.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]I have followed the suggestions from a similar question [Can't connect to WPA2 Enterprise PEAP network]("https://askubuntu.com/questions/929680/cant-connect-to-wpa2-enterprise-peap-network") (e.g. modify /etc/NetworkManager/system-connections/<WIFI_SSID>, use/not use ca-certificate, etc) but got no luck.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Please give any suggestion about how to debug this situation. Thanks![/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]My system: Ubuntu 16.04 Desktop, kernel 4.4.0-96-generic[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]Wireless adaptor (given by **lscpi**): Intel Corporation Centrino Wireless-N 2230 (rec c4).  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]The adaptor is not blocked according to **rfkill**[/FONT][/COLOR][COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]The university wifi that I try to connect to uses **WPA2-Enterprise** (PEAP/ MSCHAPv2) authentication.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]The /etc/network/interfaces file contains only the default settings:[/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    auto lo[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    iface lo inet loopback[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
**ifconfig** can show the normal 3 interfaces: eth0, lo and wlan0. The section for wlan0 is as below. [/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    wlan0     Link encap:Ethernet  HWaddr 10:40:8f:68:57:53  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              RX packets:3193 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              TX packets:4515 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              collisions:0 txqueuelen:1000 [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              RX bytes:1400747 (1.4 MB)  TX bytes:900703 (900.7 KB)[/FONT][/COLOR]

[COLOR=#454545][FONT=&amp]**iwconfig** returns[/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    wlan0     IEEE 802.11bgn  ESSID:"<WIFI_SSID>"  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Mode:Managed  Frequency:2.412 GHz  Access Point: B4:5D:50:DA:88:63   [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Bit Rate=65 Mb/s   Tx-Power=16 dBm   [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Retry short limit:7   RTS thr:off   Fragment thr:off[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Power Management:on[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Link Quality=41/70  Signal level=-69 dBm  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]              Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/FONT][/COLOR]

[COLOR=#454545][FONT=&amp]**iwlist wlan0 scan** returns multiple access points with the desired wifi name (SSID). One of them is as below:[/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    Cell 41 - Address: 84:D4:7E:6C:47:63[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Channel:1[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Frequency:2.412 GHz (Channel 1)[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Quality=38/70  Signal level=-72 dBm  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Encryption key:on[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    ESSID:"<WIFI_SSID>"[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Bit Rates:11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                              24 Mb/s; 36 Mb/s; 48 Mb/s[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Bit Rates:54 Mb/s[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Mode:Master[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Extra:tsf=0000009548497af2[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    Extra: Last beacon: 644ms ago[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 000A434D552D534543555245[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 0108168C929824304860[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 030101[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 2A0103[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                        Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                        Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                        Authentication Suites (1) : 802.1x[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 32016C[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 2D1AAD0117FFFFFFFF00000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 3D1601000500000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 4A0E14000A002C01C800140005001900[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: 7F080100080000000040[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00[/FONT][/COLOR]


The full result of the `wireless-info` script is available [here]("https://www.dropbox.com/s/zr7lu64bw4asr8i/wireless-info.txt?dl=0").
[COLOR=#454545][FONT=&amp]**What I have confirmed**:  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](1) My username and password is correct. I used them to authenticate other devices with no problems.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](2) My MAC address is not blocked. I booted the same computer into Windows 10 and Kali Linux, and it can access the same wifi using the same wireless adaptor with no problem.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](3) The wifi connection issue does not happen when connecting to other wifi which does not use `WPA2-Enterprise` (PEAP/ MSCHAPv2) authentication. For instance, connecting to me iPhone hotspot works fine.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]**What I think the problem might be**:  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](1) It might be authentication failure. After select the wifi that I want to connect, Ubuntu `NetworkManager` would prompt me to enter my username and password again, which does not usually happen when the saved password is correct.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](2) `/var/log/syslog` highlights the following lines:[/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    systemd[1]: Dependency failed for /dev/disk/by-uuid/7bb6b05e-7e8d-4895-8e8f-575806a2b9e8.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.swap: Job dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.swap/start failed with result 'dependency'.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device: Job dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device/start failed with result 'timeout'.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    NetworkManager[2993]: <info>  [1506199546.6039] device (wlan0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7][/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    NetworkManager[2993]: <info>  [1506199546.6041] manager: NetworkManager state is now DISCONNECTED[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    NetworkManager[2993]: <warn>  [1506199546.6045] device (wlan0): Activation: failed for connection '<WIFI_SSID>'[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    NetworkManager[2993]: <info>  [1506199546.6053] device (wlan0): state change: failed -> disconnected (reason 'none') [120 30 0][/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    gnome-session[1995]: (nm-applet:2171): libnm-WARNING **: (nm-access-point.c:285):nm_access_point_connection_valid: runtime check failed: (ap_ssid != NULL)[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    gnome-session[1995]: message repeated 75 times: [ (nm-applet:2171): libnm-WARNING **: (nm-access-point.c:285):nm_access_point_connection_valid: runtime check failed: (ap_ssid != NULL)][/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device: Job dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device/start timed out.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: Dependency failed for /dev/disk/by-uuid/7bb6b05e-7e8d-4895-8e8f-575806a2b9e8.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.swap: Job dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.swap/start failed with result 'dependency'.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    systemd[1]: dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device: Job dev-disk-by\x2duuid-7bb6b05e\x2d7e8d\x2d4895\x2d8e8f\x2d575806a2b9e8.device/start failed with result 'timeout'.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    gnome-session[1995]: (nm-applet:2171): libnm-WARNING **: (nm-access-point.c:285):nm_access_point_connection_valid: runtime check failed: (ap_ssid != NULL)[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    gnome-session[1995]: message repeated 41 times: [ (nm-applet:2171): libnm-WARNING **: (nm-access-point.c:285):nm_access_point_connection_valid: runtime check failed: (ap_ssid != NULL)][/FONT][/COLOR]

[COLOR=#454545][FONT=&amp](3) `/var/log/kern.log` highlights the following lines:[/FONT][/COLOR]
> 
[COLOR=#454545][FONT=&amp]    device (wlan0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7][/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    manager: NetworkManager state is now DISCONNECTED[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    device (wlan0): Activation: failed for connection '<WIFI_SSID>'[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]    device (wlan0): state change: failed -> disconnected (reason 'none') [120 30 0][/FONT][/COLOR]

[COLOR=#454545][FONT=&amp]I am sharing the complete version of `syslog` and `kern.log` [here]("https://www.dropbox.com/s/0voovm7qy16gon1/upload_fail?dl=0") when I tried to connect to my university wifi.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]For comparison, when I connect to my own iPhone hotspot successfully, the `syslog` and `kern.log` are like [here]("https://www.dropbox.com/s/s0upizfzq38b9x3/upload_success.txt?dl=0"). They are not too long.[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]**What I might have messed up with recently**:  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](1) I tried to setup a network bridge from `wlan0` to `eth0` so that other devices (raspberry pi) can connect to the internet through Ethernet. I modified the `/etc/network/interfaces` to do that. It worked, but slows down the network significantly, so I reverted the `interfaces` file.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](2) I tried to setup static IP thought NetworkManager GUI. It didn't work and I reverted back to DHCP.  [/FONT][/COLOR]
[COLOR=#454545][FONT=&amp](3) When debugging the static IP issue, I tried to modify DNS settings in `/etc/resolv.conf` and `/etc/resolvconf/resolv.conf.d/base`.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2017-09-23
Welcome. First advice normally given in this situation? Call the uni IT department and see if they can help. You don't mention them, but they know the ins and outs of their setup, network and certificates. We don't. A uni network like this is definitely not 'in the wild' and as such can be as exotic or boutique as they want to make it. No idea what they may have done to secure it.

Perhaps one of the reasons you can no longer log on is that they've changed something about their network in an effort to up the security. If you don't ask them directly you won't know and you'll never get around the wall (and we can only help you do so legally and with uni networks, we would be asking you for details perhaps only they can give anyway. :)).

Have a chat with uni IT dept. They may be able to rectify the situation quickly and save you some time. Good luck. ;)

---

