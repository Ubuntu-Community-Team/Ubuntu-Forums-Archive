---
title: "Broadcom wl driver Monitor mode support?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by mxweas on 2008-10-30
I've finally got the broadcom wl driver working, but iwconfig shows that it does not support monitor mode. I have one of the new macbook pros that has the unibody and the wireless card is a bcm4322 I believe. Is there any way to get monitor mode support? I hear ubuntu intrepid ibex will have the wl driver built in, does anyone know if it has monitor mode support?

Thanks,
Max

---

### Post by primski on 2008-11-05
don't know, but i am also interested in this feature.

any news ?

---

### Post by rjr162 on 2008-11-06
NOTE>  I'm using a broadcom in a Dell Inspiron E1505

I got monitor mode working under Ubuntu 8.10 Ibex.  After I ran into the same issue you guys hit, and reading a bit online, it looked as if the "wl" driver is what was killing it.  I simply blacklisted the "wl" driver and things are working fine for me.  In fact, it's working better now than it had under 8.04.  

Under 8.04 I was unable to be connected to an AP and be in monitor mode, the wireless manager would show no wireless card or something of the sort.  In 8.10 Ibex, I am able to stay associated with an access point as well as run monitor mode!

I just added "blacklist wl" to the end of my blacklist file and it's working good.

blacklist bcm43xx
blacklist wl

are the last two lines of my blacklist file.

The only wireless module that's running in b43, and everything seems to be well.  It even seems after opening my laptop lid, the wireless becomes active and goes on-line quicker.

---

### Post by smalldog on 2008-11-09
I am also using dell computer, but my model is vostro 1400 which wireless interface using BCM4312. 
Under Ubuntu 8.04, I can't using b43 to connect AP with any security. I had tried using ndiswrapper to using Windows driver once but failed. Lastly, I deploy wl. It works fine but cannot create any virtual interface for monitoring. 
Would you mind share your experience step by step. Many thanks:D

---

### Post by c0bra on 2008-11-09
> **smalldog said:**
> I am also using dell computer, but my model is vostro 1400 which wireless interface using BCM4312. 
Under Ubuntu 8.04, I can't using b43 to connect AP with any security. I had tried using ndiswrapper to using Windows driver once but failed. Lastly, I deploy wl. It works fine but cannot create any virtual interface for monitoring. 
Would you mind share your experience step by step. Many thanks:D

I'm in the same situation. Blacklisting the wl driver made it so eth1 isn't available anymore.

---

### Post by rjr162 on 2008-11-09
When I was using 8.04 and the b43xx driver (which was the older one) I had some snags getting the wireless to work.

What I posted above was what I did to get 8.10 working in monitor mode.  Now I can't say I've tried to connect to a wireless AP that had any sort of encryption turned on, maybe I'll try that later.  My eth0 still shows up in wireless manager.

Here's a post of ifconfig

rjr162@rjr162-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:cb:46:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7862 (7.8 KB)  TX bytes:7862 (7.8 KB)

