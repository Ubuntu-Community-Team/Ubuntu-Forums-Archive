---
title: "USB connection works, but Ethernet does not."
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by SilverDragon on 2008-01-20
Okay to start off, I recently built a new computer with an Asus P5K motherboard.

On my old computer which had Ubuntu on it before it died, this Toshiba PCX2600 modem connected through an ethernet connection and it worked fine.  I believe there was an Asus A7V8X board in that computer, but I am not entirely positive.

The reason I built this new computer is because my old computer was having other hardware problems (CPU failures and the screen going black) which occurred under Windows and Ubuntu and eventually died. My uncle is having a look at it now.

With the new computer, ethernet does not connect at all, but the usb connection works fine. The only problem is its still a little slow when compared to an ethernet connection. In addition, when I am downloading any relatively large file through a torrent, the whole internet becomes slow, which was not a problem with the ethernet connection on my old computer with the same modem. This hinders my internet capabilities because I cannot download these files and surf the internet with Firefox or even use pidgin at a reasonable speed.

I thought it was a safe purchase to buy a motherboard of the same brand for my new ubuntu computer, because I had been using Ubuntu with my old computer on and off for about 9 months and had completely switched for about 2 months :-)

This person has a very similar problem to mine, and I tried what they suggested but with no success:

[http://ubuntuforums.org/showthread.php?t=401709&page=3](http://ubuntuforums.org/showthread.php?t=401709&page=3)

Any feedback or more questions about how my computer is set up to help solve this problem would be appreciated :-)

---

### Post by kolopinki on 2008-01-20
for Asus P5K 

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5K](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5K)
surprisingly there is linux driver :)   for LAN
but atl1 driver is allready in new kernel
which ubuntu version are you using?

