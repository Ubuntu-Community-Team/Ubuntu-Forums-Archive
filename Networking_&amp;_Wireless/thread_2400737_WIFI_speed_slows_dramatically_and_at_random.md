---
title: "WIFI speed slows dramatically and at random"
date: 2018-09-09
forum: Networking &amp; Wireless
---

### Post by aaparise on 2018-09-09
I have been trying to fix this for days to no avail.
My normal WIFI speed is about 90 Mb, pretty decent.  At seemingly random times the speed drops to around 5 Mb and stays there. The only way to get the higher speed back is to disable then re-enable the WIFI using the Network manager.

I am using Ubuntu 18.04. The adapter is Realtek rtl8188ee.


Output from iwconfig :

```
wlan1     IEEE 802.11  ESSID:"Hermes"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: F0:FC:C8:FD:18:F9   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

Output from sudo lshw -class network:

```
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: a0:2b:b8:25:2f:a9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:4000(size=256) memory:c2600000-c2600fff memory:c2400000-c2403fff
  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 48:5a:b6:56:f0:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=4.15.0-33-generic firmware=N/A ip=10.0.0.37 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:31 ioport:3000(size=256) memory:c2500000-c2503fff



```


Output from wireless-info script:

[https://paste.ubuntu.com/p/m5B2Gh4x6z/](https://paste.ubuntu.com/p/m5B2Gh4x6z/)

Thanks in advance.

---

### Post by chili555 on 2018-09-09
> [22487.561086] rtlwifi: [COLOR="#FF0000"]AP off, try to reconnect now[/COLOR]
[22487.561121] wlan1: Connection to AP <MAC 'Hermes' [AC1]> lost
[22500.546857] wlan1: authenticate with <MAC 'Hermes' [AC1]>
[22500.566000] wlan1: send auth to <MAC 'Hermes' [AC1]> (try 1/3)
[22500.567960] wlan1: authenticated
[22500.569822] wlan1: associate with <MAC 'Hermes' [AC1]> (try 1/3)
[22500.573452] wlan1: RX AssocResp from <MAC 'Hermes' [AC1]> (capab=0x431 status=0 aid=2)
[22500.573770] wlan1: associated
[29425.281926] wlan1: [COLOR="#FF0000"]AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)[/COLOR]
[29426.306429] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29435.317012] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[29436.341032] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29455.284842] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[29456.411474] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29463.272018] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[29464.296011] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29465.320091] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[29466.344042] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29473.310979] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[29475.355944] wlan1: AP <MAC 'Hermes' [AC1]> changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[29913.602348] wlan1: deauthenticating from <MAC 'Hermes' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[29918.058364] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[29919.109700] wlan1: authenticate with <MAC 'Hermes' [AC1]>
[29919.119821] wlan1: send auth to <MAC 'Hermes' [AC1]> (try 1/3)
[29919.121691] wlan1: authenticatedThese interesting entries suggest to me that either the router is defective, a low likelihood, I suspect; or that the channel is set to auto select. Please see: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Also, we see this interesting entry in /etc/network/interfaces:```
auto lo
iface lo inet loopback


[COLOR="#FF0000"]auto wlan1
mtu 1462[/COLOR]
```It is malformed and ineffective; please remove it.

Entries there interfere with Network Manager.

---

### Post by aaparise on 2018-09-10
I have removed the indicated setting in [COLOR=#000000]/etc/network/interfaces.  I will see if that makes a difference before I make another change.

Router is already set for b/g/n and [/COLOR][COLOR=#000000]WPA2-AES[/COLOR][COLOR=#000000].

Bandwidth was originally set to 20. This gave a speed of about 32 Mb. When I changed it to 20/40 speed increased to about 95 Mb, so I am hard pressed to change it back.

The router is set for automatic channel selection.   I will try changing this next.  Interesting is that the router will not allow me to manually set channels 1-4.

All worth noting, I believe, is the fact that the WIFI must be disabled, then re-enabled to get the high speed functioning again.  Just disconnecting and reconnecting will keep the slow speed going.  This seems to me to be something involving the computer, not the router.

I will wait to see if this problem recurs before making further changes.


[/COLOR]

---

### Post by aaparise on 2018-09-10
Making the changes in [COLOR=#000000]/etc/network/interfaces did not change anything. 

I changed the router channel to 6 rather than automatic.  Will let that run until it happens again(if it does).[/COLOR]

---

### Post by aaparise on 2018-09-10
Changing the router channel to 6 rather than automatic had no effect.

Any more ideas?

---

### Post by chili555 on 2018-09-11
Does dmesg still contain the interesting lines I noted above?

---

### Post by aaparise on 2018-09-11
The new dmesg:

```
##### dmesg #############################

