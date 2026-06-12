---
title: "unable to install Broadcom Card"
date: 2017-01-10
forum: Networking &amp; Wireless
---

### Post by zach22 on 2017-01-10
I absolutely cannot get the broadcom card in my system to work. 
Neither the STA driver nor the  b43 driver seem to work when installed and I've tried just about everything i can think of.
It looks like everything is being loaded correctly but i can't seem to get the wifi to work and would love some help.

The system I'm running is a headless Ubuntu Server 14.04.5. 
The system used to be connected via ethernet but due to location changes it must now be wifi.

lspci -nn | grep -i network
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

lsmod
```

Module                  Size  Used bybnep                   20480  2 
rfcomm                 65536  0 
bluetooth             466944  10 bnep,rfcomm
arc4                   16384  2 
b43                   397312  0 
bcma                   49152  1 b43
mac80211              651264  1 b43
snd_hda_codec_idt      53248  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
cfg80211              487424  2 b43,mac80211
dell_wmi               16384  0 
gpio_ich               16384  0 
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0 
dcdbas                 16384  1 dell_laptop
snd_hda_intel          32768  0 
dell_smm_hwmon         16384  0 
i915                 1114112  2 
snd_hda_codec         114688  3 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
coretemp               16384  0 
snd_hda_core           61440  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0 
input_leds             16384  0 
joydev                 20480  0 
lpc_ich                20480  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
drm_kms_helper        131072  1 i915
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
wmi                    16384  1 dell_wmi
mac_hid                16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
drm                   303104  4 i915,drm_kms_helper
snd                    69632  10 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
soundcore              16384  1 snd
shpchp                 32768  0 
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
video                  36864  3 i915,dell_wmi,dell_laptop
lp                     16384  0 
parport                45056  1 lp
ums_realtek            20480  0 
uas                    20480  0 
usb_storage            53248  2 uas,ums_realtek
hid_generic            16384  0 
ahci                   36864  2 
usbhid                 49152  0 
psmouse               114688  0 
libahci                32768  1 ahci
hid                    98304  2 hid_generic,usbhid
sky2                   53248  0 
ssb                    57344  1 b43
fjes                   28672  0 

```

sudo lshw -C network
```
  *-network                      description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:4b:9a:d6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.202.90.145 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:d7:ca:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.4.0-34-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

Thank you for your help.

---

### Post by praseodym on 2017-01-10
Hi,

deactivate the STA driver and install this firmware:

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
It contains ucode15.fw which cannot be extracted anymore in newer driver versions.

---

### Post by zach22 on 2017-01-10
Thanks for rerplying!

STA driver is and has been disabled(purged via apt and modprobe doesn't show wl)
I installed the tar file you suggested and i'm not sure it made a difference

I'll be honest I'm not exactly sure how to test it but i think i made a good effort,

I tried 
```
sudo ifconfig wlan0 up
```
with no response but it brought the interface up

I configred the network i wanted to connect to and ran
```
admin@machine:/etc/wpa_supplicant$ wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
Successfully initialized wpa_supplicant
wlan0: Failed to initialize driver interface

