---
title: "NetworkManager &amp; Firestarter internet sharing"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Baji on 2007-03-28
I've been at this quite a while and I hope someone can shed some light at this issue:

I use firestarter to share a wired internet connection (eth1) through eth0 to my network.

Now NetworkManager has come and he doesnt fully agree on what I'm doing.

Firstly Firestarter doesnt start automatically because NetworkManager seems to disable (?) the interfaces first.

Second NetworkManager doesnt let the two interfaces be active at the same time (?) so firstarter allways spits an error out one of them isnt ready, whichever I try to deactivate/active.

uname -a
```
Linux flyingdutchman 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

```

firstarter 1.0.3-1.3ubuntu2
network-manager 0.6.4-6ubuntu3

cat /var/log/syslog | grep NetworkManager
```
Mar 28 08:47:51 flyingdutchman avahi-daemon[10467]: Network interface enumeration completed.
Mar 28 09:01:50 flyingdutchman NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth1 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^ISWITCH: found better connection 'eth0' than current connection 'eth1'. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IWill activate connection 'eth0'. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IDevice eth0 activation scheduled... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IDeactivating device eth1. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) started... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IOld device 'eth0' activating, won't change. 
Mar 28 09:02:00 flyingdutchman NetworkManager: <information>^IOld device 'eth0' activating, won't change. 
Mar 28 09:02:01 flyingdutchman NetworkManager: <information>^IClearing nscd hosts cache. 
Mar 28 09:02:01 flyingdutchman NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 28 09:02:01 flyingdutchman NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Mar 28 09:02:01 flyingdutchman NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Mar 28 09:02:01 flyingdutchman NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 28 09:07:37 flyingdutchman NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Mar 28 09:07:37 flyingdutchman NetworkManager: <information>^ICaught terminiation signal 
Mar 28 09:07:37 flyingdutchman NetworkManager: <debug info>^I[1175065657.696896] nm_print_open_socks (): Open Sockets List: 
Mar 28 09:07:37 flyingdutchman NetworkManager: <debug info>^I[1175065657.696962] nm_print_open_socks (): Open Sockets List Done. 
Mar 28 09:07:37 flyingdutchman NetworkManager: <information>^IDeactivating device eth1. 
Mar 28 09:07:37 flyingdutchman NetworkManager: <information>^IDeactivating device eth0. 
Mar 28 09:09:54 flyingdutchman dhclient: send_packet: Network is unreachable
Mar 28 09:10:34 flyingdutchman ntpdate[11542]: sendto(82.211.81.145): Network is unreachable
Mar 28 09:10:35 flyingdutchman ntpdate[11542]: sendto(82.211.81.145): Network is unreachable

```

as a temporary solution I disabled NetworkManager

System->Preferences->Sessions (Untick NetworkManager)

and

```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

and create two files only with "exit" in it

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

cat /etc/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0


iface eth1 inet dhcp


auto eth1

auto eth0

```

anyone can point me out how this has come to be?

---

### Post by spd106 on 2007-03-28
The current version of Network Manager will only allow one network interface to be up at any one time, it does this mainly to avoid routing collisions. So you must manage one of the interfaces through network-admin or the interfaces file. 

You should be safe to remove eth1 from the interfaces file and allow Network Manger to have control of it, but leave eth0 as it is. Though that may not be neccessary as the main advantage to using Network Manager is the ability to roam easily, of which only laptops really take advantage.

---

### Post by Baji on 2007-03-28
Thank you for your reply. So this is intented behaviour for NetworkManager? That would make it quite impossible for the average use to share internet, shouldn't there be a more user-friendly way to disable it?

furthermore I've also seen network-manager preventing the firewall from starting it's daemon at boot time, without any explicit notice of it, except through /etc/init.d/firestarter status, this shouldn't happen, should it?

referring to bug 42759

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759]("https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759")

---

