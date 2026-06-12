---
title: "rtl8192cu driver for Asus USB-N13 limited to 150 Mb/Sec and disconnects a lot"
date: 2014-02-13
forum: Networking &amp; Wireless
---

### Post by two4two on 2014-02-13
Yes, something like this has been posted a lot before.  I have Ubuntu 12.04 LTS.  The driver that comes packaged with the distro is defective.  It can connect only at half-speed (150) with weak signal, and it disconnects frequently.  I have another machine that runs Ubuntu 11.04.  No driver comes packaged with that distro for this wireless stick Asus N13.  So I went to the RealTek site and downloaded their driver and installed it on that machine and it works beautifully at full speed (300) with a 100% signal and does not ever drop connection.

What I want to do is REMOVE all of the distro-supplied driver and firmware for this stick from the 12.04 machine and replace it with the one from RealTek (like what I did on the 11.04 machine).

I did a modprobe and removed 3 modules:  rtl8192cu, rtl8192c_common and rtlwifi.  Then I followed the installation instructions from Realtek.  (BTW, the RealTek driver is only one module: 8192cu -- nothing comparable to the other two come along with it.)  But this failed.  Caused a crash of sorts.  So I re-booted thinking the modprobe wasn't good enough.  Error recurred.  So I removed the RealTek driver and added back the ones from the distro.  The re-instatement worked enough to bring it back to the lousy condition as comes with the distro, but I'd like to actually get a better driver -- the RealTek driver -- so I can connect reliably, with good strong signal and at full speed.

Can anyone give a good simple step-by-step method to fully remove distro-supplied driver and replace with RealTek driver?  Oh, and just in case anyone wants to walk me through identifying the chipset, it IS the 17ab one:

dad@Dad-Stubuntu:~$ lsusb
Bus 008 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 003: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID [COLOR="#FF0000"]**0b05:17ab**[/COLOR] ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Thank you any brave and good soul for taking time to read and respond.  It is a blessing to have educated, willing and compassionate people in this world.

---

### Post by chili555 on 2014-02-13
In fact, modprobe -r rtl8192cu only lasts until reboot. To get the modules to never load, they must be blacklisted:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rtl8192cu
blacklist rtlwifi
blacklist rtl8192c_common 
```Proofread carefully, save and close gedit.

Reinstall your 8192cu and reboot. Is it better now?

---

### Post by two4two on 2014-02-14
> **chili555 said:**
> In fact, modprobe -r rtl8192cu only lasts until reboot. To get the modules to never load, they must be blacklisted:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rtl8192cu
blacklist rtlwifi
blacklist rtl8192c_common 
```Proofread carefully, save and close gedit.

Reinstall your 8192cu and reboot. Is it better now?

Forgot to mention it in the original post; yes I did blacklist them as part of the process I described.  It does not work.  There must some more parts to it that need to be uninstalled.

I saw you, chili555, contributing in an earlier post where the poster asked a very similar question.  But the thread was taken over by someone referring to the OTHER N13 chipset and so even though the thread was marked solved, the original post was not actually solved; the overtaking one was.

---

### Post by chili555 on 2014-02-14
> There must some more parts to it that need to be uninstalled.Not really uninstalled but blacklisted. What remains when you temporarily unload those three and reload 8192cu?```
sudo modprobe -r rtl8192cu
sudo modprobe -r rtl8192c_common
sudo modprobe -r rtlwifi
sudo modprobe 8192cu
lsmod
```Were there significant warnings; say, more than two or three, when you compiled 8192cu? Anything intersting when only 8192cu is loaded here?```
cat /var/log/syslog | grep 8192
```>  But the thread was taken over by someone referring to the OTHER N13 chipset and so even though the thread was marked solved, the original post was not actually solved; the overtaking one was. Only the original poster can mark the thread solved; he must have felt that it was. As I'm sure you understand, when I see 'solved,' I bail out and start answering a new thread!

---

### Post by two4two on 2014-02-16
chili555, thank you for the help.  I found out why the install failed previously.  This time I followed your steps ACCURATELY and it all worked!  The old driver is gone; the new driver is IN!  

I rebooted and did lsmod:

carol@Carol-Ubuntu-12-04:~$ lsmod
Module                  Size  Used by
nls_utf8               12558  1 
udf                    94613  1 
crc_itu_t              12708  1 udf
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             212001  10 rfcomm,bnep
kvm_amd                56136  0 
kvm                   422160  1 kvm_amd
snd_hda_codec_realtek    79855  1 
8192cu                642039  0 
.
.
.
.


