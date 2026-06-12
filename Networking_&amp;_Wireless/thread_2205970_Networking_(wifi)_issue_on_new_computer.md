---
title: "Networking (wifi) issue on new computer"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by Zack_Newsham on 2014-02-16
Hi All, I asked this question on askubuntu.com a few days ago ([http://askubuntu.com/questions/420927/ubuntu-13-10-internet-problems-also-with-12-04-lts](http://askubuntu.com/questions/420927/ubuntu-13-10-internet-problems-also-with-12-04-lts)), but got no responses so I thought I'd try here. I built a new computer recently, and while almost everything works, networking does not. I cannot get a wired, or wireless connection - though interestingly I can connect by plugging in my iPhone. 

I moved house yesterday and no longer have wired access - so I am putting that on hold for now. This post is about the wifi. 

My wifi card is: TP-link WDN4800

running dmesg gives:

```
[  835.322749] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  836.295689] wlan0: authenticate with 08:76:ff:c8:67:d0
[  836.303592] wlan0: direct probe to 08:76:ff:c8:67:d0 (try 1/3)
[  836.507237] wlan0: direct probe to 08:76:ff:c8:67:d0 (try 2/3)
[  836.711325] wlan0: direct probe to 08:76:ff:c8:67:d0 (try 3/3)
[  836.915507] wlan0: authentication with 08:76:ff:c8:67:d0 timed out
[  837.344859] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  837.516237] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.580301] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.592172] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  837.592205] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  837.656339] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.668245] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  837.668280] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  837.732029] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.743565] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  837.743587] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  837.808400] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.820465] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00024e00
[  837.820501] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  837.884470] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.896318] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  837.896354] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  837.960517] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  837.972402] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  837.972436] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  838.036558] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  838.100608] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  838.112503] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026e00
[  838.112533] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  838.176699] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  838.188617] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  838.188646] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  838.252692] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  838.264553] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  838.264585] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.309136] wlan0: deauthenticating from 08:76:ff:c8:67:d0 by local choice (reason=3)
[  841.478857] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.490702] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  841.490737] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.558863] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.570786] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  841.570823] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.634987] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.646875] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  841.646910] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.710992] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.774983] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.786866] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  841.786896] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.851053] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.862974] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  841.863006] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  841.927042] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  841.938943] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026e00
[  841.938974] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  842.003202] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  842.067251] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  842.079114] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  842.079147] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  842.143292] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  842.155151] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  842.155182] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  842.219331] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  842.231204] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  842.231232] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
```
repeated several times. I have looked around trying different solutions, but none have currently worked. Needless to say it is annoying having to leave my phone plugged in to get internet access on this machine. Does anyone have any idea how to fix this?

Thanks in advance.

---

### Post by varunendra on 2014-02-16
Welcome to Ubuntu Forums Zack_Newsham !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Zack_Newsham on 2014-02-16
I probably should have mentioned before, that I see the wireless networks and am even prompted for my password (repeatedly at ~5 minute intervals) but I never get a connection. eth0 below is my iPhone.

[http://pastebin.ubuntu.com/6947047/](http://pastebin.ubuntu.com/6947047/)

---

### Post by Bucky Ball on 2014-02-17
Try opening /etc/network/interfaces with:
```

sudo nano /etc/network/interfaces
```

and change this:

```
auto lo
iface lo inet loopback
iface **eth0** inet dhcp

```
... to this:

```
auto lo
iface lo inet loopback
iface **wlan0** inet dhcp
```

Reboot. It may or may not work, but a quick shot in the dark. If it doesn't, change it back.

---

### Post by Zack_Newsham on 2014-02-17
> **Bucky Ball said:**
> Try opening /etc/network/interfaces with:
```

sudo nano /etc/network/interfaces
```

and change this:

```
auto lo
iface lo inet loopback
iface **eth0** inet dhcp

```
... to this:

```
auto lo
iface lo inet loopback
iface **wlan0** inet dhcp
```

Reboot. It may or may not work, but a quick shot in the dark. If it doesn't, change it back.

Thanks for trying, but it had no affect.

---

### Post by wildmanne39 on 2014-02-17
In the /etc/network/interfaces file
```
iface eth0 inet dhcp
```
needs to be removed, the file should only have:
```
auto lo
iface lo inet loopback
```
then reboot.

Also run these commands one at a time:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
In your router change the encryption to just wpa2 AES CCSM if you have that option.
Thanks

---

### Post by Zack_Newsham on 2014-02-17
> **Wild Man said:**
> In the /etc/network/interfaces file
```
iface eth0 inet dhcp
```
needs to be removed, the file should only have:
```
auto lo
iface lo inet loopback
```
then reboot.

Also run these commands one at a time:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
In your router change the encryption to just wpa2 AES CCSM if you have that option.
Thanks

Thanks, but no luck - also I can't change wifi settings (I dont control it).

---

### Post by wildmanne39 on 2014-02-17
While your computer was off did you unplug your iphone? you can not use wifi and iphone at the same time.

Shutdown then unplug iphone, boot up, if it does not connect post a new wireless file?

Are you in Australia?
Thanks

---

### Post by Zack_Newsham on 2014-02-17
Still nothing unfortunately, no - I'm in Canada.

[http://pastebin.ubuntu.com/6947405](http://pastebin.ubuntu.com/6947405)

---

### Post by Bucky Ball on 2014-02-17
Well, that is very odd, because I thought you were one of my country people. Your wireless output shows this:

```
country AU:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 23)
	(5250 - 5330 @ 40), (3, 23), DFS
	(5735 - 5835 @ 40), (3, 30)
```

According to your system, at least wifi, you're in Aus. That is why Wild Man assumed as much ... ;)

---

### Post by varunendra on 2014-02-17
> **Bucky Ball said:**
> Well, that is very odd, because I thought you were one of my country people. Your wireless output shows this:

```
country AU:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (3, 23)
	(5250 - 5330 @ 40), (3, 23), DFS
	(5735 - 5835 @ 40), (3, 30)
```

According to your system, at least wifi, you're in Aus. That is why Wild Man assumed as much ... ;)

> **Zack_Newsham said:**
> Still nothing unfortunately, no - I'm in Canada.

Hmm.. let's take you to home then, and see if the wireless like the weather there.

Please run the following code in a terminal -
```
sudo sed -i 's:^exit 0:iw reg set CA\n&:' /etc/rc.local
```
This will add a line "**iw reg set CA**" in your **/etc/rc.local** file just above the last line that should always be "**exit 0**". It is a command to manually change the regdomain settings, and adding it to that file will make it run automatically since next boot.

There is some difference in regulatory domain settings between Canada and Australia. The regdomain settings for Canada are -
```
country CA:
        (2402.000 - 2472.000 @ 40.000), (3.00, 27.00)
        (5170.000 - 5250.000 @ 40.000), (3.00, 17.00)
        (5250.000 - 5330.000 @ 40.000), (3.00, 20.00), DFS
        (5490.000 - 5710.000 @ 40.000), (3.00, 20.00), DFS
        (5735.000 - 5835.000 @ 40.000), (3.00, 30.00)
```
The zeros in the decimal places don't matter (they are just because of where I copied it from), but the frequency difference may. So let's see if the change does the trick.

---

### Post by Zack_Newsham on 2014-02-17
Alas, nothing :( I checked the output and it was changed as above, but the wifi still didnt work :(

---

### Post by varunendra on 2014-02-17
Hmm.. I was a little hopeful, but not surprised with the "no improvement" result.

How about trying a newer driver? A backported one that has been reported by a few users to be working better.

Before trying that, make sure the basic requirements to compile a module are installed -
```
sudo apt-get install linux-headers-generic build-essential
```

Then,

[indent]**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)
**2)** Right-click the downloaded package > Extract here..
**3)** Assuming the extracted directory is in the "Downloads" folder in you Home, run the following commands in a terminal to compile and install the newer driver -
```
cd Downloads/backports-3.12.8-1
make defconfig-ath9k
make
sudo make install
```
**4)** Reboot, or manually reload the driver -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```[/indent]
Is everyone - the wifi, the router...., the user.. happy now?

---

### Post by Zack_Newsham on 2014-02-18
Still no luck :( perhaps a hardware fault?

---

### Post by varunendra on 2014-02-19
> **Zack_Newsham said:**
> perhaps a hardware fault?

We don't have any such indication from the wireless reports you posted. All those "Fail" messages you may have noticed look more like a software/driver failure.

Although this driver that I suggested has been reported to be working, yesterday Wild Man had success with the latest one also ([this post]("http://ubuntuforums.org/showthread.php?t=2206138&p=12932301#post12932301")). So please try the same installation procedure as in my previous post with the latest backports package from the same page and see if it works any better.

If not, please run the script again and give us its latest report with the backported driver installed.

---

### Post by Zack_Newsham on 2014-02-19
Still nothing :(
```


*************** info trace ***************

***** uname -a *****

Linux zacknewsham-server 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168
--
07:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:3112]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 008 Device 002: ID 2109:3431  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country AU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (3, 23)
    (5250 - 5330 @ 40), (3, 23), DFS
    (5735 - 5835 @ 40), (3, 30)

***** lsmod *****

ath9k                 105813  0 
mac80211              543473  1 ath9k
ath9k_common           13550  1 ath9k
ath9k_hw              436973  2 ath9k,ath9k_common
ath                    28657  3 ath9k,ath9k_common,ath9k_hw
cfg80211              495728  3 ath9k,mac80211,ath
compat                 13893  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: wlan0  [HOMELAND] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BronzeCheetah:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    BELL420:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Home2:           Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    OURHOME:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    Taurus-guest:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    wen:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    HOMELAND:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=true

***** interfaces *****

auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"BELL420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001eb79e861aa
                    Extra: Last beacon: 19724ms ago
                    IE: Unknown: 000742454C4C343230
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706434120010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8806C2E85F88593103C000101
                    IE: Unknown: 0505000100DC1B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010015127A
                    IE: Unknown: DD07000C4300000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"BronzeCheetah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f7a238186
                    Extra: Last beacon: 1604ms ago
                    IE: Unknown: 000D42726F6E7A6543686565746168
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f7a2389ac
                    Extra: Last beacon: 1600ms ago
                    IE: Unknown: 000A00000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"OURHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b993ce71f2
                    Extra: Last beacon: 1144ms ago
                    IE: Unknown: 00074F5552484F4D45
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0712465220010D14010D1401071408060A010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400
                    IE: Unknown: 050400010000
          Cell 05 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Home2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000578c3e6280
                    Extra: Last beacon: 8760ms ago
                    IE: Unknown: 0005486F6D6532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD270050F204104A00011010440001021047001041CCE07E3C0DA07F3AA420543A61C983103C000103
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dd7fdac32
                    Extra: Last beacon: 26532ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0505000E127A
                    IE: Unknown: DD07000C4304000000
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"HOMELAND"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003537dd9307f
                    Extra: Last beacon: 1584ms ago
                    IE: Unknown: 0008484F4D454C414E44
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F94445242EBA6103C000101
                    IE: Unknown: DD050050F20500
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010041127A
                    IE: Unknown: DD1E00904C33EE1113FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist r8169
blacklist b43

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A7623E4A23D648C3DACFE05
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     F1855C93DA7170B2E624BB2
depends:        compat,ath,ath9k_hw
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
version:        backported from Linux (v3.13.2-0-gfd82174) using backports v3.13.2-1-0-gaef13bc
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     52239603B4654F16DA42B38
depends:        compat,ath
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0BE5FC7C1EAF38AFA84BEDB
depends:        cfg80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.0/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.391511] ath: EEPROM regdomain: 0x21
[    2.391515] ath: EEPROM indicates we should expect a direct regpair map
[    2.391517] ath: Country alpha2 being used: AU
[    2.391518] ath: Regpair used: 0x21
[    2.652215] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  616.051840] ath9k: ath9k: Driver unloaded
[  619.842966] ath: EEPROM regdomain: 0x21
[  619.842968] ath: EEPROM indicates we should expect a direct regpair map
[  619.842970] ath: Country alpha2 being used: AU
[  619.842971] ath: Regpair used: 0x21
[  619.856793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  622.438046] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  625.394469] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.451276] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.506177] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.562583] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.618630] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.689079] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.742751] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.800788] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.854683] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.926128] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  625.938043] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  625.938068] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  626.006149] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.074236] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.142253] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.154137] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  626.154163] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  626.222297] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.290359] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.358381] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.426420] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.926769] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  626.994824] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  627.063047] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  627.130915] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  627.191486] wlan0: authenticate with <MAC address removed>
[  627.199004] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  627.215579] wlan0: direct probe to <MAC address removed> (try 1/3)
[  627.223858] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  627.418749] wlan0: direct probe to <MAC address removed> (try 2/3)
[  627.622900] wlan0: direct probe to <MAC address removed> (try 3/3)
[  627.827032] wlan0: authentication with <MAC address removed> timed out
[  627.843335] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.019531] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.031400] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026400
[  628.031425] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.099506] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.171569] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.239632] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.251511] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  628.251534] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.319701] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.391737] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.459771] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.471541] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  628.471560] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.539829] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.551744] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00004400
[  628.551769] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.619917] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.687962] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.699832] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  628.699861] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.771917] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.840056] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.908109] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  628.920009] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  628.920038] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  628.987888] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.056243] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.124240] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.192315] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.692607] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.760676] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.828710] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.896703] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  629.964813] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  632.219519] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  632.790606] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  632.858704] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  632.926762] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  632.994779] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.062853] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.074734] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  633.074760] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  633.142896] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.154778] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  633.154807] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  633.222641] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.290968] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.359053] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.371029] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  633.371059] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  633.439337] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.507062] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.518914] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  633.518945] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  633.587201] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.655242] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.723287] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.791394] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.859323] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  633.927405] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.427753] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.495825] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.563856] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.631922] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.692274] wlan0: authenticate with <MAC address removed>
[  634.699981] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  634.716396] wlan0: direct probe to <MAC address removed> (try 1/3)
[  634.919681] wlan0: direct probe to <MAC address removed> (try 2/3)
[  635.123819] wlan0: direct probe to <MAC address removed> (try 3/3)
[  635.327944] wlan0: authentication with <MAC address removed> timed out
[  635.356230] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.532475] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.600377] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.668589] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.736627] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.804729] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.816625] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  635.816659] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  635.884718] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  635.952776] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.020771] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.032688] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  636.032718] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  636.100874] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.168930] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.180807] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  636.180835] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  636.248955] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.317004] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.385081] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.453099] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.521350] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.589213] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  636.657278] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  637.157607] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  637.225659] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  637.293674] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  637.361671] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  637.429754] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  639.722177] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  640.295657] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.363670] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.431728] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.499816] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.567476] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.579065] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  640.579081] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  640.647792] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.659703] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  640.659728] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  640.727931] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.739801] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  640.739825] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  640.808006] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.876071] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.887961] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  640.887987] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  640.956098] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  640.967978] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  640.968004] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  641.036128] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.104179] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.116041] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  641.116067] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  641.184282] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.196192] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  641.196218] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  641.264258] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.332325] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.400325] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.468358] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  641.968750] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  642.036810] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  642.104868] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  642.172822] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  642.233242] wlan0: authenticate with <MAC address removed>
[  642.240982] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  642.257515] wlan0: direct probe to <MAC address removed> (try 1/3)
[  642.460686] wlan0: direct probe to <MAC address removed> (try 2/3)
[  642.668771] wlan0: direct probe to <MAC address removed> (try 3/3)
[  642.876973] wlan0: authentication with <MAC address removed> timed out
[  642.909324] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.085495] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.097376] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  643.097404] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.165547] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.233609] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.301660] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.313564] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  643.313591] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.381620] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.449739] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.517730] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.529596] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  643.529622] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.597811] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.609679] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  643.609707] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.677874] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.745959] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.757838] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  643.757862] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.825948] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.837811] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  643.837839] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  643.906070] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.974053] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  643.985944] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  643.985968] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  644.054133] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.122180] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.190124] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.258275] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.758604] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.826680] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.894648] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  644.962752] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  645.030822] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  647.263239] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  647.836699] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  647.904622] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  647.972756] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.040777] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.052667] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.052693] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.120775] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.132669] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.132693] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.200930] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.212808] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.212833] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.280949] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.348998] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.417043] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.428953] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.428979] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.497128] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.508772] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.508789] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.577155] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.589052] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  648.589080] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  648.657203] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.725225] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.793271] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.861353] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.929325] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  648.997448] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.497772] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.565782] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.633779] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.701906] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.762613] wlan0: authenticate with <MAC address removed>
[  649.769938] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  649.786435] wlan0: direct probe to <MAC address removed> (try 1/3)
[  649.989738] wlan0: direct probe to <MAC address removed> (try 2/3)
[  650.193886] wlan0: direct probe to <MAC address removed> (try 3/3)
[  650.398018] wlan0: authentication with <MAC address removed> timed out
[  650.414347] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.590449] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.602325] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  650.602351] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  650.670553] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.682467] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  650.682494] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  650.750611] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.818648] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.886699] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  650.898561] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  650.898587] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  650.966755] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.034798] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.102839] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.114689] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  651.114714] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  651.182907] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.194787] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  651.194814] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  651.262933] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.331018] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.342886] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  651.342911] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  651.411035] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.479061] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.547046] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.615114] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.683224] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  651.751182] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  652.251593] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  652.319675] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  652.387607] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  652.455693] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  652.523787] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  654.792186] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  655.365638] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.433723] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.501457] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.569808] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.637851] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.705913] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.717765] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  655.717793] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  655.785922] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.797819] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  655.797846] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  655.866041] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.877909] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  655.877934] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  655.946034] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  655.957893] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  655.957916] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  656.026099] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.094133] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.162201] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.174073] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  656.174097] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  656.242230] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.314239] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.382271] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.450410] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  656.518146] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.018724] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.086821] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.154839] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.222908] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.283565] wlan0: authenticate with <MAC address removed>
[  657.290918] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  657.307325] wlan0: direct probe to <MAC address removed> (try 1/3)
[  657.510709] wlan0: direct probe to <MAC address removed> (try 2/3)
[  657.714888] wlan0: direct probe to <MAC address removed> (try 3/3)
[  657.919010] wlan0: authentication with <MAC address removed> timed out
[  657.935301] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.111536] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.179512] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.247562] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.315599] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.383686] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.395574] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  658.395600] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  658.463699] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.475598] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  658.475622] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  658.543766] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.611448] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.679861] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.691725] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  658.691752] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  658.759872] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.827992] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.839872] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  658.839898] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  658.907990] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  658.976062] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.044044] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.112087] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.180181] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.248240] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.748555] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.816588] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.884645] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  659.952714] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  660.020762] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  662.313093] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  662.886662] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  662.898529] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  662.898554] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  662.966739] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  662.978611] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  662.978639] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.046743] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.114790] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.182831] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.194709] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  663.194735] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.262916] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.274816] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  663.274842] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.342957] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.411011] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.422891] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  663.422914] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.491069] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.502909] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  663.502936] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.571084] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.639104] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.651008] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  663.651033] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  663.719189] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.787226] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.855310] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.923369] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  663.991384] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.059435] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.559786] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.627855] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.695864] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.763963] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.824190] wlan0: authenticate with <MAC address removed>
[  664.831934] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  664.848502] wlan0: direct probe to <MAC address removed> (try 1/3)
[  665.051711] wlan0: direct probe to <MAC address removed> (try 2/3)
[  665.255872] wlan0: direct probe to <MAC address removed> (try 3/3)
[  665.459983] wlan0: authentication with <MAC address removed> timed out
[  665.484314] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.664478] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.732553] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.800580] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.868642] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.880515] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  665.880542] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  665.948659] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  665.960580] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  665.960608] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  666.028583] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.096825] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.164851] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.232918] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.300990] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.368973] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.436934] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.505055] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.516895] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  666.516926] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  666.589239] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.657332] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.725171] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  666.792974] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  667.293427] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  667.361612] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  667.429682] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  667.497709] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  667.565726] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  669.854300] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  670.427652] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.495738] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.563755] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.575648] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  670.575673] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  670.643821] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.655452] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  670.655467] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  670.723842] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.791924] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.803836] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  670.803861] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  670.871816] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  670.883398] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  670.883414] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  670.948022] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.020054] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.031939] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  671.031965] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  671.100128] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.168160] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.236189] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.248062] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  671.248088] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  671.316264] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.328050] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  671.328078] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  671.396220] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.464364] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.532409] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  671.600417] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.100672] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.168806] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.236813] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.304815] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.365605] wlan0: authenticate with <MAC address removed>
[  672.373035] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  672.389622] wlan0: direct probe to <MAC address removed> (try 1/3)
[  672.592646] wlan0: direct probe to <MAC address removed> (try 2/3)
[  672.796803] wlan0: direct probe to <MAC address removed> (try 3/3)
[  673.000911] wlan0: authentication with <MAC address removed> timed out
[  673.033296] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.213476] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.225394] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.225422] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.293614] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.361608] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.429650] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.441509] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.441536] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.513681] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.525547] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.525573] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.593732] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.661771] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.673642] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.673668] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.741853] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.753730] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.753757] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.821896] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.889967] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.901828] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  673.901851] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  673.970010] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  673.981882] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  673.981908] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  674.050038] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.118049] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.186194] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.254216] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.322218] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.390280] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.890624] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  674.958677] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  675.026628] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  675.094742] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  675.162765] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  677.395338] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  677.968683] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.036698] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.048513] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  678.048541] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.116762] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.184862] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.252751] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.264623] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  678.264651] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.332934] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.344809] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  678.344836] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.412945] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.481008] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.492871] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  678.492899] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.561035] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.572927] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  678.572954] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.641065] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.709135] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.720994] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  678.721021] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.788853] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.800395] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  678.800440] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  678.865228] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  678.933326] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.001354] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.069363] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.137439] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.637796] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.705819] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.773930] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.841920] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.902209] wlan0: authenticate with <MAC address removed>
[  679.909894] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  679.926368] wlan0: direct probe to <MAC address removed> (try 1/3)
[  680.129744] wlan0: direct probe to <MAC address removed> (try 2/3)
[  680.333897] wlan0: direct probe to <MAC address removed> (try 3/3)
[  680.538030] wlan0: authentication with <MAC address removed> timed out
[  680.554366] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  680.730490] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  680.802500] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  680.874549] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  680.942681] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.010700] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.022579] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  681.022605] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  681.090755] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.158841] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.226805] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.238654] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  681.238678] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  681.306858] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.375011] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.386939] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  681.386962] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  681.454814] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.466423] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  681.466445] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  681.531282] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.599069] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.667069] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.735209] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.803185] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  681.871498] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  682.371520] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  682.439653] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  682.507716] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  682.575711] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  682.643845] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  684.932145] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  685.505620] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.517509] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026400
[  685.517538] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  685.585688] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.653754] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.721835] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.733747] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  685.733777] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  685.801892] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.869887] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.937932] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  685.949819] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  685.949846] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  686.018025] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.029952] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  686.029980] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  686.098093] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.110015] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  686.110041] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  686.178089] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.189986] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  686.190012] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  686.258138] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.326134] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.394289] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.406156] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  686.406188] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  686.474225] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.542354] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.610382] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  686.678445] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  687.178796] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  687.246792] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  687.314886] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  687.382883] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  687.450948] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.451635] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.523641] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.591679] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.659416] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.727842] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.795895] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.807764] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  688.807792] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  688.879585] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.948010] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  688.959888] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  688.959913] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  689.028031] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.039901] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  689.039927] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  689.108099] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.119956] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  689.120009] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  689.188108] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.256132] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.268047] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  689.268075] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  689.336168] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.404295] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.472222] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.540366] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  689.608389] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.108724] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.176747] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.244840] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.312902] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.373257] wlan0: authenticate with <MAC address removed>
[  690.381017] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  690.397475] wlan0: direct probe to <MAC address removed> (try 1/3)
[  690.600656] wlan0: direct probe to <MAC address removed> (try 2/3)
[  690.804797] wlan0: direct probe to <MAC address removed> (try 3/3)
[  691.008916] wlan0: authentication with <MAC address removed> timed out
[  691.025248] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.201456] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.269403] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.337535] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.405342] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.473690] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.485558] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  691.485588] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  691.553688] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.565556] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  691.565581] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  691.633754] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.701791] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.769866] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.781742] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  691.781769] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  691.849899] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.917928] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  691.929805] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00026800
[  691.929838] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  691.998005] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.066009] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.134043] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.202025] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.270087] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.338245] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.838487] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.906569] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  692.974602] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  693.042668] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  693.110774] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.403179] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  695.664402] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.676256] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  695.676285] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  695.744434] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.812488] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.880506] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.892337] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  695.892365] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  695.960273] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  695.971838] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  695.971857] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  696.040680] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.108694] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.176730] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.188616] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  696.188642] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  696.256796] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.324725] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.336618] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00020800
[  696.336645] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  696.404859] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.416722] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  696.416755] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  696.485001] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.552973] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.621061] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.689104] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.757072] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  696.825194] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.325529] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.393508] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.461576] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.529578] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.590066] wlan0: authenticate with <MAC address removed>
[  697.597760] ath: phy0: Failed to stop TX DMA, queues=0x001!
[  697.614296] wlan0: direct probe to <MAC address removed> (try 1/3)
[  697.622502] ath: phy0: Failed to stop TX DMA, queues=0x001!

