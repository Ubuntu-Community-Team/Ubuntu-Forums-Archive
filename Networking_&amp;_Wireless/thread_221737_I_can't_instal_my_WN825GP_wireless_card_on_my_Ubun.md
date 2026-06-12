---
title: "I can't instal my WN825GP wireless card on my Ubuntu Laptop"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by tholman_ut on 2006-07-23
I just put Ubuntw with at Dual Boot with Win98, the Install went smooth as could be.  Now that I have my Ubuntu up and running I am trying to get my Motorola WN825GP (BCM4306/BCM22050000 chipset) working.  I have another posting here: [http://www.ubuntuforums.org/showthread.php?t=221318](http://www.ubuntuforums.org/showthread.php?t=221318)

I have read several posts and haven't gotten anything to work.  First I tried *sudo apt-get install bcm43xx-fwcutter* of couse my comuter doesn't have the *bcm43xx-fwcutter* file.  I tried to enable the Universe Repository but of course I can't because the laptop cannot connect to the internet (because the wireless card doesn't work).  This seems to be a Paradox of sorts. ](*,) 

I basically tried everything in this article but couldn't get it to work because I don't have the *bcm43xx-fwcutter*.

I tried to import the *bcm43xx-fwcutter* from my Ubuntu Desktop, which can connect to the internet.  I can't seem to get the *bcm43xx-fwcutter* onto any sort of removable media (floppy or CD ROM).

