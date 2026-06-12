---
title: "[SOLVED] BUG: unable to enable wireless network card"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by eckeroo on 2008-08-08
I was following the sticky thread: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

when I got the following error after typing the command to enable my network card [sudo ifconfig wmaster0 up] : "SIOCSIFFLAGS: Operationnot supported"

This means the ifconfig program can't enable my wireless network card! Nightmare.

I'm using Edimax [Ralink] EW-7128G network card. The driver rt61pci is installed.

I followed the sticky thread after my wireless options disappeared from the Network Manager. My problems started when I was trying to get Network Manager to see my new wireless network [WPA2 encoded]. It could see the other networks fine, so I tried to manually configure to my new SSID, the Network Manager then froze, I did a halt command, rebooted, and then the wireless function ceased on Network Manager.

Whatever disabled the network card, I now believe a bug or incompatibility with the rt61 driver means that Network manager cannot enable the network card.

What are the options available to me? It did work before. I don't want to reinstall the whole of Ubuntu 8.04.

Cheers

P.S Funnily enough, Network Settings can still be accessed from the GUI [although it runs very slowly] and I'm able to configure to another wireless network (another slower network, but with a WEP encryption only) expect it thinks my wireless card is on wlan01 instead of wmaster0 as per 'lshw -C network'.

---

### Post by 4lc0h0l1c on 2008-08-08
> **eckeroo said:**
> I was following the sticky thread: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

when I got the following error after typing the command to enable my network card [sudo ifconfig wmaster0 up] : "SIOCSIFFLAGS: Operationnot supported"

This means the ifconfig program can't enable my wireless network card! Nightmare.

I'm using Edimax [Ralink] EW-7128G network card. The driver rt61pci is installed.

I followed the sticky thread after my wireless options disappeared from the Network Manager. My problems started when I was trying to get Network Manager to see my new wireless network [WPA2 encoded]. It could see the other networks fine, so I tried to manually configure to my new SSID, the Network Manager then froze, I did a halt command, rebooted, and then the wireless function ceased on Network Manager.

Whatever disabled the network card, I now believe a bug or incompatibility with the rt61 driver means that Network manager cannot enable the network card.

What are the options available to me? It did work before. I don't want to reinstall the whole of Ubuntu 8.04.

Cheers

P.S Funnily enough, Network Settings can still be accessed from the GUI [although it runs very slowly] and I'm able to configure to another wireless network (another slower network, but with a WEP encryption only) expect it thinks my wireless card is on wlan01 instead of wmaster0 as per 'lshw -C network'.
Hello,
I got my Ralink card working after a lot of work so I'm trying to help everyone else out.  I wrote a detailed guide: [http://ubuntuforums.org/showthread.php?t=884247](http://ubuntuforums.org/showthread.php?t=884247)

I would recommend not using network manager.  All of the other network manager tools I used seemed to function better.  Also, was your wireless working *before* network manager froze?  When I saw things like "SIOCSIFFLAGS: Operationnot supported" it usually meant it wasn't recognizing my network interface correctly; in your case, I think wmaster0 is no longer your wireless interface.  What happens if you run "sudo ifconfig wlan0 up"?  What is the output of ifconfig and iwconfig?

It might be your settings in /etc/network/interfaces, if network manager froze and you had to reboot.  I have read that the way network manager configures that file renders it incompatible with other network managers.

If anyone sees I am giving incorrect information, feel free to correct me.

---

### Post by eckeroo on 2008-08-09
My wireless was working before my network manager froze, although it couldn't detect my new WPA2 encoded broadcast.

Here is the output of the ifconfig command, before and after enabling wlan1 [sudo ifconfig wlan1 up], also the output of iwconfig is at the end.

Note that I have an ethernet card installed on eth0. My wireless is currently set for my old WEP network [ssid: user].

It looks very odd that I have something on lo, wlan1 and wmaster0.

I'm now going to check out your thread.

```
output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:50:bf:6d:b0:4f  
          inet6 addr: fe80::250:bfff:fe6d:b04f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:24
          collisions:204 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:936 (936.0 B)
          Interrupt:10 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82504 (80.5 KB)  TX bytes:82504 (80.5 KB)

output of ifconfig after "sudo ifconfig wlan1 up":

eth0      Link encap:Ethernet  HWaddr 00:50:bf:6d:b0:4f  
          inet6 addr: fe80::250:bfff:fe6d:b04f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:24
          collisions:204 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:936 (936.0 B)
          Interrupt:10 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82504 (80.5 KB)  TX bytes:82504 (80.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1f:1f:03:19:16  
          inet addr:192.168.0.93  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:554074 (541.0 KB)  TX bytes:13165 (12.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-03-19-16-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"user"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:40:96:A2:01:A7   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=59/100  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

output from 'lshw -C network':

  *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 00
       serial: 00:50:bf:6d:b0:4f
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 module=ne2k_pci multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wmaster0
       version: 00
       serial: 00:1f:1f:03:19:16
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.93 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g

Output from 'sudo dhclient -r wmaster0':

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

Output from 'sudo ifconfig wmaster0 up':

SIOCSIFFLAGS: Operation not supported
```

---

### Post by huxterby on 2008-08-09
Hi eckeroo,

