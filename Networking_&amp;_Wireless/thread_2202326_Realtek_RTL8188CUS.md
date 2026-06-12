---
title: "Realtek RTL8188CUS"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by lestat2 on 2014-01-28
I used to be able to use my Ubuntu desktop to connect to my Wireless   AP.  Then I moved across country and when I finally received my box, the   system would no longer connect to the AP.  I have other devices   attached to that AP, so I know it works. I have tried to authenticate to   a different AP, but that fails. I have taken the wireless NIC card and   put it in my laptop, the NIC worked. 

  The device is able to detect the NIC is there, and uses it to try to   authenticate to the network.  I've watched the logs, and when I enter a   new AP this is what I see.  Logs from what I've seen below. 

  My AP is a Netgear and my NIC is a Edimax.

  I've run out of ideas, any suggestions of what else I could try????

```
 lestat@france:/var/log$ tail -f auth.log syslog
==> auth.log <==
Jan 27 13:17:08 france sudo: lestat : TTY=pts/0 ; PWD=/etc/NetworkManager/system-onnections ; USER=root ; COMMAND=/usr/bin/less FRITZ!Box 7330
Jan 27 13:17:08 france sudo: pam_unix(sudo:session): session opened for user root by estat(uid=1000)
Jan 27 13:17:38 france sudo: pam_unix(sudo:session): session closed for user root
Jan 27 13:27:04 france polkitd(authority=local): Unregistered Authentication Agent for nix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.32, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Jan 27 13:27:37 france lightdm: pam_unix(lightdm-autologin:session): session opened for user lestat by (uid=0)
Jan 27 13:27:37 france lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Jan 27 13:27:38 france polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.27 {/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1}, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jan 27 13:27:41 france dbus[758]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=1000 pid=1583 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1171 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan 27 14:17:01 france CRON[2021]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 14:17:01 france CRON[2021]: pam_unix(cron:session): session closed for user root
==> syslog <==
Jan 27 14:37:31 france NetworkManager[796]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 27 14:37:31 france NetworkManager[796]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0/wireless): access point 'Orleans2000' has security, but secrets are required.
Jan 27 14:37:31 france NetworkManager[796]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 27 14:37:31 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 27 14:38:17 france NetworkManager[796]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 27 14:38:17 france NetworkManager[796]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 27 14:38:17 france NetworkManager[796]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0/wireless): connection 'Orleans2000' has security, and secrets exist. No new secrets needed.
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: added 'ssid' value 'Orleans2000'
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: added 'scan_ssid' value '1'
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: added 'psk' value '<omitted>'
Jan 27 14:38:17 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 27 14:38:17 france NetworkManager[796]: <info> Config: set interface ap_scan to 1
Jan 27 14:38:17 france NetworkManager[796]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan 27 14:38:17 france wpa_supplicant[1024]: Trying to authenticate with c4:3d:c7:64:0d:25 (SSID='Orleans2000' freq=2437 MHz)
Jan 27 14:38:17 france NetworkManager[796]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 27 14:38:18 france kernel: 4259.084194] wlan0: authenticate with c4:3d:c7:64:0d:25 (try 1)
Jan 27 14:38:18 france wpa_supplicant[1024]: Trying to associate with c4:3d:c7:64:0d:25 (SSID='Orleans2000' freq=2437 MHz)
Jan 27 14:38:18 france kernel: 4259.086363] wlan0: authenticated
Jan 27 14:38:18 france NetworkManager[796]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 27 14:38:18 france kernel: 4259.110689] wlan0: associate with c4:3d:c7:64:0d:25 (try 1)
Jan 27 14:38:18 france kernel: 4259.114336] wlan0: RX AssocResp from c4:3d:c7:64:0d:25 (capab=0x411 status=0 aid=2)
Jan 27 14:38:18 france kernel: [ 4259.114340] wlan0: associated
Jan 27 14:38:18 france wpa_supplicant[1024]: Associated with c4:3d:c7:64:0d:25
Jan 27 14:38:18 france kernel: 4259.127405] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 27 14:38:18 france NetworkManager[796]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 27 14:38:18 france wpa_supplicant[1024]: WPA: Key negotiation completed with c4:3d:c7:64:0d:25 [PTK=CCMP GTK=CCMP]
Jan 27 14:38:18 france wpa_supplicant[1024]: CTRL-EVENT-CONNECTED - Connection to c4:3d:c7:64:0d:25 completed (auth) [id=0 id_str=]
Jan 27 14:38:18 france NetworkManager[796]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'Orleans2000'.
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 27 14:38:18 france NetworkManager[796]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 27 14:38:18 france dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jan 27 14:38:18 france dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jan 27 14:38:18 france dhclient: All rights reserved.
Jan 27 14:38:18 france dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan 27 14:38:18 france dhclient:
Jan 27 14:38:18 france NetworkManager[796]: <info> dhclient started with pid 2145
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 27 14:38:18 france NetworkManager[796]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 27 14:38:18 france NetworkManager[796]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 27 14:38:18 france dhclient: Listening on LPF/wlan0/80:1f:02:34:32:33
Jan 27 14:38:18 france dhclient: Sending on LPF/wlan0/80:1f:02:34:32:33
Jan 27 14:38:18 france dhclient: Sending on Socket/fallback
Jan 27 14:38:18 france dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan 27 14:38:21 france dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan 27 14:38:28 france kernel: [ 4269.502234] wlan0: no IPv6 routers present
Jan 27 14:38:28 france dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan 27 14:38:38 france NetworkManager[796]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 27 14:38:38 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 27 14:38:38 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 27 14:38:38 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 27 14:38:38 france dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jan 27 14:38:52 france dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jan 27 14:39:03 france NetworkManager[796]: <warn> (wlan0): DHCPv4 request timed out.
Jan 27 14:39:03 france NetworkManager[796]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2145
Jan 27 14:39:03 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jan 27 14:39:03 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jan 27 14:39:03 france NetworkManager[796]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jan 27 14:39:03 france NetworkManager[796]: <warn> Activation (wlan0) failed for access point (Orleans2000)
Jan 27 14:39:03 france NetworkManager[796]: <warn> Activation (wlan0) failed.
Jan 27 14:39:03 france NetworkManager[796]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jan 27 14:39:03 france NetworkManager[796]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 27 14:39:03 france NetworkManager[796]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 27 14:39:03 france kernel: [ 4304.436359] wlan0: deauthenticating from c4:3d:c7:64:0d:25 by local choice (reason=3)
Jan 27 14:39:03 france wpa_supplicant[1024]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jan 27 14:39:03 france NetworkManager[796]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jan 27 14:39:03 france kernel: 4304.522687] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan 27 14:39:03 france kernel: 4304.522692] cfg80211: Restoring regulatory settings
Jan 27 14:39:03 france kernel: 4304.522696] cfg80211: Calling CRDA to update world regulatory domain
Jan 27 14:39:03 france kernel: 4304.525578] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan 27 14:39:03 france kernel: 4304.525581] cfg80211: World regulatory domain updated:
Jan 27 14:39:03 france kernel: 4304.525583] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 27 14:39:03 france kernel: 4304.525585] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 27 14:39:03 france kernel: 4304.525587] cfg80211: (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 27 14:39:03 france kernel: 4304.525588] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 27 14:39:03 france kernel: 4304.525590] cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 27 14:39:03 france kernel: 4304.525592] cfg80211: (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 27 14:39:06 france NetworkManager[796]: <info> Auto-activating connection 'Orleans2000'.
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) starting connection 'Orleans2000'
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0/wireless): access point 'Orleans2000' has security, but secrets are required.
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0/wireless): connection 'Orleans2000' has security, and secrets exist. No new secrets needed.
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: added 'ssid' value 'Orleans2000'
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: added 'scan_ssid' value '1'
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: added 'psk' value '<omitted>'
Jan 27 14:39:06 france NetworkManager[796]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 27 14:39:06 france NetworkManager[796]: <info> Config: set interface ap_scan to 1
Jan 27 14:39:06 france NetworkManager[796]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 27 14:40:06 france NetworkManager[796]: <warn> Activation (wlan0/wireless): association took too long.
Jan 27 14:40:06 france NetworkManager[796]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 27 14:40:06 france NetworkManager[796]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan 27 14:40:06 france NetworkManager[796]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 27 14:40:06 france NetworkManager[796]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 27 14:40:09 france NetworkManager[796]: <info> (wlan0): supplicant interface stat e: scanning -> inactive
```

