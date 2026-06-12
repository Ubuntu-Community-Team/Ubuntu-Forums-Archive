---
title: "Acer Aspire-5710G Network issue"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by deepaknr on 2008-02-13
Hi,

I am getting a strange error during boot-up, it does not happen every time though. When it happens I have to restart the system there is no other go.

I am copying the system log when this happens. Any one kindly help me out

```
Feb 13 18:57:54 avahi-autoipd(eth0)[5494]: Successfully called chroot().
Feb 13 18:57:54  avahi-autoipd(eth0)[5494]: Successfully dropped root privileges.
Feb 13 18:57:54  avahi-autoipd(eth0)[5494]: Starting with address 169.254.7.168
Feb 13 18:57:59 anacron[5538]: Anacron 2.3 started on 2008-02-13
Feb 13 18:57:59 anacron[5538]: Normal exit (0 jobs run)
Feb 13 18:57:59  /usr/sbin/cron[5565]: (CRON) INFO (pidfile fd = 3)
Feb 13 18:57:59  /usr/sbin/cron[5566]: (CRON) STARTUP (fork ok)
Feb 13 18:57:59  /usr/sbin/cron[5566]: (CRON) INFO (Running @reboot jobs)
Feb 13 18:58:00 avahi-autoipd(eth0)[5494]: Callout BIND, address 169.254.7.168 on interface eth0
Feb 13 18:58:00 avahi-daemon[5365]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.168.
Feb 13 18:58:00 avahi-daemon[5365]: New relevant interface eth0.IPv4 for mDNS.
Feb 13 18:58:00 avahi-daemon[5365]: Registering new address record for 169.254.7.168 on eth0.IPv4.
Feb 13 18:58:04 avahi-autoipd(eth0)[5494]: Successfully claimed IP address 169.254.7.168
Feb 13 18:58:04 NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface eth0 
Feb 13 18:58:04 avahi-autoipd(eth0)[5494]: Got SIGTERM, quitting.
Feb 13 18:58:04 avahi-autoipd(eth0)[5494]: Callout STOP, address 169.254.7.168 on interface eth0
Feb 13 18:58:04 avahi-daemon[5365]: Withdrawing address record for 169.254.7.168 on eth0.
Feb 13 18:58:04 avahi-daemon[5365]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.7.168.
Feb 13 18:58:04 avahi-daemon[5365]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 13 18:58:04 avahi-autoipd(eth0)[5495]: client: RTNETLINK answers: No such process
Feb 13 18:58:05 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Feb 13 18:58:05 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb 13 18:58:06 dhclient: DHCPOFFER from 192.168.0.1
Feb 13 18:58:06 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 13 18:58:07 dhclient: DHCPACK from 192.168.0.1
Feb 13 18:58:07 avahi-daemon[5365]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.47.
Feb 13 18:58:07 avahi-daemon[5365]: New relevant interface eth0.IPv4 for mDNS.
Feb 13 18:58:07 avahi-daemon[5365]: Registering new address record for 192.168.0.47 on eth0.IPv4.
Feb 13 18:58:08 NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Feb 13 18:58:08 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 13 18:58:08 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Feb 13 18:58:08 dhclient: bound to 192.168.0.47 -- renewal in 271 seconds.
Feb 13 18:58:08 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 13 18:58:08 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 13 18:58:08 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 13 18:58:08 NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 13 18:58:08 NetworkManager: <info>    address 192.168.0.47 
Feb 13 18:58:08 NetworkManager: <info>    netmask 255.255.255.0 
Feb 13 18:58:08 NetworkManager: <info>    broadcast 192.168.0.255 
Feb 13 18:58:08 NetworkManager: <info>    gateway 192.168.0.1 
Feb 13 18:58:08 NetworkManager: <info>    nameserver 192.168.0.1 
Feb 13 18:58:08 NetworkManager: <info>    domain name 'mshome.net' 
Feb 13 18:58:08 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 13 18:58:08 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Feb 13 18:58:08 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Feb 13 18:58:08 avahi-daemon[5365]: Withdrawing address record for 192.168.0.47 on eth0.
Feb 13 18:58:08 avahi-daemon[5365]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.47.
Feb 13 18:58:08 avahi-daemon[5365]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 13 18:58:08 avahi-daemon[5365]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.47.
Feb 13 18:58:08 avahi-daemon[5365]: New relevant interface eth0.IPv4 for mDNS.
Feb 13 18:58:08 avahi-daemon[5365]: Registering new address record for 192.168.0.47 on eth0.IPv4.
Feb 13 18:58:09 NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 13 18:58:09 NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 13 18:58:09 NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Feb 13 18:58:09 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 13 18:58:09 NetworkManager: <info>  Activation (eth0) successful, device activated. 
Feb 13 18:58:09 kernel: [   45.184000] NET: Registered protocol family 10
Feb 13 18:58:09 kernel: [   45.184000] lo: Disabled Privacy Extensions
Feb 13 18:58:09 kernel: [   45.184000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 13 18:58:12 ntpdate[5716]: step time server 91.189.94.4 offset 1.565342 sec
Feb 13 18:58:12 avahi-daemon[5365]: Registering new address record for fe80::216:d4ff:fede:7b47 on eth0.*.
Feb 13 18:58:21 kernel: [   55.872000] eth0: no IPv6 routers present
Feb 13 18:58:29 kernel: [   64.240000] tg3: eth0: Link is down.
Feb 13 18:58:29 NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Feb 13 18:58:29 NetworkManager: <info>  Deactivating device eth0. 
Feb 13 18:58:29 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5460
Feb 13 18:58:29 dhclient: killed old client process, removed PID file
Feb 13 18:58:30 dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Feb 13 18:58:30 avahi-daemon[5365]: Withdrawing address record for 192.168.0.47 on eth0.
Feb 13 18:58:30 avahi-daemon[5365]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.47.
Feb 13 18:58:30 avahi-daemon[5365]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 13 18:58:30 avahi-daemon[5365]: Withdrawing address record for fe80::216:d4ff:fede:7b47 on eth0.
Feb 13 18:58:30 NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Feb 13 18:58:30 NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Feb 13 18:58:44 init: tty4 main process (4616) killed by TERM signal
Feb 13 18:58:44 init: tty5 main process (4617) killed by TERM signal
Feb 13 18:58:44 init: tty2 main process (4621) killed by TERM signal
Feb 13 18:58:44 init: tty3 main process (4622) killed by TERM signal
Feb 13 18:58:44 init: tty1 main process (4623) killed by TERM signal
Feb 13 18:58:44 init: tty6 main process (4624) killed by TERM signal
Feb 13 18:59:36 syslogd 1.4.1#21ubuntu3: restart.
```

---

### Post by dca on 2008-02-13
Are you using ndiswrapper for your wireless card and what kind of wireless card is it?  Also, when you don't get the errors on start-up, networking (ethernet & wireless) work okay?

---

### Post by deepaknr on 2008-02-16
Hi,

I think I solved the problem. Basically the network manager was not configured properly and wireless used to be under roaming mode by default and it used to actively look for network and used to try connecting the one which is some where around here. this used to jam the network or some thing of that sort.

thanks for your reply.

---

