---
title: "WNA3100 netgear wireless USB issues - driver installed but no stable connection"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by luis_antonio2 on 2014-05-04
All,

I have been reading the great job that people have done in this subject. I followed most of the pertinent work done here to get my wireless USB card to work. 
Based on the suggeestions I was able  to get my wireless USB netgear wna3100 to start, recognize wireless networks around (including ours) but I cannot stablish connection with the network. I got continously the request for the network password and after giving the correct password, I do not get connection.

I appreciate very much any help. 

Cheers,
Luis


Just to give you guys some information:

result from lsusb

Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 024: ID 0b0e:a330 GN Netcom

result from: lsmod | grep ndis:  ndiswrapper           237175  1 ndiswrapper module is loaded

result from: ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present

This is the windows driver that is installed in my windows XP partition. I used the ndiswrapper to intall it under linux. It is importatnt to tell that I tried three different versions of the same driver, including the one I copied from the windows partition. Unfortunately, I cannot retrieve the .in fille from the manufacturer (even running 7zip under windows).

Result of : ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.11.0-15-generic/misc/ndiswrapper.ko
version:        1.59
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686

result of: dmesg | grep -e ndis -e wlan
[  240.860201] usbcore: deregistering interface driver ndiswrapper
[  240.865456] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  241.119510] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[  241.414007] wlan0: ethernet device 08:bd:43:87:ac:6b using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[  241.419612] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  241.436154] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  241.436434] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  252.735153] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

with another option that I found in the discussions (the bcmn43xx32.sys driver), which seems that works for some people. I get in the dmesg | grep -e ndis -e wlan that the device is not activated and cannot be activated. It is also important to tell that it is an old computer 32-bits. I have installed Ubuntu 12.04 32-bits, since I am working with the same version in another computer but at 64-bits version.

with iwconfig I get

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

when I am trying to get connected during the attempts.

---

### Post by luis_antonio2 on 2014-05-11
Hi All,

Just complementing my original post. I checked further the posts about this subject. I changed some settings of my router, such as using b/g instead of b/g+n, or using WPA2-AES, channel width of 20 MHz instead of automatic 20/40 MHz.  I also disabled IPV6 setting to ignore. 
To regain access to the internet via wireless, I need to re-boot the computer or disconnect and re-connect the wireless USB stick

just give you all part of the syslog just after my internet contact is lost. 

$ cat /var/log/syslog | tail -n40

May 11 20:04:33  kernel: [   60.329207] audit_printk_skb: 99 callbacks suppressed
May 11 20:04:33  kernel: [   60.329212] type=1400 audit(1399831473.252:69): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2162 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
May 11 20:04:33  goa[2167]: goa-daemon version 3.4.0 starting [main.c:112, main()]
May 11 20:05:01  dbus[865]: [system] Activating service name='org.gnome.SettingsDaemon.DateTimeMechanism' (using servicehelper)
May 11 20:05:01  dbus[865]: [system] Successfully activated service 'org.gnome.SettingsDaemon.DateTimeMechanism'
May 11 20:05:24  dbus[865]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May 11 20:05:25  AptDaemon: INFO: Initializing daemon
May 11 20:05:26  AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 11 20:05:26  dbus[865]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May 11 20:05:26  AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May 11 20:05:26  AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/1a9a9c891dce47f78bd61cfdad6054b9
May 11 20:05:26  AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/1a9a9c891dce47f78bd61cfdad6054b9
May 11 20:05:29  AptDaemon.PackageKit: INFO: Get updates()
May 11 20:05:29  AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/1a9a9c891dce47f78bd61cfdad6054b9
May 11 20:11:27  AptDaemon: INFO: Quitting due to inactivity
May 11 20:11:27  AptDaemon: INFO: Quitting was requested
May 11 20:17:01 CRON[2471]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 11 20:20:41  wpa_supplicant[1255]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May 11 20:20:42  wpa_supplicant[1255]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May 11 20:20:43  NetworkManager[936]: <info> (wlan0): supplicant interface state: completed -> 4-way handshake
May 11 20:20:43  wpa_supplicant[1255]: WPA: Key negotiation completed with 00:0c:f6:9b:9e:fc [PTK=CCMP GTK=CCMP]
May 11 20:20:43  NetworkManager[936]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
May 11 20:20:46  wpa_supplicant[1255]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
May 11 20:21:20  wpa_supplicant[1255]: last message repeated 20 times
May 11 20:22:21  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:23:22  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:24:23  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:25:24  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:26:25  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:27:27  wpa_supplicant[1255]: last message repeated 35 times
May 11 20:28:28  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:29:29  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:30:30  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:31:31  wpa_supplicant[1255]: last message repeated 37 times
May 11 20:32:32  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:33:35  wpa_supplicant[1255]: last message repeated 35 times
May 11 20:34:36  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:35:37  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:36:38  wpa_supplicant[1255]: last message repeated 36 times
May 11 20:37:41  wpa_supplicant[1255]: last message repeated 36 times

Perhaps I have not indicated in my previous post but I installed Ubuntu 12.04 32-bits in our old computer, where the problem is occurring when I use the wireless USB stick WNA3100 N300 Netgear.

Thanks for any feedback.
Luis

---

