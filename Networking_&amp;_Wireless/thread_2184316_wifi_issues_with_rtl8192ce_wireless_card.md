---
title: "wifi issues with rtl8192ce wireless card"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by beckeswins on 2013-10-28
Hello all, I'm less than 24 hours into Linux/Ubuntu.  I'm on 12.04 LTS. 
 
I can connect initially but within 1-20 minutes (varies) I am no longer able to view new web pages although I seem to still be connected to the router.

I ran a few things that it seems likely will be asked of me having looked at other similar posts.  Please let me know if you need anything else.

nathaniel@nathaniel-Satellite-C875:~$ modinfo rtl8192ce
filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B41EC2D43683C181DF50FB6
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

-----------------------------------------------------------------------------------------------------------------------------------------


nathaniel@nathaniel-Satellite-C875:~$ lsmod | grep rtl
rtl8192ce              58733  0 
rtl8192c_common        49561  1 rtl8192ce
rtlwifi                81225  1 rtl8192ce
mac80211              630977  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              525326  2 rtlwifi,mac80211

------------------------------------------------------------------------------------------------------------------------------------------


nathaniel@nathaniel-Satellite-C875:~$ dmesg | grep rtl 
[    8.417968] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[    8.536512] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.536688] rtlwifi: wireless switch is on
[   66.194356] rtlwifi: wireless switch is on

---------------------------------------------------------------------------------------------------------------------------


