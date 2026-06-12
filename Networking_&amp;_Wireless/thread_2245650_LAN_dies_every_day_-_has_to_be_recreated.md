---
title: "LAN dies every day - has to be recreated"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by maxinstuff2 on 2014-09-25
As the title suggests, my LAN connection completely dies at regular intervals - pretty much every day like clockwork. Fixing it each day has become a ritual now :|

Basically each day or so, on boot my LAN will try to connect about 3 times and fail. No amount of disconnecting and reconnecting fixes it.

The only procedure that seems to get it back up is:
delete the connection in network settings
unplug and replug ethernet cable
recreate the connection

THis procedure does NOT work without the second step.

It then works again for 24-48 hours before relapsing..... I can shutdown/reboot without loosing the connection in between, it seems to take a full day to lose it's marbles. 


From "lspci -v" :
```
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
        Subsystem: Gigabyte Technology Co., Ltd Device e000
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at f7f00000 (32-bit, non-prefetchable) [size=128K]
        Memory at f7f39000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f040 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: e1000e
```

My motherboard is a Gigabyte Z87-D3HP and the ethernet port is referred to in the manual just as an RJ-45 LAN port. The rest of my hardware is in my sig.

---

### Post by fidelis2 on 2014-09-25
My Ethernet connection also dies, not every day, but every few days. It then just doesn't route anything anymore. It's still there (i.e. in the task-bar on the right), but it can't even ping the router or any other machine.

So maybe you and I got a similar problem? For sure I got a similar main-board just with another network chip:
- Gigabyte GA-Z77X-UD3H
- Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
 Subsystem: Gigabyte Technology Co., Ltd Device e000

Maybe it's a Linux driver problem with our main-boards?
Could you test if the following works for you? Because with these two commands I can wake-up my died network again:
> sudo ifdown lo
> sudo ifup lo


Have you used your hardware with another OS (like Windows) before? If so, did the problem already exist back then?
Because for me, when I used to use Windows-7 on my machine, the network worked fine with a ~2012 network driver, until I installed a newer ~2013 driver for it. Then the network started to die every few days. So I rolled back the Windows7's network-driver to the old version, and the network worked again.
I'm wondering if something similar could be the problem here with our (X-/K-) Ubuntu OS and the used main-board and network chip combination.

---

### Post by maxinstuff2 on 2014-09-25
I built my machine and don't own a copy of Windows :|

It has done this since day 1 so I can't compare to anything. I'll try those commands next time it dies.

---

### Post by fidelis2 on 2014-09-25
> **maxinstuff2 said:**
> It has done this since day 1 so I can't compare to anything.
Same here; as soon as I installed (X-) Ubuntu 14 on my machine, the ethernet "dying" problem started to show. (And as said: in contrast to your situation not every day, but say every 2nd day or so.)
However, since when I used Windows7 before and noticed the same problem with Windows and a new Ethernet driver (whereas an older driver worked), I suppose it's a driver problem and hopefully can be solved by a newer or another Linux driver, too.

By the way, did you see any improvement concerning your problem with the most recent Linux firmware and kernel updates? In my case it looks like since these updates -- maybe one or two weeks ago -- the dying ethernet problem doesn't happen as often as it used to.

---

### Post by maxinstuff2 on 2014-09-29
Bump.

---

### Post by maxinstuff2 on 2014-10-07
So this situation has improved a little after setting the wired connection with a static ip - that is, manually specifying the gateway, DNS servers and IP address to request from the router.

it still fails every day or so, but only the internet access, I still maintain connection to the lan.
i think this means whatever it is happening is breaking the auto-negotiation (because before it would completely lose it's marbles and disconnect completely), but it still seems to require unplugging and replugging the Ethernet cable at the very least to fix.

Im not really sure where to start with troubleshooting this further so any assistance is appreciated.

---

### Post by tgalati4 on 2014-10-07
Sometimes hardware errors will get captured in /var/log/syslog, but often the errors are misleading.  So look through your logs and post anything network-related.

I do know that home routers sometimes need to be rebooted from time to time--their limited RAM and crappy firmware cause lock-ups.  It's possible that your router is having an issue.  Try changing it.  Try changing your cables.

File a bug in Launchpad and see if others are having similar problems with your motherboard and the current kernel that you are using.  If you get a handful of responses, then it could be a module problem.

I have seen Southbridge chips fail.  Does yours get hot?  Put your finger on it.  If you can't keep your finger on it for 30 seconds, then that could be the source of the problem.  Some motherboards use the Southbridge to handle network and sound.  So trying to stream audio becomes a problem.

---

### Post by maxinstuff2 on 2014-10-07
> **tgalati4 said:**
> Sometimes hardware errors will get captured in /var/log/syslog, but often the errors are misleading.  So look through your logs and post anything network-related.

I do know that home routers sometimes need to be rebooted from time to time--their limited RAM and crappy firmware cause lock-ups.  It's possible that your router is having an issue.  Try changing it.  Try changing your cables.

File a bug in Launchpad and see if others are having similar problems with your motherboard and the current kernel that you are using.  If you get a handful of responses, then it could be a module problem.

I have seen Southbridge chips fail.  Does yours get hot?  Put your finger on it.  If you can't keep your finger on it for 30 seconds, then that could be the source of the problem.  Some motherboards use the Southbridge to handle network and sound.  So trying to stream audio becomes a problem.

Thankyou very much for your reply :)

