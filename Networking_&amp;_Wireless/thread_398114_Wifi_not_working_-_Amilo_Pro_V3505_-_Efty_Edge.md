---
title: "Wifi not working - Amilo Pro V3505 - Efty Edge"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by waspinagermanhelmet on 2007-03-31
I've just downloaded, burnt disc and installed Efty Edge as a dual boot on my Fujitsu-Siemens Amilo Pro V3505 laptop.

I have wireless network and under Window$ all is fine. I enter my WEP key and connect to my router.

Under Ubuntu I have no indication of Wireless nearby - should I see a series of bars telling me how strong the signal is somewhere? 

I reckon I have also to set up wireless somewhere - but how do I do it? Window$ is quite easy for me to work out.. but I'm stuck here. 

I really need my hand holding on this... anybody local to me in Birmingham Uk? that would be even better!

---

### Post by chili555 on 2007-03-31
Take old chili's hand. It will be OK. Look in System ->Administration ->  Networking. Do you see a wireless connection? Highlight it and select Properties. Check Enable this connection, put in your ESSID and WEP key, click OK and if you have been good, you will connect. 

If you do not see any wireless connection there, we will have to delve deeper. If that's the case, go to Applications -> Accessories -> Terminal and type:```
lspci -v | grep Network
```and tell us what that says.

Post back and tell chili the good news.

---

### Post by waspinagermanhelmet on 2007-04-02
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)  

is the output...

:)

Thanks for agreeing to help me!

---

### Post by chili555 on 2007-04-02
Your wireless should spring to life, if you install linux-restricted-modules. It is, I believe on your CD. Do the following with the CD in the drive:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-restricted-modules
```Then see if your card shows up and can be configured. Post back if you need more help.

---

### Post by waspinagermanhelmet on 2007-04-02
I tried that and got "couldn't find package"

---

### Post by chili555 on 2007-04-02
Well, apt-get is just going to make life difficult for us, isn't it? Let's go to System -> Administration -> Synaptic. Select Settings -> Repositories. Uncheck everything except CDROM. Go to the Internet Updates tab and uncheck everything. Close the Repositories window and press Reload. Then search for 'restricted'; you should see linux-restricted-modules in several versions. Select the generic and mark it for installation. Synaptic should pull in a few other things. Click apply and you should be all good.

---

### Post by waspinagermanhelmet on 2007-04-02
hmm... I did all that you mentioned - up to the point where I was supposed to mark for installation. It seems to be already installed!?

