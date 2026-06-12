---
title: "Requesting bug confirm: '/etc/dhcp/dhclient.conf' being ignored"
date: 2022-07-03
forum: Networking &amp; Wireless
---

### Post by markfilipak-linux on 2022-07-03
Kernel: 5.4.0-121-generic x86_64
bits: 64
compiler: gcc v: 9.4.0
Desktop: MATE 1.26.0 
wm: marco
dm: LightDM
Distro: Linux Mint 20.3 Una
base: Ubuntu 20.04 focal

As a test, I configured my router's IP lease duration to 4321 seconds. It previously was 7200 seconds.

Here is /etc/dhcp/dhclient.conf (with comment lines removed):
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
  domain-name, domain-name-servers, domain-search, host-name,
  dhcp6.name-servers, dhcp6.domain-search, dhcp6.fqdn, dhcp6.sntp-servers,
  netbios-name-servers, netbios-scope, interface-mtu,
  rfc3442-classless-static-routes, ntp-servers;
send dhcp-lease-time 3600;
timeout 300;
```
As you can see, I'm explicitly forcing 'dhcp-lease-time' to 3600 seconds.

Here are syslog entires, before and after setting the router:
```
Jul  2 21:31:38 mark-VirtualBox NetworkManager[552]: <info>  [1656811898.6775] dhcp4 (enp0s3): option dhcp_lease_time => '7200'
...
Jul  2 21:40:10 mark-VirtualBox NetworkManager[556]: <info>  [1656812410.8610] dhcp4 (enp0s3): option dhcp_lease_time => '4321'
```

Ubuntu is ignoring /etc/dhcp/dhclient.conf and is setting its lease request duration to 4321 seconds. The only way it can 'know' that number is if it queries the router, which is clearly what it's doing. Ubuntu is setting it's lease duration to what the router has set as the maximum lease duration. That is wrong. I am getting expiries on about 1-of-3 leases. That is trashing streaming.

Granted, IP lease renewal should check 'dhcp_lease_time' against the router's maximum lease time in order to set a value that doesn't exceed, but it should not ignore 'dhclient.conf'.

---

### Post by &amp;KyT$0P# on 2022-07-03
Are you sure NetworkManager is actually using dhclient?
How did you try to configure NetworkManager to use dhclient?

---

### Post by Doug S on 2022-07-03
I think you want to use the "surpersede" option modifier for your use case.
Myself, and based on the man page for "dhclient.conf", I would not have expected "send dhcp-lease-time 3600" to do what you wanted.

---

### Post by markfilipak-linux on 2022-07-03
> **halogen2 said:**
> Are you sure NetworkManager is actually using dhclient?
Of course not. I'm not sure of anything. I'm not a developer.
>  How did you try to configure NetworkManager to use dhclient?
I didn't.

There's a /etc/init.d/network-manager
There's a sleeping process named NetworkManager that has no files open.

---

### Post by markfilipak-linux on 2022-07-03
> **Doug S said:**
> I think you want to use the "surpersede" option modifier for your use case. ...
Do you mean uncomment this line:
"#supersede domain-name "fugue.com home.vix.com";"
I don't think so.

---

### Post by markfilipak-linux on 2022-07-03
```
Jul  3 19:15:59 mark-VirtualBox NetworkManager[545]: <info>  [1656890159.8403] dhcp4 (enp0s3): state changed bound -> expire
Jul  3 19:15:59 mark-VirtualBox NetworkManager[545]: <info>  [1656890159.8404] device (enp0s3): DHCPv4: trying to acquire a new lease within 90 seconds
Jul  3 19:17:01 mark-VirtualBox CRON[12830]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8101] device (enp0s3): DHCPv4: grace period expired
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8102] device (enp0s3): state change: activated -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8107] manager: NetworkManager state is now DISCONNECTED
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <warn>  [1656890249.8146] device (enp0s3): Activation: failed for connection 'Wired connection 1'
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8156] device (enp0s3): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Withdrawing address record for fe80::cf88:3bbc:8bf3:940e on enp0s3.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Leaving mDNS multicast group on interface enp0s3.IPv6 with address fe80::cf88:3bbc:8bf3:940e.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Interface enp0s3.IPv6 no longer relevant for mDNS.
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8206] dhcp4 (enp0s3): canceled DHCP transaction
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8206] dhcp4 (enp0s3): state changed expire -> done
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Withdrawing address record for 192.168.0.17 on enp0s3.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Leaving mDNS multicast group on interface enp0s3.IPv4 with address 192.168.0.17.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Interface enp0s3.IPv4 no longer relevant for mDNS.
Jul  3 19:17:29 mark-VirtualBox dbus-daemon[544]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.9' (uid=0 pid=545 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul  3 19:17:29 mark-VirtualBox systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8316] policy: auto-activating connection 'Wired connection 1' (c29f090c-e3dd-33a9-a3b5-44bb409f3e72)
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8583] device (enp0s3): Activation: starting connection 'Wired connection 1' (c29f090c-e3dd-33a9-a3b5-44bb409f3e72)
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8589] device (enp0s3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8614] manager: NetworkManager state is now CONNECTING
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8633] device (enp0s3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.8968] device (enp0s3): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.9001] dhcp4 (enp0s3): activation: beginning transaction (timeout in 45 seconds)
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Joining mDNS multicast group on interface enp0s3.IPv6 with address fe80::cf88:3bbc:8bf3:940e.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: New relevant interface enp0s3.IPv6 for mDNS.
Jul  3 19:17:29 mark-VirtualBox avahi-daemon[541]: Registering new address record for fe80::cf88:3bbc:8bf3:940e on enp0s3.*.
Jul  3 19:17:29 mark-VirtualBox dbus-daemon[544]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  3 19:17:29 mark-VirtualBox systemd[1]: Started Network Manager Script Dispatcher Service.
Jul  3 19:17:29 mark-VirtualBox nm-dispatcher[12863]: run-parts: failed to stat component /etc/network/if-post-down.d/avahi-daemon: No such file or directory
Jul  3 19:17:29 mark-VirtualBox NetworkManager[545]: <info>  [1656890249.9479] dhcp4 (enp0s3): state changed unknown -> expire
Jul  3 19:17:30 mark-VirtualBox dbus-daemon[992]: [session uid=1000 pid=992] Activating service name='org.freedesktop.Notifications' requested by ':1.32' (uid=1000 pid=1243 comm="nm-applet " label="unconfined")
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option dhcp_lease_time      => '4321'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option domain_name_servers  => '209.18.47.63 209.18.47.61'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option expiry               => '1656894570'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option ip_address           => '192.168.0.18'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option next_server          => '192.168.0.1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_broadcast_address => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_domain_name => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_domain_name_servers => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_domain_search => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_host_name  => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_interface_mtu => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_ms_classless_static_routes => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_nis_domain => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9908] dhcp4 (enp0s3): option requested_nis_servers => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_ntp_servers => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_rfc3442_classless_static_routes => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_root_path  => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_routers    => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_static_routes => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_subnet_mask => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_time_offset => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9909] dhcp4 (enp0s3): option requested_wpad       => '1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9910] dhcp4 (enp0s3): option routers              => '192.168.0.1'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9910] dhcp4 (enp0s3): option subnet_mask          => '255.255.255.0'
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9910] dhcp4 (enp0s3): state changed expire -> bound
Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9928] device (enp0s3): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:30 mark-VirtualBox avahi-daemon[541]: Joining mDNS multicast group on interface enp0s3.IPv4 with address 192.168.0.18.
Jul  3 19:17:30 mark-VirtualBox avahi-daemon[541]: New relevant interface enp0s3.IPv4 for mDNS.
Jul  3 19:17:30 mark-VirtualBox avahi-daemon[541]: Registering new address record for 192.168.0.18 on enp0s3.IPv4.
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9974] device (enp0s3): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9980] device (enp0s3): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9990] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890251.0009] manager: NetworkManager state is now CONNECTED_SITE
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890251.0012] policy: set 'Wired connection 1' (enp0s3) as default for IPv4 routing and DNS
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890251.0071] device (enp0s3): Activation: successful, device activated.
Jul  3 19:17:31 mark-VirtualBox dbus-daemon[992]: [session uid=1000 pid=992] Successfully activated service 'org.freedesktop.Notifications'
Jul  3 19:17:31 mark-VirtualBox NetworkManager[545]: <info>  [1656890251.1783] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: Listen normally on 13 enp0s3 192.168.0.18:123
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: Deleting interface #12 enp0s3, 192.168.0.17#123, interface stats: received=108, sent=108, dropped=0, active_time=3870 secs
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 108.61.56.35 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 45.83.234.123 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 216.229.4.69 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 72.30.35.89 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 50.205.57.38 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 137.184.81.69 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 45.33.68.112 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 104.171.113.34 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 50.205.244.107 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: 217.180.209.214 local addr 192.168.0.17 -> <null>
Jul  3 19:17:32 mark-VirtualBox ntpd[707]: new interface(s) found: waking up resolver
Jul  3 19:17:33 mark-VirtualBox ntpd[707]: 45.83.234.123 local addr 192.168.0.18 -> <null>
Jul  3 19:17:37 mark-VirtualBox ntpd[707]: Soliciting pool server 2604:4500:a:30:bad:babe:ca11:911
Jul  3 19:17:40 mark-VirtualBox ntpd[707]: Soliciting pool server 66.70.172.17
Jul  3 19:17:41 mark-VirtualBox systemd[1]: NetworkManager-dispatcher.service: Succeeded.
```

*Note the line:*
**Jul  3 19:17:30 mark-VirtualBox NetworkManager[545]: <info>  [1656890250.9907] dhcp4 (enp0s3): option dhcp_lease_time      => '4321'**
**"dhcp_lease_time"*** exactly matches the line in* /etc/dhcp/dhclient.conf.

---

### Post by &amp;KyT$0P# on 2022-07-03
> **markfilipak-linux said:**
> I'm not sure of anything. ...

I didn't.

Ok.  If you want to configure NetworkManager to use dhclient:

edit [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] , under [FONT=Courier New][main][/FONT] section add this line -
```
dhcp=dhclient
```
Then restart NetworkManager to apply the change -
```
sudo systemctl restart NetworkManager
```

For more info on that change, refer to [FONT=Courier New]man NetworkManger.conf[/FONT]

---

### Post by markfilipak-linux on 2022-07-03
> **halogen2 said:**
> Ok.  If you want to configure NetworkManager to use dhclient:

edit [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] , under [FONT=Courier New][main][/FONT] section add this line -
```
dhcp=dhclient
```
Then restart NetworkManager to apply the change -
```
sudo systemctl restart NetworkManager
```

For more info on that change, refer to [FONT=Courier New]man NetworkManger.conf[/FONT]

```

