---
title: "connects then disconnects (possible bug?)"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by freewarelover on 2014-06-02
So since my last thread broadcom works and it still does but only for a certain period of time after boot. Upon startup it connects but after a certain period of time it disconnects and doesn't even see my router anymore until I reboot.

Any ideas? This isn't that big of a deal for me right now but in the future it's gonna become a real pain.

Edit: Forgot to add the prefix that it's Lubuntu.

---

### Post by varunendra on 2014-06-05
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by freewarelover on 2014-06-17
Hi sorry for the very late response. How do you paste in terminal on lubuntu? Ctrl+V doesn't work nor does Ctrl+Shift+V. I was originally going to attempt to type it manually but I really don't want to because it looks very prone to error.

---

### Post by varunendra on 2014-06-18
No Idea about Lubuntu ways, but the standard copy-paste using mouse pointer should work (select > right-click > copy > right-click > paste (in terminal)).

---

### Post by freewarelover on 2014-06-19
No sorry forgot to mention I tried that as well. No right-click drop-down list appears.

---

### Post by varunendra on 2014-06-19
> **freewarelover said:**
> No sorry forgot to mention I tried that as well. No right-click drop-down list appears.

How have you opened the terminal? The shortcut key is 'Ctrl-Alt-T'.

I just checked a Lubuntu 12.04 Live CD in a virtual machine, and the behaviour of the terminal is same as in default Ubuntu. Ctrl-Shift-V, right-click, menu.. everything works here. The screenshot attached below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=254055&stc=1&d=1403162405[/IMG]

Unless things have radically changed in 14.04, I wonder if the installation is broken, or if you are talking about some other 'Terminal'.

---

### Post by freewarelover on 2014-06-20
[COLOR=#222222][FONT=Verdana]Thanks for the key command. For me there only seem to be two terminals one called UXTerm and the other called XTerm neither of which have the right-click menu or the bar of drop-down menus. (file, edit, view, ect) Anyway here you go. 
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

freewarelover-HP-Mini-311-1000 3.13.0-29-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 1760 MB
Uptime : 18:07:56 up 18 min,  2 users,  load average: 0.59, 0.49, 0.32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Hewlett-Packard Company Device [103c:3651]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 090c:637b Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fe:3e23 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 linksys>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:19   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
mxm_wmi                12893  1 nouveau
b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  3 hp_wmi,mxm_wmi,nouveau
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID   | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
==================o=============o===========o==============o=========o===========o==============o===========
 wlan0  [linksys] | 802.11 WiFi | b43       | connected    | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE091:        Infra, <MAC C-02 2WIRE091>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *linksys:        Infra, <MAC C-01 linksys>, Freq 2412 MHz, Rate 54 Mb/s, Strength 88

    Address:         192.168.1.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             71.9.127.107
    DNS:             68.116.46.115
    DNS:             69.144.127.53
------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0             | Wired       | forcedeth | unavailable  | no      |           |              | <MAC eth0>
------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

linksys              : ssid=linksys | bssid=<MAC C-01 linksys> | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search charter.com


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.073/1.364/1.655/0.291 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.075/0.078/0.081/0.003 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 linksys>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a537d98f0b
                    Extra: Last beacon: 4ms ago
          Cell 02 - Address: <MAC C-02 2WIRE091>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"2WIRE091"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003d25c980b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10de:0x0ab0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43)
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
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=50e92f0e-8f19-4428-a8c7-a36d3976bbe1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.368610] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.369447] audit: initializing netlink socket (disabled)
[    2.022742] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.064711] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.064734] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.064752] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.064767] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.064783] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.136239] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   13.172718] wmi: Mapper loaded
[   15.422056] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.672842] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.732986] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   20.933302] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   26.639147] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.649042] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.113247] wlan0: authenticate with <MAC C-01 linksys>
[   29.124855] wlan0: send auth to <MAC C-01 linksys> (try 1/3)
[   29.128179] wlan0: authenticated
[   29.128749] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.128762] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.132140] wlan0: associate with <MAC C-01 linksys> (try 1/3)
[   29.134196] wlan0: RX AssocResp from <MAC C-01 linksys> (capab=0x401 status=0 aid=10)
[   29.135337] wlan0: associated
[   29.135370] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.138173] wlan0: deauthenticating from <MAC C-01 linksys> by local choice (reason=2)
[   29.139422] wlan0: authenticate with <MAC C-01 linksys>
[   29.139913] wlan0: send auth to <MAC C-01 linksys> (try 1/3)
[   29.145439] wlan0: authenticated
[   29.150727] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.150741] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.152449] wlan0: associate with <MAC C-01 linksys> (try 1/3)
[   29.154541] wlan0: RX AssocResp from <MAC C-01 linksys> (capab=0x401 status=0 aid=10)
[   29.160508] wlan0: associated
[   39.166421] wlan0: deauthenticating from <MAC C-01 linksys> by local choice (reason=3)
[   40.393453] wlan0: authenticate with <MAC C-01 linksys>
[   40.404898] wlan0: send auth to <MAC C-01 linksys> (try 1/3)
[   40.407841] wlan0: authenticated
[   40.408394] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   40.408407] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   40.412137] wlan0: associate with <MAC C-01 linksys> (try 1/3)
[   40.414321] wlan0: RX AssocResp from <MAC C-01 linksys> (capab=0x401 status=0 aid=10)
[   40.415445] wlan0: associated

    ======== Done ========


