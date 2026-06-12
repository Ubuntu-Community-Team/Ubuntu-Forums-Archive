---
title: "Wireless Card &amp; WPA Supplicant"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Malviolent on 2008-07-23
Hey all,

I have an Atheros wireless card (currently using ndiswrapper with the AR242x driver) and I'm having trouble connecting wirelessly.  The network manager won't connect to any networks.  iwlist scan doesn't list any found networks under wlan0, although wlan0 does show up. I tried using wicd and it recognizes that I have wlan0 turned on, but it can't find any wireless networks either.

I know how to configure my wpa_supplicant.conf if I need to, but I can't seem to find it!  I'm using ubuntu 8.04 hardy, and it's not in my /etc/ folder.  In fact, find / | grub doesn't show it anywhere!  I do have my wpasupplicant package up-to-date from the aptitude repo.

Is there something wrong with my driver?  ndiswrapper -l yields:

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

iwlist wlan0 scan yields:

wlan0     No scan results

Is there something wrong with my wpasupplicant package, as I cannot find a wpa_supplicant.conf?

Any help would be awesome, thanks!

---

### Post by imdano on 2008-07-23
Wicd keeps the wpa_supplicant config files in /opt/wicd/encryption/configurations.  They're named after the mac address of the access point they're for.

But it does look like you might be having a driver problem.  You have ndiswrapper intalled but it looks like ath_pci is still active.

---

### Post by Malviolent on 2008-07-23
My ath_pci driver is blacklisted in /etc/modprobe.d/blacklist. I'll check for the wicd supplicant, but I don't think the wpa_supplicant is the issue.  It should at least be able to find an AP within range.

Any other idea as to why I can't pick up any wireless networks, or why my driver wouldn't be working correctly?  I'm using the ar5211.sys/net5211.inf XP driver for the ar5007eg, and my lspci lists:

05:00.0 Ethernet controller: Atheros Commmunications Inc. AR242x 802.11abc Wireless PCI Express Adapter (rev01)

The driver was obtained as per this thread: [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

Also, as another update, /etc/wicd/ does not have an /encryption/ directory.  Only /data/ misc.pyc and networking.pyc.

---

### Post by PinkFloyd102489 on 2008-07-23
Check /etc/default/wpasupplicant. If there's no such file or nothing in the file, run this command:

```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Then restart for good measure.

---

### Post by imdano on 2008-07-23
> **Malviolent said:**
> Any other idea as to why I can't pick up any wireless networks, or why my driver wouldn't be working correctly?  I'm using the ar5211.sys/net5211.inf XP driver for the ar5007eg, and my lspci lists:

05:00.0 Ethernet controller: Atheros Commmunications Inc. AR242x 802.11abc Wireless PCI Express Adapter (rev01)Whats the output of the following?
```
sudo lshw -C network
iwconfig
ifconfig -a

```

> Also, as another update, /etc/wicd/ does not have an /encryption/ directory.  Only /data/ misc.pyc and networking.pyc.What version of wicd are you using?  Also, not sure if what you have above is a typo, but it should be /opt/wicd, not /etc/wicd.

Sometimes uninstalling NetworkManager causes interfaces to disappear, I think its because NM edits a couple of config files when it gets uninstalled (not 100% sure about that though).  Usually they're still listed in ifconfig -a, and you just need to run a sudo ifconfig <interface> up for it to come back.

---

### Post by Malviolent on 2008-07-23
pinkfloyd:
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
did nothing. :(

The file did not exist, and after rebooting no changes occured.

imdano:

lshw -C network spits out:

```

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:37:34:9e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:c5:4f:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

looks like the driver is installed.  unfortunately, when I try
```
iwlist wlan0 scan
```
it takes ~3 seconds to return "No scan results."

My wicd version is 1.4.2 from the [http://deb.wicd.net/](http://deb.wicd.net/) repo.

Looks like I was accidently looking in my /etc/ folder; however, /opt/wicd/encryption/configurations/ is empty.

ifup wlan0 also failed to find a working lease.

Thanks for all the help so far guys, I really appreciate it.

---

### Post by imdano on 2008-07-23
You forgot the ifconfig -a, that one's important.  Although based on what I'm seeing, wlan0 is there and probably up, its just not finding any networks.  My guess is it's one of two things:
a) There aren't any wireless networks around.
or
b) Your driver isn't working.

My money is on b.

---

### Post by Malviolent on 2008-07-23
Oh right, I did do ifconfig -a and wlan0 was listed as the third interface after eth0 and lo.

There are wireless networks around as I am running a WPA2 TKIP router literally 2 feet from the laptop, among other routers in the vicinity (apartment complex).

Any ideas on how to get this driver to work?  ndiswrapper seems to be functioning (for the most part) and it lists ndiswrapper as the driver with the associated XP driver.  I'm clueless.

---

### Post by Malviolent on 2008-07-23
Okay, my iwconfig output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:37:34:9e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe37:349e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:368680 (360.0 KB)  TX bytes:65623 (64.0 KB)
          Interrupt:218 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57012 (55.6 KB)  TX bytes:57012 (55.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:c5:4f:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:f8000000-f8010000 

```

Something strange happened.  After rebooting, running these two commands (which should have no effect on the interface itself), wicd found a list of networks!  Then, after rebooting again, I found no networks!  I've even tried running both commands, and those were the only two commands that I executed.  Makes no sense!  But I know I'm getting close ;)

---

### Post by Malviolent on 2008-07-24
I'm getting mixed results now.  Sometimes it will discover wireless networks, sometimes it won't.  It's very flaky and I am not sure why it would alternate without any system changes.

When I discover wireless networks (about 20-30% of the time), wicd freezes after I click Connect.  Not really sure what's going on, or why it isn't discovering these networks half the time in the first place.

---

### Post by Malviolent on 2008-07-24
Have I stumped you guys yet? ;)

Anyway, when the wireless networks do magically appear, I found that if I set a static IP address, wicd thinks it connects.  It gives me a message "Connected to AP at ## (192.168.1.x)" however, I can't seem to ping out to anything and I don't really seem connected at all.

---

### Post by imdano on 2008-07-24
That's just an issue with wicd.  If an ip address shows up in iwconfig and your signal strength isn't 0, wicd says you're connected.  You can do this by assigning a static ip without actually being connected to the internet.

I really think you're dealing with a flaky driver or hardware.  It's definitely an issue that is below the level a network management app works at.

---

