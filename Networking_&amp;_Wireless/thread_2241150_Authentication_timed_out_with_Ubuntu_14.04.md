---
title: "Authentication timed out with Ubuntu 14.04"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by banand on 2014-08-24
I have newly installed Ubuntu 14.04 on my laptop. Wired connection works fine but wireless connections times out. Here is the content from syslog:
```

Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) starting connection 'Wi-Fi connection 1'
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> NetworkManager state is now CONNECTING
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0/wireless): connection 'Wi-Fi connection 1' has security, and secrets exist.  No new secrets needed.
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Config: added 'ssid' value 'DDW3655F'
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Config: added 'scan_ssid' value '1'
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Config: added 'psk' value '<omitted>'
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> Config: set interface ap_scan to 1
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> (wlan0): supplicant interface state: inactive -> scanning
Aug 24 12:54:54 MegLaptop wpa_supplicant[1182]: message repeated 9 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Aug 24 12:54:54 MegLaptop wpa_supplicant[1182]: wlan0: SME: Trying to authenticate with 90:48:9a:70:c9:0e (SSID='DDW3655F' freq=2462 MHz)
Aug 24 12:54:54 MegLaptop kernel: [  407.145945] wlan0: authenticate with 90:48:9a:70:c9:0e
Aug 24 12:54:54 MegLaptop kernel: [  407.152572] wlan0: direct probe to 90:48:9a:70:c9:0e (try 1/3)
Aug 24 12:54:54 MegLaptop NetworkManager[1127]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 24 12:54:55 MegLaptop kernel: [  407.353219] wlan0: direct probe to 90:48:9a:70:c9:0e (try 2/3)
Aug 24 12:54:55 MegLaptop kernel: [  407.557416] wlan0: direct probe to 90:48:9a:70:c9:0e (try 3/3)
Aug 24 12:54:55 MegLaptop kernel: [  407.761727] wlan0: authentication with 90:48:9a:70:c9:0e timed out
Aug 24 12:54:55 MegLaptop NetworkManager[1127]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 24 12:54:55 MegLaptop wpa_supplicant[1182]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 24 12:54:55 MegLaptop NetworkManager[1127]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <info> NetworkManager state is now DISCONNECTED
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <warn> Activation (wlan0) failed for connection 'Wi-Fi connection 1'
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 24 12:55:19 MegLaptop NetworkManager[1127]: <info> (wlan0): supplicant interface state: scanning -> inactive

```

I have looked at different forums tried everything but it doesn't solve this problem. I have hp envy 15t laptop. Here is the wireless-info.txt of my box: [http://pastebin.com/raw.php?i=9bpLnatb](http://pastebin.com/raw.php?i=9bpLnatb)

My router SSID is DDW3655F. Any help in solving this would be great. I really need this working for my college project.

Thanks again

---

### Post by varunendra on 2014-08-25
Welcome to Ubuntu Forums banand!

Please try this -
```
sudo iwconfig wlan0 power off
```
Then try to connect again. If it doesn't help, try a driver parameter temporarily (it will be reset on next boot, if helps, we can make it permanent) -
```
sudo modprobe -rv iwlwifi
sudo modprobe -v iwlwifi 11n_disable=8
```

If it still fails, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Please note that it is a slightly different script that provides a little more info that may be useful.

---

### Post by banand on 2014-08-26
I tried both and it didn't work. It still times out. Here is the output of the wireless_script you requested: [http://pastebin.com/raw.php?i=JA2F9ZF4](http://pastebin.com/raw.php?i=JA2F9ZF4)

Sorry for the late reply.

---

### Post by varunendra on 2014-08-26
Please post the report with both the suggested changes applied. None of them is showing as applied in the current report.

After applying the changes, I also suggest to delete the currently saved connection profile from Network Manager, and let it create a fresh one by itself.

---

### Post by banand on 2014-08-27
Sorry about that my bad. I rebooted the machine before running the script.
Here is the script output: [http://pastebin.com/raw.php?i=absArDdh](http://pastebin.com/raw.php?i=absArDdh)

---

### Post by varunendra on 2014-08-28
Just to confirm, have you tried the wifi connection without the Ethernet cable plugged in? Network Manager may not attempt a wireless connection if a cable connection is detected. So disconnect the Ethernet cable > reboot > retry to connect to your wireless AP. Keep the Ethernet cable unplugged all this while.

If that doesn't help, try these -

1) Firstly, you seem to have been unnecessarily busy with Realtek drivers while your system has no Realtek card in it. So, please delete the conf files you have created -
```
sudo rm /etc/modprobe.d/{modprobe,rtl8188ee}.conf
```

2) We have recently discovered that the iwlwifi driver may go into an infinite connection attempt loop if the driver is reloaded on a running system. Therefore, please try the parameter in permanent mode -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot and retry to connect, and report back. We'll try other things based on your feedback.

---

### Post by banand on 2014-08-28
I tried connecting to the wifi without ethernet cable and it didnt connect. Then I tried the two commands that you had suggested and rebooted, but I still couldnt connect.

