---
title: "problem with installing wireless drivers"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by havivi on 2010-10-12
hello everyone.
I'm tring to active my USB wireless card, LevelOne WUA-0600 on my ubunto (zorin 64 bit vertion), but the linux does not recognize it. I'm realy new user of linux, and barely know where to begin, so every help will be appreciated.
thank you

---

### Post by Hippytaff on 2010-10-12
If you press Ctrl+Alt+t and input these commands, then copy and paste the output here, we can try to help. - may be worth going to system > network connections and clicking the wireless tab to see if your network is there first.

```

lsusb

```

```

iwconfig

```

```

lshw -C network

```

---

### Post by havivi on 2010-10-12
ok...
alt + ctrl + t didn't worked for me, so i entered the commands in the terminal and here are the results:

lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 148f:2770 Ralink Technology, Corp. 
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1b:fc:53:4d:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A ip=192.168.1.100 latency=0 multicast=yes
       resources: irq:29 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:11:6b:d8:7e:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

i looked in the control panel and the connection is there. i just can't connect to my wireless network.
In addition, the device work fine on windows, so the problam isn't with the device.
thanks

---

### Post by scrooge_74 on 2010-10-12
The problems usually are not the devices or the fact that they runs on Windows. Most of the time is either it dosent have a driver installed or there is no driver.

In your case you have a:

Bus 001 Device 007: ID 148f:2770 Ralink Technology, Corp. 

If you spend enough time around here you notice that a bunch of network cards from different "vendors" user the same chips inside so if there is a driver you are in luck, then is a matter of configuration.

Fast google search got me this:

[http://ubuntuforums.org/showthread.php?p=9236718](http://ubuntuforums.org/showthread.php?p=9236718)

Could be you need to blacklist something

---

### Post by Hippytaff on 2010-10-12
Ralink often cause problems in linux - might be driver issues...there's loads of stuff on the forums and in the documentation. you need to look into ndsiwrapper and search using the ralink driver name. you can find this out by putting

```

lsusb

```

will be called 'ralink number'

post back if you need further assistance :-)

---

### Post by Hippytaff on 2010-10-12
> **scrooge_74 said:**
> The problems usually are not the devices or the fact that they runs on Windows. Most of the time is either it dosent have a driver installed or there is no driver.

In your case you have a:

Bus 001 Device 007: ID 148f:2770 Ralink Technology, Corp. 

If you spend enough time around here you notice that a bunch of network cards from different "vendors" user the same chips inside so if there is a driver you are in luck, then is a matter of configuration.

Fast google search got me this:

[http://ubuntuforums.org/showthread.php?p=9236718](http://ubuntuforums.org/showthread.php?p=9236718)

Could be you need to blacklist something

Do this first :-D

---

### Post by havivi on 2010-10-12
> Quote:
Originally Posted by scrooge_74  
The problems usually are not the devices or the fact that they runs on Windows. Most of the time is either it dosent have a driver installed or there is no driver.

In your case you have a:

Bus 001 Device 007: ID 148f:2770 Ralink Technology, Corp. 

If you spend enough time around here you notice that a bunch of network cards from different "vendors" user the same chips inside so if there is a driver you are in luck, then is a matter of configuration.

Fast google search got me this:

[http://ubuntuforums.org/showthread.php?p=9236718](http://ubuntuforums.org/showthread.php?p=9236718)

Could be you need to blacklist something
Do this first 

Just did this. work like a charm :P
thank you very much :)

---

### Post by scrooge_74 on 2010-10-12
Cool mark this thread as solve so others can benefit from this.

---