mark@mark-VirtualBox:~$ man NetworkManger.conf
No manual entry for NetworkManger.conf
mark@mark-VirtualBox:~$ info NetworkManger.conf
info: No menu item 'NetworkManger.conf' in node '(dir)Top'
mark@mark-VirtualBox:~$ cd /etc
mark@mark-VirtualBox:/etc$ cd NetworkManager
mark@mark-VirtualBox:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no


```
So, what is doing DHCP at the moment?

 I don't need to love dhclient. dhclient is a stranger. I just want to love no more disconnects.

Is there a GUI and some help?

---

### Post by markfilipak-linux on 2022-07-03
[https://linux.die.net/man/5/networkmanager.conf](https://linux.die.net/man/5/networkmanager.conf)

"**dhcp=*dhclient* | *dhcpcd***
This key sets up what DHCP client NetworkManager will use. Presently *dhclient* and *dhcpcd* are supported. The client configured here should be available on your system too. If this key is missing, available DHCP clients are looked for in this order: dhclient, dhcpcd."

Neither dhclient nor dhcpcd are currently running. So what is handling DHCP?

PS: Neither dhclient nor dhcpcd are currently installed. It appears they don't exist. At least, they don't exist as programs.

---

### Post by markfilipak-linux on 2022-07-03
> **halogen2 said:**
> ... edit [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] , under [FONT=Courier New][main][/FONT] section add this line -
```
dhcp=dhclient
```

  Done -- rebooted -- look at 'syslog'.

Lines of concern:
Jul  3 23:00:37 mark-VirtualBox dhclient[748]: Can't create /run/NetworkManager/dhclient-enp0s3.pid: Permission denied
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9767] dhcp4 (enp0s3):   lease time 4321
Jul  3 23:00:39 mark-VirtualBox dhclient[748]: Can't create /run/NetworkManager/dhclient-enp0s3.pid: Permission denied

As is plainly seen, the 'lease time' is incorrect. The only explanation I can think of is that Ubuntu is ignoring '/etc/dhcp/dhclient.conf'.
Or the permissions denied are real.
```

