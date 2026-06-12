---
title: "No wifi on Presario V2000 / Broadcom BCM4318"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by pablo26 on 2014-09-21
ok so im new to the ubuntu system and im having a problem with the wifi not setting up dont really know what to do, can anyone plz help me, the wifi light on the button does not come on and it does not even show any wifi connections to log in to, i tried going into the additional drivers and click the broadcom to apply changes it starts then ends and goes back to do not use device need some help here please and thanks

---

### Post by deadflowr on 2014-09-21
Thread Moved to Networking and Wireless

Perhaps look over this thread
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by pablo26 on 2014-09-21
thanks deadflowr i tried it but to no avail i appresiate ur help though

---

### Post by varunendra on 2014-09-21
Welcome to the forums pablo26!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by pablo26 on 2014-09-21
ok here is the file 
```

======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

mario-Presario-V2000-EC186UA-ABA 3.8.0-19-generic x86_64,  Ubuntu 13.04, raring

CPU    : AMD Turion(tm) 64 Mobile Technology ML-28
Memory : 1120 MB
Uptime : 22:17:52 up 34 min,  2 users,  load average: 0.12, 0.18, 0.24


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3091]
    Kernel driver in use: 8139too
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
b43                   378642  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
wmi                    19070  1 hp_wmi
ssb                    56748  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43           (9): bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=======o=========o===========o=========o===========o==============o===========
 Interface & ID        | Type  | Driver  | State     | Default | Speed     | Support      | HW Addr   
=======================o=======o=========o===========o=========o===========o==============o===========
 eth0  [Auto Ethernet] | Wired | 8139too | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.2.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
-----------------------+-------+---------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
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
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.482/0.486/0.491/0.022 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.063/0.070/0.078/0.011 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     25C66A8DD9B8B72E053E622
depends:        wmi,sparse-keymap

[b43]
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     E64F87F86B1D9102BD20006
depends:        ssb,mac80211,bcma,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

[bcma]
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/bcma/bcma.ko
srcversion:     F7A1658A8CB1D58E3D347C1
depends:        

[mac80211]
filename:       /lib/modules/3.8.0-19-generic/kernel/net/mac80211/mac80211.ko
srcversion:     2B2B66D5E403FA4D5C2715F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.8.0-19-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8633812892D8ADD6480983B
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     E6D2183F1F271B3545B1E5C
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[ssb]
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/ssb/ssb.ko
srcversion:     9D55B1BBCEE317BD4F3C992
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:14.4/0000:05:00.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=30c3720a-5604-4158-8121-f9f8c10031d1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.464054] audit: initializing netlink socket (disabled)
[    2.062798] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.074629] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.100122] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    2.100137] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    2.100149] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    2.100159] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    2.100168] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    2.140230] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0
[   21.084875] wmi: Mapper loaded
[   22.256727] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   22.302317] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   23.148106] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.148197] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   23.148274] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   23.919116] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

```

---

### Post by varunendra on 2014-09-21
> **pablo26 said:**
> ```
[   23.148106] b43-phy0 ERROR: **[COLOR="#FF0000"]Firmware file "b43/ucode5.fw" not found[/COLOR]**
[   23.148197] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   23.148274] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Doesn't look like you tried installing the "firmware-b43-installer" package as suggested in the thread deadflowr linked to. Or maybe it failed for some reason if you tried.

To be precise, please try installing it again while being connected to internet with your wired connection -
```
[s]sudo apt-get install --reinstall firmware-**[COLOR="#FF0000"]43[/COLOR]**-installer[/s]
sudo apt-get install --reinstall firmware-b43-installer
```

If it gives any errors or fails otherwise, try the offline method : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

Let us know which one worked.

---

### Post by pablo26 on 2014-09-21
ok i tried it and heres what i just got i'll try the offline method tomorrow and let u know
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-43-installer

```

---

### Post by varunendra on 2014-09-21
> **pablo26 said:**
> ok i tried it and heres what i just got i'll try the offline method tomorrow and let u know
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package **firmware-[COLOR="#FF0000"]43[/COLOR]-installer**

