---
title: "Can't connect to any wireless network"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by unclejames on 2007-05-19
I run two wireless networks - one with WPA, and one which is open. I'm also running Ubuntu Feisty Fawn (latest updates).

Both networks appear in the Network Manager; FON_free_internet_access (the name of my open network) appears as open, but when trying to connect to it, my wireless card's lights flash a little, but not much else happens. (The Network Manager changes two two grey balls with a blue flash aimlessly circling them).

I'd like this wireless card to connect to my WPA system eventually, but even the open network would be a good start. What gives?

The relevant bits of iwconfig read:
```
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=87/100  Signal level=-51 dBm  Noise level:-208 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My /etc/network/interfaces reads:
```
auto lo
iface lo inet loopback

auto eth0

auto ra0
iface ra0 inet dhcp
```

I've read these forums, used Google, but am *so* confused with the different versions of Ubuntu and thus the different advice given, that I'm really, really confused. Stuff that might have worked on previous versions appears not to work on this, and my head hurts.

Can anyone point me to a really simple how-to that is **meant for Fawn**, so I can get this wireless card working again?

j

---

### Post by georgie on 2007-05-20
Hey James. I've got a fon network too (presume this is the new fonero, little white router with 2 ESSIDs) , so  this might be helpful. I'm, running stock feisty on x86

0) start a separate shell with #sudo tail -f /var/log/syslog

(watching this should give some feedback about the results below)

1) Try deleting everything in /etc/network/interfaces apart from
auto lo
iface lo inet loopback



2) # sudo /etc/init.d/dbus restart

3) # killall nm-applet

4) # nm-applet

You should then get some chatter, which will at least give some more info if the above doesn't work.

There's a chance nm-applet has got confused with some previous attempts - easiest way to test this is to create a new user and login as that, and then try connecting again.

George

---

### Post by unclejames on 2007-05-21
Neat trick with the separate terminal window.

That lot hasn't helped (I'll post the logfile once I've worked out how to get the USB key working!), bu I'll try creating a new user and seeing what happens there.

j

---

### Post by unclejames on 2007-05-21
The new user also exhibited exactly the same issues as above: a spinning network manager icon, and little else.

Here's the logfile from the original attempt:

```
May 21 10:13:10 localhost gconfd (root-5668): GConf server is not in use, shutting down.
May 21 10:13:10 localhost gconfd (root-5668): Exiting
May 21 10:13:16 localhost avahi-daemon[4685]: Got SIGTERM, quitting.
May 21 10:13:16 localhost NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
May 21 10:13:16 localhost NetworkManager: <information>^ICaught terminiation signal 
May 21 10:13:16 localhost NetworkManager: <debug info>^I[1179738796.194461] nm_print_open_socks (): Open Sockets List: 
May 21 10:13:16 localhost NetworkManager: <debug info>^I[1179738796.194506] nm_print_open_socks (): Open Sockets List Done. 
May 21 10:13:16 localhost NetworkManager: <information>^IDeactivating device ra0. 
May 21 10:13:16 localhost NetworkManager: <information>^IDeactivating device eth0. 
May 21 10:13:16 localhost hcid[4985]: Got disconnected from the system message bus
May 21 10:13:21 localhost dhclient: DHCPREQUEST on ra0 to 192.168.182.1 port 67
May 21 10:13:21 localhost dhclient: send_packet: Network is unreachable
May 21 10:13:21 localhost dhclient: send_packet: please consult README file regarding broadcast address.
May 21 10:13:24 localhost dhcdbd: Started up.
May 21 10:13:24 localhost NetworkManager: <information>^Istarting... 
May 21 10:13:25 localhost NetworkManager: <information>^Ira0: Device is fully-supported using driver 'rt2500'. 
May 21 10:13:25 localhost NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 21 10:13:25 localhost avahi-daemon[5949]: Found user 'avahi' (UID 107) and group 'avahi' (GID 113).
May 21 10:13:25 localhost avahi-daemon[5949]: Successfully dropped root privileges.
May 21 10:13:25 localhost avahi-daemon[5949]: avahi-daemon 0.6.17 starting up.
May 21 10:13:25 localhost avahi-daemon[5949]: Successfully called chroot().
May 21 10:13:25 localhost avahi-daemon[5949]: Successfully dropped remaining capabilities.
May 21 10:13:25 localhost avahi-daemon[5949]: No service found in /etc/avahi/services.
May 21 10:13:25 localhost avahi-daemon[5949]: Network interface enumeration completed.
May 21 10:13:25 localhost avahi-daemon[5949]: Registering HINFO record with values 'I686'/'LINUX'.
May 21 10:13:25 localhost avahi-daemon[5949]: Server startup complete. Host name is ubuntu-laptop.local. Local service cookie is 1819678454.
May 21 10:13:25 localhost NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 21 10:13:25 localhost NetworkManager: <information>^INow managing wireless (802.11) device 'ra0'. 
May 21 10:13:25 localhost NetworkManager: <information>^IDeactivating device ra0. 
May 21 10:13:25 localhost NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'e100'. 
May 21 10:13:25 localhost NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 21 10:13:25 localhost NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 21 10:13:25 localhost NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
May 21 10:13:25 localhost NetworkManager: <information>^IDeactivating device eth0. 
May 21 10:13:25 localhost NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 21 10:13:25 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 21 10:13:34 localhost dhclient: DHCPREQUEST on ra0 to 192.168.182.1 port 67
May 21 10:13:34 localhost dhclient: send_packet: Network is unreachable
May 21 10:13:34 localhost dhclient: send_packet: please consult README file regarding broadcast address.
May 21 10:13:48 localhost dhclient: DHCPREQUEST on ra0 to 192.168.182.1 port 67
May 21 10:13:48 localhost dhclient: send_packet: Network is unreachable
May 21 10:13:48 localhost dhclient: send_packet: please consult README file regarding broadcast address.
```

Typing 192.168.182.1 into the machine that works, results in the admin page for my wireless access point (La Fonera), so that bit clearly works.

Irritatingly, I did get this working once (about 7 days ago) but no idea how, and it's seemingly unrepeatable. So I know it works...

---

### Post by georgie on 2007-05-25
OK, it looks like there's some good news in those logs

'ra0: Device is fully-supported using driver 'rt2500'

So, the driver works OK. Now it's just userspace stuff.

I think there might be a conflict with your address ranges. The Fonero uses 192.168.182.* for its unsecured connection - perhaps your default settings ar 10.0.0.x or 192.168.1.x

(May 21 10:13:34 localhost dhclient: DHCPREQUEST on ra0 to 192.168.182.1 port 67
May 21 10:13:34 localhost dhclient: send_packet: Network is unreachable
May 21 10:13:34 localhost dhclient: send_packet: please consult README file regarding broadcast address.)


Can you do this


#ifconfig

and

#ifconfig -a

and

#route

and then post the results.

Suggestions

1) I suggest you try again without the wired connection plugged in (if it is plugged in- it looks like it)

Boot from cold without it.

2) Skip this and try the WPA interface. (your private one)

3) in the midst of network manager doing the blue swirly dot thing, do this 
#sudo /etc/init.d/networking restart
Let us know. If all else fails, bring it in to the BC at some point soon... :)

G

---

### Post by unclejames on 2007-05-26
No dice. After a cold reboot (with no wired connection):

```
james@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:9E:64:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:35:8A:10  
          inet6 addr: fe80::20e:2eff:fe35:8a10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:107960 (105.4 KiB)
          Interrupt:9 Base address:0xc000 

james@ubuntu-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:46:9E:64:F3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:35:8A:10  
          inet6 addr: fe80::20e:2eff:fe35:8a10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:135440 (132.2 KiB)
          Interrupt:9 Base address:0xc000 

james@ubuntu-laptop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
james@ubuntu-laptop:~$ 
```

---

### Post by unclejames on 2007-06-02
If anyone's interested:

I downloaded the Ubuntu Live disk, and booted off that. No dice. I therefore conclude that my setup isn't at fault, since the Ubuntu Live disk wouldn't work at all.

I dug out my old WG511 v1 card. This works correctly; but doesn't connect to WPA networks (complaining that it is not compatible or something).

So, this is posted from my trusty Ubuntu box, which is at least a start, even if I'm only connecting via my open FON network instead of the encrypted one.

---