---

### Post by praseodym on 2014-01-28
Hi,

please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work? What kind of computer is it?

---

### Post by lestat2 on 2014-01-28
The wireless lan works for my other devices.  

The computer is a custom x64 bit box I built.

> Script started on Tue 28 Jan 2014 04:34:50 PM EST
lestat@france: 
lestat@france:~$ uname -a 
Linux france 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
lestat@france: 
lestat@france:~$ lspci -nnk| grep -iA2 net 
02:00.0 Ether [Knet[K controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ether[01;31m[Knet[m[K controller [10ec:8168] (rev 06) 
    Subsystem: Biostar Microtech Int'l Corp Device [1565:230a] 
    Kernel driver in use: r8169 
lestat@france: 
lestat@france:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 003: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard 
Bus 002 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS] 
Bus 002 Device 005: ID 0781:556b SanDisk Corp.  
lestat@france: lsmod 
Module                  Silestat  Used by 
nls_iso8859_1          12713  1  
nls_cp437              16991  1  
vfat                   17585  1  
fat                    61512  1 vfat 
uas                    18180  0  
usb_storage            49198  1  
vesafb                 13844  1  
snd_hda_codec_hdmi     32474  2  
snd_hda_codec_realtek   224173  1  
rfcomm                 47604  0  
bnep                   18281  2  
bluetooth             180104  10 rfcomm,bnep 
binfmt_misc            17540  1  
arc4                   12529  2  
ppdev                  17113  0  
joydev                 17693  0  
snd_hda_intel          33773  5  
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13668  1 snd_hda_codec 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0  
snd_rawmidi            30748  1 snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
parport_pc             32866  1  
snd_timer              29990  2 snd_pcm,snd_seq 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
rtl8192cu             103297  0  
rtl8192c_common        75767  1 rtl8192cu 
rtlwifi               111202  1 rtl8192cu 
mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi 
fglrx                3263886  123  
cfg80211              205544  2 rtlwifi,mac80211 
usbhid                 47199  0  
psmouse                97443  0  
hid                    99592  1 usbhid 
mac_hid                13253  0  
serio_raw              13211  0  
soundcore              15091  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
mei                    41616  0  
lp                     17799  0  
parport                46562  3 ppdev,parport_pc,lp 
r8169                  62099  0  
lestat@france:  iwconfig 
lo        no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off 
          Power Management:off 
           
eth0      no wireless extensions. 
 
lestat@france:  rfkill list 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
lestat@france:  cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.0.1 
lestat@france:~$ exit 
exit 

Script done on Tue 28 Jan 2014 04:37:01 PM EST


---

### Post by praseodym on 2014-01-28
Update the driver via LAN:

```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. You should update your system.

---

### Post by lestat2 on 2014-01-28
What would the commands be for downloading those on one computer,
then installing them to from a thumbdrive on the problem computer? My Cat5 isn't long enough to reach the computer.

---

### Post by praseodym on 2014-01-29
Downloads these two files and save them in "Downloads":

[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu2_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by lestat2 on 2014-01-30
That worked!!

Here's the screen output of what happened. 



=====================================================
```
lestat@france:/media/armand$ ls *deb
dkms_2.2.0.3-1.1ubuntu2_all.deb  rtl8192cu-tjp-dkms_1.6_all.deb
lestat@france:/media/armand$ sudo dpkg -i *deb
[sudo] password for lestat: 
(Reading database ... 232070 files and directories currently installed.)
Preparing to replace dkms 2.2.0.3-1ubuntu3 (using dkms_2.2.0.3-1.1ubuntu2_all.deb) ...
Unpacking replacement dkms ...
Selecting previously unselected package rtl8192cu-tjp-dkms.
Unpacking rtl8192cu-tjp-dkms (from rtl8192cu-tjp-dkms_1.6_all.deb) ...
Setting up dkms (2.2.0.3-1.1ubuntu2) ...
Processing triggers for man-db ...
Setting up rtl8192cu-tjp-dkms (1.6) ...
Loading new rtl8192cu-tjp-1.6 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-33-generic
Building for architecture x86_64
Building initial module for 3.2.0-33-generic
Done.

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-33-generic/updates/dkms/

depmod........

Backing up initrd.img-3.2.0-33-generic to /boot/initrd.img-3.2.0-33-generic.old-dkms
Making new initrd.img-3.2.0-33-generic
(If next boot fails, revert to initrd.img-3.2.0-33-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
lestat@france:/media/armand$ echo "blacklist rtl8192cu" | sudo tee -a /etc/mo
modprobe.d/ modules     mono/       motd        
lestat@france:/media/armand$ echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf 
blacklist rtl8192cu
lestat@france:/media/armand$ cat /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rtl8192cu
```

Thank you for your help.

---

### Post by John_Majikes on 2014-03-11
Be careful.   I received the following from the dpkg command and now wireless device is not found.

dpkg: warning: version '*-*' has bad syntax: version number does not start with digit
It is likely that 3.8.13-bone28 belongs to a chroot's host
Building for architecture armhf
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed

---

