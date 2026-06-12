---
title: "No wireless after Upgrading from 9.10 to 10.04"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by user1001 on 2010-05-09
Hi.

I'm frustrated, it shouldn't be this hard.
When I had 9.10 i used to be able to click on the wireless icon on the bar and choose my wireless network to connect to..
now it's not like that :S
I right clicked on it this time and clicked on edit connection..

then I clicked on wireless then added the details and wep key

however I don't know how to connect it doesn't do anything :S

I have to wireless devices.

Internal PCI card: Wireless PCI 802.11b/g adapter **WN4201B**
USB Dongle: NETGEAR RangeMax(TM) Wireless USB 2.0 Adapter **WPN111**

I tried installing madwifi..I couldn't do it. 

Help ?

btw I also don't have sound :| 
My sound card is: Creative SB Audigy 2 ZS (WDM)

thanks .

---

### Post by kachkeis on 2010-05-09
Hi there,

I'm also new to Ubuntu and to his forum, but i succeeded in connecting this damn WPN111 from hell.

Ubuntu is awesome, I decided to keep it and to get rid of all the  Microsoft ****, this time for good. Ubuntu 10.04. finally made me accept  Linux as a valuable alternative. I feel like I have to apologize for  the years I didn't even know it existed...

@user1001: I suggest you use only one wireless device at a time while disabling one of them permanently, just to avoid hardware conflicts.

This post is about keeping the WPN111 enabled:

The link posted at the end of my message helped me quite well to get the installation done, as I said, I'm a bloody newbie with some MS-DOS experience, it reminded me of these times back in the nineties ;)

Result: Connection established and working with WPN on USB. :popcorn:

But my problem persisted with WPN111 even AFTER successful application of the linked guide. The thing was that, after a simple restart, there wasn't any way to establish a connection again (I tried a lot of things but everything was configured as necessary). Damn WPN111 wouldn't start correctly at boot...but the f****ing blue light kept flashing and flashing even when i shut the computer down until pulling the electrical plug ;)

THERE it was. I found out that by unplugging the power supply completely so that there isn't any electrical current in the PC, the WPN111 seems to "shut down" so that it's starting correctly at boot.

It works for me, you just can't do a "Restart" without unplugging,  because the WPN111 won't work at boot up.

So, to get rid of this Problem i'll get another stick. I also own one from LINKSYS and it works just fine since the first day of installation. Driver recognized and installed automatically.

So, f*** the Netgear people for not supplying ubuntu-linux-drivers. :guitar:

Here's the link:

[http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023)

Ciao,
kachkeis

---

### Post by kachkeis on 2010-05-09
Ah yes, here are the files I used
:P

---

### Post by user1001 on 2010-05-09
I think I installed ndiswrapper successfully from the tar.gz archive..

I also installed the driver from the file you gave me

i did ndisrapper -l

and I get a report which says

driver installed
and device exists or something

however though there is no blue light flashing

and ii can't connect to the network yet again..
I restarted and still no chance..
I am getting even more frustrated..

it should not be this hard.
not to mention I can't go on the internet on the ubuntu
I am constantly restarting the computer to login to xp then ubuntu and vice versa.

