---
title: "Wireless card - w200 on Compaq Evo N800w wont work. Please Help!"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by changingessence on 2008-06-04
I am new to linux. I am running Ubuntu 8.04. When I installed Ubuntu my wireless card did not work. I have tried some of the fixes form some online forums but nothing seems to work. Now when I type lsusb in the terminal the cursor vanishes and the terminal stops functioning (I can type stuff but it doesn't care)

Any help would be appreciated I link linux but it can be frustrating to get started.

~Mike

---

### Post by changingessence on 2008-06-04
This info could help for some info about my computer


```
mike@mike-laptop:~$ lspci | grep -i network
mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mike@mike-laptop:~$ sudo lshw -C network
[sudo] password for mike: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:6c:14:15
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
mike@mike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:6c:14:15  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe6c:1415/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109923818 (104.8 MB)  TX bytes:8350393 (7.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78716 (76.8 KB)  TX bytes:78716 (76.8 KB)

mike@mike-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

mike@mike-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
mike@mike-laptop:~$ lsusb

and now it does not let me do anything in terminal


```

---

### Post by Unix_Slayer on 2008-06-04
> **changingessence said:**
> This info could help for some info about my computer


```
mike@mike-laptop:~$ lspci | grep -i network
mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mike@mike-laptop:~$ sudo lshw -C network
[sudo] password for mike: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:6c:14:15
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
mike@mike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:6c:14:15  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe6c:1415/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109923818 (104.8 MB)  TX bytes:8350393 (7.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78716 (76.8 KB)  TX bytes:78716 (76.8 KB)

mike@mike-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

mike@mike-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
mike@mike-laptop:~$ lsusb

and now it does not let me do anything in terminal


```

**_You Have no USB device installed._**  What type of adapter do you have?

---

### Post by changingessence on 2008-06-04
> **Unix_Slayer said:**
> **_You Have no USB device installed._**  What type of adapter do you have?

I have read a few online threads of people dealing with the same problem. Most of them seem to come to the conclusion that the wireless card is a usb device. The card says w200 on the side and comes stock with many compaq laptops (like my evo n800w) The card is attached to the back of my LCD screen and does not plug into any of the external usb ports.

One of the threads I read had someone that could see the device when he entered lsusb in the terminal. (He was able to tun the card on and off by pressing Fn F2 and visualize this by checking lsusb) When ever I type lsusb the terminal kinda shuts down. I can still type but the termal does not respond to anything.

Note: Fn + F2 is how the device is turned on and off in windows.

thanks for helping me

~Mike

---

### Post by Unix_Slayer on 2008-06-05
> **changingessence said:**
> I have read a few online threads of people dealing with the same problem. Most of them seem to come to the conclusion that the wireless card is a usb device. The card says w200 on the side and comes stock with many compaq laptops (like my evo n800w) The card is attached to the back of my LCD screen and does not plug into any of the external usb ports.

One of the threads I read had someone that could see the device when he entered lsusb in the terminal. (He was able to tun the card on and off by pressing Fn F2 and visualize this by checking lsusb) When ever I type lsusb the terminal kinda shuts down. I can still type but the termal does not respond to anything.

Note: Fn + F2 is how the device is turned on and off in windows.

thanks for helping me


~Mike

That's an odd contraption. Did Compaq sell it that way, or is it an addon? Just curious. Because I am able to 98% of the time, get any adapter working. Whether it USB, or a PCI/wired combo.

Actually if you could, a quick picture would help reference it better for me. Are there any version codes on it? Also.... What kind/type adapter does Windows see it as? That would be helpful as well.

---

### Post by Unix_Slayer on 2008-06-05
P.s. Have you tried the tutorial on this link yet? ==>[http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless&page=9]("http://ubuntuforums.org/showthread.php?t=769990&highlight=wireless&page=9")

---

### Post by changingessence on 2008-06-05
> **Unix_Slayer said:**
> That's an odd contraption. Did Compaq sell it that way, or is it an addon? Just curious. Because I am able to 98% of the time, get any adapter working. Whether it USB, or a PCI/wired combo.

Actually if you could, a quick picture would help reference it better for me. Are there any version codes on it? Also.... What kind/type adapter does Windows see it as? That would be helpful as well.

This link will give more info about the card: http:[//h20331.www2.hp.com/Hpsub/cache/295352-0-0-225-121.html]("http://h20331.www2.hp.com/Hpsub/cache/295352-0-0-225-121.html") 

It was not an addon it came with my computer. I have attached an image. Havent had a chance to try your link.

---

### Post by Unix_Slayer on 2008-06-05
Another question. This page has a big list of adapters that could have been used on your laptop. If you have used Windows on this laptop, do you know which device it is? Is it the Intel, or the Broadcom?

See Link ==>[http://http://h20331.www2.hp.com/Hpsub/cache/295457-0-0-225-121.html]("http://http://h20331.www2.hp.com/Hpsub/cache/295457-0-0-225-121.html")

---

### Post by fluffkitten on 2008-06-05
> **changingessence said:**
> This link will give more info about the card: http:[//h20331.www2.hp.com/Hpsub/cache/295352-0-0-225-121.html]("http://h20331.www2.hp.com/Hpsub/cache/295352-0-0-225-121.html") 

It was not an addon it came with my computer. I have attached an image. Havent had a chance to try your link.

Its an Orinoco USB device. Got one on my N600c but have yet to try it with 
8.04. There is quite a god HOWTO on the community documentation site. 

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)   

fK

---

### Post by Unix_Slayer on 2008-06-05
> **fluffkitten said:**
> Its an Orinoco USB device. Got one on my N600c but have yet to try it with 
8.04. There is quite a god HOWTO on the community documentation site. 

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)   

fK

I guess this statement from the webpage you supplied explains everything.

"This device can be very frustrating indeed under Linux. The MultiPort interface inside the lid-mounted shell is in fact USB electrically - if you are good with electronics, you may seriously consider gutting the shell and putting a well-supported USB wifi adapter inside it."

---

### Post by changingessence on 2008-06-05
> **fluffkitten said:**
> Its an Orinoco USB device. Got one on my N600c but have yet to try it with 
8.04. There is quite a god HOWTO on the community documentation site. 

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)   

fK

I went to the link and everything seemed to work until I got to 

```
sudo modprobe -v orinoco_usb help
```

Then the terminal goes to the next line but nothing happens. I says that if it worked the light on my wireless card should turn on but it doesn't.

Anyone have a suggestion?

Thanks

---

### Post by changingessence on 2008-06-05
That code should be 

```
sudo modprobe -v orinoco_usb
```

---

### Post by fluffkitten on 2008-06-06
> **changingessence said:**
> That code should be 

```
sudo modprobe -v orinoco_usb
```

If the light on it still hasn't come on try hitting Fn+F2, if the W200 isn't
turned on that will turn it on. Not sure if the W200's on/off button works
with the N800w (doesn't with the N600c) but you could try that if you've
still got hassles.

Beyond that I'm afraid I've no ideas about getting it going. The Doc page was
the thing that finally enabled me to use my W200 after loads of frustration.

fK

---

### Post by fluffkitten on 2008-06-06
> **Unix_Slayer said:**
> I guess this statement from the webpage you supplied explains everything.

"This device can be very frustrating indeed under Linux. The MultiPort interface inside the lid-mounted shell is in fact USB electrically - if you are good with electronics, you may seriously consider gutting the shell and putting a well-supported USB wifi adapter inside it."

Yep, the thing is evil. :) I have the greatest admiration for the people
who've managed to hack together a driver for it, can't have been an easy
job.

fK

---

### Post by Unix_Slayer on 2008-06-06
If you can't get it going, I would suggest gutting it, and putting a Linksys device in the case.

---

### Post by scrumpydude on 2008-06-28
Hi,

The W200 card used to work fine with Ubuntu (as long as you followed the Howto on it [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)). However, the last two kernel releases seem to have broken it. The last kernel release that I think works with it is 2.6.24-16. If I manage to get it working again I'll post back here with the info.

TTFN

---

### Post by g.c.rousseau on 2008-07-05
Same problem here with my Evo n1000c.  I tried the w200 wiki tutorial and it worked except that I cannot turn the device on with fn+f2.  I think if I could configure fn+f2 to power on the usb device, it would actually work!  any ideas?

Thanks,

Geoff

---

### Post by g.c.rousseau on 2008-07-06
Just tried the w200 method again with the older version of the kernel 2.6.24-16-generic and it did not work for my evo n1000c.  In xconsole it says that the key e078 is not specified when i try to turn on the wireless card with fn+f2.

how do i go back to an older version of the kernal than this so i can try it again? 2.6.24-26 was the oldest one i had on grub to choose from.

Geoff

---

