---
title: "compaq presario cq50-139wm wireless not connecting"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by newbiefly on 2008-11-08
hello,
    So i landed one of the 298$ laptops at walmart this morning the compaq presario cq50-139wm.  got it out checked out vista wireless was working.  Then scrapped windows entirely for the new ubuntu release everything seems great except wireless i get the following in terminal:

user@computer:lspci -nn
.....
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

user@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:75:89:ab  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe75:89ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3239 errors:0 dropped:2866845965 overruns:0 frame:0
          TX packets:2290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3264091 (3.2 MB)  TX bytes:246930 (246.9 KB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

user@computer:~$ lspci | grep eth*
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

System --> Administration --> Harware Drivers says:
No proprietary drivers are in use on this system.
Support for Atheros 802.11 wireless LAN cards.
Tested by th Ubuntu developers
License: Free
This driver is activated and currently in use.

user@computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

user@computer:~$ uname -m
i686
user@computer:~$ uname
Linux

any suggestions as to where i go from here?  i know its some sort of driver issue but beyond that am somewhat clueless.:confused:

thanks guys,
newbiefly

---

### Post by pytheas22 on 2008-11-08
That's strange...if you're using Ubuntu 8.10 (you are, right?) ar242x cards should work out-of-the-box.  Perhaps the madwifi module is not being loaded for some reason.  Does the interface come up if you type:
```

sudo modprobe ath_pci
```

or:
```

sudo modprobe ath9k
```

After running one of those commands and waiting a few seconds, you should see an entry for either 'ath0' or 'wlan0' in the output of 'ifconfig.'

If not, what is the output (in this order) of:
```

sudo modprobe ath_pci
lshw -C Network
dmesg | grep -e ath -e wlan
```

---

### Post by Corwin7 on 2008-11-09
I grabbed one of the Walmart laptops too. :) 

# lspci -nn | grep Atheros
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

# uname -a
Linux dworken 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux


I was able to grab madwifi-hal-0.10.5.6-r3875-20081105 and apply the aircrack-ng patch: madwifi-ng-r3745.patch 

I was able to compile this and I can use:
wlanconfig ath0 create wlandev wifi0 wlanmode monitor

and then use airodump-ng and see networks, however I can not connect. I assume this has to do with the orange light on the wifi button, I believe until the push button turns blue that transmit is disabled.

---

### Post by newbiefly on 2008-11-09
yes 8.10 i made a live cd and did the install of latest version saturday afternoon i tried those commands and nothing so here is a copy of the terminal session```
user@computer:~$ sudo modprobe ath_pci
[sudo] password for user: 
user@computer:~$ sudo modprobe ath9k
user@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:75:89:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2111961407 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

user@computer:~$ sudo modprobe ath_pci
user@computer:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:75:89:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:c2:4f:d2:95:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
user@computer:~$ dmesg | grep -e ath -e wlan
[   14.531523] ath_hal: module license 'Proprietary' taints kernel.
[   14.533724] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.547060] wlan: 0.9.4
[   14.555786] ath_pci: 0.9.4
[   14.555826] ath_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.555838] ath_pci 0000:02:00.0: setting latency timer to 64
[   14.604359] ath_pci 0000:02:00.0: PCI INT A disabled
[  204.554229] ath9k: 0.1
user@computer:~$ 
```

the button does seem weird never seen one on a laptop before didn't seem to do anything when pushed while i was running vista for 5 minutes isn't doing anything now that its an ubuntu system

much appreciation for your interest,
looking forward to your reply,
newbiefly

---

### Post by hawas on 2008-11-09
Hey I too have a compaq laptop, cant say much about the make though. Anyways I faced a similar problem with my laptop. The wireless doesnt seem to be working at all. The terminal output is given below...also I am a total noob...




