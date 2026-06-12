---
title: "Wireless will not connect at boot"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by dernwine on 2006-10-12
Having an interesting problem, which will turn out to be a stupid mistake on my part...

On Ubuntu LTS when I boot my desktop the wirless interface (ath0) is not started by default. Starting the wireless assistant (wlassistant) app and
connecting to the interface once the desktop is booted DOES work, however. 
I've tried commenting out the unused interfaces out of the /etc/network/interfaces file (eth0, eth1, eth2) and rebooted with no success, actually wlassistant doesn't like it if you try to comment out those i/f's.

Here is my interfaces file:

root@groucho:/etc/network# cat interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid xxxxxxxxx
wireless-key s:xxxxxxxxx

auto wlan0
iface wlan0 inet dhcp

Can anyone explain to me what I need to do to get the ath0 i/f
to come up automatically at system boot?


TIA,
David

---

### Post by dernwine on 2006-10-12
Some additional info that may/may not be helpful:
Output from iwconfig:

ath0      IEEE 802.11g  ESSID:"xxxxxxx"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:FF:30:7A
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:B7A8-ED04-7B   Security mode:open
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:8542  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

