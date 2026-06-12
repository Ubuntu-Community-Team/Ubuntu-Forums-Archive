---
title: "Solutions to the 64Bit Wifi Broadcom Ndiswrapper problem on Ubuntu"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by sidewalkcynic on 2014-04-30
How about a 32 bit Ubuntu on the 64 bit machine (USB installation), and use the bcmn43xx32.inf file?

If anybody knows the drawbacks/sacrifices, please let it be known.

---

### Post by chili555 on 2014-04-30
The only drawback i can think of is that it simply won't work. There have been plenty of cases of mismatch between 32- and 64-bit in ndiswrapper and, invariably, the same error is thrown; something like:> [ 12.273556] ndiswrapper (check_nt_hdr:150): **kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B**
[ 12.273565] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2860'
[ 12.274422] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'It only takes a few moments to try it yourself. Please go ahead and let us hear your report.

---

### Post by sidewalkcynic on 2014-04-30
Same problem, however, it does not cut out as quickly - I was able to download update, and Ndiswrapper utils, and view quite a few pages before it quit.
```
lunaphiles@CircuitCircus:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:91:13:A0:F9   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

lunaphiles@CircuitCircus:~$ dmesg | grep ndis
[  171.012955] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  171.304420] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  171.563805] usbcore: registered new interface driver ndiswrapper
lunaphiles@CircuitCircus:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        10:0D:7F:32:B1:74

  Capabilities:
    Speed:           117 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    belkin.a74:      Infra, 08:86:3B:7E:0A:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    linksys-madina:  Infra, 00:22:6B:52:55:CB, Freq 2452 MHz, Rate 54 Mb/s, Strength 64 WEP
    *dlink:          Infra, 00:21:91:13:A0:F9, Freq 2422 MHz, Rate 54 Mb/s, Strength 78
    optimumwifi:     Infra, 22:4E:7F:18:69:18, Freq 2437 MHz, Rate 54 Mb/s, Strength 57
    186918:          Infra, 20:4E:7F:18:69:17, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    E56CA2:          Infra, 04:A1:51:E5:6C:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    optimumwifi:     Infra, 06:A1:51:CB:D0:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    IVAN:            Infra, E0:46:9A:7A:1F:0A, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    butt:            Infra, C0:C1:C0:B8:9F:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    optimumwifi:     Infra, 92:03:D8:83:5A:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    CBD050:          Infra, 04:A1:51:CB:D0:4F, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    835A24:          Infra, 00:03:D8:83:5A:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    807164:          Infra, 00:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    NETGEAR51:       Infra, 28:C6:8E:1A:05:11, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    optimumwifi:     Infra, 92:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    optimumwifi:     Infra, 06:A1:51:E5:6C:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 49
    butt-guest:      Infra, C0:C1:C0:B8:9F:8D, Freq 2412 MHz, Rate 54 Mb/s, Strength 40

  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:26:2D:16:52:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


lunaphiles@CircuitCircus:~$ cat /var/logsyslog | grep -e etwork -e wlan | tail -n20
cat: /var/logsyslog: No such file or directory
lunaphiles@CircuitCircus:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Apr 30 09:50:41 CircuitCircus NetworkManager[971]: <info>   gateway 192.168.0.1
Apr 30 09:50:41 CircuitCircus NetworkManager[971]: <info>   nameserver '192.168.0.1'
Apr 30 09:50:41 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 30 09:50:41 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 30 09:50:41 CircuitCircus avahi-daemon[814]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.187.
Apr 30 09:50:41 CircuitCircus avahi-daemon[814]: New relevant interface wlan0.IPv4 for mDNS.
Apr 30 09:50:41 CircuitCircus avahi-daemon[814]: Registering new address record for 192.168.0.187 on wlan0.IPv4.
Apr 30 09:50:42 CircuitCircus NetworkManager[971]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 30 09:50:42 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 30 09:50:42 CircuitCircus NetworkManager[971]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 30 09:50:42 CircuitCircus NetworkManager[971]: <info> Policy set 'dlink' (wlan0) as default for IPv4 routing and DNS.
Apr 30 09:50:42 CircuitCircus NetworkManager[971]: <info> Writing DNS information to /sbin/resolvconf
Apr 30 09:50:43 CircuitCircus avahi-daemon[814]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::120d:7fff:fe32:b174.
Apr 30 09:50:43 CircuitCircus avahi-daemon[814]: New relevant interface wlan0.IPv6 for mDNS.
Apr 30 09:50:43 CircuitCircus avahi-daemon[814]: Registering new address record for fe80::120d:7fff:fe32:b174 on wlan0.*.
Apr 30 09:50:52 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) successful, device activated.
Apr 30 09:51:01 CircuitCircus NetworkManager[971]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 30 09:51:01 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 30 09:51:01 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 30 09:51:01 CircuitCircus NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
lunaphiles@CircuitCircus:~$ 
```

I think I am going to see if I can find a Trendnet TEW-649UB - seems to be the best/only recommendation I have seen around here, and it less than $20.

---

### Post by sidewalkcynic on 2014-04-30
Yes, the Trendnet TEW-649UB is the best solution - $14.14 + subway fare.

Worked out of the box.

---

