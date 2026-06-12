---
title: "broadcom not recognized"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by 4lc0h0l1c on 2008-08-10
Hi,
I have a broadcom 4306. I can not get it to work.  I followed all the steps the tutorials.  Perhaps I am loading the drivers in the wrong order.  Everything I have found indicates I should use the bcmwl5.inf driver with ndiswrapper.  Doesn't work.  I know the card works because I hosed all my wireless settings about two weeks ago, and before that I had the broadcom card and my wireless usb card working simultaneously.  At this point I cannot see an interface for the broadcom chipset.  Help?

---

### Post by 4lc0h0l1c on 2008-08-10
Sorry, here is relevant info.  wlan0 is my wireless usb card.  eth1 is my broadcom PCI card.

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: ssb)
rt73 : driver installed
        device (148F:2573) present (alternate driver: rt2500usb)



$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:84:b6:af
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:0b:cd:75:94:95
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:d0004000-d0006000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:44834 (43.7 KB)  TX bytes:44834 (43.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:18:cc:ee
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37826947 (36.0 MB)  TX bytes:1658289 (1.5 MB)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:"mine"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:A6:27:28
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The problem is the access point not associated I think.  I can't see any networks when I scan with eth1.  Also, for some reason Wicd is able to connect with wlan0 but running sudo dhclient wlan0 times out on DHCPOFFER.  Wicd is not able to see any networks with eth1.

---

### Post by 4lc0h0l1c on 2008-08-10
bump

---

### Post by Ayuthia on 2008-08-10
Try and see if you can connect after you do the following:
[code]sudo modprobe -r b43 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper[code]
If it works, it will only work for this session.

---

### Post by 4lc0h0l1c on 2008-08-10
Thank you so much for your reply.  I really want to get this figured out!
No it doesn't work...
Now I can't see the eth1 interface at all.  Sometimes I can and sometimes I can't.  I can't figure it out!

I now see that dmesg gives me some error messages!  I began googling it and haven't found anything yet.

[  442.498800] usbcore: deregistering interface driver ndiswrapper
[  474.201773] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  474.313851] ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) loaded
[  474.314883] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[  474.321028] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: dce85b02
[  474.321041] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x104
[  474.321192] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  474.321206] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  474.321240] ndiswrapper (mp_halt:259): device db229480 is not initialized - not halting
[  474.321244] ndiswrapper: device eth%d removed
[  474.321278] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[  474.321320] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[  474.339951] usbcore: registered new interface driver ndiswrapper

---

### Post by Ayuthia on 2008-08-10
> **4lc0h0l1c said:**
> Thank you so much for your reply.  I really want to get this figured out!
No it doesn't work...
Now I can't see the eth1 interface at all.  Sometimes I can and sometimes I can't.  I can't figure it out!

I now see that dmesg gives me some error messages!  I began googling it and haven't found anything yet.

[  442.498800] usbcore: deregistering interface driver ndiswrapper
[  474.201773] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  474.313851] ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) loaded
[  474.314883] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[  474.321028] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: dce85b02
[  474.321041] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x104
[  474.321192] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  474.321206] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  474.321240] ndiswrapper (mp_halt:259): device db229480 is not initialized - not halting
[  474.321244] ndiswrapper: device eth%d removed
[  474.321278] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[  474.321320] ndiswrapper: probe of 0000:00:09.0 failed with error -22
[  474.339951] usbcore: registered new interface driver ndiswrapper

I am not for sure about the error message either, but sometimes using another driver might help.  You might want to check the rev number of your card (lspci -nn or lshw -C network) and maybe try the driver from:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by 4lc0h0l1c on 2008-08-10
Forgot to say, my card is a revision 02.  I have tried the driver from that page, as well as many other drivers.  I found (lost the link!) a post where someone said that not all the bcmwl5 drivers are the same.  I couldn't find a the driver on the compaq page though.

---

### Post by Ayuthia on 2008-08-10
What is the make and model of your computer?  Also what version of Ubuntu are you using (32 or 64 bit)?  Can you also provide your lspci -nn info?  I am going to see if I can find one for you.

Also, have you tried using the b43 driver yet?

---

### Post by 4lc0h0l1c on 2008-08-10
Hi, thanks again for helping.

My computer is a Presario 2100 laptop.  It didn't come stock with wireless, but my friend had a broken Presario 2100 that did, so I grabbed the PCMCIA card, which is why I forgot that I had PCI wireless.

