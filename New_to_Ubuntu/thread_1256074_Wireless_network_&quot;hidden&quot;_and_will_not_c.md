---
title: "Wireless network &quot;hidden&quot; and will not connect."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by deviantdan on 2009-09-02
Hi,,, total beginner here.  I only installed ubuntu a few weeks ago.  I was surprised at how everything just worked within minutes of install with very minimal stuffing around.  However i now have a problem..

For no apparent reason my router does not show up in the list of available networks.  I can select "join hidden network" and it is there but it just hangs and then repeatedly asks me for my WPA key which I've typed in correctly each time, yet it doesn't connect. 

I can't think what I may have done to cause this.  The other computers work fine (mac and PC) and this very same machine works fine in an XP boot.  I even tried booting from Live USB and it's still not showing up.

confused :-/

---

### Post by aeiah on 2009-09-02
sounds like you've only got a partially supported wireless card. you may need to install some drivers manually. is your wireless card a usb dongle or an internal wifi card?

if its usb, open a terminal (menu > accessories > terminal) and issue the command:
```

lsusb

```
and post the results. if it's internal you'll have to issue the command
```

lspci

```

this will give us the specifics of exactly what wireless card you're using.

---

### Post by deviantdan on 2009-09-02
lspci

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
05:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```

my card is a D-Link DWA547 if that helps

---

### Post by aeiah on 2009-09-02
the useful bit is:
```

05:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

which is a little odd. i thought atheros chipsets were very well supported

---

### Post by aeiah on 2009-09-02
according to a quick google i found this:
[http://ubuntuforums.org/showthread.php?t=727964](http://ubuntuforums.org/showthread.php?t=727964)

and the guy there solved his issue by using:
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)


however this uses a nightly build and since the thread was last year, it's a suprise that it hasnt been included in ubuntu by now. what version are you running? are you able to update ubuntu via a wired network connection?

---

### Post by deviantdan on 2009-09-02
I have the latest version... it was working perfectly up until a few days ago.  maybe after the last update?

---

### Post by aeiah on 2009-09-02
perhaps yea. does it find any wireless networks at all?

what does ifconfig show you?

---

### Post by ayenack on 2009-09-02
This worked for someone I was trying to help ages ago not sure it will for you but worth a try.

Turn off Hidden SSID in the router connect from your Ubuntu box make sure you can surf then turn back on Hidden SSID then restart the  Ubuntu box and it may well connect automatically.

Other than that check to see if the router is using MAC address filtering. If it is you'll have register your Ubuntu box with the router.

BTW. If either of the above works you may well have to save it in your router and do a restart of the router. Otherwise the next time your router looses power it'll re-set to the default settings and you'll be left scratching your head again.

---

### Post by t0p on 2009-09-02
Post the output from the commands

```
ifconfig
```

and 

```
iwconfig
```

This should show us the status of your wireless interface.

---

### Post by pbateman on 2009-09-02
I am using a thinkpad latop with an Atheros card as well. I had a similar issue and tried just about anything but could not get it to work either with my hidden network.
In my case, it would take forever to connect, and i had to do it manually by going into 'connect to hidden newtork' and then it wouldn't remember the passkey so I had to manually enter it all the time..etc. Eventually after it would connect it would lose connection after about 5-10 minutes.
I was able to fix the connection drop by using the madwifi drivers (under System-Preferences-Hardware drivers), but it would still take about 10 minutes of manually messing with it to connect...it would not auto connect after a reboot
To make a long story short, the only way I was able to fix it was by broadcasting the SSID. Now it connects automatically after reboots with no issue. 
I was reading in a Thinkpad forum that apparently Ubuntu has issues with the Atheros card and hidden networks, in my case at least, that seemed to be the case. 
In short i would try first using the madwifi drivers, if that doesnt help I'd try broadcasting the SSID. 
I might try what ayenack mentioned of turning the broadcast off again  to see if it still connects but as of now I have it broadcasting and its working great.

---

### Post by deviantdan on 2009-09-02
> **aeiah said:**
> perhaps yea. does it find any wireless networks at all?

what does ifconfig show you?

yes it sees other networks...

I don't think that I set the router to "hidden" tbh.. I had a look for the setting just now and couldn't find it, but it's never been hidden before.

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:e5:8c:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:3b:4f:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-3B-4F-0F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by winotree on 2009-09-02
Link Quality:0  Signal level:0  Noise level:0

??

---

### Post by aeiah on 2009-09-02
> **winotree said:**
> Link Quality:0  Signal level:0  Noise level:0

??

well yea, its not connected. what kind of link quality did you expect? :p

as a side note, hiding your SSID is pretty pointless because its trivial to detect anyway (although i know this doesn't particularly apply to you deviantdan)

hmm. i guess you could use the terminal to scan for wireless networks. this would rule out network manager as being the problem anyway.
```

iwlist wlan0 scan

```

also try turning off your wireless encryption on the router, see if it works, then bumping things back up to secure and see where the problem is. there's a chance there's a bug with the encryption side of things i suppose (try WPA instead of WPA2 or one of them instead of mixed etc).

---

### Post by winotree on 2009-09-02
Thanks for the clarification -- I'd assumed as much but it nice to know my old eyes weren't fooling me!!

---

### Post by deviantdan on 2009-09-04
encryption off or on doesn't make any difference...

the terminal scan above returned no results... which is weird because some wireless networks are visible in the GUI.....

:-/

---

### Post by deviantdan on 2009-09-06
anyone? I still can't get this to work in Live boot or booting from previous kernal... my windows partition works fine :-/

---

### Post by ayenack on 2009-09-06
Did you try turning off hidden SSID in your router?

As I said earlier this worked for someone I trying to help some time ago. After he'd turned off hidden SSID he could establish a connection when he turned it back on again he was connected automatically. As far as we could work out it was more to do with the router not keeping the client details.

It's worth a try.

Also are you sure you're not using MAC address filtering in the router?

---

