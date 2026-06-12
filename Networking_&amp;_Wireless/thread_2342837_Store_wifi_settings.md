---
title: "Store wifi settings"
date: 2016-11-10
forum: Networking &amp; Wireless
---

### Post by conor8 on 2016-11-10
I have a intel NUC running ubuntu server. At present it connects to a wifi network via a TP-Link TL-WR702N. This works but I want to neaten up the cabling and use a usb Wifi adapter.

Would it be possible to store the Wifi config files on a USB drive? I can then remove the drive edit the file and put it back in if the network conditions change?

I had also wondered if it was possible to have the Nuc broadcast a wifi network if it does not detect my wifi connection so I can connect and use SSH to reconnect it?

I've googled and googled but I'm struggling to explain the problem in a concise manner for searches.

Thankss

---

### Post by chili555 on 2016-11-10
Wow. Just wow. There is so much fun stuff here, I hardly know where to begin. Because I am a contrarian, let's start at the end:>  if it was possible to have the Nuc broadcast a wifi network if it does not detect my wifi connectionUh, no. If your wifi connection isn't detected at all, it isn't going to broadcast a wifi signal so you can connect to it by ssh or any other means.>  I want to neaten up the cabling and use a usb Wifi adapterI own and love a NUC, too, and that wouldn't be my first choice. Most all NUCs have provisions for an add-in (PCIe half-mini, in my case) wireless device. Many of them are Intel devices. Every Intel wireless device suitable for a NUC is fully supported in later kernels; say 4.2.0-xx or so. If I wanted wireless in my NUC, I'd look there.> Would it be possible to store the Wifi config files on a USB driveOf course. However, assuming that your settings are, as is usual in a server, set up in /etc/network/interfaces, you can simply jot them down by hand quickly and easily. 

Tell us more; what settings did you set up that you want to save?

