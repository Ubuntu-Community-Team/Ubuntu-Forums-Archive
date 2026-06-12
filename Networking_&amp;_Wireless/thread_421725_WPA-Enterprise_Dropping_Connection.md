---
title: "WPA-Enterprise Dropping Connection"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by nintendophile on 2007-04-24
Hi,
Sorry if this has been covered elsewhere, my search-fu is weak.

Basically I'm running Feisty and was pleasantly surprised when it allowed me to connect to my Uni network;
WPA-Enterprise
PEAP / MS-Chap-V2

Unfortunately the connection will drop every 5-10 minutes or even quicker. Then sometimes I cannot connect again.  My home connection works flawlessly (with WEP).

The messages log yields some information that's beyond me:

```
Apr 24 20:41:47 heisenberg kernel: [ 5867.176000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:42:05 heisenberg kernel: [ 5885.816000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:42:11 heisenberg dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Apr 24 20:42:11 heisenberg dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr 24 20:42:11 heisenberg dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr 24 20:50:10 heisenberg kernel: [ 6369.740000] ipw2200: Firmware error detected.  Restarting.
Apr 24 20:50:58 heisenberg kernel: [ 6418.228000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:50:59 heisenberg kernel: [ 6419.196000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:51:58 heisenberg kernel: [ 6478.396000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:51:59 heisenberg kernel: [ 6479.360000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:51:59 heisenberg kernel: [ 6479.776000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:52:00 heisenberg kernel: [ 6480.360000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:52:40 heisenberg kernel: [ 6520.388000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:52:41 heisenberg kernel: [ 6521.348000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:53:49 heisenberg kernel: [ 6589.108000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 24 20:55:48 heisenberg kernel: [ 6708.556000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 24 20:55:49 heisenberg kernel: [ 6709.568000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

This is an example of it dropping and then not letting me connect to any other networks, including the unsecured network which I never normally have a problem with.
```
sudo /etc/init.d/dbus restart
```
Lets me connect again, but only if I select the network from networkmanager and put in my credentials again. Then the above happens again

Some other information

```
tgrime@heisenberg:~$ lspci | grep Wireless
02:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```
```

tgrime@heisenberg:~$ dmesg | grep Wireless
[   23.324000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   23.332000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
```

I've no idea what to do

Thanks,
Tom

---

### Post by haywire on 2007-05-23
Hey tom did you ever find a solution for your problem 

im having the same issues w/ feisty i started a thread

[http://ubuntuforums.org/showthread.php?p=2708546#post2708546](http://ubuntuforums.org/showthread.php?p=2708546#post2708546)
and came across yours

---

