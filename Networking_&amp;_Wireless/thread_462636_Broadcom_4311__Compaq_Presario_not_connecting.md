---
title: "Broadcom 4311 / Compaq Presario not connecting"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by brn on 2007-06-02
This is a popular topic.  I have applied quite a few methods and how-to's from this forum with no luck so far.  Here is what I have:
[LIST]
[*]Compaq Presario C502 laptop running Fiesty with Windows Vista pre-installed
[*]Broadcom 4311 miniPCI
[/LIST]
Wireless  works with Vista.

I have tried both ndiswrapper and fwcutter (several times each) and believe I have the correct driver installed by ndiswrapper.  However, everything I find relating to the wrapper refers to 'wlan0' yet all I see with the Network Manager is 'Eth1' as the wireless connection.

Here is what I see in Fiesty:
**lspci:**
 > 06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
**NOTE:**  The driver installed with Vista is bcmwl6.inf.  I have checked both the HP and Dell driver downloads and they agee.  According to the HP blurb, bcmwl6 corrects some minor items from bcmwl5.  (I tried bcmwl5 -wrapper and cutter- with no success there either.)

**iwconfig:** 
> eth1      IEEE 802.11b/g  ESSID:"zoom1535"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:01:38:73:D7:24   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=81/100  Signal level=-48 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Here that the MAC address (Access Point) is *_different from what is written on the miniPCI itself_*.  Vista reports the correct MAC.  I think this is important but don't  know what to do about it.

**ifconfig:**
> eth1      Link encap:Ethernet  HWaddr 00:1A:73:0F:12:DA  
          inet6 addr: fe80::21a:73ff:fe0f:12da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:24552 (23.9 KiB)
          Interrupt:3 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:1A:73:0F:12:DA  
          inet addr:169.254.5.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x8000 
Here the HWaddr (MAC) is correct, agreeing with the miniPCI sticker and Vista too.  ..Strange!..  I have no idea what 'eth1:avah' is but it seems harmless.

**sudo iwlist scan:**
> eth1      Scan completed :
          Cell 01 - Address: 00:01:38:73:D7:24
                    ESSID:"zoom1535"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-40 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 60ms ago
          Cell 02 - Address: 00:17:3F:66:C4:8E
                    ESSID:"MR2BOOST20"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-84 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 6876ms ago

Cell01 shows my own router/modem.   As with iwconfig, the MAC address is wrong.  Cell02 is evidently a neighbor.

Here are all the relevant file entries I know about.
**/etc/modprobe.d/ndiswrapper:**
> alias wlan0 ndiswrapper
**/etc/network/interfaces:**
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid zoom1535
wireless-key xxxxxxxxxx
auto wlan0

iface eth1 inet dhcp
wireless-essid zoom1535
wireless-key xxxxxxxxxx

auto eth1

auto eth0
i may have manually added the "iface wlan0" text and the eth1 data was put there when I configured Network Manager. (I have spoofed the wireless-key for obvious reasons.)

On a tip from a forum post I also added ndiswrapper to /etc/network/interfaces.  I Don't know if it made a difference but I still can't connect.

I'm running out of ideas.  Can anyone spot something that I have overlooked?  -Thanks-

---

### Post by mkoyle on 2007-07-11
I have a broadcom in a slightly older Presario.  I got mine working yesterday.

I am using WPA2 with a pre-shared key (PSK).  The following output shows that I have the same hardware as you are trying to configure.  If your output from these commands is much different, you have found your problem.

> matthew@V5120NR:~$ lspci -v |grep Broadcom
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


> matthew@V5120NR:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

To configure mine, I just followed step by step the how to at [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) for ndiswrapper and then (since I use WPA2) I followed the howto at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) which shows exactly how to configure WPA, WPA2 and who-knows-what-else.

If you have trouble following, post again and I will follow up.  Since your 'spoofed' wireless key is very short, I am wondering if you missed the sort of strange part where using your essid and your pre-shared key it generates a hex code (this is from the second howto above):

the instructions require wpasupplicant:
sudo apt-get install wpasupplicant

> VERY IMPORTANT:
Now convert your WPA ASCII password using the following command (' ' single quotes required):
Quote:
wpa_passphrase 'your_essid' 'your_ascii_key'
Resulting in an output like...
Quote:
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. Then save the file and restart your network:
Quote:
sudo /etc/init.d/networking restart



Here is my /etc/network/interfaces; I have slightly modified the hex key, but it is about the right length-- 64 ascii characters/32 hex codes.
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up sleep 5
pre-up modprobe ndiswrapper
pre-up sleep 5
wpa-driver wext
wpa-ssid KyleWNet
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk e70099b566be9b83baf7d154f56c1b440cd7ad08a761aa2c9fa086dea3241109


If you keep having trouble, post again.  Include information about your router: ESSID, whether you use WPA/WPA2, whether you broadcast the ESSID, whether you are going to use static or dynamic addresses, etc.  I'm glad to help.

--Matthew

---

### Post by drhavanger on 2007-07-12
hmm, wow, i have a broadcom (hp pavilion ze4910us), and didn't have to do any of that.  all i did was bring up synaptic package manager, do a search for fwcutter, download, installed it and everything works perfect.  no hack and slash terminal needed.

---

