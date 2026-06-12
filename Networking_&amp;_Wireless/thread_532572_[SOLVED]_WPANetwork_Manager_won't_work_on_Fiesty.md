---
title: "[SOLVED] WPA/Network Manager won't work on Fiesty"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by db163404 on 2007-08-22
Hi, first time poster... weeeeeeeeeeee.

I've recently moved to Ubuntu Linux from Microsoft. I have tinkered around with *nix systems off and on but have just recently taken the plunge using Ubuntu as my primary OS. I'm still very much a novice, so far everything has been great. Anyways... moving on.

I spent several hours this afternoon reading various posts on here and Blogs other people have written about getting WPA to work on Ubuntu. I decided I liked the network-manager approach as opposed to doing a bunch of command line/config file editting. My WEP wireless networks have worked fine just by going into the network-admin and setting up my networks. 

Today I needed to set up a WPA network and find that there is no WPA key option in network-admin. So I started looking into things. I installed the gnome network-manager and set wireless to roaming mode and then comment out all but the lo entries in my /etc/network/interfaces file. I restart my system and the network-manager will pick up all networks in range and lists WPA as an option but will not let me connect to any of them.  Further investigation revealed that even my WEP networks that were working fine before no longer work under network-manager. I've since uncommented the entries in my /etc/network/interfaces file and restarted the system so I could join my WEP network again. However, I would really like to be able to join WPA networks in the future and find the network-manager more appealing than the generic/limited network-admin panel.

I appreciate any and all help that I can get to straighten things up.

Again I'm running on Ubuntu Fiesty Fawn 7.04, 32bit desktop installation. My machine is a Gateway laptop Model T3A6B41011579 with integrated WLAN. I tried to see if my wireless card was supported but couldn't make heads or tails out of the wpasupplicant page.

Thanks,
Derek

---

### Post by Jamie Jackson on 2007-08-22
What's "lshw -C network" give you?

---

### Post by db163404 on 2007-08-22
Hi Jamie, thanks for the reply! Here is the output:

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c1:ea:30
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d4000000-d4003fff ioport:2000-20ff irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:9f:42:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d6000000-d6000fff irq:16

---

### Post by db163404 on 2007-08-23
Bump

---

### Post by db163404 on 2007-08-23
bump

---

### Post by kevdog on 2007-08-23
Ok 

You have an intel chipset -- this should work.

Have you installed the wpa-supplicant package??  If not:
```
sudo aptitude install wpasupplicant
```

Ok, the next step we are going to do is to try to configure everything by hand manually.  Note that this is not the permanent solution.  Because you are having problems, this gives us a window to receive debugging statements and make adjustments as necessary.  So please dont think this is how its going to be done everytime!

Ok lets start:

Create a wpa_supplicant.conf file
```

gksu gedit /etc/wpa_supplicant.conf

```

Contents of the wpa_supplicant.conf file are the following:
This example is assuming WPA (not WPA2) with TKIP cipher
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid in quotes>"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="<ASCII password in quotes>"
}

```

Next find your interface name (ie wlan0, eth1, etc).  In order to do this:
```

lshw -C network