**$ lspci -nn | grep Broad**
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)


I check here [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) and used the R115321 drivers just now, and I have my wireless interface back.  Apparently there a bunch of different versions of these drivers out there, AFAICT having the correct driver is what determines if your interface shows up, even if ndiswrapper says it loads OK.  Now I am back to the problem that it detects no access point:
[B]
from dmesg:[/B]
[ 3733.106107] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3733.188890] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
[ 3733.191305] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[ 3733.195969] ndiswrapper: using IRQ 10
[ 3733.584434] wlan0: ethernet device 00:0b:cd:75:94:95 using NDIS driver: bcmwl5, version: 0x40a2800, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[ 3733.585224] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3733.589252] usbcore: registered new interface driver ndiswrapper
[ 3734.163780] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[ 3734.163966] udev: renamed network interface wlan0 to wlan1


[B]
$ ifconfig[/B]
eth0      Link encap:Ethernet  HWaddr [eth0 addr]
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:397225 errors:0 dropped:1763 overruns:0 frame:0
          TX packets:205228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:518836328 (494.8 MB)  TX bytes:15041965 (14.3 MB)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23998 (23.4 KB)  TX bytes:23998 (23.4 KB)

wlan1     Link encap:Ethernet  HWaddr [broadcom addr]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:d0004000-d0006000

