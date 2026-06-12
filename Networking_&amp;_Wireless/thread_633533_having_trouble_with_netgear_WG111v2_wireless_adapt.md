---
title: "having trouble with netgear WG111v2 wireless adapter"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by mydearleo on 2007-12-06
Hi everyone, I am new to Ubuntu, just got the disk yesterday and installed Ubuntu last night.

I am having problem with my netgear WG111v2 USB adapter, let me explain my situation first.

I have set up a wireless network using MAC address, no WEP or WPA. After a fresh installation of Ubuntu 7.10, everything seems to be working fine. WG111v2 can detect wireless network arround it, but when I tried to connect, it would take 1 minute trying to connect, then stopped. I also tried it manually, however, it only 4 encryption options while I did not need any encryption at all.

I noticed there are several threads here talking about WG111v2, but the situations are all different to mine.

I will appreciate any hint or help from you guys. Thanks a lot.

---

### Post by slayer^_^ on 2007-12-07
i didn't have any troubles with that adapter with kubuntu gutsy, but however let me give you some hints:

1)try to understand if your device is a REAL or FAKE v2 (the fake v2 has got v1 hardware)... you'll be able to understand it looking at the mac address and on the [www.netgear.com](www.netgear.com) website (or googling a litl bit...). i can't exactly tell you which way right now...

2) emulate windows drivers with ndiswrapper, in my experience they do their job.