```
meghana@MegLaptop:~$ tail -f /var/log/syslog
Aug 28 01:53:49 MegLaptop wpa_supplicant[1150]: wlan0: SME: Trying to authenticate with 90:48:9a:70:c9:0e (SSID='DDW3655F' freq=2462 MHz)
Aug 28 01:53:49 MegLaptop kernel: [  202.003714] wlan0: authenticate with 90:48:9a:70:c9:0e
Aug 28 01:53:49 MegLaptop NetworkManager[1107]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 28 01:53:49 MegLaptop kernel: [  202.014444] wlan0: direct probe to 90:48:9a:70:c9:0e (try 1/3)
Aug 28 01:53:49 MegLaptop kernel: [  202.215194] wlan0: direct probe to 90:48:9a:70:c9:0e (try 2/3)
Aug 28 01:53:49 MegLaptop kernel: [  202.419351] wlan0: direct probe to 90:48:9a:70:c9:0e (try 3/3)
Aug 28 01:53:49 MegLaptop kernel: [  202.623503] wlan0: authentication with 90:48:9a:70:c9:0e timed out
Aug 28 01:53:49 MegLaptop NetworkManager[1107]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 28 01:53:49 MegLaptop wpa_supplicant[1150]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 28 01:53:49 MegLaptop NetworkManager[1107]: <info> (wlan0): supplicant interface state: disconnected -> scanning

Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <info> NetworkManager state is now DISCONNECTED
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <warn> Activation (wlan0) failed for connection 'DDW3655F'
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 28 01:54:14 MegLaptop NetworkManager[1107]: <info> (wlan0): supplicant interface state: scanning -> inactive
^C
meghana@MegLaptop:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
meghana@MegLaptop:~$
```

Please tell me what I could do next. I really appreciate the help.

---

### Post by varunendra on 2014-08-29
Assuming the new connection profile is automatically saved in Network Manager, please try saving the authentication info in it (under "Wireless Security" tab) if you haven't already.

If it is your own router, please make sure the regional setting (if it is manageable) is set to "US" (United States) since your Ubuntu is using the same regional settings. If required, we can change it in Ubuntu itself.

Again in the router, try fixing the channel bandwidth to 20 MHz if it is currently set to 20/40 MHz auto mode. Same for the channel - fix it to 1 or 11 if it is set to 'auto'.

With (or without, if you don't have admin access to the router) these changes, if required, try some other driver parameters -

**1)** Try software encryption instead of hardware, and disable wifi/bluetooth coexistence by adding "swcrypto=1" and "bt_coex_active=N" parameters to the already existing one -
```
sudo sed -i '/^options/ s/.*/& swcrypto=1 bt_coex_active=N/' /etc/modprobe.d/iwlwifi.conf
```
Like before, test the effect after a reboot.

**2)** If still no change, try completely disabling 'N' channel support by changing value '8' to '1' in "11n_disable=8" parameter -
```
sudo sed -i '/^options/ s/8/1/' /etc/modprobe.d/iwlwifi.conf
```
Again, reboot and retry.

If success, please let us know which of the steps worked, so we can possibly simplify it. If still failure, please report back with a fresh wifi script report.

---

### Post by banand on 2014-08-31
Hello,

The wifi security password is saved with the connection. Unfortunately I dont have access to the router. I tried both the changes and the wifi didnt connect after the reboots. Here is the wirelessinfo.txt

Sorry for the delay, thanks for your patience.


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

MegLaptop 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
Memory : 11949 MB
Uptime : 02:01:51 up 6 min,  4 users,  load average: 0.12, 0.22, 0.12


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
    Kernel driver in use: iwlwifi
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:1962]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 8087:07da Intel Corp. 
Bus 003 Device 005: ID 138a:0050 Validity Sensors, Inc. 
Bus 003 Device 004: ID 0eef:a103 D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         yes           no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=1 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169   | connected    | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | iwlwifi | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    DDW36113A:       Infra, <MAC C-02 DDW36113A>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    114 Ferris:      Infra, <MAC C-03 114 Ferris>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    svvFerrisPl:     Infra, <MAC C-06 svvFerrisPl>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
    carlos tzul:     Infra, <MAC C-07 carlos tzul>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    DDW361134:       Infra, <MAC C-NA DDW361134 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    NETGEAR00:       Infra, <MAC C-NA NETGEAR00 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Bill Wi, the Science Fi: Infra, <MAC C-12 Bill Wi, the Science Fi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    112 Ferris:      Infra, <MAC C-NA 112 Ferris 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    belkin.86c:      Infra, <MAC C-01 belkin.86c>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    An Even Flier Wifi: Infra, <MAC C-NA An Even Flier Wifi 2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    DDW3658B:        Infra, <MAC C-NA DDW3658B 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    An Even Flier Wifi-guest: Infra, <MAC C-NA An Even Flier Wifi-guest 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15
    FerrisPlace1182: Infra, <MAC C-NA FerrisPlace1182 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    DDW3655F:        Infra, <MAC C-NA DDW3655F 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    DDW36557:        Infra, <MAC C-09 DDW36557>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HE'SSOFLUFFYI'MGONNADIE: Infra, <MAC C-NA HE'SSOFLUFFYI'MGONNADIE 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    octocat:         Infra, <MAC C-NA octocat 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

