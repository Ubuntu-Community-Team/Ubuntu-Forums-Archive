---
title: "Creating a Wireless Network on wlan1 using eth0 for internet access"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by barr5790 on 2013-12-02
Hi guys,

I've a feeling I'm trying to do something stupid here. Basically I want to have linux running a wireless access point using wlan1 (which is a TP-WM722M), but with it getting internet access from eth0 (this is in a VM so this is NAT'd to a windows host WiFi connection...)

Why?
I am working with a WiFi embedded device, with development being done in the Linux VM. For early development I wish to use an unsecured network. In addition to this in the long run I envisage testing performance and battery useage when using wireless security as well as static IP addresses. So, I thought by creating an access point in Linux I can avoid having to constantly configure my home network / do some of the testing in University whose network I certainly wouldn't be able to reconfigure. In the future I may also have 2+ devices connecting.

So far...
I've been reading over various guides and my AP on wlan1 setup is: hostapd with udhcpd. This by itself seems to work OK when testing with my phone.
The problem is I'm not really sure on how to get access to the internet via eth0. I attempted bridging these two networks but I'm not quire sure that is the correct approach - when I try this is seems the bridge is giving my phone the IP address, not the udhcp client.

Diagram
I was hoping to do something like this:

```

device -- TL-WN722N --USB--**| **  -- wlan1 -- br0 -- eth0 --   **|** -- NAT-- **| **-- Networking -- **| -- **WiFi Network Adapter
         WiFi Hardware             **|  **VMWARE VM Lubuntu 12.04 **| **VMWare   **|**Windows 7 Host   **|**           WiFi Hardware

```



I've been looking a few guides, and I havn't seen anyone doing the exact same thing as me... I think part of the configuration problems is the fact its a VM, with the network the windows host is connected to is likely to change. 
Is what I am attempting possible? (in particular the bridging an interface which is an AP) / Can anyone provide me with some suggestions? I'll dump my current config files below, they've been changed that much I am not sure what guide/blog what came from :S

Cheers :)

```
# /etc/network/interfaces

auto lo
iface lo inet loopback


auto wlan1
iface wlan1 inet static
    address 10.0.0.1
    network 10.0.0.0
    netmask 255.255.255.0
    broadcast 10.0.0.255




allow-hotplug eth0
iface eth0 inet manual


auto br0
iface br0 inet dhcp
    bridge_ports eth0 wlan1



```

```

#/etc/hostapd/hostapd.conf
interface=wlan1
bridge=br0
driver=nl80211
ssid=FYP
hw_mode=g
channel=6
#auth_algs=1
#config for WPA security
#macaddr_acl=0
#ignore_broadcast_ssid=0
#wpa=2
#wpa_passphrase=MyPassphrase123
#wpa_key_mgmt=WPA-PSK
#wpa_pairwise=TKIP

```

```

#/etc/udhcpd.conf
# Sample udhcpd configuration file (/etc/udhcpd.conf)


# The start and end of the IP lease block


start   10.0.0.10       #default: 192.168.0.20
end     10.0.0.20       #default: 192.168.0.254




# The interface that udhcpd will use


interface    wlan1        #default: eth0




# The maximim number of leases (includes addressesd reserved
# by OFFER's, DECLINE's, and ARP conficts


#max_leases    254        #default: 254




# If remaining is true (default), udhcpd will store the time
# remaining for each lease in the udhcpd leases file. This is
# for embedded systems that cannot keep time between reboots.
# If you set remaining to no, the absolute time that the lease
# expires at will be stored in the dhcpd.leases file.


#remaining    yes        #default: yes




# The time period at which udhcpd will write out a dhcpd.leases
# file. If this is 0, udhcpd will never automatically write a
# lease file. (specified in seconds)


#auto_time    7200        #default: 7200 (2 hours)




# The amount of time that an IP will be reserved (leased) for if a
# DHCP decline message is received (seconds).


#decline_time    3600        #default: 3600 (1 hour)




# The amount of time that an IP will be reserved (leased) for if an
# ARP conflct occurs. (seconds


#conflict_time    3600        #default: 3600 (1 hour)




# How long an offered address is reserved (leased) in seconds


#offer_time    60        #default: 60 (1 minute)


# If a lease to be given is below this value, the full lease time is
# instead used (seconds).


#min_lease    60        #defult: 60




# The location of the leases file


#lease_file    /var/lib/misc/udhcpd.leases    #defualt: /var/lib/misc/udhcpd.leases


# The location of the pid file
#pidfile    /var/run/udhcpd.pid    #default: /var/run/udhcpd.pid


# Everytime udhcpd writes a leases file, the below script will be called.
# Useful for writing the lease file to flash every few hours.


#notify_file                #default: (no script)


#notify_file    dumpleases    # <--- useful for debugging


# The following are bootp specific options, setable by udhcpd.


#siaddr        192.168.0.22        #default: 0.0.0.0


#sname        zorak            #default: (none)


#boot_file    /var/nfs_root        #default: (none)


# The remainer of options are DHCP options and can be specifed with the
# keyword 'opt' or 'option'. If an option can take multiple items, such
# as the dns option, they can be listed on the same line, or multiple
# lines. The only option with a default is 'lease'.


#Examles
#opt    dns    192.168.10.2 192.168.10.10
option    subnet    255.255.255.0
opt    router    10.0.0.1
#opt    wins    192.168.10.10
option    dns    129.219.13.81    # appened to above DNS servers for a total of 3
option    domain    local
option    lease    864000        # 10 days of seconds




# Currently supported options, for more info, see options.c
#opt subnet
#opt timezone
#opt router
#opt timesrv
#opt namesrv
#opt dns
#opt logsrv
#opt cookiesrv
#opt lprsrv
#opt bootsize
#opt domain
#opt swapsrv
#opt rootpath
#opt ipttl
#opt mtu
#opt broadcast
#opt wins
#opt lease
#opt ntpsrv
#opt tftp
#opt bootfile
#opt wpad


# Static leases map
#static_lease 00:60:08:11:CE:4E 192.168.0.54
#static_lease 00:60:08:11:CE:3E 192.168.0.44



```


```
#Command Line:
~$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.000c29a24a55    no        eth0
                            wlan1


~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:0c:29:a2:4a:55  
          inet addr:192.168.254.128  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea2:4a55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:702435 (702.4 KB)  TX bytes:151296 (151.2 KB)


eth0      Link encap:Ethernet  HWaddr 00:0c:29:a2:4a:55  
          inet6 addr: fe80::20c:29ff:fea2:4a55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4752598 (4.7 MB)  TX bytes:556879 (556.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:576 (576.0 B)  TX bytes:576 (576.0 B)


mon.wlan1 Link encap:UNSPEC  HWaddr 64-66-B3-1F-4B-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31543051 (31.5 MB)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr 64:66:b3:1f:4b:44  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6666:b3ff:fe1f:4b44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404868 (404.8 KB)  TX bytes:4689991 (4.6 MB)




```

---

### Post by barr5790 on 2013-12-03
It seems a NAT setup between eth0 and wlan1 was what I was after, using the guide here [http://www.bctes.com/nat-linux-iptables.html](http://www.bctes.com/nat-linux-iptables.html)

---

