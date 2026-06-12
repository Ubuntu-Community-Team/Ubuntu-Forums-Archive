---
title: "Mobile Broadband connected but no internet access"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by medin2014 on 2015-10-22
```
yesterday i upgraded my ubuntu version from 15.04 to 15.10, my mobile 3G broadband is correctly connected but when i try to access to internet i can't, here's my system log if anyone can help me:

Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): Activation: starting connection 'Medi Telecom Abonnement 1' (da0c734a-986b-4ede-a9e5-28310ad58318)
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  NetworkManager state is now CONNECTING
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: prepare -> need-auth (reason 'none') [40 60 0]
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect started...
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect state (4/8): Wait to get fully enabled
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect state (5/8): Register
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect state (6/8): Bearer
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect state (7/8): Connect
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (registered -> connecting)
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): modem state changed, 'registered' --> 'connecting' (reason: user-requested)
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (connecting -> connected)
Oct 22 10:43:01 mohamed-ubuntumate ModemManager[752]: <info>  Simple connect state (8/8): All done
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): modem state changed, 'connecting' --> 'connected' (reason: user-requested)
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <warn>  (ttyUSB0): failed to look up interface index
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <warn>  (ttyUSB0): interface ttyUSB0 not up for IP configuration
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): using modem-specified IP timeout: 20 seconds
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  starting PPP connection
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  pppd started with pid 6019
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): IPv6 configuration disabled
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: Plugin /usr/lib/pppd/2.4.6/nm-pppd-plugin.so loaded.
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: Plugin /usr/lib/pppd/2.4.6/nm-pppd-plugin.so loaded.
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (plugin_init): initializing
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: pppd 2.4.6 started by root, uid 0
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): new Generic device (carrier: UNKNOWN, driver: 'unknown', ifindex: 18)
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: Using interface ppp0
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: Using interface ppp0
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: Connect: ppp0 <--> /dev/ttyUSB0
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: Connect: ppp0 <--> /dev/ttyUSB0
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: <info>  device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: CHAP authentication succeeded
Oct 22 10:43:01 mohamed-ubuntumate pppd[6019]: CHAP authentication succeeded
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: CHAP authentication succeeded
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: CHAP authentication succeeded
Oct 22 10:43:01 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Oct 22 10:43:04 mohamed-ubuntumate pppd[6019]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: local  IP address 197.247.23.154
Oct 22 10:43:04 mohamed-ubuntumate pppd[6019]: local  IP address 197.247.23.154
Oct 22 10:43:04 mohamed-ubuntumate pppd[6019]: remote IP address 10.64.64.64
Oct 22 10:43:04 mohamed-ubuntumate pppd[6019]: primary   DNS address 8.8.8.8
Oct 22 10:43:04 mohamed-ubuntumate pppd[6019]: secondary DNS address 41.214.140.5
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  keyfile: add connection in-memory (6fc663cf-d629-4ef8-80c0-fed721c9b0e0,"ppp0")
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: remote IP address 10.64.64.64
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: primary   DNS address 8.8.8.8
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: secondary DNS address 41.214.140.5
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_phasechange): status 9 / phase 'running'
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_ip_up): ip-up event
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: nm-pppd-plugin-Message: nm-ppp-plugin: (nm_ip_up): sending IPv4 config to NetworkManager...
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  Device 'ppp0' has no connection; scheduling activate_check in 0 seconds.
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): Activation: starting connection 'ppp0' (6fc663cf-d629-4ef8-80c0-fed721c9b0e0)
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  PPP manager (IPv4 Config Get) reply received.
Oct 22 10:43:04 mohamed-ubuntumate whoopsie[772]: [10:43:04] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <warn>  (ppp0): arping could not be found; no ARPs will be sent
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  NetworkManager state is now CONNECTED_LOCAL
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  Policy set 'Medi Telecom Abonnement 1' (ppp0) as default for IPv4 routing and DNS.
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  Writing DNS information to /sbin/resolvconf
Oct 22 10:43:04 mohamed-ubuntumate dnsmasq[2003]: setting upstream servers from DBus
Oct 22 10:43:04 mohamed-ubuntumate dnsmasq[2003]: using nameserver 8.8.8.8#53
Oct 22 10:43:04 mohamed-ubuntumate dnsmasq[2003]: using nameserver 41.214.140.5#53
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ttyUSB0): Activation: successful, device activated.
Oct 22 10:43:04 mohamed-ubuntumate dbus[721]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 22 10:43:04 mohamed-ubuntumate whoopsie[772]: [10:43:04] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/25
Oct 22 10:43:04 mohamed-ubuntumate whoopsie[772]: [10:43:04] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/14
Oct 22 10:43:04 mohamed-ubuntumate NetworkManager[779]: <info>  (ppp0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Oct 22 10:43:04 mohamed-ubuntumate dbus[721]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 22 10:43:04 mohamed-ubuntumate nm-dispatcher: Dispatching action 'up' for ppp0
Oct 22 10:43:04 mohamed-ubuntumate whoopsie[772]: [10:43:04] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Stopping LSB: Start NTP daemon...
Oct 22 10:43:04 mohamed-ubuntumate ntp[6117]: * Stopping NTP server ntpd
Oct 22 10:43:04 mohamed-ubuntumate ntpd[5944]: ntpd exiting on signal 15
Oct 22 10:43:04 mohamed-ubuntumate ntp[6117]: ...done.
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Stopped LSB: Start NTP daemon.
Oct 22 10:43:04 mohamed-ubuntumate ntpdate[6126]: name server cannot be used: Temporary failure in name resolution (-3)
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Starting LSB: Start NTP daemon...
Oct 22 10:43:04 mohamed-ubuntumate ntp[6154]: * Starting NTP server ntpd
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6162]: ntpd 4.2.6p5@1.2349-o Fri Oct  2 10:30:36 UTC 2015 (1)
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: proto: precision = 0.768 usec
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Oct 22 10:43:04 mohamed-ubuntumate ntp[6154]: ...done.
Oct 22 10:43:04 mohamed-ubuntumate systemd[1]: Started LSB: Start NTP daemon.
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listen and drop on 1 v6wildcard :: UDP 123
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listen normally on 3 ppp0 197.247.23.154 UDP 123
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listen normally on 4 lo ::1 UDP 123
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: peers refreshed
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Listening on routing socket on fd #21 for interface updates
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Oct 22 10:43:04 mohamed-ubuntumate ntpd[6163]: Deferring DNS for ntp.ubuntu.com 1
Oct 22 10:43:06 mohamed-ubuntumate NetworkManager[779]: <warn>  (ppp0): arping could not be found; no ARPs will be sent
```

