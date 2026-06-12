---
title: "ethernet problem -detected but not working"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by help_help on 2006-09-17
I installed Ubuntu 6.06 yesterday . I have an AMD 64 bit processor and am a new Linux user. When I go to the nework options, it says ethernet 0 is detected. I use DHCP. I am also behind a firewall. however , I am unable to acces the net(which i can do from windows). When I went to etc/network/interfaces
it showed the foll o/p

auto lo
iface lo net loop back
auto eth0
iface net loop back
auto eth1
iface  net loop back
auto eth2
iface  net loop back
auto ath0
iface net loop back
auto wlan  0
iface net loop back

I know my ip address,subnet mask , gateway(from windows) but dont know  how and where to put it in linux.

---

### Post by catlett on 2006-09-17
All you should have to do is, go to the top panel and enter into System<Administration<Networking. That will bring up a window for your interfaces. It should show an ethernet connection. Select it and then select 'activate'. That should be it but if it doesn't show activate but it does show properties, select properties and check off 'enable this connection'.
What happens when you try that? Does it activate or do you get an error?

---

### Post by help_help on 2006-09-18
i tried what you said but when i opened it, it said ethernet card was active. Deactivated and activated it, didnt work. Went to properties, unticked the enable option, didnt work and then ticked and activated it again, didnt work.

---

### Post by Jimmy_r on 2006-09-18
What happens if you go to the console and write ```
sudo dhclient
```

---

### Post by help_help on 2006-09-18
these are the o/pfor various commands
_/etc/network/interfaces_
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0


_if config_
eth0      Link encap:Ethernet  HWaddr 00:14:85:CE:D1:B9
          inet6 addr: fe80::214:85ff:fece:d1b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32373734 (30.8 MiB)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6384 (6.2 KiB)  TX bytes:6384 (6.2 KiB)
_sudo dhclient_
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:ce:d1:b9
Sending on   LPF/eth0/00:14:85:ce:d1:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

My subnet is 255.255.0.0
Gateway is 10.94.0.254

---