mark@mark-VirtualBox:/etc/dhcp$ ls -l
total 16
-rw-r--r-- 1 root root 1426 Feb 25  2020 debug
-rw-r--r-- 1 root root 1734 Jul  2 21:17 dhclient.conf
drwxr-xr-x 2 root root 4096 Jul  1 23:29 dhclient-enter-hooks.d
drwxr-xr-x 2 root root 4096 Jan  4 13:16 dhclient-exit-hooks.d

```

'syslog', pruned of non-networking lines:
```

Jul  3 23:00:36 mark-VirtualBox systemd[1]: Starting Network Manager...
Jul  3 23:00:36 mark-VirtualBox kernel: [    1.891751] e1000 0000:00:03.0 eth0: (PCI:33MHz:32-bit) 08:00:27:7e:bc:29
Jul  3 23:00:36 mark-VirtualBox kernel: [    1.891756] e1000 0000:00:03.0 eth0: Intel(R) PRO/1000 Network Connection
Jul  3 23:00:36 mark-VirtualBox kernel: [    1.904856] e1000 0000:00:03.0 enp0s3: renamed from eth0
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.1761] NetworkManager (version 1.22.10) is starting... (for the first time)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.1771] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Jul  3 23:00:37 mark-VirtualBox systemd[1]: Started Network Manager.
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.1919] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.2339] manager[0x5599ead00030]: monitoring kernel firmware directory '/lib/firmware'.
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.2351] monitoring ifupdown state file '/run/network/ifstate'.
Jul  3 23:00:37 mark-VirtualBox dbus-daemon[552]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.9' (uid=0 pid=555 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6456] hostname: hostname: using hostnamed
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6456] hostname: hostname changed from (none) to "mark-VirtualBox"
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6460] dns-mgr[0x5599eace9290]: init: dns=systemd-resolved rc-manager=symlink, plugin=systemd-resolved
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6686] manager[0x5599ead00030]: rfkill: Wi-Fi hardware radio set enabled
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6686] manager[0x5599ead00030]: rfkill: WWAN hardware radio set enabled
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6895] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wifi.so)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.6922] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-adsl.so)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7012] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-team.so)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7187] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-bluetooth.so)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7211] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wwan.so)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7216] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7218] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7220] manager: Networking is enabled by state file
Jul  3 23:00:37 mark-VirtualBox dbus-daemon[552]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.9' (uid=0 pid=555 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7244] dhcp-init: Using DHCP client 'dhclient'
Jul  3 23:00:37 mark-VirtualBox systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7282] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-settings-plugin-ifupdown.so")
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7283] settings: Loaded settings plugin: keyfile (internal)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7283] ifupdown: management mode: unmanaged
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7284] ifupdown:       interface-parser: parsing file /etc/network/interfaces
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7284] ifupdown:       interface-parser: source line includes interfaces file(s) /etc/network/interfaces.d
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7284] ifupdown:       interface-parser: finished parsing file /etc/network/interfaces
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7347] device (lo): carrier: link connected
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7356] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7402] manager: (enp0s3): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Jul  3 23:00:37 mark-VirtualBox systemd[1]: Started Network Manager Script Dispatcher Service.
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7615] settings: (enp0s3): created default wired connection 'Wired connection 1'
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7652] device (enp0s3): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jul  3 23:00:37 mark-VirtualBox networkd-dispatcher[566]: ERROR:Unknown state for interface NetworkctlListState(idx=2, name='enp0s3', type='ether', operational='n/a', administrative='unmanaged'): n/a
Jul  3 23:00:37 mark-VirtualBox kernel: [    6.410901] e1000: enp0s3 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
Jul  3 23:00:37 mark-VirtualBox kernel: [    6.411282] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s3: link becomes ready
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.7900] device (enp0s3): carrier: link connected
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8027] modem-manager: ModemManager available
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8027] device (enp0s3): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8104] policy: auto-activating connection 'Wired connection 1' (c29f090c-e3dd-33a9-a3b5-44bb409f3e72)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8130] device (enp0s3): Activation: starting connection 'Wired connection 1' (c29f090c-e3dd-33a9-a3b5-44bb409f3e72)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8133] device (enp0s3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8149] manager: NetworkManager state is now CONNECTING
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8166] device (enp0s3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8259] device (enp0s3): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8298] dhcp4 (enp0s3): activation: beginning transaction (timeout in 45 seconds)
Jul  3 23:00:37 mark-VirtualBox NetworkManager[555]: <info>  [1656903637.8374] dhcp4 (enp0s3): dhclient started with pid 748
Jul  3 23:00:37 mark-VirtualBox avahi-daemon[549]: Joining mDNS multicast group on interface enp0s3.IPv6 with address fe80::cf88:3bbc:8bf3:940e.
Jul  3 23:00:37 mark-VirtualBox avahi-daemon[549]: New relevant interface enp0s3.IPv6 for mDNS.
Jul  3 23:00:37 mark-VirtualBox avahi-daemon[549]: Registering new address record for fe80::cf88:3bbc:8bf3:940e on enp0s3.*.
Jul  3 23:00:37 mark-VirtualBox dhclient[748]: DHCPDISCOVER on enp0s3 to 255.255.255.255 port 67 interval 3 (xid=0x524af009)
Jul  3 23:00:37 mark-VirtualBox dhclient[748]: Can't create /run/NetworkManager/dhclient-enp0s3.pid: Permission denied
Jul  3 23:00:37 mark-VirtualBox dhclient[748]: DHCPREQUEST for 192.168.0.21 on enp0s3 to 255.255.255.255 port 67 (xid=0x9f04a52)
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9759] dhcp4 (enp0s3):   address 192.168.0.21
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9759] dhcp4 (enp0s3):   plen 24 (255.255.255.0)
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9767] dhcp4 (enp0s3):   gateway 192.168.0.1
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9767] dhcp4 (enp0s3):   lease time 4321
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9767] dhcp4 (enp0s3):   nameserver '209.18.47.63'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9767] dhcp4 (enp0s3):   nameserver '209.18.47.61'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option broadcast_address    => '192.168.0.255'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option dad_wait_time        => '0'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option default_ip_ttl       => '64'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option dhcp_lease_time      => '4321'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option dhcp_message_type    => '5'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option dhcp_server_identifier => '192.168.0.1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option domain_name_servers  => '209.18.47.63 209.18.47.61'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9768] dhcp4 (enp0s3): option expiry               => '1656907959'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9769] dhcp4 (enp0s3): option ip_address           => '192.168.0.21'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option network_number       => '192.168.0.0'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option next_server          => '192.168.0.1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option requested_broadcast_address => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option requested_domain_name => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option requested_domain_name_servers => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option requested_domain_search => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9785] dhcp4 (enp0s3): option requested_host_name  => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_interface_mtu => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_ms_classless_static_routes => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_netbios_name_servers => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_netbios_scope => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_ntp_servers => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_rfc3442_classless_static_routes => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9786] dhcp4 (enp0s3): option requested_root_path  => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9787] dhcp4 (enp0s3): option requested_routers    => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9787] dhcp4 (enp0s3): option requested_static_routes => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9787] dhcp4 (enp0s3): option requested_subnet_mask => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9787] dhcp4 (enp0s3): option requested_time_offset => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9795] dhcp4 (enp0s3): option requested_wpad       => '1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9796] dhcp4 (enp0s3): option routers              => '192.168.0.1'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9796] dhcp4 (enp0s3): option subnet_mask          => '255.255.255.0'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9796] dhcp4 (enp0s3): option time_offset          => '0'
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9796] dhcp4 (enp0s3): state changed unknown -> bound
Jul  3 23:00:38 mark-VirtualBox avahi-daemon[549]: Joining mDNS multicast group on interface enp0s3.IPv4 with address 192.168.0.21.
Jul  3 23:00:38 mark-VirtualBox avahi-daemon[549]: New relevant interface enp0s3.IPv4 for mDNS.
Jul  3 23:00:38 mark-VirtualBox avahi-daemon[549]: Registering new address record for 192.168.0.21 on enp0s3.IPv4.
Jul  3 23:00:38 mark-VirtualBox NetworkManager[555]: <info>  [1656903638.9898] device (enp0s3): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0021] device (enp0s3): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0045] device (enp0s3): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0081] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0152] manager: NetworkManager state is now CONNECTED_SITE
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0167] policy: set 'Wired connection 1' (enp0s3) as default for IPv4 routing and DNS
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0194] device (enp0s3): Activation: successful, device activated.
Jul  3 23:00:39 mark-VirtualBox dhclient[748]: Can't create /run/NetworkManager/dhclient-enp0s3.pid: Permission denied
Jul  3 23:00:39 mark-VirtualBox NetworkManager[555]: <info>  [1656903639.0263] manager: startup complete
Jul  3 23:00:40 mark-VirtualBox NetworkManager[555]: <info>  [1656903640.1200] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul  3 23:00:41 mark-VirtualBox ntpd[713]: Listen normally on 4 enp0s3 192.168.0.21:123
Jul  3 23:00:41 mark-VirtualBox ntpd[713]: Listen normally on 5 enp0s3 [fe80::cf88:3bbc:8bf3:940e%2]:123
Jul  3 23:00:51 mark-VirtualBox systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Jul  3 23:00:55 mark-VirtualBox NetworkManager[555]: <info>  [1656903655.3250] agent-manager: agent[90b03af42fc599d4,:1.42/org.freedesktop.nm-applet/1000]: agent registered