```

I also ran this which shows it attempting to scan but not getting any scan results over and over and over
```
machine@:/etc/wpa_supplicant$ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -d
[sudo] password for kioskadmin: 
wpa_supplicant v2.1
random: Trying to read entropy from /dev/random
Successfully initialized wpa_supplicant
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='asu'
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:4
nl80211: Supported cipher 00-0f-ac:10
nl80211: Supported cipher 00-0f-ac:8
nl80211: Supported cipher 00-0f-ac:9
nl80211: Using driver-based off-channel TX
nl80211: interface wlan0 in phy phy0
nl80211: Set mode ifindex 3 iftype 2 (STATION)
nl80211: Subscribe to mgmt frames with non-AP handle 0x9cc3aa8
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=0104
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=040a
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=040b
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=040c
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=040d
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=090a
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=090b
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=090c
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=090d
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=0409506f9a09
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=7f506f9a09
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=0801
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=06
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=0a07
nl80211: Register frame type=0xd0 nl_handle=0x9cc3aa8 match=0a11
netlink: Operstate: ifindex=3 linkmode=1 (userspace-control), operstate=5 (IF_OPER_DORMANT)
nl80211: driver param='(null)'
Add interface wlan0 to a new radio phy0
nl80211: Regulatory information - country=00
nl80211: 2402-2472 @ 40 MHz 20 mBm
nl80211: 2457-2482 @ 40 MHz 20 mBm
nl80211: 2474-2494 @ 20 MHz 20 mBm
nl80211: 5170-5250 @ 40 MHz 20 mBm
nl80211: 5735-5835 @ 40 MHz 20 mBm
nl80211: Added 802.11b mode based on 802.11g information
wlan0: Own MAC address: 00:22:5f:d7:ca:42
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=4 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 (wlan0) alg=0 addr=(nil) key_idx=5 set_tx=0 seq_len=0 key_len=0
wlan0: RSN: flushing PMKID list in the driver
nl80211: Flush PMKIDs
wlan0: Setting scan request: 0.100000 sec
wlan0: WPS: UUID based on MAC address: 00f92382-4e56-55d0-be60-712f44961e7b
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
nl80211: Skip set_supp_port(unauthorized) while not associated
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
wlan0: Added interface wlan0
wlan0: State: DISCONNECTED -> DISCONNECTED
nl80211: Set wlan0 operstate 0->0 (DORMANT)
netlink: Operstate: ifindex=3 linkmode=-1 (no change), operstate=5 (IF_OPER_DORMANT)
random: Got 20/20 bytes from /dev/random
RTM_NEWLINK: ifi_index=3 ifname=wlan0 operstate=2 linkmode=1 ifi_flags=0x1003 ([UP])
wlan0: State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=3):
     61 73 75                                          asu             
wlan0: Starting AP scan for wildcard SSID
wlan0: Add radio work 'scan'@0x9cd25e0
wlan0: First radio work item in the queue - schedule start immediately
wlan0: Starting radio work 'scan'@0x9cd25e0 after 0.000018 second wait
wlan0: nl80211: scan request
Scan requested (ret=0) - scan timeout 10 seconds
nl80211: Drv Event 33 (NL80211_CMD_TRIGGER_SCAN) received for wlan0
wlan0: nl80211: Scan trigger
wlan0: Event SCAN_STARTED (49) received
wlan0: Own scan request started a scan in 0.000056 seconds
wlan0: CTRL-EVENT-SCAN-STARTED 
EAPOL: disable timer tick
RTM_NEWLINK: ifi_index=3 ifname=wlan0 wext ifi_flags=0x1003 ([UP])
nl80211: Drv Event 34 (NL80211_CMD_NEW_SCAN_RESULTS) received for wlan0
wlan0: nl80211: New scan results available
nl80211: Scan probed for SSID 'asu'
nl80211: Scan probed for SSID ''
nl80211: Scan included frequencies: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484
wlan0: Event SCAN_RESULTS (3) received
wlan0: Scan completed in 1.111313 seconds
nl80211: Received scan results (0 BSSes)
wlan0: BSS: Start scan result update 1
BSS: last_scan_res_used=0/0
wlan0: New scan results available (own=1 ext=0)
wlan0: Radio work 'scan'@0x9cd25e0 done in 1.112127 seconds
wlan0: No suitable network found
wlan0: Setting scan request: 5.000000 sec
Scan SSID - hexdump_ascii(len=3):
     61 73 75                                          asu             
