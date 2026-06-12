---
title: "Another USB Linksys Help"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by batninth on 2007-01-21
Hi,

I've installed Edgy on my PC and have a Linksys HU100 USB connected wireless adaptor (aka WUSB54Gv4 - it's a local name in the UK).

I have installed the rt2570 drivers from the Networking (Universe) repository, and then built the drivers & added them to modprobe.

When I restarted & look at the USB devices I see:
desktop:/etc/network$ lsusb
Bus 004 Device 002: ID 13b1:001a Linksys 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

When I look at iwconfig I see:
desktop:/etc/network$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      RT2500USB WLAN  ESSID:"home_wireless"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

And when I look at ipconfig I see:
desktop:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:92:EA:B8  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe92:eab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:10810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11003456 (10.4 MiB)  TX bytes:651745 (636.4 KiB)
          Interrupt:185 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:12:17:73:6F:BF  
          inet6 addr: fe80::212:17ff:fe73:6fbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32222 (31.4 KiB)  TX bytes:202592 (197.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Firstly - should the Wireless device show as "eth1"?
Secondly whey is it coming up at 11MB/s & not getting an address from DHCP even though the router is set to do so? It looks to me like the device isn't being set up correctly but I cannot see where to configure it.

Can anyone help please?

---

### Post by teaker1s on 2007-01-21
it's a minor config file issue you should get up and running by

install
[COLOR="Red"]network-manager-gnome[/COLOR]

this can be installed from alternate.iso and using either apt or synaptic to add cdrom source if you have no wired internet connection


now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key
_

---

