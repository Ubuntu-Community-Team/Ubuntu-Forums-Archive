---
title: "[SOLVED] Need to re-enter password to connect wireless"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by HalSF on 2007-11-16
'm running Xubuntu Gutsy on a Dell Inspiron 600m with an Intel PRO/Wireless 2100 card using WPA encryption. The only way I can get a wireless connection after booting up is to open Network Settings, go to Properties, and re-enter the password. Any idea how I can make my wireless work automatically upon startup?

Here's what I get in Terminal when I enter "sudo lshw -C network":

*-network:0
description: Ethernet interface
product: NetXtreme BCM5702X Gigabit Ethernet
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:0d:56:7c:a4:12
capacity: 1GB/s
width: 64 bits
clock: 66MHz
capabilities: pcix pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5702-v2.25 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
*-network:1
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:02:03.0
logical name: eth1
version: 04
serial: 00:04:23:a2:d6:a8
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.104 latency=32 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
__________________
Edit/Delete Message

---

### Post by tinycamp on 2007-11-16
r u using network manager???

```

tinycamp@itacate:~$ ps xa |grep nm-applet
 5901 ?        S      0:00 nm-applet --sm-disable   < --- this one
 8191 pts/1    R+     0:00 grep nm-applet

```that will help you automagically connect to the network, also, try editing /etc/network/interfaces, there you can keep a permanent config.

i prefer network manager.

---

### Post by HalSF on 2007-11-16
Thanks . . . I'll give your suggestions a shot.

---

### Post by HalSF on 2007-11-18
Success -- here's my quick problem-solving report. Hope this helps (and gives hope) to others.

The suggestion that did the trick was to try editing the /etc/network/interfaces file. I'm virtually brand-new to command-line computing in Ubuntu so this was a bit daunting, but I crossed my fingers and went forward.

After reviewing some of the posts at [http://ubuntuforums.org/showthread.php?t=571188&highlight=Network+Manager](http://ubuntuforums.org/showthread.php?t=571188&highlight=Network+Manager) and elsewhere on the forum, I was able to learn the significance of some of my key wireless config information such as my driver, SSID name, interface name (eth1), etc.  I then launched the Terminal and entered:

gksu mousepad [the default editor in Xubuntu] /etc/network/interfaces

For whatever reason there was a lot of bad info in this file; for example, the WPA1 password in the interfaces file was incorrect.  I typed in the correct password and interface name and also entered the correct shorthand for my driver [ipw] and the name of my SSID network, and saved the new version of interfaces. From that point on I've had a solid wireless connection every time upon booting Xubuntu Gutsy.

In addition to trying out the suggestion about editing the interfaces file, the key to figuring this out was a lot of trial and error. I tried installing the wpa_supplicant utility and configuring my network using the Network Manger [nm-applet] in the Terminal, but neither approach fixed anything. But I'm learning that these quixotic detours are actually essential; these failed attempts were also useful self-tutoring sessions to helped me grasp the key components of the wireless config and improve my facility in command-line land. 

Two final general observations: 

-- I have to agree with other observations (and enraged flames) here that the GUI implementation of network setup in Gutsy Gibbon is scandalously inadequate. You just have to go to the command-line to troubleshoot if you have problems, period.

-- Since WPA encryption is now incorporated in Ubuntu 7.10 (Gutsy Gibbon), there's a lot of seriously outdated stuff on the forum about using wpa-supplicant, which as far as I can tell is unnecessary and useless for configuring Gutsy.

---

### Post by Blutack on 2007-11-18
You could try using WICD
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Bit lighter than Network manager for an Xubuntu machine.

---

### Post by HalSF on 2007-11-18
Thanks for the WICD link; I'll definitely check it out.

---

### Post by victorcache on 2008-02-24
I'm another user with the same problem but I haven't found enough specifics in HalSF's post to solve it.  I'm also running xbuntu gutsy/7.10, on a Compaq Armada m300 laptop with D-LInk DWL-G650.  

My /etc/network/interfaces has 
************************************************************
/etc/network$ more interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface ath0 inet dhcp
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk 03663b701f2809a838fa4efa77f492a305ca1f0fa697bd3bdac05ceb33ab13ee
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <my_SSID>

auto ath0
********************************************

I edited the file with vi to set my wpa-psk passphrase in cleartext, but that didn't work and clearly it wants to store it encrypted.  

Any good references on the contents of the   interfaces   file?  I don't know enough about  the fields to tell it how to accept an unencrypted wpa-psk; man interfaces doesn't mention wpa or psk.  

Here's the wireless/ath0 output from ifconfig after I used  the GIUI to re-enter the wpa-psk

laptop-armada-m300:~$ ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:13:46:B6:3B:E7  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:feb6:3be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1789 errors:4 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2068100 (1.9 MB)  TX bytes:282158 (275.5 KB)

---

