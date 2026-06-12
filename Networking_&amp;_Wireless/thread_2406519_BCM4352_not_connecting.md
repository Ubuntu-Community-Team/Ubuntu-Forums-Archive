---
title: "BCM4352 not connecting"
date: 2018-11-21
forum: Networking &amp; Wireless
---

### Post by weavil on 2018-11-21
Hello,

I have a router running ddwrt. other computer on wifi, 4 android phones, google home minis all connect with out an issue. 

This box running 18.04 with a BCM4352 using this mobo for fyi:
[https://www.asus.com/us/Motherboards/Z97IPLUS/](https://www.asus.com/us/Motherboards/Z97IPLUS/)

can not connect. wired ethernet works just fine. When I try to connect with wifi I get:

Activation of network connection failed. This is trying on N and AC.

Here's the weird part. When I turn on my pixel phones hotspot I connect just fine. Both router and pixel are on WPA2 PSK.

I've tried manually setting IP/DNS/Gateway to no avail. From the router here is the logon:

```

Dec 31 19:10:41	DDWRT_X10 daemon.info hostapd: ath1: STA  MLME: auth request, signal -45 (Accepted)Dec 31 19:10:41 DDWRT_X10 daemon.info hostapd: ath1: STA  IEEE 802.11: authenticated
Dec 31 19:10:41 DDWRT_X10 daemon.info hostapd: ath1: STA  MLME: assoc request, signal -45 (Accepted)
Dec 31 19:10:41 DDWRT_X10 daemon.info hostapd: ath1: STA  IEEE 802.11: associated (aid 8)
Dec 31 19:10:41 DDWRT_X10 daemon.info hostapd: ath1: STA  RADIUS: starting accounting session 
Dec 31 19:10:41 DDWRT_X10 daemon.info hostapd: ath1: STA  WPA: pairwise key handshake completed (RSN)
```

I did purge and reinstall the broadcom driver here's some info:


```
modinfo wl
filename:       /lib/modules/4.15.18-041518-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.18-041518-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string



```

```
dmesg | grep wl
[    2.579472] wl: loading out-of-tree module taints kernel.
[    2.579474] wl: module license 'MIXED/Proprietary' taints kernel.
[    2.580885] wl: module verification failed: signature and/or required key missing - tainting kernel
[    2.582314] wl 0000:03:00.0: enabling device (0000 -> 0002)
[    2.647669] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    2.662113] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.101900] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.320487] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  223.008878] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  306.004586] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  350.518031] ERROR @wl_dev_intvar_get : 
[  350.518042] ERROR @wl_cfg80211_get_tx_power : 



```

```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

```
lspci -nnk | grep -A2 0280
03:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4352 802.11ac Wireless Network Adapter [1043:855c]
    Kernel driver in use: wl



```

I'm honestly getting ready to throw myself in the oven with the turkey at this point. 

gobble,gobble

---

### Post by weavil on 2018-11-21
before i forget

```
https://paste.ubuntu.com/p/KNwGtgxzg6/
```

---

### Post by chili555 on 2018-11-22
Here is a long thread about your exact 14e4:43b1 device and the exact same error message: [https://ubuntuforums.org/showthread.php?t=2405333](https://ubuntuforums.org/showthread.php?t=2405333)

```
[ 469.086453] ERROR @wl_dev_intvar_get : 
```Please see my post #21 and the following reply:

> WiFi working perfectly now! Thanks! I referred the poster to this post: [https://ubuntuforums.org/showthread.php?t=2405673&p=13816190#post13816190](https://ubuntuforums.org/showthread.php?t=2405673&p=13816190#post13816190) You will note that this is also a 14e4:43b1!

While your error is the same, your symptoms are slightly different. However, I think it is worth trying the proposed fix to see if it helps. If not, it is just as easily reversible.

> Guys,

The solution is:

1. Edit as root this file: "/etc/default/grub"
- Find and modify GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="intremap=off"
- Save and exit

2. $sudo grub-mkconfig -o /boot/grub/grub.cfg

3. Reboot

After it wifi works fine.If you need step-by-step guidance, post back and I'll be happy to help.

---

### Post by weavil on 2018-11-22
Thanks chili555, I was kind of hoping it would be you that responded.

This is how grub looks now after reboot:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="intremap=off"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

The error I get is :

Connection Failed
Activation of network connection failed.

I have tried all these steps with and without secure boot. Only because I remember back when I was on 16.04 I needed to disable secure boot to get WiFi to work. I want to think user error on my part but as I said previously, other devices can connect to router (lifx, google home mini, android phones, another desktop next to me with a Maximus XI Code mobo on Windows 10). Also, the fact that I can connect to my phones Hotspot makes my head hurt.

The last thing I just tried was disabling WiFi Security for all bands on the router. I still got the activation of network connection failed.

=(

---

### Post by chili555 on 2018-11-23
> I still got the activation of network connection failed.Which is no difference from your original post; that is, no better and no worse.

Before we undertake other measures, let's at least see if the errors remain or have been resolved. Please run and post:```
dmesg | grep -e wl -e intremap
```Also, I'd like to see some details about your router. Please run:```
sudo iwlist scan
```Please show us your router only. Redact the MAC address like this:```

Cell 03 - Address: [COLOR="#FF0000"]xxxxxx[/COLOR]
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001299493355
                    Extra: Last beacon: 4048ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




```

---

### Post by weavil on 2018-11-23
Sure.

```

dmesg | grep -e wl -e intremap
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.18-041518-generic root=UUID=abe30bfe-13b7-4b5f-8ff9-0a7794aa21a5 ro intremap=off quiet splash vt.handoff=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.18-041518-generic root=UUID=abe30bfe-13b7-4b5f-8ff9-0a7794aa21a5 ro intremap=off quiet splash vt.handoff=1
[    2.611348] wl: loading out-of-tree module taints kernel.
[    2.611349] wl: module license 'MIXED/Proprietary' taints kernel.
[    2.612537] wl: module verification failed: signature and/or required key missing - tainting kernel
[    2.613548] wl 0000:03:00.0: enabling device (0000 -> 0002)
[    2.678002] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    2.865969] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.470837] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.665279] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   92.966566] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  196.954963] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  245.965562] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  284.963620] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  692.635899] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  725.972009] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  753.972811] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  807.969329] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[79867.921589] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready



