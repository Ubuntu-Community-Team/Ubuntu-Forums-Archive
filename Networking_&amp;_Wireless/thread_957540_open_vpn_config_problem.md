---
title: "open vpn config problem"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Sico2 on 2008-10-24
Hi,
I am trying set up open vpn on my acer laptop for an encrypted connection but I get some error stage during the setup and am really stuck on it with no idea why it doesn't work. Apparently there are plenty of nm bugs that cause it, but my whole net connection depends on nm.

```
root@****:~# tail /var/log/daemon.log
Oct 12 19:28:12 *** NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 6 -> 3.
Oct 12 19:28:12 *** NetworkManager: <info>  VPN Activation (xerobank) Stage 3 of 4 (Connect) reply received.
Oct 12 19:28:12 *** NetworkManager: <info>  VPN Activation (xerobank) Stage 4 of 4 (IP Config Get) timeout scheduled...
Oct 12 19:28:12 *** NetworkManager: <info>  VPN Activation (xerobank) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
Oct 12 19:28:12 *** nm-openvpn[8569]: Options error: local and remote/netmask --ifconfig addresses must be different
Oct 12 19:28:12 *** nm-openvpn[8569]: Use --help for more information.
Oct 12 19:28:12 *** NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.openvpn', signal 'ConnectFailed', with message 
'The VPN login failed because the VPN program could not connect to the VPN server.
Oct 12 19:28:12 *** NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 3 -> 6.
Oct 12 19:28:12 *** NetworkManager: <WARN>  nm_vpn_service_stop_connection():(VPN Service org.freedesktop.NetworkManager.openvpn): 
could not stop connection 'xerobank' because service was 6.
Oct 12 19:28:13 *** NetworkManager: <debug> [1223836093.007386] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of VPN connection 'xerobank'

```

And if I continue further to actually launch the service I get log like this:
```

root@***:~# /etc/init.d/openvpn restart

 * Stopping virtual private network daemon. [ OK ]
 * Starting virtual private network daemon. [ OK ]

root@***:~# tail -f /var/log/daemon.log

Oct 12 18:43:53 *** avahi-daemon[5215]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.65.
Oct 12 18:43:53 *** avahi-daemon[5215]: New relevant interface eth0.IPv4 for mDNS.
Oct 12 18:43:53 *** avahi-daemon[5215]: Registering new address record for ***.***.*.** on eth0.IPv4.
Oct 12 18:43:54 *** NetworkManager: <info>  Clearing nscd hosts cache.
Oct 12 18:43:54 *** NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): 
could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Oct 12 18:43:54 *** NetworkManager: <info>  Activation (eth0) successful, device activated.
Oct 12 18:43:54 *** NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Oct 12 18:43:54 *** NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 12 18:43:52 *** ntpdate[9546]: step time server 91.189.94.4 offset -2.126402 sec
Oct 12 18:43:53 *** avahi-daemon[5215]: Registering new address record for fe80::21b:24ff:fec5:d933 on eth0.*.

```

help...!

---

### Post by Sico2 on 2008-11-06
Anyone with a big better knowledge of Network manager than me...?
[I]
"[8569]: Options error: local and remote/netmask --ifconfig addresses must be different"[/I]

---

### Post by superprash2003 on 2008-11-06
post ifconfig output.. maybe two interfaces have same ips.. resuling in ip conflict..

---

### Post by Sico2 on 2009-01-31
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c5:d9:33  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fec5:d933/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38147342 (38.1 MB)  TX bytes:5960162 (5.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3000 (3.0 KB)  TX bytes:3000 (3.0 KB)

---