****************** done ******************


```

---

### Post by Bucky Ball on 2014-02-19
Is your router/access point listed here anywhere:

```
Wireless Access Points 
    BronzeCheetah:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    BELL420:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Home2:           Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    OURHOME:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    Taurus-guest:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    wen:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    HOMELAND:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP


```

? Wireless card seems to be scanning fine and you should even be able to log on to 'Taurus-guest' as it has no security. When you left click on the network icon do you not see this list of access points?

---

### Post by Zack_Newsham on 2014-02-20
Yes, HOMELAND. I've always been able to see the networks, as mentioned previously I also get prompted for my password - repeatedly, however the connection never succeeds.

---

### Post by Bucky Ball on 2014-02-20
Ok, have you manually set it up in Network Manager rather than relying on clicking the access point from the NM drop down list on left-click? Sorry if you've tried already and mentioned previously. 

Right click NM>Edit Connections>Wireless>Add> and add your AP details (even if you see the connection there and listed under 'Wireless' ignore and create a new one). The really important bit is getting the AP name in there and the security details. Once you've done that, reboot and see what gives.

The idea of this is that on reboot, it will see 'HOMELAND' set up there with it's security details which will prevent it asking you to manually do it all the time and ... all is right with the world of wireless! Well, got my fingers crossed, but worth a try. I always set them up manually so I know they have the correct details and it stops a few issues popping up (If you use static IP addresses this is also how you would set it up).

---

### Post by varunendra on 2014-02-20
Please do as BB suggested above, it is worth a try.

But be aware that a WEP security is almost NO security in today's world. There are plenty of free tools that take only a double-click + 10 minutes (at most) to crack it. I highly recommend that you change the security in the router to pure WPA2-PSK with AES (also called CCMP). Make sure it is _pure_ **WPA2** with AES (CCMP), not WPA/WPA2 mixed mode or TKIP - that is worse performance-wise.

However, the above is just our attempt to try our luck. In my 'logical' approach to find a solution, whatever I could find on the net wasn't very promising, instead disheartening maybe.

I searched for the "Fail" messages you are continuously getting in your dmesg -
> **Zack_Newsham said:**
> ```

