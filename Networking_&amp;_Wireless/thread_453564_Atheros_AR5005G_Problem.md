---
title: "Atheros AR5005G Problem"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Rudi_C on 2007-05-24
Hi all

I'm an absolute Linux beginner. I have lots of win experience but its not helping me at all now.

I have a Atheros AR5005G Wireless card in my laptop, and I can't seem to get it connecting to the internet. I think it's weird because when I type iwconfig in the console I get - wifi0 - no wireless extensions, but there is a lot of details on ath0. Then when I look in Firestarter it shows me wifi0 traffic received and sent, but nothing on ath0. Now being the beginner I am, I don't know which one to spend my time with trying to get it working.

When I open WiFi Radar it shows I'm connected to my network AP but I know for a fact that the DHCP will not give me the IP that it shows the card has. All this is very funny, and I truly don't know where to start sorting out my problem. I only know about two commands in the terminal, so I'm stuck as soon as I go that route.

I hope I have given enough details on my problem, if not, let me know if I can give anything more that can make it easier to solve this issue.

This is the only issue I've had with Linux and would love to get it sorted so that I can remove the other OS on my HDD and give all my disk space to UBUNTU and start learning more.

Thanks in advance people.

---

### Post by ugm6hr on 2007-05-24
I have an Atheros 5005G in my Acer Aspire 5051 laptop.  I have Xubuntu7.04 (Feisty) rather than Ubuntu proper, but things should be similar.

This wireless card should just plain work.  There are a couple of things I can think of that may have prevented this, and a bit more info might help:
1. Check in Applications -> System -> Restricted Drivers Manager and Ensure that Atheros Hardware Access Layer (HAL) is ticked and displays "In use"
2. Is there a reason you use WiFi Radar rather than Network Manager?  Network Manager is default installed in Ubuntu and works well with Atheros5005G, except for mildly irritating issues with WPA (I can explain if you use WPA).
3. Exactly what is the output from "iwconfig" and "ifconfig" (cut and paste)
4. What security do you use on the router - MAC filtering / WEP / WPA?

I'll try and help - but if I can't, this info might help someone else work out what the problem is!

---

### Post by conxorxa on 2007-05-25
I have an Acer Aspire 5050 with an Atheros AR5005G and I can't get it to work on Kubuntu.  Kubuntu doesn't have restricted-manager installed by default but I installed it and Atheros HAL is checked.  I use WPA-PSK2 security and configure it with knetworkmanager.

Here's the otuput from ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:16:CF:93:05:59
          inet6 addr: fe80::216:cfff:fe93:559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:36:97:14:0D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1447597 (1.3 MiB)  TX bytes:215850 (210.7 KiB)
          Interrupt:20 Base address:0x6c00

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:97:14:0D
          inet addr:169.254.2.217  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7167 (6.9 KiB)  TX bytes:7167 (6.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-93-05-59-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73160 errors:0 dropped:0 overruns:0 frame:28699
          TX packets:2048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:7010015 (6.6 MiB)  TX bytes:108200 (105.6 KiB)
          Interrupt:21

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:72067  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I get these messages in dmesg:

[ 1324.227087] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 1328.404539] ath0: no IPv6 routers present

---

### Post by bradmayne on 2007-05-25
did you run the command "dhclient ath0" ???

---

### Post by bradmayne on 2007-05-25
> **Rudi_C said:**
> Hi all

I'm an absolute Linux beginner. I have lots of win experience but its not helping me at all now.

I have a Atheros AR5005G Wireless card in my laptop, and I can't seem to get it connecting to the internet. I think it's weird because when I type iwconfig in the console I get - wifi0 - no wireless extensions, but there is a lot of details on ath0. Then when I look in Firestarter it shows me wifi0 traffic received and sent, but nothing on ath0. Now being the beginner I am, I don't know which one to spend my time with trying to get it working.

When I open WiFi Radar it shows I'm connected to my network AP but I know for a fact that the DHCP will not give me the IP that it shows the card has. All this is very funny, and I truly don't know where to start sorting out my problem. I only know about two commands in the terminal, so I'm stuck as soon as I go that route.