Start at about 4:00 here: [https://www.youtube.com/watch?v=zIzCXtZfjuA](https://www.youtube.com/watch?v=zIzCXtZfjuA)

---

### Post by conor8 on 2016-11-10
Thanks for response, I don't know why I didn't think of an internal card. I have a USB one sat doing nothing and that's what got me thinking initially.

> Of course. However, assuming that your settings are, as is usual in a server, set up in /etc/network/interfaces, you can simply jot them down by hand quickly and easily. 

Tell us more; what settings did you set up that you want to save?

I'm hoping to just have the SSID and password saved, then I can update it on my laptop and plug it in before booting.
The reasoning for wanting to quickly change it, is that I plan to move and don't want to take a keyboard with me and hook it up to a TV or monitor to set it up.
I am moving my files to a portable USB3 Drive (from a desktop one at present) and was hoping I could have something that with 1 plug could have all my plex media library available and cast to a chrome cast. 

I'm guessing that to do the usb drive idea I would need to create symlinks to the /etc/network/interfaces.

> Uh, no. If your wifi connection isn't detected at all, it isn't going to broadcast a wifi signal so you can connect to it by ssh or any other means.
This idea came from the idea of a router. If I plug it in in an unfamiliar place without wifi, I could wait a minute or so and then connect, set it up and it would be good to go, with just my laptop (or phone)

---

### Post by chili555 on 2016-11-10
> I'm hoping to just have the SSID and password saved, then I can update it on my laptop and plug it in before booting.Ahhh! My favorite kind of post; the ones where I get previously unknown details and challenges with every post.

So your objective now is not to transition the NUC to USB wireless, but to enable the USB wireless on your laptop and boot it up and have it connect? Are you moving with your wireless access point/router? If so, what do you need aside from the SSID (the name of the network) and the WPA password. I'd suggest that you get the USB wireless going and save the details in Network Manager.

> I am moving my files to a portable USB3 Drive (from a desktop one at present) and was hoping I could have something that with 1 plug could have all my plex media library available and cast to a chrome cast. I am not familiar with, nor is this forum about Chromecast, however, if it all works perfectly well here, why wouldn't it wherever you are moving?

Perhaps, or likely, there is something I still don't understand. Please help me.

---

### Post by conor8 on 2016-11-12
I haven't explained my set up very well. Or the changes I hope to make.

At present I have a Nuc (headless, running ubuntu server), with an external drive for media and connect via a WR702N to my home wifi network. It runs Plex media server to give me TV shows and movies.

This means I have 2 electrical plugs, and the WR702N and all their wires hanging around the back.

As I'll be moving and want to take the Nuc (and its media), I want keep cluttering cables and not require a usb keyboard etc for set up.

My hope was to 
a. Have the Nuc use a usb wifi dongle [COLOR=#ff0000]*Remove the clutter of the WR702N*[/COLOR]
b. Be able to connect it to a wifi network without need of a keyboard and monitor, cables or accessories. *[COLOR=#ff0000]I don't want to take any extra gear. Just my laptop, Nuc and Portable USB Drive[/COLOR]*
End Goal - Plug in electricity, tuck it away and not have to worry about spaghetti junction.

> So your objective now is not to transition the NUC to USB wireless, but to enable the USB wireless on your laptop and boot it up and have it connect?
The Transition to USB wireless is purely for neatness. I don't want extra cables.
The setting it up is for the Nuc to connect to an existing wifi network (i.e friends house).

> Are you moving with your wireless access point/router?
No, I will most likely need to connect to an already established wifi network when I arrive. I also won't be in a position to control the router.

>  I'd suggest that you get the USB wireless going and save the details in Network Manager.
I don't think I can use network manager as its Headless Ubuntu server, there is no GUI. That was my reasoning for having the config file on an external pen drive (tiny one, for neatness). I can then edit the text file on my laptop. Plug it in a boot. It would then connect to the new wifi network, without having to set it all up with a TV and keyboard etc.

Thanks for coming back to me, I hope I made my current setup and objectives a bit clearer.

---

### Post by chili555 on 2016-11-12
May I assume that the NUCs network configuration is done in /etc/network/interfaces as is usual for a server of any kind? Let's check:```
cat /etc/network/interfaces
```If so, I suggest that you simply edit the file to provide for the wireless. I assume you are using ethernet now, attached to the WR702N. Detach it and with a keyboard and display at home before the visit to the friend, change the file to comment out all the ethernet lines, something like:```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp
```Now plug in the wireless USB and watch the message log to see that it is recognized and an interface is created; something like:```

[22570.308995] usb 3-1: Product: USB2.0 WLAN
[22570.308996] usb 3-1: Manufacturer: ATHEROS
[22570.308997] usb 3-1: SerialNumber: 12345
[22571.353180] usb 3-1: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
[22571.353298] usbcore: registered new interface driver ath9k_htc
[22571.640672] usb 3-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[22571.892490] ath9k_htc 3-1:1.0: ath9k_htc: HTC initialized with 33 credits
[22572.157850] ath9k_htc 3-1:1.0: ath9k_htc: FW Version: 1.4
[22572.157852] ath9k_htc 3-1:1.0: FW RMW support: On
[22572.157853] ath: EEPROM regdomain: 0x809c
[22572.157854] ath: EEPROM indicates we should expect a country code
[22572.157854] ath: doing EEPROM country->regdmn map search
[22572.157855] ath: country maps to regdmn code: 0x52
[22572.157855] ath: Country alpha2 being used: CN
[22572.157856] ath: Regpair used: 0x52
[22572.164032] ieee80211 phy1: Atheros AR9271 Rev:1
[22572.167022] ath9k_htc 3-1:1.0 [COLOR="#FF0000"]wlx30b5c2120f20[/COLOR]: renamed from wlan0

```Note the interface name, in this case wlx30b5c2120f20, and set it up in /etc/network/interfaces:```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlx30b5c2120f20
iface wlx30b5c2120f20 inet dhcp
wpa-ssid <friends_wireless_network>
wpa-psk <friends_password>

```Now carry the NUC to the friend's home, turn it on and connect. In order for this to work perfectly, every detail above must be exact. In other words, if the name of the friend's network is ColdBeer and you input the name Coldbeer, it will never connect and you will need to get a keyboard and display to correct it. As I often say, proofread twice!

---

### Post by conor8 on 2016-11-12
Perfect, Thanks for the Info, and showing an example. I always find it much easier to understand when I can see a working example.

I'm guessing if I put a usb pen drive in and set up fstab correctly, I can create a symbolic link:
ln -s /media/USBPEN/interface /etc/network/interfaces

Then once I get there I can edit and plug in. I won't know wifi settings until I arrive

Thanks again

---