[   38.402994] rtl8188ee: rtl8188ee: Power Save off (module option)
[   38.402995] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   38.403002] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   38.828119] r8169 0000:01:00.0 eth0: link down
[   38.828206] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.828228] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   38.828439] rtlwifi: rtlwifi: wireless switch is on
[   39.198740] wl: loading out-of-tree module taints kernel.
[   39.198745] wl: module license 'MIXED/Proprietary' taints kernel.
[   39.200501] wl: module verification failed: signature and/or required key missing - tainting kernel
[   39.204468] rtl8188ee 0000:02:00.0 wlan1: renamed from wlan0
[   47.977334] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.004471] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 3 times)
[   53.017759] wlan1: authenticate with <MAC 'Hermes' [AC1]>
[   53.027885] wlan1: send auth to <MAC 'Hermes' [AC1]> (try 1/3)
[   53.029952] wlan1: authenticated
[   53.032040] wlan1: associate with <MAC 'Hermes' [AC1]> (try 1/3)
[   53.035781] wlan1: RX AssocResp from <MAC 'Hermes' [AC1]> (capab=0x431 status=0 aid=2)
[   53.036097] wlan1: associated
[   54.162396] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready



```

---

### Post by chili555 on 2018-09-11
dmesg looks much better but not perfect.> [   39.198740] wl: loading out-of-tree module taints kernel.
[   39.198745] wl: module license 'MIXED/Proprietary' taints kernel.
[   39.200501] wl: module verification failed: signature and/or required key missing - tainting kernelIt might help to remove the Broadcom, presumably incorrect, driver:```
sudo apt purge bcmwl-kernel-source
```Reboot.

Any improvement?

---

### Post by aaparise on 2018-09-11
No improvement. New dmesg:

```
##### dmesg #############################

[   36.642192] rtl8188ee: rtl8188ee: Power Save off (module option)
[   36.642193] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   36.642204] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   37.476200] r8169 0000:01:00.0 eth0: link down
[   37.476286] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.476327] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   37.476556] rtlwifi: rtlwifi: wireless switch is on
[   38.356488] wl: loading out-of-tree module taints kernel.
[   38.356494] wl: module license 'MIXED/Proprietary' taints kernel.
[   38.358402] wl: module verification failed: signature and/or required key missing - tainting kernel
[   38.362960] rtl8188ee 0000:02:00.0 wlan1: renamed from wlan0
[   47.932672] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.136021] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 3 times)
[   66.822535] wlan1: authenticate with <MAC 'Hermes' [AC1]>
[   66.832686] wlan1: send auth to <MAC 'Hermes' [AC1]> (try 1/3)
[   66.834516] wlan1: authenticated
[   66.836104] wlan1: associate with <MAC 'Hermes' [AC1]> (try 1/3)
[   66.839784] wlan1: RX AssocResp from <MAC 'Hermes' [AC1]> (capab=0x431 status=0 aid=1)
[   66.840029] wlan1: associated
[   67.154427] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready



```

---

### Post by chili555 on 2018-09-11
We wonder why this is still present.> [   38.356488] wl: loading out-of-tree module taints kernel.
[   38.356494] wl: module license 'MIXED/Proprietary' taints kernel.
[   38.358402] wl: module verification failed: signature and/or required key missing - tainting kernel Please show us:```
sudo dpkg -s bcmwl-kernel-source | grep Status
history | grep purge
```Did you reboot?

---

### Post by aaparise on 2018-09-11
```
sudo dpkg -s bcmwl-kernel-source | grep Status 
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
aparise@Daedalus:~$ history | grep purge
  585  sudo apt-get purge unity8-desktop-session-mir
  673  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  679  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  760  sudo apt-get purge wicd wicd-gtk
  765  sudo apt-get purge wicd wicd-gtk
  801  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  841  sudo apt-get remove --purge flashplugin-installer
  898  sudo apt-get remove --purge flashplugin-installer
  900  sudo apt-get remove --purge flashplugin-installer
  903  sudo apt-get remove --purge flashplugin-installer
  996  sudo apt-get purge bluez # remove old versions
 1300  sudo apt-get remove --purge ttf-mscorefonts-installer
 1308  sudo apt --purge --reinstall install ttf-mscorefonts-installer
 1434  sudo apt install ppa-purge
 1435  sudo ppa-purge ppa:morphis/anbox-support
 1546  sudo apt-get purge wicd
 1580  sudo apt purge bcmwl-kernel-source
 1583  history | grep purge