wlan1     Link encap:Ethernet  HWaddr 00:18:f3:f7:2b:dd  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fef7:2bdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141789312 (141.7 MB)  TX bytes:13846524 (13.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-F3-F7-2B-DD-62-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I don't have an ethernet cable plugged in right now.  Haven't used a wired link in a few weeks lol, so I'm not sure how that works with the blacklisting.  If I get a chance tonight or tomorrow I'll WEP/WPA the wireless as well as try using eth0 to make sure everything is working.  

Like I said I've been on open wireless connections, and that all has been working great for me.  

rjr162@rjr162-laptop:~$ sudo airmon-ng start wlan1 


Interface	Chipset		Driver

wlan1		Broadcom 43xx	b43 - [phy0]
				(monitor mode enabled on mon0)

rjr162@rjr162-laptop:~$ sudo airmon-ng check


Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID\tName
5652	NetworkManager
5664	wpa_supplicant
18504	dhclient
Process with PID 18504 (dhclient) is running on interface wlan1
rjr162@rjr162-laptop:~$ sudo airmon-ng


Interface	Chipset		Driver

wlan1		Broadcom 43xx	b43 - [phy0]
mon0		Broadcom 43xx	b43 - [phy0]

On a side note, kismet is working fine as well, picking up the packets from a WEP'ed AP that's apparently in my range.  Will post more later

---

### Post by shadesofevil on 2008-11-11
I've been trying to get monitor mode to work on my card as well. I used ndiswrapper before this and it worked fine, but with the new b43 driver it is being quite stubborn.

I tried with wl driver but it does not appear to support this mode yet, so I'm trying with b43 for now.

my card is a BCM4311 rev 02 on a compaq presario v3000

my card seems to go into promiscuous mode quite happily, but i can only capture my own packets and nobody elses.

here is the output of dmesg after just after I ran dsniff (tcpkill) followed by wireshark afterwards. (and closed it apparently)

I removed the wl module just before doing so

```

[16331.776675] wlan0: authenticate with AP 00:08:5c:7c:31:77
[16331.778162] wlan0: authenticated
[16331.778172] wlan0: associate with AP 00:08:5c:7c:31:77
[16331.780314] wlan0: RX ReassocResp from 00:08:5c:7c:31:77 (capab=0x451 status=0 aid=1)
[16331.780330] wlan0: associated
[17900.560532] ieee80211_crypt: unregistered algorithm 'NULL'
[17921.252112] device wlan0 entered promiscuous mode
[17943.760105] device wlan0 left promiscuous mode
[18020.041098] device wlan0 entered promiscuous mode
[18128.368092] device wlan0 left promiscuous mode

```

can somebody tell me the difference between rmmod and modprobe -r?

---

### Post by rjr162 on 2008-11-17
an update: I enabled WPA on my router and on the dell, I was still able to connect even with wl blacklisted.  I haven't tried a wired connection yet, but I'm figuring that would work fine too.

I did notice a few nights ago with some update, everything was listed twice in my wirelessmanager, including the wired section.  Weird.  Everything was also listed as "eth0" even though it was a wireless AP, but everything still worked fine.  It's fixed now (maybe the laptop just needed rebooted)

I still haven't hit any snags yet...

---

### Post by Micro_s on 2009-01-11
Is there any way how to get b43 working on 8.04?

My card:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

---

### Post by Plumtreed on 2009-01-16
> **Micro_s said:**
> Is there any way how to get b43 working on 8.04?

My card:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


I have bcm4312 working in 8.04 but I have the NetworkManager 0.7.1 loaded, which is included with 8.10.

Broadcom provide a linux driver for bcm4312 (&others). See their web page.

---

### Post by Micro_s on 2009-01-17
> **Plumtreed said:**
> I have bcm4312 working in 8.04 but I have the NetworkManager 0.7.1 loaded, which is included with 8.10.

Broadcom provide a linux driver for bcm4312 (&others). See their web page.

I can make Broadcom STA driver work too (and with better signal than with ndiswrapper driver), but I can connect only via knetworkmanager. Using Konsole I can't even scan networks. And it does not support Monitor mode. So that's why I'm looking for B43 driver.

---

### Post by Diabolis on 2009-05-29
> **shadesofevil said:**
> can somebody tell me the difference between rmmod and modprobe -r?

There is no difference, is just a matter of preference. Some people think that if you have a command that inserts modules, then is more consistent to have another one that removes modules.

I'm trying to get the BCM4312 NIC to work in monitor mode too. I'll post back if I achieve it.

---

### Post by binwiederweg on 2009-08-06
So? Did you find out anything? -- Having the same problem.

---

### Post by chrisfu on 2009-08-26
> **Diabolis said:**
> There is no difference, is just a matter of preference. Some people think that if you have a command that inserts modules, then is more consistent to have another one that removes modules.


That's not entirely accurate.  rmmod is much less gracious in it's approach to unloading modules.  You should always try modprobe -r before resorting to rmmod, as it works more intelligently and is less likely to cause any problems.

---

### Post by kevdog on 2009-08-26
I thought rmmod was an alias for modprobe -r -- so I thought there was no difference.

As far as monitor mode, wl and ndiswrapper can not be put in monitor mode.

b43 or openfwwf drivers for broadcom (which only support certain chipsets -- not all broadcom cards) can be put into monitor mode.

---

### Post by opipa on 2011-04-16
My solution(although been noticed above, where requires a step-by-step. My NIC is broadcom4312, ubuntu 10.04, current driver: wl):
1. blacklist wl :
add "blacklist wl" to the last line in the file /etc/modprobe.d/broadcom-sta-common.conf
to do so, you may need 
```
sudo gedit /etc/modprobe.d/broadcom-sta-common.conf
```comment out the "install wl..." line using "#"(in case it has) 
2. remove running module "wl" from kernel:
```
sudo modprobe -r wl 
```add new module which support monitor mode(b43):
```
sudo modprobe -a b43
```3. now enjoy, if you cannot change it to monitor mode because it is busy, try the following before:
```
sudo ifconfig wlan0 down
```notice that while you switched your driver, your interface name is being changed from eth-x to wlan-x.
p.s. It is a solved issue. Two ways to tackle with, 1) patch injection when using wl(which I didn't test on mine) or 2) use b43 only.
More info for injection(if you find it works, plz give us the detail): 
specific for broadcom NDIS-compliant driver
[http://seclists.org/fulldisclosure/2008/Nov/506](http://seclists.org/fulldisclosure/2008/Nov/506)
injection as general
[http://aircrack-ng.org/doku.php?id=patching](http://aircrack-ng.org/doku.php?id=patching)
[]("http://aircrack-ng.org/doku.php?id=injection_test")

---

### Post by josephmills on 2011-04-16
If you are using a b43 driver please post the following ```
lspci -vnn | grep 14e4
``` thanks 
@ Micro_s 
you need have to make sure you blacklist the “wl” driver before you utilize b43, otherwise they will collide and your card will stop functioning altogether, let alone hope for injection. The “wl” driver does not support aircrack-ng.

source [http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=63084470778633e231f902d1db3c12d8](http://www.aircrack-ng.org/doku.php?id=b43&DokuWiki=63084470778633e231f902d1db3c12d8)

---

### Post by BrandonBan6 on 2011-07-27
Did the .conf file "broadcom-sta-common.conf" get replaced with something else in 11.04? 

I don't have that file. (and I am using the STA driver)

lscpi output:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

---

### Post by BrandonBan6 on 2011-07-28
> **BrandonBan6 said:**
> Did the .conf file "broadcom-sta-common.conf" get replaced with something else in 11.04? 

I don't have that file. (and I am using the STA driver)

lscpi output:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

Never mind, I generated the file. I'm working now with B43 (and monitor mode supported) W00T! :guitar:

---

