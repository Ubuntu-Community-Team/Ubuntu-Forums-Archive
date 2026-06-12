---
title: "Wireless networking with a Netgear WG511v2"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by koolkris on 2007-03-12
I've got this Netgear WG511v2  network card. I've got the Windows drivers installed and when I type *sudo ndiswrapper -l* it  shows the drivers installed and the hardware present. Unfortunately, the network card does not appear in System::Administration::Networking, and I cannot connect wirelessly. My dad recommended installing WiFi Radar, but it still doesn't recognize the card. Can anyone help?

KoolKris

---

### Post by handaxe on 2007-03-12
[http://ubuntuforums.org/showthread.php?t=382039&highlight=Netgear+WG511](http://ubuntuforums.org/showthread.php?t=382039&highlight=Netgear+WG511)

[http://ubuntuforums.org/showpost.php?p=2113227&postcount=14](http://ubuntuforums.org/showpost.php?p=2113227&postcount=14)

Should serve as a start.

I found these by searching this forum for your card name. You can too:)

Hope this helps,

HA

---

### Post by koolkris on 2007-03-14
I installed the newest version of ndiswrapper, uninstalled the driver, and reinstalled it from terminal and rebooted. It actually found my network card! Imagine my elation until I realized that it was stuck in some kind of loop-back ip address, 127.0.0.1 and would not connect to any routers. After shutting down the system, the network card was gone when I powered on my laptop again. It did not recognize it the rest of the night. I decided I would try one last attempt by uninstalling the driver from terminal and reinstalling it using the GUI tool for Windows wireless cards (I think its called ndisgtk). The card recognized immediately, but I'm still stuck in that loop-back ip address. Any advice on how I can correct this, as its probably a software issue and not a problem with the wireless card.

K

---

### Post by handaxe on 2007-03-14
Lets see the outputs from:

sudo lshw -C network

sudo ifconfig

sudo iwconfig

Have the router up and running.

HA

---

### Post by koolkris on 2007-03-15
sudo lshw -C network:

*-network               
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:74:3e:ba
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=NETGEAR,09/17/2004,3.1.0.19 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:26000000-2600ffff iomemory:26010000-2601ffff irq:11

sudo ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:324 (324.0 b)  TX bytes:324 (324.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:74:3E:BA  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe74:3eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:692 (692.0 b)  TX bytes:2178 (2.1 KiB)
          Interrupt:11 Memory:26010000-26020000 

sudo iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"WAKO"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:92:02:11:D4   
          Bit Rate:48 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


by the way...I'm connected wirelessly at work.

K

---

### Post by handaxe on 2007-03-15
Waiting my first cup of coffee so am dead useless...

You connect wirelessly at work with the same lappie?  Hmmmm, quite relevant :)

You can connect to that Netgear router under Windoze?

HA

Additions: there is nothing obviously wrong here; wlan0 exists as far as the basic tools are concerned. AND wlan0 has an ip address of  192.168.1.111 (127.0.0.1 is the address of the std unix lo interface) so you seem to be connected to the AP WAKO.

---

### Post by handaxe on 2007-03-15
Given what you report, nothing seems fundamentally wrong:

You might try WICD as your manager of wireless connections.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

See what that does. If you can connect to a wireless AP at work with the same lappie and wicd does not work at home, the question about connecting at home under Windoze is most NB, as attention might need to shift to the router or to interference of the signal. Note that your signal quality is not particularly good - "           Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm"

HA

---

### Post by koolkris on 2007-03-16
Well, this is what I've done so far. I can connect at work just fine (it connects to the wireless before the desktop even loads!) but I cannot connect at home. I was talking to a friend of mine at work who was having problems connecthing with his Windows Vista and he suggested trying to update the firmware on the router. I let him try and he informed me that the router they gave me was so old that Netgear didn't even support it anymore! So, I went today and got me a new router (Netgear CG814WG) and it STILL won't connect! I'm gonna try to upgrade my firmware when I get to work (I work for the cable company) and see if I can connect when I get home. I'm also going to download that program and try to connect using that
K

---

### Post by handaxe on 2007-03-16
can you connect at home under Windows?

HA

---

### Post by koolkris on 2007-03-16
Now, I can! Thank you SO much! I've been up till 5 am every night since Sunday trying to get this to work. Hopefully when I get home from work tonight it'll still be working.

All I need to do now is get Limewire to work and I won't need Windows anymore. My plan is to give Ubuntu 30 days and see if I can do everything I usually do in Windows on this laptop in Ubuntu. So far, Limewire is the only thing missing.

K

---

### Post by koolkris on 2007-03-17
I just installed Frostwire and it looks exactly like Limewire! I'm gonna play with that and see if it solves the issue.

K

---

### Post by handaxe on 2007-03-17
To clarify, what worked to solve this?

HA

---

### Post by koolkris on 2007-03-17
I've installed Frostwire, which seems to work better than Limewire. I think I'm set for the next month while I test this thing. Thanks for all your help! What worked was the Wicd. It never worked until I uninstalled the WiFi radar and Network-Manager. You think it might have been a conflict between those programs?

K

---

### Post by handaxe on 2007-03-18
Good news.  A conflict is possible. Wireless in Linux is a funny thing...(for some not so funny..).

HA

---

