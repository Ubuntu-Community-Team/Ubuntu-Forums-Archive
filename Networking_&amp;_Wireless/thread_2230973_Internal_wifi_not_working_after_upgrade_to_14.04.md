---
title: "Internal wifi not working after upgrade to 14.04"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by prakash-trivedi on 2014-06-22
I have Dell Latitude E6410

Until I did the upgrade to 14.04 internal wireless was working fine. Now its not working. If I plugin a isb wifi adapter then it comes up and works fine.

Following are outputs of some of the commands that usually are being asked on the forum to check.

interfaces:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#auto eth0
#allow-hotplug eth0
#iface eth0 inet dhcp


auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf


iface default inet dhcp


#Below lines were added to make eth0 work with local LAN with RPIs
#auto eth0
#allow-hotplug eth0
#iface eth0 inet static
#address 192.168.1.100
#netmask 255.255.255.0
----end of interfaces file------
I commented out eth0 in hopes of getting wlan0 to work

lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:08:54:15
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:e9600000-e961ffff memory:e9670000-e9670fff ioport:8020(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:23:51:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=9.221.4.1 build 25532 ip=10.0.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:e6e00000-e6e01fff


lspci -v
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e6e00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)

I did try to search the forum but could not find anything that helped in my case.

Thank you,
pk

---

### Post by varunendra on 2014-06-26
Welcome to the forums Prakash!

Why are you using WPA Supplicant and 'interfaces' file to control the wireless? It is a server install without GUI? If not, you should be using Network Manager which is the default choice to manage wireless.

If there is a reason for not using NM, please explain it to us. If there is none, you should try reverting the 'interfaces' file to default, and purge WPA Supplicant, then use NM to manage the connection (after a reboot).

For details of your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