The old modules are not listed.  Now the connection is full strength, good strong signal and at FULL SPEED = 300.  It's been only a short while, so I don't know if it'll get any disconnects, but the signs are good.  I'll run this until it never drops again and report back afterwards and mark this resolved if it is.

Also, I'm going to go do it in my Linux Mint 13 LTS because it is based on Ubuntu 12.04 LTS.  

Thanks again chili555

---

### Post by two4two on 2014-02-16
I repeated the process on the Linux Mint, which is based on Ubuntu 12.04 and it worked there too.  Thanks chili555.:)

So far I'll say this is a success.  I wonder why Ubuntu people (Canonical) don't scrap their driver for the ASUS N13 and replace it with the RealTek one.

---

### Post by chili555 on 2014-02-16
> I wonder why Ubuntu people (Canonical) don't scrap their driver for the ASUS N13 and replace it with the RealTek one. That's not the only thing I wonder! In their partial defense, the Realtek version won't compile successfully in 13.10.

You might look for a bug report to add to or file a new one against rtl8192cu: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by phil19 on 2014-03-25
Just a note as I came across this thread. I have got my N13 working on 12.04 LTS with kernel 3.11 by following the instructions here: 
[COLOR=#333333][FONT=UbuntuRegular]f you run into this problem, what worked for me was installing the following driver:[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]From the [README.md]("https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md") file:[/FONT][/COLOR]
[INDENT][h=2]Installation[/h]Ensure you have the necessary prerequisites:
sudo apt-get install linux-headers-generic build-essential dkms
Clone this repository:
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Set it up as a DKMS module:
sudo dkms add ./rtl8192cu-fixes
Build and install it:
sudo dkms install 8192cu/1.8
Refresh the module list:
sudo depmod -a
Ensure the native (and broken) kernel driver is blacklisted:
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
And reboot. You're done.
[/INDENT]

---

### Post by erwin.feser on 2014-04-30
> **phil19 said:**
> Just a note as I came across this thread. I have got my N13 working on 12.04 LTS with kernel 3.11 by following the instructions here: 
[COLOR=#333333][FONT=UbuntuRegular]f you run into this problem, what worked for me was installing the following driver:[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]From the [README.md]("https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md") file:[/FONT][/COLOR][INDENT]**Installation**

Ensure you have the necessary prerequisites:
sudo apt-get install linux-headers-generic build-essential dkms
Clone this repository:
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Set it up as a DKMS module:
sudo dkms add ./rtl8192cu-fixes
Build and install it:
sudo dkms install 8192cu/1.8
Refresh the module list:
sudo depmod -a
Ensure the native (and broken) kernel driver is blacklisted:
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
And reboot. You're done.
[/INDENT]


It worked in Ubuntu 14.04 too! Thank you!

---

### Post by Leonardo_Chiappisi on 2014-05-18
Hi, I am also having some problems with the TL-WN8200ND USB wireless key, using an RTL8192cu chipset. 

I have followed the fix reported by phil19, the new driver (8192cu) is now installed and the old one is in the blacklist. However, I cannot connect to my router. 

When trying to connect, it asks me the password, after some seconds, the password is asked again. The password typed in is correct. I really have no idea where to look for to solve the problem. 


Herafter some commands which might be useful:

```
leonardo@leonardo-A58MD:~$ lsmod | grep 8192
8192cu                632715  0 

```

```
leonardo@leonardo-A58MD:~$ grep rtl8192 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:blacklist rtl8192cu
/etc/modprobe.d/blacklist.conf~:blacklist rtl8192cu
/etc/modprobe.d/blacklist-native-rtl8192.conf:## This file ships with the rtl8192-fixes DKMS module.
/etc/modprobe.d/blacklist-native-rtl8192.conf:blacklist rtl8192cu
/etc/modprobe.d/blacklist-native-rtl8192.conf:blacklist rtl8192c_common

```

According to nm-tool, the device is using the rtl8192cu drivers. Is this correct? Shouldn't it be using the 8192cu drivers?


```
leonardo@leonardo-A58MD:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan2 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        C0:4A:00:27:43:A1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    homePathieGuest: Infra, 82:C7:A6:6E:A0:AD, Freq 2412 MHz, Rate 44 Mb/s, Strength 96 WPA WPA2
    homePathieGuest: Infra, 82:C7:A6:43:8A:89, Freq 2412 MHz, Rate 44 Mb/s, Strength 84 WPA WPA2
    homePathie:      Infra, 82:C7:A6:70:3F:54, Freq 2412 MHz, Rate 44 Mb/s, Strength 44 WPA2
    homePathie:      Infra, 9C:C7:A6:43:8A:89, Freq 2412 MHz, Rate 44 Mb/s, Strength 84 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:97:5A:78:14:A4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

In lsusb the key is not shown

```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
Bus 002 Device 002: ID 2109:0701  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2357:0100  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thanks in advance for your help.
Leo

PS: the usb stick is working under windows.

---

### Post by varunendra on 2014-05-18
> **Leonardo_Chiappisi said:**
> In lsusb the key is not shown
Indeed it is shown, just not by its name, only by its device ID :
```
Bus 001 Device 006: ID **2357:0100**
```
(see [here]("http://usb-ids.gowdy.us/read/UD/2357/0100"))

..And yes, it should be using '8192cu' driver. Please follow the instructions in this post to provide us a detailed report so we can see if there is something obvious that needs to be fixed : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
Obviously, your troubleshooter would be dr. chili, I'm just posting to keep track of the thread, better participating than subscribing to it and sitting aside.

---

### Post by Leonardo_Chiappisi on 2014-05-29
Thanks varunendra, 

here the output of the script. 

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

leonardo-A58MD 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD A8-6600K APU with Radeon(tm) HD Graphics
Memory : 7090 MB
Uptime : 13:03:09 up  1:41,  2 users,  load average: 1,08, 0,41, 0,19


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:2400]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 2357:0100  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan2     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

8192cu                632715  0 
r8188eu               814658  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1
r8188eu      (38): debug=1 | if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_antdiv_type=0 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=66 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_fw_iol=1 | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_smart_ps=2 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan2          | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan1>

    homePathieGuest: Infra, <MAC C-03 homePathieGuest>, Freq 2412 MHz, Rate 44 Mb/s, Strength 100 WPA WPA2
    homePathieGuest: Infra, <MAC C-01 homePathieGuest>, Freq 2412 MHz, Rate 44 Mb/s, Strength 74 WPA WPA2
    homePathie:      Infra, <MAC C-02 homePathie>, Freq 2412 MHz, Rate 44 Mb/s, Strength 74 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

homePathie           : ssid=homePathie | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
homePathie 1         : ssid=homePathie | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_DE.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan2     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan2     Scan completed :
          Cell 01 - Address: <MAC C-01 homePathieGuest>
                    ESSID:"homePathieGuest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=74/100  
          Cell 02 - Address: <MAC C-02 homePathie>
                    ESSID:"homePathie"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=74/100  
          Cell 03 - Address: <MAC C-03 homePathieGuest>
                    ESSID:"homePathieGuest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=58/100  Signal level=98/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8192cu

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[8192cu]
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     0178C5A913EE91E7925ADE1
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)

