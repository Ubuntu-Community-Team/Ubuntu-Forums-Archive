---
title: "Is my Wi-Fi card installed?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by LonelyTraveler on 2008-05-08
How will I know if my Wi-Fi card is installed? When I click on the network computers in the system tray and make a wi-fi network, I can't pick it up from my phone. Does this mean it is not installed?

Thanks

---

### Post by pytheas22 on 2008-05-08
What is the output of ifconfig and iwconfig?  These will tell you whether the card is installed or not.  Are there any wireless networks in range that you could try to connect to in order to test the card out?

Also make sure that your phone is set up properly to connect to the network you've created--you might have to specify that it should use an ad-hoc connection.

---

### Post by LonelyTraveler on 2008-05-08
> **pytheas22 said:**
> What is the output of ifconfig and iwconfig?  These will tell you whether the card is installed or not.  Are there any wireless networks in range that you could try to connect to in order to test the card out?

Also make sure that your phone is set up properly to connect to the network you've created--you might have to specify that it should use an ad-hoc connection.

Hi Pytheas,

I don't have a wifi network here I can connect to, but at work I can see the wifi networks.

ifconfig and iwconfig output:
```

crownambassador@CrownAmbassador:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:18:d4:0d  
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
          RX packets:2015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91321 (89.1 KB)  TX bytes:91321 (89.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.61.58.193  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:6391060 (6.0 MB)  TX bytes:803858 (785.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:09:a6:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-09-A6-04-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

crownambassador@CrownAmbassador:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
```


I guess as there is a output for wlan0 above it means it is installed? So I should be able to just create network by going to "Create new wireless network" and be able to connect via my phone?

Thanks

---

### Post by pytheas22 on 2008-05-08
> I guess as there is a output for wlan0 above it means it is installed? So I should be able to just create network by going to "Create new wireless network" and be able to connect via my phone?

Yes, from the output above, things do appear to be set up properly on the Ubuntu side.  I would check the settings on the phone's end--make sure it's on the same frequency as your ad-hoc network and that it is configured to connect to ad-hoc networks.

---

### Post by LonelyTraveler on 2008-05-08
> **pytheas22 said:**
> Yes, from the output above, things do appear to be set up properly on the Ubuntu side.  I would check the settings on the phone's end--make sure it's on the same frequency as your ad-hoc network and that it is configured to connect to ad-hoc networks.

I can't find any wifi options on my phone. It simply has a option to connect to what ever wifi network it detects. What bothers me is that when i go the the "creat new wireless network" option on my computer, the button on the bottom of the window says connect and not create. Doesn't this seem a little odd?

---

### Post by pytheas22 on 2008-05-08
The button says connect for me too, although the last time I used Network Manager to create an ad-hoc network was two years ago on Fedora.  Maybe you could try searching for an application to make it easier to make ad-hoc networks--I would be surprised if something built explicitly for that purpose doesn't exist in the repositories somewhere.  Otherwise, I don't know what else you could do to trouble shoot the problem beyond trying to connect with a device other than your phone, or bringing your computer to somewhere where there is a network and trying to connect.

Also, another thought is to create the ad-hoc network with NM, and then use the command "iwlist wlan0 scan" to see if your own card sees it.  This wouldn't rule out problems with other cards seeing the network, but it would be tell you something worthwhile.

---

### Post by LonelyTraveler on 2008-05-09
Searched for my wifi network from my computer in the command line and only picked up the shop next doors wifi network, same thing from my phone and other computer here running Windoze. I've downloaded wi-fi radar and created a network there. Wifi radar shows the network, but it shows there is no signal. And I can't pick it up anywhere else.

---

### Post by LonelyTraveler on 2008-05-09
It seems like my wifi card does not support master mode. Is that possible? 
```
~$ sudo iwconfig wlan0 mode master 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

---

### Post by pytheas22 on 2008-05-09
> It seems like my wifi card does not support master mode. Is that possible? 

I don't know, what kind of card is it?  If you don't know, use the lspci (or lsusb if it's a USB device) command.

It's possible that the driver you use doesn't use iwconfig to set the mode.  Atheros cards for instance have to use their own special utility.

---

### Post by LonelyTraveler on 2008-05-09
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I can never remember witch one it is. The last one?:confused:

---

### Post by pytheas22 on 2008-05-09
Yes, it's the last one, Intel 3945ABG wireless.  Some quick searching on Google makes it look like it doesn't support master mode: see [http://ubuntuforums.org/showthread.php?t=689287](http://ubuntuforums.org/showthread.php?t=689287) or, better, the documentation for the driver, [http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945) .  Note the line, "Current modes unsupported: Master, Repeater, Secondary."  Maybe if you do some more research though there would be a solution; I just did a quick search.

It does say that ad-hoc mode is supported and can be enabled using iwconfig.  I think you should be able to use this mode to do what you want, but I don't know as much about it as I should to tell you exactly what to do.

---

### Post by LonelyTraveler on 2008-05-09
> **pytheas22 said:**
> Yes, it's the last one, Intel 3945ABG wireless.  Some quick searching on Google makes it look like it doesn't support master mode: see [http://ubuntuforums.org/showthread.php?t=689287](http://ubuntuforums.org/showthread.php?t=689287) or, better, the documentation for the driver, [http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945) .  Note the line, "Current modes unsupported: Master, Repeater, Secondary."  Maybe if you do some more research though there would be a solution; I just did a quick search.

It does say that ad-hoc mode is supported and can be enabled using iwconfig.  I think you should be able to use this mode to do what you want, but I don't know as much about it as I should to tell you exactly what to do.

Thanks pytheas. I'll have a look at it tomorrow.

---