:(:(:( help !

---

### Post by user1001 on 2010-05-10
bump

---

### Post by user1001 on 2010-05-10
Bumppppp

---

### Post by user1001 on 2010-05-10
bump :\

---

### Post by emoguitarist06 on 2010-05-10
Sorry I'm no wireless pro
but did you upgrade to 10.04 or did you do a fresh install?
what kind of computer do you have?

---

### Post by user1001 on 2010-05-10
Well I did a fresh install from USB. But in grub there are other versions too ..
Wireless doesn't work with livecd boot too ..

---

### Post by Nxion on 2010-05-10
Ok lets look at the card for a second. OPen a terminal and do the following.

```
sudo lshw -C network
```

also do this:

```
iwconfig
```


Can you post the output of this? Thanks

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> Ok lets look at the card for a second. OPen a terminal and do the following.

```
sudo lshw -C network
```

also do this:

```
iwconfig
```


Can you post the output of this? Thanks

Here is the output..
> 
fenerlitk@fenerlitk-desktop:~$ sudo lshw -C network
[sudo] password for fenerlitk: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:8e:4b:3d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:e800(size=256) memory:bffff400-bffff4ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:bfffc000-bfffdfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:34:8a:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.55+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.1.63 link=yes multicast=yes wireless=IEEE 802.11g


First time I did iwconfig
> 
fenerlitk@fenerlitk-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The second time I did iwconfig... I got a different result.
> 
fenerlitk@fenerlitk-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Livebox-41F8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:CE:26:AB:18   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

fenerlitk@fenerlitk-desktop:~$ 


Now there is a few problems...
There are two usb ports in the front of my pc.. when I put the wireless usb device on the top one it doesn't work, however in the second one it seems to work..

now i established a connection to my network as you will see in the second iwconfig... (btw te first iwconfig was done when the usb was on top as well and the connection was also estabilished)

and when i try to go to google.. it is very slow and sometimes it says looking for sometime it says waiting...

i don't think this driver is able to use this device properly, and it keeps dropping the connection .

and also I'd like my accton card to work though now usb will do 

thanks in advance.

edit: i did iwconfig and your post says iv... is that okay ?

---

### Post by Nxion on 2010-05-10
> **user1001 said:**
> Here is the output..


First time I did iwconfig


The second time I did iwconfig... I got a different result.


Now there is a few problems...
There are two usb ports in the front of my pc.. when I put the wireless usb device on the top one it doesn't work, however in the second one it seems to work..

now i established a connection to my network as you will see in the second iwconfig... (btw te first iwconfig was done when the usb was on top as well and the connection was also estabilished)

and when i try to go to google.. it is very slow and sometimes it says looking for sometime it says waiting...

i don't think this driver is able to use this device properly, and it keeps dropping the connection .

and also I'd like my accton card to work though now usb will do 

thanks in advance.

edit: i did iwconfig and your post says iv... is that okay ?

Where is our laptop in relation to the Wireless router/access point?

---

### Post by Nxion on 2010-05-10
also check this out... This is a bit old but it might be what you need based on the card you have.

[http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")

So if I understand you have two network cards?? One internal and one usb? if so I really think you should take out one of the other. Rather take out the card you DONT want to use and we will work on getting the other working.


As for the really strange USB problem, maybe the USB port is bad? I cant say for sure. What is the brand/model of computer and its specs?

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> Where is our laptop in relation to the Wireless router/access point?

I think you meant where is my laptop in relation to the router..

it's quite close but the ethernet cable is very short :\

---

### Post by Nxion on 2010-05-10
> **user1001 said:**
> I think you meant where is my laptop in relation to the router..

it's quite close but the ethernet cable is very short :\

I should really spell and grammar check lol.

---

### Post by Nxion on 2010-05-10
> **user1001 said:**
> it's quite close but the ethernet cable is very short :\

Is the laptop connected via a network cable and wireless?

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> also check this out... This is a bit old but it might be what you need based on the card you have.

[http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")

So if I understand you have two network cards?? One internal and one usb? if so I really think you should take out one of the other. Rather take out the card you DONT want to use and we will work on getting the other working.


As for the really strange USB problem, maybe the USB port is bad? I cant say for sure. What is the brand/model of computer and its specs?

I already installed ndiswrapper..
yeah I would rather have the internal card to work and not the USB Device.
hmm.. maybe it is the port but I don't think so, anyway I'll check another port too..

But i really want to get the card running.

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> Is the laptop connected via a network cable and wireless?

nope it's not connected by a cable...
i go back and forth between ubuntu and xp, it's getting on my nerves lol :\

---

### Post by Nxion on 2010-05-10
Did you see my post number 13?

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> Did you see my post number 13?

Yep, replied to it (post number 17) :)

btw the usb does not work anymore on either of the ports... though it does work on xp. :S:S

hey check your number of beens before you reply :PP ^^ LOL :D

---

### Post by Nxion on 2010-05-10
So it can connect but it is really slow? What kind of router is it? what is the model?

---

### Post by user1001 on 2010-05-10
> **Nxion said:**
> So it can connect but it is really slow? What kind of router is it? what is the model?

well it can't connect at all now there is no wireless option, 
and for the router, it's just an orange livebox..

btw I used to be able to connect with no problems with my internal card with ubuntu 9.10 and previous ones :\

---

### Post by user1001 on 2010-05-11
Bump

---

### Post by user1001 on 2010-05-11
Bump.

---

### Post by Nxion on 2010-05-11
> **user1001 said:**
> well it can't connect at all now there is no wireless option, 
and for the router, it's just an orange livebox..

btw I used to be able to connect with no problems with my internal card with ubuntu 9.10 and previous ones :\

What is a Orange livebox?

---

### Post by user1001 on 2010-05-12
> **Nxion said:**
> What is a Orange livebox?

it's a modem and a wireles router.., well I don't think that is the problem since I can connect to it from XP..


[[IMG]http://img534.imageshack.us/img534/1461/screenshotihu.png[/IMG]](http://img534.imageshack.us/i/screenshotihu.png/)


it's interesting that the system can find the network card, but it can't use it :S

Btw I installed a new Ubuntu and formated the drive,
iwconfig now says:
> 
lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by Nxion on 2010-05-12
Im curious, have you tired 9.10 instead of 10.10. Im curious to see if it might might be a kernel problem.

---

### Post by user1001 on 2010-05-12
now I installed the ndiswrapper.. and I installed a driver from this thread..
now when I do iwconfig.. i get this:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


now I go the option to connect to my wireless router, I try to connect to it, it asks for my key.. I type it in, I wait and it asks for the key again after a while, I'm sure I typed it in properly and I did pairing too. :\

---

### Post by user1001 on 2010-05-12
> **Nxion said:**
> Im curious, have you tired 9.10 instead of 10.10. Im curious to see if it might might be a kernel problem.

9.10 of what? ubuntu? yes, in ubuntu 9.10 I didn't need the wpn111 device, my internal wireless card (accton) worked out of the box. :S

---

### Post by Nxion on 2010-05-12
So which adapter do you have connected right now? THe internal or USB one?

---

### Post by Nxion on 2010-05-12
> **user1001 said:**
> 9.10 of what? ubuntu? yes, in ubuntu 9.10 I didn't need the wpn111 device, my internal wireless card (accton) worked out of the box. :S

This sounds to me like it is a issues with the drivers and the kernel in ubuntu 10.04. 

Sorry I ment to say have you tried ubuntu 10.04 not 10.10.

Ok so I would go fill out a bug report on launchad about what is going on.

---

### Post by Nxion on 2010-05-12
> **user1001 said:**
> Yep, replied to it (post number 17) :)

btw the usb does not work anymore on either of the ports... though it does work on xp. :S:S

hey check your number of beens before you reply :PP ^^ LOL :D

That was funny :)

---

### Post by user1001 on 2010-05-12
> **Nxion said:**
> So which adapter do you have connected right now? THe internal or USB one?

USB... however the internal card is inside too.. as you can see in the picture I have uploaded above, sys info finds the card and it knows the name :S

I'd love to be able to use the card ..

---

### Post by Nxion on 2010-05-12
OK. unplug the usb for right now. and try to connect to your wireless network.

If it still does not work can you change the encryption of the wireless to WPA instead of WEP. I want to see if this works better with a different form of encryption.

---

### Post by user1001 on 2010-05-12
well.. when I unplug the usb, I don't have any wireless options.. :S
and for the wep key, I used to be able to connect to this with the previous ubuntu no problems :\


> **Nxion said:**
> OK. unplug the usb for right now. and try to connect to your wireless network.

If it still does not work can you change the encryption of the wireless to WPA instead of WEP. I want to see if this works better with a different form of encryption.



You're a pro :P, the key was on option "wep or wpa", I changed it to "WPA Only".
well what happened is I'm now being able to get a kind of stable connection, the network doesn't drop...
but I have seen a major speed drop 

This is the speed I get with wireless (WPA Enabled)
[[IMG]http://www.speedtest.net/result/813267921.png[/IMG]](http://www.speedtest.net)

This is the speed I get with ethernet:
[[IMG]http://www.speedtest.net/result/813273848.png[/IMG]](http://www.speedtest.net)


Also I'd rather get my Accton Card working...

---

### Post by user1001 on 2010-05-14
Bump the usb is not working properly yet again..
anyone know how i can get my accton internal wireless card working
and explain to me why wireless is slow?

thanks

---

### Post by itsme2day on 2010-05-14
bump / following thread to find out about speed issues.

---

### Post by user1001 on 2010-05-14
> **itsme2day said:**
> bump / following thread to find out about speed issues.

you have the same problem ?

and of course bump :P

---

### Post by user1001 on 2010-05-15
Bump.

---

### Post by dez93_2000 on 2010-05-19
Painful stuff. I've got much the same problem. When I plug my usb wireless adapter in, nothing happens. Nothing at all. No lights, not recognised, not listed using the sudo process mentioned which should give ATTACHED / etc etc.

So i looked to do the ndiswrapper process based on the help file, but that needs one to install something else (n something) which obviously i can't do. Catch 22.

The other suggestion was to boot to windows and ensure that the adapter's working and switched on there. But something's happened to grub which means although i can select my windows installs, it doesn't boot to either of them (i have 2, on 2 drives). It just flashes an underscore in the top left of the screen. I know that the installs haven't changed (unless ubuntu's changed them which is unlikely) and i've accessed the drives fine from ubuntu.

I guess i'll drag my tower downstairs to the router and plug it in, try the ndiswrapper process by downloading whatever's required, then try to fix the grub problem, by looking around elsewhere.

I *really* want to like ubuntu, but these crucial failings are making it so hard to do so...

---

### Post by dez93_2000 on 2010-05-20
yaay. dragging the PC downstairs & doing the ndiswrapper thing worked a treat. Still no dual boot though, but that's for elsewhere

---

### Post by dduehning on 2010-05-20
I had this same issue with my HP laptop and a broadcom wireless adapter - My solution - I connected directly to the router with a network cable, and then after verifying I was connected to the internet, I clicked System-Administration-Hardware Drivers and let it scan for any that I would need.  For me I needed to enable the ATI proprietary drivers, and after doing that and a reboot, I then had the wireless adapter and was able to connect.  Something worth trying... It might also be worth your time to check for any updates while you're wired.

---

### Post by DOSn3rd on 2010-11-21
Just thought i would confirm this guide as working for Ubuntu 10.10 too. Tried it just now and it worked flawlessly :) Stupid netgear only had the driver as an exe *sigh*

---

