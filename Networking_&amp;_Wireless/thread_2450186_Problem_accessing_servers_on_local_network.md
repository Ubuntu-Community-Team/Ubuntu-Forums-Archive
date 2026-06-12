---
title: "Problem accessing servers on local network"
date: 2020-09-09
forum: Networking &amp; Wireless
---

### Post by zmsc12 on 2020-09-09
A couple of days ago I wanted to access my Linksys router's admin page on 192.168.1.1 from my (six-month-old) Ubuntu 20.04 laptop. I've done this many times before, no problem, but this time it timed out. So I got out my old Macbook Air, connected immediately and did what needed to be done. Then I noticed that my laptop isn't replicating with Nextcloud any more. Nextcloud is on 192.168.1.144. And I can't connect to the new Presspi instance I've been playing with. All these thing are accessible from my Macbook and from a truly ancient laptop that runs Lubuntu, but not from my new laptop. So what's causing my laptop, which works perfectly in all other ways to refuse to connect to any web service on my local LAN? It appears I can connect to any address but not 192.168.1.*

Your expert advice will be very welcome.

TIA,
Stuart

---

### Post by TheFu on 2020-09-09
First, lets determine if this is a networking problem or just name resolution on the LAN.
This sort of issue comes up enough that I wrote a blog post about it with steps to be done - IN ORDER.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
The 'ping' steps are really helpful for determining if this is really a network problem or just DNS/LAN name lookup problem.  Don't blindly copy/paste the commands in the blog. Each will need to be changed for YOUR network.

---

### Post by zmsc12 on 2020-09-09
Thanks very much for that JD.

dmesg reports IP as 192.168.1.141 as expected - I use DHCP with reserved addresses so I can put names of my various equipment in the hosts file

lshw confirms my gateway address as 192.168.1.1 - a Linksys router. Until a couple of days ago, I was able to connect to its admin interface, but I can't now. However I can connect to it from other PCs on my network.

pinging the gateway address gives "operation not permitted" - as does pinging any 192.168.1.*

ifconfig shows packets sent and received, with no dropped packets

resolv.conf gives nameserver as 127.0.0.53 - I assume that means look up addresses locally first before using DNS

Reading elsewhere, I understand some people have reported problems after using NordVPN killswitch to disable network if their VPN is down. I use NordVPN, but I haven't used the killswitch option.

---

### Post by TheFu on 2020-09-09
Please post the output from the commands that the blog post suggests.  Facts.  Not descriptions of what you *think* is happening.  BTW, recently firefox started enabling DNS-over-HTTPS. If you enable that, it may not allow any LAN websites to be accessed.

I'd also be concerned about any Linksys router being hacked.  Has the firmware been patched in the last 2 months?  Consumer routers are notorious for poor firmware updates after 2-3 years.  [https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/](https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/)

If ping by IP is working between the devices, then this is a name resolution problem. Period. If ping doesn't work between all the devices, then note which is failing and check that target for firewall rules getting in the way. If ufw is being used, beware that it doesn't control the whole firewall ruleset.  I've been burned by this a few times on systems where I have thousands of blocked subnets and use ipset to make those much more efficient.

127.0.0.53 is supposed to be a local DNS caching server.  Ubuntu has been pushing these the last 8 yrs and I've always had problems with them.  About the last 2 year, I find it easier disable their overly complex solution at the first sign of trouble and use the 1992 method which still works - just edit the /etc/resolv.conf file.  We have to disable and remove the systemd.resolved and resolvconf packages or this doesn't work.

BTW, I've been running nextcloud for a few years, but barely use the file sync aspects. For me, it is all about the addons for RSS feeds, GPS tracks, and contacts.  I do have some read-only access to files (videos/photos/music/ebooks) through nextcloud, but generally don't trust it and use other tools instead (plex, calibre, a custom perl gallery, and NFS).  Perhaps if nextcloud arrived 10 yrs ago, I'd be using it as the primary.  Some nextcloud updates break some addons.  This year, I've been left with nextcloud that refuses to work 3 times after an update due to incompatible addons. Sadly, the errors in the logs seldom pinpoint the failed addon, so it becomes trial and error to see by removal which allows the core system to work again.
Oh, and the "Talk" addon is pretty great for family video conferences. We usually have wider meetings on Jitsi, but for 1-on-1 where security is more important, nextcloud-talk is what I choose.

---

### Post by zmsc12 on 2020-09-10
Thanks for that ... output from the various diagnostics suggested

 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 7c:2a:31:3c:50:96 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.141/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp1s0
       valid_lft 85811sec preferred_lft 85811sec
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.8.3.16/24 brd 10.8.3.255 scope global tun0
       valid_lft forever preferred_lft forever
       
****************************************************************************       
 $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.3.1        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    20600  0        0 wlp1s0