```

5GHz - [COLOR=#000000]Activation of network connection failed.[/COLOR]
```

Cell 02 - Address: [COLOR=#FF0000][FONT=&amp]xxxxxx[/FONT][/COLOR]
                    Channel:165
                    Frequency:5.825 GHz
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"oWRT-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:63.5 Mb/s; 63 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00076F5752542D3547
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0301A5
                    IE: Unknown: 070C555320240817640C1795051E
                    IE: Unknown: 3202FFFE
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3B027D00
                    IE: Unknown: 2D1AED091BFFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D16A5000400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: BF0C92018033AAFF1806AAFF1806
                    IE: Unknown: C005000000FCFF
                    IE: Unknown: C302003C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


```

2.4GHz - [COLOR=#000000]Activation of network connection failed.[/COLOR]
```

Cell 05 - Address: [COLOR=#FF0000][FONT=&amp]xxxxxx[/FONT][/COLOR]
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"oWRT-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s; 63.5 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00066F5752542D4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32053048606CFF
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3B025100
                    IE: Unknown: 2D1AED191BFFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1609000400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```

PIXEL HOTSPOT 2.4GHz - Connects fine.
```

Cell 11 - Address: [COLOR=#FF0000][FONT=&amp]xxxxxx[/FONT][/COLOR]
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"Pixel_9160"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A506978656C5F39313630
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 3B110C010204050C1617181A1B1C1D1F202180
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD0113FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: BF0C92798133FAFF0C03FAFF0C03
                    IE: Unknown: C005000000FAFF
                    IE: Unknown: 7F080400000000000040
```

---

### Post by weavil on 2018-11-23
little update,

I tried with a few other routers, an r7000 (ddwrt) wndr3700 (open wrt) and I was able to connect to all bands and all network modes(AC/N/G/B). Back to my main?(r9000 ddwrt) router. I can now connect but only 2.4GHz and only on G,N/G. Everything is set to 20MHz bandwidth and the settings between both ddwrt routers match. Also while testing I change the SSID to make sure I'm the only device connecting to the routers.

Kind of a weird situation, what would tell the router folks:
All my devices connect except 1. They're going to say something is wrong with that 1.

Then the reverse here, I can connect to all routers except 1. Well something must be wrong with that 1 router.

---