```

---

### Post by &amp;KyT$0P# on 2022-07-03
> **markfilipak-linux said:**
> ```

mark@mark-VirtualBox:~$ man NetworkManger.conf
No manual entry for NetworkManger.conf

```

:confused:
No idea how this could happen?

I think the online manpage you found is for an older version of NetworkManager.  You can view the Ubuntu 20.04 version online [here]("https://manpages.ubuntu.com/manpages/focal/en/man5/NetworkManager.conf.5.html").

I don't see any problem with the syslog lines you posted, in testing I saw similar, including those permission denied errors.  Since DHCP with dhclient was working anyway I ignored those.

So I tried editing my dhclient.conf (which was otherwise default) and adding this line -
```
supersede dhcp-lease-time 3600;
```
Did [FONT=Courier New]sudo systemctl restart NetworkManager[/FONT] to apply this change, and then my syslog showed
```
dhcp4 (enp0s3):   lease time 3600
```
instead of the default lease time.

Does this help?

---

### Post by Doug S on 2022-07-04
> **halogen2 said:**
> So I tried editing my dhclient.conf (which was otherwise default) and adding this line -
```
supersede dhcp-lease-time 3600;
```That is what I meant with my earlier post.

---

### Post by markfilipak-linux on 2022-07-04
What am I to make of this?
```

