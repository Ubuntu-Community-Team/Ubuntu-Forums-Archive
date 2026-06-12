---
title: "Intel Corporation Wireless-AC 9560 failing"
date: 2019-09-10
forum: Networking &amp; Wireless
---

### Post by gaymer2 on 2019-09-10
ok so my laptop has Intel Corporation Wireless-AC 9560 and it used to work fine but recently it starts to connect poorly. I've had this laptop for about a year now and when I first got it I was getting 3-10ms in games like quake(on LAN server) but recently I've been getting somewhere around 65 - 999ms. no huge changes were made to the router, and I didn't change rooms. at home I can play a game smoothly for about 5 minutes until my ping spikes and watching a youtube video in 720p starts to become impossible. I'm wondering if there is a driver fix to this and if not what wifi adapter would you forum people recommend I buy

---

### Post by chili555 on 2019-09-11
Let's have a look at the router setup. Please run:```
sudo iwlist scan
```Show only your router and redact the MAC address like this:```

wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]XXXXX[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```As for different devices, I like Intel and I think your 9560 is a great choice!

---

### Post by gaymer2 on 2019-09-11
lo        Interface doesn't support scanning.

wlp0s20f3  Interface doesn't support scanning.

enp6s0f1  Interface doesn't support scanning.

---

### Post by chili555 on 2019-09-11
> wlp0s20f3 Interface doesn't support scanning.Very strange. Let's dig deeper:```
dmesg | grep -e iwl -e wlp
iwconfig
```

---

### Post by jeremy31 on 2019-09-11
I have heard some issues with 4.15.0-60.  Is that the kernel you are using? ```
uname -r
```

---

### Post by gaymer2 on 2019-09-11
> **jeremy31 said:**
> I have heard some issues with 4.15.0-60.  Is that the kernel you are using? ```
uname -r
```

no im running 4.20.8

---

### Post by gaymer2 on 2019-09-11
> **chili555 said:**
> Very strange. Let's dig deeper:```
dmesg | grep -e iwl -e wlp
iwconfig
```

```
[    3.928410] Loading modules backported from iwlwifi
[    3.928410] iwlwifi-stack-public:master:8042:654c426c
[    3.987191] iwlwifi 0000:00:14.3: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    3.989904] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-46.ucode failed with error -2
[    3.989921] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-45.ucode failed with error -2
[    3.992406] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-44.ucode failed with error -2
[    4.010049] iwlwifi 0000:00:14.3: loaded firmware version 43.95eb4e97.0 op_mode iwlmvm
[    4.032157] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    4.121852] iwlwifi 0000:00:14.3: base HW address: 0c:54:15:c3:8d:4f
[    4.273024] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.275021] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[    5.239726] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    5.436933] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
[    5.437660] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    5.513854] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    8.920341] wlp0s20f3: authenticate with cc:b2:55:61:e9:5c
[    8.927241] wlp0s20f3: send auth to cc:b2:55:61:e9:5c (try 1/3)
[    8.965957] wlp0s20f3: authenticated
[    8.966821] wlp0s20f3: associate with cc:b2:55:61:e9:5c (try 1/3)
[    8.971265] wlp0s20f3: RX AssocResp from cc:b2:55:61:e9:5c (capab=0x431 status=0 aid=5)
[    8.976106] wlp0s20f3: associated
[    8.996455] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s20f3: link becomes ready
[  189.904154] wlp0s20f3: AP cc:b2:55:61:e9:5c changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
[ 2350.059610] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.059631] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.066201] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.077784] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.085899] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.093297] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b
[ 2350.101502] iwlwifi 0000:00:14.3: Unhandled alg: 0x71b


```

iwconfig
```
lo        no wireless extensions.

wlp0s20f3  no wireless extensions.

enp6s0f1  no wireless extensions.
```

---

### Post by chili555 on 2019-09-11
The more I read the less I know!> 
iwlwifi 0000:00:14.3: Unhandled alg: 0x71b


This bug report suggests that the issue may be in the router: [https://bugzilla.kernel.org/show_bug.cgi?id=201053](https://bugzilla.kernel.org/show_bug.cgi?id=201053) This line in dmesg seems to support the theory that the router is a factor:> 
wlp0s20f3: AP cc:b2:55:61:e9:5c changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
Here are my usual suggestions for Intel devices.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot the router and the computer and show us a new:```
dmesg | grep -e wlp -e iwl
```> no im running 4.20.8Which flavor of Ubuntu is that?

---

### Post by gaymer2 on 2019-09-11
ok uh switching to 2.4g fixed everything instantly. thanks a lot for your help!

---

### Post by chili555 on 2019-09-11
Awesome! Glad it's working as expected.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