```

Oops!! A serious typo, sorry!

It is "b43", not "43" in the command above. I just corrected that in my original post, please try that one.

---

### Post by pablo26 on 2014-09-21
ok i tried both again with the typo fix same thing
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

```
and i tried the manual way and the following commands do absolutly nothing i can nothice
```

sudo mkdir -p /lib/firmware/b43
sudo cp b43/* /lib/firmware/b43
dmesg | grep firmware

``` 
i tried the last command on the post and here is what says
```

a0g0bsinitvals5.fw     lcn400initvals33.fw    sslpn1bsinitvals20.fw
a0g0bsinitvals9.fw     lp0bsinitvals13.fw     sslpn1bsinitvals27.fw
a0g0initvals5.fw       lp0bsinitvals14.fw     sslpn1initvals20.fw
a0g0initvals9.fw       lp0bsinitvals15.fw     sslpn1initvals27.fw
a0g1bsinitvals13.fw    lp0bsinitvals16.fw     sslpn2bsinitvals19.fw
a0g1bsinitvals5.fw     lp0initvals13.fw       sslpn2initvals19.fw
a0g1bsinitvals9.fw     lp0initvals14.fw       sslpn3bsinitvals21.fw
a0g1initvals13.fw      lp0initvals15.fw       sslpn3initvals21.fw
a0g1initvals5.fw       lp0initvals16.fw       sslpn4bsinitvals22.fw
a0g1initvals9.fw       lp1bsinitvals20.fw     sslpn4initvals22.fw
b0g0bsinitvals13.fw    lp1bsinitvals22.fw     ucode11.fw
b0g0bsinitvals5.fw     lp1initvals20.fw       ucode13.fw
b0g0bsinitvals9.fw     lp1initvals22.fw       ucode14.fw
b0g0initvals13.fw      lp2bsinitvals19.fw     ucode15.fw
b0g0initvals5.fw       lp2initvals19.fw       ucode16_lp.fw
b0g0initvals9.fw       n0absinitvals11.fw     ucode16_mimo.fw
ht0bsinitvals26.fw     n0bsinitvals11.fw      ucode16_sslpn.fw
ht0bsinitvals29.fw     n0bsinitvals16.fw      ucode16_sslpn_nobt.fw
ht0initvals26.fw       n0bsinitvals17.fw      ucode17_mimo.fw
ht0initvals29.fw       n0bsinitvals22.fw      ucode19_sslpn.fw
lcn0bsinitvals24.fw    n0bsinitvals24.fw      ucode19_sslpn_nobt.fw
lcn0bsinitvals25.fw    n0bsinitvals25.fw      ucode20_sslpn.fw
lcn0bsinitvals26.fw    n0initvals11.fw        ucode20_sslpn_nobt.fw
lcn0initvals24.fw      n0initvals16.fw        ucode21_sslpn.fw
lcn0initvals25.fw      n0initvals17.fw        ucode21_sslpn_nobt.fw
lcn0initvals26.fw      n0initvals22.fw        ucode22_mimo.fw
lcn1bsinitvals24.fw    n0initvals24.fw        ucode22_sslpn.fw
lcn1bsinitvals25.fw    n0initvals25.fw        ucode24_lcn.fw
lcn1bsinitvals26.fw    n16bsinitvals30.fw     ucode24_mimo.fw
lcn1initvals24.fw      n16initvals30.fw       ucode25_lcn.fw
lcn1initvals25.fw      n18bsinitvals32.fw     ucode25_mimo.fw
lcn1initvals26.fw      n18initvals32.fw       ucode26_mimo.fw
lcn2bsinitvals24.fw    n1bsinitvals20.fw      ucode27_sslpn.fw
lcn2bsinitvals25.fw    n1initvals20.fw        ucode29_mimo.fw
lcn2bsinitvals26.fw    n2bsinitvals19.fw      ucode30_mimo.fw
lcn2initvals24.fw      n2initvals19.fw        ucode32_mimo.fw
lcn2initvals25.fw      pcm5.fw                ucode33_lcn40.fw
lcn2initvals26.fw      sslpn0bsinitvals16.fw  ucode5.fw
lcn400bsinitvals33.fw  sslpn0initvals16.fw    ucode9.fw

```

any other suggestions that i should try??

---

### Post by varunendra on 2014-09-23
> **pablo26 said:**
> ```

lcn2initvals26.fw      sslpn0bsinitvals16.fw  **[COLOR="#0000FF"]ucode5.fw[/COLOR]**
lcn400bsinitvals33.fw  sslpn0initvals16.fw    ucode9.fw

```

any other suggestions that i should try??

Yes, please post back a fresh report of the wireless_script, as the initial problem seems to have been solved. The firmware is now available in the system as highlighted above, so now there is some further problem that the script should be able to tell us about.

---

