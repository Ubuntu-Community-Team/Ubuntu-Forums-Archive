---
title: "wpa key not accepted"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by kush on 2008-04-24
hello, I have managed to install my Belkin wireless usb adapter after a fresh install of the new 8.04 release from today, using ndiswrapper and the windows driver, and it now shows in the network manager. I can also see a list of networks, including my own, 
But when I try to connect and enter my wpa key phrase, it cannot establish a connection to my router, and keeps prompting for the key phrase.
Does anyone else have this problem, or even better, a solution?

P.S. The wireless adapter worked under the previous version 7.10.

---

### Post by kutjara on 2008-04-24
> **kush said:**
> hello, I have managed to install my Belkin wireless usb adapter after a fresh install of the new 8.04 release from today, using ndiswrapper and the windows driver, and it now shows in the network manager. I can also see a list of networks, including my own, 
But when I try to connect and enter my wpa key phrase, it cannot establish a connection to my router, and keeps prompting for the key phrase.
Does anyone else have this problem, or even better, a solution?

P.S. The wireless adapter worked under the previous version 7.10.

Are you using 32 or 64 bit Hardy? I found it impossible to make my Broadcom wifi card work with WPA under 64 bit Hardy. I never got to the bottom of whether it was the 64 bits, NDISWrapper, wpa-supplicant, the card, the driver, or my router (all of which used WPA just fine fine under other configurations), but that particular setup just wouldn't work for me.

---

### Post by kush on 2008-04-25
I am using the 32 bit version. I have tried manual configuration according to the stickies at the top of this forum, but unfortunately those don't work either.

So for the time being, I am tied to the wire...:)

---

### Post by kikapu on 2008-04-25
> **kush said:**
> hello, I have managed to install my Belkin wireless usb adapter after a fresh install of the new 8.04 release from today, using ndiswrapper and the windows driver, and it now shows in the network manager. I can also see a list of networks, including my own, 
But when I try to connect and enter my wpa key phrase, it cannot establish a connection to my router, and keeps prompting for the key phrase.
Does anyone else have this problem, or even better, a solution?

P.S. The wireless adapter worked under the previous version 7.10.

I have the same problem. I use 8.04 from a Live CD (i have not  install it yet) and i already made a post here for this problem) While i give the WEP key, it keeps asking me for a passprase.

Any solution ??

---

### Post by kutjara on 2008-04-25
> **kush said:**
> I am using the 32 bit version. I have tried manual configuration according to the stickies at the top of this forum, but unfortunately those don't work either.

So for the time being, I am tied to the wire...:)

What's the chipset in the card (Atheros, Broadcom, Ralink...)? Often, NDISWrapper isn't the best solution for a particular chipset. Atheros cards, for example sometimes give better results with Madwifi drivers, while Ralink ones work well with Serialmonkey.

---

### Post by kush on 2008-04-25
The adapter I use is a Belkin F5D7050. I am not sure which version, so the chipset could be either broadcom or Ralink. However, it worked with ndiswrapper in ubunto 7.10 and also works fine now without using wpa encryption.... although that doesn't really help, having to leave the network unsecured.

Output fromm dmesg when I connect it is:

[  966.286638] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  966.427016] usb 3-1: configuration #1 chosen from 1 choice
[  966.554313] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[  966.695081] ndiswrapper: driver blkwgu (Belkin Corporation.,06/01/2007,5.1089.0601.2007) loaded
[  970.215908] wlan0: ethernet device 00:17:3f:34:11:a0 using NDIS driver: blkwgu, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 050D:705E.F.conf
[  970.215976] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


iwconfig:
kushad@Mylapdog:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And this from iwevent when I try to use it:

kushad@Mylapdog:~$ iwevent
Waiting for Wireless Events from interfaces...
22:55:17.733322   wlan0    Set Encryption key:off
22:55:46.312489   wlan0    Set Mode:Managed
22:55:46.594205   wlan0    Set ESSID:"kushome"
22:55:49.597495   wlan0    Set Mode:Managed
22:55:49.597537   wlan0    Set Frequency:2.462 GHz (Channel 11)
22:55:49.597606   wlan0    Set ESSID:"kushome"
22:55:49.648180   wlan0    Association Request IEs:00076B7573686F6D65010C82848B968C129824B048606CDD180050F20101000050F20201000050F20201000050F2020000
22:55:49.648261   wlan0    New Access Point/Cell address:00:11:50:94:09:B4
22:55:49.653180   wlan0    New Access Point/Cell address:Not-Associated
22:55:52.757607   wlan0    Set Mode:Managed
22:55:52.757646   wlan0    Set Frequency:2.462 GHz (Channel 11)
22:55:52.757676   wlan0    Set ESSID:"kushome"
22:55:52.815282   wlan0    Association Request IEs:00076B7573686F6D65010C82848B968C129824B048606CDD180050F20101000050F20201000050F20201000050F2020000
22:55:52.815348   wlan0    New Access Point/Cell address:00:11:50:94:09:B4
22:55:56.819182   wlan0    New Access Point/Cell address:Not-Associated

