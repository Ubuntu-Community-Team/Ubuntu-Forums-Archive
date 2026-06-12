---
title: "network keeps losing connection"
date: 2016-11-10
forum: Networking &amp; Wireless
---

### Post by jgw on 2016-11-10
Suddenly my system has lost the internet.  Sometimes it said it was connected but, every few minutes, it put up a notice that it had lost connection.  First I thought it was the vpn but I disabled that and still kept getting the lost connection thing.  Below I have included a bunch of stuff about this system and its network thing.  The network type is 'wired'.  I ttried some stuff but it did no good.  I tried to restart the network, it went down but cannot get back up.

Thank you...............

______________________________________________________________________________________________________________________________________________________________________

network manager conf file:
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=fc:aa:14:8c:6b:c7
[ifupdown]managed=true

greg@greg-movies:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr fc:aa:14:8c:6b:c7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:87200 (87.2 KB)

greg@greg-movies:~$ systemctl status NetworkManager.service
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor p
   Active: inactive (dead) (Result: exit-code) since Thu 2016-11-10 09:27:42 PST
  Process: 13398 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, st
 Main PID: 13398 (code=exited, status=1/FAILURE)
the System:
Memory    7.7 GiB
Processor amd a4-7300 apu with Radeon hd graphics x2
graphics  geforce gt 440/pcie/sse2
OS type   64-bit
disk      4.9 TB

Nov 10 09:27:42 greg-movies systemd[1]: NetworkManager.service: Service hold-off
Nov 10 09:27:42 greg-movies systemd[1]: Stopped Network Manager.
Nov 10 09:27:42 greg-movies systemd[1]: NetworkManager.service: Start request re
Nov 10 09:27:42 greg-movies systemd[1]: Failed to start Network Manager.

