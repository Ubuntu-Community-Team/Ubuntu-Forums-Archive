---
title: "Various medium to minor internet problems."
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Raziel-chan on 2008-07-03
Well, I'm still amazed how first Ubuntu and then Kubuntu (after installing kdm) handled my wireless card without problem, while in wXP I had to first install the drivers, then put in the card. Still, not everything is perfect:

1. The bug I read about, involving improper frequency reporting in the knetworkmanager gui, persists. My connections, set on channel 11, is reported as 0.000 GHZ frequency. Also, signal strength is kind of wonky, as it seems to be fluctuating between ~50% and ~80%, despite that I changed the xmit power of the router from 28 to 50 mW.

Here's the output of nm-tool:

> razielchan@razielchan-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            forcedeth
  Active:            no
  HW Address:        [shroud of secrecy]

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes

  Wired Settings
    Hardware Link:   no


- Device: wlan0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/wlan0
  Type:              802.11 Wireless
  Driver:            rt61pci
  Active:            yes
  HW Address:        [shroud of secrecy]

  Capabilities:
    Supported:       yes
    Speed:           54 Mb/s

  Wireless Settings
    Scanning:        yes
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Networks (* = Current Network)
    *Doregan Tech:   Infrastructure Mode, Freq 0.000 MHz, Rate 62 Mb/s, Strength                                                               50%, Encrypted (WEP)
    MisOl:           Infrastructure Mode, Freq 0.000 MHz, Rate 62 Mb/s, Strength                                                               48%, Encrypted (WPA WPA2)
    Jurand:          Infrastructure Mode, Freq 0.000 MHz, Rate 62 Mb/s, Strength                                                               47%, Encrypted (WEP)

  IP Settings:
    IP Address:      192.168.1.111
    Subnet Mask:     255.255.255.0
    Broadcast:       192.168.1.255
    Gateway:         192.168.1.1
    Primary DNS:     192.168.1.1
    Secondary DNS:   0.0.0.0

Note the improper network bandwidth rates.

> razielchan@razielchan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Doregan Tech"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:A4:0B:FB
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Link Quality=87/100  Signal level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I'm using a WMP54G card and Wrt54GL router with DD-WRT v23 SP2.

2. The second problem arises when I first disable the wireless device/switch to offline mode and then enable the wireless device/switch to online mode. What happens is that the OS halts... And then simply restarts itself.

An excerpt from syslog:

> Jul  3 16:25:02 (none) /USR/SBIN/CRON[6793]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul  3 16:35:01 (none) /USR/SBIN/CRON[6952]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul  3 16:37:55 (none) NetworkManager: <info>  Going to sleep. 
Jul  3 16:37:55 (none) kernel: [ 1734.625032] wlan0: deauthenticate(reason=3)
Jul  3 16:37:55 (none) dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6465
Jul  3 16:37:55 (none) dhclient: killed old client process, removed PID file
Jul  3 16:37:55 (none) dhclient: wmaster0: unknown hardware address type 801
Jul  3 16:38:51 (none) syslogd 1.5.0#1ubuntu1: restart.
Jul  3 16:38:52 (none) kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul  3 16:38:52 (none) kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jul  3 16:38:52 (none) kernel: Symbols match kernel version 2.6.24.
Jul  3 16:38:52 (none) kernel: Loaded 33208 symbols from 97 modules.

Another one, right before that previous one:

> Jul  3 16:15:01 razielchan-desktop /USR/SBIN/CRON[26657]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jul  3 16:17:01 razielchan-desktop /USR/SBIN/CRON[26664]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 16:18:07 razielchan-desktop NetworkManager: <info>  User request to disable wireless. 
Jul  3 16:18:07 razielchan-desktop NetworkManager: <info>  Deactivating device wlan0. 
Jul  3 16:18:07 razielchan-desktop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6342
Jul  3 16:18:07 razielchan-desktop dhclient: killed old client process, removed PID file
Jul  3 16:18:07 razielchan-desktop dhclient: wmaster0: unknown hardware address type 801
Jul  3 16:18:07 razielchan-desktop dhclient: wmaster0: unknown hardware address type 801
Jul  3 16:18:07 razielchan-desktop dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Jul  3 16:18:08 razielchan-desktop avahi-daemon[5286]: Withdrawing address record for 192.168.1.111 on wlan0.
Jul  3 16:18:08 razielchan-desktop avahi-daemon[5286]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.111.
Jul  3 16:18:08 razielchan-desktop avahi-daemon[5286]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul  3 16:18:08 razielchan-desktop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jul  3 16:18:08 razielchan-desktop dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Jul  3 16:18:08 razielchan-desktop kernel: [515654.773973] wlan0: deauthenticate(reason=3)
Jul  3 16:18:09 razielchan-desktop avahi-daemon[5286]: Withdrawing address record for fe80::21c:10ff:fee4:12d2 on wlan0.
Jul  3 16:18:19 (none) syslogd 1.5.0#1ubuntu1: restart.
Jul  3 16:18:19 (none) kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul  3 16:18:20 (none) kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jul  3 16:18:20 (none) kernel: Symbols match kernel version 2.6.24.
Jul  3 16:18:20 (none) kernel: Loaded 33208 symbols from 97 modules.

I'll be glad for any help I can get. And thanks in advance.

cya
Raziel-chan

---

