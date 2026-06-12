---
title: "strange wireless problem..."
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by jamesbeat on 2007-05-01
Hi everyone, I'm new to the forums.
I have been using ubuntu as my only operating system for just over a year now, and have never had a problem before.
Unfortunately, I spilled a drink on my laptop the other day and killed it :o(
I bought a new one yesterday and installed 7.04 on it. I also installed it on my girlfriend's laptop.

My girlfriend's machine works perfectly (which is how I am able to post this!) but on mine, I cannot get wireless working.

In network settings, i have two cards show up: 'Wireless connection (wmaster0)' and 'Wireless connection (wlan0)'

Both have a '-' sign next to them and say 'roaming mode enabled' underneath. I can't click the minus symbol to make it into a plus unless I go into properties and deselect 'enable roaming' and put my settings in manually.

Neither of these work, but strangely if I keep the settings on 'roaming mode enabled' I can see the available wireless connections (my own and my neighbour's) when I click on the network icon.

If I then click on my network, it says it is connected but has (0%) next to it and I can't connect to the internet.
If I click on my neighbour's network, it asks me for a password, so it must be communicating something.

When I use lspci I can't see any wireless cards! I get:

Ethernet controller: realtek semiconducter co., ltd. RTL-8139/8139C/8139C+ (rev 10) 

but from what I can gather this is not a wireless adapter.
I was going to try and figure out how to use ndswrapper but I don't have a clue what driver to use etc.

It must be seeing the wireless card because I can view the available networks, but I'm afraid I'm a bit of a noob and I am stuck!

If it helps, the laptop is just the cheapest one I could find in Curry's- an E system (or EI systems depending on which label you read!) 3090

Please help me because I REALLY don't want to go back to using windows!

---

### Post by spd106 on 2007-05-01
Interesting...

wmaster0 indicates that it is or at least attempting to use the new mac80211 wireless stack. However that won't really help diagnosing the problem.

Could you please post the output of these commands
```
lspci
``````
sudo lshw -class network
``````
iwconfig
```
Thanks

---

### Post by jamesbeat on 2007-05-01
Ok, here they are...





lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)




sudo lshw -class network:

  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:5a:b1:f8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:2000-20ff iomemory:b0200000-b02000ff irq:17
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:04:26:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



I'm afraid I don't know what to make of all this, but I hope you do!
Thanks for helping.

---

### Post by jamesbeat on 2007-05-01
Hmm, seems that the board has turned some of that output into smileys :o
That's a bit inconvenient...

---

### Post by spd106 on 2007-05-01
For future reference it's usually best to wrap output like this in code tags, see the hash symbol at the message entry box. You can also select to disable smilies in the additional options section a little further down.

Now.. I can't see any wifi device listed either, this leads me to suspect that you have an internal usb card. Try this command instead
```
lsusb
```

There is a good chance that you have a card that's using the [zd1211rw]("http://www.linuxwireless.org/en/users/Drivers/zd1211rw") driver. If so you are using fairly cutting edge stuff, so it might not work 100%.

The output of this command may also give some clues as to what's going on. Be advised that it is rather long and you only really need to examine the second half for parts about the wireless driver.
```
dmesg
```

---

### Post by jamesbeat on 2007-05-01
Ok, I found it! It's an internal USB device- here's what it came up as:

6877 micro star international

Unfortunately I can't seem to find any info on it. I googled '6877 micro star international ubuntu' and most of the results were in foreign languages. The only pertinent result I got was a thread like this one with a guy asking the same thing! No replies though....

Is this any help?

---

### Post by jamesbeat on 2007-05-01
....And here's the output of dmesg:
```

wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: cannot create symlink to default key
wlan0: cannot create symlink to default key
wlan0: cannot create symlink to default key
eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
wlan0: Initial auth_alg=0
wlan0: authenticate with AP 00:00:00:00:00:00
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: Trigger new scan to find an IBSS to join
wlan0: starting scan
wlan0: failed to set channel 1 (2412 MHz) for scan
wlan0: failed to set channel 2 (2417 MHz) for scan
wlan0: failed to set channel 3 (2422 MHz) for scan
wlan0: failed to set channel 4 (2427 MHz) for scan
wlan0: failed to set channel 5 (2432 MHz) for scan
wlan0: failed to set channel 6 (2437 MHz) for scan
wlan0: failed to set channel 7 (2442 MHz) for scan
wlan0: failed to set channel 8 (2447 MHz) for scan
wlan0: failed to set channel 9 (2452 MHz) for scan
wlan0: failed to set channel 10 (2457 MHz) for scan
wlan0: failed to set channel 11 (2462 MHz) for scan
wlan0: failed to restore operational channel after scan
wlan0: scan completed
wlan0: cannot create symlink to default key
usb 5-2: new high speed USB device using ehci_hcd and address 3
usb 5-2: new device found, idVendor=058f, idProduct=6331
usb 5-2: new device strings: Mfr=1, Product=2, SerialNumber=3
usb 5-2: Product: Mass Storage Device
usb 5-2: Manufacturer: Generic
usb 5-2: SerialNumber: 058F0O1111B
usb 5-2: configuration #1 chosen from 1 choice
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
  Vendor: Multi     Model: Flash Reader      Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 4022272 512-byte hdwr sectors (2059 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 4022272 512-byte hdwr sectors (2059 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
 sdb: sdb1
sd 2:0:0:0: Attached scsi removable disk sdb
sd 2:0:0:0: Attached scsi generic sg1 type 0
usb-storage: device scan complete

```

---

### Post by spd106 on 2007-05-02
Unfortunately the dmesg log has been flooded with error messages so the bash pager was exhausted. Could you please open the /var/log/dmesg file and post from the beginning down to the error messages?  In particular you are looking for the part where the driver is loaded.

It will probably look like this with several mentions of wlan0 and a mac address, though obviously it won't be using ndiswrapper or bcmwl5.
```
[17179592.868000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
[17179593.024000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[17179593.028000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179593.028000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17179593.808000] wlan0: ethernet device 00:11:50:xx:xx:xx using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
[17179593.808000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179593.808000] usbcore: registered new driver ndiswrapper

```
This is important as if we can't fix the driver then it will have to be removed (blacklisted) to allow ndiswrapper to work instead.

Also the output of lsusb would be appreciated in order to confirm the usbid.

I don't seem to be able to find much information about this wifi adaptor either, which usually indicates that it is probably rather new. This thread seems to be active and worth watching [http://ubuntuforums.org/archive/index.php/t-313674.html](http://ubuntuforums.org/archive/index.php/t-313674.html)

---