i wrote a howto here [http://ubuntuforums.org/showthread.php?t=632651](http://ubuntuforums.org/showthread.php?t=632651) , it's not your case but you can try using the "TROUBLE 1" section to install the driver you need.

REMEMBER : if you've got the fake v2 versione use the wg111 driver (subfolder ndis5), if you've got  the real v2 use the wg111v2 driver (subfolder win98 ).

REMEMBER 2 : that guide was written for xubuntu dapper, thus using the xfce notepad, in ubuntu i guess you should use "sudo gedit" or "gksudo gedit" instead of "sudo mousepad".

if you wanna answer me you can also reply directly on that post.

good luck wg111v2 brother !!!

---

### Post by mydearleo on 2007-12-07
Hi Slayer. Thanks for you quick reply, however, I have already read your thread but having problem inplement your first solution. When I tried to edit module and link mac to wan0, i got "access denied" error saying that I dont have privilege to edit them.

BTW, my wg111v2 is a real v2. I will keep on trying, if you have any other suggestions, I will be very appreciated.Thanks

---

### Post by slayer^_^ on 2007-12-08
what you've written sounds quite strange,,, let's try again the process

**link MAC to wlan0**

let's state first that on MY hardware it is recognized as wlan0, on yours it could be eth0, wlan1, l1, or whatever else... try to understand which way is it recognized and not to do misunderstanding with, for example, the ethernet card.

You can find the MAC address of the device written n the side. It should be something like 000FB5XXXXXX, you just need to place the colon after each 2 characters/numbers.

```
sudo mousepad /etc/iftab/
```

if you are in ubuntu 

```
sudo gedit /etc/iftab/
```

if you are in kubuntu

```
sudo kwrite /etc/iftab/
```

**don't forget _sudo_, it will give you all the administrative privileges you need**

_a text file will open, in which you'll have to add_

wlan0 mac 00:00:00:00:00:00

with YOUR mac address instead of this one containing only zeros...

again, if your device is recognized not as wlan0, the string to add in the text file will be different, for example the result could be:

wlan1 mac 01:2a:3b:4c:66:00

hope to have solved, let me know if you encounter more troubles by the way...

---

### Post by mydearleo on 2007-12-12
> **slayer^_^ said:**
> what you've written sounds quite strange,,, let's try again the process

**link MAC to wlan0**

let's state first that on MY hardware it is recognized as wlan0, on yours it could be eth0, wlan1, l1, or whatever else... try to understand which way is it recognized and not to do misunderstanding with, for example, the ethernet card.

You can find the MAC address of the device written n the side. It should be something like 000FB5XXXXXX, you just need to place the colon after each 2 characters/numbers.

```
sudo mousepad /etc/iftab/
```

if you are in ubuntu 

```
sudo gedit /etc/iftab/
```

if you are in kubuntu

```
sudo kwrite /etc/iftab/
```

**don't forget _sudo_, it will give you all the administrative privileges you need**

_a text file will open, in which you'll have to add_

wlan0 mac 00:00:00:00:00:00

with YOUR mac address instead of this one containing only zeros...

again, if your device is recognized not as wlan0, the string to add in the text file will be different, for example the result could be:

wlan1 mac 01:2a:3b:4c:66:00

hope to have solved, let me know if you encounter more troubles by the way...


Ubuntu 7.10 gusty automaticly recognised the wg111v2, with wlan0 and its mac address, and the device can detect network arround. however, it does not seems to like my network (no wep or wap, just mac address recognition), because when I tried to connect to other people's network, it will prompt me to enter password which I assume that it was working. 

I also followed your instrauctions, but it did not make any difference. I also noticed that in the 'networking' there is no TCP/IP under wlan0 (my eth0 has). I am not sure whether this is the problem or not.

---

### Post by slayer^_^ on 2007-12-13
i know that gutsy detects the WG111v2 device, but don't think gutsy does the job with it like it does with all the rest of the hardware, on gutsy (with gutsy native driver) WG111v2 works crappy, trust me...
 
I tried ndiswrapper to emulate the driver on gutsy and it works great, surely better...

trying ndiswrapper is the first thing i'd suggest you.

then, try to manually edit the interfaces file :

```
sudo gedit /etc/network/interfaces
```

and then configure your device settings (wlan0 right ?)

```

iface wlan0 inet dhcp
wireless-essid Yournetworkname (CASE SENSITIVE)
wireless-mode managed
wireless channel 11
auto wlan0 [CODE]

many prefer putting it like this:

[CODE]
auto wlan0
iface wlan0 inet dhcp
wireless-essid Yournetwork name (CASE SENSITIVE)
wireless-mode managed
wireless channel 11 [CODE]

try them both: 

remember that the network name is case sensitive and to put the right wireless channel.

you **won't[B] have to use your network software detector, it should automatically associate with your network. [B]if it doesn't** try restarting the network devices with this command

[CODE]sudo /etc/init.d/networking restart
```

many people told me they're able to connect only with this last code...

let me know if it works...

---

### Post by mydearleo on 2007-12-13
> **slayer^_^ said:**
> i know that gutsy detects the WG111v2 device, but don't think gutsy does the job with it like it does with all the rest of the hardware, on gutsy (with gutsy native driver) WG111v2 works crappy, trust me...
 
I tried ndiswrapper to emulate the driver on gutsy and it works great, surely better...

trying ndiswrapper is the first thing i'd suggest you.

then, try to manually edit the interfaces file :

```
sudo gedit /etc/network/interfaces
```

and then configure your device settings (wlan0 right ?)

```

iface wlan0 inet dhcp
wireless-essid Yournetworkname (CASE SENSITIVE)
wireless-mode managed
wireless channel 11
auto wlan0 [CODE]

many prefer putting it like this:

[CODE]
auto wlan0
iface wlan0 inet dhcp
wireless-essid Yournetwork name (CASE SENSITIVE)
wireless-mode managed
wireless channel 11 [CODE]

try them both: 

remember that the network name is case sensitive and to put the right wireless channel.

you **won't[B] have to use your network software detector, it should automatically associate with your network. [B]if it doesn't** try restarting the network devices with this command

[CODE]sudo /etc/init.d/networking restart
```

many people told me they're able to connect only with this last code...

let me know if it works...

Thanks for you continuous hints and help, I will spend some more over the weekend to try it. I hope it will get start working eventually.  It ls like trying window 3.1 in a DOS world, haha, it is pain and fun.

---

### Post by coolbrook on 2007-12-13
I got this working the other day.  I uninstalled the initial driver I was using, tried to blacklist rtl8187 and then I downloaded the 1.3 version of the driver, installed it with ndiswrapper and then did a manual configuration to connect to my router (disabling roaming.)  A link to the Windows 98 driver is in my signature.  Click on "Netgear WG111v2"

You just need to use the files that are created under the Win 98 folder that's extracted and then install the .inf with ndiswrapper.

---

### Post by vbn_newbie on 2007-12-17
hi,
i tried following the steps in this thread. ndiswrapper does say that i have the driver installed, and i tried blacklisting the things mentioned. but i still can't get it to work. primarily, the os doesn't seem to recognize the dongle plugged into the usb port. when i try lsusb i get

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Anyone have any idea why? 

Thanks!
VBN

---

### Post by slayer^_^ on 2007-12-18
gimme more info... your ()ubuntu version above all !!

..be sure you blacklisted well !!!

---

### Post by vbn_newbie on 2007-12-18
slayer, 
thanks for your reply. i have ubuntu 7.04.

---

### Post by slayer^_^ on 2008-01-05
have you tried to open the terminal and input this command?

```
sudo /etc/init.d/networking restart
```

tell me if it works... however i suggest upgrading to gutsy...

p.s. sorry if it took me a lotta time to answer, but i was abroad :D

---

### Post by Hightide on 2008-01-05
HI
I had a number of problems trying to get WG111 v2 adaptor to work to no avail. After I reinstalled Gutsy and without any effort using roaming mode, I now have a wireless WPA connection.

dont know if this helps!

---

### Post by HokeyFry on 2008-01-05
Honestly, I have had many many issues with the native wireless drivers. I suggest setting up your wireless via ndiswrapper. The link in my sig should point you in the right direction if you need help.

Also, the WG111v2 does work with ndiswrapper, I use it for my wii to connect to.

---

### Post by slayer^_^ on 2008-02-01
sure, with gutsy my WG111v2 worked too... but i suggest you to try the ndiswrapper way, it goes really really better !!!

i you can't make it work you can revert to the native driver by unblacklisting it at the end of the process!

let me remember you a few things:

1) use WIN98 drivers

2) install ndiswrapper-utils via synaptic (didn't experience downloading the package from ndiswrapper site, the repository one works and that's all)

3) blacklist the correct native driver
(that you can discover with the command
```
ndiswrapper -l
```
it will show you the alternate driver that you got to blacklist

4) add "ndiswrapper" to the file /etc/modules to be sure it will by loaded at boot-time

if you need feel free to contact me!

best wishes !!

---

