---
title: "Wireless Not working"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Charles Skyline on 2008-11-27
I am a total newb at this. I just switched over from XP, and my wireless doesn't come on at all.

Here is what I get. 

> **heather@heather-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:03:25:25:54:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16144 (16.1 KB)  TX bytes:16144 (16.1 KB)

**heather@heather-laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**heather@heather-laptop:~$ sudo lshw -c network**
[sudo] password for heather: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:25:54:e0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:f5:32:bf:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:fd:d3:86:c2:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
heather@heather-laptop:~$ 


It seems that it is disabled. 

But when i do the system>admin>hardware drivers and hit activate it installs it, and nothing. 

Any help?

---

### Post by Charles Skyline on 2008-11-28
bump

---

### Post by gnusci on 2008-11-28
Give a look to the sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

To diagnose your problem more information is need:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Charles Skyline on 2008-11-28
all of the info is listed there.

Other than telling you its a gateway laptop.

---

### Post by Ayuthia on 2008-11-28
Can you try the following (in the Terminal):
```
sudo ifconfig wlan0 up
sudo iwlist scan
```

If it does not produce any wireless sites, can you post/attach the results of:
```
dmesg|grep -e b43 -e wlan
```

---

### Post by Charles Skyline on 2008-11-28
> **heather@heather-laptop:~$ sudo ifconfig wlan0 up **
[sudo] password for heather: 
SIOCSIFFLAGS: No such file or directory 
**heather@heather-laptop:~$ sudo iwlist scan **
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 

pan0      Interface doesn't support scanning. 

**heather@heather-laptop:~$ dmesg|grep -e b43 -e wlan **
[    4.107530] b43-pci-bridge 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10 
[   18.644471] b43-phy0: Broadcom 4306 WLAN found 
[   33.771168] input: b43-phy0 as /devices/virtual/input/input9 
[   33.852055] firmware: requesting b43/ucode5.fw 
[   33.916613] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   33.916638] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4). 
[   33.990837] input: b43-phy0 as /devices/virtual/input/input10 
[   34.032065] firmware: requesting b43/ucode5.fw 
[   34.036262] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   34.036287] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4). 
[  154.063172] input: b43-phy0 as /devices/virtual/input/input11 
[  154.104070] firmware: requesting b43/ucode5.fw 
[  154.109681] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  154.109696] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4). 
heather@heather-laptop:~$ 


I even connected a Ethernet cord to it from the router and still a no go.

---

### Post by Ayuthia on 2008-11-28
> **Charles Skyline said:**
> I even connected a Ethernet cord to it from the router and still a no go.

It looks like the firmware is not installed.  Can you go into the Terminal and do the following:
```
sudo apt-get install b43-fwcutter
```

If it says that it is installed and you have a working internet connection, please run the following:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```This should download and install the firmware for you.  Once that is complete, please try the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo /etc/init.d/networking restart
```
This will reload the b43 module that is used for your wireless card and hopefully that will get it going.

---

### Post by Charles Skyline on 2008-11-28
> **Ayuthia said:**
> 
If it says that it is installed and **you have a working internet connection**, please run the following:

Thats the thing, it won't connect at all, I took the ethernet cord from the router to the laptop, and it won't connect. Then I went straight to the modem to laptop, and nothing it won't even realize that i have it plugged in. 

It seems that "it" doesn't even know that it has a modem, or a wireless card. 

And, my net works just fine, I'm on it right now, and even my x-box is connected. 

So, any other suggestions?

---

### Post by gnusci on 2008-11-28
You will need to do it manually, just go to the page:

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

And download the firmware and do the installation, there you will find the instructions.

---

### Post by Ayuthia on 2008-11-28
Does the following get your wired card running:
```
sudo dhclient eth0
```

If not, you can try this [link]("http://ubuntuforums.org/showpost.php?p=6028741&postcount=4") and it provides the information on what you need to download and install into Ubuntu to get teh b43 driver running.

---

### Post by Charles Skyline on 2008-11-28
> **Ayuthia said:**
> Does the following get your wired card running:
```
sudo dhclient eth0
```

If not, you can try this [link]("http://ubuntuforums.org/showpost.php?p=6028741&postcount=4") and it provides the information on what you need to download and install into Ubuntu to get teh b43 driver running.

the code didn't work.

---

### Post by Ayuthia on 2008-11-28
> **Charles Skyline said:**
> the code didn't work.