### Post by kevdog on 2007-07-12
Can you post the contents of your /etc/iftab file.  I bet that is where the problem is.  Good initial post by the way, it explained everything thoroughly.  Also post the following:
lshw -C network.

---

### Post by mkoyle on 2007-07-15
When I configured my wireless the first time, I used the first way I found.  It really didn't take long.  I have since seen many posts suggest network-manager, and I have to agree with them... for most people it is better.  Just comment out everything about eth1 (put # in front of each line) and install the fwcutter package or use ndiswrapper.

--Matthew

---

### Post by El Viejo Lobo on 2007-07-15
I have a Presario V2000 and broadcom 4318 maybe it can be done the same way.
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fcontrib%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_005-2_i386.deb&md5sum=299999dfd475bedf9250f6fe5b190162&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fcontrib%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_005-2_i386.deb&md5sum=299999dfd475bedf9250f6fe5b190162&arch=i386&type=main)
With Feisty I did it with a few clicks here: [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)

---

### Post by edwin.e.johnson on 2007-07-16
i had same problem with mine........ i got it working using this

[http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.2.tar.gz](http://darkn00b1971.googlepages.com/bcm43xx-gtk-installer-0.2.tar.gz)

or just type in at google  "43xx the easy way"

i use the ndis wrapper method but in order to install that option i have to be connected to a hard line with all repo's enabled..

---

### Post by brn on 2007-08-14
[SIZE="3"]**[COLOR="Purple"]Success at last!.[/COLOR]**[/SIZE].  Thanks all!  I have been fighting this critter for four months, trying each of the referenced HOW-TOs over and over, first with Dapper, then Fiesty, then Dapper again, then Fiesty again.  FWCutter ddn't work at all.  Ndiswrapper always held promise, the WiFi button worked and WLAN0 was seemingly recognized.  But no connection.  In this forum I had seen mention of **wifi-radar** but it seemed to be just another graphical configuration utility.  Still, today I thought I'd give it a try. --BINGO--  Suddenly wireless works.

Interestingly, iwconfig and iwlist still report seeing a completely foreign MAC address, something that has plagued me since day one.  For info:
> ~ :> iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"zoom1535"  Nickname:"zoom1535"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:01:38:73:D7:24   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
...and...
> ~ :> sudo iwlist wlan0 scan
Password:
wlan0     Scan completed :
          Cell 01 - Address: 00:01:38:73:D7:24
                    ESSID:"zoom1535"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
...Although ifconfig sees the correct MAC:
> ~ :> ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1A:73:0F:12:DA  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe0f:12da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7908857 (7.5 MiB)  TX bytes:1923275 (1.8 MiB)
          Interrupt:17 Memory:30000000-30004000 
Again, only ifconfig has the correct MAC, just as I noted three months ago, but this time dhclient (started when I hit 'connect') found the correct host with the correct MAC.  Thanks to **Wifi-Rada**r, Harmony has at last been restored here in my Little Universe.

---

### Post by noob12 on 2007-08-14
Um.  The ones you are seeing in those iwlist scan and iwconfig outputs are showing the MAC address of your access point, not your own.

---

### Post by brn on 2007-08-14
>  Um. The ones you are seeing in those iwlist scan and iwconfig outputs are showing the MAC address of your access point, not your own.
49 Minutes Ago 10:46 PM
That would be logical noob12 but the MAC for my router is 00:01:38:70:ed:e5.  Iwlist sees signals from several neighbors but those don't match either.  This one is a mystery.  I have often wished I knew where each of the config/status reporting routines finds the data but this has eluded me.

Incidentlally.  I notice now that the *Gnome Network Manage*r Applet (icon in the top-right corner) is now somehow "out of the loop".  the other applet,* "Network Monitor" *(bottom launch bar near the workspace block) now has the correct configuration data for wlan0.  It once displayed "eth1:avahi" (which it could not find to configure) but now that one is gone.  Baffling!

---

### Post by kevdog on 2007-08-14
Interesting solution. Does the Mac address listed in /etc/iftab match your MAC address on your wireless card??

Can you post this file?

---

### Post by brn on 2007-08-14
Here it is:  :>   ~ :> cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:a3:31:b9 arp 1
# eth1 mac 00:1a:73:0f:12:da arp 1
wlan0 mac 00:1a:73:0f:12:da arp 1
It looks like I commented the eth1 line and may also have (manually) added wlan0.  I try to follow the various HOW-TO recipes as carefully as possible but after a few frustrating failures, get sloppy and neglect to record exactly what I have done as I do it.  In any case, the eth1 line, which I didn't put there, shows the correct MAC.

It can be noted that since starting this struggle im May, I have not slept, shaved, eaten, or bathed.  With wireless working I can again rejoin humanity.  :)

---

### Post by noob12 on 2007-08-14
OK.  Well, the AP has a wireless MAC and one or more wired MACs.  Generally this is the wireless MAC that you see in the association info or scan.  I've never seen otherwise.   Probably 00:01:38:70:ed:e5 (what you are thinking of as the AP's MAC) is that of one of its wired interfaces.

---

### Post by brn on 2007-08-14
About all I have taken away from this exercise is an ego-deflating awareness that modern communication protocols are dauntingly compllicated.  I wish I could find a really comprehensive book on the topic, one with large type and  lots of pictures.  Edible covers would be a bonus.   :wink:

---