nathaniel@nathaniel-Satellite-C875:~$ dmesg | grep -e rtl -e 80211 -e wlan
[    7.568257] cfg80211: Calling CRDA to update world regulatory domain
[    8.417968] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[    8.536512] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.536688] rtlwifi: wireless switch is on
[   15.922653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.922919] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.918113] wlan0: authenticate with 5c:57:1a:d7:e2:70
[   20.949695] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[   21.124423] wlan0: authenticated
[   21.125057] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[   21.137780] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=3)
[   21.137944] wlan0: associated
[   21.137957] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.948146] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[   61.984778] cfg80211: Calling CRDA for country: EC
[   66.194356] rtlwifi: wireless switch is on
[   68.867214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   72.213557] wlan0: authenticate with 5c:57:1a:d7:e2:70
[   72.245459] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[   72.247442] wlan0: authenticated
[   72.249150] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[   72.260906] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[   72.261069] wlan0: associated
[   72.261079] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  264.765119] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[  264.807585] cfg80211: Calling CRDA for country: US
[  272.105040] wlan0: authenticate with 5c:57:1a:d7:e2:70
[  272.129333] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[  272.134530] wlan0: authenticated
[  272.136727] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[  272.146802] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[  272.146965] wlan0: associated
[  525.021020] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[  525.059848] cfg80211: Calling CRDA to update world regulatory domain
[  532.345262] wlan0: authenticate with 5c:57:1a:d7:e2:70
[  532.374166] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[  532.384738] wlan0: authenticated
[  532.385642] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[  532.397310] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[  532.397492] wlan0: associated
[ 1216.554482] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[ 1216.592606] cfg80211: Calling CRDA for country: US
[ 1223.882736] wlan0: authenticate with 5c:57:1a:d7:e2:70
[ 1223.910563] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[ 1223.912130] wlan0: authenticated
[ 1223.914939] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[ 1223.927597] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[ 1223.927763] wlan0: associated
[ 1454.312051] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[ 1454.349503] cfg80211: Calling CRDA to update world regulatory domain
[ 1461.644094] wlan0: authenticate with 5c:57:1a:d7:e2:70
[ 1461.671809] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[ 1461.673382] wlan0: authenticated
[ 1461.675268] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[ 1461.684063] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[ 1461.684244] wlan0: associated
[35484.428990] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[35484.468906] cfg80211: Calling CRDA to update world regulatory domain
[35491.759011] wlan0: authenticate with 5c:57:1a:d7:e2:70
[35491.780024] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[35491.782198] wlan0: authenticated
[35491.785601] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[35491.794285] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[35491.794449] wlan0: associated
[37449.699230] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[37449.736487] cfg80211: Calling CRDA for country: US
[37457.013415] wlan0: authenticate with 5c:57:1a:d7:e2:70
[37457.042859] wlan0: direct probe to 5c:57:1a:d7:e2:70 (try 1/3)
[37457.246099] wlan0: direct probe to 5c:57:1a:d7:e2:70 (try 2/3)
[37457.449840] wlan0: direct probe to 5c:57:1a:d7:e2:70 (try 3/3)
[37457.653569] wlan0: authentication with 5c:57:1a:d7:e2:70 timed out
[37463.950874] wlan0: authenticate with 5c:57:1a:d7:e2:70
[37463.981838] wlan0: direct probe to 5c:57:1a:d7:e2:70 (try 1/3)
[37464.185118] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 2/3)
[37464.190428] wlan0: authenticated
[37464.193301] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[37464.207439] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[37464.207615] wlan0: associated
[37840.014512] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[37840.056904] cfg80211: Calling CRDA to update world regulatory domain
[37841.054674] wlan0: authenticate with 5c:57:1a:d7:e2:70
[37841.086562] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[37841.088008] wlan0: authenticated
[37841.090148] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[37841.098872] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[37841.099053] wlan0: associated
[38211.316937] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[38211.363949] cfg80211: Calling CRDA to update world regulatory domain
[38212.346797] wlan0: authenticate with 5c:57:1a:d7:e2:70
[38212.378593] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[38212.581951] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 2/3)
[38212.785688] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 3/3)
[38212.989440] wlan0: authentication with 5c:57:1a:d7:e2:70 timed out
[38218.936084] wlan0: authenticate with 5c:57:1a:d7:e2:70
[38218.966382] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[38218.967921] wlan0: authenticated
[38218.969692] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[38218.978328] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[38218.978481] wlan0: associated
[38526.055464] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[38526.097918] cfg80211: Calling CRDA for country: US
[38533.389005] wlan0: authenticate with 5c:57:1a:d7:e2:70
[38533.413065] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[38533.415046] wlan0: authenticated
[38533.415903] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[38533.426599] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[38533.426760] wlan0: associated
[38696.325529] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[38700.082256] cfg80211: Calling CRDA to update world regulatory domain
[38707.355454] wlan0: authenticate with 5c:57:1a:d7:e2:70
[38707.386868] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[38707.582609] wlan0: authenticated
[38707.586215] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[38707.618877] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[38707.619059] wlan0: associated
[38986.465625] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[38986.513453] cfg80211: Calling CRDA for country: US
[38993.756647] wlan0: authenticate with 5c:57:1a:d7:e2:70
[38993.779645] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[38993.784645] wlan0: authenticated
[38993.787150] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[38993.801117] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[38993.801302] wlan0: associated
[39081.401645] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[39081.454816] cfg80211: Calling CRDA to update world regulatory domain
[39088.734718] wlan0: authenticate with 5c:57:1a:d7:e2:70
[39088.761295] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[39088.767490] wlan0: authenticated
[39088.768840] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[39088.777552] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[39088.777716] wlan0: associated
[39092.028037] wlan0: deauthenticated from 5c:57:1a:d7:e2:70 (Reason: 15)
[39092.064711] cfg80211: Calling CRDA to update world regulatory domain
[39093.447683] wlan0: authenticate with 5c:57:1a:d7:e2:70
[39093.479187] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[39093.484799] wlan0: authenticated
[39093.486795] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[39093.495490] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[39093.495659] wlan0: associated
[39897.730449] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[39897.793459] cfg80211: Calling CRDA for country: US
[39905.060679] wlan0: authenticate with 5c:57:1a:d7:e2:70
[39905.086931] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[39905.089198] wlan0: authenticated
[39905.090500] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[39905.104216] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[39905.104380] wlan0: associated
[40366.542055] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[40366.589901] cfg80211: Calling CRDA to update world regulatory domain
[40367.545515] wlan0: authenticate with 5c:57:1a:d7:e2:70
[40367.577591] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[40367.580260] wlan0: authenticated
[40367.581182] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[40367.589856] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[40367.590031] wlan0: associated
[42816.822883] wlan0: deauthenticating from 5c:57:1a:d7:e2:70 by local choice (reason=3)
[42816.830956] cfg80211: Calling CRDA for country: US
[42817.418361] wlan0: authenticate with 5c:57:1a:d7:e2:70
[42817.449996] wlan0: send auth to 5c:57:1a:d7:e2:70 (try 1/3)
[42817.453152] wlan0: authenticated
[42817.453443] wlan0: associate with 5c:57:1a:d7:e2:70 (try 1/3)
[42817.462272] wlan0: RX AssocResp from 5c:57:1a:d7:e2:70 (capab=0xc11 status=0 aid=2)
[42817.462457] wlan0: associated

