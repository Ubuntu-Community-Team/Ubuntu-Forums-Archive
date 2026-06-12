---
title: "NetworkManager fails to connect, but I can do it manually"
date: 2016-04-30
forum: Networking &amp; Wireless
---

### Post by denys-usynin on 2016-04-30
This almost certainly looks like a bug in NetworkManager to me. I installed Ubuntu 16.04 and at first it connected to my WiFi just fine. But next day NetworkManager suddenly disconnected and any attempt to reconnect failed after a few seconds. So I was thinking, maybe software updated pulled in a bad kernel driver, or perhaps it is some weird wifi issue, so I plugged my computer into ethernet port instead, and discovered that I am having exactly the same issue with ethernet interface.

syslog seems to indicate that connection fails when dhclient gets killed for some reason:
```

Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7535] device (enp2s0): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7537] manager: NetworkManager state is now DISCONNECTED
Apr 30 19:26:17 eggsnow NetworkManager[919]: <warn>  [1462040777.7541] device (enp2s0): Activation: failed for connection 'Wired connection 2'
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7550] device (enp2s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 30 19:26:17 eggsnow avahi-daemon[854]: Withdrawing address record for fe80::9829:8d7f:ac9:9374 on enp2s0.
Apr 30 19:26:17 eggsnow avahi-daemon[854]: Leaving mDNS multicast group on interface enp2s0.IPv6 with address fe80::9829:8d7f:ac9:9374.
Apr 30 19:26:17 eggsnow avahi-daemon[854]: Interface enp2s0.IPv6 no longer relevant for mDNS.
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7613] policy: auto-activating connection 'Wired connection 2'
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7645] device (enp2s0): Activation: starting connection 'Wired connection 2' (e7973309-a682-42c3-9503-d975c9a29722)
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7654] device (enp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7662] manager: NetworkManager state is now CONNECTING
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7676] device (enp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7690] device (enp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7694] dhcp4 (enp2s0): activation: beginning transaction (timeout in 45 seconds)
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7741] dhcp4 (enp2s0): dhclient started with pid 2740
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7776] dhcp4 (enp2s0): client pid 2740 killed by signal 15
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7780] dhcp4 (enp2s0): state changed unknown -> fail
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7783] dhcp4 (enp2s0): canceled DHCP transaction
Apr 30 19:26:17 eggsnow NetworkManager[919]: <info>  [1462040777.7784] dhcp4 (enp2s0): state changed fail -> done
Apr 30 19:26:17 eggsnow kernel: [ 1358.121594] audit: type=1400 audit(1462040777.770:40): apparmor="DENIED" operation="connect" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/var/run/NetworkManager/private-dhcp" pid=2741 comm="nm-dhcp-helper" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
Apr 30 19:26:18 eggsnow avahi-daemon[854]: Joining mDNS multicast group on interface enp2s0.IPv6 with address fe80::9829:8d7f:ac9:9374.
Apr 30 19:26:18 eggsnow avahi-daemon[854]: New relevant interface enp2s0.IPv6 for mDNS.
Apr 30 19:26:18 eggsnow avahi-daemon[854]: Registering new address record for fe80::9829:8d7f:ac9:9374 on enp2s0.*.

```

I then tried bringing network up from the command line by disabling NetworkManager and then using "ifconfig enp2s0 up" and "dhclient enp2s0" and that worked - I was able to connect to the network. So it seems that my system configuration got buggered somehow, even though I haven't touched any config files or installed any non-ubuntu packages.

I am looking for a community suggestion here - should I convert this into a bug report, or should I troubleshoot some more (but I cannot find any good troubleshooting guides for 16.04, and the ones I found for 14.04 seem obsolete, things have moved, etc).

---

### Post by T.J. on 2016-04-30
> **denys-usynin said:**
> This almost certainly looks like a bug in NetworkManager to me. 

