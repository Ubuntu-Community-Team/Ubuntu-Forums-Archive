---
title: "Intel Pro 2200BG only reaching 28%? No network/interfaces?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Beacon11 on 2008-04-30
Hello all. I recently acquired an old Dell 600m with a bad hard drive from a friend who didn't know what to do with it. So like any good big brother I of course replaced the hard drive and put Kubuntu on it, so I can g ive it to my 11-year-old programming brother.
I installed 7.10, but then immediately went through the upgrade process to Hardy (8.04). I had the ethernet cable plugged in at this point and can't say whether wireless was working or not-- I didn't test it. Regardless... it isn't working now.

KNetworkManager shows the correct wireless networks (open, WEP, and WPA networks) and when I attempt to connect to any of them, no matter what protection (or lack thereof), the connection bar reached 28% immediately and stops there. About a minute later, I inevitably get the "Cannot connect to network" message. For your reference, I will include the following:

```

krf@kids:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

krf@kids:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:10:bf:33
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.127 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:97:5e:bc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

```

An interesting note... my network/interfaces is basically empty, I'm not sure what to make of that:

```

auto lo
iface lo inet loopback

```

I searched around a lot for helpful information, but I couldn't find anything that worked! I'm really quite stumped as to why my network/interfaces is empty. I mean... I can't even disable my network! I remember reading something about that meaning my network settings were on 'roam'... but it didn't make much sense to me. I would appreciate any help with this, and will provide any other necessary information. Thank you!

---

### Post by Paresh on 2008-04-30
I get the same issue, stuck at 28%.

knetworkmanager can see my wireless and others in the area.  I have been using ubuntu (7.04 and 7.10) with no problems on my Toshiba Tecra A9.

Today I decided to install kububtu 8.04 as a fresh install and it all went well until I tried to wireless connect.  I then tried manually connecting, but had the same result

---

### Post by Beacon11 on 2008-04-30
Huh... I wonder what the 28% signifies? If I remember correctly... the text that corresponds is "configuring device"? So... there's definitely a driver issue. Well shoot! Hardy really does have wireless issues huh? I was thinking about going the ndiswrapper route, but from what I read, it looked like it should be working right out of the front gates.

Paresh, can you run the commands I did and post your output? Let's see what we have in common. Is your network/interfaces basically empty as well? Maybe we can figure out what's going on here.

---

### Post by chili555 on 2008-04-30
You seem to have a NetworkManager issue. Check here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themAs long as you have your wired connection attached and have a good, working IP address, which you do, NetworkManager will balk at giving you another by wireless. Why would you need two?```
ip=192.168.1.127 latency=32 link=yes
```Please reboot without the ethernet cable attached and try again.

---

### Post by Beacon11 on 2008-04-30
Huh... Thanks Chili. That was a simple fix, it worked. Well, part way. It took a little more tweaking to get to connect to WPA, but eventually it all worked. What's interesting is that I agree, it makes no sense to connect via wireless when you're wired, so I didn't try. Every time I tried to connect to a wireless network, the ethernet cable was not plugged in. However, as soon as I rebooted without the ethernet plugged in, it worked whether the ethernet was plugged in or not, as it should have in the first place. I'm curious what happens differently when you boot without ethernet? That seemed to fix everything, as if it wrote some file that wasn't there before.

---

### Post by chili555 on 2008-05-01
NetworkManager is supposed to do this stuff automagically and, more or less instantly; for some, it just works, for others, it just won't. Why, I don't know.

My main laptop never leaves home, so I have removed NM and added my details to */etc/network/interfaces.*

NM is installed by default and I think a lot of us have machines with wireless cards because it's a pain to string CAT5 all around the house or rented/leased apartment, not because we are going down to the coffee shop to surf. When I think of those miserable folks struggling with a twitchy NM, I shudder.

End rant.

---

### Post by Paresh on 2008-05-02
I tried the WifiDocs page, up to the Automatic Keyring (but not done that bit yet)

I am still having problems.

Ubuntu 7.10 worked fine with the wireless at home and wired at work so I didn't expect any problems with updating to Kubuntu 8.04.

I have WPA security on my wireless network, but disabling this didn't make any difference

For the record, my settings are:
```

paresh@paresh-laptop:~$ iwconfig
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

```
```

paresh@paresh-laptop:~$ sudo lshw -C network
[sudo] password for paresh:
  *-network
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:15:b7:e5:01:ec
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:5e:7b:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```
and /etc/network/interfaces is
```

auto lo
iface lo inet loopback

```

Any further help would be greatly appreciated.  I need the laptop to work both wirelessly and wired (as it did in 7.10)

---

### Post by chili555 on 2008-05-02
Paresh-

I wonder why you replied here. Are you getting to 28% and no further? Do you have a IPW2200?

I suggest you search here for iwl3945 and look for the dozens of posts that suggest installing *linux-backports-modules-hardy-generic.* Did that solve your problem? If not, start a new or reply to a more appropriate existing thread.

It's not very clear to me what your problem actually is.

---

### Post by Beacon11 on 2008-05-02
Actually Chili, if you scroll up a bit, you'll see that Paresh posted right after me, saying he was having the same issue: stuck at 28% and no further. I asked him to post the outputs so we could see what we have in common. Fortunately though, mine worked as soon as I rebooted.

Paresh, I know that you can't do wireless period (much less WPA) but did you check the wpa_supplicant docs to see if your card is even supported? I was surprised by how limited that list was.... thank God my card was on it.

As to your problem of not being able to do anything to begin with... have you tried ndiswrapper? Check out [http://ubuntuforums.org/showthread.php?t=756260&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=756260&highlight=ndiswrapper)

Also, check out [http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_3945ABG_Mini-PCI_Express_Adapter)

I don't know what driver Ubuntu includes on default for your wireless card, but maybe that link will help. I have finals on Monday, I don't have a ton of time to do research, but you might be able to fix things by installing newer drivers, or perhaps installing ndiswrapper and using the windows drivers. You're lucky, Toshiba has excellent support, you should be able to find those drivers easily. Good luck!

---

### Post by chili555 on 2008-05-02
Sorry for my misunderstanding.

---

### Post by Paresh on 2008-05-03
Just to be clear, my the wireless hardware on my Toshiba Tecra A9 was working fine with Ubuntu 7.10, and only caused a problem when I installed Kubuntu 8.04.

Anyway, it is now sorted, installing the linux-backports-modules-hardy-generic package seems to do the trick.  Thanks for the help.

---

### Post by markofealing on 2008-05-10
Well I've tried this and I get to 57% where it sticks. I can connect to my wireless using Konsole, but for some reason crappy knetworkmanager (an absolute waste of space) repeatedly asks fro the WEP key, even though it has been entered.

I can get a wired connection but not wireless. Is there a way of hard coding in the essid and wep key as I'm very tempted to wipe 8.04 and go back t 7.10 which at least worked reasonably well.

BTW this was a fresh install.

---

### Post by markofealing on 2008-05-10
Fixed it!

I installed Wireless Assistant - Wireless LAN Manager, selected my network from the list of essids and entered the wep key and it just worked!:)

Why can't knetworkmanager just work out of the box? Considering it is supposed to make network access, particularly wireless as painless as possible all it manages to achieve is the absolute opposite.:confused:

---

