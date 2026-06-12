---
title: "DWL-G520 as access point"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by wroopy on 2006-09-25
Hello!

I've configured my DWL-G520 as an access-point. I can now attach to it from my Laptop (based on Intel 2200BG) running Windows XP. The laptop connects at 54Mbps and signal strength is 4 of 5.
The connections works fine for a few minutes, but then the spped/rate is getting lower and lower until the connections is dropped. My Laptop reestablish the connection at 54 Mbps and the speed is getting lower and lower.  Then it keeps (dis)function like this.

If I connect my LapTop to my Netgear WGT624, it connects at 54 Mbps and then the speed could be lowered and also raised.

I'd like to have the same functionality with my Ubuntu-based (Dapper 6.06.1) firewall.

Any suggestins on what configuration I should do?

My wirless card is bridged together with my internal networkcard.

Below are the configuration from /etc/network/interfaces, iwconfig, lspci and dmesg. 

#/etc/network/interfaces
auto eth0 ath0 br0
iface eth0 inet dhcp
iface ath0 inet manual
    wireless-mode master
    wireless-essid DahlenTest
    wireless-key xxxxxxxxx
    post-up iwpriv ath0 mode 3
iface br0 inet static
    bridge_ports eth1 ath0
    address 10.0.1.1
    netmask 255.255.255.0


#iwconfig ath0
ath0      IEEE 802.11g  ESSID:"DahlenTest"
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:13:46:94:B4:1B
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:B033-1311-66   Security mode:restricted
          Power Management:off
          Link Quality=94/94  Signal level=-1 dBm  Noise level=-95 dBm
          Rx invalid nwid:742  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:366  Invalid misc:366   Missed beacon:0

#lspci -v
0000:00:11.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc DWL-G520 Wireless PCI Adapter rev. B
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at fa000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

# dmesg
[17179582.888000] ath_hal: module license 'Proprietary' taints kernel.
[17179582.892000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179583.192000] ath_rate_sample: 1.2
[17179583.208000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179584.704000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179584.704000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179584.704000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179584.704000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179584.704000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179584.704000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179584.704000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179584.704000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179584.704000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179584.704000] ath0: Use hw queue 8 for CAB traffic
[17179584.704000] ath0: Use hw queue 9 for beacons
[17179584.704000] ath0: Atheros 5212: mem=0xfa000000, irq=10
[17179589.116000] device ath0 entered promiscuous mode
[17179589.128000] br0: port 2(ath0) entering learning state
[17179591.772000] ath0: creating bss 00:13:46:94:b4:1b
[17179604.128000] br0: port 2(ath0) entering forwarding state


/Andreas

---

