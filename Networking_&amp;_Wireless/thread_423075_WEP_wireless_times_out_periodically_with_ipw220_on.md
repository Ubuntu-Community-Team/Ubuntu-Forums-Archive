---
title: "WEP wireless times out periodically with ipw220 on Feisty."
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-04-25
I am seeking help with a problem I am facing but let me tell you that after skimming through the titles of the posts here, I feel a little better, not absolutely but relatively. I have a Toshiba Centrino which has an Intel Pro Wireless (ipw2200) card and it was working better (not absolutely fine with the network managers like wifi-radar, network-manager, etc. and without them too) compared to Feisty. I had many other reasons because of which I feel fine with upgrading to Feisty. 

I am connecting to a wireless connection at home which has a 64-bit WEP encryption. The major issue with my wireless connection is that with or without a network-manager, it seems to kind of not ping or download a page for a few minutes every now and then. I have restarted back into linux (Kubuntu) and still it behaves the same way so I am assuming that wasn't anything that got cleared up with a restart. So it has to be some configuration which is not working for me by default. I keep facing this problem every hour and half or around that time. I booted into Windows to check if it was a problem with my wireless, but that wasn't the case. I jave tried siabling ipv6 but it didn't make any differnce so I again enabled it. I just noticed that even on a connection without any encryption I am getting a slower connection (which is different from the problem I have with WEP on my home wireless). It feels as if something is strangling the pipe from where data comes and goes. I am not sure what is going on. In Firefox I often get sutck on messages like "looking for..." or "waiting for..." for some seconds. I shouldn't get those problems at least when I am in my university(where there is no encryption) which has a blazing fast connection. I have been using opendns nameservers and the following is my /etc/network/interfaces:

[COLOR="Red"]auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp[/COLOR]

Any ideas on this? Thanks.

Keith.

---

### Post by Buffalo Soldier on 2007-04-25
**_Network Interface & Network Manager_**

I'm using a DELL Inspiron 510m, the same Intel PRO/Wireless 2200 but I'm using WPA encryption. So far it's been trouble-free in Edgy and Feisty.

```
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

As far as I know, to have Network Manager handle your network connections, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces. Example:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp
```
Reference: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)


**_OpenDNS & Dynamic IP (DHCP)_**

OK, now that you commented out everything in /etc/network/interfaces we need to do something to set your network to use the OpenDNS nameserver.
[LIST=1]
[*]Run: ```
sudo gedit /etc/dhcp3/dhclient.conf
```

[*]Change the prepend line to read:

> prepend domain-name-servers 208.67.222.222, 208.67.220.220;

[*]Run: ```
sudo /etc/init.d/networking restart

```[/LIST]

Reference: [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by keith11 on 2007-04-26
Thank you for your suggestions. I did comment out all other interfaces in /etc/network/interfaces and also started knetworkmanager. I am not sure though why knetworkmanager doesn't change the icon to progressive bars when it is fully connected. I have noticed that when I am connected to wireless without using the opendns nameservers, it does show the progressive bars when it is connected, but when I use the opendns servers, the icon just shows a small full bar under a wheel and doesn't get transformed to the bars. I am locking my resolv.conf so I didn't have to go for the second setting that you suggested. I am not sure if knetworkmanager will let me kill the application as well as restart it without restarting the system as it has been happening so far. I will try it and post the result. 

Was there anything that could indicate why I would be losing the connection periodically though? Thanks again.

Keith.

Edit: Although this is not directly related to the original problem, but this is about knetworkmanager. As I have been facing the problem, I can't do anything like switching to offline mode or disabling wireless through the options menu of knetworkmanager. And whwatever option I try to select, let's say diabling wireless, that option will be activated next time I boot. I CAN select other options like configuring notifications, etc. Owing to these problems I had uninstalled knetworkmanager and tried wicd and wifi-radar but nothing worked. In addition to the WEP problem, is there a way I can get proper control of knetworkmanager? I have filed a bug report related to this problem here: [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450) 
Thanks.

---

