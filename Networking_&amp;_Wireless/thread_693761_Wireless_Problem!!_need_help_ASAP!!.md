---
title: "Wireless Problem!! need help ASAP!!"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by btole79 on 2008-02-11
very weird issue.  i loaded Ubuntu 7.10 on my HP Laptop and everything works great.  i only had an issue with the Video not wanting to go into advanced settings but after some research on the web i found the issue and everything is fine.  i have been raving about ubuntu to my boss and how we should switch to it and i have to show him a working machine and i think im all set on my lap but yesterday for some reason i have no wireless devices installed any more.  i run an ifconfig and the wireless card doesn't show and if i run and iwconfig it says its not installed.  the weird thing is under the restricted drivers section it shows an Intel wireless card driver being used.  i have been working fine on this laptop for two weeks now and yesterday the wireless card disapears.  can any one help?

very frustrating.:mad:

i love Ubuntu by te way:guitar:

---

### Post by Hightide on 2008-02-11
Hi btole79

try this good troubleshooting [guide]("http://ubuntuforums.org/showthread.php?t=571194") first and post output of 

lshw -C network

regards

be back later

:)

---

### Post by btole79 on 2008-02-11
this is the result of the command

*-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:8a:61:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 ip=192.168.60.110 latency=0 module=tg3 multicast=yes

---

### Post by btole79 on 2008-02-13
no one has any ideas?

---

### Post by dca on 2008-02-13
...was this after a kernel update or update manager indicating that the updates to be installed reference either:  linux-kernel, kernel headers, kernel-restricted, etc, etc???

---

### Post by Hightide on 2008-02-13
Hi btole79

thats a very good card you have and its definitely in use (configuration: driver=ipw3945 latency=0 module=ipw3945)

I have as seen a similar [thread]("http://ubuntuforums.org/showthread.php?t=674683") with respect to this card, which may help  


regards

:)

---

### Post by btole79 on 2008-02-13
yes i believe so but i am still pretty new to linux.  i can get around really easy in it but the more advanced fetures im missing.  is there a way to unistall the kernal update?  i am open to truing anything at this point.  i have broke down and now im using a netgear pcmcia card and i would much rather use the internal card.

thanks

---

### Post by dca on 2008-02-13
Post contents of this at CLI:
 
lsmod | grep 3945
 
let us know if it looks like this:
 
ipw3945      124576  1
ieee80211     35272  1 ipw3945 
 
...or something there-abouts...
 
If you do, then running ifconfig at CLI should reference eth something or the wireless card, if you don't see anything then the drivers are no longer being loaded on start-up.

---

### Post by btole79 on 2008-02-13
these are the results from the commands.  the ath0 is the netgear card and the wifi0 is the internal intel card i believe.  how can i check if the drivers are loading.  under the restricted drivers the intel card is checked to use.

lsmod | grep 3945

ipw3945               132384  1 
ieee80211              38472  1 ipw3945

ifconfig:
 ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:D5:10:88  
          inet addr:192.168.60.111  Bcast:192.168.60.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fed5:1088/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8396 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7293610 (6.9 MB)  TX bytes:1858554 (1.7 MB)

eth0      Link encap:Ethernet  HWaddr 00:1A:4B:8A:61:3B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3989 (3.8 KB)  TX bytes:3989 (3.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-D5-10-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31991 errors:0 dropped:0 overruns:0 frame:32022
          TX packets:8648 errors:6 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:10827519 (10.3 MB)  TX bytes:2210823 (2.1 MB)
          Interrupt:16 

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"WizzleDoodle"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:54:A6:9A   
          Bit Rate:24 Mb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:9427  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dca on 2008-02-13
eth0 should be the NIC, ath0 & wifi0 should be the wireless card...
 
type sudo modprobe -i ipw3945
 
does it come back w/ errors?

---

### Post by btole79 on 2008-02-13
so how do i make the drivers load at startup that i need to run the internal wireless.

---

### Post by btole79 on 2008-02-13
so how to i get the drivers to load at start up?

---

### Post by btole79 on 2008-02-13
sudo modprobe -i ipw3945

when i run this command it doesnt come back with anything.

---

### Post by dca on 2008-02-13
Okay, driver module is reinstalled so you should see wireless networks in network manager?

---

### Post by btole79 on 2008-02-13
no such luck.  if i unplug the netgear i still do not have anything in the wireless manager,

---

### Post by dca on 2008-02-13
You've read through that similar post in thread #6 in a similar situation?  The only other thing is remove the ethernet cable, right-click on the network manager and un-check enable networking and enable wireless.  Then go to System -> Application -> Network on the panel menu.  See if you have a wired and wireless connection listed.  If so, make sure both are set to roaming mode and obtain IP automatically DHCP whatever, then click on 'DNS' tab and clear everything out of there.  Click 'ok' and restart your system.  After reboot click on the nm-applet icon on the top right panel by the time and see if it lists any wireless networks.

---

### Post by btole79 on 2008-02-13
i have tried this and if i unplug te netgear card the other wireless card never shows in network settings?  this is very odd

---

### Post by btole79 on 2008-02-13
well after all this i have discovered im a moron.  this hp laptop has a touch switch for the volume and wireless control.  i think i touched the wireless and turned the card off.:confused:

anyways all is working again.  thanks for the help.

---

### Post by dca on 2008-02-13
Geez, thank God, I was running out of juice on that one...

---

