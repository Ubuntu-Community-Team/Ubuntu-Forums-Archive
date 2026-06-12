---
title: "Connection repeatedly breaking"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by CLomax on 2008-02-20
I'm using a D-Link DWL G-122 Rev. C1 with a D-Link 124 router and my connection breaks on a constant basis. Just wondering if anyone has any idea as to why and how to fix it.

Thanks in advance.

---

### Post by nixscripter on 2008-02-21
What exactly does "connection breaks" mean? Can you be more specific about symptoms, such as:

1. The networking icon changes to the "no network" symbol, a computer with an X by it.
2. The next time you try to, for example, load a webpage, it gets an error.
3. If your card has lights, they go out or change pattern.
4. The machine is no longer detected on the other end of the network (trying pinging, for example).

---

### Post by ju5tin on 2008-02-22
I have the same problem.

The G122 was configured during installation (7.10 live cd amd64). Network manager asked for the WPA-PSK upon first connection, and connected to the network and full internet access granted and the key kept in the wallet. 

Everything appears normal except at some point the connection will be dropped and can only be reconnected by a restart.

When this happens, network manager icon "attempts to join network" followed by the computer+red cross. The Link light on the adapter is on. 

The network is still shown in the list of available networks although it will try, but fail to reconnect. Network manager does not show any other available network, just the one it was connected to.

I happen to have two of these DWL-G122 c1and the problem remains using both of them.

Occasionally, when the computer shuts down I get some terminal output referring to "disconnecting wlan0", repeated two or three times followed by the computer hanging.

The Ubuntu installation has been updated, successfully each week.


Does this usb adapter need any manual configuration?

Any help is most appreciated.

---

### Post by nixscripter on 2008-02-22
> **ju5tin said:**
> When this happens, network manager icon "attempts to join network" followed by the computer+red cross. The Link light on the adapter is on.


Get it to do that again, open up a Terminal, and post the output of ```
iwconfig
``` and ```
ifconfig -a
```

to see what the network status is.

---

### Post by InRainbows001 on 2008-02-22
hi, im having exactly the same problem it seems. here's what i got from putting those two things you said about into the terminal:


tony@tony-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Belkin_G_Plus_MIMO_E20769"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:E2:07:69   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tony@tony-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:11:C3:D8:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:BC:A4:88  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febc:a488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240068843 (228.9 MB)  TX bytes:12955434 (12.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-BC-A4-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tony@tony-desktop:~$

---

### Post by nixscripter on 2008-02-22
> **InRainbows001 said:**
> hi, im having exactly the same problem it seems. here's what i got from putting those two things you said about into the terminal:


Okay, this may be a different problem.

```

wlan0     IEEE 802.11g  [COLOR="Green"]ESSID:"Belkin_G_Plus_MIMO_E20769" [/COLOR] 
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:E2:07:69   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          [color=red]Link Signal level=-47 dBm[/color]
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It appears to believe it's associated from the green. However, the signal appears to be dead from the red.

```

wlan0     Link encap:Ethernet  HWaddr 00:11:50:BC:A4:88  
         [COLOR="Blue"] inet addr:192.168.2.5[/COLOR]  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febc:a488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240068843 (228.9 MB)  TX bytes:12955434 (12.3 MB)

```

It has an IP, shown in blue, so it is probably attempting to route the packets down the path.

My diagnosis from this information: your wireless signal just keeps dropping out. See if you can use the machine standing right next to the router (no walls or other obstruction) for a long period of time.

Again, this might be different than the person which started the thread. I await his information.

---

### Post by mandeepsmagh on 2008-02-23
[SIZE="3"]     [FONT="Times New Roman"]Hi, all. As I can see u all have similar g122 usb adaptor like me. i also had the same problem.

     I had network connection in roaming mode. Then i did manual configuration and the connection is  
   
      now stabilize. Although it is stabilize at the moment. But I have to wait and check if it stays that way. Don't know why connection breaks in roaming mode. maybe some expert would 
 
      know.  I hope it will help u guys. Good Luck ![/FONT][[/SIZE]

---

### Post by mandeepsmagh on 2008-02-25
[FONT="Times New Roman"][SIZE="4"]
Well, I am having connection breaking problem again. So, manual configugration is not the perfect solution. 

There might be some other problem. When I check connection information it shows** rt73usb ** driver. 

I think I have got the right driver. Really not able to figure it out, what the real problem is ? Pls help guys ![/SIZE][/FONT]

---

### Post by nixscripter on 2008-02-25
mandeepsmagh,

After the connection breaks, please post the output of the same commands I asked of ju5tin: ```
iwconfig
``` and ```
ifconfig -a
```

I'll see what I can do.

---

### Post by mandeepsmagh on 2008-02-26
Hi, nixscripter. This is the result of iwconfig

[PHP]singh@singh-desktop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/PHP]

This is the result of ifconfig -a
[PHP]
singh@singh-desktop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:8C:83:C8   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Base address:0xdf40 Memory:feae0000-feb00000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wlan0     Link encap:Ethernet  HWaddr 00:1B:11:15:A8:70   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:285 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:155048 (151.4 KB)  TX bytes:25887 (25.2 KB) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-15-A8-70-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 [/PHP]

Thanks !

---

### Post by nixscripter on 2008-02-26
```

wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.437 GHz  [COLOR="Red"]Access Point: Not-Associated[/COLOR]
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          [color=red]Link Quality:0  Signal level:0  Noise level:0[/color] 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/PHP]

```

It looks like it doesn't see the network. I assume you did this right after the connection failed?

Please verify you are in range of the network by getting a list of networks: ```
sudo iwlist wlan0 scan
```

Make sure the "Quality" field is greater than 50/100.

---

### Post by ju5tin on 2008-02-26
Hi all

Thanks for your help nixscripter, the reason I have not posted those results is because the connection has not broken since I posted.

This is either ironic, since I actually posted or perhaps is due to a setting that I changed on my router.

I changed the "channel selection" from automatic to manual channel 7. Since then I have had no problems.

My router is 

Product Name:	BT Home Hub 15
Software Release:	6.2.6.E
Software Variant:	BK
Boot Loader Version:	2.0.7
Product Code:	36308970
Board Name:	BANT-Z

maybe try it and see?

thanks, Justin

---

### Post by ju5tin on 2008-02-26
I guess its just ironic, 15 mins later it went down.

```
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
wlan0     Link encap:Ethernet  HWaddr 00:15:E9:A5:05:9A  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7217348 (6.8 MB)  TX bytes:1034325 (1010.0 KB)

```
This was carried out after I reconnected....

 ```
 ESSID:"JTR"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz
                    Signal level=-50 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000018c04a50
