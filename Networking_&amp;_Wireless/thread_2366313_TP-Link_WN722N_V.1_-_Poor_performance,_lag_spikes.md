---
title: "TP-Link WN722N V.1 - Poor performance, lag spikes"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by noxarcz on 2017-07-16
Hi, after 6 months of not using linux i decided to give it another shot, but just like last time, problems with wifi arose.

The USB Wifi adapter im using is TP-Link WN722N Version 1 using the Atheros AR 9271 chipset (V2 and 3 use Realtek iirc.)

While it works fine for downloading, browsing etc. it's very unreliable in multiplayer games, at some moments it's running smoothly at 30ms latency,
but other times lag spikes appear and you start teleporting through the space. This is not a framerate issue, tested in single player games as well, stable at 60FPS.


I've tried using the Ndiswrapper, which was installed correctly without any issues, then i downloaded the TP-Link driver and installed it via Ndiswrapper (Windows XP 64bit package) and rebooted the system.
After reboot the wifi didn't work at all so i tried versions for Windows 7, 8.1 as well as 32bit ones, not a single one worked so i removed all ndiswrapper associated files from my Xubuntu installation and restored the original wifi drivers, so i'm back at the beggining.

I would appreciate any help because it's really frustrating, i've given up on linux back in December for the same reason, and i couldnt find any solution now neither back then.
[B]
Full system specs:[/B]

Xubuntu 17.04
intel i5 4590
GTX 960 (newest proprietary binary driver 384)
120GB SSD and 1TB HDD
USB Wifi adapter **TP-Link WN722N** (chip Atheros AR 9271)

---