### Post by Jimmy_r on 2006-09-18
```
Listening on LPF/eth0/00:14:85:ce:d1:b9
Sending on LPF/eth0/00:14:85:ce:d1:b9
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Hm, have you booted into another operating system recently?
I have had this problem when i have done so.

It has been solved by "simply" shutting down the computer 10-20 minutes and then booting straight into ubuntu.

What if you go to System > Administration > Networking , select your network connection, go to properties. Under configuration, choose Static IP address instead of DHCP and then fill in your IP, subnet and gateway?

---

### Post by help_help on 2006-09-18
Nopes, I met with no luck.these were the corrseponding o/p s in static and then dhcp.
under static:
eth0      Link encap:Ethernet  HWaddr 00:14:85:CE:D1:B9
          inet addr:10.94.9.195  Bcast:10.94.255.255  Mask:255.255.0.0
          inet6 addr: fe80::214:85ff:fece:d1b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2306037 (2.1 MiB)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6484 (6.3 KiB)  TX bytes:6484 (6.3 KiB)

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 10.94.9.195
netmask 255.255.0.0
gateway 10.94.0.254

auto eth0

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:ce:d1:b9
Sending on   LPF/eth0/00:14:85:ce:d1:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---under dhcp 

eth0      Link encap:Ethernet  HWaddr 00:14:85:CE:D1:B9
          inet6 addr: fe80::214:85ff:fece:d1b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:266297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:15 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18164107 (17.3 MiB)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15260 (14.9 KiB)  TX bytes:15260 (14.9 KiB)



Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:ce:d1:b9
Sending on   LPF/eth0/00:14:85:ce:d1:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

---

### Post by Original Brownster on 2006-09-18
Hi,
can you post the output of 
$ route

and 

$ifconfig -a

and

$ less /var/log/syslog | grep eth0

and confirm the full contents of your /etc/network/interfaces file

You have a lot of network interfaces listed, eth0,eth1,eth2 etc in your /etc/network/interfaces file, all set to 'auto' to activate at boot, are any of these being used? if not deactivate them as none are set up it seems.

You say you are behind a firewall, is this a separate piece of kit or not? Could you give us a bit more info about the setup ie
Which box does is the dhcp server / IP
is this also the router and gateway for your lan?
Is this same box the firewall?


Your gateway address (10.94.0.254) would this be the dhcp server too?

with your ip set static as before, can you ping the dhcp server:

$ ping 10.94.0.254

---

### Post by help_help on 2006-09-18
hey!
i kept my comp switched off for abt an hour and mysteriously when i sitched it on, voila: net was working..i am still online, should i save soem particualr settings or something?

---

### Post by help_help on 2006-09-18
My net works when I boot directly into Linux but not so when I start from windows and tthen boot into Linux.can I do something abt this??

---

### Post by Original Brownster on 2006-09-18
Hi,
What's the chipset for the nic? 
I heard of some that are left in a suspended state by windows, windows forces a reset of the card at boot so it works ok, but I think an nforce chipset driver for linux doesn't force a reset hence the card doesn't come up unless you disconnect power for a while, now your online you should run a system update, it may download a more recent module for your nic and solve the problem.

HTH.

---

### Post by Jimmy_r on 2006-09-19
> My net works when I boot directly into Linux but not so when I start from windows and tthen boot into Linux.
Welcome to the club :p I have had this problem since dapper was in beta. My solution: I stopped dual-booting(to windows favor unfortunately, until something killed off my windows installation).

The only distro i have not had this problem with is openSuse.
One thing you can try is to install network-manager-gnome and its dependencies from synaptic. Suse uses that, and it solved my recent problem where simply rebooting ubuntu edgy forced me to do the shutdown procedure to get internet back.Now i have no problems, so it may or may not help you. I cannot test it myself since i got rid of windows.

May I ask if your ISP is swedish Telia? This may or may not be the source of the problem.

> I heard of some that are left in a suspended state by windows, windows forces a reset of the card at boot so it works ok, but I think an nforce chipset driver for linux doesn't force a reset hence the card doesn't come up unless you disconnect power for a while

That sounds interesting, i do have an nforce 4 chipset (Asus A8n-e). But if this is indeed the problem, i would be very interested in what suse does that the other major distros does not (in my experience Fedora, Ubuntu, Gentoo and a few smaller ones all have this problem.

---

### Post by Original Brownster on 2006-09-19
Hi,

> 
That sounds interesting, i do have an nforce 4 chipset (Asus A8n-e). But if this is indeed the problem, i would be very interested in what suse does that the other major distros does not (in my experience Fedora, Ubuntu, Gentoo and a few smaller ones all have this problem.

Check out this [thread,]("http://ubuntuforums.org/showthread.php?t=186848") he has a solution, you can download a patched version of the forcedeth driver that's the latest version. check the kernel it's patched against though.

---

### Post by Jimmy_r on 2006-09-19
Thanks, but as i understand it he patches his forcedeth to the version in the 2.6.17 kernel. Since i am running edgy, i already have the 2.6.17 kernel and the bug should not be present. It might still work for help_help though.

Another interesting thing is that i installed Vista RC1 a while ago. When i wiped vista and tried to reinstall ubuntu, the installation cd did not get dhcp as usual, so i shut the computer down and tried about 18 hours later. Still no dhcp.
I installed xp, and after a while it managed to get the internet working. So i kept xp about a week, and then reinstalled ubuntu.
This time i managed to get dhcp, but it is still acting more weird than before i installed Vista.
I could not even reboot ubuntu without getting the dhcp problem. This was resolved when i installed network-manager-gnome under edgy.
Now, if i shut down ubuntu and reboots into the live cd, i get dhcp. if i boot back into ubuntu, or reboot the livecd, i do not get dhcp.
So, in my understanding the standard ubuntu networking tools (dhclient etc) might not release the dhcp lease at shutdown, while the tools in network-manager does so.
But in that case, xp does not either release dhcp, but suse still manages to get dhcp lease after it.

And what vista did, i dont even want to think about. Either it messed with my hardware or my ISPs dhcp server. Or my ISP might simply have changed their hard/software at the same time as i installed vista.

help_help, how about you? If you have not installed network-manager yet, boot into ubuntu and make sure internet is working, then reboot directly into ubuntu again - does internet still work?

---