10.8.3.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
128.0.0.0       10.8.3.1        128.0.0.0       UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
185.134.22.218  192.168.1.1     255.255.255.255 UGH   0      0        0 wlp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

*****************************************************************************
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 192.168.1.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6134ms

*****************************************************************************
$ dmesg | grep wlp1
[    4.437068] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    9.573893] wlp1s0: authenticate with 30:23:03:df:2c:52
[    9.583985] wlp1s0: send auth to 30:23:03:df:2c:52 (try 1/3)
[    9.589419] wlp1s0: authenticated
[    9.589592] wlp1s0: associating with AP with corrupt beacon
[    9.591522] wlp1s0: associate with 30:23:03:df:2c:52 (try 1/3)
[    9.593459] wlp1s0: RX AssocResp from 30:23:03:df:2c:52 (capab=0x511 status=0 aid=3)
[    9.597375] wlp1s0: associated
[    9.597399] wlp1s0: Limiting TX power to 14 (17 - 3) dBm as advertised by 30:23:03:df:2c:52
[    9.618117] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

*******************************************************************************
$ sudo lshw -C network
[sudo] password for stuart: 
  *-network                 
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 78
       serial: 7c:2a:31:3c:50:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-45-generic firmware=36.77d01142.0 ip=192.168.1.141 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:135 memory:df100000-df101fff
       
************************************************************************************       
$ ifconfig -a
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1336  bytes 124778 (124.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1336  bytes 124778 (124.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.3.16  netmask 255.255.255.0  destination 10.8.3.16
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 8208  bytes 6658314 (6.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8021  bytes 1071418 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.141  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 7c:2a:31:3c:50:96  txqueuelen 1000  (Ethernet)
        RX packets 8375  bytes 7257688 (7.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8150  bytes 1848561 (1.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

******************************************************************************************
$ more /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0

*******************************************************************************************
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.3.1        128.0.0.0       UG    0      0        0 tun0
default         _gateway        0.0.0.0         UG    20600  0        0 wlp1s0
10.8.3.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
128.0.0.0       10.8.3.1        128.0.0.0       UG    0      0        0 tun0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
218.22.134.185. _gateway        255.255.255.255 UGH   0      0        0 wlp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

*******************************************************************************************
              
I hadn't picked up on the Firefox DNS over HTTPS issue - thanks for bringing that to my attention. When I looked I found that DOH was selected by default, so I switched it off and rebooted - but it didn't make any difference, so that doesn't appear to be the problem.

My Linksys router is very recent, I deliberately moved up from an ISP-provided one - model is WRT3200ACM - and it's on the latest firmware.

On ping, I can ping the router with ping 192.168.1.1 from my ancient Lubuntu laptop and see the appropriate responses. The same command run on my new laptop gives "not permitted".

---

### Post by zmsc12 on 2020-09-10
Thanks for help given - I've now resolved the problem.

There was a strange entry in iptables that (if I understand it correctly) allowed connections in from some specific IP address in China and blocked outgoing connections. I fixed it by resetting iptables to default settings and can now ping local devices and connect to local servers. I imagine the entry in iptables was a result of malware, so I'll need to do more research, but I've at least resolved the particular problem.

---

### Post by TheFu on 2020-09-10
Properly patched systems are very hard to get malware on Linux. If you don't 100% KNOW what happened, it is time to wipe the system and restore only data files.

Never trust a system that may have been successfully attacked and compromised. Never.  With proper versioned backups, wiping and starting over from 27 or 69 days ago is only 30-45 minutes.

BTW, whenever posting shell output, please, please, please use "code tags." Too hard to read otherwise when all the columns don't line up. Code tags are in the Advanced Editor here. Use the '#' key just like you would the bold or quote tags key.

It appears you do have a VPN running.  If the exit node for the VPN is in China, then having an IPTables rule which points to China make perfect sense.  If not, well ... a normal VPN would use routing to control where packets are sent, not IPtables.

NordVPN  [https://www.zdnet.com/article/meet-nordsec-the-company-behind-nordvpn-wants-to-be-your-one-stop-privacy-suite/](https://www.zdnet.com/article/meet-nordsec-the-company-behind-nordvpn-wants-to-be-your-one-stop-privacy-suite/)
I found it interesting reading for how many different countries can be involved in a fairly simple corporate organization requirement. Let's just say I have a little experience as a board member for an international company with multiple subsidiaries. Did that for about 4 yrs.

Regardless, if you think the problem is solved, great.  Please use the "Thread Tools" button near the top to mark it "solved" so others seeking solutions can find it.

---

### Post by zmsc12 on 2020-09-11
Thanks for that, and yes, I've looked further and found that my VPN can cause rules to be put in iptables. I've been using Linux for about 10 years and still find there are things I know nothing about!

---

