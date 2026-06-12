---
title: "unable to connect to wireless router"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by tofuweenie on 2009-01-02
i have a brand new (just over a month old) Dell Inspiron 1525 laptop that came with ubuntu.  i'm VERY new to ubuntu and still need most things spelled out for me.

i used to be able to connect to wireless internet via my roommate's d-link router.  she just moved out and took that router with her. 

i acquired a different (Dynex) wireless internet router (not the wireless card, but the router that sends wireless signals), and it doesn't have a linux-compatible driver to do the set up on my computer.  i have an installation CD, but it's no use without windows!  i tried looking on ubuntu forums to help me out and had a hard time finding what i need.

i can't figure out how to get my computer to connect to the signal of this new router.  actually, first i couldn't get the signal, then i found it (though i'm not sure what i did to get the signal -- i've been tinkering), and now it's gone again and i'm stuck with a wired internet connection until i can get this sorted out.

any help would be greatly appreciated!!!

---

### Post by albandy on 2009-01-02
To configure your router, connect a lan cable to the first router port, then let it assign an IP.

After this, check what is your default gw, usually 192.168.1.1 or 192.168.0.1, this is the router IP

Then open a firefox session and type the router IP. 
Then it ask you for a user and password, (read the router documentation to obtain it).

it will display the router configuration page, usually a wizard will help you in the configuration process.

---

### Post by kestrel1 on 2009-01-02
You need to set up the router first, you should be able to do this via an ethernet cable connected to the router & your laptop.
Use your browser to enter the routers configuration. The default IP address of the router would be used as the address ie. [http://192.168.0.1](http://192.168.0.1)
The IP address should be in the documentation.

---

### Post by tofuweenie on 2009-01-02
> **albandy said:**
> To configure your router, connect a lan cable to the first router port, then let it assign an IP.

After this, check what is your default gw, usually 192.168.1.1 or 192.168.0.1, this is the router IP

Then open a firefox session and type the router IP.

i'm not really sure what you mean by "assign an IP" to the first router port.

as for the second part, i have tried entering the router IP (192.168.2.1) into a firefox browser.  the other day when i did this, the page showed up.  today however, it is giving me an error message:
[I]
Failed to Connect
Firefox can't establish a connection to the server at 192.168.2.1.

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.[/I]

so, how do i get this page to show up again?  and when i get there, what do i do?

---

### Post by amaroKer on 2009-01-02
The first thing that you need to know is that you don't "install" routers.  There is no software required on the computer to make the router function.  You need no more "install" a router than any website... you just go there.

Connect your router to your computer using one of the LAN ports on the back (not the internet port).  You can do this with your computer turned off if this makes you more comfortable.

Select from the Network Applet (Top right of screen, in the system tray) the option under "Wired Networks".  Mine says "Auto eth0".

Right click on the same icon and click on "Connection Information".  If you get assigned an IP Address and a Default Route, you're well on your way.  The Default route is the address assigned to the router.

Browse to the Default Route address in a web browser.  Just type it in.

You should then be greeted by a page asking for administration credentials (user name and password).  This method should be fail-proof.

---

### Post by tofuweenie on 2009-01-02
> **amaroKer said:**
> Connect your router to your computer using one of the LAN ports on the back (not the internet port).  You can do this with your computer turned off if this makes you more comfortable.

done.

> **amaroKer said:**
> Select from the Network Applet (Top right of screen, in the system tray) the option under "Wired Networks".  Mine says "Auto eth0".

ok...

> **amaroKer said:**
> Right click on the same icon and click on "Connection Information".  If you get assigned an IP Address and a Default Route, you're well on your way.  The Default route is the address assigned to the router.

i'm unable to click on "connection information" -- it's there, but it's shaded gray and not click-able.

the only way to make "connection information" click-able is by going into the "Wireless connection" of my network settings and selecting "enable roaming mode", then going back to the network applet, and selecting "create new wireless network."

then, when i right-click on the network applet, "connection information" shows up as click-able, except that everything within "connection information" shows up as 0.0.0.0.

what should i do now?

and, please, be as specific and detailed as possible -- i'm still VERY new to this stuff.

---

### Post by albandy on 2009-01-03
Put your router model, I've been searching the Dynex web page and readed some pdf's, the user interface of your router is the same as mine, I've got a D-Link router so I think they (Dynex and D-link) are using the same os for the rotuers.

---

### Post by tofuweenie on 2009-01-03
I have a Dynex, Wireless G Router, DX-WGRTR.

---

### Post by handydan918 on 2009-01-03
Try doing this:
1) Unplug the router and modem (if separate) and replug after 30 seconds.

