---
title: "Prevent dhclient from adding default gateway on some devices"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by jono3 on 2014-02-26
I have a BeagleBoneBlack running:
```

ubuntu@ubuntu-armhf:~$ uname -a
Linux ubuntu-armhf 3.8.13-bone30 #1 SMP Thu Nov 14 06:23:24 UTC 2013 armv7l armv7l armv7l GNU/Linux

```

and I'm trying to use it to control a Sony Nex 5 camera or GoPro using their somewhat incomplete WiFi API to make a remotely triggered/viewable camera over the internet. The problem I have is that the cameras allocate ip addresses via DHCP, and it also sets a default gateway, which prevents me from using my LTE connection to reach outside addresses. 

How would I go about letting the the camera allocate an IP address, but preventing it from setting a default gateway? I've hacked around with /etc/dhcp/dhclient.conf but I can't seem to get the appropriate behaviour.

What I have so far is dhclient.conf for two devices. lte0 (the LTE connection, set using custom udev rules) and wlan0 (the camera connection), where I've removed all 'routers' and 'name-server' related items for wlan0:
```

ubuntu@ubuntu-armhf:~$ sudo cat /etc/dhcp/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#


option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;


#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
interface "lte0"
        {
        prepend domain-name-servers 8.8.8.8;
        request subnet-mask, broadcast-address, time-offset, routers,
                domain-name, domain-name-servers, domain-search, host-name,
                dhcp6.name-servers, dhcp6.domain-search,
                netbios-name-servers, netbios-scope, interface-mtu,
                rfc3442-classless-static-routes, ntp-servers,
                dhcp6.fqdn, dhcp6.sntp-servers;
        require routers, domain-name, domain-name-servers, domain-search;
        }


interface "wlan0"
        {
        request subnet-mask, broadcast-address, time-offset, host-name
                netbios-name-servers, netbios-scope, interface-mtu,
                rfc3442-classless-static-routes, ntp-servers,
                dhcp6.fqdn, dhcp6.sntp-servers;
        }


#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;


#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}


#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

My /etc/network/interfaces is as follows (I have auto wlan0 off as it kills my LTE):
```

ubuntu@ubuntu-armhf:~$ sudo cat /etc/network/interfaces
auto lo
auto eth0
# auto wlan0
auto lte0


iface lo inet loopback


# This is to set up the ethernet address.
iface eth0 inet static
    netmask 255.255.255.0
    address 192.168.2.14


# This is the LTE connection using the Pantech 295 dongle.
allow-hotplug lte0
iface lte0 inet dhcp


# These settings are for WiFi.
allow-hotplug wlan0
iface wlan0 inet manual
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp

```

State of the system before sudo ifup wlan0:
```

ubuntu@ubuntu-armhf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:59:af:50:f6:33  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::9259:afff:fe50:f633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21810 (21.8 KB)  TX bytes:6075 (6.0 KB)
          Interrupt:56 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86323 (86.3 KB)  TX bytes:86323 (86.3 KB)


lte0      Link encap:Ethernet  HWaddr d0:57:85:f8:2c:61  
          inet addr:192.168.32.50  Bcast:192.168.32.255  Mask:255.255.255.0
          inet6 addr: 2600:1010:b002:2da2:d257:85ff:fef8:2c61/64 Scope:Global
          inet6 addr: fe80::d257:85ff:fef8:2c61/64 Scope:Link
          inet6 addr: 2600:1010:b002:2da2:482c:4f7a:70c5:3578/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1428  Metric:1
          RX packets:2906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:435463 (435.4 KB)  TX bytes:679989 (679.9 KB)


ubuntu@ubuntu-armhf:~$ ping www.google.com
PING www.google.com (209.118.208.44) 56(84) bytes of data.
64 bytes from 209.118.208.44: icmp_seq=1 ttl=50 time=44.1 ms
64 bytes from 209.118.208.44: icmp_seq=2 ttl=50 time=45.9 ms
64 bytes from 209.118.208.44: icmp_seq=3 ttl=50 time=42.5 ms
^C
--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 42.599/44.230/45.900/1.347 ms
ubuntu@ubuntu-armhf:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.32.2    0.0.0.0         UG    0      0        0 lte0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.32.0    0.0.0.0         255.255.255.0   U     0      0        0 lte0

```

And this is after:
```

ubuntu@ubuntu-armhf:~$ sudo ifup wlan0
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWESSID]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ubuntu@ubuntu-armhf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:59:af:50:f6:33  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::9259:afff:fe50:f633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66997 (66.9 KB)  TX bytes:50851 (50.8 KB)
          Interrupt:56 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132060 (132.0 KB)  TX bytes:132060 (132.0 KB)


