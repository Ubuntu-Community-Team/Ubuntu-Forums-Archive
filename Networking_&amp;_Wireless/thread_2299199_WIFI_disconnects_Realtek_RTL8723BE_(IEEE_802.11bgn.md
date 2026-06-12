---
title: "WIFI disconnects: Realtek RTL8723BE (IEEE 802.11bgn) using Lubuntu 15.04"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by mr-good555 on 2015-10-16
New to the forums, and hopefully this is what you need to fix my WIFI problem.
[URL="http://paste.ubuntu.com/12798827/"]
[/URL][http://paste.ubuntu.com/12798827/](http://paste.ubuntu.com/12798827/)

> 
########## wireless info START ##########

Report from: 16 Oct 2015 23:11 PHT +0800

Booted last: 16 Oct 2015 20:09 PHT +0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:07:32 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:2335]
    Kernel driver in use: r8169

09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              86016  0 
snd_soc_rt286          28672  0 
btcoexist              49152  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                65536  2 rtl_pci,rtl8723be
snd_soc_core          167936  1 snd_soc_rt286
mac80211              626688  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              462848  2 mac80211,rtlwifi
snd_pcm                94208  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fde0:dffc:d4ee:0:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: fde0:dffc:d4ee:0:ad5a:a7a:be1f:367a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256195303 (256.1 MB)  TX bytes:23755169 (23.7 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"20AA4B9DA7CF"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '

So yeah, I'm lost on what else I need to do.

I've tried "options iwlwifi 11n_disable=1" in "/etc/modprobe.d/iwlwifi.conf".

And I've already updated, upgraded, and dist-upgraded.

---

### Post by Hadaka on 2015-10-16
hi, this command..
```
So yeah, I'm lost on what else I need to do.

I've tried "options iwlwifi 11n_disable=1" in "/etc/modprobe.d/iwlwifi.conf".
```
Is for an intel card. you have a realtek card. try this command instead..
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
if that doesnt help go here
[http://ubuntuforums.org/showthread.php?t=2298712](http://ubuntuforums.org/showthread.php?t=2298712)

---

### Post by mr-good555 on 2015-10-16
I've applied the changes, and so far so good.

I'll check again tomorrow if anything happens. Thanks

---

### Post by Hadaka on 2015-10-16
great, hopefully that is what was needed, I also noticed a couple
other items that may be contributing to your problem. First let's
get rid of this incorrect setting. please do...
```
sudo rm /etc/modprobe.d/iwlwifi.conf
```
Then your country code is not defined,,let's fix that,,please COPY and paste.
```
sudo iw reg set PH
sudo sed -i 's/^REG.*=$/&PH/' /etc/default/crda
```
then go into your router 192.168.0.200 and change the TKIP to WPA2 AES
or anything but TKIP

lastly set your NetworkManager IPV6 setting to IGNORE >>see attached,,
[ATTACH=CONFIG]264985[/ATTACH]

---

### Post by mr-good555 on 2015-10-16
There were no disconnects for an hour so far, I have yet to try it on a game though (I first noticed the urgency when I keep disconnecting during a Frozen Throne game)

But yeah, I've removed the old config, and added the Country code.

However, NetworkManager exists but does nothing (as in no pop-up or console messages), and I have no power over my Routers Settings. The Family just prefers it, I guess.

Hopeful this is enough still. Many thanks, I'll update here if it acts up while in the work router.

---

### Post by Hadaka on 2015-10-16
Glad to hear ! If at all possible changing that router setting will also help.
linux /ubuntu  is not fond of TKIP, and changing that should have no effect
on the other machines, also..if you are satisfied with the current results
please sign in to your thread and mark this thread SOLVED by clicking  Thread Tools
in the upper right side. If you have problems with your work router, please start
a new thread, however.,i seriously doubt your work will change their router settings
so you can play games,;)
thanks.

---

