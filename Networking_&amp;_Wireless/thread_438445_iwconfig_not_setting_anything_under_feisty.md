---
title: "iwconfig not setting anything under feisty"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by neocookie on 2007-05-09
I'm having a nightmare with wireless in feisty at the minute. I managed to get wireless working for a short while yesterday, but today it seems as though iwconfig doesn't want to set anything.

I've tried:```
# sudo iwconfig wlan0 essid "mywireless" mode Managed
```and variations of the same, but with no luck - iwconfig just reports:```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I've tried it with wicd and network-manager, and without. i've reinstalled 5 times now, and even tried downgrading to edgy, with no luck there. Everything works fine in windows, but I'm more productive under linux.

I'm using the marvell/libertas drivers under ndiswrapper 1.43, and I've blacklisted everything I can find including the broken drivers.

Can anyone tell me whats going on? I've had a lovely 6 months working on edgy with wireless enabled, but recently wireless has gone up the wall on ubuntu. I need to get back on wireless before I start loosing money (i'm a freelancer).

---

### Post by dante.regis on 2007-05-09
give wifi-radar a try. I have an acer laptop with broadcom wireless, and the only way my network worked was with wifi-radar.

apt-get install wifi-radar.

---

### Post by neocookie on 2007-05-10
I'll give that a try tonight.

Its mad, really. I've had 6 month's bliss using ubuntu: everything worked straight away. And now, something has changed, and wireless just doesn't want to work. Its a shame I can't just roll back to edgy - it seems whatever's been broken has been back-ported.

Its not as if wireless is completely dead - I can scan fine, I can see all my local networks, and I've even connected to a couple of the unsecured ones (briefly). I just can't connect for any reasonable length of time, or to any secured network.

---

### Post by anubhavrocks on 2007-05-10
what is the output of 
```
dmesg|grep -i ndis
```

---

### Post by Jouke74 on 2007-05-10
I had the same problem for the same chipset, see : [http://ubuntuforums.org/showthread.php?t=419727](http://ubuntuforums.org/showthread.php?t=419727) for probable solve.

:)

---

### Post by neocookie on 2007-05-10
Thanks Jouke74, but those instructions/drivers wouldn't connect and just locked my machine up after a reboot, forcing a re-install.

After some more toying about, it seems as though iwconfig won't set any details if the mode is *anything* other than "ad-hoc", for example:```
$ sudo iwconfig wlan0 mode ad-hoc essid "mywireless" channel 11 key s:123mypassword open
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"mywireless"  Nickname:"mywireles"
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
So the essid is being set (even though there is still no connection). However, doing things "properly":```
$ sudo iwconfig wlan0 mode managed essid "mywireless" channel 11 key s:123mypassword open
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"mywireles"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So, ndiswrapper is installing fine, the drivers install fine, its just iwconfig which doesn't want to play nice.

Any ideas on how I can fix this?

---

### Post by neocookie on 2007-05-10
> **anubhavrocks said:**
> what is the output of 
```
dmesg|grep -i ndis
```
```
$ dmesg|grep -i ndis
[   39.099931] ndiswrapper version 1.42 loaded (smp=yes)
[   39.197549] ndiswrapper: driver netmw125 (Marvell,12/30/2005,3.2.3.2) loaded
[   39.199896] ndiswrapper: using IRQ 20
[   39.468129] wlan0: ethernet device 00:15:af:00:ba:43 using NDIS driver: netmw125, version: 0x3020007, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
[   46.170201] usbcore: registered new interface driver ndiswrapper
```
And as I say... I can perform a scan fine, and see all my local networks. I just can't set the correct config with iwconfig.

---

### Post by Jouke74 on 2007-05-11
&^&^!, it was not supposed to make you reinstall Ubuntu, sorry for that. :(  Probably you are using a 32-bit version of Ubuntu?  I use 64bit and that's why your system was crashing on NDISwrapper when you use my drivers I wrote about: 32bit and 64bit don't mix. 

I'll post my iwconfig later. Can you do the steps after the installation of Ndiswrapper (from step 7 : uninstall network manager etc..) that is not supposed to give you severe system crashes.

---

### Post by Tarrasque on 2007-05-11
> **neocookie said:**
> I'll give that a try tonight.

Its mad, really. I've had 6 month's bliss using ubuntu: everything worked straight away. And now, something has changed, and wireless just doesn't want to work. Its a shame I can't just roll back to edgy - it seems whatever's been broken has been back-ported.

Its not as if wireless is completely dead - I can scan fine, I can see all my local networks, and I've even connected to a couple of the unsecured ones (briefly). I just can't connect for any reasonable length of time, or to any secured network.

I'm having that same sort of problems with Feisty.

I just bought a NETGEAR USB WG111v2 dongle because I read it was usable out of the box. In facts, it seems to be recognized as soon as you plug it in, and the applet on the top right of Gnome (I guess it's that "network-manager") scans a wireless network, and once I provide the WEP key it says I'm connected and I even get an IP.

Still, most of the time I cannot surf the net, and often even if i ping the router it says it's "unreachable". Sometimes, I don't know how, I have been able to surf for a bit but speed and connection stability were awful. Windows wifi networking works well from the same spot.

I never used Edgy so I can not tell you whether the dongle used to work or not.

This is a big issue for me, because the router and modem are in a different room, on a different floor in my house!!

And wired connection is, frankly, out of question. Without a working wireless I will have to revert to Windows...

---

### Post by gypsy_roadhog on 2007-05-11
I have experienced a very similar situation with a netgear WG311v3 card. After a lot of trying I realised that the software was setup correctly,  that iwconfig thought it was setting the essid but that this wasn't being put into effect on the card for some reason

After many hours of trying the only way I could clear this was to reinstall windows xp on a spare corner of the machine and use the windows tools to configure the card.

On rebooting to Ubuntu the card worked fine........ I don't like the solution very much but it worked.

---

### Post by Jouke74 on 2007-05-11
IWCONFIG:

[I]wlan0     IEEE 802.11g  ESSID:"WirelessJ"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:15:F2:0F:39:70   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:378   Missed beacon:0[/I]



sudo gedit /etc/network/interfaces

[I]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid WirelessJ
wireless-key 0(+rest of my hexidacimal key)

auto wlan0[/I]




Try edit the interfaces file in this way. This is only for WEP Hexademical. Not for WPA. WPA I cannot get to work (yet). Of course ESSID needs to be the name of your visible wireless network. The key needs to be the hexadecimal string that you get have entered as a password.

You have to disable the roaming under: System > administration > network >  click "wlan0" > properties > enable this connection.

---

### Post by neocookie on 2007-05-12
> **Jouke74 said:**
> Try edit the interfaces file in this way. This is only for WEP Hexademical. Not for WPA. WPA I cannot get to work (yet). Of course ESSID needs to be the name of your visible wireless network. The key needs to be the hexadecimal string that you get have entered as a password.

Checked the file - thats how its set already. As much as I hate to say it, I think I'm gonna have to go back to windows. Its been nearly a year since I switched fully over, and I must admit its been fun. But I've started to loose money since all the problems with the wireless card started up, and I can't afford to loose any more.

---