I don't THINK it is a heat issue. My sound also works without issue (analog out).
This is generally happening right after startup, and sensors reports things are nice and frosty:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +105.0°C)
temp2:        +29.8°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +27.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +31.0°C  (high = +80.0°C, crit = +100.0°C) 
```

I also do not think it is a cabling problem - the same issue occurs on wifi (I took the wifi card out after switching to ethernet though. The same issue occurred on the wifi).
I don't think it is the router either as none of my other connected devices have problems (tablet and phone - tablet was used to come to this thread as soon as the issue happened this morning).
Given it also happened on wifi, I think my wifi connected tablet and phone would have issues as well if it was the router?

syslog does report a bunch of network stuff right after login, here it all is from the point where it starts trying to connect - it looks like the same loop repeats a bunch of times before giving up. It gets connected at the end after I unplug the ethernet and plug it back in. I did nothing more sophisticated than that...

```
Oct  8 07:04:47 max-Z87-D3HP dbus[730]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully called chroot.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully dropped privileges.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully limited resources.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Running.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Watchdog thread running.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Canary thread running.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2008 of process 2008 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 1 threads of 1 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2021 of process 2008 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 2 threads of 1 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2023 of process 2008 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 3 threads of 1 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2024 of process 2008 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 4 threads of 1 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2026 of process 2026 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 5 threads of 2 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP pulseaudio[2026]: [pulseaudio] pid.c: Daemon already running.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2028 of process 2028 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:04:47 max-Z87-D3HP rtkit-daemon[2010]: Supervising 5 threads of 2 processes of 1 users.
Oct  8 07:04:47 max-Z87-D3HP pulseaudio[2028]: [pulseaudio] pid.c: Daemon already running.
Oct  8 07:04:46 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2f3f0a3f)
Oct  8 07:04:49 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 (xid=0x2f3f0a3f)
Oct  8 07:04:49 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:04:49 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:04:49 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:04:49 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2178 of process 2178 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Supervising 5 threads of 2 processes of 1 users.
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2179 of process 2178 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Supervising 6 threads of 2 processes of 1 users.
Oct  8 07:04:54 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x2f3f0a3f)
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2181 of process 2178 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:54 max-Z87-D3HP rtkit-daemon[2010]: Supervising 7 threads of 2 processes of 1 users.
Oct  8 07:04:55 max-Z87-D3HP rtkit-daemon[2010]: Successfully made thread 2182 of process 2178 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:04:55 max-Z87-D3HP rtkit-daemon[2010]: Supervising 8 threads of 2 processes of 1 users.
Oct  8 07:04:55 max-Z87-D3HP pulseaudio[2178]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct  8 07:04:55 max-Z87-D3HP pulseaudio[2178]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct  8 07:04:57 max-Z87-D3HP kernel: [   35.108960] type=1400 audit(1412712297.474:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2194 comm="apparmor_parser"
Oct  8 07:04:57 max-Z87-D3HP kernel: [   35.108966] type=1400 audit(1412712297.474:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2194 comm="apparmor_parser"
Oct  8 07:04:57 max-Z87-D3HP kernel: [   35.109185] type=1400 audit(1412712297.478:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2194 comm="apparmor_parser"
Oct  8 07:04:57 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-Gray..
Oct  8 07:04:57 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-RGB..
Oct  8 07:04:57 max-Z87-D3HP colord: Device added: cups-Photosmart-C4200-series
Oct  8 07:05:01 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21 (xid=0x2f3f0a3f)
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1314
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:05:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:05:14 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:05:14 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:05:14 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:05:15 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:05:15 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:05:15 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2207
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:05:17 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:05:17 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:05:17 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:05:17 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:05:17 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:05:17 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:05:17 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:05:17 max-Z87-D3HP dhclient: 
Oct  8 07:05:17 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:05:17 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:05:17 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:05:17 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:05:17 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x3e304159)
Oct  8 07:05:19 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:05:19 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:05:19 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:05:24 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x3e304159)]
Oct  8 07:05:29 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xb941909)
Oct  8 07:05:32 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 (xid=0xb941909)
Oct  8 07:05:36 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0xb941909)
Oct  8 07:05:37 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:05:37 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:05:37 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:05:37 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:05:45 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0xb941909)
Oct  8 07:05:53 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0xb941909)
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2207
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:06:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:06:02 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:06:02 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:02 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:06:04 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:04 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:06:04 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2219
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:06:05 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:06:05 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:05 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:06:05 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:06:05 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:06:05 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:06:05 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:06:05 max-Z87-D3HP dhclient: 
Oct  8 07:06:05 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:06:05 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:06:05 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:06:05 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:06:05 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x7e770f81)
Oct  8 07:06:06 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:06 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:06:06 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:06:13 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x7e770f81)]
Oct  8 07:06:19 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2012565d)
Oct  8 07:06:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:06:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:06:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:06:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:06:22 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2012565d)
Oct  8 07:06:25 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 (xid=0x2012565d)
Oct  8 07:06:30 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0x2012565d)
Oct  8 07:06:39 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18 (xid=0x2012565d)
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2219
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:06:50 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:06:50 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:06:50 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:50 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:06:52 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:52 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:06:52 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2239
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:06:53 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:06:53 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:53 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:06:53 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:06:53 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:06:53 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:06:53 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:06:53 max-Z87-D3HP dhclient: 
Oct  8 07:06:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:06:53 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:06:53 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:06:53 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:06:53 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x6e183668)
Oct  8 07:06:55 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:06:55 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:06:55 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:07:13 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:07:13 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:07:13 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:07:13 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:07:03 max-Z87-D3HP dhclient: message repeated 3 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x6e183668)]
Oct  8 07:07:14 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x708e5420)
Oct  8 07:07:17 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 (xid=0x708e5420)
Oct  8 07:07:23 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15 (xid=0x708e5420)
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2239
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> Marking connection 'New 802-3-ethernet connection' invalid.
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:07:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:07:38 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:07:38 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:07:38 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:07:40 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:07:40 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:07:40 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:09:27 max-Z87-D3HP anacron[1097]: Job `cron.daily' started
Oct  8 07:09:27 max-Z87-D3HP anacron[2298]: Updated timestamp for job `cron.daily' to 2014-10-08
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2347
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:12:38 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:12:38 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:12:38 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:12:38 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:12:38 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:12:38 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:12:38 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:12:38 max-Z87-D3HP dhclient: 
Oct  8 07:12:38 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:12:38 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:12:38 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:12:38 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:12:38 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x1a833927)
Oct  8 07:12:40 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:12:40 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:12:40 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:12:41 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x1a833927)
Oct  8 07:12:49 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x118d5856)
Oct  8 07:12:52 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x118d5856)
Oct  8 07:12:55 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 (xid=0x118d5856)
Oct  8 07:12:58 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:12:58 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:12:58 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:12:58 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:13:01 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 (xid=0x118d5856)
Oct  8 07:13:11 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15 (xid=0x118d5856)
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2347
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:13:23 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:13:23 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:13:23 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:13:23 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:13:25 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:13:25 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:13:25 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2418
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:13:26 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:13:26 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:13:26 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:13:26 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:13:26 max-Z87-D3HP dhclient: 
Oct  8 07:13:26 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:13:26 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:13:26 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:13:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:13:26 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:13:26 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:13:26 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:13:26 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x6d4304d6)
Oct  8 07:13:28 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:13:28 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:13:28 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:13:34 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x6d4304d6)]
Oct  8 07:13:43 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2767c0a8)
Oct  8 07:13:46 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:13:46 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:13:46 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:13:46 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:13:46 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x2767c0a8)
Oct  8 07:13:53 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12 (xid=0x2767c0a8)
Oct  8 07:14:05 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 (xid=0x2767c0a8)
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2418
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:14:11 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:14:11 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:14:11 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:14:11 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:14:12 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:14:12 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:14:12 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2421
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:14:14 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:14:14 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:14:14 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:14:14 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:14:14 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:14:14 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:14:14 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:14:14 max-Z87-D3HP dhclient: 
Oct  8 07:14:14 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:14:14 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:14:14 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:14:14 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:14:14 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x512cecff)
Oct  8 07:14:15 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:14:15 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:14:15 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:14:22 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x512cecff)]
Oct  8 07:14:30 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x5cb3a40f)
Oct  8 07:14:33 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x5cb3a40f)
Oct  8 07:14:34 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:14:34 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:14:34 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:14:34 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:14:41 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 (xid=0x5cb3a40f)
Oct  8 07:14:51 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11 (xid=0x5cb3a40f)
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2421
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:14:59 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:14:59 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:14:59 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:14:59 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:15:00 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:00 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:15:00 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2454
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:15:02 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:15:02 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:02 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:15:02 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:15:02 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:15:02 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:15:02 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:15:02 max-Z87-D3HP dhclient: 
Oct  8 07:15:02 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:15:02 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:15:02 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:15:02 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:15:02 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x149bd3a3)
Oct  8 07:15:03 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:03 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:15:03 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:15:11 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x149bd3a3)]
Oct  8 07:15:20 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x7b797f75)
Oct  8 07:15:22 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:15:22 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:15:22 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:15:22 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:15:23 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x7b797f75)
Oct  8 07:15:31 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0x7b797f75)
Oct  8 07:15:40 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 (xid=0x7b797f75)
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2454
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> Marking connection 'New 802-3-ethernet connection' invalid.
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:15:47 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:15:47 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:15:47 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:47 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:15:49 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:49 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:15:49 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2458
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:15:55 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:15:55 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:55 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:15:55 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:15:55 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:15:55 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:15:55 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:15:55 max-Z87-D3HP dhclient: 
Oct  8 07:15:55 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:15:55 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:15:55 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:15:55 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:15:55 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0xb86b1e7)
Oct  8 07:15:57 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> disconnected (reason 'user-requested') [70 30 39]
Oct  8 07:15:57 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Oct  8 07:15:57 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2458
Oct  8 07:15:57 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:15:58 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:15:58 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:15:58 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2460
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:16:07 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:16:07 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:16:07 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:16:07 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:16:07 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:16:07 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:16:07 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:16:07 max-Z87-D3HP dhclient: 
Oct  8 07:16:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:16:07 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:16:07 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:16:07 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:16:07 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0xd49fa3d)
Oct  8 07:16:08 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:16:08 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:16:08 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:16:14 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0xd49fa3d)]
Oct  8 07:16:24 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xc0585f5)
Oct  8 07:16:27 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0xc0585f5)
Oct  8 07:16:28 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:16:28 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:16:28 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:16:28 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  8 07:16:34 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0xc0585f5)
Oct  8 07:16:43 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 (xid=0xc0585f5)
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <warn> (eth1): DHCPv4 request timed out.
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2460
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now DISCONNECTED
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> Marking connection 'New 802-3-ethernet connection' invalid.
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <warn> Activation (eth1) failed for connection 'New 802-3-ethernet connection'
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  8 07:16:53 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  8 07:16:53 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:16:53 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:16:53 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:16:55 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:16:55 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:16:55 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:17:01 max-Z87-D3HP CRON[2464]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  8 07:17:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): carrier now OFF (device state 30)
Oct  8 07:17:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Oct  8 07:17:07 max-Z87-D3HP NetworkManager[923]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
Oct  8 07:17:07 max-Z87-D3HP kernel: [  764.153681] e1000e: eth1 NIC Link is Down
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): carrier now ON (device state 20)
Oct  8 07:17:25 max-Z87-D3HP kernel: [  782.823979] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Oct  8 07:17:25 max-Z87-D3HP kernel: [  782.823989] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Auto-activating connection 'New 802-3-ethernet connection'.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) starting connection 'New 802-3-ethernet connection'
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTING
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> dhclient started with pid 2466
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Beginning IP6 addrconf.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  8 07:17:25 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  8 07:17:25 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  8 07:17:25 max-Z87-D3HP dhclient: All rights reserved.
Oct  8 07:17:25 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  8 07:17:25 max-Z87-D3HP dhclient: 
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  8 07:17:25 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  8 07:17:25 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  8 07:17:25 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  8 07:17:25 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x5a9676ed)
Oct  8 07:17:25 max-Z87-D3HP dhclient: DHCPACK of 10.1.1.16 from 10.1.1.1
Oct  8 07:17:25 max-Z87-D3HP dhclient: bound to 10.1.1.16 -- renewal in 40575 seconds.
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info>   address 10.1.1.16
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info>   prefix 24 (255.255.255.0)
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info>   gateway 10.1.1.1
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info>   nameserver '10.1.1.1'
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info>   domain name 'BoB'
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct  8 07:17:25 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.16.
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv4 for mDNS.
Oct  8 07:17:25 max-Z87-D3HP avahi-daemon[824]: Registering new address record for 10.1.1.16 on eth1.IPv4.
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct  8 07:17:26 max-Z87-D3HP avahi-daemon[824]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  8 07:17:26 max-Z87-D3HP avahi-daemon[824]: New relevant interface eth1.IPv6 for mDNS.
Oct  8 07:17:26 max-Z87-D3HP avahi-daemon[824]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> Policy set 'New 802-3-ethernet connection' (eth1) as default for IPv4 routing and DNS.
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> DNS: starting dnsmasq...
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <warn> dnsmasq not available on the bus, can't update servers.
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <error> [1412713046.947797] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <warn> DNS: plugin dnsmasq update failed
Oct  8 07:17:26 max-Z87-D3HP NetworkManager[923]: <info> Writing DNS information to /sbin/resolvconf
Oct  8 07:17:26 max-Z87-D3HP dnsmasq[2469]: started, version 2.68 cache disabled
Oct  8 07:17:26 max-Z87-D3HP dnsmasq[2469]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Oct  8 07:17:26 max-Z87-D3HP dnsmasq[2469]: DBus support enabled: connected to system bus
Oct  8 07:17:26 max-Z87-D3HP dnsmasq[2469]: warning: no upstream servers configured
Oct  8 07:17:26 max-Z87-D3HP whoopsie[1111]: message repeated 22 times: [ offline]
Oct  8 07:17:29 max-Z87-D3HP whoopsie[1111]: Could not get the list of active connections: Timeout was reached
Oct  8 07:17:29 max-Z87-D3HP whoopsie[1111]: offline
Oct  8 07:17:37 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) successful, device activated.
Oct  8 07:17:37 max-Z87-D3HP dbus[730]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  8 07:17:37 max-Z87-D3HP NetworkManager[923]: <warn> dnsmasq appeared on DBus: :1.76
Oct  8 07:17:37 max-Z87-D3HP NetworkManager[923]: <info> Writing DNS information to /sbin/resolvconf
Oct  8 07:17:37 max-Z87-D3HP dnsmasq[2469]: setting upstream servers from DBus
Oct  8 07:17:37 max-Z87-D3HP dnsmasq[2469]: using nameserver 10.1.1.1#53
Oct  8 07:17:37 max-Z87-D3HP dbus[730]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  8 07:17:44 max-Z87-D3HP ntpdate[2577]: adjust time server 91.189.89.199 offset 0.394793 sec
Oct  8 07:17:47 max-Z87-D3HP NetworkManager[923]: <info> (eth1): IP6 addrconf timed out or failed.
Oct  8 07:17:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  8 07:17:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  8 07:17:47 max-Z87-D3HP NetworkManager[923]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

