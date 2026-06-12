---
title: "No wireless connection with wicd or network manager"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-01-27
Been at this for bout a week now and still no luck. I have a Toshiba Satelliet Pro 6100 (my daughters) and have been trying to get it to connect to my Netgear wireless router with absolutely no joy. Two other hp laptops with same os as this one (Mavrick) also using wicd hook up immediately, no problem. This toshiba shows eth1 as my wireless and all three show same config in wicd preferences and netgear icon properties. All three show same Netgear hardware address and essid. At my wits end getting wit-less-er er er. Any help would be very welcome. Thanks.

---

### Post by Foxheadz on 2011-01-27
What exactly happens when you try to connect?

---

### Post by jerrynewt on 2011-01-27
It keeps searching for the ip and after about a minute ti says not connected.

---

### Post by Foxheadz on 2011-01-27
Let's try something to see if it just might be a problem with the software first install dhcpcd ```
sudo apt-get install dhcpcd
``` then run ```
iwconfig (interface) essid '(network name)' key s: (password (no s: if its just numbers))
```

for example ```
iwconfig eth1 essid 'sputnik' key 5147380955
```

then run ```
dhcpcd (interface)
```

---

### Post by Bucky Ball on 2011-01-27
Run this command in a terminal:

```
lshw -C network
```

That will give us the card and whatever driver you have installed. eth0 is generally the wired connection. You should be looking for something along the lines of wlan0. I'm guessing this is running a Realtek wireless card and you may need to install drivers from their site for it (I have a Toshiba Satellite Pro L510 with Realtek card).

Have you got the drivers installed already? System>Admin>Additional Drivers. Have you plugged an ethernet cable into the machine and gotten all updates? That may pick up the card and offer you the appropriate drivers/firmware etc.

---

### Post by Foxheadz on 2011-01-27
Yeah normaly its something like wlan but for some reason on my laptop its eth1

---

### Post by Bucky Ball on 2011-01-27
Run this command:

lshw -C network

... and post the result back here. ;)

Follow rest of instructions in my post. We need to identify the card and if you have a driver installed first.

---

### Post by dBuster on 2011-01-27
Okay this may sound a little off, but have you checked the wireless access point/router to see how many wireless connections it is setup to receive?  I mean I can set my wireless router to only allow say 2 connections what so ever and if two are already on then no others can connect.

OR

The MAC address is filtered and or blocked on the router for that one computer that is not connecting.  

Just some things to think about and check.

One other thing to look at is the security of the wireless connection.  Do you have the one for your daughter setup to connect with the proper security settings ie password for what ever type of security you have chosen, if you have chosen any.

---

### Post by jerrynewt on 2011-01-27
Output of lshw -C network is
*-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:00:39:05:ba:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.102 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:fceff000-fcefffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:86:00:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-23-generic firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b

Brought the laptop back to my place (no wireless router -- cable broadband ethernet. The wireless network at her house is unsecured as of right now until I get this thing straightened out. Her brother set the Netgear wireless router up about three months ago and lost the login info for the router, but until I upgraded from 9.04 (fresh install of 10.10) she no problems connecting at all. Also 10.10 doesn't support her Nvidia GeForce 4 card, so no available drivers in Additional Drivers section.

---

### Post by Bucky Ball on 2011-01-27
Interesting. Doesn't actually say what the card is. ('Product' is missing). Try this:

```
lspci
```

There is a bit there but you are looking for the network controller near the bottom. Post the output here (all is no prob).

Also:

```
iwconfig
```

---

### Post by jerrynewt on 2011-01-27
Ok lspci results in 

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

iwconfig is
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Just in case you need it too here is ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:39:05:ba:e3  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe05:bae3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34694016 (34.6 MB)  TX bytes:2023383 (2.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:86:00:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by Bucky Ball on 2011-01-28
lspci shows no network controller yet eth1 in your iwconfig shows as a wireless device ... is this a USB wireless dongle??? If so, what? If so:

```
lsusb
``````
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
```... is your hardwire. A network controller entry should be present next for your wireless.

```
eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None
```... indicates there is no ESSID assigned (your network name configured on your router) and no access point assigned (your router). Details on local machine match router's? Security key and type correct?

I'm still not convinced you have the correct driver/firmware installed but as it is not showing your network controller that it's hard to figure. Are you actually getting a signal from the router in the wireless icon in your taskbar, just not connecting to the network?

Few ideas there. I'll crank up the box with wicd tomorrow and investigate more. Toshibas can be unfriendly sometimes until trained! Could you put any output between code tags, please, achieved by clicking 'New Reply' not quick reply or 'Go Advanced' in quick reply. ;)

---

### Post by jerrynewt on 2011-01-28
Yeah Bucky Ball wicd shows 84% signal strength, unsecured -- the whole tamale, it just will not hook up. When she had 9.10 she never had any problems at all. It hooked up every time with no problems at all. Kinda wondering bout the whole driver/firmware question though since all worked great in 9.10.

---

### Post by jerrynewt on 2011-01-29
Just finished installing 10.04 and viola wireless came back screamin'. No problems with it now, but can't enable the 96 nvidia driver. Every time I try it boots to grey, black and white lines -- login sound plays but no gui. I tried to do the sudo sh x86-96.43.19-pkg1.run (after downloading it) but same results. Had to boot into recovery and change nvidia to nv in /etc/X11/xorg.conf. Gui is back but no desktop effects.

---

### Post by AwarmRay on 2011-02-05
[SIZE=2]I am new at this, but it sounds like you have the same kind of problem I just had with a Netgear USB wireless plug in. The simple solution I found was to set the Network Connection; Editing [/SIZE][connection name] [SIZE=2]; IPV6 tab; Method: to "ignore."  It kept trying to connect with IPV6 when I had both IPV4 and IPV6 set to Automatic.

I will let someone with knowledge guess why that happened. I certainly do not know.
[/SIZE]

---

