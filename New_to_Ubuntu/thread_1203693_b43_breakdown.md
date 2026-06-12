---
title: "b43 breakdown"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by to25 on 2009-07-03
Hi this may have been mention but i may not have dug far enough. I was using b43, and it just stopped working. I was surfing the web web my negligence caught up with me and my battery died. after that it does not work any more. I tried removing and then reinstalling but it did not work. Any ideas?

I am on:
gateway 7405gx
Broadcom bcm4306 802.11b/g rev3
ubuntu 9.04 jaunty

Oh yes and I am a complete noob.

---

### Post by linuxmagick on 2009-07-03
Can you open a terminal and type in the following command?  It should show us if your wireless interface is being detected and assigned an interface name.
```

ifconfig -a
```

And remember, everyone is a noob at something :-)

---

### Post by MarkusIggy on 2009-07-03
I am experiencing a similar problem. And not just with b43, but we might as well start with that one, because Internet-connection is more important than desktop effects.. ;)

Anyway, earlier today I was at home, listening to music as I was packing stuff for my summer vacation. Just before I left, I let Ubuntu update itself, and then I let [Ksplice Utrack ]("http://www.ksplice.com/") update the kernel. After that, I turned off my computer. Now, I'm in Riga in Latvia, and when I booted up my computer to search for wireless networks, I was unable to find any networks, even though my brother (on his Windows XP-computer) was connected to the Internet just fine. If you're wondering, I'm connected to a cabled modem, and it's no problem using this.

Other problems I encountered is the fact that the desktop effect-settings are not enabled. and it's not possible to enable either. Also, my touchpad is ****** up (might be a problem with the touchpad), and when I connect a USB-mouse, I have to switch USB-ports some times, to get it to work. May it be so that all my problems is because of this new kernel update, or because of Ksplice? I don't know...

linuxmagick requested the output from ifconfig -a from the original poster, and I thought that I might just post mine, in addition. :)