---

### Post by tgalati4 on 2014-10-07
You appear to have an IPv4 vs IPv6 issue.  Search the forums for different ways to turn off IPv6 and just use IPv4.  The simple way is to Right-click the connection icon on the panel and "Edit Connections"  Set up IPv4 connections under the IPv4 tab, and select "Ignore" for IPv6 tab.

---

### Post by varunendra on 2014-10-07
Do you create the connection profile in NM manually or is it created automatically? I am suspecting if you happen to put something in the "Device MAC address" field. It is usually empty, or picked up automatically.

Also, the Gigabyte motherboards have a feature called "IOMMU" in their BIOS. Quite often (or perhaps always) it needs to be enabled to work properly with Linux. Either that, or using a boot parameter "iommu=soft" along with the default options ("quite splash" in /etc/default/grub).

**PS:**
To disable IPv6 completely, if required : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

--

---

### Post by maxinstuff2 on 2014-10-08
> **varunendra said:**
> Do you create the connection profile in NM manually or is it created automatically? I am suspecting if you happen to put something in the "Device MAC address" field. It is usually empty, or picked up automatically.

Also, the Gigabyte motherboards have a feature called "IOMMU" in their BIOS. Quite often (or perhaps always) it needs to be enabled to work properly with Linux. Either that, or using a boot parameter "iommu=soft" along with the default options ("quite splash" in /etc/default/grub).