If anybody can make sense of this, please let me know.

---

### Post by kutjara on 2008-04-25
> **kush said:**
> The adapter I use is a Belkin F5D7050. I am not sure which version, so the chipset could be either broadcom or Ralink. However, it worked with ndiswrapper in ubunto 7.10 and also works fine now without using wpa encryption.... although that doesn't really help, having to leave the network unsecured.

Output fromm dmesg when I connect it is:

[  966.286638] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  966.427016] usb 3-1: configuration #1 chosen from 1 choice
[  966.554313] usb 3-1: reset high speed USB device using ehci_hcd and address 3
[  966.695081] ndiswrapper: driver blkwgu (Belkin Corporation.,06/01/2007,5.1089.0601.2007) loaded
[  970.215908] wlan0: ethernet device 00:17:3f:34:11:a0 using NDIS driver: blkwgu, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 050D:705E.F.conf
[  970.215976] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


iwconfig:
kushad@Mylapdog:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And this from iwevent when I try to use it:

kushad@Mylapdog:~$ iwevent
Waiting for Wireless Events from interfaces...
22:55:17.733322   wlan0    Set Encryption key:off
22:55:46.312489   wlan0    Set Mode:Managed
22:55:46.594205   wlan0    Set ESSID:"kushome"
22:55:49.597495   wlan0    Set Mode:Managed
22:55:49.597537   wlan0    Set Frequency:2.462 GHz (Channel 11)
22:55:49.597606   wlan0    Set ESSID:"kushome"
22:55:49.648180   wlan0    Association Request IEs:00076B7573686F6D65010C82848B968C129824B048606CDD180050F20101000050F20201000050F20201000050F2020000
22:55:49.648261   wlan0    New Access Point/Cell address:00:11:50:94:09:B4
22:55:49.653180   wlan0    New Access Point/Cell address:Not-Associated
22:55:52.757607   wlan0    Set Mode:Managed
22:55:52.757646   wlan0    Set Frequency:2.462 GHz (Channel 11)
22:55:52.757676   wlan0    Set ESSID:"kushome"
22:55:52.815282   wlan0    Association Request IEs:00076B7573686F6D65010C82848B968C129824B048606CDD180050F20101000050F20201000050F20201000050F2020000
22:55:52.815348   wlan0    New Access Point/Cell address:00:11:50:94:09:B4
22:55:56.819182   wlan0    New Access Point/Cell address:Not-Associated

If anybody can make sense of this, please let me know.

I'm using the Belkin F5D7050, too, and it works perfectly with WPA (1 & 2). I downloaded and installed the Serialmonkey rt73 driver package and RutilT GUI network manager (also available from the Serialmonkey site). Follow the directions on the site (or search on these forums under Serialmonkey - there are a couple of nice HOWTOs), and you should be up and running in no time.

I ended up using the Belkin card because I couldn't get my Broadcom card to use WPA with NDISWrapper. It worked fine in 32 bit, but not in 64.

---

### Post by kush on 2008-04-26
Thanks for the suggestion, Kutjara.

But unfortunately, still no luck. I installed the rt73 driver and Rutilt, disabled ndiswrapper, added rt73 to /etc/modules.
When I rebooted it showed as wlan0, but in Rutilt, only the WEP encryption option was available.
I rebooted again, (and again and again) and then my adapter was no longer recognised.... no wireless apdapter present, although rt73 showed in the lsmod output, and a Belkin device was listed in lsusb.
So I reverted to ndiswrappper, tried that with Rutilt, and again, only WEP was available.
In short, I am back to square one. I think it is time for a nice long walk in the sun, and hope that will bring some inspiration :)

---

### Post by kutjara on 2008-04-26
> **kush said:**
> Thanks for the suggestion, Kutjara.

But unfortunately, still no luck. I installed the rt73 driver and Rutilt, disabled ndiswrapper, added rt73 to /etc/modules.
When I rebooted it showed as wlan0, but in Rutilt, only the WEP encryption option was available.
I rebooted again, (and again and again) and then my adapter was no longer recognised.... no wireless apdapter present, although rt73 showed in the lsmod output, and a Belkin device was listed in lsusb.
So I reverted to ndiswrappper, tried that with Rutilt, and again, only WEP was available.
In short, I am back to square one. I think it is time for a nice long walk in the sun, and hope that will bring some inspiration :)