```

After the disconnect I removed the adapter, waited a couple of mins and reinserted it. I was then able to select the network from the list (net man icon) and it succesfully reconnected.

Many thanks.

---

### Post by mandeepsmagh on 2008-02-27
Hi, nixscripter. I checked the command u suggested. It shows **signal strength over 60**. But 

  when it is not connected, it doesn't show anything. I have tried another thing by removing 

** network manager**. I just feel network manager could be the cause of problem. i have installed 

** wifi rada**r. it is working good so far, even though it is working only for past 30 minutes. So, I will 

 check if it stays that way.  It may helpful to other guys as well. I keep my fingers cross and 

 thanks  for help !

---

### Post by mandeepsmagh on 2008-02-28
Update. Nothing works. I tried** wifi radar **and then [B]rutilt utility 

[/B]but still nosolution. It is preety annoying, I just don't know what the  

real problem  is. It could be driver, I suupose now, after trying 

everything else. any idea ?

---

### Post by ju5tin on 2008-02-28
Ok, just read this[ thread]("http://ubuntuforums.org/showthread.php?t=684495")

My output of ```
lshw -C network
```
was ```
*-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:e9:a5:05:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 
```
According to that post this means the driver is not installed properly.
> If your network device comes back UNCLAIMED or there is no driver listed, then you have not correctly installed the driver for your device. You must review the procedures for installation of your wireless driver.

Im going to look into a way of installing a driver, I will let you know if it works.

---

### Post by nixscripter on 2008-02-28
From this, I am seeing problems with device drivers:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=27246&sid=203cf3f6e154b72643be168c335d046a](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=27246&sid=203cf3f6e154b72643be168c335d046a)

Try loading rt73 driver instead of rt73usb:

```
sudo rmmod rt73usb
sudo modprobe rt73
```

I don't know if it will work, much less if it's installed with Ubuntu, but it's the next thing I can think of.

Good luck.

---

### Post by PeteZA on 2008-03-01
FWIW I am havin the same issues. I was using Gutsy for about 3 months but got too frustrated with this particular issue and switched back to XP. Have since come back to Ubuntu and have had the same problem....

Wireless stays up for ages and for no apparent reason drops the signal (I am also for the record running a DLink G112).... Any ideas. It is very intermittent so I may or may not be able to post anything when it goes down

---

### Post by mandeepsmagh on 2008-03-08
Stll no solution,  seems like there is problem with **rt73usb driver**.** Which  comes by default in ubuntu**. It is really

annoying. I have done fresh install of ubuntu, to check whether it makes any difference at all. Yet the same

problem persists. So far what I have found, **rt73 usb driver** from** serialmonkey **might be solution to this 

problem. Any other idea ?

---

### Post by rustybronco on 2008-03-08
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by mandeepsmagh on 2008-03-08
Thanks, rustybronco for ur suggestion.but since there is rt73 linux 

driver .That might work better than ndiswrapper. I want to try 

serialmonkey drivrers, but no idea how to compile it. There is also a

thread for installing serialmonkey drivers , but it did not work for me. 

because I don't have wired internet connection, so that might be a 

problem. the only internet connection I  have is wireless.

---

### Post by jocheem67 on 2008-03-08
I'm having a rt61pci chipset with the same probs you guys are having.
For me compiling the serialmonkey drivers was the answer....

The ralinks ( rt's ) are notorious, you'll never get them to work..

[http://ubuntuforums.org/showthread.php?t=584657&highlight=howto+serialmonkey](http://ubuntuforums.org/showthread.php?t=584657&highlight=howto+serialmonkey)

This thread has been very helpful, I've just changed the name of the chip used to mine. Compiling the serialmonkey's is not that hard btw...

---

### Post by rustybronco on 2008-03-09
> **mandeepsmagh said:**
> but since there is rt73 linux 
driver .That might work better than ndiswrapper. I want to try 
serialmonkey drivrers, but no idea how to compile it. 

because I don't have wired internet connection, so that might be a 

problem. the only internet connection I  have is wireless.

download the rt73-cvs from here [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
I extracted the installation instructions for you to read in the interim.
>  3. Install the driver (as root): sudo su  'should do nicely'
```
Installation instructions for the Legacy rt73 module
[[http://rt2x00.serialmonkey.com]](http://rt2x00.serialmonkey.com])


==================
Build Instructions
==================

    1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install


====================
INVOCATION
====================
Load the driver:

    $ modprobe rt73 [ifname=<name>] [debug=<mask>] [firmName=<file>]

    <name> is the name of the device and defaults to "wlan%d". If more
    than one adapter is installed, successive devices will be named
    wlan0, wlan1, etc. If you wish to use a different scheme - say
    eth*, and there are already wired ethernet devices named eth0 and
    eth1, then specifying <name> as "eth%d" gives the adapter the name
    "eth2".

    <mask> is a decimal or hex number. See TESTING file. Ignored if
    driver compiled without debug support.

    <file> is the name of a firmware file and defaults to "rt73.bin"
    if omitted. Only the basename - not the full path - may be
    specified.

Start it up:

    $ ifup wlan0        # If using Debian - or
    $ ifconfig wlan0 up
    $ iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section. Otherwise,
check out the following install notes...

_________
NOTES:

* Firmware file (rt73.bin)

    The rt73 chipset uses a firmware file which is loaded in device
    memory using the kernel firmware_class facility. 'make install'
    copy the firmware file to the standard firmwares location:
    /lib/firmware.

    However some linux distributions divert from the standard and e.g.
    use /lib/firmware/<KERNEL_VERSION>. If this is your case, you will
    have to manually move the firmware file to the right location.
    If you have problems with firmware loading, please ask on your
    distro's support media (forum, etc).

* Driver alias

    rt73 uses wlan* as its modprobe alias. This means you can have
    several devices and they will be named wlan0, wlan1, etc.

    If for some reason you want this interface number 'static' (e.g.
    if you have several wlan devices and their numbers change on
    reboot) you can change the rt73 alias in /etc/modprobe.d/ralink
    (2.6 kernels) or /etc/modules.conf (2.4 kernels) back to wlan0 (or
    wlan1, etc).

    However the proper way to achieve this purpose is to use a udev
    rule based on the wlan MAC address, for example:
    KERNEL=="wlan*", SYSFS{address}=="00:de:ad:be:ef:00", NAME="wlan0"
    (See:
     [http://www.reactivated.net/writing_udev_rules.html#example-netif](http://www.reactivated.net/writing_udev_rules.html#example-netif))

* Module parameters

    You can load the rt73 module with two optional parameters:
       firmName=<FILE_NAME>  Use another firmware file.
       debug=<DEBUG_MASK>    Set debug verbosity (see below).


==============================
Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

    If you're looking for a GUI config tool we provide RutilT on our
    download page
    [[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]).

MANUAL CONFIG:

    1. Set the interface mode and bring it up
          # iwconfig wlan0 mode managed
          # ifconfig wlan0 up

    2. Set your target network / Access Point
       If you just want to join a wireless network, set its ESSID:
          # iwconfig wlan0 essid <ESSID>
       If you want to associate with a specific AP, set its MAC
       address:
          # iwconfig wlan0 ap <BSSID>

    3. Set encryption if needed

       a) WEP (802.11b)
          Choose the authentication mode (open/restricted):
             # iwconfig wlan0 key open
          Or:
             # iwconfig wlan0 key restricted
          Set the encryption key:
             # iwconfig wlan0 key <KEY>

       b) WPA (802.11g)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPAPSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=TKIP

       c) WPA2 (802.11i)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPA2PSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=AES

    4. Check that you're associated with an AP
          # iwconfig wlan0

If everything's ok, you can now configure the wlan0 interface
statically or dynamically (DHCP). If you need more wireless config
details and examples (Adhoc mode e.g.), see iwpriv_usage.txt (included
in driver sources). Otherwise, read the following config notes...

_________
NOTES:

* Auto-load on boot

    If you want your device to come up on boot the best is to use your
    specific linux distribution's tools (boot scripts, etc).
    If you need support doing so, ask on your distro's support media.

* wpa_supplicant

    wpa_supplicant is a userland WPA/WPA2/802.1X layer. This driver is
    not compatible with it. As most wpa_supplicant features are
    embedded into our driver, you should not need it though.
    If you need to use a feature that only wpa_supplicant provides:
       - either use our next-generation rt2x00 driver which
         is compatible with wpa_supplicant
       - or patch wpa_supplicant to make it work with rt73 (more info:
         [http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2](http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2))


==================
Misc. information
==================

* hostapd

    hostapd allows your wlan device to act like an Access Point. Legacy
    drivers are _not_ compatible with it, but our next-generation
    rt2x00 drivers are.

* Network auditing

    Our drivers allow you to peform in-depth wireless network auditing.
    Most of the following settings require that you bring the
    interface down beforehand.

    You can set a custom MAC address as you would do for any other
    ethernet interface:
       # ifconfig wlan0 hw ether <MAC_ADDRESS>

    You can put your wlan interface in promiscuous mode as you would
    do for any other interface:
       # ifconfig wlan0 promisc

    You can put your interface in monitor mode and have it listen to all
    802.11 frames around:
       # iwconfig wlan0 mode monitor

    You can also inject 802.11 frames on the fly. To enable injection,
    run:
       # iwpriv wlan0 rfmontx 1

* Testing / debugging

    If you experience any driver related problem you can ask for
    support on our mailing list or our legacy driver forum.
    Before asking for help, read the TESTING file and follow its
    advice. Do *not* post messages like: "wlan does not work. please
    help!".
```

---

### Post by mandeepsmagh on 2008-03-10
Thanks, rustybronco. U guys are really great. I have installed **serialmonkey drivers** and right now I 

am writing this from ubuntu. So far everything is good.** I can also see connection speed**, [B]which I was 

unable to see before with default rt73usb drivers.[/B] Here is the thread that I followed 
[B][URL="http://ubuntuforums.org/showthread.php?t=400236"]
http://ubuntuforums.org/showthread.php?t=400236[/URL] . [/B]Just follow the steps in this thread and  

anyone can install serialmonkey drivers easily. I will update in few hours, whether it is stable or not.  

Thanks everyone ! :lolflag:

---

### Post by mandeepsmagh on 2008-03-10
Hi, everyone. I have tested internet connection for almost 24 hours and it is very stable. I would 

  recommend everyone to follow the thread I suggested in my  previous post. Some additional information 

  - since network manager do not work with serial monkey drivers (at least it did not work for me), u 

will need to remove network manager and  do manual configuration. If u want u can install [B]rutilt 

wlan manager[/B] because it supports serialmonkey drivers. It feels so good right now, no need to 

reboot into windows every five minutes.:guitar: Thanks everyone.

 I hope it will help u guys. Good luck !

---