---

### Post by dccurtis on 2015-10-23
I seem to be getting the same thing. I'm using a Huawei E1691. Just upgraded to 15.10 yesterday, Oct 22nd.

Modem seems to connect ok, ifconfig shows ppp0 is up and has an IP address, I get the same output from the logs. But:

ping 8.8.8.8 (google's DNS)
ping: network unreachable

and

ping [www.google.com](www.google.com)
ping: unknown server

I booted into Windows to look for a work around on the internet but no luck just found this post. So the modem obviously works as does the service provider.

I'm going to start looking at route and gateways.

---

### Post by Terone on 2016-01-02
Anyone find a fix for this yet? I seem to be having the same issues with 15.10

---

### Post by dkozlows on 2016-01-25
> **Terone said:**
> Anyone find a fix for this yet? I seem to be having the same issues with 15.10

I have the same problem on 15.10.

---

### Post by Neo_Mofoka on 2016-01-31
I just experienced this issue after also upgrading from 15.04 to 15.10. At first I could connect just find but then suddenly I couldn't connect any longer. After plugging and unplugging the modem into different slots, I'm suddenly able to connect to the internet again. 

I was thinking it was a firewall issue but since I didn't do anything in that area to initiate or resolve the problem, I'm doubtful. The only thing I can thing of that I did was run:

     ```
ifup -a
```

And

    ```
nmcli c
```

But none of those should affect an existing and active connection the way it did.

---

### Post by prahladyeri on 2016-05-21
Its May already and still no fix for this yet.

---

### Post by wildmanne39 on 2016-05-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Also please use normal fonts.

---

### Post by wildmanne39 on 2016-05-21
prahladyeri if you need help please start a new thread and do not post into someone else's especially one that does not have any answers at all.  Use a descriptive title tell us what you have tried so far, and run the wireless script in my signature and post the file created in your own thread using code tags.

---