[  648.200930] ath: phy0: **[COLOR="#FF0000"]Failed to stop TX DMA, queues=0x001[/COLOR]**!
[  648.212808] ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x00006400
[  648.212833] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up

```
....and it seems that it is a looooongstanding bug in either the atheros wireless cards or the ath9k drivers. The reports about it date back to 2010 (maybe even earlier) till now, and still there are no fixes. There were a couple of patches but those were just experiments and there were no positive feedbacks.

Of the plenty of links I found, these two should be enough for reference : [https://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg07923.html](https://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg07923.html) (just one of a long chain of mail exchanges, this one includes the last suggested patch, so I chose it for reference. Follow the links at the bottom to follow previous/later mails)
and
[https://dev.openwrt.org/ticket/11862](https://dev.openwrt.org/ticket/11862) *(a long battle against the bug that started 20 months ago, and still going on. The last post is just 13 days old)*.

These error messages are always related to failing/inconsistent connectivity. I am not yet sure but the bug seems to be related with low signal, antenna fault or power management (either the card or on router's side).

So for now, if what BB suggested in above post (and the changing of encryption type as I suggested above) don't help, try this as another experiment -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k bt_ant_diversity=1
```
This will be a temporary change that will be lost at next boot. So try connecting without rebooting after above commands. If it helps, we've probably found a miracle. Since miracles are hard to come by, if this doesn't help, please report back with the output of following commands -
```
iwconfig
nm-tool
grep [[:alnum:]] /sys/module/ath9k/parameters/*
dmesg | tail -20
```