### Post by jeremy31 on 2017-07-16
[https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
Should be a good start
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
If you don't have gedit just substitute your text editors name
Add the following to the bottom of the file
```
[device]
wifi.scan-rand-mac-address=0
```

Restart network manager
```
systemctl restart network-manager.service
```

I couldn't connect at all in 17.04 with the WN722N until I disabled the random MAC and then it worked fine

---

### Post by noxarcz on 2017-07-16
I've already used this to make the Wifi work in the first place, it didn't work at all initially

---

### Post by jeremy31 on 2017-07-16
See the wireless script link in my signature and post your results

---

### Post by noxarcz on 2017-07-16
Regarding your first reply, i checked the ubuntu thread you linked me and learned nothing new, in fact im already running at the reccomended settings.
I also ran your wireless script and here is the result 
[http://paste.ubuntu.com/25103916/](http://paste.ubuntu.com/25103916/)

---

### Post by BenginM on 2017-07-16
Salutations!

Wireless gaming on a PC! well okay .. game on with Ethernet, do you see any lags! of course not.. but if you still insist on pointing fingers,  then the fault is either on the driver or the adapter device itself and NOT the kernel! .. maybe get a better usb adapter!

is this on a home built desktop! either way PCI wireless devices are more reliable... the best of which being intel (7260, 7265, 8260, ... and they are cheap online check:

[https://pcgamingbuilds.com/best-pci-wireless-adapter](https://pcgamingbuilds.com/best-pci-wireless-adapter)

[https://www.amazon.com/Best-Sellers-Electronics-Internal-Computer-Networking-Cards/zgbs/electronics/13983711](https://www.amazon.com/Best-Sellers-Electronics-Internal-Computer-Networking-Cards/zgbs/electronics/13983711)

---

### Post by noxarcz on 2017-07-16
First of all, no i can't use Ethernet, if i could i would, the device worked perfectly for years on windows so it's not the device. Where do you see me blaming Kernel? I'm asking if anyone knows a solution to this problem WITHOUT having to buy new hardware. Because it is software side issue.

---

### Post by jeremy31 on 2017-07-16
I would actually suggest trying it in Ubuntu 16.04 as it is the long term support version.  The issues might be caused by some change in 17.04 which will not be supported at the end of January next year

---

### Post by noxarcz on 2017-07-16
I have used 16.04 or 16.10 back in December iirc, the problem was the same

---

### Post by jeremy31 on 2017-07-16
Did you disable IPv6 in network manager settings.  I would also recommend not using UFW if you do have it enabled.  Can you set the computer to a static IP in the router setup?

---

### Post by noxarcz on 2017-07-16
IPv6 is disabled already, i don&#7831; use UFW, checked it and says it's inactive, im not sure if i did so correctly, but i set my IP to static according to this guide [https://www.tecmint.com/set-add-static-ip-address-in-linux/](https://www.tecmint.com/set-add-static-ip-address-in-linux/)

---

### Post by praseodym on 2017-07-16
Using the same driver here. This one works well:
```

echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9khtc.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Replug the stick. If the stick becomes too hot, reduce the uptake current:
```

echo 'KERNEL=="wlx74ea3a940c39*", ACTION=="add", RUN+="/sbin/iwconfig wlx74ea3a940c39 txpower 16"' | sudo tee /etc/udev/rules.d/10-wlan-stick.rules
```
Reboot and check "iwconfig"

---

### Post by jeremy31 on 2017-07-16
I would have just used Network Manager to set IPv4 to manual then click add and enter the IP address, net mask, and gateway.  You could use 192.168.0.100 for IP, net mask 24, gateway 192.168.0.1, and DNS 192.168.0.1
Reboot and try it out
I did it for my Ubuntu laptop when I was using a hotspot for a connection, now with my router I can do the assignment from it

---

### Post by noxarcz on 2017-07-16
So i executed the commands praseodym suggested, the device didnt feel any hotter so i rebooted and tested again (For reference im using Team Fortress 2 for testing, back in December also tried War Thunder with identical, bad results)
Then i followed jeremys advice and set the network manager the way he told me to, rebooted, tested yet again with no effect.
I was about to respond but then the internet stopped working  completely, tried rebooting and changing the uptake current to txpower 16 like praseodym said, to no avail.
Had to set network back to automatic DHCP to make it work again, but it could've just been coincidence.

---

### Post by BenginM on 2017-07-16
if you think it's a software side issue lets test it real quick! , assuming you're using network manager ... "lock your connection to the AP's BSSID" setting your AP's BSSID in network manager, if you don't have anymore lags then it's Network manager's fault! usually caused by Network Manager's background network scans.

## if you want to git dirty and debug this , Set NM loglevel to debug and look if you encounter a log entry add_pending_action: scan exactly when the network latency spikes.

or switch to use wicd , and test this ..

#see 

[https://steamcommunity.com/groups/homestream/discussions/0/540735426854884989/](https://steamcommunity.com/groups/homestream/discussions/0/540735426854884989/)

also consider this , does the lag happens with different game mode , does it occurs with all games !

also while playing a game run $ top , and watch processes to see if there is something running in the background that suddenly jumps in.

---

### Post by jeremy31 on 2017-07-16
Can you run ```
dmesg | tail -20
```
The next time the lag spike happens to see if it gives us some idea as to what is going on?

---

### Post by noxarcz on 2017-07-16
To clarify, the lag is quite random, for a couple seconds it runs nicely, then it gets choppy, resumes normal function and after a short while start lagging again, the game displays ~40 ping consistently even during the lag (score screen shows ping)

So i just played around in TF2 a bit, had some lags, switched to terminal and ran the ```
**dmesg | tail -20**
``` command, this is the output:

```
[  198.667865] ath9k_htc 3-6:1.0: ath9k_htc: FW Version: 1.4
[  198.667866] ath9k_htc 3-6:1.0: FW RMW support: On
[  198.667867] ath: EEPROM regdomain: 0x809c
[  198.667868] ath: EEPROM indicates we should expect a country code
[  198.667869] ath: doing EEPROM country->regdmn map search
[  198.667869] ath: country maps to regdmn code: 0x52
[  198.667870] ath: Country alpha2 being used: CN
[  198.667870] ath: Regpair used: 0x52
[  198.674635] ieee80211 phy2: Atheros AR9271 Rev:1
[  198.675256] ath9k_htc 3-6:1.0 wlx74ea3a940c39: renamed from wlan0
[  198.720472] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
[  198.905308] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
[  198.950057] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
[  201.614172] wlx74ea3a940c39: authenticate with 90:94:e4:55:03:86
[  201.873923] wlx74ea3a940c39: send auth to 90:94:e4:55:03:86 (try 1/3)
[  201.875712] wlx74ea3a940c39: authenticated
[  201.877560] wlx74ea3a940c39: associate with 90:94:e4:55:03:86 (try 1/3)
[  201.880913] wlx74ea3a940c39: RX AssocResp from 90:94:e4:55:03:86 (capab=0x411 status=0 aid=6)
[  201.889385] wlx74ea3a940c39: associated
[  201.889392] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74ea3a940c39: link becomes ready
```


Also, im not sure if i should try the WICD, don't want to break the Network entirely, in addition, the WICD page provides only installation instructions for Gnome/Unity and KDE (Kubuntu)
While i use Xubuntu (Xfce)

---

### Post by jeremy31 on 2017-07-16
```
cat /var/log/kern.log | tail -20
```
After the next lag if you can as nothing was reported to dmesg

---

### Post by noxarcz on 2017-07-16
output
```
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667865] ath9k_htc 3-6:1.0: ath9k_htc: FW Version: 1.4
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667866] ath9k_htc 3-6:1.0: FW RMW support: On
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667867] ath: EEPROM regdomain: 0x809c
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667868] ath: EEPROM indicates we should expect a country code
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667869] ath: doing EEPROM country->regdmn map search
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667869] ath: country maps to regdmn code: 0x52
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667870] ath: Country alpha2 being used: CN
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.667870] ath: Regpair used: 0x52
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.674635] ieee80211 phy2: Atheros AR9271 Rev:1
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.675256] ath9k_htc 3-6:1.0 wlx74ea3a940c39: renamed from wlan0
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.720472] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.905308] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
Jul 16 22:38:40 noxar-MS-7850 kernel: [  198.950057] IPv6: ADDRCONF(NETDEV_UP): wlx74ea3a940c39: link is not ready
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.614172] wlx74ea3a940c39: authenticate with 90:94:e4:55:03:86
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.873923] wlx74ea3a940c39: send auth to 90:94:e4:55:03:86 (try 1/3)
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.875712] wlx74ea3a940c39: authenticated
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.877560] wlx74ea3a940c39: associate with 90:94:e4:55:03:86 (try 1/3)
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.880913] wlx74ea3a940c39: RX AssocResp from 90:94:e4:55:03:86 (capab=0x411 status=0 aid=6)
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.889385] wlx74ea3a940c39: associated
Jul 16 22:38:43 noxar-MS-7850 kernel: [  201.889392] IPv6: ADDRCONF(NETDEV_CHANGE): wlx74ea3a940c39: link becomes ready
```

Just to be clear, the "lag" is not a long lag/freeze, its more like a stutter, microlag pretty much, for example you are flying through air, falling to the ground and you can see its choppy, you get stuck in the air for a fraction of second, start falling again and then it gets choppy again.
So i just played the game, had some stutter/lag then alt tabbed to terminal, pasted the command and above is the output of said command.

Should i try to replace NetworkManager with WICD?

---

### Post by jeremy31 on 2017-07-16
I don't know if WICD would be better or not as nothing in either log even shows an issue.  Does this game you are playing have a support forum as I would ask there maybe even use a camera to record the stutter you are seeing and upload to youtube or wherever.  I can't be sure if it is an issue with the wireless or if it is CPU/GPU related

---

### Post by BenginM on 2017-07-16
Yes you should try wicd for now and test it for awhile to exclude the network side issue!

it's fairly simple , 

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

but still, form what you described .. it could not be a network issue in the first place ..

Freezing = Game requesting information from the storage device.

Micro-stuttering = frame times / latency between GPU's.

This is a very basic way of looking at it. There a million reasons for stuttering and frame skipping. You need to have a good understanding of hardware architecture and computer programming to truly understand. Computer Science or Games Programming are great courses to look into for gaining such knowledge.

also does the CPU get high , that might chock the GPU! how much VRAM the GPU has!

Again ... is this a home built desktop , what's specs of the machine!

---

### Post by noxarcz on 2017-07-16
[https://www.youtube.com/watch?v=9-V3Wi0q0Mg&feature=youtu.be](https://www.youtube.com/watch?v=9-V3Wi0q0Mg&feature=youtu.be)

It's much easier to feel the lag when you are actuall playing the game, but it can be clearly seen in **1 minute and 12th second** of the video, just watch how the teammates lag while they walk.

---

### Post by noxarcz on 2017-07-16
> **Sary.sa said:**
> Yes you should try wicd for now and test it for awhile to exclude the network side issue!

it's fairly simple , 

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

but still, form what you described .. it could not be a network issue in the first place ..

Freezing = Game requesting information from the storage device.

Micro-stuttering = frame times / latency between GPU's.

This is a very basic way of looking at it. There a million reasons for stuttering and frame skipping. You need to have a good understanding of hardware architecture and computer programming to truly understand. Computer Science or Games Programming are great courses to look into for gaining such knowledge.

also does the CPU get high , that might chock the GPU! how much VRAM the GPU has!

Again ... is this a home built desktop , what's specs of the machine!

I've told you what my specs are in the original post, but ill retype them here for you
Nvidia Geforce GTX 960 2GB VRAM
intel Core i5 4590

It's not a framerate issue, in singleplayer the problem simply isnt there, only in multiplayer.

---

### Post by noxarcz on 2017-07-16
I've fully switched to WICD and deleted NetworkManager, tried the game again and while it seems like it got slightly better, the issue persists, tbh i think its more of a placebo effect than an actual improvement.

---

### Post by BenginM on 2017-07-16
> **noxarcz said:**
> I've told you what my specs are in the original post, but ill retype them here for you
Nvidia Geforce GTX 960 2GB VRAM
intel Core i5 4590

It's not a framerate issue, in singleplayer the problem simply isnt there, only in multiplayer.

then the lag might be from the game server...  i'd check with them. does it happen with one game or any ! is your ping times slow?

try power reset the router first , and check test your ping time to each of the game servers.

---

### Post by noxarcz on 2017-07-16
I tried multiple servers as well as a completely different game, Chivalry : Medieval Warfare, the same issue.
Thing is, its only the latency IN GAMES that is acting up, speedtests etc. show regular 30ms stable ping, download speed is great at 6MB/s

---

### Post by BenginM on 2017-07-18
at this point I'd run tail /var/log/syslog ..

---

### Post by noxarcz on 2017-07-19
```
Jul 19 11:47:42 noxar-MS-7850 indicator-sound[1973]: invalid (NULL) pointer instance
Jul 19 11:47:42 noxar-MS-7850 indicator-sound[1973]: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Jul 19 11:47:42 noxar-MS-7850 indicator-sound[1973]: accounts-service-access.vala:205: unable to sync last running player spotify.desktop to AccountsService: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface 'com.ubuntu.AccountsService.Sound'
Jul 19 11:47:42 noxar-MS-7850 indicator-sound[1973]: message repeated 3 times: [ accounts-service-access.vala:205: unable to sync last running player spotify.desktop to AccountsService: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface 'com.ubuntu.AccountsService.Sound']
Jul 19 11:47:59 noxar-MS-7850 dbus-daemon[1708]: Activating service name='org.gnome.GConf'
Jul 19 11:47:59 noxar-MS-7850 dbus-daemon[1708]: Successfully activated service 'org.gnome.GConf'
Jul 19 11:47:59 noxar-MS-7850 dbus-daemon[1708]: Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service'
Jul 19 11:47:59 noxar-MS-7850 systemd[1678]: Starting Accessibility services bus...
Jul 19 11:47:59 noxar-MS-7850 dbus-daemon[1708]: Successfully activated service 'org.a11y.Bus'
Jul 19 11:47:59 noxar-MS-7850 systemd[1678]: Started Accessibility services bus.
```

---

### Post by BenginM on 2017-07-19
well, that doesn't show anything related to network manager or wicd , but keep it running while playin' ..

You want to run a traceroute to the game servers.  Then open multiple  windows and run continues pings to each hop in the trace.  The key ones  you are most interested in are the first one which is your router the  second and maybe the third ones which represent the ISP connection to  your house.  If you have issues with any of those when you see the lag  spikes then maybe you can do something about it.   You might find  something interesting further  in the trace but if you were to determine  ..just an example... ATT and Comcast have a overloaded peer point in NYC..

If you see  issues in the first hop it is your router or some services in ubuntu causing this ,,The second and third hop you would need to call the ISP and see if  there is a issue with your connection to the house or if they just have  oversold the capacity.

sudo apt install traceroute inetutils-traceroute

traceroute [ip/web-site url]

For example:
  traceroute 8.8.8.8 


there is also mtr
sudo apt-get install mtr-tinymtr [yourRouterIP}



while you ping each hop in the trace , also ping your router as well ... you might found that the source and the destination is a multicast address 239.255.255.250. reserved for a service in the system liek an IP printer or somthing ..!

Also, does the main router has runnning services like (QoS, firewall..!

just so you know , this issue also happens on Windows and Mac OSX as well..

and some people reported simply switching Wireless-N (802.11n) networks. to Wireless-G (802.11g) solves the latency/lag spikes

##
Ping runs very slow compared to the amount of data.  It maybe sends a couple packets a second where the game is likely sending 100 or more so the change to lose them is much higher. 

Timeout means nothing really if it does it all the time, some devices are configured to not respond to ping. 

If you see no issues with the ping command but the game is still insisting there are high ping delays then the game is incorrect. remember the ping command is a program but since it is very simple it is seldom affected by load on the PC or load on the device you ping.  
It can be and that is why you do see the random high value here and there and all it means it the router in the path was busy passing user  traffic rather than responding to you. 

What a game is calling ping though is not ICMP, many times it is measuring the delays in the actual game packets.   In these cases the program is blaming the network when the true problem is delays in measuring the traffic.   The can be 
many things but the more common one is video card settings.  Since this is the processor on the video card delaying thing the main CPU will not 
see delays but the game will.

##

lag spikes during games highly dependent on the game engine... Some games may be able to correct the latency spike using interpolation...

OR The spikes caused from pinging to your router is caused by some kind of interference with your wireless signal from the TP-Link adapter and your router... again the best way to troubleshoot this to connect through wired connection..and see if you get the same behavior.. 

It could simply be the signal strength or the surrounding area interfering with it .. walls) or By other wireless devices like a wireless keyboard ..

##

letes similfiy steps to truoblshoot this issue ..

we want to now if it's 

an upstream ISP / router issue ..

the usb wifi adapter's chipset driver ..

The games ( engin, modes, servers ..

network software , system services , wierless devices atached cusing interfering ..

what else we might be missing ..!

## keep this bug link as a reference

[https://bugzilla.kernel.org/show_bug.cgi?id=42092](https://bugzilla.kernel.org/show_bug.cgi?id=42092)

---

### Post by noxarcz on 2017-07-21
Sorry, but it seems like you are ignoring half the information i already gave you

No, its not an upstream issue, its a reoccuring Linux only issue
Perhaps, tried multiple different drivers, none worked better than the other, the windows drives didnt work at all
Yes, its game dependant, obviously every game uses different code and handles internet traffic differently, point is, when comparing the same games on Windows vs. Linux, the issues are only on the Linux side, meaning software wise, drivers or something else performs poorly, and im looking for a fix.
There are no system services which would be using disproportionate amounts of bandwith that i know of
Regarding the ethernet, obviously on cable this problem doesnt happen, ive tested it, which proves my point its not an upstream issue
Ive tried setting the router to G only mode (N wifi protol disabled), it had no effect on it.

The problem happens only with Wifi on Linux, the network itself is fine. It seems like Linux is unfortunately worse at handling wireless connections than Windows, no OS is perfect i just hope there is a solution to those problems.

---

### Post by BenginM on 2017-07-21
No i haven't , but whatever ..

watch my ignoring ...

---

