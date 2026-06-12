---
title: "Acer 5520-5334 Atheros AR5007EG Wireless"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by campbecf on 2007-12-05
Been trying to get my wireless working with no luck so far.

I've been using the following as reference:
[http://ubuntuforums.org/showthread.php?t=554531](http://ubuntuforums.org/showthread.php?t=554531)
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

I am using the 64bit AMD version. 

I can see the network, I just can't connect to it with or without protection.

I've used ndiswrapper to load the Atheros driver (multiple versions).

output of dmesg | grep "ndis"
```
[   35.617196] ndiswrapper version 1.45 loaded (smp=yes)
[   36.091292] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   36.093062] ndiswrapper: driver net5211 (,07/26/2007,5.3.0.67) loaded
[   36.093805] ndiswrapper (ZwClose:2247): closing handle 0x0 not implemented
[   36.508341] ndiswrapper: using IRQ 19
[   36.713287] usbcore: registered new interface driver ndiswrapper
```

I have added the following lines to my blacklist file:
```
blacklist ath_pci
blacklist ath_hal
```

ndiswrapper -l gives me:
```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```


What other information can I give that will be useful?

---

### Post by campbecf on 2007-12-05
Is this a lost cause? Without the wireless I can't use Ubuntu :(

---

### Post by AJB2K3 on 2007-12-05
Are you usin nm_applet or wifi radar to connect to wireless connection?

---

### Post by campbecf on 2007-12-05
network-manager-applet I believe.

---

### Post by campbecf on 2007-12-06
Managed to get it working briefly.. no longer though. 

It was connecting, everything was great - put the laptop into standby. Ever since I can't get it to connect properly.

Works great in Windows XP, connects flawlessly so its not the card.

I think it might be network-manager, I can make the application segfault without even trying. All I have to do is click "connect to other wireless network".

Anyone have tips? I'm absolutely fed up with this.

---

### Post by chandler on 2007-12-06
see what lspci gives ya when it's gone...  if it doesn't even show up it may be some power saving thing that turns it off when power goes down?  Not sure, but it's a suggestion.

---

### Post by campbecf on 2007-12-06
lspci:

```
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

By the way - its a AR5007EG, not 6.

As soon as I login to Ubuntu I get the swirly stuff in the network-manager that says "trying to join wireless network "blah"." but it never happens.

---

### Post by rustybronco on 2007-12-06
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

"Atheros AR5007EG ¶
Chipset: AR2425 / AR5007EG  
URL: [http://atheros.com/pt/AR5007EG.htm](http://atheros.com/pt/AR5007EG.htm)  
Supports: 802.11b 802.11g  
Interface: PCI-Express x1  
Device Information: Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01),Subsystem: AMBIT Microsystem Corp. Unknown device 3065  
Notes: not supported by HAL as of 2007.04.28 - resturns Hal status 13  
Notes: Suported by ndiswrapper with windows driver, but some user reports crash problems  
Notes: Instructions about how to use the windows driver + ndiswrapper  

***Notes: works fine with ndiswrapper, using old drivers, search ubuntu forums****  

***Notes: Sometimes erroneously reported as an AR5006EG by lspci"***

---

### Post by campbecf on 2007-12-06
I'm already using ndiswrapper as I stated in my original post, its not working. I simply cannot get connected even though I can see the network.

---

### Post by erfahren on 2007-12-06
what works well for me is this: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
which basically just sets up everything manually in the /etc/network/interfaces file, there's a script there to restart it at boot.

I started using that with Feisty when there wasn't great WPA support. 

I don't use ndiswrapper, and just have the Atheros Hardware Access Layer enabled in the Restricted Drivers. Using the madwifi driver.

---

### Post by rustybronco on 2007-12-06
> **campbecf said:**
> I'm already using ndiswrapper as I stated in my original post, its not working. I simply cannot get connected even though I can see the network.
> Managed to get it working briefly.. no longer though. 

It was connecting, everything was great - put the laptop into standby. Ever since I can't get it to connect properly.
***Notes: Suported by ndiswrapper with windows driver, but some user reports crash problems ****
well it stated works fine using OLD drivers (win98?)  don't know but worth the try.


and this ***Notes: Sometimes erroneously reported as an AR5006EG by lspci"*** was in reference to your report of it being a AR5007EG. always worth the knowledge to someone looking  for help in the future.

---

### Post by campbecf on 2007-12-06
It only has XP / Vista drivers so I don't know what it means by "old".

It isn't crashing, its just refusing to work.

---

### Post by giobertox on 2008-01-05
I have the SAME identical problem 
my Ubuntu 64 bit on my Acer 5520 , and the fact is that :

-SEE the wireless network around (on nm-applet 0.6.5 it shows the list and if they are protected and the quality of the signal)

-DOESNT CONNECT  to any of em (protected wep , wpa or open)




it's so frustrating !

Does anybody has the solution ? please post it if you have an acer 5520 with wireless working on Ubuntu , thanks :KS

---

### Post by campbecf on 2008-01-05
I had to drop down to the 32bit Ubuntu in order to get mine working. :(

---

### Post by Prometheum on 2008-01-05
I have the same problem. AR5007EG card on an HP dv9700. I can see wireless networks, and yesterday I managed to get it to connect to a few, but then it crapped out a few hours later.

I'm at a complete loss. I think it might have something to do with a bug in avahi, but I'm nowhere near certain.

I'm using 64 bit ndiswrapper with 64 bit drivers... Everything set up fine, I have no idea where the problem is.

Are the other people in this thread affected using 64 bit? If so, open up System Log Viewer and see what happens in syslog while you're trying to connect. I have no real idea but that information might be good. If you see something suspicious, post it. I'm getting an error that implies that avahi lacks the privileges to do what it wants to do.

EDIT: Okay, I just connected. This is weird as hell.

Here's a pastebin with my successful and unsuccessful connection attempts.
[http://pastebin.ubuntu.com/3310/](http://pastebin.ubuntu.com/3310/)

---

### Post by adasilva on 2008-01-05
Prometheum,
Did you do anything differently to get it working?

I am having a similar problem (also with 64bit). I can see many networks, and can connect to some, but not my own for more than a second.

---

### Post by zipperback on 2008-01-05
> **campbecf said:**
> 

ndiswrapper -l gives me:
```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```


What other information can I give that will be useful?



Show me the output of:

```

iwconfig

ifconfig

```


Also, you might want to consider installing wicd for your network management.

I have an acer with the atheros chipset as well, and wicd resolved a lot of problems for me.

you can download wicd from:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

- zipperback
:popcorn:

---

### Post by adasilva on 2008-01-05
I hope it's okay for me to post my results here... 

iwconfig:
```
lo        no wireless extensions.

eth24     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig:
```

eth24     Link encap:Ethernet  HWaddr 00:00:6C:27:72:C7  
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe27:72c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10230 (9.9 KB)  TX bytes:27731 (27.0 KB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:2C:84:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:f6000000-f6010000 

```

i tried wicd earlier, and it did not help, but i'll give it another try.

---

### Post by zipperback on 2008-01-05
> **adasilva said:**
> I
i tried wicd earlier, and it did not help, but i'll give it another try.


You're output looks fine.

Install wicd.

Launch wicd.
Click preferences


Set your wireless adapter to:  wlan0

Click OK

Click Refresh

You should now see a list of wifi access points.
Select your access point, click Advanced settings, and add your connection information such as your key and encryption type.
Also click the check box that says automatically connect.
Click Connect and you should be done.

If you are still having problems with your network connectivity, it might be your 10/100 NIC grabbing the ip address and causing you a problem.
If this is the case then launch wicd and click preferences, then set your Wired Interface to none. Then unplug the cable to the NIC.
Then reboot your laptop.

- zipperback
:popcorn:

---

### Post by adasilva on 2008-01-05
wicd is installed, and I can see all of the access points, the preferences have been set... but when I click connect, it appears to get stuck on "Obtaining IP address" and will not connect.

I don't know if this is related, but in the preferences, there is a box for WPA Supplicant Driver. What does this mean? Should it be on ndiswrapper and/or is there a way for me to check which it should be?

At least it seems to be in the right direction.

EDIT: Sorry, I forgot to mention, this is the problem even after setting wired connection to none, unplugging the cable, and rebooting.

---

### Post by campbecf on 2008-01-05
> **zipperback said:**
> Show me the output of:

```

iwconfig

ifconfig

```


Also, you might want to consider installing wicd for your network management.

I have an acer with the atheros chipset as well, and wicd resolved a lot of problems for me.

you can download wicd from:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

- zipperback
:popcorn:

My problem is resolved, I had to switch to 32bit Ubuntu and the solutions already provided in my first post worked fine. This may be an issue affecting only the 64bit version of Ubuntu.

---

### Post by zipperback on 2008-01-06
> **campbecf said:**
> My problem is resolved, I had to switch to 32bit Ubuntu and the solutions already provided in my first post worked fine. This may be an issue affecting only the 64bit version of Ubuntu.

I'm glad to hear you got it up and running at least. 

- zipperback
:popcorn:

---

### Post by Prometheum on 2008-01-06
What are you talking about, Zipperback, installing a different GUI won't change anything. I won't get any DHCP offers if I use the command line, I won't get any in WICD, unless WICD uses non-standard means (i.e. has reprogrammed everything down to the drivers) to set the connection.

This probably is a bug, somewhere in something having to do with our architecture. **Anyone who has this problem should post if they're using 32 bit or 64 bit systems.** We need to get this narrowed down.

I've sniffed the packet stream while attempting to get a DHCP lease, and it isn't working. I don't see any responses from the router. I do see my computer, with the IP it thinks it has, sending enough UDP packets to flood something to what looks like the broadcast address of the network it thinks its on (from the log of my unsuccessful attempt, you can see that the interface thinks I have the IP of 169.254.1.66). The interesting thing is, another computer has another IP in that range, and is sending stuff to the same broadcast address. So maybe this is some routing thing I don't know about.

I'm going to keep trying to find what's going on, people can help by posting their information and the bug they're having. If I can narrow it down to something tangible I'll file a bug report. I don't get what the hell the problem is, and its just weird.

I don't think my router is replying to any of my DCHP requests. You can check for this by installing Wireshark on another computer that can use wifi, opening it as super-user, listening on the wireless interface (start new live capture on that interface), and then use the filter string: "(ip.addr == 0.0.0.0 || ip.addr == 192.168.1.1) && not tcp && not dns". Replace 192.168.1.1 with your router's IP if its different, I think that's what should be there, because in my syslog, that's where the DCHPOFFER came from.

I'll post/edit for further updates.

---

### Post by campbecf on 2008-01-07
Could it be an issue with the 64bit version of the driver not liking ndiswrapper?

---

### Post by zipperback on 2008-01-07
> **Prometheum said:**
> What are you talking about, Zipperback, installing a different GUI won't change anything. I won't get any DHCP offers if I use the command line, I won't get any in WICD, unless WICD uses non-standard means (i.e. has reprogrammed everything down to the drivers) to set the connection.

First off, my discussion of wicd was directed to someone else who actually started the thread. Secondly, they had a nearly working configuration but went back to using another version.

I suggested WICD as a means of easily network management. It wasn't a matter of simply switching to a different GUI, that's absurd. WICD is a network manager application which makes network management a lot easier than using something like the default network manager. And yes it does make a difference if someone is trying to get their network connectivity up and running but they can't seem to get it configured correctly. Using an application such as wicd will take the guess work out of the configuration and allow them to just make it work. If you can see the access points, then you know its working.

Also, wicd allows for the easy management of wep and wpa encryption and the keys for it without having to deal with manual configuration too.

It DOES make a difference, especially if someone is new to Ubuntu and they just need it to work. Making something easy for someone, could mean the difference between that person having a good experience and staying with Linux, and them getting frustrated and going back to another operating system such as Window$.


There may be an bug which prevents it from getting an ip address via dhcp with the 64bit version.

> 
This probably is a bug, somewhere in something having to do with our architecture. **Anyone who has this problem should post if they're using 32 bit or 64 bit systems.** We need to get this narrowed down.

I've sniffed the packet stream while attempting to get a DHCP lease, and it isn't working. I don't see any responses from the router. I do see my computer, with the IP it thinks it has, sending enough UDP packets to flood something to what looks like the broadcast address of the network it thinks its on (from the log of my unsuccessful attempt, you can see that the interface thinks I have the IP of 169.254.1.66). The interesting thing is, another computer has another IP in that range, and is sending stuff to the same broadcast address. So maybe this is some routing thing I don't know about.


It isn't correctly configured if you are getting the 169.x.x.x ip address.
If it is correctly configured it will work.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-07
> **campbecf said:**
> Could it be an issue with the 64bit version of the driver not liking ndiswrapper?

Are you compiling the ndsiwrapper package from source or are you using the one from the repositories. You might also try the most recent one from the developers website.

- zipperback
:popcorn:

---

### Post by Prometheum on 2008-01-10
Well, my networking started working for some reason, and I knew I'd be back here, since I couldn't find the cause.

Installing Wicd does NOT work. The system still hangs trying to get a DHCP lease.

Has anyone on x86_64 had any success with this?

---

### Post by zipperback on 2008-01-10
If you have properly compiled the ndiswrapper from the SOURCE andbe sure you are using the  net5211.inf file set for the Atheros wifi chip set.

Do the following.

Black list the atheros module from the ubuntu installation.


```

sudo gedit /etc/modprobe.d/blacklist

```

Add the following line to the top of the file.

```

blacklist ath_pci

```


Save the file.
reboot

- zipperback
:popcorn:

---

### Post by adasilva on 2008-01-10
Prometheum,
I have a 64 bit processor, and eventually switched to 32 bit linux, and wireless works great with madwifi drivers. I couldn't get it to work with the 64bit version, and I'm still not sure why, but after a few days, I gave up for the time being (as I am a bit busy for the time being).
Just wanted to let you know this option.

---

### Post by Prometheum on 2008-01-12
Ndiswrapper is compiled from source, all the appropriate madwifi drivers are blacklisted. ath_hal isn't loaded on boot, but no matter how much I try I can't seem to remove it from my system (though if it isn't loaded it doesn't matter). I'm also using the appropriate windows driver.

Downgrading to 32 bit isn't an option for me, I don't want to take the performance hit and I also like being able to use all of my RAM. Besides, if this is a bug, it should be fixed to allow functionality on every architecture that Ubuntu is supposed to run on.

Wireless works on the card intermittently. If I chain reboot enough times it'll work, but that's no indicator of future performance. I don't see what besides a driver issue or a hardware defect on the card itself could cause that.

---

### Post by zipperback on 2008-01-12
> **Prometheum said:**
> Ndiswrapper is compiled from source, all the appropriate madwifi drivers are blacklisted. ath_hal isn't loaded on boot, but no matter how much I try I can't seem to remove it from my system (though if it isn't loaded it doesn't matter). I'm also using the appropriate windows driver.

Downgrading to 32 bit isn't an option for me, I don't want to take the performance hit and I also like being able to use all of my RAM. Besides, if this is a bug, it should be fixed to allow functionality on every architecture that Ubuntu is supposed to run on.

Wireless works on the card intermittently. If I chain reboot enough times it'll work, but that's no indicator of future performance. I don't see what besides a driver issue or a hardware defect on the card itself could cause that.


I am currently running the 32bit version of Ubuntu on this laptop, however I have an additional 80gb external drive that I am willing to install the 64bit version onto. I will type up the detailed documentation of how exactly to get the wifi working. I will then post it online here on the forums.

- zipperback
:popcorn:

---

### Post by Prometheum on 2008-01-15
I think I may have found a "fix", but I still don't know why it works and if it works on any systems besides my own.

I'll boot up to a no-internet system. I'll shut down, unplug or plug in the cord on my laptop, and boot up. Then, I'll reboot twice. It seems to work after that.

:confused::confused::confused:

Any luck with the 64-bit install, Zip?

---

### Post by zipperback on 2008-01-17
> **Prometheum said:**
> I think I may have found a "fix", but I still don't know why it works and if it works on any systems besides my own.

I'll boot up to a no-internet system. I'll shut down, unplug or plug in the cord on my laptop, and boot up. Then, I'll reboot twice. It seems to work after that.

:confused::confused::confused:

Any luck with the 64-bit install, Zip?


No luck yet. Still working on it.  You are correct though, it does appear to have a problem with the 64bit version. I'm working on a fix for it. 

- zipperback
:popcorn:

---

### Post by robpower on 2008-01-20
I have the same problem on Ubuntu Gutsy 64 bit.
I tried using madwifi (latest version or asus eeepc patch), ndiswrapper with net5211 driver, and all things founded with google, but still no luck. I tried also wcid: if i try to connect normally it stops while getting IP, if I try to specify IP , gateway, ecc manually, it says : "Connected to None" and IP <the IP number I set up>, but still no Internet and no LAN connection.
I'm sure gateway's IP and other settings are right, i double checked.
Please someone could write a patch also for 64bit version.
Here is a similar bug ( [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/162251](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/162251) ) but i'm not sure if it's really the same. 
Any help would be appreciated! :popcorn:

---

### Post by Prometheum on 2008-02-10
Has anyone had any success with this? I've finally just swapped out to a broadcom card, but I'd like to get rid of it, because the atheros one is better and broadcom makes my kernel panic.

---

### Post by dronin on 2008-02-14
Hm... Changing the hardware address on the wlan0 interface seems to fix the issue for me. I am executing the follow from my start up scripts:

/sbin/ifconfig wlan0 hw ether 00:1E:4C:2D:7F:0A

After that I am able to connect to wireless networks (public and WPA protected) by using wicd. Networkmanager seems to be flaky when connecting to WPA protected wireless.

I am still not sure why the above command works, maybe the card needs to be reset or something. Running some tests to determine exactly what makes it work...

---

### Post by Prometheum on 2008-02-16
I would guess (though this is really just a guess, and there's no way to confirm it without checking the windows drivers) that the windows drivers won't accept packets that aren't to its MAC address unless its in promiscuous mode (like drivers should) and that somehow ndiswrapper isn't picking up on it as well as it should. When my wireless was bad and I'd get the wlan0:avahi interface, it'd have a blatently wrong MAC, so this fix seems feasible.

---

