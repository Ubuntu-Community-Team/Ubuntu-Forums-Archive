---
title: "Dapper Drake - unexpected wirless issue"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by benndamann33 on 2006-12-13
So yesterday I was at work with my laptop and the wireless there is a littel different and for some reason does not get picked up by your laptop unless you explicitly type in a network name. So I just edited the configuration of my wireless connection and through in a network name(typically, to connect in my dorm room I just have all the fields blank and it autodetects/connects). However, after going to work, I simply removed the network name to go back to normal. However, in my dorm now, I am getting a signal strength of 95%, however on the taskbar indicator there's simply a little red box indicating it's disconnected. I've tried ifdown -a and ifup -a multiple times, with the same result: unable to bring up wlan0 . I don't really understand why this problem came about. Any suggestions? 
Ben

---

### Post by benndamann33 on 2006-12-13
also, under properties says "this network interface is not configured"

---

### Post by benndamann33 on 2006-12-15
no one has any ideas?

---

### Post by benndamann33 on 2006-12-19
wow, thanks for the help

---

### Post by dbott67 on 2006-12-19
What's the output of the following commands:

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command tries to detect wireless access points using each NIC:

```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

-Dave

---

### Post by benndamann33 on 2006-12-20
iwlist scanning
lo            Interface doesn't support scanning

eth0         Interface doesn't support scanning

eth1        Scan completed  :
               Cell 01 - Address: 00:18:39:58:90:26
                ESSID: "linksys"
               Protocol: IEEE 802.11bg
               Mode:Master
               Channel: 6
               Encrpytion key: off
               Bit Rates 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                             48 Mb/s; 54 Mb/s
               Quality = 25/100   Signal level = -84 dBm
               Extra:  Last beacon: 484ms ago

               Cell 02 - Address: 00:90:4b:0C:5E:BA
               ESSID: "wireless"
               Protocol: IEEE 802.11bg
               Mode:Master
               Channel: 6
               Encrpytion key: off
               Bit Rates 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
               Quality = 29/100   Signal level = -82 dBm
               Extra:  Last beacon: 13032 ms ago

sit0          Interface doesn't support scanning

---

### Post by benndamann33 on 2006-12-20
cat interfaces

auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auth ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by benndamann33 on 2006-12-20
ifconfig -a

eth0  Link encap: Ethernet HWaddr 00:12:3F:0F:13:b3
         UP BROADCAT MULTICAST MTU:1500 Metric: 1
         RX packets 463 error: 0 dropped: 0 overruns:0 frame:0
         TX packets: 75 errors:0 droppeD:0 overruns:0 carrier: 0
         collisions:0 txqueuelen:1000
         RX bytes: 32246(31.4 KiB) TX bytes: 11370 (11.1 KiB)
         Interrupt: 169


eth1  Link encap: Ethernet HWaddr 00:12:F0:AA:4B:DA
         UP BROADCAT MULTICAST MTU:1500 Metric: 1
         RX packets 82 error: 0 dropped: 0 overruns:0 frame:0
         TX packets: 36 errors:0 droppeD:0 overruns:0 carrier: 0
         collisions:0 txqueuelen:1000
          RX bytes: 34358 (33.5 KiB) TX bytes: 432 (432.0 b)
         Interrupt: 201 Base address: 0xe000 MEmory: dfcff000-dfcfffff



lo      Link encap: Local Loopback
         inet addr:127.0.0.1 Mask: 255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436   Metric:1
         RX packets:638 error:0 dropped:0 overruns:0 frame:0
         TX packets:638 errors:0 dropped:0 overruns:0 carrier:0         
         collisions:0 txqueuelen:0
         RX bytes: 87200(85.1 KiB) TX bytes: 87200 (85.1 KiB)

sit0     Link encap: IPv6-in-IPv4
          NOARP  MTU:1480   Metric:1
          RX packets:0 error:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0        
          collisions:0 txqueuelen:0
          RX bytes: 0(0,0 b) TX bytes: 0 (0.0 b)


Note: I can no longer access the internet even via a wired connection so I typed this all on another computer, so blatent typos I apologize for in advance. Thanks for the help.
Ben

---

### Post by dbott67 on 2006-12-20
> **benndamann33 said:**
> ... Note: I can no longer access the internet even via a wired connection so I typed this all on another computer, so blatent typos I apologize for in advance. Thanks for the help.
Ben

[COLOR="Blue"][I]YIKES!  Type by hand! :)

A little trick that you might use when you can't get online is to use a floppy/usb thumb drive/CDRW/SD card.  If you've got a thumb drive, it should mount automatically to the Desktop folder.  I've got a Corsair USB thumb drive that mounts as /home/dbott/Desktop/CORSAIR.

Knowing this, I can copy & paste the output from the terminal into a text file on the thumb drive and then bring it over to a working computer.

The other way to do it would be to use the 'redirect' option.  Instead of displaying the output on screen, you can re-direct the output to a file:
```
ifconfig -a > ~/Desktop/ifconfig.txt
```
The above command would create a file on my desktop called ifconfig.txt.  To copy it straight to my USB drive, I would type:
```
ifconfig -a > ~/Desktop/CORSAIR/ifconfig.txt
```

You can do this for every command to save a lot of typing.[/I][/COLOR]

Anyhow, looking at the output of your commands:
```
cat /etc/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto [COLOR="Red"]eth2[/COLOR]
iface [COLOR="Red"]eth2[/COLOR] inet dhcp