[r8188eu]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
srcversion:     EEC10BD45D2303EBF0BA81A
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4cb51b77-0eeb-4468-b494-f3ef56e97b95 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.906043] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.906352] audit: initializing netlink socket (disabled)
[    1.334881] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.391089] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    8.511309] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[    8.512131] rtl8192cu driver version=v4.0.2_9000.20130911
[    8.512208] register rtw_netdev_ops to netdev_ops
[    8.660988] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan1>
[    8.727093] systemd-udevd[360]: renamed network interface wlan1 to wlan2
[   11.796834] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.834074] rtl8192cu_hal_init in 572ms
[   14.847886] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   14.848399] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   14.855771] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   14.857152] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   15.402737] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.403070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.411348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.354807] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.889531] ==> rtl8192cu_hal_deinit 
[   39.098387] ===> ips_netdrv_open.........
[   39.676893] rtl8192cu_hal_init in 580ms
[   41.716745] ==> rtl8192cu_hal_deinit 
[   72.092646] ===> ips_netdrv_open.........
[   72.654011] rtl8192cu_hal_init in 564ms
[   74.693832] ==> rtl8192cu_hal_deinit 
[  115.082168] ===> ips_netdrv_open.........
[  115.641090] rtl8192cu_hal_init in 560ms
[  117.680921] ==> rtl8192cu_hal_deinit 
[  168.073430] ===> ips_netdrv_open.........
[  168.654120] rtl8192cu_hal_init in 584ms
[  170.693845] ==> rtl8192cu_hal_deinit 
[  231.057853] ===> ips_netdrv_open.........
[  231.617001] rtl8192cu_hal_init in 560ms
[  233.656768] ==> rtl8192cu_hal_deinit 
[  294.046318] ===> ips_netdrv_open.........
[  294.607873] rtl8192cu_hal_init in 564ms
[  296.647642] ==> rtl8192cu_hal_deinit 
[  357.036588] ===> ips_netdrv_open.........
[  357.598744] rtl8192cu_hal_init in 564ms
[ 2978.009604] issue_deauth_ex(wlan2) to <MAC ID removed>, ch:1, 5/5 in 496 ms
[ 2979.543923] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2981.461052] issue_deauth_ex(wlan2) to <MAC C-02 homePathie>, ch:1, 5/5 in 496 ms
[ 2983.035110] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2984.956360] issue_deauth_ex(wlan2) to <MAC C-02 homePathie>, ch:1, 5/5 in 496 ms
[ 2986.514517] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2988.431546] issue_deauth_ex(wlan2) to <MAC C-02 homePathie>, ch:1, 5/5 in 496 ms
[ 2989.997731] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2991.918855] issue_deauth_ex(wlan2) to <MAC C-02 homePathie>, ch:1, 5/5 in 496 ms
[ 2993.477062] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2998.472796] ==> rtl8192cu_hal_deinit 
[ 2999.889861] ===> ips_netdrv_open.........
[ 3000.451937] rtl8192cu_hal_init in 564ms
[ 3002.491910] ==> rtl8192cu_hal_deinit 
[ 3008.107527] ===> ips_netdrv_open.........
[ 3008.706247] rtl8192cu_hal_init in 600ms
[ 3010.745963] ==> rtl8192cu_hal_deinit 
[ 3011.479352] ===> ips_netdrv_open.........
[ 3012.045602] rtl8192cu_hal_init in 568ms
[ 3014.085452] ==> rtl8192cu_hal_deinit 
[ 3034.477909] ===> ips_netdrv_open.........
[ 3035.040864] rtl8192cu_hal_init in 564ms
[ 3037.080576] ==> rtl8192cu_hal_deinit 
[ 3067.469314] ===> ips_netdrv_open.........
[ 3068.033867] rtl8192cu_hal_init in 568ms
[ 3070.073697] ==> rtl8192cu_hal_deinit 
[ 3110.457792] ===> ips_netdrv_open.........
[ 3111.020816] rtl8192cu_hal_init in 564ms
[ 3113.060786] ==> rtl8192cu_hal_deinit 
[ 3163.447546] ===> ips_netdrv_open.........
[ 3164.009984] rtl8192cu_hal_init in 564ms
[ 3166.049581] ==> rtl8192cu_hal_deinit 
[ 3226.434824] ===> ips_netdrv_open.........
[ 3227.016846] rtl8192cu_hal_init in 584ms
[ 3229.056447] ==> rtl8192cu_hal_deinit 
[ 3289.423384] ===> ips_netdrv_open.........
[ 3289.983726] rtl8192cu_hal_init in 560ms
[ 3292.023791] ==> rtl8192cu_hal_deinit 
[ 3352.409666] ===> ips_netdrv_open.........
[ 3352.990465] rtl8192cu_hal_init in 584ms
[ 3355.030195] ==> rtl8192cu_hal_deinit 
[ 3415.397081] ===> ips_netdrv_open.........
[ 3415.957346] rtl8192cu_hal_init in 560ms
[ 3417.997064] ==> rtl8192cu_hal_deinit 
[ 3478.386927] ===> ips_netdrv_open.........
[ 3478.948342] rtl8192cu_hal_init in 564ms
[ 3480.988174] ==> rtl8192cu_hal_deinit 
[ 3541.371246] ===> ips_netdrv_open.........
[ 3541.931092] rtl8192cu_hal_init in 560ms
[ 3543.971062] ==> rtl8192cu_hal_deinit 
[ 3604.360550] ===> ips_netdrv_open.........
[ 3604.921964] rtl8192cu_hal_init in 564ms
[ 3606.961923] ==> rtl8192cu_hal_deinit 
[ 3667.344283] ===> ips_netdrv_open.........
[ 3667.904964] rtl8192cu_hal_init in 564ms
[ 3669.944916] ==> rtl8192cu_hal_deinit 
[ 3730.331535] ===> ips_netdrv_open.........
[ 3730.891712] rtl8192cu_hal_init in 560ms
[ 3732.931486] ==> rtl8192cu_hal_deinit 
[ 3793.317007] ===> ips_netdrv_open.........
[ 3793.878710] rtl8192cu_hal_init in 564ms
[ 3795.918304] ==> rtl8192cu_hal_deinit 
[ 3856.303458] ===> ips_netdrv_open.........
[ 3856.865459] rtl8192cu_hal_init in 564ms
[ 3858.905652] ==> rtl8192cu_hal_deinit 
[ 3919.292234] ===> ips_netdrv_open.........
[ 3919.852333] rtl8192cu_hal_init in 560ms
[ 3921.892055] ==> rtl8192cu_hal_deinit 
[ 3982.281728] ===> ips_netdrv_open.........
[ 3982.863325] rtl8192cu_hal_init in 584ms
[ 3984.903058] ==> rtl8192cu_hal_deinit 
[ 4045.265882] ===> ips_netdrv_open.........
[ 4045.846197] rtl8192cu_hal_init in 580ms
[ 4047.886640] ==> rtl8192cu_hal_deinit 
[ 4108.249361] ===> ips_netdrv_open.........
[ 4108.808953] rtl8192cu_hal_init in 560ms
[ 4110.848677] ==> rtl8192cu_hal_deinit 
[ 4171.239347] ===> ips_netdrv_open.........
[ 4171.799950] rtl8192cu_hal_init in 564ms
[ 4173.839573] ==> rtl8192cu_hal_deinit 
[ 4234.229219] ===> ips_netdrv_open.........
[ 4234.810815] rtl8192cu_hal_init in 584ms
[ 4236.850788] ==> rtl8192cu_hal_deinit 
[ 4297.213401] ===> ips_netdrv_open.........
[ 4297.773573] rtl8192cu_hal_init in 560ms
[ 4299.813295] ==> rtl8192cu_hal_deinit 
[ 4360.196828] ===> ips_netdrv_open.........
[ 4360.756571] rtl8192cu_hal_init in 560ms
[ 4362.796304] ==> rtl8192cu_hal_deinit 
[ 4423.185750] ===> ips_netdrv_open.........
[ 4423.767437] rtl8192cu_hal_init in 584ms
[ 4425.807013] ==> rtl8192cu_hal_deinit 
[ 4486.176675] ===> ips_netdrv_open.........
[ 4486.738316] rtl8192cu_hal_init in 564ms
[ 4488.777901] ==> rtl8192cu_hal_deinit 
[ 4549.160527] ===> ips_netdrv_open.........
[ 4549.721191] rtl8192cu_hal_init in 564ms
[ 4551.760788] ==> rtl8192cu_hal_deinit 
[ 4612.150755] ===> ips_netdrv_open.........
[ 4612.711940] rtl8192cu_hal_init in 564ms
[ 4614.751668] ==> rtl8192cu_hal_deinit 
[ 4675.134657] ===> ips_netdrv_open.........
[ 4675.698937] rtl8192cu_hal_init in 564ms
[ 4677.738667] ==> rtl8192cu_hal_deinit 
[ 4738.124514] ===> ips_netdrv_open.........
[ 4738.685685] rtl8192cu_hal_init in 564ms
[ 4740.725406] ==> rtl8192cu_hal_deinit 
[ 4801.108356] ===> ips_netdrv_open.........
[ 4801.668685] rtl8192cu_hal_init in 560ms
[ 4803.708893] ==> rtl8192cu_hal_deinit 
[ 4864.098025] ===> ips_netdrv_open.........
[ 4864.659557] rtl8192cu_hal_init in 564ms
[ 4866.699139] ==> rtl8192cu_hal_deinit 
[ 4927.082217] ===> ips_netdrv_open.........
[ 4927.642430] rtl8192cu_hal_init in 560ms
[ 4929.682150] ==> rtl8192cu_hal_deinit 
[ 4990.071687] ===> ips_netdrv_open.........
[ 4990.633177] rtl8192cu_hal_init in 564ms
[ 4992.673370] ==> rtl8192cu_hal_deinit 
[ 5053.055980] ===> ips_netdrv_open.........
[ 5053.636046] rtl8192cu_hal_init in 580ms
[ 5055.675764] ==> rtl8192cu_hal_deinit 
[ 5116.042930] ===> ips_netdrv_open.........
[ 5116.602926] rtl8192cu_hal_init in 560ms
[ 5118.642788] ==> rtl8192cu_hal_deinit 
[ 5179.029873] ===> ips_netdrv_open.........
[ 5179.589924] rtl8192cu_hal_init in 560ms
[ 5181.629740] ==> rtl8192cu_hal_deinit 
[ 5242.019256] ===> ips_netdrv_open.........
[ 5242.580854] rtl8192cu_hal_init in 564ms
[ 5244.620521] ==> rtl8192cu_hal_deinit 
[ 5305.003160] ===> ips_netdrv_open.........
[ 5305.563671] rtl8192cu_hal_init in 560ms
[ 5307.603265] ==> rtl8192cu_hal_deinit 
[ 5366.638986] ===> ips_netdrv_open.........
[ 5367.199009] rtl8192cu_hal_init in 560ms
[ 5369.238481] ==> rtl8192cu_hal_deinit 
[ 5786.838116] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 5786.838830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5786.839221] ===> ips_netdrv_open.........
[ 5787.399187] rtl8192cu_hal_init in 560ms
[ 5791.442455] ==> rtl8192cu_hal_deinit 
[ 5810.897015] ===> ips_netdrv_open.........
[ 5811.458100] rtl8192cu_hal_init in 564ms
[ 5813.497949] ==> rtl8192cu_hal_deinit 
[ 5843.889137] ===> ips_netdrv_open.........
[ 5844.471206] rtl8192cu_hal_init in 584ms
[ 5846.511056] ==> rtl8192cu_hal_deinit 
[ 5886.881594] ===> ips_netdrv_open.........
[ 5887.446411] rtl8192cu_hal_init in 568ms
[ 5889.485985] ==> rtl8192cu_hal_deinit 
[ 5939.870508] ===> ips_netdrv_open.........
[ 5940.431198] rtl8192cu_hal_init in 564ms
[ 5942.471094] ==> rtl8192cu_hal_deinit 
[ 5977.553920] ===> ips_netdrv_open.........
[ 5977.553994] rtl8192cu_hal_init in 0ms
[ 5977.553996] -ips_netdrv_open - drv_open failure, bup=1
[ 5977.583128] rtw_sta_flush(wlan2)
[ 5977.583280] rtw_cmd_thread(wlan2) stop_req:1, break
[ 5977.583444] =====> rtl8192c_free_hal_data =====
[ 5977.583445] <===== rtl8192c_free_hal_data =====
[ 5977.583454] -r871xu_dev_remove, done
[ 5980.423608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5980.426888] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5980.435650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5992.242546] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6063.703660] register rtw_netdev_ops to netdev_ops
[ 6063.838980] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan1>
[ 6063.857171] systemd-udevd[4015]: renamed network interface wlan1 to wlan2
[ 6064.425489] rtl8192cu_hal_init in 568ms
[ 6064.438821] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 6064.439309] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 6064.446554] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 6064.448081] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 6070.483322] ==> rtl8192cu_hal_deinit 
[ 6086.150486] ===> ips_netdrv_open.........
[ 6086.711881] rtl8192cu_hal_init in 564ms
[ 6090.757554] ==> rtl8192cu_hal_deinit 
[ 6101.558667] ===> ips_netdrv_open.........
[ 6102.120498] rtl8192cu_hal_init in 564ms

    ======== Done ========