anupam@heater:~$ sudo modprobe ath_pci
anupam@heater:~$ sudo modprobe ath9k
anupam@heater:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:f9:b6:0e  
          inet addr:10.94.20.27  Bcast:10.94.255.255  Mask:255.255.0.0
          inet6 addr: fe80::216:d3ff:fef9:b60e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13288368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1169320920 (1.1 GB)  TX bytes:17901646 (17.9 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:cb:88:85  
          inet6 addr: fe80::21a:73ff:fecb:8885/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10108886 (10.1 MB)  TX bytes:10108886 (10.1 MB)

anupam@heater:~$ sudo modprobe ath_pci
anupam@heater:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:16:d3:f9:b6:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=10.94.20.27 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:cb:88:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:ff:cb:3c:ca:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
anupam@heater:~$ dmesg | grep -e ath -e wlan
[    2.496123] md: multipath personality registered for level -4
[19103.703263] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[19103.731257] wlan: 0.9.4
[19103.746438] ath_pci: 0.9.4
[19113.256914] ath9k: 0.1
anupam@heater:~$

---

### Post by Chas_E_Erath on 2008-11-09
> **newbiefly said:**
> hello,
    So i landed one of the 298$ laptops at walmart this morning the compaq presario cq50-139wm.  got it out checked out vista wireless was working.  Then scrapped windows entirely for the new ubuntu release everything seems great except wireless i get the following in terminal:

...

thanks guys,
newbiefly

Heh...funny thing.  Yesterday, I found myself with one of those $298 laptops, too.  My intention was to install Ubuntu 8.04 on it since 8.10 seems fraught with wireless problems.  But the 8.04 disk won't even boot (has a modprobe failure?).  I tried 8.10 after that, but the partition editor fails.  I'm trying to resize the MS partition rather than blow it away (I'm not sure why).  This morning I'm having better luck.

Sorry for the post, since its not relevant to your issue (yet).  I suspect, though, that I'll be in touch.

Chow (the dog)
Chas.

---

### Post by mordalo on 2008-11-09
I also bought one of these...inexpensive...laptops, and had the same problem.

Did a little searching through the forums, and found this:

[http://ubuntuforums.org/showpost.php?p=6075320&postcount=10](http://ubuntuforums.org/showpost.php?p=6075320&postcount=10)

It works.  I followed the directions, rebooted, and connected via wireless right away.

---

### Post by mordalo on 2008-11-09
**Caveat!**

Some users (myself included) noticed that there's some connectivity issues using the method I posted in a previous link.

My apologies.  In my zeal after finding a fix, I didn't notice the connection issues at first.

I've also tried this method.  

[http://ubuntuforums.org/showpost.php?p=6086847&postcount=2](http://ubuntuforums.org/showpost.php?p=6086847&postcount=2)

After trying the second method, thing seem to be moving a bit faster, but as always, your results may vary...

---

### Post by pytheas22 on 2008-11-09
hawas: you have a Broadcom-based wireless card.  It looks like an interface is being created for it, so you should be able to see networks.  You may need to install firmware, however.  Try running:
```

sudo apt-get install bcm43xx-fwcutter
```

If that doesn't help, please start a new thread and let us know the URL.  Since your problem is not the same as that of the other posters here (who all seem to have Atheros cards), it would be best to start a new thread.

Everyone else: if the link provided by mordalo doesn't help you, I would try using the script from [this thread]("http://ubuntuforums.org/showthread.php?t=798485"), which will painlessly grab the latest madwifi source and compile it for you.  ar242x cards should work with the latest madwifi.

---

### Post by Corwin7 on 2008-11-09
My old laptop did almost exactly the same thing; with the wifi switch in airport/disabled mode you could see APs but not connect until you flipped the switch. On this Compaq laptop the wifi button cycled from blue to orange when you pressed it in vista, but it's only orange in Linux. I can see the access points just fine. I assume the people who are able to join an access point have a blue button, right? Any clue how to enable this in Linux? Since it's just a switch it probably can be removed/soldered off the wifi card.

---

### Post by newbiefly on 2008-11-09
i tried using mordalo's linked threads but whenever i wget i get```
HTTP request sent, awaiting response... 404 Not Found
2008-11-09 20:44:00 ERROR 404: Not Found.
```
or```
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz [following]
--2008-11-09 20:45:15--  http://snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz/
Resolving snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz... failed: Name or service not known.
wget: unable to resolve host address `snapshots.madwifi-project.orgmadwifi-hal-0.10.5.6-current.tar.gz'

```
which seems weird because i'm posting from my wired connection as i'm trying to do this

i'll try more in the morning after work
thanks to everyone for responding

---

### Post by pytheas22 on 2008-11-10
The link from the first thread is broken because the file name (which is based on the date the file was uploaded, and it gets updated frequently) changed.  Try:
```

wget **http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-11-10.tar.bz2**
tar jxvf compat-wireless*
cd compat-wireless*
make
sudo make install
sudo make unload
sudo make load
```

If that doesn't work, try changing the date in the part of the command in bold above to whatever is most recent at [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

As for the second link also failing, it's the same problem.  Try running the first three commands there as:
```

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
tar -xvf madwifi-hal*
cd madwifi-hal-0.10.5.6*
```

The remaining steps in the second thread should still work as they're written.

---

### Post by farqward on 2008-11-11
I too have the $298 walmart compaq.  I am using it right now connected via wifi.  I had to get a new driver for the atheros chipset.  I just followed the instructions from: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
BTW The wifi light stays orange in ubuntu

---

### Post by newbiefly on 2009-11-29
upon upgrade to 9.10 wifi now works YAY!

---

### Post by Unwashed on 2011-11-23
I hope this helps. I had the same problem, with the same computer, until i found this link to a driver  [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-62508-1&lc=en&dlc=en&cc=us&product=3752689&os=2093&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-62508-1&lc=en&dlc=en&cc=us&product=3752689&os=2093&lang=en) It's amazing to have internet again, i was just about to give up and buy a new computer.

---