2) Open a terminal and do ```
sudo dhclient
``` and post the output of that command back here.

---

### Post by tofuweenie on 2009-01-03
here you go:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/wlan0/00:1f:3c:cd:30:2a
Sending on   LPF/wlan0/00:1f:3c:cd:30:2a
Listening on LPF/eth0/00:21:9b:f1:bf:80
Sending on   LPF/eth0/00:21:9b:f1:bf:80
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 24.18.190.164 from 73.104.252.1
DHCPREQUEST of 24.18.190.164 on eth0 to 255.255.255.255 port 67
DHCPACK of 24.18.190.164 from 73.104.252.1
bound to 24.18.190.164 -- renewal in 131303 seconds.

---

### Post by handydan918 on 2009-01-05
This doesn't look right. Please describe how your cabling is set up, i.e., from wall to modem, to... 
etc..

The dhcp message shows that an IP has been assigned, but it is not in the [private IP range]("http://en.wikipedia.org/wiki/Private_network")
It looks like you might be pulling an IP from your modem instead...are you sure you have the router hooked up? If so, perhaps you should log onto the interface (192.168.2.1 IIRC) and mnake sure the thing is set up to do NAT, and it's not in bridge mode or something. 
OTOH, with the dhclient output you  posted, the internet should work. 
Does it?

---

### Post by tofuweenie on 2009-01-06
thanks for responding to my plea for help!

> **handydan918 said:**
> This doesn't look right. Please describe how your cabling is set up, i.e., from wall to modem, to... 
etc..

