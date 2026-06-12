---
title: "intel pro wireless 2200bg --tried about everything"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by ronenc on 2008-09-30
Hi,
I'm a total linux noob so please excuse me if I am being slow.
I looked about everywhere for a solution but I still can't get my wireless adapter to work. I have a wireless router at home (and several others from the neighbours) and i can't find any of them! I tried every possible way to install the drivers (although as much as I understand it they are already installed).These are the results of what i got this far:
when I put in 
> $iwconfig
i get this:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


when I put in:
> sudo lshw -C network
I get:
>   *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 05
       serial: 00:13:ce:f1:8d:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=32 link=no maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 78
       serial: 00:e0:91:0d:41:ab
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.124 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s


if anybody can help I will be most appreciative,
thank you


btw - running Ubuntu 8.04

---

### Post by jmbargar on 2008-09-30
Your wireless interface is wlan0, so all you have to do is configure this interface with the apropiate values using the frontend that you can find in the System -> Administration -> Network menu, available in Gnome desktop.

Good luck!

---

### Post by ronenc on 2008-09-30
hi jmbargar
thanx for the quick replay, i tried what you said (even added a photo just to make sure i understood correctly), but it still won't work. The wireless adapter searches for the network for a while and then when it's connected there is no internet nor network connection available... is there another way?
[IMG]http://img360.imageshack.us/img360/1336/networkig4.png[/IMG]

Sorry the image is in Hebrew (but i guess you can figure out what I mean).

---

### Post by ronenc on 2008-10-01
Has anyone an idea of what to do? I'm really frustrated...

---

### Post by jmbargar on 2008-10-01
I have an intel pro wireless 2200bg like yours and I have no problem related with the module that manage it in Ubuntu, you seems either with it according to the iwconfig output that you have sent in your post.

If you use wpa2 and you have a dhcp server running in your router, I suggest you configure your wireless connection using network-manager. Usually, this tool is installed in Ubuntu by default, in any case you can install it easily using Synaptic Package Manager or typing something like this:

> sudo apt-get install network-manager-gnome

Good luck!

---

### Post by jj662 on 2008-10-27
I am having the same thing goingon. My Wired connection is working great, but the wireless is not cooperating.

I have the Intel PRO/Wireless 2200BG [Calexico2]Network Connection [rev5] installed per Ubuntu. This seems to line up with the hardware that this HP nc6220 has noted on it&#347; tech support site per the extended model number.

I did the same Terminal window commandsthat were done earlier in this string.

jeffj@HPLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"EDGEMONT"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A6:E8:98   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=79/100  Signal level=-50 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:14169  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


jeffj@HPLaptop:~$ sudo lshw -C network 
[sudo] password for jeffj: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:b0:30:c3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751m-v3.29a ip=192.168.0.105 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:17:7a:d3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:bf:88:24:ad:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

jeffj@HPLaptop:~$ sudo apt-get install network-manager-gnome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  libarts1c2a kdelibs4c2a libartsc0 kdelibs-data liblualib50 libavahi-qt3-1
  libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


EDGEMONT is the name of my home router.
When Windows was installed on this same HP Laptop, the wireless worked fine with this router.

I am very new to Linux. This install is only a few days old on this machine. I installed Unbuntu 8.04, and under the Network configuration I could at least see my home router, but it wouldn´t go ahead and connect.It would not appear in the list of available networks. Last night I updated to  8.10 in an effort to see if that would work better.
Same basic problem, but this time it won´t browse since everything is now under the Network Connections applette. 

So,
what do I do next or where do I go from here??
Sorry for the long thread.
JeffJohnson
Portland, OR

---

### Post by bobromeo on 2008-10-31
> **jmbargar said:**
> I have an intel pro wireless 2200bg like yours and I have no problem related with the module that manage it in Ubuntu

Mine worked just fine for a couple of upgrades, but now after upgrading to Intrepid (8.10/2.6.25-2-386) Nothing !
> *-network:0 UNCLAIMED   
description: Network controller
product: PRO/Wireless 2200BG [Calexico2] Network Connection

Have you upgraded ?
{Even my sound is gone:(}

---

### Post by trantloveazuen on 2008-10-31
I have the same wireless card and have instaled Ubuntu 8.04.1 and i am having trouble conecting to my home network :/ Its WPA encrypted and it works fine on my Windows Xp. My wpa_supplicant.conf is the following

###############################################

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
ssid="TranTNetwork"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="password123"
}
###############################################

in order to conect i do:
1- sudo iwconfig eth1 essid TranTNetwork
2- sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -B
3- dhclient eth1

and in 3 after some line i get :

No DHCPOFFERS received.

what can i do to fix this?


Regards

---

### Post by aasmith on 2008-11-02
**This might help...**

Upgraded to Intrepid 24 hours ago, and promptly lost both sound and wireless.  Tried to use modprobe in order to activate ndiswrapper, which had worked before when it was disabled--but kept getting this annoying "module not found" error.  So I went under the assumption that I was missing the module, and searched for packages under Synaptic.  Added one called "linux-restricted-modules," and when I rebooted, my wireless was back.  As an added bonus, sound came back too.

Hope that helps someone.

Adam

&#1513;&#1500;&#1493;&#1502;
:)

---

### Post by jonasbuntu on 2008-11-12
Be sure ubuntu-modules is installed for your running kernel. I did everything I can think of short of completely reinstalling. After some searching around in the synaptic package list for kernel stuff, noticed the kernel I upgraded from had it's ubuntu-modules package installed, but the running kernel did not.
Wireless started working as expected. Access points appeared in the manager list and iwconfig showed an interface as it should. All without rebooting. Linux luv once again.\\:D/

---