greg@greg-movies:~$ journalctl -xe
Nov 10 09:38:09 greg-movies gnome-session[1566]: net.ipv6.conf.all.disable_ipv6 
Nov 10 09:38:09 greg-movies gnome-session[1566]: net.ipv6.conf.default.disable_i
Nov 10 09:38:09 greg-movies gnome-session[1566]: net.ipv6.conf.lo.disable_ipv6 =
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:38:54 greg-movies org.gnome.Terminal[1425]: (gnome-terminal-server:161
Nov 10 09:39:09 greg-movies gnome-session[1566]: SIOCDELRT: No such process
Nov 10 09:39:09 greg-movies gnome-session[1566]: ip6tables: No chain/target/matc
Nov 10 09:39:09 greg-movies gnome-session[1566]: ip6tables: No chain/target/matc
Nov 10 09:39:09 greg-movies gnome-session[1566]: net.ipv6.conf.all.disable_ipv6 
Nov 10 09:39:09 greg-movies gnome-session[1566]: net.ipv6.conf.default.disable_i
Nov 10 09:39:09 greg-movies gnome-session[1566]: net.ipv6.conf.lo.disable_ipv6 =
Nov 10 09:39:09 greg-movies kernel: IPv6: ADDRCONF(NETDEV_UP): eth1: link is not
Nov 10 09:39:13 greg-movies gnome-session[1566]: ip6tables: No chain/target/matc
Nov 10 09:39:13 greg-movies gnome-session[1566]: ip6tables: No chain/target/matc
Nov 10 09:39:13 greg-movies gnome-session[1566]: ip6tables: No chain/target/matc
Nov 10 09:39:13 greg-movies gnome-session[1566]: net.ipv6.conf.all.disable_ipv6 
Nov 10 09:39:13 greg-movies gnome-session[1566]: net.ipv6.conf.default.disable_i
Nov 10 09:39:13 greg-movies gnome-session[1566]: net.ipv6.conf.lo.disable_ipv6 =

reg@greg-movies:~$ lspci -km | grep Eth -A2
02:00.0 "Ethernet controller" "Realtek Semiconductor Co., Ltd." "RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller" -r0c "Gigabyte Technology Co., Ltd" "Motherboard"

Nov 10 09:38:09 greg-movies gnome-session[1566]: net.ipv6.conf.all.disable_ipv6 
Nov 10 09:38:09 greg-movies gnome-session[1566]: net.ipv6.conf.default.disable_i

---

### Post by chili555 on 2016-11-10
Ahhh! The notorious r8169 device. Let's try a quick and not so dirty fix. ```
gksudo gedit /etc/rc.local
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Add a new line above exit 0:```
ethtool -s eth1 speed 100 autoneg off
```Proofread carefully, save and close the text editor.

Reboot and test.

---

### Post by jgw on 2016-11-10
Thank you for the reply!

Did as you suggested.  Network failed.  Here are the results.  The first lines are the /etc/rc.local file.  The rest are the results of sudo service network-manager start

I also checked the permissions on this file and its set "allow executing file as program" is checked.
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ethtool -s eth1 speed 100 autoneg off

exit 0


greg@greg-movies:~$ sudo service network-manager start
[sudo] password for greg: 
Job for NetworkManager.service failed because the control process exited with error code. See "systemctl status NetworkManager.service" and "journalctl -xe" for details.
greg@greg-movies:~$ systemctl status NetworkManager.service
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor p
   Active: inactive (dead) (Result: exit-code) since Thu 2016-11-10 16:09:54 PST
  Process: 7007 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, sta
 Main PID: 7007 (code=exited, status=1/FAILURE)

Nov 10 16:09:54 greg-movies systemd[1]: NetworkManager.service: Failed with resu
Nov 10 16:09:54 greg-movies systemd[1]: NetworkManager.service: Service hold-off
Nov 10 16:09:54 greg-movies systemd[1]: Stopped Network Manager.
Nov 10 16:09:54 greg-movies systemd[1]: NetworkManager.service: Start request re
Nov 10 16:09:54 greg-movies systemd[1]: Failed to start Network Manager.
lines 1-11/11 (END)
greg@greg-movies:~$ journalctl -xe
-- Unit NetworkManager.service has finished shutting down.
Nov 10 16:09:54 greg-movies systemd[1]: NetworkManager.service: Start request re
Nov 10 16:09:54 greg-movies systemd[1]: Failed to start Network Manager.
-- Subject: Unit NetworkManager.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit NetworkManager.service has failed.
-- 
-- The result is failed.
Nov 10 16:10:31 greg-movies gnome-session[4351]: SIOCDELRT: No such process
Nov 10 16:10:31 greg-movies gnome-session[4351]: ip6tables: No chain/target/matc
Nov 10 16:10:31 greg-movies gnome-session[4351]: ip6tables: No chain/target/matc
Nov 10 16:10:31 greg-movies gnome-session[4351]: net.ipv6.conf.all.disable_ipv6 
Nov 10 16:10:31 greg-movies kernel: IPv6: ADDRCONF(NETDEV_UP): eth1: link is not
Nov 10 16:10:31 greg-movies gnome-session[4351]: net.ipv6.conf.default.disable_i
Nov 10 16:10:31 greg-movies gnome-session[4351]: net.ipv6.conf.lo.disable_ipv6 =
Nov 10 16:10:42 greg-movies gnome-session[4351]: ip6tables: No chain/target/matc
Nov 10 16:10:42 greg-movies gnome-session[4351]: ip6tables: No chain/target/matc
Nov 10 16:10:42 greg-movies gnome-session[4351]: ip6tables: No chain/target/matc
Nov 10 16:10:42 greg-movies gnome-session[4351]: net.ipv6.conf.all.disable_ipv6 
Nov 10 16:10:42 greg-movies gnome-session[4351]: net.ipv6.conf.default.disable_i
Nov 10 16:10:42 greg-movies gnome-session[4351]: net.ipv6.conf.lo.disable_ipv6 =
lines 1558-1580/1580 (END)

---

### Post by chili555 on 2016-11-10
Any further clues here?```
cat /var/log/syslog | grep etwork
```Since NM isn't running, can you at least get connected?```
sudo dhclient eth1
```If you can get connected, we'll probably recommend that you purge and then install a fresh copy of NM.

---

### Post by jgw on 2016-11-10
Thanks again.

before you start reading this I should tell you that, suddenly, my network start running again (with the vpn!)  I have no idea why, or how.  What makes it even more mysterious is that my network icon is no longer on the top bar.  Now I have to figure out how to get that back.  While its working now I don't think its exactly right - thoughts?

I have posted the results of your suggestions at [http://pastebin.com/VRS33k7h](http://pastebin.com/VRS33k7h)   (there was a LOT of stuff}  but I have included tghe results of the dhclient eth1 below.

greg@greg-movies:~$ sudo dhclient eth1
/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf

---

### Post by chili555 on 2016-11-10
Let's try to fix the resolv issue and maybe NM will then start as expected. In a terminal:```
sudo rm /etc/resolv.conf
sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
sudo resolvconf -u
```Reboot. Now does NM appear to be running; that is, is the usual applet icon happily present in the upper right?

Any interesting clues here?```
sudo service network-manager restart
```

---

### Post by jgw on 2016-11-12
thanks for the help.

I did the restart and I seem to be back to:
Job for NetworkManager.service failed because the control process exited with error code. See "systemctl status NetworkManager.service" and "journalctl -xe" for details.

There is no networkmanager on my desktop bar and its not running and I have no idea how I got it starting before
 dbus-launch nm-applet



oK - then I did: sudo dhclient eth1 and I have my network back (without the icon)  It takes it a bit of time but I looked up and there it was connected and my vpn (pia) icon appeared on the bar!  (exciting!!)

now all I need is to get my network icon back.

I rooted around a bit and tried "dbus=launch nm-applet"  I got:
6 warnings - theme parsing error: gtk.css.28:35:junk at the end of value
then: WARNING**: .1dNetworkingManager is not running

I thought that was pretty interesting.  I have my network (and vpn) up and running and I have access to the net.  Mysteries abound?? <G>
Again, it makes sense that there is no network manager icon as the network manager is not running!  

I left this machine for about an hour and, when I got back the network was down.  so I did the dhclient thing again and got:
sudo dhclient eth1
[sudo] password for greg: 
/etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf

and then the network came back.   I also then tried to run the network manager but got the same results.  

In between all of this I did a update of everything and re-booted.  The network didn't automatically start so I did the dhclient eth1 and got it back.

now all I need to know is to how to get the network manager back up and running!  I am seriously thinking of reinstalling the network manager.

I have tried some other stuff and didn't fix anything. 

I checked my ip for the heck of it:
greg@greg-movies:~$ sudo ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fc:aa:14:8c:6b:c7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.4/24 brd 192.168.0.255 scope global eth1
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 100
    link/none 
    inet 10.40.10.6 peer 10.40.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever

Then I reinstalled (and tried to start it with the same results):

sudo aptitude reinstall network-manager network-manager-gnome

then I did some other stuff  (check the ip for the heck of it and then I reinstalled the network manager - nothing helped):
greg@greg-movies:~$ sudo ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fc:aa:14:8c:6b:c7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.4/24 brd 192.168.0.255 scope global eth1
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 100
    link/none 
    inet 10.40.10.6 peer 10.40.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever

here is what I used to reinstall the network manager:
sudo aptitude reinstall network-manager network-manager-gnome

I also:
greg@greg-movies:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

I don't thing that one can rename a topic but this one has morphed into a network manager problem which seems a bit intractable.  Perhaps I should abandon this topic and start another?

Thank you................

---

### Post by jgw on 2016-11-16
After spending several days wasting my time and not paying attention I finally re-read everything and noted that chili555 told me to purge the network manager and reinstall.  This time, paying attention, I did as suggested and THAT saved the day and got me back up and running the network manager.  

thank you chili555 (reget it took me so long to actually pay attention and do what I was told to do several days ago <G>)

---