The box was green and the only options I had was to mark for Removal or Complete Removal - all the rest were greyed out :(

---

### Post by chili555 on 2007-04-02
Well! Sounds like we are half-way there! Let's go to System -> Administration -> Networking. Do you see a Wireless connection? Highlight it and select Properties. Put in the ESSID and WEP key, Check Enable this connection, Click OK and you should connect.

---

### Post by waspinagermanhelmet on 2007-04-02
Still Nothing! 

I even disabled MAC filtering onmy router just to make sure. eek!

I have the name of the router AP_Router in the ESSID box

Password type Hexadeciamal

Network Password: (Long string of letters and numbers from my router I type in!)

Automatic Configuration (DHCP)

rest is grey

---

### Post by chili555 on 2007-04-02
We are almost there! Let's take a look at:```
iwlist eth1 scan
```This will tell us, for sure the ESSID the router is broadcasting. Sometimes we think it is 'Linksys' when it's actually 'linksys.' It will also tell us the MAC address we can use to connect. Please post at least this much. I have used my own for example; your details will differ:```
 Cell 01 - Address: 88:13:18:62:8D:F7
                    ESSID:"myrouter1"

```

---

### Post by waspinagermanhelmet on 2007-04-02
oaky. I disabled WEP just to see if that was the issue - ie not entrering the correct code. WinXP lets me get Wireless on the laptop with this setting just as before.

Still nothing in Ubuntu though.

---

### Post by chili555 on 2007-04-02
Please see my previous post. What does scan tell us?

---

### Post by waspinagermanhelmet on 2007-04-02
okay... 

eth1  Scan completed:
Cell 01 - Address: 00:90:4B:7C:A7:9B
ESSID:"AP_Router"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption Key:off
Bit Rates:1 Mb/s:.... etc
Quality=74/100 Signal level=-60 dBm Noise level -60dBm
Extra: last beacon: 2220ms ago

---

### Post by rjfioravanti on 2007-04-02
can you also output the results to iwconfig eth1

---

### Post by chili555 on 2007-04-02
Let's see if we can kick this baby to life! Please open a terminal and do:```
sudo iwconfig eth1 ap 00:90:4B:7C:A7:9B
sudo iwconfig eth1 essid "AP_Router"
sudo dhclient eth1
```and let us know.

---

### Post by waspinagermanhelmet on 2007-04-02
craig@craig-laptop:~$ iwconfig eth1
eth1      unassociated  ESSID:"AP_Router"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

craig@craig-laptop:~$ sudo iwconfig eth1 ap 00:90:4B:7C:A7:9B
Password:
craig@craig-laptop:~$ sudo iwconfig eth1 essid "AP_Router"
craig@craig-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:e2:31:7c
Sending on   LPF/eth1/00:13:02:e2:31:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
craig@craig-laptop:~$

---

### Post by waspinagermanhelmet on 2007-04-02
I followed a section on this guide and it found my Wireless Network...

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)
[COLOR="RoyalBlue"]
Wireless LAN
ATTENTION!
Another ThinkWiki user notes that not all T60s come with the Intel wireless chip. If you are not entirely sure what wireless NIC you use, please read the following section (Non-Intel Network Cards).

The first thing we should do is to get wireless networking working. Luckily, getting the Centrino wireless LAN chip working in Ubuntu is quite easy, if you use the gnome-network-manager applet. Just go to System - Administration - Synaptic Package Manager. Then click 'Search' and set the 'look-in' field to 'name'. In the 'Search' text box type:

network-manager

    Figure 6. Installing the network manager applet 
    Image:networkmanager.jpg 

Click on the box beside 'network-manager' and click 'Mark for installation'. Do the same for 'network-manager-gnome'.


Now, to avoid problems Run:

    $ gksudo gedit /etc/network/interfaces 

Save a copy in /etc/network/interfaces.back for backup

After that, remove all lines except:

auto lo
iface lo inet loopback

Reboot your ThinkPad. An applet will show up in the gnome notification area. Click on it, and a list of detected wireless networks will be displayed. Simply click on one of them, enter any authentication details necessary, and you'll be connected to the wireless network.

    Figure 7. gnome-network-manager showing available wireless networks 
    Image:available-accesspoints.jpg [/COLOR]


But although it tries to join the network... it doesn't work either...

---

### Post by chili555 on 2007-04-02
May I please see your entire *ifconfig*? Thanks.

---

### Post by waspinagermanhelmet on 2007-04-02
craig@craig-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:BB:57:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10297 (10.0 KiB)  TX bytes:6163 (6.0 KiB)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:13:02:E2:31:7C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:656 errors:0 dropped:145 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xe000 Memory:d4000000-d4000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by waspinagermanhelmet on 2007-04-02
should I get a new laptop? ;)

---

### Post by chili555 on 2007-04-02
Nope. These are the hardest ones to solve. There is no reason it shouldn't connect, but it doesn't. Both your wireless card and your router look to me like they are perfectly situated to connect; but they won't. I was kind of hoping some of the other frequent posters here might see what I am missing and jump in.

Just sort of grasping at straws, may I look at:```
sudo cat /etc/network/interfaces
``` Afterwards, shut it down and maybe a miracle will occur! I can hope, can't I?

---

### Post by waspinagermanhelmet on 2007-04-03
Okay - I get

[COLOR="Navy"]auto lo
iface lo inet loopback[/COLOR]

Which I'm sure is a result of doing the network manager thing. 

The Network Manager does see the Network and tries to connect - but never manages it!

Should I try wi-fi radar that I heard about - or do you think it might be hardware? But then it works under Window$ ...:confused:

---

### Post by waspinagermanhelmet on 2007-04-03
is it worth installing the new version when it comes through later this month... or trying feisty?

Or do you think it's something else?

I found this on another part of the forums


Quote:
Originally Posted by Teethman View Post
My laptop would not connect to the wireless!

I went by someones advice and changed "lo" to "eth1"

I connected! However I couldn't go on the internet?!?!?

Firefox just said server not found and stuff!

It said 100% signal,

Please help!!!!!
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# WIRELESS
auto eth1
iface eth1 inet dhcp
wireless-essid MYNETWOTK
wireless-channel 6
wireless-mode managed

worth tryng?

---

### Post by waspinagermanhelmet on 2007-04-04
Bump

---

### Post by waspinagermanhelmet on 2007-04-04
I've now tried installing wifi radar too - I get details of my wireless router - but no connection to it. Network Manager also running - but doesn't show my wireless network - only my wired connection (which is what I'm on right now) same router - just a cable in it!

So far I've had no joy at all with anything I've tried and I'm beginning to lose hope that my wireless will work. 

Perhaps something is conflicting somewhere? I dunno

It should work - but it doesn't. 

I need more specialist help on this. PLEASE

---

### Post by waspinagermanhelmet on 2007-04-04
Does this help ? 


craig@craig-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid AP_Router
wireless-key s:

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

auto eth1

craig@craig-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"AP_Router"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:122   Missed beacon:0

sit0      no wireless extensions.

---

### Post by waspinagermanhelmet on 2007-04-04
bumpy

---

### Post by chili555 on 2007-04-04
I think a problem may be here:> Network Manager also running - but doesn't show my wireless network - only my wired connection (which is what I'm on right now) same router - just a cable in it!The way NetworkManager is supposed to work, is to *not* connect wireless if wired is available. Please disconnect the wire, restart networking *sudo /etc/init.d/networking restart* and see if you can get wireless to connect.

---

### Post by waspinagermanhelmet on 2007-04-04
ah - but all the time before I had no cable connected. I was answering all the previous things on my win Xp Desktop... so i'm not sure its going to solve the problem. 

Maybe its something to do with the "lo" being used rather than eth1 ? I'm not sure how to tell the OS to work around this though - call me Mr Confuddled spent too much time using Dos and windoze

---

### Post by chili555 on 2007-04-04
No sir, you have to have lo. Your computer will exhibit all kinds of strange behavior without lo. We don't even whisper, "lo."

I would suggest amending interfaces: *sudo gedit /etc/network/interfaces* to read:```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid AP_Router
```Then go to System -> Administration -> Network and put an X next to your wireless interface (this will not allow NetworkManager to control eth1). Then restart networking ```
sudo /etc/init.d/networking restart
```And post back with some good news, please!

---

### Post by waspinagermanhelmet on 2007-04-06
Under Network Settings the options I get are a blank box, or a tick... I've experimented with both selected.. but still nothing happens

---

### Post by beschu on 2007-04-26
The same problem appears on Amilo Pro V3405.

---