You might want to try the link that I provided in my last post.  It might help get your wireless up and running.  Then you might create another post for help with the wired connection.

---

### Post by Charles Skyline on 2008-11-28
this [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
does not work for me

---

### Post by Ayuthia on 2008-11-28
> **Charles Skyline said:**
> this [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
does not work for me

That's odd.  I just clicked on the link that you posted and was able to download it.  Are you saying that you are having problems with downloading the file or are you having problems with the file?

---

### Post by gnusci on 2008-11-28
> **Charles Skyline said:**
> this [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
does not work for me

It works fine for me too....

---

### Post by Charles Skyline on 2008-11-28
it downloads just fine, but there is no extracting, its just the file, should I put the file in home directory?

---

### Post by Ayuthia on 2008-11-29
Correct.  It should go into the home directory.  You will also need to get the other file:
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Once you have them in your home directory, you will then need to do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo /etc/init.d/networking restart
```

These commands will extract the information needed from the firmware and then try to activate your card.

---

### Post by Charles Skyline on 2008-12-01
Stupid question, but where is my home directory? Like, how do I extract/ place the files in there?

---

### Post by Ayuthia on 2008-12-01
> **Charles Skyline said:**
> Stupid question, but where is my home directory? Like, how do I extract/ place the files in there?

It is /home/<username>.  So if your username was skyline, your home directory would be /home/skyline.

If you want to copy the files into your home directory, it might be easier to use Nautilus to copy it from one location (like a USB drive) to your home directory.

---

### Post by n2dabloo on 2008-12-01
My wireless just stopped working this morning.  Please help.  It has worked fine, even after my upgrade to 8.10 which is what I'm using now.  I've followed this thread and this is what I see in the terminal: 
darryl@darryl:~$ sudo ifconfig wlan0 up
[sudo] password for darryl: 
darryl@darryl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:E4:43:ED
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-77 dBm  Noise level=-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000412ca4c262
                    Extra: Last beacon: 24ms ago

pan0      Interface doesn't support scanning.

darryl@darryl:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:d1:93:27:e4
Sending on   LPF/eth0/00:a0:d1:93:27:e4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 163.187.3.187 from 163.187.3.129
DHCPREQUEST of 163.187.3.187 on eth0 to 255.255.255.255 port 67
DHCPACK of 163.187.3.187 from 163.187.3.129
bound to 163.187.3.187 -- renewal in 40388 seconds.
darryl@darryl:~$ 

What can I do to restore my wireless?  Thanks in advance.

---

### Post by Ayuthia on 2008-12-01
> **n2dabloo said:**
> My wireless just stopped working this morning.  Please help.  It has worked fine, even after my upgrade to 8.10 which is what I'm using now.  I've followed this thread and this is what I see in the terminal: 
darryl@darryl:~$ sudo ifconfig wlan0 up
[sudo] password for darryl: 
darryl@darryl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:E4:43:ED
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-77 dBm  Noise level=-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000412ca4c262
                    Extra: Last beacon: 24ms ago

pan0      Interface doesn't support scanning.

darryl@darryl:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:d1:93:27:e4
Sending on   LPF/eth0/00:a0:d1:93:27:e4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 163.187.3.187 from 163.187.3.129
DHCPREQUEST of 163.187.3.187 on eth0 to 255.255.255.255 port 67
DHCPACK of 163.187.3.187 from 163.187.3.129
bound to 163.187.3.187 -- renewal in 40388 seconds.
darryl@darryl:~$ 

What can I do to restore my wireless?  Thanks in advance.

What happens when you disconnect your wired connection and try to connect:
```
sudo dhclient -r
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```

---

### Post by n2dabloo on 2008-12-01
When I pull the cable so to speak, I don't get the the same reaction in the little icon at the top of the window panel like I use to.  When I click on that icon, I get a submenu that pops up saying: Network Properties etho, but I don't see the old "searching circle" that I used to see wherein my computer was looking for a wireless connection.

---

### Post by n2dabloo on 2008-12-02
Ok, this is strange.  I booted up this morning and, voila, there's my wireless icon right where it should be and everything is working normally.  I still don't know what caused the loss earlier or what to do in the future if it happens again.  Also, around the same time I was getting an error message about my updates, saying that I had some conflicts with programs.  That has also resolved itself.  I'm guessing when that happened, the wirless "fixed" itself?  Anyway, thanks for the response earlier.

---