**PS:**
To disable IPv6 completely, if required : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

--
I am using network manager to "manually" create a wired connection, while the cable is unplugged. Then plug the cable back in and click to connect. With everything set to auto negotiate it will die completely within a day or two, if I manually specify DNS and set a static ip (Only for IPv4 that is) it simply disconnects and unplugging and re plugging the cable alone (without having to delete and recreate the connection) gets me back online. I DO have to unplug the cable, disconnecting and reconnecting in NM does not work.
I'll check bios first and failing that I'll try deactivating IPv6 and see how I go from there.

EDIT: So I poked around in bios and even referred to the manual and there doesn't seem to be anything in there called IOMMU. A bit of googling indicates that the relevant setting could be Vt-d (described in the manual as "enables or disables intel virtualisation technology for directed I/O"*), but this was enabled already by default.
I have recreated my connection with ipv6 set to "ignore" in NM. If that doesn't work I will try disabling it entirely using the instructions in the link above. I noted that I can also disable it in BIOS but I doubt this would stop the OS from attempting it so is probably pointless.
Will report back in a few days!

*superfluous capitalisation and "TM" symbols ommitted. Seriously - this manual's use of capitalisation and trademark signs is a crime against humanity (and the english language).

---

### Post by maxinstuff2 on 2014-10-08
I didn't have to wait long, next morning the issue recurred.
I watched it fail to connect a few times and then unplugged the cable, replugged it a few seconds later and like magic I was back up and running.
THis is really weird...