I then tried bringing network up from the command line by disabling NetworkManager and then using "ifconfig enp2s0 up" and "dhclient enp2s0" and that worked - I was able to connect to the network. So it seems that my system configuration got buggered somehow, even though I haven't touched any config files or installed any non-ubuntu packages.

I am looking for a community suggestion here - should I convert this into a bug report, or should I troubleshoot some more (but I cannot find any good troubleshooting guides for 16.04, and the ones I found for 14.04 seem obsolete, things have moved, etc).


Honestly, I wouldn't bother.  Network-manager is maintained by the Gnome Project. They are not bad folks, but by reputation, they are generally considered hostile to outsiders.  That is, they respond with a blanket  "you aren't doing it right" when asking questions.  

If you have no need of a GUI for wireless, I suggest you simply purge it from the system or deactivate it, and setup the connection manually in /etc/network/interfaces.  (If you use software that is dependent on NM, such as apper - there is a  third option. You can set a manual interface and have NM activate it on  boot.  I won't post that unless you really want it.)


*sudo apt-get purge network-manager*

or 
[I]
sudo systemctl disable network-manager[/I]

Either way, you will want to reboot afterwards to clear any stale connections it tries to hold on to. Then you can configure the network interface manually.  It's very easy.  It's just one file in /etc/network/ named interfaces.



Example with a bridge for virtual machines (requires bridge-utils) using eth0:

```
 
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo br0
iface lo inet loopback
iface br0 inet dhcp
 bridge_ports eth0
 


```

In your case, it might look like:
```
 
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo enp2s0
iface lo inet loopback
iface enp2s0 inet dhcp


```

Setting the interface in this way is considerably more reliable than using NM, and you can* ifup *or* ifdown *it at any time as needed without rebooting.

You can accept "auto DNS" for DHCP or you can edit /etc/dhcp/dhclient.conf to set your specific nameservers (by IP address) with the prepend option. (Yes, once NM is gone, you can just use /etc/resolv.conf - but this is bit more classy)

Sample /etc/dhcp/dhclient.conf that uses prepend to add a localhost nameserver:

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
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

After you make your changes, just down and up the connection to force it to re-query the DHCP service:

[I]sudo ifdown enp2s0
sudo ifup enp2s0

(P.S. Please do not take offense, if the instructions seem "dumbed down" or patronising with your skills.  It's written that way for the sake of others who might need the thread someday.  I also apologise if this is redundant because you prefer wireless.  I never use wireless, so I can't offer specifics regarding it.  Hopefully this might provide a basic framework to assist you.)
[/I]

---

### Post by denys-usynin on 2016-05-02
Thanks TJ, that is a sensible and good suggestion, it is effectively what I ended up doing for now. I still would like to get NetworkManager working at some point, for convenience of switching wireless networks and connecting to VPN on the fly.

I have discovered that after I reboot, all I need to do is issue the following in the command line:
   "sudo dhclient enp2s0"
and that allows NetworkManager to acknowledge "connection established". That confirms that the failing step is the dhclient invocation. I am going to look around for some pointers on how to make NetworkManager run dhclient in a more verbose mode.

---

### Post by Bucky Ball on 2016-05-02
```
sudo apt update
sudo apt full-upgrade
```

Reboot. Still a problem with Network Manager?

Removing network manager, etc. etc. is an option, not a good one. Network Manager is working absolutely fine for 99% of users in 16.04 LTS so rather than 'ignore it and the problem will go away' and uninstall it would be better to attempt to get to the bottom of why you specifically are having issues. 

Found anyone else that's having this issue? Then it's not a bug, it's down to your particular setup, hardware or software, and it's a matter of finding out what. Anything else is a kludge (unless, of course, you'd prefer to configure and control your network and settings via a terminal that is and avoid the fact your Network Manager, for some reason, has issues, in which case, if something else network-related breaks in future you won't be surprised and will know exactly where to start digging).

---