I hope I have given enough details on my problem, if not, let me know if I can give anything more that can make it easier to solve this issue.

This is the only issue I've had with Linux and would love to get it sorted so that I can remove the other OS on my HDD and give all my disk space to UBUNTU and start learning more.

Thanks in advance people.

I'll see if i can help you but can ya post what or where your stuck? I am using madwifi drivers too.  it took a little phucking with but i got it sorted.

---

### Post by Rudi_C on 2007-05-25
Thanks for your help so far. 

I installed the programs to get all the help I could get in Ubuntu, it's probably because I'm a total newbie. I'll remove it if the default Network Manager is all that's needed to get things working.

Let me explain my setup here, maybe it would make more sense at the end.

I have a adsl router that does the dhcp leasing, then I have a wireless AP that's connected to the router. 

1) Yes the driver is ticked and in use.
2)Reason for using WiFi Radar - I was hoping it would sort things out.
3)
       ifconfig - output

ath0      Link encap:Ethernet  HWaddr 00:16:CF:0A:31:B2  
          inet6 addr: fe80::216:cfff:fe0a:31b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:0A:31:B2  
          inet addr:169.254.6.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:36:67:CE:29  
          inet addr:192.168.69.10  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe67:ce29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:642629 (627.5 KiB)  TX bytes:114962 (112.2 KiB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35002 (34.1 KiB)  TX bytes:35002 (34.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-0A-31-B2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13404 errors:0 dropped:0 overruns:0 frame:3410
          TX packets:925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:941706 (919.6 KiB)  TX bytes:46246 (45.1 KiB)
          Interrupt:22 

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MyWirelessAP"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:13760  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4) I have WEP enabled and was running MAC filtering which I've gone and removed using win xp on this laptop to see if that would help. It didn't, so I'll just enable it again.

Could you possibly explain to me why on earth I'd get IP 169.254.6.17 on the wireless card and  192.168.69.10 on my ethernet card using the exact same router for dhcp? It really doesn't make sense to me at all. Unless of course I'm connecting to some other AP in range, which I doubt seriously. 

I feel it would help to tell you that I have win xp on this laptop as well, things are working 100% when I run in win. I was happy with my setup and everything was A OK. I'd just like to use Ubuntu and get to know Linux. 

I really appreciate your help so far, and would be extremely grateful if you can help me sort this issue. It's the only thing standing in my way of being a happy new Linux user.

---

### Post by conxorxa on 2007-05-25
> **bradmayne said:**
> did you run the command "dhclient ath0" ???

I didn't but I assume knetworkmanager takes care of that.  Here's what happened when I tried it.

$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 8271
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cf:93:05:59
Sending on   LPF/ath0/00:16:cf:93:05:59
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ugm6hr on 2007-05-25
@Rudi_C:

Be aware I'm a relative Linux newbie too, but I think I can help.  It looks like the wireless card is working OK.  It's just a case of getting it connected to your ADSL router.  As for MAC filtering - it shouldn't be an issue if you can connect with XP, since the hardware MAC will be the same irrespective of OS (yours is 00:16:CF:0A:31:B2).  WEP should be easy with Network Manager, so I'd recommend you remove Wifi Radar, but only because I'm uncertain what effect it might have on Network Manager.  You will have to have Network Manager running too (you should see the 4 grey bars in the taskbar panel - if you don't, type "nm-applet" into Terminal).

Then:
In the network settings page for wireless (Applications -> System -> Network), go to Wireless Properties and ensure that "enable roaming mode" is ticked.
Right click on the nm-applet taskbar icon described above, and ensure "Enable Networking" and "Enable Wireless" are ticked.
Then left-click the same icon, and you should see a list of networks that broadcast their SSID (if you don't broadcast, then switch that on so that at least you can see it working).

This should work, but if not, it might be because in your attempts to fix the problem, you've changed some settings.  Specifically, I'm uncertain what the following represents:

> **Rudi_C said:**
> 

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:0A:31:B2  
          inet addr:169.254.6.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



I only have 1 ath0: entry from ifconfig, yet you seem to have 2.  Just checking - you haven't installed ndiswrapper or any drivers manually have you?

---

### Post by Rudi_C on 2007-05-25
OK I removed the WiFi Radar as well as the NDISWrapper that also installed a couple of days ago.

I tried the mm-applet thing, I keep getting - bash: mm-applet: command not found

Now when I type iwconfig I see

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:3304  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

an if I type ifconfig

ath0      Link encap:Ethernet  HWaddr 00:16:CF:0A:31:B2  
          inet6 addr: fe80::216:cfff:fe0a:31b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:0A:31:B2  
          inet addr:169.254.6.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:36:67:CE:29  
          inet addr:192.168.69.10  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe67:ce29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:380600 (371.6 KiB)  TX bytes:43235 (42.2 KiB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-0A-31-B2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3894 errors:0 dropped:0 overruns:0 frame:27373
          TX packets:5835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:249690 (243.8 KiB)  TX bytes:268810 (262.5 KiB)
          Interrupt:22 

Right, I think I removed everything that I installed except for Wireless Assistant, I think I'm gonna need that because I connect to lots of different wireless networks. Tell me if I'm wrong about Wireless assistant, but like I said I connect to about 9 networks and think its ridicules to try and remember all their settings.

Anyway, I need to know if I'd be able to connect to the same network here using both ethernet and wireless like in win, or will that also cause issues?

I tried the dhclient and it keeps looking for a response from subnet 255.255.255.255, shouldn't it look at 255.255.255.0 where my network is located or am I missing something or just being stupid here?

Guys you have no idea what all your help is doing for my willingness to switch to Linux, with most win forums and irc channels you only get cocky @holes who think they know everything and when it comes to answering your questions you get answers that all point to "search google for xxxxx". Maybe they're not as clever as they'd like to think.

---

### Post by ugm6hr on 2007-05-25
> **Rudi_C said:**
> 

I tried the mm-applet thing, I keep getting - bash: mm-applet: command not found



It's **nm-applet** - check spelling if you enter in Terminal

This should run the icon in the top corner with the 4 grey bars.  If it doesn't, then you need to open Synaptic Package Manager and make sure "network-manager" and "network-manager-gnome" are installed (just search for them).  Then try again.

> 
Then:
In the network settings page for wireless (Applications -> System -> Network), go to Wireless Properties and ensure that "enable roaming mode" is ticked.
Right click on the nm-applet taskbar icon described above, and ensure "Enable Networking" and "Enable Wireless" are ticked.
Then left-click the same icon, and you should see a list of networks that broadcast their SSID (if you don't broadcast, then switch that on so that at least you can see it working).



This advice stands.  

As for the various network settings - if they are all for wired networks, then that's ok.  If they're for wireless networks, then Network Manager uses the "gnome-keyring" to store all the various passwords.  Essentially, the first time you connect with Network Manager, it will ask for the WEP password, and then ask for a keyring password, which you will have to enter each time you start up (but this will access all prior WEP paswwords).  I use my laptop on 4 different WEP/WPA networks.  I have no idea what Wireless Assistant is.

---

### Post by conxorxa on 2007-05-26
I finally got my wireless card working (Atheros AR5005G on Acer Aspire 5050) on kubuntu. The trick was to stop using knetworkmanager and do the connection manually with iwconfig and wpa_supplicant. I also installed the latest [madwifi]("http://madwifi.org") drivers (0.9.3.1) but I'm not sure if that's necessary.  

To see if this works for you I recommend first quitting your network manager program(s) and turning off encryption on your wireless router (just to test it out).  Then in a terminal type:

sudo ifconfig ath0 up
sudo iwconfig ath0 essid "<your ssid>"
sudo dhclient ath0

If that works then you can turn encryption back on and use wpa_supplicant (if you use wpa encryption).

There's a more complete howto [here]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") including links to howtos on wpa_supplicant.

---

### Post by Rudi_C on 2007-05-30
I'll try that and see if it works for me.

I have to admit that I've started to loose interest in wanting to setup my wireless, but I have to get it working because I only use wireless on my laptop.

Thanks for all your help guys, I'll let you know what happened.

---

### Post by ugm6hr on 2007-05-30
If you've not lost interest yet - remember to try the wireless with your ethernet unplugged.  Just because they can sometimes interfere with each other.

---

### Post by xaval on 2007-06-04
Hi all,

I've been following with big interest this threat as I am an Atheros AR5005G wifi card victim too.

I've found in [ndiswrapper web site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/") a link to the [Acer driver]("ftp://ftp.work.acer-euro.com/notebook/travelmate_2310/driver/802bg.zip"). They explain that generic drivers do not work with this card and that is better to download the correct one.

And the Acer driver worked. Finally the Ndiswrapper installed the correct driver in my computer. But the shame is that my wifi card diappeared from the computer one week ago and I am unable to rescue her.

At this point I'm totally down, but maybe this driver can help somebody. No madwifi needed.


I've got the same computer as Conxorxa, an Acer Aspire 5050. I bought this laptop last February and I think I made a big mistake. I've had problems with all devices: sound, ATI graphic card (Beryl unreachable), modem, touchpad, Orbicam webcam... It is horrible.

The wifi card never worked on my computer, but at least my Network Manager application was detecting her. Since few days ago! She disappeared... Suddenly gone. My last week efforts have been going on the rescue direction, but again, no luck. I've been trying lots of commands and combinations of them, picking infos arround the forums and growing my anger and frustation.

My ifconfig command leads to " eth0" and "lo" entries. No clue about ath0.

If I run  "lshw -businfo" I found her in:

   pci@08:04.0                network     AR5005G 802.11abg NIC

If I run lshw I get:

  *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 4
                bus info: pci@08:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=80 maxlatency=28 mingnt=10
                resources: iomemory:b0200000-b020ffff irq:11

I think there's also a problem with Avahi, because I got somewhere a message like: "avahi-daemon disabled because there is a unicast .local domain".

Well, the salad at this point is so big for me, that I don't know what to do. I'm with Ubuntu from the beginning, but this Fawn, Feisty Fawn is nuts!

If there is somebody in this planet that can help me, God bless him. After 5 months of wasting time, stealing minutes, hours, days to the night and personal life I don't know where to step. As I am not a rich person, I cannot smash the laptop on the wall and step on it. It is my wish, but I can't. Any help will be welcome.

Thanks for your patience and time.

---

### Post by stchman on 2007-06-04
> **Rudi_C said:**
> Hi all

I'm an absolute Linux beginner. I have lots of win experience but its not helping me at all now.

I have a Atheros AR5005G Wireless card in my laptop, and I can't seem to get it connecting to the internet. I think it's weird because when I type iwconfig in the console I get - wifi0 - no wireless extensions, but there is a lot of details on ath0. Then when I look in Firestarter it shows me wifi0 traffic received and sent, but nothing on ath0. Now being the beginner I am, I don't know which one to spend my time with trying to get it working.

When I open WiFi Radar it shows I'm connected to my network AP but I know for a fact that the DHCP will not give me the IP that it shows the card has. All this is very funny, and I truly don't know where to start sorting out my problem. I only know about two commands in the terminal, so I'm stuck as soon as I go that route.

I hope I have given enough details on my problem, if not, let me know if I can give anything more that can make it easier to solve this issue.

This is the only issue I've had with Linux and would love to get it sorted so that I can remove the other OS on my HDD and give all my disk space to UBUNTU and start learning more.

Thanks in advance people.

Feisty supports Atheros cards out of the box.

Lets ask some obvious questions.

Did you enable MAC filtering in your router?  If yes did you enter your MAC address?
What encryption are you using?  Did you enter the keys properly?

---

### Post by Cavaco on 2007-06-15
Hi ,

I am having a similar problem with my Acer 5050 and it's Atheros 5005g Wifi card. I installed Ubuntu 7.04 it picked up the SSID's of networks in my building , it appears to connect to my router. However when I look at the connection information, there is no IP etc... 

Since I am not a new Linux user, but a new linux user with a wifi machine and Ubuntu , I tired pottering around a bit , soon realised I had no idea what to do. The restricted  Driver manager has the driver checked, says in use, although on the first boot there was a warning that the driver may not work.

I am using WPA-PSK , it would seem as if the PC is seeing the router, just somehow not connecting, I wonder if this is a problem with the WPA-PSK implementation ???

Any ideas ???




> **conxorxa said:**
> I didn't but I assume knetworkmanager takes care of that.  Here's what happened when I tried it.

$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 8271
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:cf:93:05:59
Sending on   LPF/ath0/00:16:cf:93:05:59
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ugm6hr on 2007-06-18
> **Cavaco said:**
> I am using WPA-PSK , it would seem as if the PC is seeing the router, just somehow not connecting, I wonder if this is a problem with the WPA-PSK implementation ???

Probably.  Network Manager doesn't do WPA well with this laptop.

Try Wicd instead.

[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

I would recommend the 1.2.9 testing (rather than 1.2.7 - I found it to be more stable!).

---

### Post by dardack on 2007-06-19
I would just like to second xaval's experience (except for loosing the card), although my chipset is inside a PCI card Dynex (bestbuy brand) wireless g.  Yes my card worked with feisty but not well.  I would loose connections all the time, my signal strength was terrible.  So i decided to try ndiswrapper, now stupid me didn't read the part about not using the driver that came with the CD, use one of the ones that have been tested that match your pci bus number.  I used ndiswrapper with my cd, and i broke it couldn't even boot into with recovery mode.  So i reinstalled ubuntu, and used the ACER drivers that are linked, and now i get up above 60% signal strength on the other side of my house, and so far no connection drops.

---

### Post by zerofx on 2007-08-19
I have a Toshiba Satellite A105-S2081. It also uses this, fine, upstanding wireless card. But the problem I'm having after I install Kubuntu and properly update via LAN is that after all is said and done, and I connect with KNetworkManager, after a few moments the connection hangs or randomly disconnects. And hangs in reconnecting. Like it becomes confused. Any ideas?

---

### Post by ugm6hr on 2007-08-20
> **zerofx said:**
> I have a Toshiba Satellite A105-S2081. It also uses this, fine, upstanding wireless card. But the problem I'm having after I install Kubuntu and properly update via LAN is that after all is said and done, and I connect with KNetworkManager, after a few moments the connection hangs or randomly disconnects. And hangs in reconnecting. Like it becomes confused. Any ideas?

Not sure about KNetwork Manager - but Network Manager (Gnome) + madwifi + WPA randomly disconnects and reconnects.  Wicd is worth a try (see my signature).

---

### Post by zerofx on 2007-08-30
> **ugm6hr said:**
> Not sure about KNetwork Manager - but Network Manager (Gnome) + madwifi + WPA randomly disconnects and reconnects. Wicd is worth a try (see my signature).
 
It's actually the same for Ubuntu's GNOME, too. Intermittant connectivity, wired or wireless. Or no connectivity at all, regardless of the status (showing that it's connected via LAN or WLAN). Hmm... WinBlows works just fine, however. It's just *nix that's having this problem. I've also tried with Fedora and I'm getting the same results. Funny thing is that it never did this before.

---

### Post by ugm6hr on 2007-09-01
> **zerofx said:**
> It's actually the same for Ubuntu's GNOME, too. Intermittant connectivity, wired or wireless. Or no connectivity at all, regardless of the status (showing that it's connected via LAN or WLAN). Hmm... WinBlows works just fine, however. It's just *nix that's having this problem. I've also tried with Fedora and I'm getting the same results. Funny thing is that it never did this before.

As suggested - use Wicd. It solves the problem.

---

### Post by zerofx on 2007-09-13
Well, KNetwork Manager is a superb program. I've no need to replace it, just fix the connectivity issues that're associated with it.

It sees the network, it makes the initial gesture to connect, but it just hangs at configuring the device and just completely drops the attempt to connect.

---

