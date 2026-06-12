---
title: "Wifi connection drops often and does not reconnect until I reboot."
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by ravit_ on 2014-08-04
Hullo. 

I am relatively new to Ubuntu. I am on a Dell Inspiron N5110 which has a Intel Corporation Centrino Wireless-N 1030 card. 
As the title suggests my connection drops pretty often and it does not reconnect to the Wifi Network until I reboot. I thought the problem was with the connection but it works rock solid on my Android phone. 
I know this has been asked before but none of those solutions were really clear to me.

Would appreciate some direction. 
I've already turned the power saving for the card off.

---

### Post by WinEunuchs2Unix on 2014-08-05
It might be the intel firmware but more information is needed and I'm not smart enough to ask the right questions.  Two things might happen:

1) Someone named Varun will ask you to run this script: [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
2) Some nice forum moderator will move this thread out of Hardware and into Networking & Wireless section.

---

### Post by varunendra on 2014-08-05
> **WinEunuchs2Unix said:**
> Two things might happen:

1) Someone named Varun will ask you to run this script: [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
:lolflag:

Am I so infamous for asking that?

**@ravit_**,
Please do what 'WinEunuchs2Unix' (not me ;)) suggested. That is, follow that link and post back the script report mentioned there.

As for moving the thread to the suitable section (Networking & Wireless), you could help it by reporting it using "Report Post" button below every post, in case you didn't already know it. Oh, and reporting also earns you a bean :p

So.. unless it gets moved before I can report it, I'm on my way to earn an extra bean :-\"

---

### Post by QIII on 2014-08-05
And ... moved.

---

### Post by ravit_ on 2014-08-05
Thanks for the reply and sorry for not putting this in the right category. 

Here is what that script returned. 

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


TARDIS 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 3860 MB
Uptime : 21:24:12 up  5:47,  2 users,  load average: 1.29, 0.98, 0.66




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:04b0]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"EACCESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 54:3D:37:12:A3:58   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:183  Invalid misc:12728   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwldvm                232285  0 
mac80211              630653  1 iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 dell_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
==================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID   | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
==================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [EACCESS] | 802.11 WiFi | iwlwifi | connected   | yes     | 6 Mb/s    | WEP/WPA/WPA2 | BC:77:37:81:48:A9


    EACCESS:         Infra, 8C:0C:90:07:B8:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    EACCESS:         Infra, 54:3D:37:19:2D:A8, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA
    *EACCESS:        Infra, 54:3D:37:12:A3:58, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA
    EACCESS:         Infra, 8C:0C:90:05:2B:78, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    EACCESS:         Infra, 8C:0C:90:08:13:F8, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA
    EACCESS:         Infra, 8C:0C:90:07:B2:18, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    EACCESS:         Infra, 54:3D:37:12:6A:88, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA
    EACCESS:         Infra, 54:3D:37:12:0A:08, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA
    TU:              Infra, 54:3D:37:59:08:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    EACCESS:         Infra, 54:3D:37:99:08:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    EACCESS:         Infra, 8C:0C:90:07:51:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    EACCESS:         Infra, 8C:0C:90:07:BE:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    EACCESS:         Infra, 8C:0C:90:07:BC:68, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    EACCESS:         Infra, 54:3D:37:19:A8:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    EACCESS:         Infra, 8C:0C:90:06:A0:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    EACCESS:         Infra, 8C:0C:90:08:11:08, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA


    Address:         172.31.121.224
    Prefix:          22 (255.255.252.0)
    Gateway:         172.31.120.2
    DNS:             172.31.1.8
    DNS:             172.31.1.7
    DNS:             172.31.1.6
------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0             | Wired       | r8169   | unavailable | no      |           |              | 78:2B:CB:ED:D5:8B
------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




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


no-auto-default=78:2B:CB:ED:D5:8B,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
```

---

### Post by WinEunuchs2Unix on 2014-08-05
@Varun... yup you're world famous:lolflag:

---

### Post by varunendra on 2014-08-08
> **WinEunuchs2Unix said:**
> @Varun... yup you're world famous:lolflag:
Hmm.. Ignoring that 'lol-flag', I think it's time now to start negotiating with the admins/canonical to start paying me then. [-(


**@ravit_,**

Sorry for not being able to respond earlier (the reason explained [here]("http://ubuntuforums.org/showpost.php?p=13093195")), but the report you posted is incomplete. However, it still gives an important clue -
> **ravit_ said:**
> ```
iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"EACCESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 54:3D:37:12:A3:58   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:183  Invalid misc:12728   Missed beacon:0
```

Try the easy fix first -
```
sudo iwconfig wlan0 power off
```
Then keep an eye on the outputs of 'iwconfig' to make sure the 'Power Management' remains "**off**".

If it turns back on automatically after sometime, try disabling the default power management script for wifi by creating a blank file "wireless" in /etc/pm/power.d directory -
```
sudo touch /etc/pm/power.d/wireless
```
Then run the "iwconfig wlan0 power off" command again and keep watching the output of "iwconfig" again to make sure it remains off.

If it still turns back on, try forcing the "power off" command on it by putting the command in the "wireless" file created above, and making it executable -
```
echo "/sbin/iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```

Then turn the power management "off" again using the iwconfig command (if required), and observe the output of 'iwconfig' again.

If none of these can keep the power management off, or if turning it off doesn't help, please run the script again and post back its full report this time. A sample of a complete report : [http://ubuntuforums.org/showthread.php?t=2237440&p=13090906#post13090906](http://ubuntuforums.org/showthread.php?t=2237440&p=13090906#post13090906)

---

