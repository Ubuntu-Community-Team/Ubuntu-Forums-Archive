---
title: "Failed to initialize control interface '/run/wpa_supplicant'"
date: 2020-02-24
forum: Networking &amp; Wireless
---

### Post by nonick95 on 2020-02-24
i have an ubuntu server 16.04 with 1 NIC and 1 wifi, 
i want them to be up and running together, was thinking simple mission but apparently not so simple..

this is my /etc/network/interfaces file

```
auto lo
iface lo inet loopback


auto wlp1s0
iface wlp1s0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 8.8.8.8
wpa-ssid linksys
wpa-psk password


auto eno1
iface eno1 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.2.254
dns-nameservers 8.8.8.8

```

after a reboot i run

```
systemctl status networking.service

networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Mon 2020-02-24 19:00:08 IST; 4min 31s ago
     Docs: man:interfaces(5)
  Process: 1045 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 993 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo
 Main PID: 1045 (code=exited, status=1/FAILURE)




Feb 24 19:00:08 srv1 wpa_supplicant[1469]: Delete '/run/wpa_supplicant/wlp1s0' manually if it is not used anymore
Feb 24 19:00:08 srv1 wpa_supplicant[1469]: Failed to initialize control interface '/run/wpa_supplicant'.
                                                  You may have another wpa_supplicant process already running or the file was
                                                  left by an unclean termination of wpa_supplicant in which case you will need
                                                  to manually remove this file before starting wpa_supplicant again.
Feb 24 19:00:08 srv1 wpa_supplicant[1469]: nl80211: deinit ifname=wlp1s0 disabled_11b_rates=0
Feb 24 19:00:08 srv1 ifup[1045]: /etc/network/if-pre-up.d/wpasupplicant: 120: /etc/network/if-pre-up.d/wpasupplicant: cannot
Feb 24 19:00:08 srv1 ifup[1045]: run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Feb 24 19:00:08 srv1 ifup[1045]: Failed to bring up wlp1s0.
Feb 24 19:00:08 srv1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Feb 24 19:00:08 srv1 systemd[1]: Failed to start Raise network interfaces.
Feb 24 19:00:08 srv1 systemd[1]: networking.service: Unit entered failed state.
Feb 24 19:00:08 srv1 systemd[1]: networking.service: Failed with result 'exit-code'.





```

if i leave only one interface (wlp1s0 or eno1) in the /etc/network/interfaces file the interface will go up after a reboot \ service restart  successfully 


please your advice

---