here the drivers are newer from those directly from asus
[http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)
[http://www.hogchain.net/attansic/attansic.html](http://www.hogchain.net/attansic/attansic.html)
(sometimes the older version is better,that depends on kernel version)

---

### Post by SilverDragon on 2008-01-20
Thanks for your response.

I'm using Ubuntu 7.10. 

Knowing that do you recommend me downloading one of those drivers over another?

---

### Post by kolopinki on 2008-01-20
No ,network card should be working   out-of-the box with 7.10.
try 
 ```
  sudo modinfo atl1
   sudo lsmod | grep atl 
```
to see is the driver loaded

---

### Post by SilverDragon on 2008-01-20
This is what came up when I typed those commands in the terminal. 

huy@ubuntu-desktop-huy:~$ sudo modinfo atl1
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/net/atl1/atl1.ko
version:        2.0.7
license:        GPL
description:    Attansic 1000M Ethernet Network Driver
author:         Attansic Corporation <xiong_huang@attansic.com>, Chris Snook <csnook@redhat.com>, Jay Cliburn <jcliburn@gmail.com>
srcversion:     72817DF5514C46E3458C9C3
alias:          pci:v00001969d00001048sv*sd*bc*sc*i*
depends:        mii
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           int_mod_timer:Interrupt moderator timer (array of int)
parm:           flash_vendor:SPI flash vendor (array of int)
huy@ubuntu-desktop-huy:~$ sudo lsmod | grep atl
atl1                   36108  0 
mii                     6528  2 atl1,usbnet

It seems like the driver is loaded?

This is a silly question, but how do you put stuff in "code" like you did with the commands?

---

### Post by kolopinki on 2008-01-20
The # near the 'quote' icon when full posting (not quick post) i think
or by typing  [ code ] your text [ / code ]  without spaces between brackets

the driver is loaded
try 
 ```
 ifconfig -a 
```
there shoud be reference eth0  and UP or DOWN for interface ,somwhere 

dunnno for thoshiba is it using  dhcp or something else
there are known problems conecting to cable providers when
switching devices (for instance from laptop to desktop network card ,etc)

---

### Post by SilverDragon on 2008-01-21
Here's what comes up in the terminal:

```
 
huy@ubuntu-desktop-huy:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:0D:32:C5:4B  
          inet addr:76.24.104.110  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::208:dff:fe32:c54b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32978 errors:41 dropped:0 overruns:0 frame:41
          TX packets:8815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7992300 (7.6 MB)  TX bytes:1996673 (1.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:1D:60:67:26:F1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe67:26f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:153734 (150.1 KB)  TX bytes:5613 (5.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I'm not sure what a reference to eth0 and UP or DOWN for interface would do though. Would it tell  me if I needed a static i.p. or to just use DHCP? Or some other information you could use?

---

### Post by kolopinki on 2008-01-21
i beleive this information is qute suffitiant for further diagnostics ;)

eth0 is actually toshiba running via usb cable  (00:08:0D)
it has ip adress suplied by your ISP provider inet addr:76.24.xxx.yyy
(note: when posting public ip change last two digits for security reasons)

eth1 is  local network card, asus on the motherboard ( 00:1D:60)
it look's like eth1 has static ip 192.168.0.100 (this is ip range for local networks not neeed for changing xxx.yyy when posting, at least i think so)
[first unplug ethernet cable if it is conected at this moment]
this should be set to dhcp . in upper right corner on desktop there is like systray button 'network'
when clicked change info for eth1  from    '- roaming' to 'dhcp' and afterwards
make sure there is checkbox instead of '-'

then wait 1 min or two and unplug usb cable 
and you may need to shutdown modem compleetly since cable ISP assigns dhcp adreses
acording to your networc card mac adress (00:1D:60:67:26:F1) or even reboot modem
(this is case in my country dont know is this also for other countries)
then plug in ethernet cable and after that turn the modem on,after 5 or 10 mins (for not to damage hw with frequent power cycle swithing)

*and should check is the mac  addres same in vind driver,this leads to probl. after reboot sometimes

---

### Post by SilverDragon on 2008-01-22
I followed your procedure in this manner.

1. Since the ethernet cable was already unplugged I set eth1 from "-roaming" to "dhcp" and put the check mark there.
2. I waited a minute, then unplugged the USB cable.
3. I shut down the modem and plugged in the ethernet cable.
4. 5 minutes later I plugged in the power cable.

After I followed that procedure, I still could not connect to the internet.

Some things I noticed were when the usb cable was in, the Cable, PC and Power areas on the modem were lit up and the data area was blinking as it should be.

On the other hand, when the ethernet cable was in, the Cable and Power were lit up, but the PC and Data area had no light.

In addition, when I plugged in the ethernet cable to the computer, the light is yellow on the back of the computer. I'm not sure, but I think that light is supposed to be green.

> *and should check is the mac addres same in vind driver,this leads to probl. after reboot sometimes

I am not really sure what you mean by this.

---

### Post by kolopinki on 2008-01-23
looks like there is no carrier (PC led on modem) modem is for 10/100 
in attacment is orange led's meaning for computer, either  'linked' or set to 100Mbit/sec

check the cable,by trying another cable for direct connection ( not the crossover cable)
ethernet cable should be at least 3 or 4 meters (about 10 feet) long for maximum compatibility
there are cases when shorter cables(~1.5 meters) work on one motherboard and not woking on another
ask for gigabit cable i guess?,or maybbe beter ordinary 10/100? not sure about that

could be also the network card speed ( 10/100/1000)
there is a way to set network card on motherboard on 100 Mbit/sec with   **ethtool** command
but i dont know exact syntax for that :(
[http://linux.die.net/man/8/ethtool](http://linux.die.net/man/8/ethtool)
it could be   ```
sudo ethtool -s ethX speed 100
```
ethX is either eth0 or eth1,needs to be seen with **ifconfig -a**
picos when usb is unpluged the number of eth interfaces  will change

---

### Post by SilverDragon on 2008-01-24
I have two cables, one which is about 10 feet and one which is shorter at about only 1.5 meters. I'm not sure if their "crossover cables" or "gigabit cables" or "10/100" cables though.

I tried using both cables and setting the the network card speed using the ```
sudo ethtool -s ethX speed 100
```

The same response came in the terminal with both cables. ```
Cannot get current device settings: No such device
  not setting speedd
```

Then after looking through the link you provided I tried ```
sudo ethtool -t test offline
``` and ```
sudo ethtool -t online
```

The following response came up in the terminal ```
Cannot get driver information: No such device

```

The fact the computer does not seem to detect the device even though the LAN port LED is orange is strange.

Actually I just realized based on the attachment in your post with a picture of the LAN port LED indications, that only one of the lights is lit up. Earlier when I was talking about a green and blinking light on my old XP computer that was normal considering their was data connectivity.

On the other hand, with my current computer with only one orange light lit up that would just indicate that it is either connected or just showing the speed, right?

In that case, wouldn't the one orange light indicate that it is connected, because how could it indicate the speed without being connected?

After looking at the attachment you provided and the LAN port LED, it only does show it's connected.

---