aut[COLOR="Red"]o[/COLOR] ath0 [COLOR="Blue"]<--- changed the 'h' to 'o' (just a typo, I'm sure)[/COLOR]
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
Not sure if this is a typo or not: eth[COLOR="Red"]2[/COLOR].  According to the output of iwlist, your wireless interface is eth1, which is not listed in your interfaces file (this would be a problem).

Generally speaking, each interface should have an 'auto <if#>' to automatically enable it.  Each interface that you have listed (eth0, eth2, etc.) has this, except for eth1.  We'll need to correct this (see below).

```
ifconfig -a
```
This shows that the system 'sees' 4 interfaces: lo (the local loopback), eth0 (probably the wired ethernet), eth1 (probably the wireless interface) & sit0 (sit stands for "simple internet transition" and is basically a device capable of encapsulating ipv6 in ipv4 datagrams).

Under normal circumstances, we should see an IP address bound to either eth0 or eth1.

The iwlist scanning command reveals that eth1 is capable of 'seeing' wireless signals and it sees 2 APs ([COLOR="Red"]linksys[/COLOR] and [COLOR="Red"]wireless[/COLOR] are the 2 ESSIDs it sees):
```
iwlist scanning
lo Interface doesn't support scanning

eth0 Interface doesn't support scanning

**[COLOR="Red"]eth1 Scan completed :[/COLOR]**
Cell 01 - Address: 00:18:39:58:90:26
ESSID: "linksys"
Protocol: IEEE 802.11bg

Mode:Master
Channel: 6
Encrpytion key: off
Bit Rates 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality = 25/100 Signal level = -84 dBm
Extra: Last beacon: 484ms ago

Cell 02 - Address: 00:90:4b:0C:5E:BA
ESSID: "wireless"
Protocol: IEEE 802.11bg
Mode:Master
Channel: 6
Encrpytion key: off
Bit Rates 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
Quality = 29/100 Signal level = -82 dBm
Extra: Last beacon: 13032 ms ago

sit0 Interface doesn't support scanning
```

Both appear to have encryption turned off (good for troubleshooting purposes, but after we get it going, you may want to enable WEP or WPA).  Which AP is yours, linksys or wireless?

If you edit your /etc/network/interfaces file to include eth1 (instead of eth2) 

and your ESSID, it may get you connected wirelessly:
```
sudo gedit /etc/network/interfaces
```
Add the following lines (in red):
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth[COLOR="Red"]1[/COLOR]
iface eth[COLOR="Red"]1[/COLOR] inet dhcp
[COLOR="Red"]wireless-essid **your-ap**[/COLOR]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
Keep in mind that your-ap should be changed to linksys or wireless (whichever is yours).

Save the file and then restart the network (or re-boot):
```
sudo/etc/init.d/networking restart
```

Keep me posted.

-Dave

---

### Post by benndamann33 on 2006-12-20
haha yes, typing by hand was a horrible idea but my flashdrive was in my sleeping sisters room. Didn't know about the atuomatic save to txt file though, pretty cool. Anyway, thanks for the help I'll try it out and let you know in a few minutes here.

---

### Post by benndamann33 on 2006-12-20
well now it doesn't have a little red box next to my wireless connection, it has full bars and looks fine. However, if I go to system administration networking, still says wireless connection is not configured and the internet does not work. Thanks for the help on the interfaces file(not sure how it got changed to eth2?) thanks again, any other ideas?
Ben

---

### Post by dbott67 on 2006-12-20
What is the output of **ifconfig -a** now?

If you don't see an IP address bound to one of the interfaces (see my example below), then try issuing the command:
```
sudo dhclient eth1
```
You can also issue the command for the wired interface 'sudo dhclient eth0'

ifconfig -a should look something like this (keep in mind, my wireless interface is wlan0 & yours will be eth1):
```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          [COLOR="Red"]inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

-Dave

---

### Post by benndamann33 on 2006-12-21
Thank you very much, I got it working. One problem was I had previously install gnome network manager, and removed it, but I had to purge it before the internet would work. Thank you for your help. Also, while I have your attention, after I secure the router which  I would like to do by encrypting it, then how do I get the wireless to work? furthermore, what routers would you recommend? 802.11g looks more expensive thatn 802.11b but I'm not sure the difference? thanks
ben

---

### Post by dbott67 on 2006-12-21
G is the current standard (54 Mbps) and is backwards compatible with B (11 Mbps).  There is a new standard called N that is coming down the pike that can obtain throughput of 540 Mbps.

[http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11) for more details.

Of course, to obtain full speeds, you must have a card in your computer that supports the technology in your router.  At present the N standard is not ratified, although there are routers and cards that are "pre-N" and will be able to be upgraded (via firmware) to the official standard once it's ratified.

If you live in the US or Canada, most electronic retailers will have plenty to choose from.  D-Link, Linksys and Netgear are 3 that I generally recommend.  If you are a bit of a hacker, the Linksys WRT54G is a good choice. [http://www.futureshop.ca/catalog/subclass.asp?catid=19994&logon=&langid=EN](http://www.futureshop.ca/catalog/subclass.asp?catid=19994&logon=&langid=EN)

Personally, I have the D-Link 614 (b, 11Mbps) but if I were buying one today, I'd buy the D-Link DI-624 (D-Link has a 2x technology that doubles the throughput if you're using a D-Link supported card).

Both the D-Link and the Linksys models listed above are about the same price ($50-60 CDN).  There are some cheap routers that start at $20, but I would stick with the one of the bigger names as firmware supports and tech support are better if you stick with the well-known vendors.

As for encryption, there's WEP and WPA.  WPA is far more secure, but is also more difficult to get going.  There are some good how-to's in the forum; just search for "WPA howto".  My router only supports WEP.

**_Enabling WEP:_**

If you are able to connect without WEP, try turning it back on in the router and use 128-bit encryption with a simple 13-character password (such as 'wepencryption')

In your **/etc/network/interfaces** try changing the line to:

```
wireless-key **s:wepencryption**
```
The preceding 's:' idicates that the key is in plain ASCII text & should be 13 characters long (assuming you're using 128-bit).

'sudo ifdown eth1', 'sudo ifup eth1', 'sudo dhclient eth1' and see what happens.

If it works, then change the WEP key to something more difficult and repeat the above steps.

-Dave

---

### Post by benndamann33 on 2006-12-25
I installed a new 802.11g LINKSYS w\ speed booster wireless router. It works fine with the computer it's directly connected  to(windows xp) and wirelessly with my mac laptop. I'm using 128 wep hex encryption. I cannot get wireless to work on this computer, however. I have tried the following commands to debug, but no luck! It's weird it works on the mac fine but not on ubuntu, seems weird. Let me know if you have any suggestions? My network name is Grant-Network. 

bdg4@BensSweetComputer:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:57:CD:E3
                    ESSID:"Grant-Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-38 dBm  
                    Extra: Last beacon: 64ms ago
          Cell 02 - Address: 00:18:39:5B:90:26
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=87/100  Signal level=-72 dBm  
                    Extra: Last beacon: 88ms ago
          Cell 03 - Address: 00:90:4B:0C:5E:BA
                    ESSID:"wireless"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 104ms ago
          Cell 04 - Address: 00:0F:3D:63:6A:D6
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=20/100  Signal level=-86 dBm  
                    Extra: Last beacon: 13952ms ago



My interfaces file:
 cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
wireless-essid Grant-Network
wireless key ##########################

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