---------------------------------------------------------------------------------------------------------------------------------------------------


nathaniel@nathaniel-Satellite-C875:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        70:54:D2:5F:F8:5E


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off




- Device: wlan0  [HOME-E272] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        24:EC:99:EA:01:F1


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *HOME-E272:      Infra, 5C:57:1A:D7:E2:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2
    Tonya:           Infra, 00:1D:D4:D8:D6:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    HOME-0EA2:       Infra, 00:1D:D3:4F:0E:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    BlueSkyWireless: Infra, 00:25:3C:C4:ED:51, Freq 2447 MHz, Rate 54 Mb/s, Strength 67 WPA
    2WIRE373:        Infra, 98:2C:BE:06:14:49, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA
    Owner24:         Infra, 00:26:F2:FE:EE:98, Freq 2422 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    2WIRE226:        Infra, 3C:EA:4F:79:34:29, Freq 2422 MHz, Rate 54 Mb/s, Strength 72 WPA
    ATT376:          Infra, B8:16:19:3F:C6:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    TriqWave:        Infra, A0:21:B7:A1:3A:26, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    davis567:        Infra, F8:ED:A5:AA:68:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    veganaisse_EXT:  Infra, 20:E5:2A:57:11:0B, Freq 2412 MHz, Rate 54 Mb/s, Strength 65
    HPC410a.464F20:  Ad-Hoc, 02:26:26:91:94:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
    Brenda network:  Infra, 84:C9:B2:54:92:AD, Freq 2432 MHz, Rate 54 Mb/s, Strength 67 WPA
    2WIRE854:        Infra, 60:C3:97:42:1F:51, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76

This run of nm-tool was while I had no use-able internet connection although it appears I'm connected to the router in some way.

Any help would be greatly appreciated!!!

[COLOR=#000000]@varunendra
@chili555 - you two seem to really know what you're doing with these issues.  Hope you can help me!

Also, although I had some difficulty getting 12.04 to install (had issues with grub/boot files) I am willing to switch to 13 if it will solve this issue.  Regarding 13 and the 9 month support- does that mean I will have to install a new version of Ubuntu in 9 months to continue getting security/other updates?  Or will 13 then just become the new LTS?  I know that's a very basic question but hey, I'm a Linux noob!  :)[/COLOR]

---

### Post by varunendra on 2013-10-29
Let me first Welcome you to the forums beckeswins ! :)

Next, please edit your above post to enclose the output part within 'Code' tags. It preserves the code's formatting, and make the post cleaner & more readable. Please follow the "Using Code Tags" link in my signature to see how to use it for existing as well as new posts.

Further next, (Ahem!) you know me only because the real experts seem to be too busy these days, while I have all the time in the world to make like a thousand posts per day. :-\"

Dr. chili555, oh yeah, he's the real Guru who I usually go to when a problem makes me cry, and he is always able to comfort me with his solution candies. :P


Finally towards the problem -
> **beckeswins said:**
> 
  ```
Wireless Access Points (* = current AP)
    *HOME-E272:      Infra, 5C:57:1A:D7:E2:70, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
```
This is the most dreaded encryption type that you are using. While it works, it is highly recommended to use pure WPA2-PSK (AES/CCMP) encryption in the router.
Please change to that, reboot the router, then follow the instructions in this post to try a few parameters with the driver : [http://ubuntuforums.org/showthread.php?t=2179279&p=12813120#post12813120](http://ubuntuforums.org/showthread.php?t=2179279&p=12813120#post12813120) (read the following posts too to get an idea of what each parameter does and how to make it permanent)

More detailed steps to try them temporarily : [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912)

If any of them seems to make the connection stable, make it permanent as suggested in the first linked thread.

If none of them helps, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. And don't forget to use the 'Code' tags this time. :)

---