mark@mark-VirtualBox:~$ dhclient
RTNETLINK answers: Operation not permitted
mark@mark-VirtualBox:~$ which dhclient
/usr/sbin/dhclient
mark@mark-VirtualBox:~$ apt install dhclient
[sudo] password for mark:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dhclient

```

<bitch>
"E:"? What? Are programmers getting too lazy to print the word "error"? That's really going to make it easy for users to find error statements, eh?
</bitch>

---

### Post by markfilipak-linux on 2022-07-04
> **Doug S said:**
> That is what I meant with my earlier post.

Ah! Thank you, Doug. I'll give it a try right now. I'll need to reboot afterwards, so I'll be right back. Stay tuned to this program...

...Wait a minute! I just made the change to '/etc/dhcp/dhclient.conf' and I noticed there was a notification waiting:
```
[X] Upgrade: "isc-dhcp 4.4.1-2.1ubuntu5.20.04.3", packages: 'isc-dhcp-client' 'isc-dhcp-common'
```
Is that a coincidence? Got to be! But that brings up a question: Should I doing something with 'isc-dhcp' instead of 'dhclient'?

...Following reboot, from syslog:
```
Jul  4 12:49:49 mark-VirtualBox NetworkManager[541]: <info>  [1656953389.9920] dhcp4 (enp0s3):   lease time 3600
```
So, it worked! Thank you, Doug.

...Now, to be complete, I'm going to remove the "dhcp=dhclient" forcing from '[FONT=Courier New]/etc/NetworkManager/NetworkManager.conf' [/FONT](added earlier) in order to see whether NetworkManager is taking the correct default (i.e. is actually reading '/etc/dhcp/dhclient.conf'). I'll be back following the change and reboot.

...And here is the result:
```
Jul  4 13:38:59 mark-VirtualBox NetworkManager[549]: <info>  [1656956339.7494] dhcp4 (enp0s3): option dhcp_lease_time      => '4321'
```
So, by default, Network Manager is ignoring '/etc/dhcp/dhclient.conf[FONT=Courier New]'[/FONT].

...And, thank you, halogen2.

---

### Post by Doug S on 2022-07-04
> **markfilipak-linux said:**
> ...Wait a minute! I just made the change to '/etc/dhcp/dhclient.conf' and I noticed there was a notification waiting:
```
[X] Upgrade: "isc-dhcp 4.4.1-2.1ubuntu5.20.04.3", packages: 'isc-dhcp-client' 'isc-dhcp-common'
```
Is that a coincidence? Got to be! But that brings up a question: Should I doing something with 'isc-dhcp' instead of 'dhclient'?
Yes, coincidence:

```

