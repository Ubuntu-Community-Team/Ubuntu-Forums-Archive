---
title: "My wireless went away"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2007-07-02
Hi,

Any experts out there on wireless cards? I had installed a network manager substitute program called wicd to try and troubleshoot another problem I was having, but needed to uninstall it and reinstall network manager (I won't get into details here, partially cause I can't reconstruct everything). Now I am unable to see any wireless network at all. If I pull down my network manager menu, I only get the options for wired networking and manual config, no wireless. Roaming mode is enabled and I've been through all the help on the ubuntu official docs. My chipset is supported (Realtek RTL8187) and I was connecting to wireless just fine before I decided to screw with things I don't know enough about.

For what it's worth, here's my output for iwconfig:

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 IEEE 802.11g Frequency:2.412 GHz
RTS thr:off Fragment thr=2346 B

wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

For the sake of brevity, I've attached a copy of the output of lsmod as well.

Thanks in advance from a frustrated noob

---

### Post by imdano on 2007-07-03
If you run "iwlist scanning" in a console does it find wireless networks?  If yes, your card is working and the problem is most likely with network manager.  Did you completely reinstall it (both network-manager and network-manager-gnome)?

---

### Post by scholzilla on 2007-07-03
Thanks for the response, imdano. As it turns out, I don't think the card is working....Here is the output of iwlist:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results

Any suggestions on what to do next? As I said before, this card worked fine before I went fooling around with wicd and then followed a network manager's advice to fool with the wpa_supplicant.conf file. And to answer your question, I believe I did do the full install. I handled it from synaptic and reinstalled the following:

network-manager
network-manager-dev
network-manager-gnome
network-manager-openvpn
network-manager-pptp
network-manager-vpnc

Thanks!

---

### Post by scholzilla on 2007-07-03
btw: sorry to all for double posting this message on the absolute beginner board. I'm, well, an absolute beginner.... Won't do it again.

---

### Post by kevdog on 2007-07-03
What is the following output:
lshw -C network

How did you install drivers in the first place?

---

### Post by alan34 on 2007-07-03
Hi your wireless card driver might be blacklisted.

In terminal

cd /etc/modprobe.d

sudo cp blacklist blacklist.backup

sudo gedit blacklist

Should see this at the end without the # in front of 'blacklist r8187' add a # as below

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
#blacklist r818x
#blacklist r8187

Reboot your system, then in network manager your wireless should be there ( it was for me).

You may have to add an extra charactor to your ESSID to get it to work I did with
a Realtek r8185 chipset like

youressid becomes youressidX just a bug?????

Good Luck

---

### Post by scholzilla on 2007-07-03
Thanks for the responses. Alan34: I did see the output you mentioned on the blacklist after following your instructions. After rebooting, though, I still have the same problem. I've now tested this from multiple APs that should work, so I know the problem is on my end.

kevdog: I don't recall how I installed the drivers originally. If you go the [Realtek website]("http://www.realtek.com.tw/downloads/searchView.aspx?keyword=rtl8187"), they have two separate drivers, one for 8187L and one for 8187B. I don't recall chosing between these (and I really don't know the difference). As I recall, my wireless just worked out of the box when I first installed ubuntu. I really don't want to reinstall, of course. Output for lshw -C network is

 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=72.211.155.107 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c0200000-c0203fff ioport:a000-a0ff irq:16
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Your continued patience with my ignorance is greatly appreciated.

---

### Post by alan34 on 2007-07-04
The RTL8187L file looks the latest if you download it and open with Archive Manager
(just double click) then extract to a directory.

In a terminal
 cd rtl8187_linux_26.1025.0328.2007/

 gedit ReadMe.txt

have a good look but to me you have to in the same  rtl8187.......... directory in a terminal

1) sudo ./makedrv
2) sudo ./wlan0up

try sudo lshw -C network then to see if you have a driver for the card loaded
mine looks like
 *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@03:03.0
       logical name: wlan0
       version: 20
       serial: 00:12:0e:62:42:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.0.2 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b/g linked
       resources: ioport:dc00-dcff iomemory:dceffe00-dcefffff irq:23

I would then reboot to see if your wireless is in network manager then if not
look further down the ReadMe file and you will have to use the sudo iwconfig wlan0
commands to set your ESSID parameters etc

good luck again

I'm about at my limit now hope you find your card in network manager this time.
Your not your own it took me 2 weeks and a new card to get it to work in Edgy

---

### Post by scholzilla on 2007-07-04
Thanks Alan34. I decided to ditch network manager all together and went back to wicd. Now everything works fine. It's frustrating not to know what went wrong to begin with, but that's linux...

---

