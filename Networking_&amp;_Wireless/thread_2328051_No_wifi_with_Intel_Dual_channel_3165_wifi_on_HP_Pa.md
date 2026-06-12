---
title: "No wifi with Intel Dual channel 3165 wifi on HP Pavilion x360 and Ubuntu 16.04"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by telma-woerle on 2016-06-16
I installed ubuntu 16.04 on a HP Pavilion x360 3m-u001dx and the wifi is not working. On windows it is working fine. It does not have wired connection.

I already tried some fix suggestions for ubuntu 15.04 and the wifi still not working.

Follows some more information

**iwlwifi.conf**
*remove iwlwifi \*
*(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwlwifi | xargs /sbin/rmmod) \ && /sbin/modprobe -r mac80211*
*options iwlwifi 11n_disable=1*


telma@telma-HP-Pavilion-x360-m3-Convertible:~$ lsmod | grep -e iwl -e 80211
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm

telma@telma-HP-Pavilion-x360-m3-Convertible:~$ sudo modprobe iwldvm


telma@telma-HP-Pavilion-x360-m3-Convertible:~$ dmesg | grep iwl
[    7.243173] iwlwifi 0000:01:00.0: Unsupported splx structure
[    7.258092] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    7.258107] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    7.258116] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[    7.315051] iwlwifi 0000:01:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    7.907809] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    7.908155] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.908605] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    8.062509] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    8.076122] iwlwifi 0000:01:00.0 wlo1: renamed from wlan0
[   29.008400] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   29.009019] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   29.069593] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   29.070048] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   50.690378] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   50.690833] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   50.752495] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[   50.752946] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled


telma@telma-HP-Pavilion-x360-m3-Convertible:~$ iwconfig
wlo1      IEEE 802.11abg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          
lo        no wireless extensions.

---

