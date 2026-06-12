---
title: "No wireless connection on Dell Studio 1535/Wireless 1397 mini card"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by ktpinnock on 2013-12-25
Hey,
So I'm completely new to ubuntu and thought it was ideal for my 5 year old Studio 15, so please bare with me.

1. I installed Ubuntu 12.04 LTS via a USB drive.

2. During setup the wireless got disconnected and the installer provided no option to connect.

3. Under the wireless icon I see wired network and disconnect greyed out, VPN connections and Enable Network(checked), connection information greyed out and edit connections. My wireless internet cannot be seen.

4. After a couple internet searches I found a possible solution involving: sudo apt-get --install bcmwl-kernel-source which gave an output of unable to locate package bcmwl-kernel-source...and that's where I'm stuck.

Any help would be appreciated.

---

### Post by chili555 on 2013-12-26
First, let's identify your wireless device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ktpinnock on 2013-12-26
It says :  Broadcom Corp. BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by chili555 on 2013-12-26
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```If it complains that bcmwl is not installed so not removed, that's fine, just continue on. Detach the ethernet, reboot and let us hear your report.

---

### Post by ktpinnock on 2013-12-26
For both commands it says its unable to locate package bcmwl-kernel source and firmware-b43-lpphy-installer

---

### Post by ktpinnock on 2013-12-26
Nevermind, I got it to work after a lot of google searches. I think my main problem was that I was trying to install this thing without having a wired connection...It sucks that you need a wired connection to setup wireless but I guess that's how it goes.

Pretty much what I did was search for drivers in dash home, clicked additional drivers..from there ubuntu searched for packages and identified that my broadcom sta driver was not activated. So I activated it and now I can see various networks and connect!

---

### Post by chili555 on 2013-12-26
> **ktpinnock said:**
> 
Pretty much what I did was search for drivers in dash home, clicked additional drivers..from there ubuntu searched for packages and identified that my broadcom sta driver was not activated. So I activated it and now I can see various networks and connect!Oh, good! You installed exactly what I suggested you remove! Oh, well, if it's working as expected, then all is well.

---

### Post by gregconquest2 on 2014-10-05
I just followed the steps here, but the switch to turn on Wireless in Linux Mint 17 is set to "off" and when I try to slide it to "on", it just jumps back.

Can anyone help me diagnose my current situation, please? I'll post my notes below:

[COLOR=#000000][FONT=Helvetica]I issued the command:
```
lspci -nn | grep 0280
```[/FONT][/COLOR]and got this result:```
[COLOR=#000000][FONT=Helvetica]Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
I then issued these commands:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
The old stuff was removed, but then after the second command I got:[/FONT][/COLOR]```

[COLOR=#000000][FONT=Helvetica]Package firmware-b43-lpphy-installer is not available[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]...[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]However, the following packages replace it:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]firmware-b43-installer[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
So, I went ahead and tried it:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]

```[COLOR=#000000][FONT=Helvetica]
It said "This will also install b43-fwcutter and firmware-b43-installer", so i said yes, it took a few minutes to install everything. I rebooted, 

As I said above, I still can't turn on the wireless

Issuing
```
inxi -n
```
results in:
```
Network:  
Card 1: Broadcom BCM4312 802.11b/g LP-PHY
driver: b43-pci-bridge
IF: wlan0
state: down
mac: 70:1a:... etc ...
```

Can anyone help me from here?

Thank you,
Greg Conquest
 [/FONT][/COLOR]

---

### Post by varunendra on 2014-10-05
Hello Greg,

Dr. Chili is out on vacation and will be scarcely available to the forums until a few more days, so I think it's okay if I chip in to try making things a bit quicker for you.

Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by gregconquest2 on 2014-10-07
Thank you, varunendra. I ran the script, and one line jumped out at me:
```
rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes

```That looks to me like there is a hardware switch somewhere on this Dell 1545. And voila! I found it. Shared with the F2 key is a wireless toggle, I guess. There is no LED indicating status, but when I press it, the software wireless setting becomes enabled.

So, the problem is solved. I'm posting now from the wireless connection. Thanks again, varunendra.

Still, here is the full output from the script. I hope I've got everything else configured right.

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


gc-Inspiron-1545-LinuxMint-USBboot 3.13.0-36-generic x86_64,  Linux Mint 17 Qiana, qiana


CPU    : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
Memory : 3914 MB
Uptime : 21:18:25 up 35 min,  2 users,  load average: 0.90, 1.45, 2.05




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630653  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
wmi                    19177  1 dell_wmi




module parameters ~~~~~~~~~~~~~~~~~~


b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
============================o=============o========o=============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | sky2   | connected   | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.1.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | b43    | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.302/0.329/0.356/0.027 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.024/0.032/0.040/0.008 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_US.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[dell_wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap


[b43]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     7ABBDDCA84C087640B27AE6
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
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        


[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4315 (wl)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=bc80a313-4280-4d44-a979-bf0896e2fb5f ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.814642] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.814934] audit: initializing netlink socket (disabled)
[    1.089346] wmi: Mapper loaded
[    1.198884] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    1.198901] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.198918] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.198932] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.198946] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.260309] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    8.125087] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    8.172228] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[    8.251890] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.212292] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   11.516394] b43-phy0: Radio hardware status changed to DISABLED
[   11.516588] b43-phy0: Radio turned on by software
[   11.516591] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   11.517329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.591610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


    ======== Done ========

```

---

### Post by varunendra on 2014-10-07
Yup, everything else looks good in the report. Just remember NOT to install the proprietary driver ("wl", also called the 'sta' driver) that the "Additional Drivers" program may propose.

Cheers!!

---