```
Oct  9 07:29:03 max-Z87-D3HP rtkit-daemon[1973]: Successfully made thread 1988 of process 1988 (n/a) owned by '1000' high priority at nice level -11.
Oct  9 07:29:03 max-Z87-D3HP rtkit-daemon[1973]: Supervising 5 threads of 2 processes of 1 users.
Oct  9 07:29:03 max-Z87-D3HP pulseaudio[1988]: [pulseaudio] pid.c: Daemon already running.
Oct  9 07:29:06 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 (xid=0x396f2a40)
Oct  9 07:29:09 max-Z87-D3HP rtkit-daemon[1973]: Successfully made thread 2139 of process 2139 (n/a) owned by '1000' high priority at nice level -11.
Oct  9 07:29:09 max-Z87-D3HP rtkit-daemon[1973]: Supervising 5 threads of 2 processes of 1 users.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Successfully made thread 2140 of process 2139 (n/a) owned by '1000' RT at priority 5.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Supervising 6 threads of 2 processes of 1 users.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Successfully made thread 2141 of process 2139 (n/a) owned by '1000' RT at priority 5.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Supervising 7 threads of 2 processes of 1 users.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Successfully made thread 2142 of process 2139 (n/a) owned by '1000' RT at priority 5.
Oct  9 07:29:10 max-Z87-D3HP rtkit-daemon[1973]: Supervising 8 threads of 2 processes of 1 users.
Oct  9 07:29:10 max-Z87-D3HP pulseaudio[2139]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct  9 07:29:10 max-Z87-D3HP pulseaudio[2139]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct  9 07:29:12 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x396f2a40)
Oct  9 07:29:15 max-Z87-D3HP kernel: [   35.178730] type=1400 audit(1412800155.486:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2159 comm="apparmor_parser"
Oct  9 07:29:15 max-Z87-D3HP kernel: [   35.178735] type=1400 audit(1412800155.486:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2159 comm="apparmor_parser"
Oct  9 07:29:15 max-Z87-D3HP kernel: [   35.178940] type=1400 audit(1412800155.486:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2159 comm="apparmor_parser"
Oct  9 07:29:15 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-Gray..
Oct  9 07:29:15 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-RGB..
Oct  9 07:29:15 max-Z87-D3HP colord: Device added: cups-Photosmart-C4200-series
Oct  9 07:29:20 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0x396f2a40)
Oct  9 07:29:29 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 (xid=0x396f2a40)
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <warn> (eth1): DHCPv4 request timed out.
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1278
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now DISCONNECTED
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <warn> Activation (eth1) failed for connection 'home'
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  9 07:29:32 max-Z87-D3HP NetworkManager[925]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  9 07:29:32 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:29:32 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:29:32 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:29:34 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:29:34 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:29:34 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Auto-activating connection 'home'.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) starting connection 'home'
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now CONNECTING
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> dhclient started with pid 2172
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 07:29:35 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:29:35 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:29:35 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:29:35 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  9 07:29:35 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  9 07:29:35 max-Z87-D3HP dhclient: All rights reserved.
Oct  9 07:29:35 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  9 07:29:35 max-Z87-D3HP dhclient: 
Oct  9 07:29:35 max-Z87-D3HP NetworkManager[925]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  9 07:29:35 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  9 07:29:35 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  9 07:29:35 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  9 07:29:35 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x3baad601)
Oct  9 07:29:37 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:29:37 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:29:37 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:29:44 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x3baad601)]
Oct  9 07:30:01 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x58f842d9)
Oct  9 07:30:01 max-Z87-D3HP CRON[2185]: (root) CMD (start -q anacron || :)
Oct  9 07:30:01 max-Z87-D3HP CRON[2184]: (CRON) info (No MTA installed, discarding output)
Oct  9 07:30:04 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 (xid=0x58f842d9)
Oct  9 07:30:10 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 (xid=0x58f842d9)
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <warn> (eth1): DHCPv4 request timed out.
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2172
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now DISCONNECTED
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <warn> Activation (eth1) failed for connection 'home'
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  9 07:30:20 max-Z87-D3HP NetworkManager[925]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  9 07:30:20 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:30:20 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:30:20 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:30:21 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:30:21 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:30:21 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Auto-activating connection 'home'.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) starting connection 'home'
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now CONNECTING
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> dhclient started with pid 2187
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 07:30:23 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:30:23 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:30:23 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:30:23 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  9 07:30:23 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  9 07:30:23 max-Z87-D3HP dhclient: All rights reserved.
Oct  9 07:30:23 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  9 07:30:23 max-Z87-D3HP dhclient: 
Oct  9 07:30:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  9 07:30:23 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  9 07:30:23 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  9 07:30:23 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  9 07:30:23 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x455797d6)
Oct  9 07:30:24 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:30:24 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:30:24 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:30:30 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x455797d6)]
Oct  9 07:30:34 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2268047a)
Oct  9 07:30:37 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x2268047a)
Oct  9 07:30:44 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 (xid=0x2268047a)
Oct  9 07:30:58 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x2268047a)
Oct  9 07:31:06 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19 (xid=0x2268047a)
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <warn> (eth1): DHCPv4 request timed out.
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2187
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now DISCONNECTED
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <warn> Activation (eth1) failed for connection 'home'
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  9 07:31:08 max-Z87-D3HP NetworkManager[925]: <info> (eth1): deactivating device (reason 'none') [0]
Oct  9 07:31:08 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:31:08 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:08 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:31:09 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:09 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:31:09 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Auto-activating connection 'home'.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) starting connection 'home'
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now CONNECTING
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> dhclient started with pid 2207
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 07:31:11 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:31:11 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:11 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:31:11 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  9 07:31:11 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  9 07:31:11 max-Z87-D3HP dhclient: All rights reserved.
Oct  9 07:31:11 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  9 07:31:11 max-Z87-D3HP dhclient: 
Oct  9 07:31:11 max-Z87-D3HP NetworkManager[925]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  9 07:31:11 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  9 07:31:11 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  9 07:31:11 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  9 07:31:11 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x74958258)
Oct  9 07:31:12 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:12 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:31:12 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:31:18 max-Z87-D3HP NetworkManager[925]: <info> (eth1): carrier now OFF (device state 70, deferring action for 4 seconds)
Oct  9 07:31:18 max-Z87-D3HP kernel: [  158.520962] e1000e: eth1 NIC Link is Down
Oct  9 07:31:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
Oct  9 07:31:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
Oct  9 07:31:23 max-Z87-D3HP NetworkManager[925]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2207
Oct  9 07:31:23 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now DISCONNECTED
Oct  9 07:31:23 max-Z87-D3HP avahi-daemon[878]: Withdrawing address record for fe80::96de:80ff:fe77:6519 on eth1.
Oct  9 07:31:23 max-Z87-D3HP avahi-daemon[878]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:23 max-Z87-D3HP avahi-daemon[878]: Interface eth1.IPv6 no longer relevant for mDNS.
Oct  9 07:31:23 max-Z87-D3HP kernel: [  163.065288] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): carrier now ON (device state 20)
Oct  9 07:31:37 max-Z87-D3HP kernel: [  176.913411] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Oct  9 07:31:37 max-Z87-D3HP kernel: [  176.913422] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
Oct  9 07:31:37 max-Z87-D3HP kernel: [  176.913480] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Auto-activating connection 'home'.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) starting connection 'home'
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now CONNECTING
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> dhclient started with pid 2209
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 07:31:37 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  9 07:31:37 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  9 07:31:37 max-Z87-D3HP dhclient: All rights reserved.
Oct  9 07:31:37 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  9 07:31:37 max-Z87-D3HP dhclient: 
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  9 07:31:37 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct  9 07:31:37 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct  9 07:31:37 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct  9 07:31:37 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x398942d0)
Oct  9 07:31:37 max-Z87-D3HP dhclient: DHCPACK of 10.1.1.16 from 10.1.1.1
Oct  9 07:31:37 max-Z87-D3HP dhclient: bound to 10.1.1.16 -- renewal in 36167 seconds.
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info>   address 10.1.1.16
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info>   prefix 24 (255.255.255.0)
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info>   gateway 10.1.1.1
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info>   nameserver '10.1.1.1'
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info>   domain name 'BoB'
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct  9 07:31:37 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Oct  9 07:31:37 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.16.
Oct  9 07:31:37 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv4 for mDNS.
Oct  9 07:31:37 max-Z87-D3HP avahi-daemon[878]: Registering new address record for 10.1.1.16 on eth1.IPv4.
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> Policy set 'home' (eth1) as default for IPv4 routing and DNS.
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> DNS: starting dnsmasq...
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <warn> dnsmasq not available on the bus, can't update servers.
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <error> [1412800298.687360] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <warn> DNS: plugin dnsmasq update failed
Oct  9 07:31:38 max-Z87-D3HP NetworkManager[925]: <info> Writing DNS information to /sbin/resolvconf
Oct  9 07:31:38 max-Z87-D3HP dnsmasq[2212]: started, version 2.68 cache disabled
Oct  9 07:31:38 max-Z87-D3HP dnsmasq[2212]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Oct  9 07:31:38 max-Z87-D3HP dnsmasq[2212]: DBus support enabled: connected to system bus
Oct  9 07:31:38 max-Z87-D3HP dnsmasq[2212]: warning: no upstream servers configured
Oct  9 07:31:38 max-Z87-D3HP avahi-daemon[878]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fe77:6519.
Oct  9 07:31:38 max-Z87-D3HP avahi-daemon[878]: New relevant interface eth1.IPv6 for mDNS.
Oct  9 07:31:38 max-Z87-D3HP avahi-daemon[878]: Registering new address record for fe80::96de:80ff:fe77:6519 on eth1.*.
Oct  9 07:31:38 max-Z87-D3HP whoopsie[1099]: message repeated 10 times: [ offline]
Oct  9 07:31:41 max-Z87-D3HP whoopsie[1099]: Could not get the list of active connections: Timeout was reached
Oct  9 07:31:41 max-Z87-D3HP whoopsie[1099]: offline
Oct  9 07:31:48 max-Z87-D3HP NetworkManager[925]: <info> Activation (eth1) successful, device activated.
Oct  9 07:31:48 max-Z87-D3HP dbus[748]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  9 07:31:48 max-Z87-D3HP NetworkManager[925]: <warn> dnsmasq appeared on DBus: :1.66
Oct  9 07:31:48 max-Z87-D3HP NetworkManager[925]: <info> Writing DNS information to /sbin/resolvconf
Oct  9 07:31:48 max-Z87-D3HP dnsmasq[2212]: setting upstream servers from DBus
Oct  9 07:31:48 max-Z87-D3HP dnsmasq[2212]: using nameserver 10.1.1.1#53
Oct  9 07:31:48 max-Z87-D3HP dbus[748]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  9 07:31:56 max-Z87-D3HP ntpdate[2316]: step time server 91.189.89.199 offset 0.560624 sec
```