In the articles that I read they say "I assume two things: 1) you can detect the wireless card hardware & 2) you can enable the Universe Repository".  Just my luck the two thing that they "assume I can do" I cannot do (I'm not sure if I can even detect the hardware, when I do a *lspci | grep Broadcom\ Corporation* I get no response at all).

If anyone has any help I would appreciate more than you could ever know.  I have been at this all afternoon and I'm pulling my hair out trying to get it to work.

BTW I am a new comer to Ubuntu (If you couldn't already tell) and I need some serious help!!!!!!! :confused:

---

### Post by tholman_ut on 2006-07-23
Sorry one correction.  I meant dual boot with WinME (shouldn't make any difference but who knows).  Also the only method I have for internet is my wireless card as other modem is a dial up and I don't have dial up service.

---

### Post by bernied on 2006-07-24
If you want to use apt-get you need internet access.
Without internet access you can download a .deb file on another machine, transfer it using a floppy or usb stick, and use 
dpkg -i /path/to/package.deb
to install it.
That was a bit of of a guess, you should do
man dpkg
to make sure that '-i' (install - I hope) option is the right one and the only thing you need.

However, are you sure that's what you want? It looks like this is a job for ndiswrapper, which should already be installed if it was a standard installation of ubuntu. You might just be missing the driver, which is actually a Windows driver (because ndiswrapper is a way of 'wrapping' Windows drivers in linux), which you may have on a CD that came with the adapter. If not, you can probably find it somewere on the net.

So, find ndiswrapper:
locate ndiswrapper
(if you get loads of output, it is probably installed)
Find your Windows driver(s), either on a CD, or on the net (in my experience, there is often a choice between different versions of Windows, and different version may give different results)
Install the driver:
ndiswrapper -i /path/to/driver.inf

There may be another step after that, to tell ubuntu that you want to use that adapter to access the world. Have a look in the System menu.

Here's someone else who's been there before:
[http://www.ubuntuforums.org/showthread.php?t=211759](http://www.ubuntuforums.org/showthread.php?t=211759)

Out of curiosity, what do you get from
lspci
(without the grep)? Is there no mention of network adapters?

If you get no luck at all from lspci, this might help:
[http://www.linuxforums.org/forum/slackware-linux-help/36196-wireless-pcmcia-card-kernel-2-6-12-lspci-help.html](http://www.linuxforums.org/forum/slackware-linux-help/36196-wireless-pcmcia-card-kernel-2-6-12-lspci-help.html)

---

### Post by tholman_ut on 2006-07-25
OK so I went through the same exact as the guy you recomended ([http://www.ubuntuforums.org/showthread.php?t=211759](http://www.ubuntuforums.org/showthread.php?t=211759)) and I got some results but it's not working.  After I installed both .inf files and both .sys files and ran a "sudo depmod-a" and the  "sudo modprobe ndiswrapper" the lights on my card "sort of" came on.  They lit up, but not all the way.  I have obviously missed something here.

When I try to activate my eth0 it just trys to connect and finds nothing.  When I tried to ping my router it said "0 Transmitted" indicating to me that it isn't turning on (plus the power light is only half on).  I also checked "14E4:4320.5.conf" file and made sure the "Radio...|0" was actually set to 0 and not 1.

Well I've tried just about everything that I've read about in the forum and I'm still at a loss.  Does anyone have any idea what I can try next?

---

### Post by bernied on 2006-07-25
Frustrating eh?
At least it looks like you're finding your card - you are getting closer.
My guess is that the answer is somewhere in the results of:
```
lspci
```and
```
ndiswrapper -l
```and
```
ifconfig
```and
```
iwconfig
```Could you post the output from these?

Here's some more to read (but keep in mind that this is an old post, applying to an older version of Debian - which is the parent of ubuntu - so start about half-way down, you already have a 2.6 kernel and ndiswrapper installed):
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/DebianNoCompiles](http://ndiswrapper.sourceforge.net/mediawiki/index.php/DebianNoCompiles)

---

### Post by tholman_ut on 2006-07-25
bernied:
Here are the command files that you asked for.  Obviously the OS is able to detect the wireless card, but it isn't able to communicate with it.  I also noticed that it couldn't find the MAC address (I can't remember where I read that but I remember the assigned MAC address was xx:xx:...:xx).

I also don't know how to enable the wlan0 because my wireless link is called eth0 (in the Accessories-->Admin-->Network).  The article I read seemed to suggest that an "iwconfig" would create the wlan0 but when I ran it nothing happened except what you see below.


tholman@ubuntu-lt:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 FireWire (IEEE 1394): Sony Corporation CXD3222 i.LINK Controller (rev 02)
0000:00:09.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
0000:00:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem (Mob WorldW SmartDAA) (rev 01)
0000:00:0c.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
0000:00:0c.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


tholman@ubuntu-lt:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5a         driver present, hardware present
bcmwl5.sys      invalid driver!
bcmwlntp.sys    invalid driver!


tholman@ubuntu-lt:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7956 (7.7 KiB)  TX bytes:7956 (7.7 KiB)


tholman@ubuntu-lt:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"motorola 79D"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by bernied on 2006-07-26
So it looks like you're getting very close. You have hardware recognised and a driver that is working. However you seem to have tried to install 4 drivers for ndiswrapper, which *might* be a problem.

Have you tried looking at your network settings in the System menu since you got ndiswrapper going? Has your card appeared? If it is detected but is not communicating with it, I'd suggest you clean up the ndiswrapper drivers - you need just one, I'd suggest whichever one was meant for WinXP.

---

### Post by tholman_ut on 2006-07-26
I have tried to install then uninstall all drivers and leave only one, but I still wasn't able to get the wireless card to light up (I have included in this least not all the way up). reply the 14E4:4320.5.conf file that was created by my ndiswrapper with teh bcmwl5a & bcmwl5 since both files are identical (I checked) I only pasted one of them.

It seems that the wireless card isn't being allocated enough power and that is why the LED's only light up partially (it's just a guess but I've tried everything else).  I'm wondering if there is something that I need to adjust in the driver file.  If anyone has a working BCM4306 wireless card could you send me your 14E4:4320.5.conf file so that I can compare the two?
 
NdisVersion|0x50001
Environment|1
BusType|5
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Motorola,03/22/2004, 3.60.7.0

antdiv|-1
BadFramePreempt|0
BTCoexist|0
ccx_rm|0
ccx_rm_limit|300
Channel|11
Country|
EnableAutoConnect|1
EnableLeap|1
EnableSoftAP|0
frag|2346
FrameBursting|1
gpio0|-1
gpio1|-1
gpio2|-1
gpio3|-1
IBSSGProtection|2
Interference_Mode|3
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
RadioState|0
Rate|0
RoamTrigger|-70
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
SSID|
WEP|

---

### Post by tholman_ut on 2006-07-26
I am finally able to access the internet from my laptop, yes yes I got the wireless card working...   Finally.

It ended up being a really small thing that I was overlooking.  After just about giving up I stumbled accross this Ububtu Forum: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I followed the directions in the above forum, which is identical to all of the things that I had done before, except for one thing...

I added "blacklist bcm43xx" to the bottom of my "sudo nano /etc/modprobe.d/blacklist" file.  With that one (seemingly) minor adjustment my wireless card fired right up.  Needless to say I was exstatic. :D 

One minor note to add to anyone reading this is that I didn't have to disable my "eth0" and enable my "wlan0" because I only have a dial up modem and a wireless card on this laptop.  That means that my "eth0" connection is my wlan connection.  Just a side note but maybe it will help someone.

Anyway I appreciate your help in resolving this and I hope that reading this will help another "NEWBIE" in my shoes.

Thanx everyone Ubuntu Forums has saved me once again.
T

---

### Post by tholman_ut on 2006-07-27
OK So I had one more problem.  Whenever I restarted I had to go through the whole process again to get the wireless card to load.  I figured it had something to do with the fact that when I tried to code
```
sudo ndiswrapper -m
```
It would tell that there was already an alias in the file.  When I went into 
```
sudo nano /etc/modprobe.d/ndiswrapper
```
I saw "alias wlan0..." of course I knew that my wlan0 was actually eth0 so I cahnged the "wlan0" to "eth0".

I also added the "eth0" to the end of
```
sudo nano /etc/modules
```

I'm not sure which of these changes fixed my problem, as it may have only been one of the two.  Since it's working now I'm not going to mess with it.

Anyway I thing that takes care of the bcm4306 install that I was having trouble with so thanx for listening.
T :cool:

---

### Post by bernied on 2006-07-27
phew! 
May your internet enjoyment and gained wisdom be worth the frustration.

---