I had some issues with network-manager not connecting, so I switched to wicd.
[http://huxterby.wordpress.com/2008/08/06/wicd-linux-network-manager-replacement/](http://huxterby.wordpress.com/2008/08/06/wicd-linux-network-manager-replacement/)

I also have a Ralink (with the RT61) card on one of my other machines that runs Debian, and it works fine with Wicd.

I found this RT61 Howto helpful:
[http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+rt61](http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+rt61)

Huxterby

---

### Post by 4lc0h0l1c on 2008-08-09
Ok I want to make sure I understand this ... you *are* able to connect to a wireless network through your old network?

I think the network manager may have reassigned your wireless interface and now you have two conflicting interfaces for the same wireless device.  Notice that wmaster0 and wlan1 have the same hardware address?  And bringing up wlan1 also shows wmaster0.  Check your /etc/network/interfaces to see if there are multiple wireless interfaces listed there, and the output of dmesg could be helpful to see what drivers were successfully loaded.  "lshw" shows that you *do* have an IP on wlan1 with your ralink driver, so we know it works.

My experiences say: 

-the problem may be related to the WPA2 encrypted network.  Does "iwlist wlan1 scan" show the network you're trying to connect to?  I had to make sure wpa_supplicant was loaded before I could connect to any networks even though I could see them and my driver was loaded fine.

-driver conflict: run lsmod.  Are there other modules loaded that look like they have to do with wireless?  I don't know if network manager has the capability to alter drivers in use.  I would try "sudo apt-get remove network-manager" and instead install wicd or rutilt.

If you can see wireless networks on a scan, try using the command line to connect, manually entering the essid, encryption mode, psk, etc.  I think I have instructions for that in my thread around step 5 or 6, if not I can track that down.  I was able to connect that way before I got it working with any network manager utilities.

---

### Post by eckeroo on 2008-08-09
> Ok I want to make sure I understand this ... you *are* able to connect to a wireless network through your old network?

Yes, but Network Manager wouldn't show any of the available networks as it did before it crashed! I have two networks I can choose from: a slow WEP encoded SSID that works; or a fast WPA2 encoded SSID. The WEP one I can connect to, but not the WPA2.

Seen as I could get a connection, I installed Wicd. This made the wireless networks visable again (hooray!) but still could not connect to my WPA2 SSID.

I had a look at the dmesg output, nothing there indicates any wireless drivers. The output of lsmod did show the three rt61pci files.

I know Wicd must read some sort of configuration file as it was able to connect to the WEP SSID without me having to enter the WEP key. I would like an answer as to why 'ifconfig -C network' shows my wireless card connected on wmaster0 whereas iwconfig shows it on wlan1.

I switched off my computer, removed my wireless card, restarted Ubuntu , switched off again, reinserted my wireless card and restarted my ubuntu. Now when I check 'ifconfig -C network', the wireless card on wmaster0 is enabled.

I would be interested to know how to modify the configuration file manually. That may provide some more insights.

cheers

---

### Post by 4lc0h0l1c on 2008-08-10
Again, I would recommend uninstalling network-manager.

The man pages for Wicd say that it reads your system network configuration, which would be the same thing network-manager uses.  The other configuration files it talks about in the man for wicd, as far as I can tell, control the options for the program and are automatically set when you use the GUI anyway.

Since you are able to connect to a WEP network on that interface, you know you have connectivity.  The problem is with the configuration for WPA.  Are you using wpa_supplicant?  Check /etc/wpa_supplicant/wpa_supplicant.conf.  Make sure the WPA settings for your wireless network are in there.

---

### Post by eckeroo on 2008-08-13
I checked the directory etc/wpa_supplicant and only found only two files in there [functions.sh  ifupdown.sh] and no wpa_supplicant.conf

According to the synaptic package manager, wpasupplicant has been installed.

How do I go about making sure it's installed?

---

### Post by eckeroo on 2008-08-14
I've now got my EW-7128G with WPA2 encryption to work.

I followed this thread: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) correctly this time. The first time I tried to follow this thread, I hadn't installed the windows driver correctly and had to abandon ndiswrapper and try and get the Linux driver for this card to work instead. Unfortunately, the rt61pci driver doesn't work with WPA2. So it was back to ndiswrapper.

To get the EW-7128G card to work, you need to install Wicd, then follow the above thread and install ndiswrapper/wpa_supplicant. Then in Wicd, preferences, WPA supplicant driver: select wext.

And then it worked! I can now connect to my fast WPA2 encrypted SSID network.

Incidentally, I ran lshw again, and now my wireless network card appears on wlan1 and not wmaster0. I believe the Linux rt61pci driver is buggy. However, the source code for it is available, shame I don't know any coding, otherwise I may be tempted to have a nosey at the source code and see where the bug lies.

Cheers :)

---

### Post by eckeroo on 2008-08-14
Spoke too soon.

Whe I did a restart, my whole system crashed.

On start-up, all that appears is a beige screen with a white square on the top left hand corner.

I believe this problem occured once I had selected 'automatic connection' to my SSID on the Wicd seetings.

When I go to recovery mode, I see the 'networks' file fail. I cannot use gedit in the recovery console to fix it. How can I disable wicd?  What is the non-GUI file editor available to me? Otherwise, I'm going to have to do full re-installation of Ubuntu. 

:(

---

### Post by eckeroo on 2008-08-16
Right.

I reinstalled Ubuntu.

Followed this thread:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) 

then this thread (I opted for the mixed WPA/WPA2 DCHP setting):

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Bingo.

:cool:

---