```

---

### Post by chili555 on 2018-09-11
I haven't any clues so far. Does it actually load?```
lsmod | grep wl

```If so, blacklist it:```
sudo -i
echo "blacklist wl"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r wl
exit
```Wierd.

---

### Post by aaparise on 2018-09-11
I don't understand what you mean by "[COLOR=#000000]Does it actually load?[/COLOR]", but here is the result of that command:

 lsmod | grep wl


wl                   6447104  0
cfg80211              622592  3 wl,mac80211,rtlwifi

---

### Post by aaparise on 2018-09-11
In case the spacing of that is important:
```

wl                   6447104  0
cfg80211              622592  3 wl,mac80211,rtlwifi



```

---

### Post by chili555 on 2018-09-11
Please proceed with the blacklist, reboot and show us:```
dmesg | grep -e rtl -e wlan
```Very weird!

---

### Post by aaparise on 2018-09-11
```

[   37.985031] rtl8188ee: rtl8188ee: Power Save off (module option)
[   37.985032] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   37.985082] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   39.011130] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   39.011341] rtlwifi: rtlwifi: wireless switch is on
[   39.013402] rtl8188ee 0000:02:00.0 wlan1: renamed from wlan0
[   51.739359] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   52.202986] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   52.351382] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   56.870220] wlan1: authenticate with f0:fc:c8:fd:18:f9
[   56.880334] wlan1: send auth to f0:fc:c8:fd:18:f9 (try 1/3)
[   56.888269] wlan1: authenticated
[   56.892112] wlan1: associate with f0:fc:c8:fd:18:f9 (try 1/3)
[   56.895893] wlan1: RX AssocResp from f0:fc:c8:fd:18:f9 (capab=0x431 status=0 aid=1)
[   56.896178] wlan1: associated
[   57.042233] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready



```

---

### Post by chili555 on 2018-09-12
Much better! Are the slow-downs gone now?

---

### Post by aaparise on 2018-09-12
> **chili555 said:**
> Much better! Are the slow-downs gone now?


No, no change.

---

### Post by aaparise on 2018-09-13
> **aaparise said:**
> No, no change.

Well, that was yesterday.  It slowed after I made all the changes ( yes, I rebooted ), and it was getting late, so I quit for the day.

Today was different.  It didn't slow down once. I am hoping this is solved.

Thanks for all your help.

---

### Post by chili555 on 2018-09-13
> Today was different. It didn't slow down once. I am hoping this is solved.
I hope so, too. I am just about out of ideas.

---

### Post by aaparise on 2018-09-20
This is hard to believe, but after a week of working perfectly, it happened again.

---

### Post by chili555 on 2018-09-20
Are there any clues in the log?```
dmesg | grep -e rtl -e wlan
```

---

### Post by aaparise on 2018-09-21
> **chili555 said:**
> We wonder why this is still present. Please show us:```
sudo dpkg -s bcmwl-kernel-source | grep Status
history | grep purge
```Did you reboot?

I rebooted since this happened.  It didn't take a reboot to get the higher speed back, just a disable and re-enable of the WIFI.

Your request:

```
aparise@Daedalus:~$ sudo dpkg -s bcmwl-kernel-source | grep Status[sudo] password for aparise: 
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
aparise@Daedalus:~$ history | grep purge
  673  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  679  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  760  sudo apt-get purge wicd wicd-gtk
  765  sudo apt-get purge wicd wicd-gtk
  801  sudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
  841  sudo apt-get remove --purge flashplugin-installer
  898  sudo apt-get remove --purge flashplugin-installer
  900  sudo apt-get remove --purge flashplugin-installer
  903  sudo apt-get remove --purge flashplugin-installer
  996  sudo apt-get purge bluez # remove old versions
 1300  sudo apt-get remove --purge ttf-mscorefonts-installer
 1308  sudo apt --purge --reinstall install ttf-mscorefonts-installer
 1434  sudo apt install ppa-purge
 1435  sudo ppa-purge ppa:morphis/anbox-support
 1546  sudo apt-get purge wicd
 1580  sudo apt purge bcmwl-kernel-source
 1583  history | grep purge
 1601  sudo apt-get purge arp-scan
 1605  history | grep purge
aparise@Daedalus:~$ 



