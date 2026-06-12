---
title: "How-To: WiFi config using NDISwrapper"
date: 2004-12-28
forum: Networking &amp; Wireless
---

### Post by magicfab on 2004-12-28
I' ve used this method to successfully install drivers for several WiFi mini-PCI cards, which usually come integrated into recent laptops. My latest successful install was for an RT2500-based card in an Averatec Athlon XP-M 3250-HX01 computer. 

**UPDATE** : it seems there are [kernel drivers](http://rt2x00.serialmonkey.com/) (which I was [able to install succesfully](http://ubuntuforums.org/showthread.php?p=133177)) available for this specific wifi radio, however the following how-to still applies and can be used for other wifi radios and adapters. The drivers include a WPA implementation, which explains why wpa_supplicant does not support them. See this [bug report](http://hostap.epitest.fi/bugz/show_bug.cgi?id=27) for updates. Thanks to [Jayded](http://ubuntuforums.org/member.php?u=8957)  for posting about it.

These are the steps I followed:

[list=1]
[*] Using the Synaptics package manager, I installed the **ndiswrapper-utils** and **wireless-tools** packages. If you can' t find the first one, make sure the Universe repositories are activated under  Settings | Repositories.
[*] Open a Root Terminal ( Applications | System Tools | Root Terminal )
[*] Follow the instructions starting at step 2 of [NDISwrapper Installation instructions](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)
[*] Go to Computer | System Configuration | Networking and add the newly configured Wifi interface to your networking setup
[/list]

I would also suggest using a tool such as [Wifi Radar](http://www.bitbuilder.com/wifi_radar/) to discover WiFi networks and manage your WiFi connections. Unfortunately I haven' t found anything supporting more than WEP in the GUI (like WPA, etc.).

In my particular case, I used the drivers suggested at the NDISwrapper site in the list section. I downloaded the [archive with the Windows drivers](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip) to my home directory, then moved them to a new directory called WiFi and unzipped them there. Then I moved back to my parent directory (/home/magicfab) and followed the instructions step by step. **PLEASE NOTE** this is only for an Averatec 3250-HX01 with RT2500-base Wifi! However the results should be very similar for other laptops/WiFi setups.

Some laptops have a button to actually turn on / turn off the integrated WiFi radio - don' t forget to turn it on before your installation or else you'll end up wondering why nothing seems to work - like has happened to me :D

First I make sure I am using the latest kernel for my processor and test to see if NDISwrapper has installed correctly:
```
root@RoadRunner:/home/magicfab # **uname -a**
Linux RoadRunner 2.6.8.1-4-k7 #1 Thu Dec 16 13:19:52 UTC 2004 i686 GNU/Linux
root@RoadRunner:/home/magicfab # **ndiswrapper**
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile   Install driver described by inffile
-e driver    Remove driver
-l           List installed drivers
-m           Write configuration for modprobe
```
Then I verify the Windows drivers archive is there, and make sure the Win2k directory has the INF file:
```
root@RoadRunner:/home/magicfab # **ls**
Desktop  WL54driver2.2.6.0.zip
root@RoadRunner:/home/magicfab # **mkdir WiFi**
root@RoadRunner:/home/magicfab # **mv WL54driver2.2.6.0.zip WiFi/**
root@RoadRunner:/home/magicfab # **cd WiFi/**
root@RoadRunner:/home/magicfab/WiFi # **ls**
WL54driver2.2.6.0.zip
root@RoadRunner:/home/magicfab/WiFi # **unzip WL54driver2.2.6.0.zip**
Archive:  WL54driver2.2.6.0.zip
  inflating: RaLink2_RT2560.exe
   creating: Win2K/
  inflating: Win2K/rt2500.cat
  inflating: Win2K/Rt2500.INF
  inflating: Win2K/rt2500.sys
   creating: Win9xMe/
  inflating: Win9xMe/Rt2500.INF
  inflating: Win9xMe/rt25009x.sys
   creating: WinXP/
  inflating: WinXP/rt2500.cat
  inflating: WinXP/Rt2500.INF
  inflating: WinXP/rt2500.sys
root@RoadRunner:/home/magicfab/WiFi # **ls**
RaLink2_RT2560.exe  Win2K  Win9xMe  WinXP  WL54driver2.2.6.0.zip
root@RoadRunner:/home/magicfab/WiFi # **rm *.zip**
root@RoadRunner:/home/magicfab/WiFi # **ls**
RaLink2_RT2560.exe  Win2K  Win9xMe  WinXP
root@RoadRunner:/home/magicfab/WiFi # **cd ..**
root@RoadRunner:/home/magicfab # ls WiFi/Win2K/
rt2500.cat  Rt2500.INF  rt2500.sys
```
Now I use ndiswrapper to install the driver files - notice the "No such file or directory message":
```
root@RoadRunner:/home/magicfab # **ndiswrapper -i  WiFi/Win2K/Rt2500.INF**
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

ls: /etc/ndiswrapper: No such file or directory
Installing rt2500
```

NDISwrapper now reports the hardware as being present, so I use modprobe to load the drivers. Notice how I use grep to check only the ndiswrapper messages issued by dmesg at the end:
```
root@RoadRunner:/home/magicfab # **ndiswrapper -l**
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

Installed ndis drivers:
rt2500  hardware present
root@RoadRunner:/home/magicfab # **modprobe ndiswrapper**

root@RoadRunner:/home/magicfab # **dmesg | grep ndis**
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper: using irq 11
wlan0: ndiswrapper ethernet device 00:11:09:0b:de:83 using driver rt2500.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver rt2500.sys (Ralink Technology, Inc.,06/10/2004, 2.02.06.0000) added
```

SUCCESS! Now let's try **iwconfig**, it should list the WiFi interface:
```
root@RoadRunner:/home/magicfab # **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11Mb/s   Tx-Power:20 dBm   Sensitivity=-120 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:136/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Notice the interface name is **wlan0**, so you should issue the following command to associate to your nearest (unprotected, unencrypted) access point:
```
dhclient wlan0
```

Remember to carefully review the install instructions at the NDISwrapper site, they are very detailed and contain more information than this specific example. Of course come back and report your success/problems - enjoy!

---

### Post by Averatec5400 on 2004-12-29
Sweet,

That is exactly what I did and was going to write up, but I ran into christmas and no internet access or wireless access.

you can also do the extracting of zip file from GUI, but your way was easier to show without screenshots/flash

---

### Post by RockDoctor on 2005-01-13
Worked like a charm.

Thanks!

---

### Post by Mantle on 2005-02-04
I get stuck at the modprobe ndiswrapper stage. It keeps saying "module ndiswrapper doesn't exist" or something to that effect. I am using the 4.10 LiveCD and I read a review of it saying he couldn't get networking to work at all using the LiveCD which is a huge shame. However, I am fairly sure I am doing everything else correctly as I CAN use ndiswrapper successfully in Knoppix 3.7 using the same drivers. I've got an Asus WL103b in a laptop. Any suggestions?

---

### Post by jayded on 2005-03-03
What a LOT of work when its all so unecessary and far more unstable than just installing the [rt2x00 kernel driver](http://rt2x00.serialmonkey.com)  ?!?    :lol:

---

### Post by deviant03 on 2005-03-04
How about enabling WEP? I tried to enter my WEP key (hex, 64 bit) as "sudo iwconfig wlan0 key XXXXXXXXXX" or formatted as XXXX-XXXX-XX, both through network preferences and the terminal but it dosent seem to work. When WEP is disabled the wireless network works so Im positive its a problem with WEP.

---

### Post by kevy1963 on 2005-03-05
I agree, my acx111 TI based card works if I disable WEP on my USR router. I too have tried entering my WEP with iwconfig without luck. Help!!!

---

### Post by deviant03 on 2005-03-05
Ive been trying all night to get my Netgear MA521 PC Card to work with no success. So this morning I gave it another shot:

With my card already added in Network Preferences (with my ssid and WEP key) I do "sudo modprobe ndiswrapper" in terminal. Then I go to Network Preferences and click on wlan0 and hit activate. FINALLY Im connected! Using wifi right now, I just hope it stays up.

~Now I remember how I got it working. I switched the 128bit hex key from Open System to Share Key. Everything works fine now but does anyone the difference between the two?

---

### Post by otterit on 2005-03-05
I really wish I had this luck with the Linksys WUSB11 version 2.8 (atmel).

*sigh*

 :-(

---

### Post by magicfab on 2005-03-07
[QUOTE=jayded]What a LOT of work when its all so unecessary and far more unstable than just installing the [rt2x00 kernel driver](http://rt2x00.serialmonkey.com)  ?!?    :lol:[/QUOTE]

Ok, genius, did you notice I wrote the how-to when the drivers you mention did not exist yet ?  :-P 

On the other hand, many thanks for pointing out the drivers \\:D/  , however they are *only* for the Averatec laptops with those specific internal wifi radios. The how-to is still valid for other unsupported wifi cards and radios.

---

### Post by mattisking on 2005-03-30
This worked great for me (adapted for my Linksys WUSB54AG adapter). I'm running Hoary and used the version of ndiswrapper that's in the repository and the drivers that came on the CD for the adapter. It IS Hoary so there are breakages pretty often. So.... ever since I got this working each time I get up in the morning or come home in the afternoon I find the machine completely frozen and have to reset. I can't seem to find any good data to show exactly what's failing. Any suggestions?

---

### Post by mq001k on 2005-04-09
Works great on my Dell Inspiron 1150.
Have Dell Wireless 1350 WLAN Mini-PCI Card by Broadcom
BCM4360 802.11b/g (rev 3)

Used BCMWL5.sys packaged in R90501.exe by Dell.

Ubuntu is nice...

---

### Post by x96riley3 on 2005-10-21
Works great.  I have a Dell Inspiron 2200 laptop with the pentium M processor.  I went to Dells website and downloaded the driver for my wireless card (Dell Wireless 1370 (b/g)WLAN MiniPCI Card).  The driver name is 
R102320.EXE. 

Being new I didn't know how to find the inf file.  I finally figured out all you have to do is unzip the exe file name and there it is.

unzip R102320.EXE

I then followed the rest of the directions you listed above and it worked great.

Many Many Thanks my friends...

-X:D

---

### Post by surajit on 2006-12-01
Coo!!! worked great for me
Thanks

---

### Post by Satanister on 2006-12-02
I'm stuck at the modprobe command.
Can someone help with this error message
satanister@bitch:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
satanister@bitch:~$

---

### Post by birdsixone on 2007-06-09
Awesome tutorial! Worked perfectly for my mt3705 laptop.

---

### Post by hanzahar on 2008-05-23
does this apply for the latest ubuntu?

---