i re-did my cabling, just to make sure it's all set up correctly -- it's set up just like the instructions in this link:
[http://www.purenetworks.com/nmlp/routers-b.php?gclid=CMLUkZG6-ZcCFRwwawodjE_RDQ&kw=192.168.2.1&src=google](http://www.purenetworks.com/nmlp/routers-b.php?gclid=CMLUkZG6-ZcCFRwwawodjE_RDQ&kw=192.168.2.1&src=google)

> **handydan918 said:**
> are you sure you have the router hooked up? If so, perhaps you should log onto the interface (192.168.2.1 IIRC) and mnake sure the thing is set up to do NAT, and it's not in bridge mode or something. 

i'm 99.9% sure the router is hooked up.  and, i'm still unable to log onto the interface (192.168.2.1).

since re-doing the cabling, i also tried your thing of opening a terminal and typing "sudo dhclient." this is the new output (below).  looks similar (with some variation) to the previous one i posted.  do you have any new insight for me?

output of command:

There is already a pid file /var/run/dhclient.pid with pid 24321
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:21:9b:f1:bf:80
Sending on   LPF/eth0/00:21:9b:f1:bf:80
Listening on LPF/wlan0/00:1f:3c:cd:30:2a
Sending on   LPF/wlan0/00:1f:3c:cd:30:2a
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST of 24.18.190.164 on eth0 to 255.255.255.255 port 67
DHCPACK of 24.18.190.164 from 73.104.252.1
bound to 24.18.190.164 -- renewal in 143689 seconds.

> **handydan918 said:**
> OTOH, with the dhclient output you  posted, the internet should work. Does it?

yes, the internet works.  that's how i'm communicating with you via this forum right now.  however, the internet only works via a WIRED connection.  i can't figure out how to get the WIRELESS to work!

---

### Post by handydan918 on 2009-01-06
I don't understand these lines from your dhclient output.
```
DHCPACK of 24.18.190.164 from 73.104.252.1
bound to 24.18.190.164 -- renewal in 143689 seconds.
```If the router has an IP of 192.168.2.1, then that should show up on the "bound to" line. 

What kind of output do you get from dhhclient if you unplug the ethernet cable?

Also, perhaps the output of ```
iwconfig
``` and ```
iwlist scan
```

---

### Post by kestrel1 on 2009-01-06
> **handydan918 said:**
> I don't understand these lines from your dhclient output.
```
DHCPACK of 24.18.190.164 from 73.104.252.1
bound to 24.18.190.164 -- renewal in 143689 seconds.
```If the router has an IP of 192.168.2.1, then that should show up on the "bound to" line. 

From what I can see the bound to line should be the IP address of the client & according to the readout the client has got an IP address from a DHCP server @ 73.104.252.1
Basically the output from sudo dhclient should look similar to this:
> DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 34341 seconds.
but the iwconfig command may shed a bit more light on what is happening.

---

### Post by bytescribe on 2009-01-06
> **tofuweenie said:**
> done.





and, please, be as specific and detailed as possible -- i'm still VERY new to this stuff.

Tofuweenie, I, too am pretty much a complete Ubuntu noob, and feeling pretty "owned" by all this wireless stuff (not to mention other things like terminal commands, etc)...and I also need things spelled out in noob-proof detail. :-P

So you're not alone...and I'm reading in confusion right along with you, hoping to grok all this.

Noobs unite!

BB,
Kat ^.^

---

### Post by handydan918 on 2009-01-06
> **kestrel1 said:**
> From what I can see the bound to line should be the IP address of the client & according to the readout the client has got an IP address from a DHCP server @ 73.104.252.1

@kestrel1:
You're right, of course. What I intended was that the IP's should both be on the same subnet. Can't really imagine it working to have a 192.168.2/ subnet and have an ip (which is not even in the private IP range!) of 24.xxxx.xxxx.xxxx

Feel free to shoot holes in my theory, but I think there is more going on here than just a wireless issue...

---

### Post by kestrel1 on 2009-01-06
> **handydan918 said:**
> @kestrel1:
You're right, of course. What I intended was that the IP's should both be on the same subnet. Can't really imagine it working to have a 192.168.2/ subnet and have an ip (which is not even in the private IP range!) of 24.xxxx.xxxx.xxxx

Feel free to shoot holes in my theory, but I think there is more going on here than just a wireless issue...
No I totally agree, the IP address that is coming up is not in any of the private ranges. What we really need is the output from iwconfig. We may be able to see what is going on then.
Also the output from ifconfig would be useful, but have the ethernet connected before typing:
```
ifconfig
```
in to a terminal.

---

### Post by tofuweenie on 2009-01-06
> **handydan918 said:**
> What kind of output do you get from dhhclient if you unplug the ethernet cable?

```
stefanie@dell-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
```


and below are the other codes y'all requested:


```
stefanie@dell-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```


```
stefanie@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:f1:bf:80  
          inet addr:24.18.190.164  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::221:9bff:fef1:bf80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8626684 (8.2 MB)  TX bytes:563858 (550.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106660 (104.1 KB)  TX bytes:106660 (104.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:cd:30:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:cd:30:2a  
          inet addr:169.254.4.145  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-CD-30-2A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
stefanie@dell-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:51:6E:F3:15
                    ESSID:"dribbles"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000012c91af518b
                    Extra:Last beacon:6012ms ago
          Cell 02 - Address: 00:1C:10:43:43:F9
                    ESSID:"Sterling"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000011ffb37c18a
                    Extra:Last beacon:5440ms ago
          Cell 03 - Address: 00:0F:B5:6C:B8:5A
                    ESSID:"ravens"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000295afcc679
                    Extra:Last beacon:4832ms ago
          Cell 04 - Address: 00:1B:2F:B4:8B:D9
                    ESSID:"metalheadz02"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/100  Signal level:-89 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002a8ac0d183
                    Extra:Last beacon:4768ms ago
          Cell 05 - Address: 00:14:6C:00:71:1E
                    ESSID:"stereoagnostic"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000004011a5f92f2
                    Extra:Last beacon:4828ms ago
          Cell 06 - Address: 00:1C:DF:0D:62:86
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=88/100  Signal level:-44 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000db9403183
                    Extra:Last beacon:5716ms ago

eth0      Interface doesn't support scanning.
```

OY!

---

### Post by handydan918 on 2009-01-06
Okay, hate to be a bummer, but the dhclient command you ran needs to be run with root privs., i.e., ```
sudo dhclient
```

And the really bad news is that error skews all the rest of the output, so if you would be so kind as to rerun those...

---

### Post by tofuweenie on 2009-01-07
OY!  ok ok, take two: here's everything again, this time with "sudo."

```
stefanie@dell-desktop:~$ sudo dhclient
[sudo] password for stefanie: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/wlan0/00:1f:3c:cd:30:2a
Sending on   LPF/wlan0/00:1f:3c:cd:30:2a
Listening on LPF/eth0/00:21:9b:f1:bf:80
Sending on   LPF/eth0/00:21:9b:f1:bf:80
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 24.18.190.164 on eth0 to 255.255.255.255 port 67
DHCPACK of 24.18.190.164 from 73.104.252.1
bound to 24.18.190.164 -- renewal in 80398 seconds.

```

```
stefanie@dell-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
stefanie@dell-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:f1:bf:80  
          inet addr:24.18.190.164  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::221:9bff:fef1:bf80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33089 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82328455 (78.5 MB)  TX bytes:3307068 (3.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99168 (96.8 KB)  TX bytes:99168 (96.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:cd:30:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:cd:30:2a  
          inet addr:169.254.4.145  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-CD-30-2A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
stefanie@dell-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:0D:62:86
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/100  Signal level:-81 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001e4bdf2183
                    Extra:Last beacon:2048ms ago
          Cell 02 - Address: 00:1C:10:43:43:F9
                    ESSID:"Sterling"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001308dde8185
                    Extra:Last beacon:1896ms ago
          Cell 03 - Address: 00:0F:B5:6C:B8:5A
                    ESSID:"ravens"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000cfc493187
                    Extra:Last beacon:1536ms ago
          Cell 04 - Address: 00:14:6C:00:71:1E
                    ESSID:"stereoagnostic"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/100  Signal level:-89 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000411ace3f187
                    Extra:Last beacon:1604ms ago
```

---

### Post by kestrel1 on 2009-01-07
I am going to take a stab at something, it may have been mentioned.
Are you on Cable or ADSL?

---

### Post by dadozgb on 2009-01-07
It probably some kind of problem with your router 'cause you don't get any dhcp offers. You probably something messed up with it. Try to reset it and than follow instructions in router manual on how to connect to it.

---

### Post by tofuweenie on 2009-01-07
> **kestrel1 said:**
> I am going to take a stab at something, it may have been mentioned.
Are you on Cable or ADSL?

i think i'm using Cable.

---

### Post by kestrel1 on 2009-01-07
I had a feeling that you may be as the IP addresses are registered to a cable company.
Can you open a terminal & type:
```
ping -c 5 www.kcsdorset.co.uk
```
& post the result.

---

### Post by tofuweenie on 2009-01-07
```
stefanie@dell-desktop:~$ ping -c 5 www.kcsdorset.co.uk
PING www.kcsdorset.co.uk (82.165.106.95) 56(84) bytes of data.
64 bytes from kundenserver.de (82.165.106.95): icmp_seq=1 ttl=42 time=192 ms
64 bytes from kundenserver.de (82.165.106.95): icmp_seq=2 ttl=42 time=187 ms
64 bytes from kundenserver.de (82.165.106.95): icmp_seq=3 ttl=42 time=188 ms
64 bytes from kundenserver.de (82.165.106.95): icmp_seq=4 ttl=42 time=188 ms
64 bytes from kundenserver.de (82.165.106.95): icmp_seq=5 ttl=42 time=190 ms

--- www.kcsdorset.co.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 187.437/189.523/192.636/1.846 ms

```

---

### Post by kestrel1 on 2009-01-08
Going by this, you have an Internet connection via you ethernet connection.
This may have been asked before, but what version of Ubuntu are you using?

---

### Post by tofuweenie on 2009-01-08
i'm using Ubuntu 8.04

---

### Post by Dan69 on 2009-03-25
Same problem here. Can access internet just fine but cannot access the router admin page on [http://192.168.1.1](http://192.168.1.1) (and it pings just fine). Perhaps a security precaution from the firewall?
PS. I'm also new to Ubuntu.
Dan

---

### Post by kestrel1 on 2009-03-25
> **Dan69 said:**
> Same problem here. Can access internet just fine but cannot access the router admin page on [http://192.168.1.1](http://192.168.1.1) (and it pings just fine). Perhaps a security precaution from the firewall?
PS. I'm also new to Ubuntu.
Dan
The firewall shouldn't be stopping you gaining access to the routers admin page. Do you get the login screen or just the normal 'cannot display webpage' message.

---

### Post by Dan69 on 2009-03-27
Sorry for the long response.
The problem (and I haven't gone back through the thread to check if the match is exact) was that, even though I could reach the internet through the browser when wired, the wireless interface did't work (because I had lost the password, so I needed to access the router to reset it).
Accessing the router (WRT310N) didn't work (or course using [http://192.168.1.1](http://192.168.1.1)), and that is the real question.
The problem was resolved by doing a hard reboot on the router (I may have tweaked one of the router security settings, such as don't reply to ping, and probably not MAC filtering).
Thanks

---