```

---

### Post by aaparise on 2018-09-21
> **chili555 said:**
> Are there any clues in the log?```
dmesg | grep -e rtl -e wlan
```

Sorry, I got confused and answered the wrong question.
Here is the correct output:

```
aparise@Daedalus:~$ dmesg | grep -e rtl -e wlan[   36.950730] rtl8188ee: rtl8188ee: Power Save off (module option)
[   36.950731] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   36.950774] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   37.036358] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   37.036638] rtlwifi: rtlwifi: wireless switch is on
[   37.040140] rtl8188ee 0000:02:00.0 wlan1: renamed from wlan0
[   37.111382] Modules linked in: crc32_pclmul snd_hda_codec arc4 snd_hda_core rtl8188ee ghash_clmulni_intel snd_hwdep cryptd rtl_pci snd_pcm rtlwifi snd_seq_midi mac80211 snd_seq_midi_event binfmt_misc intel_cstate cfg80211 intel_rapl_perf hid_multitouch snd_rawmidi joydev mei_me mei snd_seq snd_seq_device snd_timer input_leds serio_raw hp_wmi wmi_bmof sparse_keymap rtsx_pci_ms memstick lpc_ich snd mac_hid soundcore shpchp hp_wireless sch_fq_codel iptable_filter ip6table_filter ip6_tables br_netfilter bridge stp llc arp_tables parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect psmouse sysimgblt fb_sys_fops rtsx_pci ahci wmi drm libahci r8169 mii video
[   55.960454] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   56.380936] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   56.464750] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   57.751267] wlan1: authenticate with f0:fc:c8:fd:18:f9
[   57.761377] wlan1: send auth to f0:fc:c8:fd:18:f9 (try 1/3)
[   57.763914] wlan1: authenticated
[   57.768078] wlan1: associate with f0:fc:c8:fd:18:f9 (try 1/3)
[   57.773586] wlan1: RX AssocResp from f0:fc:c8:fd:18:f9 (capab=0x431 status=0 aid=1)
[   57.773860] wlan1: associated
[   58.045300] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 6725.168162] wlan1: deauthenticating from f0:fc:c8:fd:18:f9 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6727.790695] rtlwifi: rtlwifi: wireless switch is on
[ 6731.030665] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6731.457375] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6731.513497] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6732.381125] wlan1: authenticate with f0:fc:c8:fd:18:f9
[ 6732.391265] wlan1: send auth to f0:fc:c8:fd:18:f9 (try 1/3)
[ 6732.393077] wlan1: authenticated
[ 6732.396218] wlan1: associate with f0:fc:c8:fd:18:f9 (try 1/3)
[ 6732.399881] wlan1: RX AssocResp from f0:fc:c8:fd:18:f9 (capab=0x431 status=0 aid=1)
[ 6732.400234] wlan1: associated
[ 6732.409123] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 8604.573166] wlan1: deauthenticating from f0:fc:c8:fd:18:f9 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 8606.458966] rtlwifi: rtlwifi: wireless switch is on
[ 8607.204104] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 8607.631243] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 8607.682825] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 8608.547207] wlan1: authenticate with f0:fc:c8:fd:18:f9
[ 8608.557332] wlan1: send auth to f0:fc:c8:fd:18:f9 (try 1/3)
[ 8608.563565] wlan1: authenticated
[ 8608.564660] wlan1: associate with f0:fc:c8:fd:18:f9 (try 1/3)
[ 8608.568390] wlan1: RX AssocResp from f0:fc:c8:fd:18:f9 (capab=0x431 status=0 aid=1)
[ 8608.568657] wlan1: associated
[ 8608.577044] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
aparise@Daedalus:~$ 



```

---

### Post by aaparise on 2018-09-25
It happened again, this time soon after boot.  I have not rebooted or even re-enabled the WIFI yet:

```
aparise@Daedalus:~$ dmesg | grep -e rtl -e wlan
[   40.798662] rtl8188ee: rtl8188ee: Power Save off (module option)
[   40.798663] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   40.798678] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   41.093894] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   41.094141] rtlwifi: rtlwifi: wireless switch is on
[   41.096503] rtl8188ee 0000:02:00.0 wlan1: renamed from wlan0
[   54.096882] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   54.520205] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   54.656908] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   72.411713] wlan1: authenticate with f0:fc:c8:fd:18:f9
[   72.421838] wlan1: send auth to f0:fc:c8:fd:18:f9 (try 1/3)
[   72.423673] wlan1: authenticated
[   72.424058] wlan1: associate with f0:fc:c8:fd:18:f9 (try 1/3)
[   72.427717] wlan1: RX AssocResp from f0:fc:c8:fd:18:f9 (capab=0x431 status=0 aid=1)
[   72.427961] wlan1: associated
[   72.851961] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
aparise@Daedalus:~$ 



```

---