[B]
$ iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by 4lc0h0l1c on 2008-08-10
I followed the steps from kevdog here [http://ubuntuforums.org/archive/index.php/t-523524.html](http://ubuntuforums.org/archive/index.php/t-523524.html) bringing wlan1 down and removing the pid file, and when I ran the wpa_supplicant command, I can see from the output that it can see my wireless network, and appears to authenticate, but iwconfig still has no access point and using dhclient still times out.

---

### Post by Ayuthia on 2008-08-10
> **4lc0h0l1c said:**
> I followed the steps from kevdog here [http://ubuntuforums.org/archive/index.php/t-523524.html](http://ubuntuforums.org/archive/index.php/t-523524.html) bringing wlan1 down and removing the pid file, and when I ran the wpa_supplicant command, I can see from the output that it can see my wireless network, and appears to authenticate, but iwconfig still has no access point and using dhclient still times out.

You might try and see if you can connect without WPA.  It will help determine if the card works.

I forgot that you said that you installed the card.  Can you provide the results of the following:
```
lspci -nnm|grep Broad
ls -l /etc/ndiswrapper/bcmwl5
```
I meant to ask this the first time.  I wanted to see the subvendor information.  I still have a theory the subvendor information makes a difference with the drivers.  These two commands will show the subvendor information of your card and the other one will show the driver info.  I am curious if subvendor numbers match up.

---

### Post by 4lc0h0l1c on 2008-08-10
I can't connect without WPA because I can't see any networks at all with the broadcom card.

I know the card works (at least to the point of being able to scan networks) because several months ago, before I hosed all my network settings, I forgot I had put this card in the machine.  I got error messages saying I needed different firmware for the broadcom card, so I went through the tutorials thinking "do I have an onboard card I didn't know about?" The drivers successfully installed and afterwards I always had options for 2 wireless interfaces, and they both reported [almost] the same networks, and I thought it was some linux software quirk until I remembered yesterday I actually do have this card, and unscrewed the back of the laptop....


$ lspci -nnm | grep Broad
00:09.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Compaq Computer Corporation [0e11]" "Unknown device [00e7]"



$ ls -l /etc/ndiswrapper/bcmwl5
total 1056
-rw-r--r-- 1 root root   1260 2008-08-10 20:55 14E4:4311:0007:1028.5.conf
-rw-r--r-- 1 root root   1262 2008-08-10 20:55 14E4:4311:0008:1028.5.conf
-rw-r--r-- 1 root root   1260 2008-08-10 20:55 14E4:4311.5.conf
-rw-r--r-- 1 root root   1326 2008-08-10 20:55 14E4:4312:0007:1028.5.conf
-rw-r--r-- 1 root root   1328 2008-08-10 20:55 14E4:4312:0008:1028.5.conf
-rw-r--r-- 1 root root   1326 2008-08-10 20:55 14E4:4312.5.conf
-rw-r--r-- 1 root root   1264 2008-08-10 20:55 14E4:4318:0005:1028.5.conf
-rw-r--r-- 1 root root   1258 2008-08-10 20:55 14E4:4318:0006:1028.5.conf
-rw-r--r-- 1 root root   1266 2008-08-10 20:55 14E4:4318.5.conf
-rw-r--r-- 1 root root   1330 2008-08-10 20:55 14E4:4319:0005:1028.5.conf
-rw-r--r-- 1 root root   1324 2008-08-10 20:55 14E4:4319:0006:1028.5.conf
-rw-r--r-- 1 root root   1332 2008-08-10 20:55 14E4:4319.5.conf
-rw-r--r-- 1 root root   1266 2008-08-10 20:55 14E4:4320:0001:1028.5.conf
-rw-r--r-- 1 root root   1248 2008-08-10 20:55 14E4:4320:0002:1028.5.conf
-rw-r--r-- 1 root root   1264 2008-08-10 20:55 14E4:4320:0003:1028.5.conf
-rw-r--r-- 1 root root   1246 2008-08-10 20:55 14E4:4320:0004:1028.5.conf
-rw-r--r-- 1 root root   1266 2008-08-10 20:55 14E4:4320.5.conf
-rw-r--r-- 1 root root   1332 2008-08-10 20:55 14E4:4324:0001:1028.5.conf
-rw-r--r-- 1 root root   1314 2008-08-10 20:55 14E4:4324:0002:1028.5.conf
-rw-r--r-- 1 root root   1330 2008-08-10 20:55 14E4:4324:0003:1028.5.conf
-rw-r--r-- 1 root root   1312 2008-08-10 20:55 14E4:4324:0004:1028.5.conf
-rw-r--r-- 1 root root   1332 2008-08-10 20:55 14E4:4324.5.conf
-rw-r--r-- 1 root root 555872 2008-08-10 20:55 bcmwl5.inf
-rw-r--r-- 1 root root 424320 2008-08-10 20:55 bcmwl5.sys

---

### Post by 4lc0h0l1c on 2008-08-11
Update:
I booted into a PCLinuxOS LiveCD and it worked immediately....then stopped.  I now know the card works fine for sure, because I got online with it with my wired cable unplugged.  PCLinuxOS used bcmwl5 and ndiswrapper out of the box.  If I repeatedly scan for wireless networks, one out of about every ten times it will see my network.  If I reconfigure it with the built in administration app, sometimes I can get online with it, but not for more than a few minutes before it drops the connection.

My conclusion: linux support for this card sucks.  If anyone's got any better ideas, I'm happy to hear them.

---

### Post by 4lc0h0l1c on 2008-08-11
I've been working on this for waaay too long...please don't check the frequency of my posts...
I switched to using bc43xx and not ndiswrapper and the exact same thing happened.
This is a manifestation of the "access point: invalid" or "access point:not-associated" problem.  I've googled those and gotten thousands of hits....with no solutions.
This happens in conjunction with getting no networks from iwlist eth1 scan (my wireless is eth1 now for some reason).  I have no idea how PCLinuxOS was able to find an access point sometimes.  When I scan, it returns "no scan results" *immediately*.  Something is obviously incorrect, as anytime I've gotten scan results on any card from this command, it takes a second to come up with them.
If anyone knows anything about this, please help.  I'm pretty sure I've read every single how to on the net about getting broadcoms to work.
[Edit: I somewhat duplicated the behavior of PCLinuxOS.  I installed all the drivers I could find, and ran repeated scans of the interface, and every so often it does indeed show up as detecting my wireless interface instead of saying "not-associated or "invalid", although I never got it to show for long enough to actually get any net connectivity.  For future readers: get a different card.  8.04 broke support for this card, among many other things.]

---

### Post by Ayuthia on 2008-08-11
Since your card is a 4306 rev 02 card, yours most likely falls under the b43legacy driver instead of the b43 driver.  Can you tell me if you are using b43 or bcm43xx?  If not, can you post the results of:
```
ls /lib/firmware
```
If there is a b43/b43legacy folder, then you are using the new b43/b43legacy driver, but if you have bcm43xx files in /lib/firmware, then you are using bcm43xx.  We still have some options to make it work.

The windows driver that you are using does not seem to be a 100% match with your card.  Your info is showing that your card is 14e4:4320 0e11:00e7.  If you take look at the results of /etc/ndiswrapper/bcmwl5, you will see that there was no match for yours.  From what I can tell, the driver is from Dell so it only had the Dell drivers listed.  It does not necessarily mean that it does not work for yours, the files that you see in /etc/ndiswrapper/bcmwl5 will list the chipsets that should work with that driver.  At least that is my theory.

I just looked for a driver that should work for you and it seems that the driver points to the sp33008.exe:
[ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
Did you try this one for ndiswrapper?  It looks like your card matches up with it.

If you could try using that driver, let me know if you can see any wireless sites by doing the following in the Terminal:
```
sudo iwlist scan
```

---

### Post by 4lc0h0l1c on 2008-08-12
I see what you are saying.
Using the link you posted, I get the same results (not-associated, unable to scan).

This file is present in /etc/ndiswrapper/bcmwl5:
14E4:4320:00E7:0E11.5.conf

Should that be the correct one?

the top 4 are directories

$ ls /lib/firmware
2.6.22-15-generic  
2.6.24-19-generic
b43
b43legacy
bcm43xx_initval01.fw  
bcm43xx_initval05.fw  
bcm43xx_initval09.fw    
bcm43xx_microcode4.fw  
rt73.bin
bcm43xx_initval02.fw  
bcm43xx_initval06.fw  
bcm43xx_initval10.fw    
bcm43xx_microcode5.fw                
bcm43xx_initval03.fw  
bcm43xx_initval07.fw  
bcm43xx_microcode11.fw  
bcm43xx_pcm4.fw          
bcm43xx_initval04.fw  
bcm43xx_initval08.fw  
bcm43xx_microcode2.fw   
bcm43xx_pcm5.fw

Does having the firmware for multiple drivers conflict?  I would think the drivers know where to look for their instance of the firmware.

---

### Post by Ayuthia on 2008-08-12
> **4lc0h0l1c said:**
> I see what you are saying.
Using the link you posted, I get the same results (not-associated, unable to scan).

This file is present in /etc/ndiswrapper/bcmwl5:
14E4:4320:00E7:0E11.5.conf

Should that be the correct one?

the top 4 are directories

$ ls /lib/firmware
2.6.22-15-generic  
2.6.24-19-generic
b43
b43legacy
bcm43xx_initval01.fw  
bcm43xx_initval05.fw  
bcm43xx_initval09.fw    
bcm43xx_microcode4.fw  
rt73.bin
bcm43xx_initval02.fw  
bcm43xx_initval06.fw  
bcm43xx_initval10.fw    
bcm43xx_microcode5.fw                
bcm43xx_initval03.fw  
bcm43xx_initval07.fw  
bcm43xx_microcode11.fw  
bcm43xx_pcm4.fw          
bcm43xx_initval04.fw  
bcm43xx_initval08.fw  
bcm43xx_microcode2.fw   
bcm43xx_pcm5.fw

Does having the firmware for multiple drivers conflict?  I would think the drivers know where to look for their instance of the firmware.

Having the firmware for bcm43xx and b43 does not cause any problems because I have the firmware for them also and have no issues.

The driver that you are using is what I figured would have worked.

Here is what you can do to try the bcm43xx driver:
```
sudo modprobe -r ndiswrapper b43 b43legacy ssb bcm43xx wl
sudo depmod -ae
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```
This is assuming that wlan0 is your Broadcom card.

Here is what you can do to try the b43 driver:
```
sudo modprobe -r ndiswrapper b43 ssb bcm43xx wl b43legacy
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
```

And here is what you can do to try the b43legacy driver:
```
sudo modprobe -r ndiswrapper b43 ssb bcm43xx wl b43legacy
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
```

Hopefully one of those three will produce something.

---

### Post by NoDecaf on 2008-08-12
> **4lc0h0l1c said:**
> 
Does having the firmware for multiple drivers conflict?  I would think the drivers know where to look for their instance of the firmware.

no, the kernel will automatically load the correct driver for your card.

---

### Post by 4lc0h0l1c on 2008-08-12
Using b43legacy or bcm43xx gives me a wireless interface.  They both exhibit the issue of having no access point.  Same thing if I load with ndiswrapper.  Loading b43, b44, or any other module does not show a wireless interface.  dmesg gives output that seems like it loads the driver fine, and it seems like it does.  I just don't show any wireless networks or access points.  I would think at this point that my card is broken but I had this working just a couple months ago, before upgrading to 8.04 come to think of it, and PCLinuxOS was able to get online with this card.

I read that if you don't run iwlist <iface> scan with root priveledges, it doesn't scan, just outputs the last scan results, which is why sometimes it would give me results instantly....but I still get no scan results running with sudo.

---

