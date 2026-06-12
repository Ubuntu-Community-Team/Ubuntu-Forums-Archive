---
title: "Slowering the Network"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by makkekkazzo on 2013-11-16
Hallo to everybody,
a week ago I moved in a new house starting living with new people and, on what they have said, till my arrive the internet wifi net was working good. I have a Samsung Galaxy Pocket, an ASUS 700 transformer (both with android) and an ASUS F55A with ubuntu installed. All the devices have worked good alone and all together with other networks. The net has a 6,9 mbit/sec in download, and 732 kbit/sec in upload.
The point is that from my arriving the internet is getting very slow for all the computers and a lot of times my laptop gets disconnected and reconnected and some other times it can't manage to reconnect for more than 5 minutes. I entered the router and I saw that it was really also navigate in the router settings when my mobile was connected to the net, but on the other side even though it is not connected the wifi net is really fuzzy. Usually the 2 android device seem they work better than the laptops.

I don't really understand how to manage to find what is the problem.

Thanks a lot to everybody.

---

### Post by TheFu on 2013-11-17
Every added wifi device halves the available bandwidth effectively. Turn off the radios, turn off the microwave, be close to the antenna (same room is best), avoid walls, especially concrete. Turn off every other 2.4Ghz device around   ... Bluetooth, cordless phones, there must be 500 devices using 2.4Ghz frequencies.

Convince all the neighbors to do the same. If the location is an apartment or townhouse, there isn't really much you can do, since all your neighbors really don't care. In a detached house with half-an-acre around, the outside 2.4Ghz interference isn't all that important.  RF is a 1/r^2 law after all.

Also verify that the router is on the best channel avoiding overlap if at all possible.  In the USA, only channels 1, 6 and 11 do not overlap. Overlapping channels introduce more interference.

If your router and devices support it, use the 5Ghz bands too.  Sadly, 5Ghz doesn't really work over distance or through obstructions, but when it does work, it is great!  It still has the same issues with interference and having too many devices on the frequency. No way around those ...  except

use wired Ethernet for every device that you can.

There is another thread here the last 2-3 days about monitoring a network to determine which clients were sucking all the bandwidth. It was marked solved this morning.

---

### Post by makkekkazzo on 2013-11-17
Thanks for the reply. I tried rebooting the router, using only my laptop with ubuntu, and even though it was working better, at a certain moment it started disconnecting and troubling (I was in the same room of the router). After had switched off my laptop, I tried with a MacBook and it worked fine. Controlling the router, it has always had a good connection with the server. Is it possible that ubuntu has having problems connecting with the router and at the same time is occupying a huge bandwidth that makes troubles for the other laptops, but not for Android devices?

---

### Post by TheFu on 2013-11-18
Let me think aloud. Hope you don't mind.
* works with apple and android - these devices have perfect driver support for their hardware by the manufacturer
* sometimes works well on Ubuntu. Other times, flaky and other times it doesn't work.
* Tested in the same room with local interference removed. Same issues.

So, I'm inclined to think this is NOT terrible levels of interference or any issue with the router.  Ubuntu works with wifi all over the world everyday, so it is not likely to be Ubuntu specific.That leaves the hardware and drivers for the specific wifi card inside the laptop.

Long shot ... the card is just loose inside the machine - reseat it.   If the machine is always in the same place in the room, try a different location. Sometimes there are just weird radio things - highly localized.  Neither of these is likely.

Time to research the hardware and drivers being used. [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) should help gather the data so someone might be able to help. 

I am not good at troubleshooting wifi hardware issues. Sorry.
To start, this is the information that will be needed:
* which OS and release?
* Output from **ifconfig**, **iwconfig** and **route** just to rule out simple networking issues
* Output from the **sudo lshw -short -C network ** command - should show the wifi adapter being used.

With that data, google using "ubuntu" and the model of the wifi card to see if others had the same issues with that hardware.  If others reported issues, perhaps there is a solution for the specific release?

---

### Post by makkekkazzo on 2013-11-21
Your reply seems really sarcastic, but probably it is only me, but it is really really useful thank you. I've done what is written in this already solved thread [http://ubuntuforums.org/showthread.php?t=2163615](http://ubuntuforums.org/showthread.php?t=2163615). Now the network seems working better but I'll see in the next days. If it's solved I'll put the tag. 
Thanks again.

---

### Post by Lars Noodén on 2013-11-21
+1 for using the 5GHz band if you can arrange it

As you read above, the 2.4 GHz is way too vulnerable to interference.  If you look around the net you can find lots of discussion of how to mitigate it.  But solving it is generally not possible in a crowded environment.  Moving to 5GHz is your better option.

---

### Post by makkekkazzo on 2013-11-22
SO guys the things, as we have to expect from a noob, has worsened, the solutions from that thread didn't helped and when I restarted, there are not anymore wireless options or wireless network. Now I'm connected only via ethernet.
This is the actual results from iwconfig, ifconfig, lshw -short -C network and route.
```
makkekkazzo@fra:~$ sudo lshw -short -C network
[sudo] password for makkekkazzo: 
H/W path       Device      Class          Description
=====================================================
/0/100/1c.1/0              network        RT5390 Wireless 802.11n 1T/1R PCIe
/0/100/1c.3/0  eth0        network        AR8161 Gigabit Ethernet
/1             ra0         network        Wireless interface
makkekkazzo@fra:~$ ifconfig
eth0      Link encap:Ethernet  IndirizzoHW 30:85:a9:2e:0f:f0  
          indirizzo inet:192.168.178.27  Bcast:192.168.178.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::3285:a9ff:fe2e:ff0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4552 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:8159058 (8.1 MB)  Byte TX:415076 (415.0 KB)
          Interrupt:19 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:16307 (16.3 KB)  Byte TX:16307 (16.3 KB)

makkekkazzo@fra:~$ iwconfig
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

lo        no wireless extensions.

makkekkazzo@fra:~$ route
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         fritz.box       0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.178.0   *               255.255.255.0   U     1      0        0 eth0



```

> Lars Noodén                   [INDENT]                              Re: Slowering the Network
                          +1 for using the 5GHz band if you can arrange it

As you read above, the 2.4 GHz is way too vulnerable to interference.   If you look around the net you can find lots of discussion of how to  mitigate it.  But solving it is generally not possible in a crowded  environment.  Moving to 5GHz is your better option.         [/INDENT]
    


Thanks for the advice by I won't stay here that much time and for the others is working good, so I'm not going to change that much the network.

---