Oh, and whether we succeed or not, I highly recommend you to either **file a fresh bug report** at launchpad against ath9k driver, or add yourself to the "Affects me" list of this existing bug report, with a comment about your problem : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1032826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1032826) (the last comment is more than 8 months old, but the bug is still open with "incomplete" status).

---

### Post by Zack_Newsham on 2014-02-20
I thought I had replied to this, but I guess it got lost.. it didnt work, so this evening after work I went out and bought another device, USB this time since the iPhone works nicely. It's also a broadcom device (netgear n300) however, now I am stuck dealing with ndiswrapper-dkms, which will not build no matter what I do to it - ugh. May be time to quit and return to windows. Any ideas how to deal with this error?

```

Cannot find kernel build files in /usr/src/linux-headers-3.11.0-15-generic
Please give the path to kernel build directory with
the KBUILD=<path> argument to make


make: *** [config_check] Error 1

```

if I do as it says and give it KBUILD I get:

```

Makefile:36: *** Cannot find kernel version in /usr/src/linux-headers-3.11.0-15, is it configured?.  Stop.

```

note that this is where -generic links to. I tried running make oldconfig in linux-headers-3.11... as another post suggested but still no luck. This is killing me :( I really dont want to have to reinstall because its taken me this long to get the damn video cards working!

Thanks for your help thus far chaps.

---

### Post by Bucky Ball on 2014-02-20
ndiswrapper??? Why the heck are you going there? Did you try just plugging the thing in, doing an update and checking Additional Drivers? For the most part, Broadcom is VERY well supported in Linux. ndiswrapper is long go for most cards, not just Broadcom, superseded and definitely to be avoided unless an absolute last resort. Installing it could be creating more problems, or perhaps THE problem.

Plug in the stick, do an update, open a terminal and post the result of these two commands here:

```
lsusb
sudo lshw -C network
```

Update: Yea, right. A bad choice. That card is a nightmare to get running as well. 

[https://duckduckgo.com/?q=netgear+n300+ubuntu](https://duckduckgo.com/?q=netgear+n300+ubuntu)

Your only choice might be ndiswrapper, but I wouldn't give up yet.

---

### Post by varunendra on 2014-02-21
I'm a bit allergic to ndiswrapper too. If you have an option to replace the dongle, replace it with one that is properly supported on Linux. I just made a post with some reference links about these : [http://ubuntuforums.org/showthread.php?t=2204405&p=12935301#post12935301](http://ubuntuforums.org/showthread.php?t=2204405&p=12935301#post12935301)

Wild Man is sick, but he suggested me via PM that we could have better luck if we "Uninstalled" the previous backports version before trying the latest one. Taking a look at the installation scripts, I personally think it maybe worth a try if you are wish to give it another shot.

However, if you have given up on that card, and are now stuck with this netgear one, I may try to help. But like BB mentioned above, ndiswrapper is our last resort and it should be. Please post the output of-
```
lsusb
```
..if you can't replace the dongle and have to make this one work. Even though not usually recommended, installing ndiswrapper shouldn't be a problem if you are using a current version. Please give us the link to the post/guide that you followed to install ndiswrapper.

---

### Post by Zack_Newsham on 2014-02-21
alrighty chaps, I returned the card, and bought an asus pce-n10 instead, because it states on its product page that it is compatible with Ubuntu...and it still doesnt work :( Here is the output of the wireless script. Once again, I can see the networks, I get prompted for my password - repeatedly. This is also a clean installation of Ubuntu - I have installed nothing else. No other drivers - clean slate! Really hoping this time we can figure this out.

```


*************** info trace ***************

***** uname -a *****

Linux zacknewsham-desktop 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
    Kernel driver in use: rtl8192ce

***** lsusb *****

Bus 008 Device 002: ID 2109:3431  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Zack MacBook Pro"  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: <MAC address removed>   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

***** lsmod *****

rtl8192ce              58603  0 
rtl8192c_common        53827  1 rtl8192ce
rtl_pci                27261  1 rtl8192ce
rtlwifi                64035  2 rtl8192ce,rtl_pci
mac80211              619465  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              499466  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: wlan0  [HOMELAND] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Zack MacBook Pro:Ad-Hoc, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    HOMELAND:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"Zack MacBook Pro"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 297140ms ago
                    IE: Unknown: 00105A61636B204D6163426F6F6B2050726F
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8363D6BED4EF1CF5A92482B
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     13B5FC2521B6DC5AB3F115C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.0/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.181557] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.194026] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.194230] rtlwifi: wireless switch is on
[    2.742636] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.742967] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.114914] wlan0: Selected IBSS BSSID <MAC address removed> based on configured SSID
[   17.144766] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.966369] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[   65.230660] wlan0: Trigger new scan to find an IBSS to join
[   69.961641] wlan0: Trigger new scan to find an IBSS to join
[   72.919560] wlan0: Trigger new scan to find an IBSS to join
[   73.762287] wlan0: Creating new IBSS network, BSSID <MAC address removed>
[  106.013513] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  122.276557] wlan0: Trigger new scan to find an IBSS to join
[  126.951337] wlan0: Trigger new scan to find an IBSS to join
[  129.981407] wlan0: Trigger new scan to find an IBSS to join
[  130.824021] wlan0: Creating new IBSS network, BSSID <MAC address removed>
[  163.139273] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  194.071873] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  335.109288] NETDEV WATCHDOG: eth1 (ipheth): transmit queue 0 timed out
[  335.109293] Modules linked in: ipheth vesafb(F) joydev snd_hda_codec_hdmi hid_logitech_dj mxm_wmi arc4 snd_hda_codec_realtek rtl8192ce snd_hda_intel rtl8192c_common snd_hda_codec rtl_pci rtlwifi snd_hwdep mac80211 usbhid hid snd_pcm psmouse snd_seq_midi serio_raw cfg80211 sp5100_tco edac_core fam15h_power snd_rawmidi i2c_piix4 bnep edac_mce_amd k10temp rfcomm radeon snd_seq_midi_event snd_seq bluetooth snd_timer snd_seq_device snd ttm drm_kms_helper wmi drm parport_pc soundcore snd_page_alloc ppdev i2c_algo_bit mac_hid lp parport pata_acpi r8169 firewire_ohci mii firewire_core pata_atiixp crc_itu_t ahci libahci

****************** done ******************



```

quick note: I tried setting up my laptop in ad-hoc mode with no security. I couldnt connect to that either, and it was 3 feet away. So it doesnt appear to be an encryption problem, or a range problem.

---

### Post by Bucky Ball on 2014-02-21
Ad hoc? Try 'infrastructure' and put in the correct security and IPv6 should be set to 'ignore', IPv4 'method' should be set to 'Automatic (DHCP)', 'Connect Automatically' and 'Available to all users' tick boxes at top and bottom of all pages should be ticked (enabled). 'Wireless Security' should, of course, be set with your details. 

That card appears to working just fine, the problem is connecting to your router by the looks. You can connect fine with other machines (and I mean wirelessly)?

---

### Post by varunendra on 2014-02-21
> **Bucky Ball said:**
> Ad hoc? Try 'infrastructure' and put in the correct security and IPv6 should be set to 'ignore', IPv4 'method' should be set to 'Automatic (DHCP)', 'Connect Automatically' and 'Available to all users' tick boxes at top and bottom of all pages should be ticked (enabled). 'Wireless Security' should, of course, be set with your details.

+1 to all of above. I'm also skeptical about the Ad-hoc connection name - it has blank spaces in it.

The driver you currently have in use does seem to have some issues in kernel 3.11 (judging by only a few reports on the forum), but the newer version of the same driver seems to be working nicely.

Accordingly, please make sure you do what BB suggested above, and if still having problems, try the suggestions in this post (post #4) first : [http://ubuntuforums.org/showthread.php?t=2203443&p=12924394#post12924394](http://ubuntuforums.org/showthread.php?t=2203443&p=12924394#post12924394)

If those temporary parameters seem to help, please report back and well make them permanent. If not, try installing the newer driver as suggested in **[post #6]("http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946")** in the above same thread.

---

### Post by Zack_Newsham on 2014-02-21
Still nothing. Incidentally, when I run modprobe -rv ... I still have access to my wireless adapter (i still see it trying to connect) is this correct?

FYI - I tried connecting in ad-hoc mode just to see if it made a difference, I also tried with and without wep (in ad hoc, I have no control over router) and manual IP and DHCP. I tried both the version listed in that post and the latest version of backports, without and then with the options specified in the post. This is my lsmod (if it helps)

```

Module                  Size  Used by
rtl8192se              93908  0 
vesafb                 13876  1 
joydev                 17613  0 
hid_logitech_dj        18767  0 
ipheth                 13533  0 
mxm_wmi                13021  0 
snd_hda_codec_hdmi     41736  2 
arc4                   12573  2 
rtl8192ce              79730  0 
rtl8192c_common        70705  1 rtl8192ce
snd_hda_codec_realtek    56448  1 
rtl_pci                35486  2 rtl8192se,rtl8192ce
rtlwifi                90145  3 rtl8192se,rtl8192ce,rtl_pci
mac80211              526043  4 rtl8192se,rtl8192ce,rtl_pci,rtlwifi
snd_hda_intel          53038  7 
edac_core              62944  0 
usbhid                 53329  0 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
edac_mce_amd           22792  0 
psmouse               104093  0 
snd_hwdep              13613  1 snd_hda_codec
fam15h_power           13166  0 
cfg80211              495836  2 rtlwifi,mac80211
k10temp                13173  0 
snd_seq_midi           13324  0 
serio_raw              13413  0 
hid                   106315  2 hid_logitech_dj,usbhid
compat                 13385  5 rtl8192se,rtl8192ce,rtlwifi,mac80211,cfg80211
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30416  1 snd_seq_midi
sp5100_tco             14114  0 
i2c_piix4              22299  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 74718  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
radeon               1447330  0 
snd_timer              29989  2 snd_pcm,snd_seq
bnep                   24107  2 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
bluetooth             391726  10 rfcomm,bnep
wmi                    19256  1 mxm_wmi
snd                    73753  25 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_midi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32866  0 
ttm                    84837  1 radeon
drm_kms_helper         53237  1 radeon
drm                   306660  3 radeon,ttm,drm_kms_helper
ppdev                  17711  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13564  1 radeon
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
pata_acpi              13038  0 
firewire_ohci          45076  0 
firewire_core          65168  1 firewire_ohci
r8169                  73299  0 
crc_itu_t              12707  1 firewire_core
mii                    13981  1 r8169
ahci                   30063  2 
pata_atiixp            13271  0 
libahci                32118  1 ahci



```

---

### Post by Bucky Ball on 2014-02-21
> **Zack_Newsham said:**
> 

FYI - I tried connecting in ad-hoc mode 

You want infrastructure. Unless you have a static IP and know all the IPs (gateway IP, DNS numbers) 'Manual' will get you no-where in the IPv4 tab. It might help to know exactly what it is you're trying to connect to if you have no access to the router's configuration. This is not your router?

Also, no WEP? No security or security details at all? Again, go back, wrong way. Without this you will have no luck, either, except if you are using free wifi in a wifi hotspot that requires no security. Then you would probably use ad-hoc. 

You need to know the security type your AP (router) is using and the correct security key. Create a network connection in Network Manager, call it 'HOMELAND", input all the correct details as described above and test that. Let's try and get the instance you put into Network Manager to work rather than diddling with the one it pops up everytime it sees the access point (and asks for your details). If all the correct details are there on a permanent basis, it may not ask.

---

### Post by varunendra on 2014-02-21
> **Zack_Newsham said:**
> Incidentally, when I run modprobe -rv ... I still have access to my wireless adapter (i still see it trying to connect) is this correct?
No it is not, and I can see why it happened -
```

Module                  Size  Used by
**[COLOR="#FF0000"]rtl8192se[/COLOR]**              93908  0 
.....
**[COLOR="#006400"]rtl8192ce[/COLOR]**              79730  0 

```

I made a mistake and overlooked the fact that you are using the rtl8192**[COLOR="#006400"]ce[/COLOR]** driver, not ..**[COLOR="#FF0000"]se[/COLOR]**. Although the parameters are applicable to this one the same way, so please remove both the drivers -
```
sudo modprobe -rv rtl8192se rtl8192ce
```
..and reload only the correct one with those parameters this time -
```
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```
Any improvement? If not, a fresh wireless script report please..

---

### Post by Zack_Newsham on 2014-02-21
The only change is that now the adapter wont list the available  networks. Though if I try to connect to the existing network connection  HOMELAND, I get the same symptoms.

```


*************** info trace ***************

***** uname -a *****

Linux zacknewsham-desktop 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

06:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
    Kernel driver in use: rtl8192ce

***** lsusb *****

Bus 008 Device 002: ID 2109:3431  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 005: ID 13fd:1340 Initio Corporation Hi-Speed USB to SATA Bridge
Bus 008 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

***** lsmod *****

rtl8192ce              79730  0 
rtl8192c_common        70705  1 rtl8192ce
rtl_pci                35486  1 rtl8192ce
rtlwifi                90145  2 rtl8192ce,rtl_pci
mac80211              526043  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              495836  2 rtlwifi,mac80211
compat                 13385  4 rtl8192ce,rtlwifi,mac80211,cfg80211

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: wlan0  [HOMELAND] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HOMELAND:        Infra, <MAC address removed>, Freq 0 MHz, Rate 0 Mb/s, Strength 0 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     No scan results


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     0AA476B9D524A7CBBB7360E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8811228D1788BF0C4F4D7B6
depends:        mac80211,rtlwifi
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     710FFFC52D83E7E06A71F7E
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.0/0000:06:00.0 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (rtl8192ce)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"

***** dmesg *****

[    2.259172] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[    2.270240] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.277113] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.277348] rtlwifi: wireless switch is on
[    2.852772] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.853133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.246207] wlan0: authenticate with <MAC address removed>
[    7.943485] NETDEV WATCHDOG: eth1 (ipheth): transmit queue 0 timed out
[     7.943487] Modules linked in: vesafb(F) joydev hid_logitech_dj ipheth  mxm_wmi snd_hda_codec_hdmi arc4 rtl8192ce(OF) rtl8192c_common(OF)  snd_hda_codec_realtek rtl_pci(OF) rtlwifi(OF) mac80211(OF) snd_hda_intel  edac_core usbhid snd_hda_codec edac_mce_amd psmouse snd_hwdep  fam15h_power cfg80211(OF) k10temp snd_seq_midi serio_raw hid compat(OF)  snd_pcm snd_rawmidi sp5100_tco i2c_piix4 snd_seq_midi_event rfcomm  snd_seq radeon snd_timer bnep snd_seq_device mac_hid bluetooth wmi snd  parport_pc ttm drm_kms_helper drm ppdev soundcore snd_page_alloc  i2c_algo_bit lp parport pata_acpi firewire_ohci firewire_core r8169  crc_itu_t mii ahci pata_atiixp libahci
[   10.075108] wlan0: direct probe to <MAC address removed> (try 1/3)
[   10.277039] wlan0: direct probe to <MAC address removed> (try 2/3)
[   10.481186] wlan0: direct probe to <MAC address removed> (try 3/3)
[   10.685312] wlan0: authentication with <MAC address removed> timed out
[   15.080721] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5668.678188] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[ 5668.689436] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 5668.689441] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 5668.689460] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 5668.690683] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 5668.691423] rtlwifi: wireless switch is on
[ 5669.043926] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5669.044477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

---

### Post by varunendra on 2014-02-22
Hmm.. I desperately want to try a few things with the router, but you don't control it :(

As a recap, does the /etc/rc.local file still contain the change we made to it? (the "iw reg set.." command)

Do you have any other Access-Points, hotspots near you to test the connectivity with? So that we can determine if the problem is related to this specific router or not.

I'm really running out of ideas now and don't have much to try with the system/adapter or the driver(s).

I wouldn't say it a "last" attempt, but for now, let's take a look at the following outputs, when a fresh connection attempt is made but fails (like reboot > disable/enable wifi > retry to connect > then run these commands) -
```
dmesg | tail -80
iwconfig
sudo iwlist scan
egrep -v '^#|^$' /etc/rc.local
grep ^options /etc/modprobe.d/*
```

If none of these could give us any clues, I think I'd need to take a break to collect more powerful weapon(s).

---

### Post by praseodym on 2014-02-22
You need nameservers for either card:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Zack_Newsham on 2014-02-22
I went back and re-added that line to rc.local, as this is a new installation of ubuntu.

```

zacknewsham@zacknewsham-desktop:~$ dmesg | tail -80
[    2.502018] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.504362] fb0: VESA VGA frame buffer device
[    2.842464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.842831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.908219] Switched to clocksource tsc
[    3.204600] scsi 8:0:0:0: Direct-Access     Generic  External         2.10 PQ: 0 ANSI: 4
[    3.204809] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    3.205020] sd 8:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.205549] sd 8:0:0:0: [sdc] Write Protect is off
[    3.205552] sd 8:0:0:0: [sdc] Mode Sense: 21 00 00 00
[    3.207104] sd 8:0:0:0: [sdc] No Caching mode page found
[    3.207107] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.208488] sd 8:0:0:0: [sdc] No Caching mode page found
[    3.208491] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.208787]  sdc: sdc1 sdc2 sdc3
[    3.210336] sd 8:0:0:0: [sdc] No Caching mode page found
[    3.210339] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.210342] sd 8:0:0:0: [sdc] Attached SCSI disk
[    5.234153] wlan0: authenticate with 94:44:52:42:eb:a6
[    7.883388] ------------[ cut here ]------------
[    7.883418] WARNING: CPU: 5 PID: 0 at /build/buildd/linux-lts-saucy-3.11.0/net/sched/sch_generic.c:260 dev_watchdog+0x262/0x270()
[    7.883423] NETDEV WATCHDOG: eth1 (ipheth): transmit queue 0 timed out
[    7.883426] Modules linked in: vesafb(F) joydev snd_hda_codec_hdmi hid_logitech_dj ipheth snd_hda_codec_realtek mxm_wmi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 rtl8192ce(OF) rtl8192c_common(OF) rtl_pci(OF) snd_seq_midi rtlwifi(OF) snd_rawmidi mac80211(OF) psmouse snd_seq_midi_event usbhid usb_storage hid serio_raw cfg80211(OF) sp5100_tco snd_seq fam15h_power wmi radeon edac_core snd_timer edac_mce_amd k10temp snd_seq_device i2c_piix4 rfcomm compat(OF) bnep snd ttm bluetooth soundcore drm_kms_helper snd_page_alloc drm parport_pc i2c_algo_bit ppdev mac_hid lp parport pata_acpi firewire_ohci firewire_core crc_itu_t r8169 pata_atiixp mii ahci libahci
[    7.883476] CPU: 5 PID: 0 Comm: swapper/5 Tainted: GF          O 3.11.0-15-generic #25~precise1-Ubuntu
[    7.883477] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F2 07/15/2013
[    7.883479]  0000000000000104 ffff88044ed43cf0 ffffffff8173bc5e 0000000000002a10
[    7.883482]  ffff88044ed43d40 ffff88044ed43d30 ffffffff810653ac ffff88043448a000
[    7.883484]  ffff880438748000 0000000000000000 0000000000000001 0000000000000005
[    7.883487] Call Trace:
[    7.883488]  <IRQ>  [<ffffffff8173bc5e>] dump_stack+0x46/0x58
[    7.883496]  [<ffffffff810653ac>] warn_slowpath_common+0x8c/0xc0
[    7.883498]  [<ffffffff81065496>] warn_slowpath_fmt+0x46/0x50
[    7.883501]  [<ffffffff81658472>] dev_watchdog+0x262/0x270
[    7.883503]  [<ffffffff81658210>] ? pfifo_fast_dequeue+0xe0/0xe0
[    7.883507]  [<ffffffff81072696>] call_timer_fn+0x46/0x160
[    7.883509]  [<ffffffff81073857>] run_timer_softirq+0x267/0x2c0
[    7.883511]  [<ffffffff8108bf09>] ? enqueue_hrtimer+0x39/0xc0
[    7.883514]  [<ffffffff8101b569>] ? read_tsc+0x9/0x20
[    7.883516]  [<ffffffff81658210>] ? pfifo_fast_dequeue+0xe0/0xe0
[    7.883519]  [<ffffffff81042ffd>] ? lapic_next_event+0x1d/0x30
[    7.883521]  [<ffffffff8106a520>] __do_softirq+0xe0/0x280
[    7.883524]  [<ffffffff8175239c>] call_softirq+0x1c/0x30
[    7.883527]  [<ffffffff81015e35>] do_softirq+0x65/0xa0
[    7.883529]  [<ffffffff8106a83e>] irq_exit+0x9e/0xc0
[    7.883531]  [<ffffffff81752d6a>] smp_apic_timer_interrupt+0x4a/0x60
[    7.883534]  [<ffffffff817516dd>] apic_timer_interrupt+0x6d/0x80
[    7.883535]  <EOI>  [<ffffffff8101bbf3>] ? native_sched_clock+0x13/0x80
[    7.883541]  [<ffffffff815e5aae>] ? cpuidle_enter_state+0x5e/0xe0
[    7.883542]  [<ffffffff815e5aa7>] ? cpuidle_enter_state+0x57/0xe0
[    7.883544]  [<ffffffff815e5bf0>] cpuidle_idle_call+0xc0/0x220
[    7.883547]  [<ffffffff8101d0ee>] arch_cpu_idle+0xe/0x30
[    7.883549]  [<ffffffff810ba768>] cpu_idle_loop+0x98/0x260
[    7.883552]  [<ffffffff810ba99b>] cpu_startup_entry+0x6b/0x70
[    7.883555]  [<ffffffff81042038>] start_secondary+0xc8/0xd0
[    7.883557] ---[ end trace 2ae2c05f7c9425cd ]---
[    7.883560] ipheth 8-1.1:4.2: ipheth_tx_timeout: TX timeout
[   10.058999] wlan0: direct probe to 94:44:52:42:eb:a6 (try 1/3)
[   10.260986] wlan0: direct probe to 94:44:52:42:eb:a6 (try 2/3)
[   10.465040] wlan0: direct probe to 94:44:52:42:eb:a6 (try 3/3)
[   10.669251] wlan0: authentication with 94:44:52:42:eb:a6 timed out
[   10.935264] usb 8-1.3: reset high-speed USB device number 4 using xhci_hcd
[   10.949972] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880433f61c80
[   10.949975] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880433f61cc0
[   11.541049] hfsplus: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[   11.542063] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[   11.677657] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   15.064118] wlan0: deauthenticating from 94:44:52:42:eb:a6 by local choice (reason=3)
[   22.451298] audit_printk_skb: 156 callbacks suppressed
[   22.451302] type=1400 audit(1393081402.683:63): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2477 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  288.348172] Loading modules backported from Linux version v3.12.8-0-g97f15f1
[  288.348179] Backport generated by backports.git v3.12.8-1-0-geb41fad
[  288.359810] cfg80211: Calling CRDA to update world regulatory domain
[  288.366471] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: B_CHIP_88C
[  288.377230] rtl8192ce: rtl8192ce: Power Save off (module option)
[  288.377233] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  288.377243] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  288.377413] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  288.377599] rtlwifi: wireless switch is on
[  288.722490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  288.723027] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
zacknewsham@zacknewsham-desktop:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
zacknewsham@zacknewsham-desktop:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

zacknewsham@zacknewsham-desktop:~$ egrep -v '^#|^$' /etc/rc.local
iw reg set CA
exit 0
zacknewsham@zacknewsham-desktop:~$ grep ^options /etc/modprobe.d/*
/etc/modprobe.d/alsa-base.conf:options bt87x index=-2
/etc/modprobe.d/alsa-base.conf:options cx88_alsa index=-2
/etc/modprobe.d/alsa-base.conf:options saa7134-alsa index=-2
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-intel8x0m index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-caiaq index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-ua101 index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-us122l index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-usx2y index=-2
/etc/modprobe.d/alsa-base.conf:options snd-cmipci mpu_port=0x330 fm_port=0x388
/etc/modprobe.d/alsa-base.conf:options snd-pcsp index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/vmwgfx-fbdev.conf:options vmwgfx enable_fbdev=1


```

---

### Post by Zack_Newsham on 2014-02-23
Alrighty chaps - it lives!

I decided it couldnt be a software problem, so I looked into what else it could be, we ruled out the card itself, which only really left the motherboard, by performing this search: "Gigabyte 990FXA-UD3 network problems" I came across a link which seemed to describe my problems to a T - including the USB ports. [http://askubuntu.com/questions/276788/trouble-installing-12-10-on-a-ga-990fxa-ud3-base-machine-network-and-usb-dont](http://askubuntu.com/questions/276788/trouble-installing-12-10-on-a-ga-990fxa-ud3-base-machine-network-and-usb-dont)

After enabling the required IOMMU setting in the BIOS my wifi card magically worked - HUZZAR. Although, it seems I lost access to my front panel USB ports. This is something I can live with. Thanks for all your help!

---

### Post by Bucky Ball on 2014-02-24
Great news. Please mark the thread as solved to help others. Cheers. ;)

---

### Post by varunendra on 2014-02-24
> **Zack_Newsham said:**
> After enabling the required IOMMU setting in the BIOS my wifi card magically worked - HUZZAR. Although, it seems I lost access to my front panel USB ports.
Hmm.. I think I'm not going to forget this name now - IOMMU.

Just yesterday we were discussing about it on IRC, where I heard about it for the first time (which makes me realize how much I have lost the touch with concurrent tech topics). It seems most people need to turn it Off to make things work, but evidently it was the opposite in your case which is not unusual either.

In any case, it is a problem in certain motherboards, probably Gigabyte being on top, if not alone in the list. It is not a problematic technology itself, only its implementation in the BIOS of such motherboards is non-standard and buggy. Perhaps manufacturers love 'Patches over Patches' instead of standardizing things, even if it is only going to cost them once and not too much (in re-writing the BIOS and testing it).

Anyway, I'm glad you went ahead and found the culprit yourself. Thank you so much for the feedback, it is certainly a very valuable addition to our knowledge bank !

Please mark the thread as [SOLVED] as BB requested (by using the "Thread Tools" link above the top post on the page) to make it more useful to others. :)

---

### Post by Bucky Ball on 2014-02-24
PS: Marking as solved doesn't close the thread, and often the conversation becomes quite interesting post fix, just means others can more easily find a fix if they're in the same place as you were. ;)

---

