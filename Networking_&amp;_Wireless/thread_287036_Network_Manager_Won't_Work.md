---
title: "Network Manager Won't Work"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by GreenHawkIA on 2006-10-28
Well - I have a Dell Latitude D505 which formerly had Dapper Drake on it.  I wiped it and did a clean install of Edgy.  The included networking tool will connect to any unsecured wireless network, but when I install network-manager-gnome (like what worked for this computer, no problem using 6.06) it will not scan for wireless networks to let me pick my connection.  When I go into the the networking setup dialog, it will not give me a drop-down list of wireless networks there, either.  My wireless is an Intel ProWireless 2200 b/g.  Any ideas on where to go?

---

### Post by GreenHawkIA on 2006-10-29
I have to confess this lack of response on this thread - along with no luck on Google or in the forums search - is leaving me feeling a bit hopeless.  I'm on a borrowed Windows computer to write this, as I am absolutely dependent on wireless access for the Internet for my laptop.  So if anybody has any hints, please let me know, ASAP.
Thanks.

---

### Post by squibT on 2006-10-29
Make sure your wl network settings are in /etc/network/interfaces

A quote I found "using only the Network/interfaces file is the recommended configuration"

Unfortunately I am in the same boat as you....no worky... no wl networks listed in NWM but my card is working fine...cant get an IP address though.

I switched over to the /etc/wpa_supplicant.conf file and I am using WPA right now to write this.

I have everything working using WPA and /etc/wpa_supplicant.conf file and no wl entries in the /etc/network/interfaces file. I switched to not using the /etc/wpa_supplicant.conf file and using the /etc/network/interfaces file only due to the fact that sudo wpa_supplicant -c /etc/wpa_supplicant.conf -Dndiswrapper -ieth1 reports errors. It seems this config is not using encryption but it is connecting to my AES secured wl network so it is working for me using wpa_supplicant.conf.

I will try to get the network/interfaces file setup but seems wl it doesn't work with NWM at all for me right now...more research

---