doug@s19:~/kernel/linux$ dpkg -l | grep dhcp
ii  [COLOR="#FF0000"]isc-dhcp-client[/COLOR]                               4.4.1-2.1ubuntu5.20.04.2              amd64        DHCP client for automatically obtaining an IP address
ii  [COLOR="#FF0000"]isc-dhcp-common[/COLOR]                               4.4.1-2.1ubuntu5.20.04.2              amd64        common manpages relevant to all of the isc-dhcp packages
doug@s19:~/kernel/linux$ sudo apt update
...
doug@s19:~/kernel/linux$ sudo apt upgrade
...
The following packages will be upgraded:
  [COLOR="#FF0000"]isc-dhcp-client isc-dhcp-common[/COLOR] linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04 snapd unattended-upgrades update-notifier-common
...
doug@s19:~/kernel/linux$ dpkg -l | grep dhcp
ii  [COLOR="#FF0000"]isc-dhcp-client                               4.4.1-2.1ubuntu5.20.04.3[/COLOR]              amd64        DHCP client for automatically obtaining an IP address
ii  [COLOR="#FF0000"]isc-dhcp-common                               4.4.1-2.1ubuntu5.20.04.3[/COLOR]              amd64        common manpages relevant to all of the isc-dhcp packages

```
And yes, the package is "isc-dhcp-client" which includes the "dhclient" command:

```
doug@s19:~/kernel/linux$ ls -l /sbin
lrwxrwxrwx 1 root root 8 Jan 23  2020 /sbin -> usr/sbin
doug@s19:~/kernel/linux$ dpkg -S /sbin/dhclient
isc-dhcp-client: /sbin/dhclient
```

---

### Post by markfilipak-linux on 2022-07-04
I uncommented "dhcp=dhclient" in '[FONT=Courier New]/etc/NetworkManager/NetworkManager.conf', rebooted, and confirmed via syslog:
```
Jul  4 13:56:59 mark-VirtualBox NetworkManager[534]: <info>  [1656957419.7148] dhcp4 (enp0s3): option dhcp_lease_time      => '3600'
```
[/FONT]So, I should be 'good to go'.

Do you folks confirm this as a bug or do you have other thoughts?

---

### Post by Doug S on 2022-07-04
> **markfilipak-linux said:**
> Do you folks confirm this as a bug or do you have other thoughts?No bug. The config file is only for dhclient as supplied by the isc-dhcp-client package, which you have confirmed does what is expected when used.

```
doug@s19:~/kernel/linux$ dpkg -S /etc/dhcp/dhclient.conf
isc-dhcp-client: /etc/dhcp/dhclient.conf
```

I think the issue here, is how to override default dhcp server stuff when dhclient is not being used, which typically it isn't with systemd/networkd (which I forgot earlier). When not using netplan, it is done in a file in "/etc/systemd/networkd", but I do not know about when using netplan. Here is an example from my debian server (no netplan) where I override the default name server:

```
doug@s15:~/config/etc/systemd/network$ cat 10-wan.network
  [Match]
  Name=enp1s0

  [Network]
  DHCP=ipv4

  [DHCPv4]
  UseDNS=127.0.0.1
