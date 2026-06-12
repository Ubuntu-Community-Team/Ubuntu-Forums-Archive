---
title: "major DHCP problems, please help"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2008-05-19
I have major problems connecting to most WLAN's - regardless of encryption.
The DHCP client just does not do it's job.

>               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:de:59:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g




I cannot conect to my job's network, nor to it's guest network.
It seems I can't get IP address, and it attempts to fallback to 192.168.1.x (that only works on my home network - and might be the reason I can use it at home)

I also attach the syslog, that displays unsuccessful attempts to connect to both job-networks.  Strange thing's is going on there.

Connection at home works, but I think it's only luck, as Ubuntu seems to try my last home-DHCP address everywhere, and it works at home.., and only at home.

>  lsmod | grep iwl
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211


please see attached log:

I also tried to disable network manager according to [URL="https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5"]https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5
[/URL]
it did not help.
But here's the result that sums up it all:
> 
May 19 09:22:48 Ubuntu kernel: [  140.711738] wlan0: Initial auth_alg=0
May 19 09:22:48 Ubuntu kernel: [  140.711754] wlan0: authenticate with AP 00:17:0f:81:c0:4c
May 19 09:22:48 Ubuntu kernel: [  140.712413] wlan0: RX authentication from 00:17:0f:81:c0:4c (alg=0 transaction=2 status=0)
May 19 09:22:48 Ubuntu kernel: [  140.712419] wlan0: authenticated
May 19 09:22:48 Ubuntu kernel: [  140.712423] wlan0: associate with AP 00:17:0f:81:c0:4c
May 19 09:22:48 Ubuntu kernel: [  140.713477] wlan0: RX ReassocResp from 00:17:0f:81:c0:4c (capab=0x1 status=17 aid=0)
May 19 09:22:48 Ubuntu kernel: [  140.713485] wlan0: AP denied association (code=17)
May 19 09:22:48 Ubuntu kernel: [  140.742260] wlan0: associate with AP 00:17:0f:81:c0:4c
May 19 09:22:48 Ubuntu kernel: [  140.743101] wlan0: RX ReassocResp from 00:17:0f:81:c0:4c (capab=0x1 status=0 aid=2)
May 19 09:22:48 Ubuntu kernel: [  140.743109] wlan0: associated
May 19 09:22:51 Ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 19 09:22:51 Ubuntu dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 19 09:22:51 Ubuntu dhclient: All rights reserved.
May 19 09:22:51 Ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 19 09:22:51 Ubuntu dhclient: 
May 19 09:22:51 Ubuntu dhclient: wmaster0: unknown hardware address type 801
May 19 09:22:51 Ubuntu avahi-autoipd(wlan0)[6083]: Got SIGTERM, quitting.
May 19 09:22:51 Ubuntu avahi-autoipd(wlan0)[6083]: Callout STOP, address 169.254.9.47 on interface wlan0
May 19 09:22:51 Ubuntu avahi-daemon[5070]: Withdrawing address record for 169.254.9.47 on wlan0.
May 19 09:22:51 Ubuntu avahi-daemon[5070]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.47.
May 19 09:22:51 Ubuntu avahi-daemon[5070]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 19 09:22:51 Ubuntu avahi-autoipd(wlan0)[6084]: client: RTNETLINK answers: No such process
May 19 09:22:52 Ubuntu dhclient: wmaster0: unknown hardware address type 801
May 19 09:22:52 Ubuntu dhclient: Listening on LPF/wlan0/00:18:de:de:59:ac
May 19 09:22:52 Ubuntu dhclient: Sending on   LPF/wlan0/00:18:de:de:59:ac
May 19 09:22:52 Ubuntu dhclient: Sending on   Socket/fallback
May 19 09:22:52 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May 19 09:22:57 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May 19 09:23:07 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May 19 09:23:20 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May 19 09:23:23 Ubuntu dhclient: No DHCPOFFERS received.
May 19 09:23:23 Ubuntu dhclient: No working leases in persistent database - sleeping.
May 19 09:23:23 Ubuntu avahi-autoipd(wlan0)[6339]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
May 19 09:23:23 Ubuntu avahi-autoipd(wlan0)[6339]: Successfully called chroot().
May 19 09:23:23 Ubuntu avahi-autoipd(wlan0)[6339]: Successfully dropped root privileges.
May 19 09:23:23 Ubuntu avahi-autoipd(wlan0)[6339]: Starting with address 169.254.9.47
May 19 09:23:27 Ubuntu avahi-autoipd(wlan0)[6339]: Callout BIND, address 169.254.9.47 on interface wlan0
May 19 09:23:27 Ubuntu avahi-daemon[5070]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.47.
May 19 09:23:27 Ubuntu avahi-daemon[5070]: New relevant interface wlan0.IPv4 for mDNS.
May 19 09:23:27 Ubuntu avahi-daemon[5070]: Registering new address record for 169.254.9.47 on wlan0.IPv4.
May 19 09:23:31 Ubuntu avahi-autoipd(wlan0)[6339]: Successfully claimed IP address 169.254.9.47
May 19 09:24:34 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May 19 09:24:39 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May 19 09:24:48 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May 19 09:24:57 Ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May 19 09:25:05 Ubuntu dhclient: No DHCPOFFERS received.
May 19 09:25:05 Ubuntu dhclient: Trying recorded lease 192.168.1.5
May 19 09:25:05 Ubuntu avahi-autoipd(wlan0)[6339]: A routable address has been configured.
May 19 09:25:05 Ubuntu avahi-autoipd(wlan0)[6339]: Callout UNBIND, address 169.254.9.47 on interface wlan0
May 19 09:25:05 Ubuntu avahi-daemon[5070]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.47.
May 19 09:25:05 Ubuntu avahi-daemon[5070]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.5.
May 19 09:25:05 Ubuntu avahi-daemon[5070]: Registering new address record for 192.168.1.5 on wlan0.IPv4.
May 19 09:25:05 Ubuntu avahi-daemon[5070]: Withdrawing address record for 169.254.9.47 on wlan0.
May 19 09:25:08 Ubuntu avahi-autoipd(wlan0)[6339]: No longer a routable address configured, restarting probe process.
May 19 09:25:08 Ubuntu avahi-daemon[5070]: Withdrawing address record for 192.168.1.5 on wlan0.
May 19 09:25:08 Ubuntu avahi-daemon[5070]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.5.
May 19 09:25:08 Ubuntu avahi-daemon[5070]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 19 09:25:08 Ubuntu dhclient: No working leases in persistent database - sleeping.
May 19 09:25:13 Ubuntu avahi-autoipd(wlan0)[6339]: Callout BIND, address 169.254.9.47 on interface wlan0
May 19 09:25:13 Ubuntu avahi-daemon[5070]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.47.
May 19 09:25:13 Ubuntu avahi-daemon[5070]: New relevant interface wlan0.IPv4 for mDNS.
May 19 09:25:13 Ubuntu avahi-daemon[5070]: Registering new address record for 169.254.9.47 on wlan0.IPv4.
May 19 09:25:17 Ubuntu avahi-autoipd(wlan0)[6339]: Successfully claimed IP address 169.254.9.47


$dhclient eth0 works pefectly (on eth0)

here's some extra info:

> eth0      Link encap:Ethernet  HWaddr 00:16:d4:b2:35:fd  
          inet addr:172.16.12.203  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::216:d4ff:feb2:35fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4202058 (4.0 MB)  TX bytes:426442 (416.4 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:325690 (318.0 KB)  TX bytes:325690 (318.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:de:59:ac  
          inet6 addr: fe80::218:deff:fede:59ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:25240 (24.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:de:de:59:ac  
          inet addr:169.254.9.47  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-DE-59-AC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


please see attached log for more attempts to connect to two networks:

---

### Post by Andre-D on 2008-05-20
OOOPS ! - please disregard this message.
I just discovered that both out job-networks have huge problems, an this behavior, is also happening on windows !  -so do not hvink about this.

---