A walk in the sun is a good idea. I usually just go into the garage and kick stuff, then spend the next week walking with a limp.

One thing I've noticed about the rt73 driver, is you have to set it up in System -> Preferences -> Sessions to make it work on reboot. I used rutilt -dp MyNetworkSSID in the "Command" box. Even doing this, I sometimes have to go to the "Options" tab in RutilT itself and bring the card up manually by clicking the Interface up/down button.

When you click "Site Survey" in RutilT, what do you see? You should see your own network in the list, together with the type of encryption it's using. You should then be able to click "Connect," put in your password and connect. Did you get that far, or did the list not display your router's encryption scheme correctly?

---

### Post by kush on 2008-04-26
Hi Kutjara,

yes, my network was listedin Rutilt site survey, but with WEP encryption, instead of WPA, which is how my router is set up.
But, although I am sure this problem will keep nagging in my mind, on my walk in the sun I suddenly saw the light and thought, why not take a chance, and try another usb adapter?
So I came home with e DLink G122, loaded the windows driveer in ndiswrapper, and hey presto...... all is well, I am now wireless connected.
I think £22.00 was a small price to pay, to keep my Ubuntu love alive:) 

Thanks for your help, and perhaps I will give the Belkin another try someday.. I hate lose ends, and not being able to solve things. But for now, I just relax for a while, and enjoy the fact that I have finally been able to 'cut the cord'

---

### Post by kutjara on 2008-04-26
> **kush said:**
> Hi Kutjara,

yes, my network was listedin Rutilt site survey, but with WEP encryption, instead of WPA, which is how my router is set up.
But, although I am sure this problem will keep nagging in my mind, on my walk in the sun I suddenly saw the light and thought, why not take a chance, and try another usb adapter?
So I came home with e DLink G122, loaded the windows driveer in ndiswrapper, and hey presto...... all is well, I am now wireless connected.
I think £22.00 was a small price to pay, to keep my Ubuntu love alive:) 

Thanks for your help, and perhaps I will give the Belkin another try someday.. I hate lose ends, and not being able to solve things. But for now, I just relax for a while, and enjoy the fact that I have finally been able to 'cut the cord'

Every day, I'm becoming more convinced that Linux wireless networking is the nearest thing to black magic that exists in the modern world. It's simply crazy how finicky the hardware is. Even supposedly identical kit behaves utterly differently for different users.

Sometimes, I think the only advice I can offer is that everyone just go to their local computer store, buy one of every card on the market, and try each one until one of them works. Hardly practical, I know, but the alternative is a kind of geek version of Russian-roulette.

Anyway, I'm glad you got wireless working. It's such a relief to be able to stop thinking about WPA, network protocols, drivers, and wrappers every waking moment.

---

### Post by kikapu on 2008-04-26
> **kutjara said:**
> Every day, I'm becoming more convinced that Linux wireless networking is the nearest thing to black magic that exists in the modern world. It's simply crazy how finicky the hardware is. Even supposedly identical kit behaves utterly differently for different users.

Sometimes, I think the only advice I can offer is that everyone just go to their local computer store, buy one of every card on the market, and try each one until one of them works. Hardly practical, I know, but the alternative is a kind of geek version of Russian-roulette.

Anyway, I'm glad you got wireless working. It's such a relief to be able to stop thinking about WPA, network protocols, drivers, and wrappers every waking moment.

