---
title: "Connected but no Internet - no IPv6 routers present"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by on~namas~ganga on 2006-09-28
Hi there All,

I am trying to connect to a wireless network with my almost brand new installation Ubuntu Dapper 6.06. Everything looks fine with the configuration but at this point don't know what is happening.

Here comes my message to you part by part to let you see at which point I am:


```
root@ganga:/home/daniel# lshw -C network

  *-network:0 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5901 100Base-TX
... ... ...
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 01
       serial: 00:20:e0:97:d0:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.7.2 ip=192.168.1.15 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:f8000000-f8000fff irq:11


root@ganga:/home/daniel# lspci | grep chipset
0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```

and what if? 

```
root@ganga: /home/daniel# iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:02:6F:37:41:A0
                    ESSID:"TrAir7"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:18/153  Noise level:9/153
                    Encryption key:off
                    Bit Rates:11 Mb/s

Seems that its detected and with a driver that seems to work, let's see what it does if...


root@ganga:/home/daniel# iwevent
Waiting for Wireless Events from interfaces...
19:00:31.443404   eth1     Scan request completed
19:09:10.170370   eth1     New Access Point/Cell address:00:02:6F:37:41:A0
19:09:10.185915   eth1     Tx packet dropped:00:02:6F:37:41:A0
19:09:11.111384   eth1     Tx packet dropped:00:02:6F:37:41:A0
```Yes, I see a network around me, access point available, let's connect to it : 

```
root@ganga:/etc# iwconfig eth1 essid TrAir7
root@ganga:/etc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"TrAir7"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:37:41:A0
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=24/92  Signal level=143/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:0   Missed beacon:0
```
Oh oh, there is not IP, so...

root@ganga:/home/daniel# ifconfig eth1 192.168.1.15 netmask 255.255.255.0

and then :

```
root@ganga:/home/daniel# ifconfig eth1 down

root@ganga:/home/daniel# ifconfig eth1 up 

dmesg | tail  

[17180255.504000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180255.808000] eth1: New link status: Connected (0001)
[17180255.808000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180266.744000] eth1: no IPv6 routers present
[17181079.192000] eth1: New link status: AP Out of Range (0004)
[17181141.748000] eth1: New link status: AP In Range (0005)
[17181594.116000] NET: Registered protocol family 17
[17181756.452000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181804.648000] eth1: New link status: Association Failed (0006)
[17181809.864000] eth1: New link status: Connected (0001)
[17181809.864000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17181820.836000] eth1: no IPv6 routers present
```Hey , ONE moment “ link becomes ready” oh yes mamacita... it sounds like something, lets ping :

ping 127.0.0.1 ok
ping 192.168.1.15 ok

but : 

```
root@ganga:/home/daniel# cat /etc/resolv.conf
search tricor.com.br
nameserver 200.195.53.131
nameserver 200.195.53.132
```

```
root@ganga:/home/daniel# ping 200.195.53.131
connect: Network is unreachable
root@ganga:/etc# ping 255.255.255.0
connect: Network is unreachable

root@ganga:/etc# ping 255.255.255.0
connect: Network is unreachable

root@ganga:/etc# ping www.onlinesuicides.com
ping: unknown host www.onlinesuicides.com
```
I also tried: 

```
daniel@ganga:/etc$ sudo dhclient eth1
Listening on LPF/eth1/00:20:e0:97:d0:40
Sending on   LPF/eth1/00:20:e0:97:d0:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3... 3... 8.. 12.. 20.. ..
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```


```
daniel@ganga:/etc$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:20:E0:97:D0:40
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:e0ff:fe97:d040/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38552 (37.6 KiB)  TX bytes:1584 (1.5 KiB)
          Interrupt:11 Memory:f8000000-f8000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
```

I now I am close, I don't surrender,  possibly I am doing something wrong, I am relatively new in this things, I love it, I love you all for reading this and trying to help me and to help the many people that are in the exact same point where I am... so then ... the winner of the vacuum cleaner is....

---

### Post by nekator on 2007-06-02
Dude you are one optimistic puppy...You haven't even gotten a reply to your post and are allready prancing around? Gotta love your willingness to fight...I've been baffled with a damn problem for far to long...off to sleep. Best

---