lte0      Link encap:Ethernet  HWaddr d0:57:85:f8:2c:61  
          inet6 addr: 2600:1010:b002:2da2:d257:85ff:fef8:2c61/64 Scope:Global
          inet6 addr: fe80::d257:85ff:fef8:2c61/64 Scope:Link
          inet6 addr: 2600:1010:b002:2da2:482c:4f7a:70c5:3578/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1428  Metric:1
          RX packets:4295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:645307 (645.3 KB)  TX bytes:1013043 (1.0 MB)


wlan0     Link encap:Ethernet  HWaddr 80:1f:02:bf:05:5d  
          inet addr:10.5.5.104  Bcast:10.5.5.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:febf:55d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:5 overruns:0 frame:0
          TX packets:7 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1154 (1.1 KB)  TX bytes:1346 (1.3 KB)


ubuntu@ubuntu-armhf:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"JONO-GOPRO"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: D4:D9:19:02:6C:99   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


lte0      no wireless extensions.


eth0      no wireless extensions.


ubuntu@ubuntu-armhf:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.5.5.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
ubuntu@ubuntu-armhf:~$ ping www.google.com
ping: unknown host www.google.com

```
Note the introduction of the wlan0 interface and the disappearance of the lte0 interface.

Any help would be greatly appreciated.

Best,
J

---

### Post by chili555 on 2014-02-27
This has fallen to page three with no reply, so I'll try to help, although I'm not too sure I know much to add. I know a tiny bit about GoPro and a tiny bit about networking. Just enough to be a danger to myself!

It seems to me that you want the wlan0 interface to talk to the GoPro on its network and gateway and lte1 to talk to the internet on its network and gateway; no? Then you need to bridge the interfaces so that data coming in from wlan0 can go out on lte1. This may be helpful: [https://wiki.debian.org/BridgeNetworkConnections](https://wiki.debian.org/BridgeNetworkConnections)> Bridging your network connection is a handy method for sharing your internet connection between two (or more) computers. It&#8217;s useful if you can&#8217;t buy a router with more than one ethernet port, or if you&#8217;re a college student in a dorm room with limited ethernet jacks and no router. It seems to me that you are sharing the outgoing GoPro stream with all your friends instead of sharing the incoming internet.

I see a few problems in your setup. First, I have no idea what this is supposed to do:> iface default inet dhcpDid that come from a tutorial somewhere?> iface wlan0 inet manualI believe it is static, not manual. I think you want DHCP. Last, in any wireless declaration, you must specify the access point and WPA password. Here is my sample *interfaces* when I connect, err, torture my GoPro:```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid GOPRO-BP-D896XXXCFYYY
wpa-psk goprohero
```That's it! That's all I know. I'm outa talent.

---

### Post by jono3 on 2014-02-27
Thanks for trying :)

I'll give the briding a go.

The manual config of wlan0 is to enable wpa-supplicant (roaming wifi for non WEP based connections). The 'iface default inet dhcp' allows the resulting wpa-supplicant configured device to DHCP. One can tag associated wifi networks with names, and handle them differently this way (tried fiddling with the gopro stuff, but IPs were allocated manually).

One possible solution I might try along these lines would be to have a WPA supplicant entry defined like this:
```

network={
        ssid="GOPRO"
        psk="some_password"
        priority=5
        id_str="gopro"
}

```

and then at the bottom of /etc/network/interfaces have:

```

iface gopro inet static
    netmask 255.255.255.0
    address 10.5.5.15

```

The way I actually ended up solving it was adding an entry hook in:
```

ubuntu@ubuntu-armhf:~$ cat /etc/dhcp/dhclient-enter-hooks.d/no_default_route 
#!/bin/sh


# prevent dhclient-script from setting default route every time it gets
# a new dhcpoffer for any interface.




INTERFACE_DEFAULT_ROUTE="lte0"


DEBUG_FILE="/tmp/dhclient-nodefroute.debug"


echo "Interface ${interface} entered DHCP because of $reason." >> $DEBUG_FILE


case "$reason" in
    BOUND|RENEW|REBIND|REBOOT|TIMEOUT)


	echo "New DHCP connection because of $reason." >> $DEBUG_FILE


	echo "dhcp for interface ${interface}" >> $DEBUG_FILE


	if [ ${interface} != $INTERFACE_DEFAULT_ROUTE ]; then
	    echo "interface ${interface} doesn't match ${INTERFACE_DEFAULT_ROUTE}, not setting default route." >> $DEBUG_FILE
	    unset new_routers
	else
	    echo "default route for ${interface}" >> $DEBUG_FILE
	fi


      ;;
esac

```

---