I have problems too with wireless (Intel 4965 card and i just found a solution: i installed wicd and all problems are gone. It removed Gnome network manager and wireless is working again!

---

### Post by kutjara on 2008-04-26
> **kikapu said:**
> I have problems too with wireless (Intel 4965 card and i just found a solution: i installed wicd and all problems are gone. It removed Gnome network manager and wireless is working again!

Don't even get me started on network managers! I'm simply stunned at how some people have to use Gnome NM, while others have to use WICD, and still others WiFi Radar, just to get basic stuff to work. On my Acer Aspire laptop, only WICD worked properly. On my HP tx1420us, on the other hand, it has to be Serialmonkey's RutilT. On my Vaio TX650P, nothing but Gnome Network Manager will do.

I think the secret of reliable Linux networking is about three places further down the list than the unification of quantum mechanics and general relativity. They'll cure death before they get this stuff working out of the box.

---

### Post by k66473 on 2008-04-29
Hi, I would like to tell my story:
-When I set my router to use WPA-PSK, default network manager can connect to the router but it asks for WPA key every several minutes. So my connection is not continuos. It was discreted every 3 mins.
-The I follow the tuts and install wicd. Now everything seem to be fine. Wicd is cool.

Regards.

---

### Post by ElaneFreuyh on 2008-04-29
> **kutjara said:**
> 
I think the secret of reliable Linux networking is about three places further down the list than the unification of quantum mechanics and general relativity. They'll cure death before they get this stuff working out of the box.

amen.
but in their defense - most of the hardware manufacturers won't reveal their secrets to anyone involved in open source.

having it work ok in 7.10 and then break in 8.04 is a real shame. i was this close to recommending Linux to friends (I have been for about 5 years now...)

---

### Post by ElaneFreuyh on 2008-04-29
here's the gory details....
did i mention that ethernet connection doesn't work either?

EJF@pooter:~$ sudo lshw -C network
[sudo] password for EJF: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 03
       serial: 00:0a:e4:4e:f9:f2
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.01 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:9a:0b:02:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
EJF@pooter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ZSU-23"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:92:4E:44   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=76/100  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

EJF@pooter:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:4e:f9:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6328 (6.1 KB)  TX bytes:6328 (6.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:0b:02:f2  
          inet6 addr: fe80::217:9aff:fe0b:2f2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:702 (702.0 B)  TX bytes:9755 (9.5 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:17:9a:0b:02:f2  
          inet addr:169.254.2.57  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-0B-02-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

EJF@pooter:~$ dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
EJF@pooter:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 169.254.2.57 icmp_seq=2 Destination Host Unreachable
...
and so on
...
From 169.254.2.57 icmp_seq=104 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
105 packets transmitted, 0 received, +78 errors, 100% packet loss, time 103999ms
, pipe 3

hope that means a lot more to some of you than it did to me :)

---

### Post by zveroboy on 2008-04-30
Same problem (NM keeps asking for the pass phrase with WPA) with netgear wireless card.  Used to work perfectly on Gutsy - don't know why I upgraded.  Oh, well, I hope solution is just around the corner.

BTW.  tried uninstalling network manager and installing Wicd - didn't help.  Wicd keeps locking up.  
Also, tried manual configuration from this thread:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
but it didn't work for me.  I'll keep on trying...

Both Network Manager and Wicd were able to connect to a wireless router w/out any encryption turned on.  But... no encryption = no good :).

I agree that it is a shame that something that worked perfectly in Gutsy is broken now.  :(

Any help/ideas would be greatly appreciated.

---

### Post by kevdog on 2008-04-30
All you guys with connection problems must clarify the chipset you are using --- since everyone is different, and try connecting manually using this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

It may help -- I don't know but at least it will give some output. 

If you cant see your network with iwlist scan its definitely not going to connect either.

Ruitilt used to have a bug with WPA -- would list Wep when it wasn't -- had to connect manually for use with wpa -- the underlying serial monkey (ra) driver support wpa.

---

### Post by ElaneFreuyh on 2008-04-30
my network card is a D-link DWL-G630 version E2.
a quick google suggests it has an "Ra link" chipset, but no-one seems to know for sure.

also, i'm running 64-bit xubuntu 8.04 on an Acer aspire 1500 laptop (AMD 3000+ processor)

thanks for reading

---

### Post by zveroboy on 2008-05-10
> **kevdog said:**
> All you guys with connection problems must clarify the chipset you are using --- since everyone is different, and try connecting manually using this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

It may help -- I don't know but at least it will give some output. 

If you cant see your network with iwlist scan its definitely not going to connect either.

Ruitilt used to have a bug with WPA -- would list Wep when it wasn't -- had to connect manually for use with wpa -- the underlying serial monkey (ra) driver support wpa.

It seems like the problem is beyond the chipset and/or driver since people are having this problem with various chipsets.  However, we all had wireless working in Gutsy and it broke in Hardy.  Anyway, here is some info about my card:

lshw -C network

 *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 03
       serial: 00:14:6c:71:06:15
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg511v2 driverversion=1.45+NETGEAR,02/22/2005,3.1.1.7 ip=192.168.129.103 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g



 Anyhow,  I uninstalled network manager and tried wicd to avail.  Finally, I uninstalled wicd and tried the manual set-up route outlined in the [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) thread.  That didn't work either...  but once I booted to 2.6.22-14-generic kernet the manual method worked on the first try.  So, using 2.6.24-16-generic I couldn't connect but with 2.6.22-14 I could.  I am going to try re-intalling network manager in 2.6.22.-14 to see if it works.  For, now I am suspecting that there is something going on the new kernel that causes these issues.  

I'll post when I try network manager with (one of) the latest kernels.
Hope this helps.

---

### Post by zveroboy on 2008-05-11
Just a quick update:

I've installed Network Manager and works just fine just like in Gutsy.  I am running the older kernel (2.6.22-14-generic), of course.  Since, I don't seem to get update notification I have to manually get the newest kernel (2.6.24-17) somehow.  I got to try it out - it may work :). But for now I'll use 2.6.22-14, since internet connection is a must.

---

### Post by koma77 on 2008-05-12
And here is my story:

Wireless worked great in 7.10. After upgrade to 8.04 it is broken.

My wlan device is found, (ZyXel USB) and network manager can successfully scan for networks etc. But when I try to connect it fails and repeatedly propts for WPA password.

I don't know what to do. I've tried Wicd, backports, fiddling around with the gnome-keyring, but nothing seems to work.

What bothers me is that all this worked fine in 7.10... I wish there was some kind of debug mode that you could enable in the network-manager and see _why_ it prompts for passwords. Maybe it's doing the right thing but then something else is clearly broken.

---

### Post by zveroboy on 2008-05-12
Since you've done an upgrade you must have the older kernel images left over from Gutsy.  Try booting to one of them and see if wireless starts working again.  It worked for me (read my two posts above).

Hope this helps.

---

### Post by dmac71 on 2008-05-15
I am a new user--not used a command  prompt since DOS.  do not understand any of the code, but would greatly appreciate some assistance with a very similar problem. 

 My wireless has not worked since I installed 64bit 8.04  (didn't work in 7.1 either but never installed 7.1 because hoped new version would work out of box) 

I am using a HP Pavilion 9720us with Atheros AR5007 AMD Turion x2 2gb ram. 

 Initially, could not even see any wireless network at all. 

 After I installed ndisgtk ndiswrapper-common and ndiswrapper-utils-1.9 I installed a 64 bit Atheros driver that I picked up off some website which I do not remember.  

This resulted in being able to see my network and others in the neighborhood, but when i try to connect, it asks for my WEP KEY (which it should obviously),which i enter, 

and then the little graphical network symbol at the top starts doing its whirly thing and 

then the bottom left circle (in the whirly) turns green and 

then the top right circle turns green (which I have determined means it has connected based on watching the same process on the wire connection--which works by the way) and 

then it asks for the WEP KEY again (I can play that game until the cows and the pigs come home)

I would appreciate anyone that would be kind enough to provide a person at below beginner level with Linux some assistance.  I am not afraid of the terminal, but I would need exact commands to enter.  Sorry for the highly technical communication--i.e. "whirly" and "top right circle" etc.

Thanks.

---

### Post by steppie on 2008-07-21
At the risk of starting a flame war here, I have to say that I was trying to give ubunto a chance and actually tried installing it on my laptop. Right off the bat, I start having this exact wireless issue. In fact, I was able to connect the wireless but after every reboot, I have to jump through hoops to get the thing re-connected again.

I was hoping that ubuntu would had given me an easy graphical setup that made connecting to a wireless router easy, but after reading millions of other users having issues setting up wpa wireless, and the solutions that are being given, I'm better off throwing my old XP image onto the laptop.

Oh well...

---

### Post by koma77 on 2008-07-22
I was able to get the wireless up and running by using ndiswrapper and blacklisting the original driver.

It seems that this driver does not work well with the current kernel, or something like that.

---

### Post by dmac71 on 2008-07-22
Well, I must say that I found a fix for this and now my wireless is working perfectly.  It uses the original network manager and a madwifi driver.  the link is below.  I had all kinds of problems with everything until I followed this how to.  It did not initially work for me, but I had to start with a clean Ubuntu install and then it just worked.  It is great now.


[URL="http://ubuntuforums.org/showthread.php?t=816780"]

---

### Post by zveroboy on 2008-07-23
> **dmac71 said:**
> Well, I must say that I found a fix for this and now my wireless is working perfectly.  It uses the original network manager and a madwifi driver.  the link is below.  I had all kinds of problems with everything until I followed this how to.  It did not initially work for me, but I had to start with a clean Ubuntu install and then it just worked.  It is great now.


[URL="http://ubuntuforums.org/showthread.php?t=816780"]

First of all, thank you for the link.  However, the thread you've pointed out deals with a particular wireless chipset on a 64bit Ubuntu install.  Have you used it successfuly on other configurations such as 32bit Ubuntu (8.04) and a different wireless chipset?  
Thank you in advance for you help.

---

### Post by touf on 2009-05-20
I have an Acer aspire 5672i with ubuntu 8.04 . Also lots of problems to get my WIFI WPA been accepted.
I just added to the repos 'deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras'
download with synaptic WICD, and everything working fine
Touf

---

