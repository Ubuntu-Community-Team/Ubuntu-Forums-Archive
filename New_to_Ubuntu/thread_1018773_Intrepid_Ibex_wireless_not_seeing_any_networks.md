---
title: "Intrepid Ibex wireless not seeing any networks"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by robertocastro on 2008-12-22
I am new to linux.  Installed ubuntu 8.10 on a presario a900.  The first problem I encountered was the driver for the atheros wireless card, but resolved the issue with backports-modules.  but now the wireless, though enabled, doesn't see my wireless network.  I tried connecting to hidden networks, entered the ssid and the wep key but thats where the i get caught in a circle.  after i click to connect to the hidden network it tries for a good 30 seconds then asks for the wep key again, over again.  how do i get network manager to see my network, or any network for that matter, or get connected to my hidden network?  I'll try disabling all security on my router and any help would be greatly appreciated.

---

### Post by wolfen69 on 2008-12-22
did you blacklist the appropriate modules after doing the backports-modules thing?
this can be accomplished by: ```
sudo -s
echo blacklist ath_pci >> /etc/modprobe.d/blacklist
``` then restart.  after that click the network icon on the taskbar to see what comes up.

---

### Post by robertocastro on 2008-12-22
blacklisting per the commands provided produced no difference in network detection.  neither did disabling all security for the router.

---

### Post by wolfen69 on 2008-12-22
do
```
lspci
``` and post the results here.

---

### Post by robertocastro on 2008-12-22
the output of iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


and the output of lsmod | grep "ath"
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
and lshw -C network says network is disabled but the router is working with another laptop running windows:confused:

---

### Post by robertocastro on 2008-12-22
lspci output
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by wolfen69 on 2008-12-22
is atheros activated in system>administration>hardware drivers?

---

### Post by robertocastro on 2008-12-22
yes support for 5xxx series of atheros 802.11 wireless lan cards is activated...
and I want to say I appreciate you taking the time to help me out with this issue.

---

### Post by robertocastro on 2008-12-22
I have made a clean install and decided that first i must get the wireless working.  I inserted the cd image and reloaded it.  then install linux-backports-modules-intrepid-generic.  blacklisted ath_pci and ath_hal and proceeded to reboot.  Under system-administration-hardware drivers the new driver(5xxx series...) is loaded and active with the original one being deactivated.  though networkmanager now gives me the option of wireless networks it does not scan for and see any.  I have already tried the compat-wireless and ndiswrapper but all give me the same result a recognized wireless card that can't recognize wireless networks.  Any suggestions? Thanks in advance :)

---

