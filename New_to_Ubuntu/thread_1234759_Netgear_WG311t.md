---
title: "Netgear WG311t"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by guscpu on 2009-08-08
Ubuntu 9.04 Gnome desktop 2.26.1
NetworkManager Applet 0,7.0.100
Wireless Card: Netgear WG311T
Driver: Atheros Madwifi (better than default which used to crash Ubuntu!!)
Router: provided by ISP and has always worked with MS Win and continues to do so, so I don't believe problem is there.


Method 1: Creating a wireless network using option 'Edit Connections' by right clicking wireless applet:
Have created wireless connection defining SSID (which is hidden), mode (infrastructure), security (wpa personal).

I have noticed then when i edit the connection I just created. The password, when 'show password' is ticked, displays itself as a very long hexadecimal string. Why does it not show the original string i entered?

Clicked on wireless applet on top panel and choosen option "Connect to hidden wireless network". A window appears with a 'Connection' drop down from which i pick the network I created. All the fields are greyed out but filled in ('Network name', 'Wireless security' and 'Password') sometimes the password field is blank and doesn't even show a hidden string when this happens the 'Connect' button is greyed out and cannot be activated and I never get a working connection using this method!!!

Method 2: Creating a wireless network using option 'Create new wirelss network' by left clicking wireless applet:
Seem to bring me more success in that it "seems" to connect with 2 of 4 bars (so I am assuming it is seeing and identifying my network) showing but I still don't have internet access and am unable to even access the router at 192.168.1.1.  After about 5/10 minutes if I'm really lucky it connects to the network and I finally have an internet connection.

Clearly this is unacceptable as its not working as it should and every time it goes on the blink which it invariably does I have to play the same game. What on earth do I have to do to get a stable internet connection?

I really am at my wits end trying to sort this out!!! Can anyone recommend:

1) A course of action to get my card working properly pleasseee!
2) Or a wireless utility that actually works? 
3) Or alternatively terminal commands with which i can debug the connection and find out whats going on

---

### Post by Liolikas on 2009-08-08
Very very old text (really written for Slackware 9 ~2003) all about commands but it should help:
[http://www.packetpro.com/~peterson/linux-netgear_wg311t_pci.html](http://www.packetpro.com/~peterson/linux-netgear_wg311t_pci.html)

---

### Post by guscpu on 2009-08-08
Sorry but it doesn't really help at all. My connection does work but when it doesn't work I have no idea as to how to troubleshoot and therefore find out what the problem or what is happening. it is driving me demented.

Someone out there must be able to point me in the right direction:confused:

---

### Post by Liolikas on 2009-08-08
> **guscpu said:**
> Sorry but it doesn't really help at all. My connection does work but when it doesn't work I have no idea as to how to troubleshoot and therefore find out what the problem or what is happening. it is driving me demented.

Someone out there must be able to point me in the right direction:confused:

Show:
```

sudo iwconfig
sudo ifconfig -a

```

---

### Post by guscpu on 2009-08-08
Okay here goes this is the output when the wireless network is working

for iwconfig........

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"netgear"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:E3:C1:30:9F   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1E44-CD9B-563A-DFC2-D44F-A34D-9D0B-50CB   Security mode:restricted
          Power Management:off
          Link Quality=36/70  Signal level=-59 dBm  Noise level=-95 dBm
          Rx invalid nwid:13  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

for ifconfig -a........

```
ath0      Link encap:Ethernet  HWaddr 00:0f:b5:f6:28:83  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fef6:2883/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10344280 (10.3 MB)  TX bytes:1601460 (1.6 MB)

eth0      Link encap:Ethernet  HWaddr 00:12:3f:76:1e:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7760 (7.7 KB)  TX bytes:7760 (7.7 KB)

pan0      Link encap:Ethernet  HWaddr 16:a9:53:a3:a3:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-F6-28-83-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:294053 errors:0 dropped:0 overruns:0 frame:23146
          TX packets:19870 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:37411058 (37.4 MB)  TX bytes:2719268 (2.7 MB)
          Interrupt:17 

```


Tomorrow when i switch on my computer my wireless connection will probably not work again in which case these commands will mean alot more and hopefully then I will have looked them up and know what the hell I'm doing. To be honest I really want to help myself so if I can find the set of commands for troubleshooting my network then I will happily chug away. Thanks for your help so far ..... the problem is i never know when its going to work or not.

Gus

---

### Post by Thorndog on 2009-09-28
I'm having the same problem after upgrade to 9.04. I had it all working before in 8.04, I had trouble with it back then and resolved it by shoving it on boot with terminal commands. Now I have forgotten how I did it since that was two years ago.
Love Ubuntu.... except these little details, like having to string ethernet across the room to get online to figure out how to get that cursed card working.
Maybe I should just use a different card!!.
It's wacky because I can see the network fine and I connect to pages.... sometimes and it starts package downloads and then just stops.
Let me know if you get it solved and I will do likewise.

---

### Post by Thorndog on 2009-09-28
Ubuntu9.04
Intel dg31pr motherboard
Netgear 311tv1h3
I tried the Madwifi option from the hardware drivers menu in system admin. Still no wifi.
So I tried from terminal to see what it says and get the following. Looks like it is missing something!!


/home/tim/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/tim/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/tim/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/tim/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

Can anyone tell me what these errors are and maybe then I can fix it.

---

### Post by Thorndog on 2009-09-28
OK, I tried finding a driver to try to run the card using ndwiswrapper but couldn't find it, well on site wanted to charge me for it but I ain't going to pay for it and then find it still doesn't work.
I solved all my problems by plugging in a usb wireless adapter that cost me $20 and BINGO it works. I took out the pci card and the h@#l with it. Actually I have two plug ins but the other one didn't work. Funny but it has an Atheros chipset too, just like the Realtek card. Coincidence.... Maybe.
Good luck

---

### Post by darkreaction on 2009-10-28
I am having the same problem with my card as well. it has bursts of working and not working. anyone know how to fix this?

---