wlan0: Starting AP scan for wildcard SSID
wlan0: Determining shared radio frequencies (max len 1)
wlan0: Shared frequencies (len=0): completed iteration
wlan0: Add radio work 'scan'@0x9cd25e0
wlan0: First radio work item in the queue - schedule start immediately
wlan0: Starting radio work 'scan'@0x9cd25e0 after 0.000016 second wait
wlan0: nl80211: scan request
Scan requested (ret=0) - scan timeout 30 seconds
nl80211: Drv Event 33 (NL80211_CMD_TRIGGER_SCAN) received for wlan0
wlan0: nl80211: Scan trigger
wlan0: Event SCAN_STARTED (49) received
wlan0: Own scan request started a scan in 0.000049 seconds
wlan0: CTRL-EVENT-SCAN-STARTED 
RTM_NEWLINK: ifi_index=3 ifname=wlan0 wext ifi_flags=0x1003 ([UP])
nl80211: Drv Event 34 (NL80211_CMD_NEW_SCAN_RESULTS) received for wlan0
wlan0: nl80211: New scan results available
nl80211: Scan probed for SSID 'asu'
nl80211: Scan probed for SSID ''
nl80211: Scan included frequencies: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484
wlan0: Event SCAN_RESULTS (3) received
wlan0: Scan completed in 1.107809 seconds
nl80211: Received scan results (0 BSSes)
wlan0: BSS: Start scan result update 2
BSS: last_scan_res_used=0/0
wlan0: New scan results available (own=1 ext=0)
wlan0: Radio work 'scan'@0x9cd25e0 done in 1.108552 seconds
wlan0: No suitable network found
wlan0: Setting scan request: 5.000000 sec
^C
wlan0: Removing interface wlan0
wlan0: Request to deauthenticate - bssid=00:00:00:00:00:00 pending_bssid=00:00:00:00:00:00 reason=3 state=SCANNING
wlan0: State: SCANNING -> DISCONNECTED
nl80211: Set wlan0 operstate 0->0 (DORMANT)
netlink: Operstate: ifindex=3 linkmode=-1 (no change), operstate=5 (IF_OPER_DORMANT)
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wlan0: Cancelling scan request
wlan0: Cancelling authentication timeout
Remove interface wlan0 from radio phy0
Remove radio phy0
nl80211: Remove monitor interface: refcount=0
netlink: Operstate: ifindex=3 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 3 iftype 2 (STATION)
nl80211: Unsubscribe mgmt frames handle 0x8144b221 (mode change)
wlan0: CTRL-EVENT-TERMINATING 

```

Things still seem broken...

---

### Post by Hadaka on 2017-01-10
Hi, am i correct in assuming you are doing this without internet connection to the server ?
*If that is correct, then ..even though you did this once...please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
#and just in case...
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Then go here and follow this guide for offline b43 loading.
[http://ubuntuforums.org/showthread.php?t=2316978](http://ubuntuforums.org/showthread.php?t=2316978)

***sorry just realized this is useless, as you are a headless server.
To get a good clean b43 install is probably going to require a wired connection *****

---

### Post by zach22 on 2017-01-11
The machine has ethernet working. I SSH into it because it's annoying to sit in front of it (the keyboard it has also sucks lol)

as expected:
```
Package 'bcmwl-kernel-source' is not installed, so not removed
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
```

---

### Post by Hadaka on 2017-01-11
Hi, the wireless connection is showing DISABLED
```
*-network DISABLED        description: Wireless interface
       physical id: 2
       logical name: wlan0
```
Please show us the network interface file..
```
cat /etc/network/interfaces
#and
rfkill list all
```
thanks.

---

### Post by zach22 on 2017-01-11
interfaces files doesn't contain a declaration for wlan0, just eth0 and lo. Do I need to add it manually?

```
auto eth0iface eth0 inet dhcp


auto lo
iface lo inet loopback



```

no blocks:
```
user@machine:~$ rfkill list all0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by Hadaka on 2017-01-11
Hi, Your wireless card is not configured for the server..
to use network manager to manage your network you would do,,,
```
sudo sed -i '/eth0/ d' /etc/network/interfaces
```
then go here..
[URL="https://www.youtube.com/watch?v=Hvi2cTMmTq0"]https://www.youtube.com/watch?v=Hvi2cTMmTq0
[/URL]
But...since you are headless..this is the better method
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)
 be sure to also do the if up...if down commands.
thanks.

---

### Post by zach22 on 2017-01-14
This was a headless server so networkmanager was not installed
I also did not need a static IP and was trying to connect to a enterprise authenticated network so I needed to use wpa_supplicant

Regardless I figured out my issue. The machine i was trying to use was an old partially refurbshed laptop modified for it's current job(basically a sign-in kiosk)
AS it turns out, one of the modifications that was done was removing the screen as it was not needed. Well...the antennas were in the screen so i was basically trying to use a wifi card without antennas.

I thank you for the work you put into this but I'm actually going to use an entirely different machine for this purpose for semi-related issues.

---

### Post by Hadaka on 2017-01-14
Hi zach22, Glad to read you found a resolution to the issuse
and sorted it all out. Please mark your thread Solved by clicking
THREAD TOOLS near the upper right corner of your thread, then
choose Solved.
Thanks

---