DDW3655F             : ssid=DDW3655F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.453/0.479/0.506/0.034 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.035/0.039/0.043/0.004 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.86c>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"belkin.86c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006356c20cfb
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DDW36113A>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"DDW36113A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004c592a75a0
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 114 Ferris>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"114 Ferris"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d03a780dab
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 svvFerrisPl>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"svvFerrisPl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000378a63a5f6
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-04 svvFerrisPl>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"DDW3655F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002eab848e2e
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 svvFerrisPl>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"svvFerrisPl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000378a63d1ae
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 carlos tzul>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"carlos tzul"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000665ca18c8a
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-04 svvFerrisPl>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"DDW36557"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011cfa0d709e
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 DDW36557>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"DDW36557"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011cfa0d83a4
                    Extra: Last beacon: 236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 DDW365FB>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"DDW365FB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000298bf96185
                    Extra: Last beacon: 124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 eppistle>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"eppistle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002aa08181
                    Extra: Last beacon: 112ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Bill Wi, the Science Fi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Bill Wi, the Science Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000023a4d153a
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[hp_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
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

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0887 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1 swcrypto=1 bt_coex_active=N
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=389e600e-69c2-426e-910b-7b4b4c3134ad ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.256818] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.257063] audit: initializing netlink socket (disabled)
[    1.642804] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.835077] wmi: Mapper loaded
[   10.905494] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.905601] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
[   10.954428] Modules linked in: x86_pkg_temp_thermal intel_powerclamp coretemp hp_wmi(+) kvm_intel(-) sparse_keymap kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_hda_intel(+) aes_x86_64 snd_hda_codec lrw gf128mul snd_hwdep glue_helper ablk_helper cryptd snd_pcm snd_page_alloc joydev snd_seq_midi snd_seq_midi_event snd_rawmidi serio_raw lpc_ich(+) snd_seq snd_seq_device snd_timer btusb bluetooth i915(+) parport_pc ppdev rtsx_pci_ms iwlwifi memstick lp snd drm_kms_helper parport cfg80211 drm mei_me mei i2c_algo_bit soundcore hp_accel(+) lis3lv02d video input_polldev intel_smartconnect wmi hp_wireless mac_hid usbhid hid rtsx_pci_sdmmc psmouse ahci r8169 libahci rtsx_pci mii
[   11.204387] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   11.214449] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.214451] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.214452] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.214454] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   11.214548] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   11.233536] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.579132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.143707] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   19.151439] iwlwifi 0000:01:00.0: Radio type=0x2-0x0-0x0
[   19.394993] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   19.402657] iwlwifi 0000:01:00.0: Radio type=0x2-0x0-0x0
[   19.471693] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.472205] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.185229] wlan0: authenticate with <MAC C-04 svvFerrisPl>
[   40.196329] wlan0: send auth to <MAC C-04 svvFerrisPl> (try 1/3)
[   40.301087] wlan0: send auth to <MAC C-04 svvFerrisPl> (try 2/3)
[   40.405167] wlan0: send auth to <MAC C-04 svvFerrisPl> (try 3/3)
[   40.509231] wlan0: authentication with <MAC C-04 svvFerrisPl> timed out
[   40.656309] wlan0: authenticate with <MAC C-NA DDW3655F 1>
[   40.665013] wlan0: direct probe to <MAC C-NA DDW3655F 1> (try 1/3)
[   40.865507] wlan0: direct probe to <MAC C-NA DDW3655F 1> (try 2/3)
[   41.069706] wlan0: direct probe to <MAC C-NA DDW3655F 1> (try 3/3)
[   41.273837] wlan0: authentication with <MAC C-NA DDW3655F 1> timed out

    ======== Done ========
```

---

### Post by varunendra on 2014-09-02
I think I'm out of wits for now, have asked for help.

By the way, the kernel version has been upgraded since your above post. Is the situation still the same?

Please show us the kernel versions currently installed -
```
dpkg -l | grep linux-image
```

---

### Post by chili555 on 2014-09-02
The only thing I can think of to suggest to my colleague Varun is that 11n_disable has changed a bit:```
11n_disable:disable 11n functionality, bitmap: 1: [COLOR="#FF0000"]full, 2[/COLOR]: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
```Let's try 'full':```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change 11n_disable form whatever it is now to:```
11n_disable=2
```Everything else is unchanged. Proofread carefully, save and close the text editor. Reboot.

Better?

---

### Post by banand on 2014-09-02
Hey!

I just got access to wifi from ubuntu now!

I got some help locally to gain access to the router and it was suggested that 802.11 n mode option be set to off in the settings. I tried it and I am now connected to wifi from my ubuntu.  I have not yet tried to set 11n_disable=2, but I will change it and reboot.

Thanks a lot for your help!

---