> markus@markus:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:6c:14:05  
          inet addr:87.110.116.80  Bcast:87.110.119.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:4bff:fe6c:1405/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12590258 (12.5 MB)  TX bytes:1484294 (1.4 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

pan0      Link encap:Ethernet  HWaddr ae:52:47:0f:7a:6e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by linuxmagick on 2009-07-03
Okay, MarkusIggy, we'll focus on the Internet connection to start with as you requested.  

I'm not seeing it in your ifconfig output.  Looks like eth0 is your wired connection (an onboard NIC in an HP system, I would guess, based on the MAC address in the output).  

You can try ```
lspci -v | grep Broadcom
``` to see if the system is recognizing your b43 wireless card at all.  If it is you may try re-installing it if you haven't already.  If memory serves me correctly, it should be something like ```
sudo apt-get install b43-fwcutter
``` (this will require that you are connected to the wired connection -- or just do whatever you did to install it to begin with).

---

### Post by MarkusIggy on 2009-07-03
linuxmagick: It looks like this might have solved this part of my problem! :D

Added to 'ifconfig -a', there is also an entry for eth1:
> eth1      Link encap:Ethernet  HWaddr 00:14:a5:ef:e9:7a  
          inet6 addr: fe80::214:a5ff:feef:e97a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:13
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


I looked like the b43-fwcutter had mystically been uninstalled. Now, it's installed again, at least! :)

---

### Post by linuxmagick on 2009-07-03
Awesome!  We're making some progress, at least.  Are you able to detect your wireless network and get online now?

Can you explain what is happening with your touchpad in more detail?

Also, do a ```
glxinfo | grep direct
``` and post the output.  I'd like to see if direct rendering is still enabled or if we need to focus on getting the graphics driver setup again.  Could be a reason why desktop effects aren't working.

---

### Post by MarkusIggy on 2009-07-03
About the touchpad in detail: It's not responding to touch, as it used to do. I think it's broken, and that's it. The laptop is old, and the touchpad have been heavily used, so it's not weird if it is broken, either.

> markus@markus:~$ glxinfo | grep direct
direct rendering: Yes

---

### Post by linuxmagick on 2009-07-03
Did the touchpad problem start after the kernel upgrade, or has it been a problem for a long time?  Same question for the USB mouse.

---

### Post by MarkusIggy on 2009-07-03
The touchpad have been a little on and off lately. I am very sure it's not about the operating system. The problem about the USBmouse, however, started today after the kernel update. I have never earlier had problems with any USB-based devices, so I am pretty sure the USB-mouse problem started after the kernel update.

---

### Post by to25 on 2009-07-03
Here is my ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:03:25:14:1b:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:687440 (687.4 KB)  TX bytes:687440 (687.4 KB)

pan0      Link encap:Ethernet  HWaddr c6:6f:6f:c8:be:b5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:be:fd:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-BE-FD-E6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by linuxmagick on 2009-07-03
To25, it looks like your system has assigned interface wlan0 to your wireless card.  I'm surprised that it isn't working.  Please post the output of ```
lshw -C network
```

Just out of curiosity, how did you install it the first time (System >> Administration >> Hardware Drivers or some other method like fwcutter or NDISwrapper)?

---

### Post by to25 on 2009-07-04
>   *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:14:1b:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.70 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:be:fd:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:6f:6f:c8:be:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



Its funny that you ask that because I have no idea. prior to it working I was fiddling with b43-fwcutter and ndiswrapper trying to get it to work. Eventually I came across this thread where it said I had to you cabextract (I still don't now how) During my thread with others I decided to try the fwcutter method again and it worked. How, I don't know I posted what I thought I did right in my "cabextract cofusion" Thread. I tried what I thought I did but to no avail.  But when I check my network I do see my past connection but it seems that i am not getting any signals and their are a bunch of wifi connections in my neighborhood.

---

### Post by linuxmagick on 2009-07-04
**@to25:**  I think the best thing may be to make sure you've cleaned up the different types of wireless installations you may have going on and start over.  I would start by removing ndiswrapper and giving fwcutter another shot.  If you installed ndiswrapper from the repos, do this:

```
sudo modprobe -r ndiswrapper
sudo apt-get remove ndiswrapper
sudo apt-get install b43-fwcutter
```

Then, after a reboot, see if it is working or at least check and see if there are any differences in your ifconfig -a output.  
[B]
@MarkusIggy:[/B]  I'm not sure I'll be able to help you with your remaining issues.  If no one else responds to you, I can try to do some research when I have a chance.  For the desktop effects issue, do you know what kind of video adapter you have?  Maybe there is a known issue with that particular graphics card and one of the updates you installed?  Or it could be something simpler and obvious and we're just overlooking it.  Who knows?

---

### Post by to25 on 2009-07-04
already removed them and reinstalled b43. I tried removing it again with those commands and hear is the response i got:

> FATAL: Module ndisgtk not found.

for ndiswrapper:

bash: -r: command not found

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

Do you have any other idea, I will also continue to retry reinstalling fwcutter just in case.

---

### Post by linuxmagick on 2009-07-04
```
sudo iwlist scan
```

Let's see if it's even able to see any wireless networks.

---

### Post by to25 on 2009-07-04
Funny thing, As I repeatedly tried to reinstall b43 in different ways, such as deactivateting the driver or activating it, and also removing completely the fwcutter, I almost gave up for the night. I decided to open up firefox and left it oppen. I began to mess with Keyboard Shortcuts and tried to create a command that would toggle the wifi on and off (the wifi light is always on and cant be turned off) After a few minutes of messing with that And the actual kets Function(Fn)+F2, my wifi came on. I guess my wifi was off but I don't remeber turning it off and I wouldn't be able to tell but I did mess with it prior to this thread so i don't know. I remeber reading someones comment saying that he loved ubuntu forums because it always seems as if something magical happens. In my case it probably was the wifi toggle. But to be sure here is the iwlist:

---

### Post by to25 on 2009-07-04
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:AE:FD:A9
                    ESSID:"2WIRE678"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=55/100  Signal level:-71 dBm  Noise level=-65 dBm
                    Encryption key: on
                    IE: Unknown: 00083257495245363738
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000e3689d2fe8
                    Extra: Last beacon: 816ms ago
          Cell 02 - Address: 00:24:56:62:C0:F1
                    ESSID:"2WIRE773"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/100  Signal level:-69 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 00083257495245373733
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a666011181
                    Extra: Last beacon: 1312ms ago
          Cell 03 - Address: 00:14:BF:2E:BE:ED
                    ESSID:"jenny2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/100  Signal level:-71 dBm  Noise level=-65 dBm
                    Encryption key: on
                    IE: Unknown: 00066A656E6E7932
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020007
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001b7094ad188
                    Extra: Last beacon: 1068ms ago
          Cell 04 - Address: 00:24:56:9C:5C:C1
                    ESSID:"2WIRE953"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level:-73 dBm  Noise level=-65 dBm
                    Encryption key: on
                    IE: Unknown: 00083257495245393533
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000ea0a2db181
                    Extra: Last beacon: 1336ms ago
          Cell 05 - Address: 00:16:B6:D7:CD:37
                    ESSID:"Julius2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level:-76 dBm  Noise level=-65 dBm
                    Encryption key: on
                    IE: Unknown: 00074A756C69757332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001b709a0c183
                    Extra: Last beacon: 1060ms ago
          Cell 06 - Address: 00:1F:B3:CA:2D:91
                    ESSID:"2WIRE992"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level:-76 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 00083257495245393932
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000073dc28181
                    Extra: Last beacon: 1144ms ago
          Cell 07 - Address: 00:12:0E:46:50:23
                    ESSID:"chocolate"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/100  Signal level:-68 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 000963686F636F6C617465
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001b70a81c1a7
                    Extra: Last beacon: 392ms ago
          Cell 08 - Address: 00:22:3F:25:28:A4
                    ESSID:"Leontyne"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/100  Signal level:-73 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 00084C656F6E74796E65
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001b7085bc181
                    Extra: Last beacon: 396ms ago
          Cell 09 - Address: 00:22:A4:14:8F:29
                    ESSID:"2WIRE746"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/100  Signal level:-71 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 00083257495245373436
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000182e1cc181
                    Extra: Last beacon: 368ms ago
          Cell 10 - Address: 00:12:0E:45:E6:F1
                    ESSID:"WEST6549"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level:-74 dBm  Noise level=-65 dBm
                    Encryption key:on
                    IE: Unknown: 00085745535436353439
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000a391b4c1a4
                    Extra: Last beacon: 1196ms ago

pan0      Interface doesn't support scanning.

Sorry could not post the scan for some reason, something about images dealing with :o

---