```

Find your wireless section, and then look for logical name -- this is your interface name (An example below)
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

The following is an example of what to type at the command line to bring up your network with wpa manually.
Assumptions:
1. Interface name is wlan0
2. Wireless driver is ndiswrapper (known as wext).  (See man wpa_supplicant for alternative choices)

***Specifically for you since you've provided the information your:
interface name = eth1
Wireless driver is intel so use ipw instead of wext in the example below

A lot of debugging output will be given (the whole purpose of this exercise). You  may get some errors on the first few commands -- dont worry about it -- these instructions are somewhat overkill.  Im concerned about any errors you get at the end.

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by db163404 on 2007-08-23
Great thanks! As soon as I get to a stopping point on this proposal I'll give things a try. One question though, once I get this working will I have to manually edit these config files each time I want to add a network or is there a front end for some of this?

---

### Post by Jamie Jackson on 2007-08-23
All this manual stuff is to pinpoint whatever root problem(s) you're having. Once that's straightened out, it will then be possible to step back and get something easy and automated going.

---

### Post by chankp on 2007-08-23
Greetings,

I'm also having the same problem.
Contrary to what my book (Ubuntu Unleashed) says, the network manager does not offer the WPA option at all, only WEP.
I only managed to get the wireless working (WPA) after manually keying in commands as posted by amniarix (thanks for the great info).  Since it works after issuing all the commands I assume the WPA module was already loaded when I install Fiesty.  
If this is so, how is it that the WPA option didnt appear in the network manager applet?
How can I get the network manager to include the WPA option?
Any help/advise is greatly appreciated.
Thanks n cheers.

---

### Post by db163404 on 2007-08-23
Naturally the thought never occured to me to attempt this when I had access to the WPA network... stupid me. I'll attempt the requested commands as soon as I'm back in the office. Thanks again for the help, I really appreciate it!

---

### Post by kevdog on 2007-08-24
> I only managed to get the wireless working (WPA) after manually keying in commands as posted by amniarix (thanks for the great info)

Who is amniarix and what were those commands??

---

### Post by db163404 on 2007-09-14
I've finally got the chance to get working on this stuff again. I tried to follow kevdog's suggestions. I got to this step:

```
sudo wpa_supplicant -w -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd
```

The result seemed to put things in an infinite loop of connection failures.

```

wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 2976 bytes of scan results (13 BSSes)
Scan results: 13
Selecting BSS from priority group 0
0: 00:1a:70:84:08:1b ssid='ROS' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:1a:70:84:08:1b (SSID='ROS' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=11

```

Not really sure where it starts and stops, but basically that's the output I was getting over and over again.

---

### Post by db163404 on 2007-09-14
I have no idea what the commands you had me type due, but now wireless networks that worked before no longer work. Please help!

---

### Post by Jamie Jackson on 2007-09-14
I think kevdog's on hiatus. However, the only thing I see in his commands that is "permanent" is the creation of the wpa_supplicant file*. Therefore, to reverse everything you did in those commands, just run:

```

sudo mv /etc/wpa_supplicant.conf /etc/wpa_supplicant.conf.bak

```

Afterwards, give NetworkManager a bump:

```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Jamie

*P.S. He had you install wpasupplicant, too, but that can only help your situation.

---

### Post by db163404 on 2007-09-14
This is not good at all :( I removed the wpa_supplicant file and restarted the network and still no such luck. I rebooted too. Any other advice on general wireless troubleshooting?

---

### Post by kevdog on 2007-09-15
Can you post your wpa_supplicant.conf file and also iwlist scan.  Is the router set for Wpa1 or WPA2 or do you know??  Do you have access to the router settings with the WPA?

---

### Post by db163404 on 2007-09-16
Well the good news is that I got my other network working again, weeeeeeee. The bad news is I have no idea what I changed :( But yeah, back to where I started just fighting with WPA.

I don't have access to the WPA network locally but whenever I'm in the office I do have access to it. The problem with that is, I work from home a lot.

wpa_supplicant.conf contents to follow.

---

### Post by db163404 on 2007-09-16
Also, I don't know if this helps you, help me in anyway but I thought it was worth mentioning that whenever I change network admin stuff to "roaming" to get network manager to kickin, even my wireless network (WEP) that has always worked stops working.

---

### Post by db163404 on 2007-09-16
As promised, the ever famouse wpa_supplicant.conf file :)

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="ROS"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="secret"
}

```

---

### Post by kevdog on 2007-09-16
Keeping this file will never screw anything up -- its just a text file -- so you really would never have to delete it -- if you didnt want to.

Make sure you have the wpasupplicant package installed:

sudo aptitude wpasupplicant

Also since its been so long since Ive heard anything from you -- what driver are you using for your wireless card???  If you post
lshw -C network
then everybody will know!  

Also if you post 
iwlist scan
when you are range of the WPA network it would also help.  Are you sure the credentials for your work WPA are simply a PSK and not something else??  That would mean everybody has the same password to access the network.

---

### Post by db163404 on 2007-09-16
wpasupplicant is installed
sudo apt-get install wpasupplicant
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
The following packages were automatically installed and are no longer required:
  libxfcegui4-4 libxfce4mcs-client3 libqt4-qt3support libqt4-core libsqlite0
  libarchive-zip-perl libxfce4util4 libexo-0.3-0 libqt4-gui libqt4-sql
  libxfce4mcs-manager3 libfile-rsyncp-perl libthunar-vfs-1-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c1:ea:30
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d4000000-d4003fff ioport:2000-20ff irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:9f:42:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d6000000-d6000fff irq:16

```

This is my WEP network. This is the one that stops working if I use network manager.
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B3:A2:2F:C6
                    ESSID:"DB"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-39 dBm  Noise level=-39 dBm
                    Extra: Last beacon: 88ms ago

```

The WPA network is a shared key.

---

### Post by kevdog on 2007-09-16
Just for kicks with the WEP network:

sudo ifconfig eth1 down
sudo ifconfig eth1 0.0.0.0
sudo ip route flush dev eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "DB"
sudo iwconfig eth1 key HEXKEYHERE
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

Any lock ups after this?

---

### Post by db163404 on 2007-09-16
Nope that worked flawlessly.

Let's take a step back. What should I try to do to get the WEP network (DB) to work with network manager?

I go in and I click "roaming" so that network manager kicks in. I then get the little bar thingies (for network manager) in the toolbar. I click it and I see networks in range. I choose my network DB. I enter the key. Then try to pull up a browser... and no internet for me :(

It could be such a thing that the WPA will end up working if network manager actually works. But then again I'm a newb and sux and stuff. I dunno, just a thought. What do you think?

---

### Post by kevdog on 2007-09-17
I dont know why it doesnt work.  You just connected manually, so there is no reason network manager shouldnt work for you.  As an alternative, why dont you just try installing wicd.  Connect to internet, and download and save the wicd package without installing it. 

All of your deb files should be located in /var/cache/apt/archives.  Look in here to see if you have network-manager-gnome.  If you do not, download it but do not install it.  We want to save a working copy here in case something doesnt work.  

Anyway, once have the network-manager-gnome.deb file in the archive folder and a working copy of wicd,

uninstall network-manager

sudo aptitude purge network-manager-gnome

then install wicd.  Here is the wicd homepage:
You want the 1.33 testing .deb file

---

### Post by Jamie Jackson on 2007-09-17
Side note: wicd seems pretty nice (yay, configurability), but I use the slick VPN support in NetworkManager--wicd's lack thereof keeps me from switching. (I know it's coming soon in wicd.)

---

### Post by db163404 on 2007-09-17
Before I go that route, is there a way I can completely remove network-manager (safely!) and resinstall it before I abandon it and try to go to wicd.

---

### Post by Jamie Jackson on 2007-09-17
When I tried wicd, it uninstalled NetworkManager. Same thing in reverse when I went back to NetworkManager.

Edit: But follow kevdog's instructions, so you have a local copy of the NM installer files to fall back on.

---

### Post by db163404 on 2007-09-17
apt wont work for the unistall?

---

### Post by kevdog on 2007-09-17
Ididnt know that nm did VPN -- learned something today -- but those options with wicd are sure nice!

---

### Post by db163404 on 2007-09-17
Okay, life is almost good!

The install of wicd was relatively painless and my WEP network works under it. Should be able to test WPA networks tomorrow.

I have 2 small problems right now that I'm sure have easy fixes. Please help :)

1) At startup I get a message that wicd needs access to my network cards and asks me to enter my password. It's not that big of a deal but is there a way to avoid this?
2) Despite entering python /opt/wicd/tray.py in my System -> Preferences -> Sessions the tray icon does not display at startup. I have to manually start it.

If any of you guys can help me figure this out life will be good. Thanks!

---

### Post by kevdog on 2007-09-17
I dont know if I can help you on any of these problems since I have the same issues.  The asking for password problem is very intermittent and doesnt happen all the time.  The tray icon never starts for me despite being in the Sessions menu.  Once I installed Conky that monitors my network status, I kind of forgot about it.  Possibly imdano can help on these issues.

---

### Post by db163404 on 2007-09-17
Fair enough. I can deal with it for now. Thanks so much for all the assistance. Keep your fingers crossed for me when I test on WPA tomorrow!

---

### Post by kevdog on 2007-09-17
Once you get everything up and running -- just take a look at conky.  The svn sources have wireless functions built-in so you dont have to do a lot of scripting.  Im sure you will like it --- however one step at a time.

---

### Post by Jamie Jackson on 2007-09-17
> **kevdog said:**
> Once you get everything up and running -- just take a look at conky.  The svn sources have wireless functions built-in so you dont have to do a lot of scripting.  Im sure you will like it --- however one step at a time.

Could you provide more of a teaser for conky? I looked at the home page and FAQ, but still have no idea how it relates to wireless.

---

### Post by kevdog on 2007-09-17
Sorry here is a screen capture (well to save size only the part of the screen with conky on it)  The neat thing about conky is that its dynamic, meaning that although this shot is static, the values change overtime and are updated to the screen.  The program scans for detected networks every 20 seconds (well calls iwlist wlan0 scan every twenty seconds) so these two can be updated dynamically.  Both WAN and LAN IP addresses can be listed along with signal strengths.  I like it because it just sits "embedded" on the desktop

---

### Post by Jamie Jackson on 2007-09-17
Okay, I understand better now, thanks. I thought that you might mean that it manages connections, but I see that it simply keeps you *apprised* of available networks (as well as sys monitoring stuff).

---

### Post by db163404 on 2007-09-18
First attempt is thwarted once again :( I've not been able to connect to my university network with wicd. It sees it... it gives me an ip address but the net owns me.

---

### Post by kevdog on 2007-09-18
You are assigned an IP address -- are you sure at this point its not a gateway or route problem.  If you are assigned a local IP address on the network, can you ping another computer on the network or ping google (which would be ping 72.14.207.99)??

Is your routing statement correct??

route -n

---

### Post by db163404 on 2007-09-18
It very well could be a gateway/route problem. Am I missing a step of configuration or something?

I was able to ping machines within my network and connect to my router, but nothing outside of it.

Specifically what am I looking for when I do a route -n?

---

### Post by db163404 on 2007-09-18
I've gotta get past this. The jerks at my university have installed Vista on all the lab machines, so if I can't get wireless working there (or at work) I'm forced into Vista. That simply won't do!

---

### Post by db163404 on 2007-09-18
This is nothing that a firewall would be blocking or anything like that, would it? Like have to confirm something as a trusted connection or some crap? I've installed Firestarter, that's about it.

---

### Post by kevdog on 2007-09-18
From the vista machines get the IP address of the gateway.

Then for route -n

The line that contains UG

Here is mine for example:

0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

The second value (192.168.1.1 in my example) should be the address of your gateway

Again posting route -n would help if you can.

---

### Post by db163404 on 2007-09-18
I'm actually at work right now. Here is what I get if I run route -n on another Linux box in the office:

Destination     Gateway         Genmask          Flags   Metric   Ref      Use     Iface
192.168.1.0   0.0.0.0           255.255.255.0  U        0         0         0        eth0
0.0.0.0          192.168.1.1    0.0.0.0             UG     0          0         0        eth0

I'll try to run the same on my Ubuntu box, but will probably have to reboot to get the wired connection working again.

---

### Post by db163404 on 2007-09-18
When I connect via the wired connection I get this (connection to the web success!)

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

When I connected via wireless I get this (but no connection to the web):

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

---

### Post by db163404 on 2007-09-18
Logic suggests that the gateway is correct... I can access local machines just fine, but not the internet via a browser. What the hell?

---

### Post by db163404 on 2007-09-18
I just did an ifconfig and got this:

```

eth1      Link encap:Ethernet  HWaddr 00:18:DE:9F:42:43  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe9f:4243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:3 dropped:3714 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7367 (7.1 KiB)  TX bytes:2818 (2.7 KiB)
          Interrupt:16 Base address:0xc000 Memory:d6000000-d6000fff 

```

See the errors:3 thing? Not really sure what that means, but errors don't sound good.

---

### Post by kevdog on 2007-09-18
The statement you posted is correct, the gateway is listed as the router address 192.168.1.1

Again the gateway doesnt always have to be the router, but in small networks it usually is

---

### Post by db163404 on 2007-09-18
So what's next?

---

### Post by kevdog on 2007-09-18
can you ping an external ip address, if you cant, this would imply a name resolution issue

---

### Post by db163404 on 2007-09-18
Correction, I'm unable to ping anything over wireless (at least now). This means locally or otherwise.

---

### Post by kevdog on 2007-09-18
Wait, lets back up -- you cant even ping a computer on the local network or the router itself??

---

### Post by db163404 on 2007-09-18
Alright I did a reboot and connected to wireless. I was able to ping locally and externally but no browser connectivity.

---

### Post by kevdog on 2007-09-18
Ok, thats better

If you can ping google or yahoo for example by IP address, then your internet is working, its just that name resolution (turning domain names into IP addresses) isnt functioning properly

whats your resolv.conf file show:  /etc/resolv.conf

---

### Post by db163404 on 2007-09-18
/etc/resolv.conf

```

search cns.ohiou.edu
nameserver 132.235.64.1
nameserver 132.235.64.2

```

---

### Post by db163404 on 2007-09-18
You are most correct. I just hit google by IP address and finally I get something in the browser. Woohoo!

Interestingly enough I had just figured this out myself when I started telneting into websites, lol.

So how to fix the nasty name resolution issues?

---

### Post by kevdog on 2007-09-18
Can you also post /etc/dhcp3/dhclient.conf?


Are those name servers correct??

---

### Post by db163404 on 2007-09-18
That nameserver is the one at the university, not this network per se. It's sort of weird b/c I'm on a subnet.

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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

---

### Post by db163404 on 2007-09-18
Someone heeeeeeeeeeelp. It's 5:00 and I'm about to have to go home and lose this network and stuff.

---

### Post by db163404 on 2007-09-18
When I launch the wicd tray icon from the command line I see lines that say:

disabling ip
disabling dns

after each network it detects. Is this normal?

---

### Post by db163404 on 2007-09-18
So I think the problem is centered around old connections that were stored by network-admin. I realize that installing wicd uninstalled network-manager... is there a way to take network-admin out of the equation or at least delete the old configurations. Despite choosing a different network it's using the key, dns, etc from an old configuration created by network-admin.

---

### Post by kevdog on 2007-09-19
Can you post a screenshot of the above disabling statements????  What if you just try to connect by hand not using wicd, network-manager, etc??? Didnt we try this earlier??  Have you tried this on any other network other than the university network??

---

### Post by db163404 on 2007-09-19
for each network it see its says this:

ESSID : Ohio University
making a new network entry...
disabling ip
disabling dns
0

....

etc etc for each network that is detected.

I really think the problem is old saved settings in network-admin. It's looking at stuff for my home network which is not valid for these networks (such as the route for dns). Is there a way I can delete the settings for network-admin. It says they are gone but it seems to keep defaulting to my home network that I had saved.

---

### Post by kevdog on 2007-09-19
What is network-admin???  I dont know what that is.

---

### Post by db163404 on 2007-09-19
Just the tool that comes up when you do System -> Administration -> Network, this is the generic dummy thing that comes installed on Ubuntu. Network Manager or Wicd lays on top of this.... or at least that was my impression.

---

### Post by kevdog on 2007-09-19
No WICD doesnt lay ontop of that - thats for sure.  You have confirmed that your DNS servers listed in the /etc/resolv.conf file are correct???

You might want to PM a user called imdano and ask him to join the forum here.  He knows a lot about how WICD works.  You need to do some background work however and make sure some of the information you are giving him is correct.

Also, just for kicks, take a look at the OpenDNS website.  Im not saying this is a perfect solution, however this is just a service that provides DNS for the lay public -- thats all it does.  Possibly you could use these servers first as your dns servers, and then have your university dns servers on a lower priority.


Can you do something for me, and at the command line do a 
dig -x google.com

I just want to see if this works.  Its kind of like nslookup.

---

### Post by db163404 on 2007-09-19
The nameservers are correct and work fine from wired connection or wireless when I boot up in windows.

I'm like 98% sure that the problem isn't with wicd. It's something else.

dig -x google.com just timed out and couldn't connect to the server.

---

### Post by db163404 on 2007-09-19
Why do the dns servers change back everytime I edit resolv.conf and try to reconnect? I'm trying to make it use the different nameservers (opendns for example) and it's not holding the setting?

---

### Post by kevdog on 2007-09-19
Definitely a dns problem.  PM either imdano or noob12.  noob12 is very good at resolving dns issues.  Ask him to join the discussion.  Again I dont think the problem is with network manager or wicd, just the dns resolution.

---

### Post by db163404 on 2007-09-19
Excuse my ignorance but how would I go about finding these people?

---

### Post by kevdog on 2007-09-19
At the top of the screen (almost at the top) where it says Welcome <username> Last visited....

Click on Private Messages.

Then click on Compose in the left hand column.  Your recipient will be noob12.  Give him a link to this thread and tell him that KevDog thinks you are having problems with dns resolution and configuration of the /etc/resolv.conf file.  Could you give some assistance.

---

### Post by db163404 on 2007-09-19
Nevermind I ran a search and found them.

---

### Post by noob12 on 2007-09-19
Hey db163404, try this thread if you didn't find it already:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

I'm watching that and now this thread if you have questions.

---

### Post by imdano on 2007-09-19
> **db163404 said:**
> Why do the dns servers change back everytime I edit resolv.conf and try to reconnect? I'm trying to make it use the different nameservers (opendns for example) and it's not holding the setting?This is because wicd is changing them during the connection process.  If you don't specify static DNS servers wicd lets dhclient assign them for you.  If you enter the nameservers you want to try into wicd instead of directly editting /etc/resolv.conf they should stick.

Also, seeing "disabling ip" and "disabling dns" is normal.  It's referring to static ip/dns address settings in the wicd GUI.  Kind of a misleading message though, isn't it?

You might want to compare the contents of resolv.conf after making a wired connection vs. wireless (if you haven't already, I might have missed that).

---

### Post by db163404 on 2007-09-19
Thanks for both of your replies.

So far the only difference I've been able to find between a working network and a non working network is that the working one adds an entry to /etc/network/interfaces that has the wireless network's essid and key.

I have compared the resolv.conf on both wired/wireless at work. The dns servers were the same in this instance, wire worked, wireless did not.

I'm actually at home for a bit but will be heading back in town shortly and I'll try any new suggestions that fall out. In the mean time I'll begin reading up on that other thread.

---

### Post by kevdog on 2007-09-19
The /etc/network/interfaces file is only used by network manager and not wicd.  If you see the essid and key in this file, then you are configuring the network manually -- which means network manager is not configuring it since it is defaulting to the configuration within the file.

Which are you trying to use to make the connection, network manager or wicd (I guess a third option would be the command line but I dont think you are doing this)???

---

### Post by db163404 on 2007-09-19
It must have been left in there from when I was using network manager then, because I'm using wicd now.

I've also followed the instructions on the link noob12 posted. I'll see if this helps me any when I go back in town.

---

### Post by noob12 on 2007-09-19
Hey **/etc/network/interfaces** is used by the base **/sbin/ifup** and **/sbin/ifdown** and normal basic network startup.  It is not part of NetworkManager (!)

---

### Post by kevdog on 2007-09-19
Hmm I didnt know that, however that information is funny.  Ive been managing my networks with wicd, command line (wlan0) for about 6 months now, with no mention of the wlan0 interface inside the interfaces file.  I dont really use the ifup, ifdown commands, rather than the ifconfig counterparts, which I know there is a difference between these two commands.

Correction: I didnt know that the ifup / ifdown commands were actually higher level functions that call ifconfig and route.  Guess I learned something today.

---

### Post by db163404 on 2007-09-19
Update, I'm back on campus and have a limited timeframe to work with :( As mentioned before I followed noob12's steps on the other thread before coming in town... as it turns out that made it more mad than anything else. I can now no longer even obtain an IP address... let alone resolving domain names.

---

### Post by noob12 on 2007-09-19
So here's how it works.  You have to mention things in /etc/network/interfaces if you want ifup, ifdown and /etc/init.d/networking (which call these)  to look at them.  The ifup/down utilities interpret these files even if NM isn't there.

If NM is running and you don't mention an interface in /etc/network/interfaces, then NM considers it to be "roaming" (and totally under its management), and ifup/down and /etc/init.d/networking ignore them entirely.  If you do mention them, NM is *supposed* to respect the configuration settings in the file, but I'm not confident it always does.

---

### Post by db163404 on 2007-09-19
I snagged my buddy IRL to come help me with this. After much tinkering we shutdown firestarter... and viola it works! So for whatever reason firestarter wasn't allowing DNS to flow through.

---

### Post by Jamie Jackson on 2007-09-19
Doh!

---

### Post by imdano on 2007-09-19
Oh, yeah that's actually happened to me before.  Didn't notice that you said you were running it.  Could have saved you some trouble.

---

### Post by db163404 on 2007-09-19
Lol, now you tell me!

Oh well, it's fixed. Life is good!

Thanks everyone who helped me work through that!

---

### Post by smurtguy on 2007-10-31
> **noob12 said:**
> So here's how it works.  You have to mention things in /etc/network/interfaces if you want ifup, ifdown and /etc/init.d/networking (which call these)  to look at them.  The ifup/down utilities interpret these files even if NM isn't there.

If NM is running and you don't mention an interface in /etc/network/interfaces, then NM considers it to be "roaming" (and totally under its management), and ifup/down and /etc/init.d/networking ignore them entirely.  If you do mention them, NM is *supposed* to respect the configuration settings in the file, but I'm not confident it always does.

Arrrrrggggghhhh!!!!!!!!!!!!!!!!!!!!!
And a huge cheer too

Thank you for this explanation. With it I fixed the stupid #)$)(*&^%_%__*(&@#####@@!!! on going problem with NetworkManager

I've had it "break" on multiple machines, and everyone I know has had issue too.

All I had to do was remove the references to any of the interfaces from

/etc/network/interfaces

so bleeping simple yet, so totally obfuscated

What happened on all of my machines is that at some point I installed some new packages to try some software out ect, and in the process the config for one of those packages added entries into the interfaces file for my existing network interfaces.

One thing I really would like to see is just how deep or shallowly one has to dig to find mention of this fact about the interfaces file.

not having a good autoconfig networking tool has been one of the biggest stumbling blocks I've found in getting anyone to actually stick with linux.  As soon as NM "broke" and they had to start jumping through all sorts of hoops, almost everyone I've know has just gone back to windows and stayed.

Again, thank you for mentioning this bit of information, it has helped (will help) me and others tremendously.

---

### Post by Jamie Jackson on 2007-11-01
You can find that documented [here]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"), FWIW.

---

### Post by mateuszbaranski on 2008-01-07
Shoudn't it be in deamon mode with wpa_supplicant? In my laptop your script is stopping at wpa_supplicant if I dont add option "-B"

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -[COLOR="Red"]B[/COLOR]w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

If it is daemonized your sript is working great. I had to try command line with WPA network since I encountered problems with ipw driver - if I use ipw driver in wpa_supplicant dhclient cannot receive DHCPOFFER from access point. I have got ipw2200: Intel(R) PRO/Wireless 2200/2915 card so I am confused:
it works fine when I start:
```
sudo wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd
```
but doesn't work with:
```
sudo wpa_supplicant -Bw -Dipw -ieth1 -c/etc/wpa_supplicant.conf -dd
```

The begining of the problem was that I coudn't see any network in networkmenager. I reinstalled networkmenager, wpasupplicant and all related stuff  but it didn't help.
I use gutsy 7.10

---