```

Note to site staff/devs: pasting with chrome in textbox doesn't work.
[/FONT][/COLOR]

---

### Post by freewarelover on 2014-06-25
Bump. Results didn't help?

---

### Post by varunendra on 2014-06-26
It did a bit, only I didn't get time to reply. Even today I am posting at the cost of office time, not because I want to become a 'helping angel', but because posting here is an addiction hard to resist..

Anyway, no obvious culprits in the report, so we must start with whatever tiniest bits we have. First, please edit your /etc/default/crda file to explicitly define your country code-

Assuming you are in 'US', please run the following code in a terminal to do so -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
It can also be done via GUI like sane people would do, but insanes like me like the commands since they keep instructions quick, short and easy. ;)

Next, please set the "Method" under "IPv6" in Network Manager to "Ignore" > save > close.

Apart from these changes in Ubuntu, there is a setting called "WMM Support" that you should check in your router/access-point. If there is such a setting (usually under 'QoS' settings) in your router and is enabled, try turning it off > save > reboot the router.

For now, I have only these suggestions for you. Please try these and report back how it goes. We can try a few more things if these don't help.

---

### Post by freewarelover on 2014-06-27
> **varunendra said:**
> but because posting here is an addiction hard to resist..
.
LOL nice I can relate and maybe eventually to here but as of right now I don't have the knowledge. (I'm a total linux noob compared to you) Anyway I tried the command both by typing and paste. Pasting it doesn't do anything but when I typed it it said that no such directory exists. I can't even get to that path via GUI.

---

### Post by varunendra on 2014-06-28
> **freewarelover said:**
> I tried the command both by typing and paste. Pasting it doesn't do anything but when I typed it it said that no such directory exists. I can't even get to that path via GUI.

It must have **/etc/default** directory, isn't there a file named "crda" in it?

I would like to see what exactly you typed or copy-pasted in the terminal (copy-paste everything from the terminal into your post here.

---

### Post by freewarelover on 2014-07-06
My sincere apologies. I recently realized that I had type it in wrong but regardless even when I got it right it nothing seem to happen just like when I copied and pasted it.

---

### Post by freewarelover on 2014-07-25
Bump. I tried googling about it some more but the issues I find tat others had were related to their wireless card being problematic which I know isn't the case for me because my machine is dual-booted with win7 and I never had card issues with it.

Edit: Solved with the  help of a friend I discovered that I installed the wrong broadcom driver. instead of the b43 stuff I needed to run ```
sudo apt-get install bcmwl-kernel-source 
```

---