This is with the connection set to ignore IPv6....
I have now disabled it by adding the lines below to my /etc/sysctl.conf (from the link suggested) -
```
# disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
```

See how we go, although I only see a single ipv6 reference in the log which I think is acknowledgement of the ignore option so I suspect this will be redundant.

**EDIT: **I am also procuring a known supported PCI-E ethernet card to rule out driver issues. Regardless of the results it is something I should probably keep laying around anyway. This one, listed as supported from kernel 2.2.5
[http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134&cm_re=Intel_PWLA8391GTBLK-_-33-106-121-_-Product](http://www.newegg.com/Product/Product.aspx?Item=9SIA24G1XA5134&cm_re=Intel_PWLA8391GTBLK-_-33-106-121-_-Product)
(by the way, someone at newegg is having a laugh with that discount :D )

---

### Post by varunendra on 2014-10-08
> **maxinstuff2 said:**
> (by the way, someone at newegg is having a laugh with that discount :D )

Looks like a serious discount to me -
> **$31.08**
[COLOR="#FF0000"]Save: $1,028.92 (97%)[/COLOR]
:|

If I were you, I would build a beautiful showcase for it, made of bullet-proof glass, decorated with precious gems and diamonds!

---

### Post by maxinstuff2 on 2014-10-09
So disabling IPv6 was ineffective - I'll have this other network card tomorrow so that's my next test.
```
Oct 10 07:38:17 max-Z87-D3HP rtkit-daemon[1970]: Successfully made thread 2146 of process 2140 (n/a) owned by '1000' RT at priority 5.
Oct 10 07:38:17 max-Z87-D3HP rtkit-daemon[1970]: Supervising 8 threads of 2 processes of 1 users.
Oct 10 07:38:17 max-Z87-D3HP pulseaudio[2140]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct 10 07:38:17 max-Z87-D3HP pulseaudio[2140]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Oct 10 07:38:03 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x63db0361)]
Oct 10 07:38:18 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x425da58d)
Oct 10 07:38:21 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 (xid=0x425da58d)
Oct 10 07:38:21 max-Z87-D3HP kernel: [   34.458675] audit_printk_skb: 99 callbacks suppressed
Oct 10 07:38:21 max-Z87-D3HP kernel: [   34.458678] type=1400 audit(1412887101.748:44): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2161 comm="apparmor_parser"
Oct 10 07:38:21 max-Z87-D3HP kernel: [   34.458682] type=1400 audit(1412887101.748:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2161 comm="apparmor_parser"
Oct 10 07:38:21 max-Z87-D3HP kernel: [   34.458889] type=1400 audit(1412887101.748:46): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2161 comm="apparmor_parser"
Oct 10 07:38:21 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-Gray..
Oct 10 07:38:21 max-Z87-D3HP colord: Profile added: Photosmart-C4200-series-RGB..
Oct 10 07:38:21 max-Z87-D3HP colord: Device added: cups-Photosmart-C4200-series
Oct 10 07:38:25 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 (xid=0x425da58d)
Oct 10 07:38:35 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x425da58d)
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <warn> (eth1): DHCPv4 request timed out.
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1287
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now DISCONNECTED
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <warn> Activation (eth1) failed for connection 'home'
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 10 07:38:38 max-Z87-D3HP NetworkManager[834]: <info> (eth1): deactivating device (reason 'none') [0]
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Auto-activating connection 'home'.
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) starting connection 'home'
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now CONNECTING
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> dhclient started with pid 2175
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 07:38:41 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 10 07:38:41 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 10 07:38:41 max-Z87-D3HP dhclient: All rights reserved.
Oct 10 07:38:41 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 10 07:38:41 max-Z87-D3HP dhclient: 
Oct 10 07:38:41 max-Z87-D3HP NetworkManager[834]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct 10 07:38:41 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct 10 07:38:41 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct 10 07:38:41 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct 10 07:38:41 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x1cbf6583)
Oct 10 07:38:51 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x1cbf6583)]
Oct 10 07:39:09 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x62f732c2)
Oct 10 07:39:12 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x62f732c2)
Oct 10 07:39:20 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16 (xid=0x62f732c2)
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <warn> (eth1): DHCPv4 request timed out.
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2175
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now DISCONNECTED
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <warn> Activation (eth1) failed for connection 'home'
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 10 07:39:26 max-Z87-D3HP NetworkManager[834]: <info> (eth1): deactivating device (reason 'none') [0]
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Auto-activating connection 'home'.
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) starting connection 'home'
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now CONNECTING
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> dhclient started with pid 2187
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 07:39:29 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 10 07:39:29 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 10 07:39:29 max-Z87-D3HP dhclient: All rights reserved.
Oct 10 07:39:29 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 10 07:39:29 max-Z87-D3HP dhclient: 
Oct 10 07:39:29 max-Z87-D3HP NetworkManager[834]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct 10 07:39:29 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct 10 07:39:29 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct 10 07:39:29 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct 10 07:39:29 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x5d039b73)
Oct 10 07:39:35 max-Z87-D3HP dhclient: message repeated 2 times: [ DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x5d039b73)]
Oct 10 07:39:40 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x4c3dfe63)
Oct 10 07:39:43 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x4c3dfe63)
Oct 10 07:39:46 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 (xid=0x4c3dfe63)
Oct 10 07:39:52 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x4c3dfe63)
Oct 10 07:39:59 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 (xid=0x4c3dfe63)
Oct 10 07:40:07 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12 (xid=0x4c3dfe63)
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <warn> (eth1): DHCPv4 request timed out.
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2187
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now DISCONNECTED
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <warn> Activation (eth1) failed for connection 'home'
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 10 07:40:14 max-Z87-D3HP NetworkManager[834]: <info> (eth1): deactivating device (reason 'none') [0]
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Auto-activating connection 'home'.
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) starting connection 'home'
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now CONNECTING
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> dhclient started with pid 2260
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 07:40:17 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 10 07:40:17 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 10 07:40:17 max-Z87-D3HP dhclient: All rights reserved.
Oct 10 07:40:17 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 10 07:40:17 max-Z87-D3HP dhclient: 
Oct 10 07:40:17 max-Z87-D3HP NetworkManager[834]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct 10 07:40:17 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct 10 07:40:17 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct 10 07:40:17 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct 10 07:40:17 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0xb82e112)
Oct 10 07:40:23 max-Z87-D3HP NetworkManager[834]: <info> (eth1): carrier now OFF (device state 70, deferring action for 4 seconds)
Oct 10 07:40:23 max-Z87-D3HP kernel: [  156.333039] e1000e: eth1 NIC Link is Down
Oct 10 07:40:20 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0xb82e112)
Oct 10 07:40:28 max-Z87-D3HP dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xd8dcb91)
Oct 10 07:40:28 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
Oct 10 07:40:28 max-Z87-D3HP NetworkManager[834]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
Oct 10 07:40:28 max-Z87-D3HP NetworkManager[834]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2260
Oct 10 07:40:28 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now DISCONNECTED
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): carrier now ON (device state 20)
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Auto-activating connection 'home'.
Oct 10 07:40:36 max-Z87-D3HP kernel: [  168.641754] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Oct 10 07:40:36 max-Z87-D3HP kernel: [  168.641765] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) starting connection 'home'
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now CONNECTING
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> dhclient started with pid 2262
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Oct 10 07:40:36 max-Z87-D3HP dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 10 07:40:36 max-Z87-D3HP dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 10 07:40:36 max-Z87-D3HP dhclient: All rights reserved.
Oct 10 07:40:36 max-Z87-D3HP dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 10 07:40:36 max-Z87-D3HP dhclient: 
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct 10 07:40:36 max-Z87-D3HP dhclient: Listening on LPF/eth1/94:de:80:77:65:19
Oct 10 07:40:36 max-Z87-D3HP dhclient: Sending on   LPF/eth1/94:de:80:77:65:19
Oct 10 07:40:36 max-Z87-D3HP dhclient: Sending on   Socket/fallback
Oct 10 07:40:36 max-Z87-D3HP dhclient: DHCPREQUEST of 10.1.1.16 on eth1 to 255.255.255.255 port 67 (xid=0x4f008d36)
Oct 10 07:40:36 max-Z87-D3HP dhclient: DHCPACK of 10.1.1.16 from 10.1.1.1
Oct 10 07:40:36 max-Z87-D3HP dhclient: bound to 10.1.1.16 -- renewal in 43033 seconds.
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info>   address 10.1.1.16
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info>   prefix 24 (255.255.255.0)
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info>   gateway 10.1.1.1
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info>   nameserver '10.1.1.1'
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct 10 07:40:36 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Oct 10 07:40:36 max-Z87-D3HP avahi-daemon[814]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.16.
Oct 10 07:40:36 max-Z87-D3HP avahi-daemon[814]: New relevant interface eth1.IPv4 for mDNS.
Oct 10 07:40:36 max-Z87-D3HP avahi-daemon[814]: Registering new address record for 10.1.1.16 on eth1.IPv4.
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> Policy set 'home' (eth1) as default for IPv4 routing and DNS.
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> DNS: starting dnsmasq...
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <warn> dnsmasq not available on the bus, can't update servers.
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <error> [1412887237.109400] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <warn> DNS: plugin dnsmasq update failed
Oct 10 07:40:37 max-Z87-D3HP NetworkManager[834]: <info> Writing DNS information to /sbin/resolvconf
Oct 10 07:40:37 max-Z87-D3HP dnsmasq[2265]: started, version 2.68 cache disabled
Oct 10 07:40:37 max-Z87-D3HP dnsmasq[2265]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Oct 10 07:40:37 max-Z87-D3HP dnsmasq[2265]: DBus support enabled: connected to system bus
Oct 10 07:40:37 max-Z87-D3HP dnsmasq[2265]: warning: no upstream servers configured
Oct 10 07:40:37 max-Z87-D3HP whoopsie[1060]: message repeated 10 times: [ offline]
Oct 10 07:40:40 max-Z87-D3HP whoopsie[1060]: Could not get the list of active connections: Timeout was reached
Oct 10 07:40:40 max-Z87-D3HP whoopsie[1060]: offline
Oct 10 07:40:47 max-Z87-D3HP NetworkManager[834]: <info> Activation (eth1) successful, device activated.
Oct 10 07:40:47 max-Z87-D3HP dbus[684]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 10 07:40:47 max-Z87-D3HP NetworkManager[834]: <warn> dnsmasq appeared on DBus: :1.69
Oct 10 07:40:47 max-Z87-D3HP NetworkManager[834]: <info> Writing DNS information to /sbin/resolvconf
Oct 10 07:40:47 max-Z87-D3HP dnsmasq[2265]: setting upstream servers from DBus
Oct 10 07:40:47 max-Z87-D3HP dnsmasq[2265]: using nameserver 10.1.1.1#53
Oct 10 07:40:47 max-Z87-D3HP dbus[684]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 10 07:40:55 max-Z87-D3HP ntpdate[2370]: step time server 91.189.89.199 offset 0.963622 sec
```

---

### Post by tgalati4 on 2014-10-09
It's possible your router has developed a problem.  Have you updated the firmware in the router?  Do you have another router to test with?

---

### Post by maxinstuff2 on 2014-10-09
Firmware is the latest version, however the router is a few years old. I DO have another one but it is even older and all bets are off with the firmware on that thing!

I don't think it is the router as other devices are not having this issue, but I will try this.

**EDIT:** I installed the intel network card on Saturday and it is now Monday morning - it's been solid. 
I've re-enabled ipv6 and set it back to auto in NM. If there are no issues in the next couple of days I'll mark this as solved.

---

### Post by maxinstuff2 on 2014-10-13
So I haven't had any issues since Saturday when I installed the intel PCI ethernet card, and restored all the config that I had previously changed during the troubleshooting process. 
I will give it a couple more days to make sure, but I have noted that the log is significantly different than before (comparing successful connections):
```
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> (eth2): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) complete.
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> (eth2): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct 13 18:53:39 max-Z87-D3HP whoopsie[1139]: offline
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> Policy set 'home' (eth2) as default for IPv4 routing and DNS.
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> DNS: starting dnsmasq...
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <warn> dnsmasq not available on the bus, can't update servers.
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <error> [1413186819.637723] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <warn> DNS: plugin dnsmasq update failed
Oct 13 18:53:39 max-Z87-D3HP NetworkManager[936]: <info> Writing DNS information to /sbin/resolvconf
Oct 13 18:53:39 max-Z87-D3HP dnsmasq[1262]: started, version 2.68 cache disabled
Oct 13 18:53:39 max-Z87-D3HP dnsmasq[1262]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Oct 13 18:53:39 max-Z87-D3HP dnsmasq[1262]: DBus support enabled: connected to system bus
Oct 13 18:53:39 max-Z87-D3HP dnsmasq[1262]: warning: no upstream servers configured
Oct 13 18:53:39 max-Z87-D3HP dbus[708]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Oct 13 18:53:39 max-Z87-D3HP accounts-daemon[1329]: started daemon version 0.6.35
Oct 13 18:53:39 max-Z87-D3HP dbus[708]: [system] Successfully activated service 'org.freedesktop.Accounts'
Oct 13 18:53:39 max-Z87-D3HP avahi-daemon[888]: Joining mDNS multicast group on interface eth2.IPv6 with address fe80::92e2:baff:fe7b:cd0e.
Oct 13 18:53:39 max-Z87-D3HP avahi-daemon[888]: New relevant interface eth2.IPv6 for mDNS.
Oct 13 18:53:39 max-Z87-D3HP avahi-daemon[888]: Registering new address record for fe80::92e2:baff:fe7b:cd0e on eth2.*.
```

---

### Post by maxinstuff2 on 2014-10-15
No further issues on the new card - so marking this solved.

I guess it is a kernel driver issue with the ethernet hardware on my motherboard. No issues with the PCIe ethernet card.

---

