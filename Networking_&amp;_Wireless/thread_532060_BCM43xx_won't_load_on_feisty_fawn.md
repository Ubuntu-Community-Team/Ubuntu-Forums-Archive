---
title: "BCM43xx won't load on feisty fawn"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by onyx69 on 2007-08-22
Hi, my wireless card won't load at startup I get this error message
> [ 3847.792000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

once I do iwconfig I get this
> lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"S"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and I followed this tutorial to get the wireless configured : [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

and once I do a network interface restart.  my wired interface does restart but not my wireless one.... which would be logical if I can't get the device to start in the first place


thanks for your help

If it can help here's the output for the networking restart

>  * Reconfiguring network interfaces...                                                  There is already a pid file /var/run/dhclient.eth1.pid with pid 9163
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0f:b0:0a:51:49
Sending on   LPF/eth1/00:0f:b0:0a:51:49
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.15.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0f:b0:0a:51:49
Sending on   LPF/eth1/00:0f:b0:0a:51:49
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.15.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.15.1
bound to 192.168.15.106 -- renewal in 41789 seconds.
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Could not set interface 'eth0' UP
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth0.

---

### Post by pxwpxw on 2007-08-22
You  need to install  bcm43xx_microcode5.fw in /lib/firmware/

There is a link for a .deb package to do that in this thread
[http://ubuntuforums.org/showthread.php?t=526901](http://ubuntuforums.org/showthread.php?t=526901)

You install it 
```

 sudo dpkg -i <the package name>

```

Then enable with the Network Manager. (and firewall if you are using firestarter), and restart.

You should not need to use ndiswrapper.

---

### Post by onyx69 on 2007-08-22
thanks... but something went wrong.. I did install the package, and everything seemed to be fine until my computer froze.  then I rebooted the machine and now I can't seem to be able  to see the wireless networks and nothing seems to connect

---

### Post by kevdog on 2007-08-22
If you want to abandon bcm43xx and try ndiswrapper I can help you.  Im not sure why bcm43xx doesnt work b/c it should, however sometimes trying a different solution may be of help.

---

### Post by pxwpxw on 2007-08-22
> **onyx69 said:**
> thanks... but something went wrong.. I did install the package, and everything seemed to be fine until my computer froze.  then I rebooted the machine and now I can't seem to be able  to see the wireless networks and nothing seems to connect

It probably just needs rechecking Network configuration, but just to make sure, first could you say -  
 what is your computer (PC Macintel AppleMac-ppc ?) and what is the wireless card, 
 can you change to WEP.
 is the ethernet network connection working. 
 is there a firewall (possibly blocking one of eth0 or eth1)

What is the result now for 
```

 cat  /etc/network/interfaces
 ifconfig
 iwconfig
 lsmod | grep bcm
 ls /lib/firmware/

```

---

### Post by likemindead on 2007-08-22
Here's what worked great for me: (1) uninstall network-manager, (2) install wicd, and (3) follow [these instructions]("http://ubuntuforums.org/showthread.php?t=405990") exactly.

---

### Post by onyx69 on 2007-08-22
> nick@sebaco-ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

# The wireless network interface
auto eth0
iface eth0 inet dhcp
wpa-driver wext
wpa-ssid SEBACO
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 7aa53fa7e218d744e663c2d1cb3928f4f5a6cd7bd89043d131b77c1c73ef9dba
wireless-essid SEBACO
nick@sebaco-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:4B:91:85:A2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:13 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1385 (1.3 KiB)  TX bytes:2602 (2.5 KiB)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:0F:B0:0A:51:49  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe0a:5149/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:641086 (626.0 KiB)  TX bytes:124813 (121.8 KiB)
          Interrupt:17 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:90:4B:91:85:A2  
          inet addr:169.254.8.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

nick@sebaco-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"SEBACO"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nick@sebaco-ubuntu:~$ lsmod | grep bcm
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac
nick@sebaco-ubuntu:~$  ls /lib/firmware/
2.6.20-15-generic     bcm43xx_initval05.fw  bcm43xx_microcode2.fw
2.6.20-16-generic     bcm43xx_initval06.fw  bcm43xx_microcode4.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode5.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_pcm4.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm5.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw
nick@sebaco-ubuntu:~$ 


there are the output for those command.  I have a pc it's a COMPAQ R3210CA, wireless card is a broadcom not sure of the model

what I would like to try is to undo the changes but don't know how since i'm new to linux. 

what should I look for, 

thanks

---

### Post by onyx69 on 2007-08-22
just checked the synaptic package manager and I think I know why the system froze once I installed the suggested package,  it said that it was the bcmXX firmware for Dapper and I have Feisty... could anyone confirm ?

---

### Post by pxwpxw on 2007-08-22
> **onyx69 said:**
> just checked the synaptic package manager and I think I know why the system froze once I installed the suggested package,  it said that it was the bcmXX firmware for Dapper and I have Feisty... could anyone confirm ?

No that should not be a problem it just installs those /lib/firmware/ files which are for the broadcom chip..

But did you get restarted OK after that system freeze? 
 
The info you posted looks as though you just need to finish configuring for wireless and DHCP, I will fire up a PC with feisty and broadcom bcm43xx and comment further from there - this is MacosX, but i have bcm43xx on both Applemac ppc and on intel PC celeron with a broadcom wireless card using that package, no problems, no ndiswrapper

However, if both the ndiswrapper and bcm43xx are present, there can/will  be problems, people installing ndiswrapper usually disable bcm43xx by blacklisting it, but I dont think ndiswrapper bothers bcm43xx. So did you have ndiswrapper installed also?
If you wanted to use ndiswrapper  you would need to blacklist the bcm43xx module (but I prefer the bcm43xx support ).

=== tried it on i386 PC OK ==========

Tried the deb package on oldibm = i386 PC, celeron 700MHz running xubuntu 704 and kubuntu 610 and win xp etc.

pci wireless card, Broadcom chip 

x@oldibm:~$ uname -a
Linux oldibm 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux


I am typing this in kubuntu using wireless now 

==================

~$ lspci | grep BC
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Kernel modules were already there:

x@oldibm:~$ lsmod | grep bcm
bcm43xx               127252  0
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac
x@oldibm:~$     

======================

x@oldibm:~/Desktop$ sudo dpkg -i bcm43xx_compwiz18.1-all.deb

(message about removing ndiswrapper stuff) 

Selecting previously deselected package bcm43xx-firmware.
(Reading database ... 82923 files and directories currently installed.)
Unpacking bcm43xx-firmware (from bcm43xx_compwiz18.1-all.deb) ...
Setting up bcm43xx-firmware (1.3-1ubuntu2) ...
Note that you need to DISABLE ndiswrapper and wifi-radar for this driver
to work properly! You can do this by removing the ndiswrapper driver.
Use `sudo ndiswrapper -l' to identify the driver.
Then run `sudo ndiswrapper -e <driver>' to remove it. You may also need
to remove the file /etc/modprobe.d/ndiswrapper

That just Installs these bcm43xx files (not all needed)
x@oldibm:~$ ls /lib/firmware/
2.6.17-10-386         bcm43xx_initval04.fw  bcm43xx_initval09.fw   bcm43xx_pcm4.fw
2.6.17-10-generic     bcm43xx_initval05.fw  bcm43xx_initval10.fw   bcm43xx_pcm5.fw
bcm43xx_initval01.fw  bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval02.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval03.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
ax@oldibm:~$     
===============================================

In kubuntu610 the Network configuration was broken, had to edit /etc/network/interfaces

x@oldibm:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
####auto eth0
iface eth0 inet dhcp
### had to edit this by hand to add the wep key
auto eth1
iface eth1 inet dhcp
wireless-essid bandicoots1
wireless-key s:xxxxxxxxxxxxx
ax@oldibm:~$

=====================================

Also note Firestarter needs to enable wireless eth1 here.
 ============================

---

### Post by onyx69 on 2007-08-23
let me try to reinstall the drivers... I don't have ndiswrapper installed (at least that I know of, check synaptic and it's not installed).  and to answer your question about the freeze... yes I managed to reboot the computer but had some weird problems with the wireless.

like I said I'll try again and post an update

---

### Post by msjones on 2007-08-23
Hi

I had the excat same problems, my advice is to scrap the BCM43xx drivers and use the bcmwl5.inf driver.

do the following:

$ rmmod bcm43xx

$ echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist

**Then reboot your machine**.

$ sudo apt-get build-essential

**Download ndiswrapper 1.47 and install**.

$ wget ftp.us.dell.com/network/R151517.EXE

$ unzip *.EXE

$ cd DRIVER

$ sudo ndiswrapper -i bcml5.inf

$ sudo ndiwrapper -m

$ modprobe ndiswrapper

This will get the wireless card working no problem. It is possible to get the bcm43xx card working but its a pain in the a** and not really much point unless you are wanting to use Kismet.

Hope this helps.

MJ

---

### Post by onyx69 on 2007-08-23
thanks MJ and all for your help... In my case I didn't have to fallow these instructions... the first attempt I made didn't succed but here's what I did.

I installed the bcm43XX drivers and then configured /etc/interface/networking as described in various tutorials.  then I restarted the networking interface without rebooting the machine... it froze the computer and at reboot the network card wasn't working anymore.

what I did next was removing the drivers installed, rebooting the machine (at least 3 times and the third time everything was back the way it was before the first drivers install), installed the drivers again and REBOOTED the machine. Once I logged back in... poof! everything was working and my network was automatically found.  it asked me my security key.

I am writing these line over my wireless network

So again thanks to all

---