```

---

### Post by praseodym on 2014-05-29
> r8188eu
What driver is that?!
```

sudo modprobe -rfv r8188eu 8192cu
sudo modprobe -v 8192cu
```
Replug the stick

---

### Post by dccmgb on 2014-12-18
I tried this sequence and after the sudo dkms install 8192cu/1.8 command, I received the following message.

ubuntu@ubuntu:~$ sudo dkms install 8192cu/1.8 
Error! Could not find module source directory. 
Directory: /usr/src/8192cu-1.8 does not exist

One note, I am trying to do this on a USB loaded version of 14.04.  Any help would be appreciated.

---

### Post by praseodym on 2014-12-19
Meanwhile the driver was updated. Now its
```

sudo dkms install 8192cu/1.[COLOR="#FF0000"]9[/COLOR]
```

---

### Post by dccmgb on 2014-12-19
Changing to 1.9 worked.  Thanks so much.  Now I have 14.04 running from a flash drive.

---

### Post by dccmgb on 2015-01-29
I am creating a new USB based 14.04 and the following command no longer works "sudo dkms install 8192cu/1.[COLOR=#ff0000]9[/COLOR]".  I originally changed from 1.8 to 1.9 and it worked then but not now.  Is there a new version number?

---

### Post by dccmgb on 2015-01-29
Please ignore my last post as I had a typo in a previous command.  I now have 14.04 running on a flash drive again.

---