```

EDIT: For netplan perhaps "dhcp4-overrides:", see [here]("https://netplan.io/examples#connecting-multiple-interfaces-with-dhcp")

---

### Post by markfilipak-linux on 2022-07-04
> **Doug S said:**
> No bug.
Let's see, eh?

'networkmanager.conf' documented -- redacted to key point:
```

mark@mark-VirtualBox:~$ man networkmanager.conf
dhcp
If this key is missing, it defaults to internal. It the chosen plugin is not available, clients are looked for in this order: dhclient, dhcpcd, internal.

```

I see that "internal" was recently added to the man page. What does it mean? And why would a new install screw up?

If "internal" means it queries the gateway-router and uses it's max lease, that's still a bug in my opinion as NetworkManager should not set lease time to the router's maximum.

---

### Post by markfilipak-linux on 2022-07-04
Assuming that "internal" means get the router's max lease, do you read that the way I read that?

var myDhcpClent
if (NetworkManager.conf, "dhcp" entry not found) set dhcp_lease_time to the router's max lease and exit
assume myDhcpClent='dhclient'   // what happened to the 3600 default?
 if (myDhcpClent not found) assume myDhcpClent='dhcpcd'
if (myDhcpClent not found) set dhcp_lease_time to the router's max lease
else set dhcp_lease_time via myDhcpClent

---

### Post by markfilipak-linux on 2022-07-04
Hahahahaha.....

I set my gateway-router to dhcp_lease_time = 4294967295 seconds (i.e., 136 years).

Now NetworkManager is setting dhcp_lease_time => '429496729' (i.e., 13.6 years)

There's a bug there somewhere, but I'm getting tired of NetworkManager triage. I'm not a developer.

---

### Post by Doug S on 2022-07-04
I am a server person and don't normally use NetworkManager. I started a 20.04 desktop VM, which uses network manager. From "man NetworkManager" I do not see a way to override the default-lease-time as supplied by the DHCP server when NetworkManager is using the default internal dhcp client. I thought this might do it:

```
doug@desk-ff:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

[COLOR="#FF0000"][connection]
ipv4.dhcp-timeout=3600[/COLOR]
```but it merely changes the allowed time as per:

```

Jul  4 15:31:04 desk-ff NetworkManager[518]: <info>  [1656973864.3427] dhcp4 (enp1s0): activation: beginning transaction (timeout in 45 seconds)
...
Jul  4 15:44:47 desk-ff NetworkManager[516]: <info>  [1656974687.2382] dhcp-init: Using DHCP client 'internal'
Jul  4 15:44:47 desk-ff NetworkManager[516]: <info>  [1656974687.2682] dhcp4 (enp1s0): activation: beginning transaction (timeout in 3600 seconds)

```
The actual default lease time is as per my dhcpd.conf file in my dhcp server:

```
# option definitions common to all supported networks...

default-lease-time 86400;
max-lease-time 93000;
```
.
```
Jul  4 15:31:04 desk-ff NetworkManager[518]: <info>  [1656973864.3602] dhcp4 (enp1s0): [COLOR="#FF0000"]option dhcp_lease_time      => '86400'[/COLOR]
```

---

