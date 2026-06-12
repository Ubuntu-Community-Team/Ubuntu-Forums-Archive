---
title: "Broadcom Wireless Troubles"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by homer454 on 2008-06-28
I have an HP Pavillion dv9823cl and I have a Broadcom BCM4328 802.11a/b/g/n (rev 03). I have followed numerous guides on getting wireless networking up and running in Hardy, but each attempt has failed. Does anyone know of a solution, or has been in a similar situation? 

Thanks.

By the way, how can I change my screen resolution? The only resolutions available is 640x480 and 800x600.

---

### Post by cwbar_1 on 2008-06-28
I have the dv6449us with the exact same card.  I have used these directions since Dapper, and have never had any problems.
Use the following to get wireless going.
1. Copy bcmwl5.inf & bcmwl5.sys to /home/your_directory/drivers directory. (md /home/your_directory/drivers
2. Install w/ndiswrapper.  If you do not have an internet connection, you can enable your install CD as a software resource.  Then use synaptic to install ndiswrapper and utils.

(copy and paste each line, one at a time)

	sudo ndiswrapper -i /home/Your_directory/drivers/bcmwl5.inf
	ndiswrapper -l
	sudo depmod -a
	sudo modprobe ndiswrapper
	sudo cp /etc/network/interfaces /etc/network/interfaces.orig
	echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
	sudo ndiswrapper -m
	echo 'ndiswrapper' | sudo tee -a /etc/modules
	echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Make sure to download WICD before you remove network manager.  Read the FAQs on WICD's web site.

Install WICD: Remove Ubuntu's version of network manager.  "sudo aptitude remove network-manager"
Install WICD:  double click deb package.
Install to tray:In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the &#8220;Startup Programs&#8221; tab, click the &#8220;New&#8221; button. Give it a name (&#8221;Wicd&#8221; works fine). For a command, enter &#8220;/opt/wicd/tray-edgy.py&#8221;.

As far as your screen resolution. Use Envy to install the NVIDIA drivers.

Make sure you do a complete update.

---

### Post by homer454 on 2008-06-28
Ok. I have followed the following steps and the default network manager for Ubuntu worked. But it dropped connection and couldn't reconnect. I isntalled WICD and it detects my network and attempts to connect, but cannot. I only can connect it through ethernet.Is there something wrong?

---

### Post by cwbar_1 on 2008-06-29
Looks like you're very close.  Post the results of ifconfig & iwconfig.

---

### Post by homer454 on 2008-06-29
I ran ifconfig and got this:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:56:48:e7  
          inet addr:192.168.0.191  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe56:48e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2351279 (2.2 MB)  TX bytes:380271 (371.3 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11600 (11.3 KB)  TX bytes:11600 (11.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:00:10:e4:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f2200000-f2204000 

I ran iwconfig and got this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by homer454 on 2008-06-29
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by homer454 on 2008-06-29
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by homer454 on 2008-06-29
Oops, sorry for the multiple replies. Hehe.

---

### Post by cwbar_1 on 2008-06-29
Try disconnecting eth0 (your wired network) and see if your access point is then associated with your wireless network.  ****If you are trying to use wired and wireless at the same time, I believe it would default to wired ******

---

### Post by homer454 on 2008-06-30
I've already tried that. I only had the wired connection to copy the IP info and post here.

---

### Post by cwbar_1 on 2008-06-30
OK, last possible help I know of.
Copy an paste the following in terminal.
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
(Just in case previous installs did not handle this)
Restart system, open WICD, and click on refresh.

---

### Post by twilight7 on 2008-06-30
I am new to Ubuntu
i just installed Kubuntu 7.04 and i am not able to connect to my wireless router, i am a noob at all this and not afraid to admit it, i dont want to mess anything up and i have tried to install wicd but i dont know what i am doing, it is a bit diff from windows. i have tried to follow what some of the other people have said and i am just lost, i need someone who can take me step by step. i dont have wicd installed right. i think. not sure. it is not in the starting menu, like what some other people have said. i just installed kubuntu last night. i think it is feisty. dont know so can anyone please help. it would be greatly appreciated. Thanks    Monique

---

### Post by STPitcher on 2008-06-30
Hi.  I have an HP DV6000z.  AMD 64, Broadcom BCM94311MCG.  I managed to get the wired working ok.  But had great difficulties with the wireless... just as everyone else around here has.  I finally have it working, and want to share what I've learned.

First of all, much of Linux "just works".  As you'd want.  I think I understand the issues with wireless... certain manufacturers consider their device proprietary and won't release specs to allow the open source world to code to them, but at the same time, they refuse to write software for anything other than Microsquish.  Those of us who choose to run Linux probably do best to buy a Made-For-Linux box... but then most of us buy Windows boxes and after a couple of years get bored and want to run Linux on them.  At least that's my story.

Anyhow, I've been through most of the various contortions described here... I honestly am not sure which set of instructions I finally got to work... too bad, I'd really like to thank the author.  I believe I'm finally running NDISDRIVER, rather than the other one who's name I can't recall.

The frustrating thing is, now that its working, I suspect I really had it working long ago but didn't recognize it.  This is one area where Ubuntu can probably make an improvement.

I've installed WiCD... V1.50.  Its rather more informative than the 1.42, and thus more useful.  Its much more informative than the KNetworkManager.  With WiCD when I get the thing running, I can see the various wireless networks out there.. I suspect I had it working with KNetworkManager, but it didn't show me what it saw, so I didn't realize how close I was.  Or perhaps it really wasn't working and maybe KNM does show this once its working(?).  Regardless, WiCD was a great help.  Thanks to the WiCD team!!

The final problem I had was apparently the encryption level.  I found that I was able to connect to my neighbor's unsecured network... This, in addition to SEEING *MY* network told me that I was almost there.  But I couldn't connect to my own wireless network.

I'm running a NETGEAR wireless router with WPA/PSK(TKIP).  I have no idea what that means.  Probably could look it up, but it doesn't matter.  When I switched to WPA/PSK(TKIP) + WPA2/PSK(AES) I found that I was able to connect.  I'm using WPA supplicant driver (WEXT) and WPA 1/2.

So my problem was apparently the WPA/PSK(TKIP).

Now I'm connected, and happy!

Its been a long road... Nearly a week... though I had some surgery on Wednesday, and haven't exactly been at it full-time.

It really appears that *WE* have most of what it takes to do this wireless stuff.  There's plenty of good information in these fora.  The only thing *I* added with reconfiguring my router.  I can't imagine that we can't do a better job for the poor nieve users who haven't a clue.

I know this is OpenSource... that means that *I'm* welcome to do this!  :-)  Though I really have the excuse that I don't know the Linux environment sufficiently.

At least, I'd like to recommend to Ubuntu, the use of a network manager that is more helpful than KNetworkManager.

Forgot to say:  I'm running Kubuntu 8.04, 64 bit.

I think one thing that may have helped is that the instructions I followed including rebuilding of NDISERVER from sources.  

- stp

---

### Post by homer454 on 2008-06-30
> **cwbar_1 said:**
> OK, last possible help I know of.
Copy an paste the following in terminal.
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
(Just in case previous installs did not handle this)
Restart system, open WICD, and click on refresh.

Ok, I have tried that but it still didn't work. So I just wen to System>Administration>Network and unlocked it, clicked on wireless connection, configured it and it connected online through WICD. Wi-Fi works like a charm now. However, I must always do this each time I boot up. 

Now, how get rid of WICD and get the default network manager back?

Thanks for the help! 
:popcorn:

---

### Post by cwbar_1 on 2008-06-30
Synaptic package manager.  (Search for WICD and completely remove.  Then, while on wired connection, search for network-manager & network-manager-gnome and install.

*** It may be that  blacklisting of the bcm43xx driver solved the problem.  If someone knows for sure, I wish they would jump in and let us know. ***

---

