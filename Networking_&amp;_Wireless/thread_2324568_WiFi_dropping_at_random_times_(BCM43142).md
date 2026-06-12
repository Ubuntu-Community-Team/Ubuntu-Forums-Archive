---
title: "WiFi dropping at random times (BCM43142)"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by Y4kuzi on 2016-05-14
Hello,

I am experiencing unstable WiFi connections, it is driving me crazy.
It happens randomly, it is driving me crazy. I have tried different drivers, but it did not help.
I am running Ubuntu 16.04 LTS, everything is up to date. I had the same issue on 15.10 and 14.04.
This is my wireless card:
```

08:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
```

Here is the output of the wireless-info script:
[http://pastebin.com/f2MBPYZV](http://pastebin.com/f2MBPYZV)

I have also included the /var/log/syslog here, after the connection drops:
[http://pastebin.com/ALGxF5r3](http://pastebin.com/ALGxF5r3)

I hope we can resolve this issue!

---

### Post by wildmanne39 on 2016-05-14
First let's remove ndiswrapper it is not needed and conflicts with the wl driver.
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
``` 
Then reboot and test to see if the issue is still present.
Thanks

---

### Post by wildmanne39 on 2016-05-14
Also go into network manger and make sure IPV4 is set to automatic DHCP and IPV6 to ignore, your network and all the others in your area are on channel 1 change yours to 6 or 11 because all networks also have the same signal strength and your wifi is roaning fron ne network to another constantly. 
Then reboot.
Thanks

---

### Post by Y4kuzi on 2016-05-15
The reason I had ndiswrapper installed is because I wanted to try Windows drivers (because on Windows I don't have WiFi issues).
I have it removed now. Also, my IPv4 is already set on automatic and IPv6 is ignored.
Is  there any way I can completely disable roaming? Because I think my   connection drops whenever it is roaming, but I am not sure.

[Edit]
I don't think removing ndiswrapper helped. If anything, it seems to make it worse.
I have lost WiFi connection 3 times in the last hour already.

---

### Post by wildmanne39 on 2016-05-15
Bind your wireless to your access point. Right-click the Network Manager icon, select Edit Connections. Fill in the MAC address for your access point; find it with: 
```
sudo iwlist wlo1 scan
```
If you want to connect to other networks like at a coffee house you will have to remove the MAC address. You still should try another channel other then 1. 

Also if you can I would change the network name and take out any special characters.

Also > Tx-Power=200 dBmthat number is extremely high it should be around 20 or less usually, with it that high it may burn the wifi card out.
Thanks

---

### Post by Y4kuzi on 2016-05-15
The MAC address was already associated with my current router, but in  /var/log/syslog it still shows stuff about roaming (not sure if that is  relevant).
I have changed the WiFi channel to 11 and connected to my  Linksys router directly without underscore. (The TP-LINK was a signal  repeater, to increase signal).
A quick ping session to google.com still show some packet loss. How do I change the Tx-Power number?

---

### Post by Y4kuzi on 2016-05-15
The MAC address was already associated with my current router, but in    /var/log/syslog it still shows stuff about roaming (not sure if that is    relevant).
I have changed the WiFi channel to 11 and connected to my  Linksys   router directly without underscore. (The TP-LINK was a signal  repeater,   to increase signal).
A quick ping session to google.com still show some packet loss. How do I change the Tx-Power number?

```

PING google.com (216.58.212.238) 56(84) bytes of data.
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=1 ttl=55 time=8.35 ms
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=4 ttl=55 time=8.87 ms
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=6 ttl=55 time=9.15 ms
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=8 ttl=55 time=8.85 ms
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=10 ttl=55 time=7.89 ms
64 bytes from ams16s22-in-f238.1e100.net (216.58.212.238): icmp_seq=12 ttl=55 time=16.7 ms
^C
--- google.com ping statistics ---
12 packets transmitted, 6 received, 50% packet loss, time 11039ms
rtt min/avg/max/mdev = 7.893/9.986/16.791/3.072 ms

```


Sorry for the double post, something went wrong with editting.

---

### Post by wildmanne39 on 2016-05-15
Did you enter the MAC address manually in network manager if not then it could change and allow roaming if manually entered your wifi will not be able to roam.

Edit:
The MAC address should be placed in the BSSID column.

---

### Post by Y4kuzi on 2016-05-15
```
Address:00:23:69:2E:53:57
```
I copied **00:23:69:2E:53:57**, went to Edit Connections > clicked my router > Edit > and pasted it into BSSID field and clicked Save.
I double checked, and it is the correct address for my currently used router.

---

### Post by wildmanne39 on 2016-05-15
It is still dropping out with the mac address in BSSID?

---

### Post by wildmanne39 on 2016-05-15
If it is still dropping please post a new wireless-info file so we can see the changes after you removed ndiswrapper.
Thanks

---

### Post by Y4kuzi on 2016-05-16
Yes, it is still dropping. I let it run overnight, but I lost all connectivity and it wasn't able to connect back.
The WiFi icon showed I was still connected to the network, but I could not access any sites/servers, ping did not work.
I had to manually restart network-manager for it to work again.

Here is the new wireless-info results: [http://pastebin.com/Regi8Arh](http://pastebin.com/Regi8Arh)

---

### Post by wildmanne39 on 2016-05-16
Please post the output of:
```
sudo dpkg -s bcmwl-kernel-source
```
Thanks

---

### Post by Y4kuzi on 2016-05-17
```
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7825
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu8
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases:  wl(pci:v000014E4d00004311sv*sd*bc02sc80i*,  pci:v000014E4d00004312sv*sd*bc02sc80i*,  pci:v000014E4d00004313sv*sd*bc02sc80i*,  pci:v000014E4d00004315sv*sd*bc02sc80i*,  pci:v000014E4d00004727sv*sd*bc02sc80i*,  pci:v000014E4d00004328sv*sd*bc02sc80i*,  pci:v000014E4d00004328sv*sd*bc02sc80i*,  pci:v000014E4d00004329sv*sd*bc02sc80i*,  pci:v000014E4d0000432asv*sd*bc02sc80i*,  pci:v000014E4d0000432bsv*sd*bc02sc80i*,  pci:v000014E4d0000432csv*sd*bc02sc80i*,  pci:v000014E4d0000432dsv*sd*bc02sc80i*,  pci:v000014E4d00004365sv*sd*bc02sc80i*,  pci:v000014E4d00004353sv*sd*bc02sc80i*,  pci:v000014E4d00004357sv*sd*bc02sc80i*,  pci:v000014E4d00004358sv*sd*bc02sc80i*,  pci:v000014E4d00004359sv*sd*bc02sc80i*,  pci:v000014E4d00004331sv*sd*bc02sc80i*,  pci:v000014E4d000043a0sv*sd*bc02sc80i*,  pci:v000014E4d000043B1sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
```

---

### Post by wildmanne39 on 2016-05-17
It looks like that particular version of the driver has a bug in it, we will install a new one.
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then open software center make sure multiverse is checked then close software center and open terminal and do:
```
sudo apt-get update
``` 
```
sudo apt-get upgrade
```
```
sudo apt-get install broadcom-sta-dkms
```
Then reboot and see how it works.

We may still want to change tx power but for now we will wait.

---

### Post by ab6362 on 2016-05-18
I have the same issue on laptop Lenovo P50 ubuntu 16.04 fresh install. Same wireless card. Wi-fi keep appearing and missing again once in a while (not often - once a day or less). I cannot see the reason. Wifi can drop without even rebooting the laptop. and can appear without reboot. I was told that the driver is for 32-bit machine. Mine is 64. I am not sure. Please let me know if the above device of installing a new driver worked.

---

### Post by Y4kuzi on 2016-05-18
I now have removed bcmwl-kernel-source and installed broadcom-sta-dkms.
Now let's hope it will be stable. If not, I will reply here again.

---

### Post by Y4kuzi on 2016-05-19
It seems to be pretty stable now! But once issue I face, is sometimes it only shows a few wireless networks in range, while I know there are more.
Sometimes it even show only the AP I am connected to at the moment. That doesn't seem right to me.

---

### Post by Y4kuzi on 2016-05-21
Also, I cannot connect to my other AP. It just times out and connect to my default AP.
I tried deleting/re-adding it from the Network Manager, but it did not help.
Here is the /var/log/syslog: [http://pastebin.com/u4kP7M8z](http://pastebin.com/u4kP7M8z)

---

### Post by wildmanne39 on 2016-05-21
Please click on the wireless script in my signature and post the file created by the script here so we can see what is going on while you are trying to connect to your other AP. Be my guess it is wanting to connect to the network with the strongest signal.
Thanks

---

### Post by Y4kuzi on 2016-05-22
Thanks. Here is the output of the wireless-info script while trying to connect: [http://pastebin.com/vfsUcyDW](http://pastebin.com/vfsUcyDW)
The AP I try to connect to is TP-LINK_9E9024. It is a range extender, it works fine on all my other devices.

---

### Post by wildmanne39 on 2016-05-22
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and absolutely not TKIP.  Second, if your router is capable of N speeds, You will most likely have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. 

Also you will have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.
Thanks

---

### Post by Y4kuzi on 2016-05-23
For my router, the security mode is set to: WPA2 Personal
Encryption: AES.
Network mode: Mixed
Radio band: 20MHz
Standard channel: 11
I have changed Network mode to **Wireless-N only** (that's the only thing I changed) and rebooted the router.

Also, any ideas why it sometimes only shows 1 or 2 APs, when in fact there are many more in range?


[Edit]
Still not able to connect to my range extender via Ubuntu. It also does not re-connect to the internet after connection loss.
It says it is still connected to the router, but no connectivity until I manually restart network-manager.
This is the only log-line in that time-frame regarding the connection loss:
```
May  23 13:45:16 hp-ubuntu wpa_supplicant[12611]: wlo1: WPA: Group rekeying  completed with 00:23:69:2e:53:57 [GTK=CCMP]
```
After that event, the internet stopped replying (still connected to the router). Checked all other devices, they are fine.

---

### Post by wildmanne39 on 2016-05-23
You can try by disabling  Wireless-N and see if it can connect but you do not want it only N or you will have trouble connecting and staying connected to the network.
It says link quality is 23 that is low but not sure what to do about it.

I would change IPV6 to ignore it is auto right now.
Thanks

---

### Post by Y4kuzi on 2016-05-23
I have completely reinstalled Ubuntu because I think I messed up stuff with Network-Manager.
I notice the connection is stable whenever I keep the laptop lid open, but whenever I close the lid halfway or more, internet will stop working.
It does not disconnect from the router, but ping requests do not come through, and after a while it ping-timeouts from IRC servers.
I already set **System Settings > Power > When the lid is closed > Do nothing**, but that does not help.  Any ideas how this happens?

As for the link quality, I have no idea. I'm like ~5 meters away from the router. All my other devices show full bars, even Windows on the same laptop.

---

### Post by wildmanne39 on 2016-05-23
Please post the output of:
```
iwconfig
```
according to the information from the wireless script there was nothing wrong with network manager settings, that are not manually adjustable.

Did you just reinstall or do a fresh install?
Thanks

---

### Post by Y4kuzi on 2016-05-23
```

wlo1      IEEE 802.11abg  ESSID:"Linksys3209393"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:2E:53:57   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eno1      no wireless extensions.

lo        no wireless extensions.

```

I did a fresh install. Formatted all partitions.

---

### Post by wildmanne39 on 2016-05-25
When you close the lid and the network will not reconnect run:
```
lsmod | grep wl
```
is the driver loaded? if not we should be able to get it to load.
Thanks

---

### Post by Y4kuzi on 2016-05-25
It just disconnected again, and it did not automatically reconnect. The   network-manager icon looked like as if it was still connected, but when  I  clicked it, it showed no connected AP.
Here is the output of the command:
```

$ lsmod | grep wl
wl                   6447104  0
cfg80211              565248  1 wl

```

How  I got it working again: right click on network manager on the top  if  the screen, disable Wi-Fi, and restarting network-manager, and then  re-enabling Wi-Fi again.
Twice, because for some reason it gets disabled again after the first attempt. Really annoying.


[Edit]
I just found this new entry in the logs after the disconnect happened: [http://pastebin.com/ihXThbJu](http://pastebin.com/ihXThbJu)

---

### Post by wildmanne39 on 2016-05-27
When you reinstalled ubuntu did you do a fresh install? if so you probably need to install the new driver again.
We really got off track here, it is supposed to be one thread for one issue that way when someone searches for a solution to there issue the thread that says it is about a certain issue actually is about that issue. Like this one wifi dropping at random times, when we fixed that by installing the new driver the thread should have been marked as solved and a new thread started for the other issue.

Please post the output of:
```
sudo dpkg -s bcmwl-kernel-source
```
Thanks

---

### Post by Y4kuzi on 2016-05-27
I have not installed bcmwl-kernel-source because you said that driver had bugs. I have the one you gave me, broadcom-sta-dkms, which is successfully installed.
The WiFi has been greatly improved since, but not yet fully stable. Do you want me to start a new thread, or continue with this one?
So far only 2 issues remain, which are, if the WiFi loses connection (yet network-manager says it is still connected to the router), I have to restart network-manager manually (sometimes multiple times) before it works again.
And the lid-close issue I described before.

---

### Post by wildmanne39 on 2016-05-27
I suspect the driver is missing. If that's the case, let's see if we can get it to load on resume:
```
gksu gedit /etc/pm/config.d/config
```
A new empty file will open. Add one line:
```
SUSPEND_MODULES="wl"
```
Proofread, save and close gedit.
This is for the suspend issue, I think there are 2 separate issues here, let me know if that helps with the suspend issue then we can deal with the other.
Reboot

---

### Post by wildmanne39 on 2016-05-27
Please post the output of:
```
sudo dpkg -s bcmwl-kernel-source
```
Thanks

---

### Post by Y4kuzi on 2016-05-28
As I stated before, bcmwl-kernel-source is not installed. But here are the results anyway:
```

$ sudo dpkg -s bcmwl-kernel-source
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

I tried your other solution as well, but it did not help.
It is not suspended, or locked for that matter.

---

### Post by wildmanne39 on 2016-05-28
I gave you the wrong driver to check, please do:
```
sudo dpkg -s broadcom-sta-dkms
```
and post the results here.

To be exact it is the same driver but put into a different package so different name, but what I am trying to see is what version of the driver is present it is possible for it to still be the old driver.
Thansk

---

### Post by Y4kuzi on 2016-05-29
Here is the output:
```

$ sudo dpkg -s broadcom-sta-dkms
Package: broadcom-sta-dkms
Status: install ok installed
Priority: optional
Section: non-free/kernel
Installed-Size: 14138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: broadcom-sta
Version: 6.30.223.271-2
Provides: broadcom-sta-modules
Depends: dkms (>= 2.1.0.0)
Recommends: wireless-tools
Conflicts: broadcom-sta-modules
Conffiles:
 /etc/modprobe.d/broadcom-sta-dkms.conf c5d2490e6167f876e7aae7b4f08e16e6
Description: dkms source for the Broadcom STA Wireless driver
 Broadcom STA is a binary-only device driver to support the following IEEE
 802.11a/b/g/n wireless network cards: BCM4311-, BCM4312-, BCM4313-,
 BCM4321-, BCM4322-, BCM43142-, BCM43224-, BCM43225-, BCM43227-, BCM43228-,
 BCM4331-, BCM4360-, and BCM4352-based hardware.
 .
 This package provides the source code for the wl kernel modules and makes use
 of the DKMS build utility to install them for the running kernel. The
 alternative package broadcom-sta-source can be used instead in case of build
 problems.
 .
 The wireless-tools package is also required in order to make use of these
 modules. Kernel source or headers are required to compile these modules.
Original-Maintainer: Eduard Bloch <blade@debian.org>
Homepage: http://www.broadcom.com/support/802.11/linux_sta.php

```
According to Ubuntu it is the latest version.

---

### Post by wildmanne39 on 2016-05-30
Since you reinstalled it does not look like you have posted a new wireless file created by the wireless script,please post one. You may be  having issues with the network manager bug in 16.04. Are you still have disconnections and how often?
Thanks

---

### Post by Y4kuzi on 2016-05-30
The disconnections have been greatly reduced, maybe 1-2 a day.
Here is the new wireless-info: [http://pastebin.com/GuUJdJiR](http://pastebin.com/GuUJdJiR)
I hope we can resolve this issue with automatic reconnection upon connection loss, then it would be perfect.

---

### Post by wildmanne39 on 2016-06-01
I have been looking for a way to put the commands to restart network manager upon disconnection in a script but I have not found a way to do it in 16.04.

---

