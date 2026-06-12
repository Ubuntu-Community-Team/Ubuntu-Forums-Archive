---
title: "Ad-Hoc ubuntu 12.04"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by Aline_G on 2013-10-22
Hi all,

I'm trying to use a Ad-Hoc wireless network on my ubuntu 12.04.
I followed the instructions from:
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
I don't have gnome so I tried the Wireless Extensions CLI tools Method & the Interface file method.

In both cases I get:
[ 1101.155364] wl12xx: ERROR watchdog interrupt received! starting recovery.
[ 1103.166870] wl12xx: ERROR command complete timeout
[ 1103.177612] wl12xx: ERROR Could not add or replace key
[ 1103.183197] ieee80211 phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-110)
[ 1105.198089] wl12xx: ERROR command complete timeout
[ 1105.205047] wl12xx: ERROR failed to send stop firmware logger command
[ 1107.846710] wl12xx: ERROR command complete timeout
[ 1107.861022] wl12xx: ERROR failed to initiate cmd role enable
[ 1107.869934] wl12xx: ERROR watchdog interrupt received! starting recovery.
[ 1109.893402] wl12xx: ERROR command complete timeout
[ 1109.903167] wl12xx: ERROR Could not add or replace key
[ 1109.915832] ieee80211 phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-110)
[ 1111.924652] wl12xx: ERROR command complete timeout
[ 1111.931030] wl12xx: ERROR failed to send stop firmware logger command
[ 1114.573089] wl12xx: ERROR command complete timeout
[ 1114.587677] wl12xx: ERROR failed to initiate cmd role enable
[ 1116.612182] wl12xx: ERROR command complete timeout
[ 1116.626617] wl12xx: ERROR Could not add or replace key

right after the activation: sudo ip link set wlan0 up

when I enter sudo iwconfig wlan0 I get:wlan0  IEEE 802.11abgn  ESSID:"TEST"  
          Mode:Ad-Hoc  Frequency:2.427 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1234-5678-90
          Power Management:on

Does anyone knows this problem? how to solve it?

Thank you!
Aline :)

---

