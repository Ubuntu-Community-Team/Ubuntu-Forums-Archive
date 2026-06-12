---
title: "Gutsy - Cannot obtain IP address - i680 chipset - forcedeth"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by efface on 2007-09-02
I am observing a problem that is identical to the one in this post:

[http://www.linuxforums.org/forum/linux-networking/65765-cannot-get-dhcp-work-ubuntu.html](http://www.linuxforums.org/forum/linux-networking/65765-cannot-get-dhcp-work-ubuntu.html)

I see no solution though and google has provided no working solutions.

I am using an ASUS p5n32 board with an nforce chipset.  Using the onboard NIC.

I have edited my interface file, turned ipv6 off, tried setting a static IP to my router.  I tried bypassing my router to my modem, all to no avail.

I used Ubuntu several months ago and everything worked fine with the same hardware so I believe there is a configuration problem.

I have been to #ubuntu and have received no help in the 2 hours i was in the rooom so now I come to you.

Thanks for reading my post!

---

### Post by noob12 on 2007-09-02
Can you post the output of these

```

sudo lshw -C network

ifconfig -a

# Note: substitute the appropriate interface in this command if it is is not eth0
sudo ethtool eth0

```

---

### Post by efface on 2007-09-02
I cant really post all the data from those commands as my ubuntu box is not online or networking, i am posting from another comp.

lshw returned info about a wireless adaptor and ehtool just listed the capabilities of the NIC, nothing out of the ordindary.

ifconfig shows the devices and shows that there isnt an IP or any activity

I am a lil concerned that the lshw returned info on a wireless adaptor as i dont plan on using it though its onboard, should it be showing my NIC?.

---

### Post by efface on 2007-09-02
Ok I got wireless to work on the ubuntu box so now I can post the logs you wanted.  I still wish to get lan working.  Here you go:

eth0      Link encap:Ethernet  HWaddr 00:18:F3:B7:05:90  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:123 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F3:B7:05:90  
          inet addr:169.254.7.8  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49664 (48.5 KB)  TX bytes:49664 (48.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:0D:2C:10  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1674777 (1.5 MB)  TX bytes:282728 (276.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-0D-2C-10-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


efface@efface-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0d:2c:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11g


efface@efface-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0d:2c:10
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11g

---

### Post by noob12 on 2007-09-02
OK.  I'll try to walk you through some things to check below, but depending on where each thing leads your next steps may differ.  You may need to find a USB jump drive and transfer text across to the computer from which you are posting so that you can actually show the output.

The lshw should show both devices.  For the wired card, we expect a "configuration" line to indicate that the forcedeth driver has claimed the device.  If the device does not show up at all, you want to look at **lspci -nn** and **dmesg** to see if it is being detected or if there is boot-time problem with the PCI routing.  If the device shows up but UNCLAIMED, it's been detected, but the driver hasn't claimed it, either because you don't have it installed or loaded, or because it had trouble claiming it.

In the **sudo ethtool eth0** output you should see "Link detected: yes".  If not, you've got a cable problem or a device problem.  We'd need to resolve that to get any traffic out.

If the device is detected and claimed, you should see the interface listed in **ifconfig -a** output.  It sounds like you are seeing both.  You want to see the device UP with an assigned address.  If it is not UP, then you should first bring it up (using for example **sudo ifup eth0**).  

If it is up but doesn't get an address, check the config in **/etc/network/interfaces** and check what you see from the output of **grep dhclient /var/log/syslog**, which will tell you whether the DHCP interaction is succeeding or not, and may or may not give a clue as to why not.
Manual address and gateway configuration should also work if everything else is right.

---

### Post by noob12 on 2007-09-02
Can you post the output of **sudo ethtool eth0**

Note that if you are using Network Manager, then enabling the wireless will generally put your wired interface down.

I have to go, so won't be able to respond till late.

---

### Post by efface on 2007-09-02
a link was detected and the syslog showed nothing other than ailed dhcp attempts.

=/

Been working on this all day!

---

### Post by noob12 on 2007-09-02
In this situation as far as I can tell from these diagnostics, you should be able at least to set up an address manually.   You mentioned trying that already, but you might want to double-check.  Also while you're pinging your gateway, try tailing the kernel log to look for errors (**tail -f /var/log/kern.log**).  Note that you'll need to CTRL-C quit out of that command as it will just keep watching the log forever.

Also check **dmesg** for errors related to the ethernet card at boot.

---

### Post by efface on 2007-09-02
update....

checked /var/log/messages and i found that forcedeth is reporting no link during init

---

### Post by efface on 2007-09-02
Don't know why but I unplugged my comp for 10 minutes and turned it back on.....and it works....6+ hours working on this, multiple reboots....and removing the power fixes it...who would of thunk

---

### Post by noob12 on 2007-09-03
Great to hear you resolved your issue.  Are you dual booting with Windows by any chance?

---