### Post by pete on 2006-10-29
I was able to get Network Manager working on my Latitude D610 following [this article on the Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").

According to that document, Network Manager can't use any devices listed in /etc/network/interfaces, so you need to comment out or remove everything in that file except 
[INDENT]auto lo
iface lo inet loopback[/INDENT]

---

### Post by GreenHawkIA on 2006-10-29
I just got it working myself.  See this post:
[http://www.ubuntuforums.org/showthread.php?t=263680&highlight=intel+pro+wireless+2200](http://www.ubuntuforums.org/showthread.php?t=263680&highlight=intel+pro+wireless+2200)
The last comment.  You have to go into the networking settings under System - Administration, and disable all your network configurations to let network-manager handle them.  Open properties for each wired and wireless connection and uncheck the box that says "Enable this connection."  Make sure under System - Sessions - Startup Programs, that network-manager is starting with nm-applet --sm-disable.  Then reboot, and now it works no problem for me.  Hope it works for you!

> **pete said:**
> I was able to get Network Manager working on my Latitude D610 following [this article on the Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").

According to that document, Network Manager can't use any devices listed in /etc/network/interfaces, so you need to comment out or remove everything in that file except 
[INDENT]auto lo
iface lo inet loopback[/INDENT]

---

### Post by Julius on 2006-10-30
I've just performed a clean install and I can't get network manager to work. I installed the package "network-manager-gnome", then edited the /etc/network/interfaces file, and it refuses to start. It gives some error at startup.

:(

---

### Post by GreenHawkIA on 2006-11-01
> **Julius said:**
> I've just performed a clean install and I can't get network manager to work. I installed the package "network-manager-gnome", then edited the /etc/network/interfaces file, and it refuses to start. It gives some error at startup.

:(

Post your error here.  It'll help us tell what's wrong.  Also, what did you edit your interfaces file from and to?

---

### Post by BrowneR on 2006-11-01
I am also having trouble with Network Manager under Edgy. (Dell Inspiron 9300, eth1 - ipw2200bg, eth0 - wired)

I can connect to wireless networks fine by editing my /etc/network/interfaces manually. This is fine although i frequently change networks and this is a hastle at present. I wanted to use Network Manager to allow me to quickly click and switch wireless network.

I have network manager installed and it gives the following output when started (from syslog)
```
Nov  1 23:23:53 localhost NetworkManager: <information>^IUpdating allowed wireless network lists. 
Nov  1 23:23:53 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov  1 23:24:05 localhost NetworkManager: <information>^IGoing to sleep. 
Nov  1 23:24:05 localhost dhclient: receive_packet failed on eth0: Network is down
Nov  1 23:24:07 localhost NetworkManager: <information>^IWaking up from sleep. 
Nov  1 23:24:07 localhost NetworkManager: <information>^IDeactivating device eth0. 
Nov  1 23:24:07 localhost kernel: [17179681.268000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  1 23:24:07 localhost NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Nov  1 23:24:07 localhost NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Nov  1 23:24:07 localhost NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Nov  1 23:24:07 localhost NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Nov  1 23:24:07 localhost NetworkManager: <information>^IDeactivating device eth0. 

```

the nm-applet lists no network adaptors at all.

also i notice that the gnome network settings program which allows me to configure my interfaces doesn't list all available wireless networks in a drop down list as it used to.

any ideas folks?

---

### Post by BrowneR on 2006-11-01
ok i now have network manager working!

what solved it for me was just a simple purge and reinstall with all network adapters disabled.

first we need a copy of the .debs from the repository: (as we are going to take the network down)

open a terminal and type the following (for i386)
```

wget http://fr.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb

```

now purge the currently installed packages
```
sudo aptitude purge network-manager network-manager-gnome
```

make sure all interfaces are disabled
```
sudo ifdown eth0
sudo ifdown eth1
```

make sure your /etc/network/interfaces file only has the loopback adaptor listed
```

sudo gedit /etc/network/interfaces

```

the file should read as follows
```

# The loopback network interface
auto lo
iface lo inet loopback

```

now i restarted just to make sure everything was clean

open that terminal up again and install the packages
```

sudo dpkg -i network-manager_0.6.3-2ubuntu6_i386.deb
sudo dpkg -i network-manager-gnome_0.6.3-2ubuntu6_i386.deb

```

i had to then manually add nm-applet to the gnome session.

all works for me now. no idea why that fixed it but it seemed to be quite picky about having all interfaces disabled properly and the config removed.

---

### Post by Julius on 2006-11-04
OH, the error was that icon thing. I googled for it and it was fixed. All I had to do is rebuild the icon cache, apparently. It works like a charm now :)

---

### Post by jonasren on 2006-11-15
> **GreenHawkIA said:**
> I just got it working myself.  See this post:
[http://www.ubuntuforums.org/showthread.php?t=263680&highlight=intel+pro+wireless+2200](http://www.ubuntuforums.org/showthread.php?t=263680&highlight=intel+pro+wireless+2200)
The last comment.  You have to go into the networking settings under System - Administration, and disable all your network configurations to let network-manager handle them.  Open properties for each wired and wireless connection and uncheck the box that says "Enable this connection."  Make sure under System - Sessions - Startup Programs, that network-manager is starting with nm-applet --sm-disable.  Then reboot, and now it works no problem for me.  Hope it works for you!

This worked like a charm for me too. Thanks!

---

### Post by cwhisperer on 2006-11-18
hi,
the solution posted by BrowneR works perfect on rebooting. But I wasn't able to create a VPN connection, message: no suitable vpn software found. The major problem was: when I rebooted again the nm-applet didn't found any network devices again and in the /etc/network/interfaces I found the devices I killed just before. It seems like nm-applet does not find any network devices on starting up, how to solve this ? Thank you for any further help.... ;)

---

### Post by BrowneR on 2006-11-18
Im not sure what to suggest regarding network manager. I have had problems in the past and then i just seemed to get lucky with it.

how were you trying to create the VPN? I have been using the Cisco VPN client to connect to my university network quite succesfully. could you connect to the VPN before you tried Network Manager or is this not related?

---

### Post by Geoff2077 on 2006-11-19
BrowneR's procedure (to the letter) to reinstall has gone a long way to getting the nm applet to function. Now when PC boots, the NM applet shows the searching and eventually connects.

HOWEVER....
it reports that it has made a connection to my wired network on eth01, even though this is not connected at all (just the pci card is present).

WHAT it is not doing is seeing the wireless card on ra0. Also I cannot see other network cards being available.

When I check in the System Admin Networking list, it lists only the wired connection (eth01) which is not enabled, (as it should be acc to BrowneR)

Somewhere I am loosing the ra0.
 
Anyone have an idea on how to get the applet to see the wireless network card????

So near but so far away!!!

---

### Post by Geoff2077 on 2006-11-19
Further to my posting.
Getting the wireless to work with VPN is tantalizingly close BUT as a newbie, I cant make the final connection...

I have found that if after booting up, I use terminal and issue the command
dhclient ra0
then the wireless network connection works. I have left the nm applet reporting the connection on the wired network (even though there is no connection)

I can now connect to the network and internet,etc.
NOT ONLY THAT..
I can even use the nm-applet to select a VPN connection and wonder of wonders  it actually connects to my office server.

ALL I AM MISSING
is having the nm-applet recognise and start the wireless network instead of the unconnected Wired network.

I tried putting the command
dhclient ra0 
in the /etc/rcS.d directory as a script, but I have the distinct impression that this is not being executed at startup, because there is no wireless connection. I have to manually issue this command from the terminal to start the connection, and then status is as described above.

So Close and still so far...
Geoff

---

### Post by cwhisperer on 2006-11-19
sorry for the late answer. In System/Administration/Networking I disabled all  network adapter an rebooted. Nm-applet was then able to connect to the wireless without problems. The only problem remains making a vpn connection. Still having the message: No suitable VPN software was found on your system.

---

### Post by Geoff2077 on 2006-11-19
Whisperer,
If you followed BrowneRs procedure, you wont have installed any VPN software as yet.
Use System/Admin/Sys Apt and install the network-manager-pptp application.

---

### Post by BrowneR on 2006-11-20
> **Geoff2077 said:**
> Whisperer,
If you followed BrowneRs procedure, you wont have installed any VPN software as yet.
Use System/Admin/Sys Apt and install the network-manager-pptp application.

you know i never realised Network Manager did VPN management!
thats awesome, thanks :D 

this is all getting too complex for me, think im out of my depth already... ;)

---

### Post by cwhisperer on 2006-11-20
ok every thing is working now ... thanks a lot ;)

---

### Post by Geoff2077 on 2006-11-20
BrowneR,
Lucky bugger - wish I could say the same. 
cheers

---

### Post by Tethtibis on 2007-06-27
you may have to reinstall the wireless using ndis wrapper, or some command line installer.

---

