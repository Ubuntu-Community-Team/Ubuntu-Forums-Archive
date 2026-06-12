---
title: "Atheros AR5212 802.11 abg card on Vaio TR3/SP weak performance"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by bence8810 on 2007-05-18
Hi,

I have just tried Ubuntu, and I really like it. I used Debian before on other laptops, but Ubuntu just rocks compare to whatever I tried.

The Laptop in question is a Sony Vaio TR3/SP, and all function works fine, except the builtin camera, but I wasnt hoping for that anyways.

The only problem however I am facing is the Wireless. This laptop has the supreme Atheros chipset, the Japenese version which functions in all 3 forms, etc. Its an Atheros AR5212.

This is what LSPCI shows:

```

02:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

As soon as I installed Ubuntu, on the first boot, it displayed a message from Restricted Drivers Manager:

```
In order to function properly, Ubuntu may be using driver software that cannot be supported. Atheros Hardware access layer (HAL)
```


I safely ignored the message, but I noticed, although my wireless works, the performance is really poor. I am 10 meters away from the Access Point, and getting 30% signal. If I boot into Windows, its 95%, and that is a significant difference. It looses the signal often, and after resume, it wont find it unless I do an ifconfig ath0 down and then up.

As far as I can see, it uses an ath_pci driver, and this is what I see in the loaded modules' list:

```
wlan_scan_sta          14976  1 
psmouse                38920  0 
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath_rate_sample        14080  1 
wlan                  204484  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
soundcore               8672  1 snd
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ath_hal               192592  3 ath_pci,ath_rate_sample

```

Is there anything I can do to enhance this chipset in Linux, or I just need to live with it? Its really hard, as I have to be really close to the AP in order to be able to work.

Any help is greatly appreciated,

Thanks

Ben

---

### Post by stchman on 2007-05-18
> **bence8810 said:**
> Hi,

I have just tried Ubuntu, and I really like it. I used Debian before on other laptops, but Ubuntu just rocks compare to whatever I tried.

The Laptop in question is a Sony Vaio TR3/SP, and all function works fine, except the builtin camera, but I wasnt hoping for that anyways.

The only problem however I am facing is the Wireless. This laptop has the supreme Atheros chipset, the Japenese version which functions in all 3 forms, etc. Its an Atheros AR5212.

This is what LSPCI shows:

```

02:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

As soon as I installed Ubuntu, on the first boot, it displayed a message from Restricted Drivers Manager:

```
In order to function properly, Ubuntu may be using driver software that cannot be supported. Atheros Hardware access layer (HAL)
```


I safely ignored the message, but I noticed, although my wireless works, the performance is really poor. I am 10 meters away from the Access Point, and getting 30% signal. If I boot into Windows, its 95%, and that is a significant difference. It looses the signal often, and after resume, it wont find it unless I do an ifconfig ath0 down and then up.

As far as I can see, it uses an ath_pci driver, and this is what I see in the loaded modules' list:

```
wlan_scan_sta          14976  1 
psmouse                38920  0 
snd                    54020  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath_rate_sample        14080  1 
wlan                  204484  5 ath_pci,wlan_wep,wlan_scan_sta,ath_rate_sample
soundcore               8672  1 snd
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ath_hal               192592  3 ath_pci,ath_rate_sample

```

Is there anything I can do to enhance this chipset in Linux, or I just need to live with it? Its really hard, as I have to be really close to the AP in order to be able to work.

Any help is greatly appreciated,

Thanks

Ben

I would not take the % thing that seriously.  My laptop reports that the signal strength is around 45% and I get great performance.

Are you getting signal drops?  If not don't worry about it.

---

### Post by bence8810 on 2007-05-19
Hi

No, the signal once I have it is okay, but the performance is really bad in terms of even hooking to the network. Its a WEP secured WiFi router with MAC address filtering and Shared key. It works, then I will shut down, start the next morning, and it wont find the network. It sees the percentage, but it says Unassociated. Then I do an ifconfig ath0 down and ifconfig ath0 up, and it will find it then, or sometimes it wont find it at all.

I have another laptop with PRO2200 card inside, with Ubuntu, and it works like a charm.

That is why I think there is something wrong with the driver.

Also, this morning I experimented, I went right close to the router, about 10 cm from it, and the signal strenght went up to 60% :) but it was still unassociated. I dont know what is with this card, or driver, but it is acting up.

Under windows, of course (shame) it works like a dream.

Thanks

Ben

---

### Post by bence8810 on 2007-05-20
Hi

I checked, and it seems I have the latest madwifi installed by default, the 9.3.0 

```
[   32.092000] ath_hal: module license 'Proprietary' taints kernel.
[   32.096000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   32.376000] ath_pci: 0.9.4.5 (0.9.3)
[   32.740000] ath_rate_sample: 1.2 (0.9.3)

```

So I guess re-compiling madwifi wont work.

Can someone explain to me what exactly is this Restricted Drivers Manager, and all of that? Is there any way to disable that? I have another laptop with a Sony Vaio cardbus card, and that uses also madwifi, and works like a charm on the same router.

Another thing I have noticed was that when I took the laptop to work, there we use a different router, with WEP - shared key - 64bit encryption. That works like a charm, I can resume, and the network will come back, etc.

At home, where I have the problem, I have 128bit encryption on WEP. I have two routers with two networks, to one I am unable to connect, and to the one I am currently connected I keep having problems.

When resuming, I have to re-associate to the wifi network, then do an ifconfig ath0 down and up, a few times until it comes back up.

This does not relate to the distance as i have tried it from right besides the router, and the outcome was the same.

Any pointers would be appreciated,

Thanks

Ben

---

### Post by bence8810 on 2007-05-20
Hi

The problem was with the SSID not being broadcasted. I am puzzled why this is a problem, but when I enabled the broadcasting (which I dont like), it started working, coming out of a resume as well, etc.

Here is my new thread about the broadcast problem

[http://ubuntuforums.org/showthread.php?p=2688116#post2688116](http://ubuntuforums.org/showthread.php?p=2688116#post2688116)

Thanks

Ben

---

