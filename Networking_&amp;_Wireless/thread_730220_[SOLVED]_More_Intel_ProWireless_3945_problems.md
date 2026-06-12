---
title: "[SOLVED] More Intel Pro/Wireless 3945 problems"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by Meph1st0 on 2008-03-20
I've completely messed this up now.  I'm using a Dell XPS M1710 with the Intel Pro/Wireless 3945 NIC.  

I originally had the ipw3945 restricted drivers enabled.  With that I could connect to my wireless network, but I couldn't browse any websites; they'd all time out after a minute or two.  But I was able to ping my default gateway, google.com and pidgin would even connect to msn messenger (but not google talk).

I've done quite a bit of research on this problem and in the process I think I've made it worse.

According to this link it's better to use the iwl3945 driver rather than the ipw3945 driver:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/158045)

And so I successfully changed my driver to use iwl3945 by follwing this thread:
[http://ubuntuforums.org/showthread.php?t=595060](http://ubuntuforums.org/showthread.php?t=595060)

In one of the posts it says that my logical name is supposed to change to wlan0 but it didn't.  

The following command lshw -C Network give me: 
```
jbrown@Jonslaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:0d:e2:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4d:3e:16
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5752-v3.19 ip=192.168.1.109 latency=0 module=tg3 multicast=yes

```

But in the Network Settings window in Gnome it shows three wired connections and my modem.

Wired connection (eth1)
roaming mode enabled

Wired connection (eth0)
roaming mode enabled

Wired connection (wlan0_ren)
roaming mode enabled

I would expect to see only a wired connection, a wireless connection and my modem.  I don't understand why I have extra wired connections.

The file at /etc/network/interfaces only contains the following:
```

auto lo
iface lo inet loopback

```


The network manager applet in my system tray gives me the option to connect to the wired network or the wireless network (I get about 80% signal strength).  If I select wired then I can get on the internet and everything works fine.  If I select wireless network, I can connect to the wireless network but I still can't browse any websites.  They still timeout after a minute or two. I can still ping google.com and pidgin connects to my IM services.  It's almost like my firewall is preventing port 80 when I'm connected wirelessly but I don't know how to check or fix that.

Can somebody help me?

---

### Post by jcostom on 2008-03-20
As far as the device name goes, the thread you referenced contains a link to a post that tells you how to fix that:

[http://ubuntuforums.org/showpost.php?p=3562827&postcount=5](http://ubuntuforums.org/showpost.php?p=3562827&postcount=5)

It sounds like you've got other network problems going there, which may not be related to your NIC driver.  I've got the same card in in aThinkpad T60 and it works just fine with the iwl drivers and the 2.6.24.2 kernel..  I also patched with the iwl-leds patch, so the wifi led also works correctly.  That machine connects to a network type that I've seen lots of people reporting trouble with..  Hidden SSID, WPA2 using EAP-TTLS, AES for the encryption.  Works like a champ.

Sorry, but that's the only suggestion I've got..  That, or possibly you've got defective hardware?

---

### Post by Superpup on 2008-03-23
I fought and fought with wireless problems on my Asus A7J with the same Intel wireless card under 7.10. I had tried every suggestion I was offered, searched several forums and tried the suggestions, numerous Howtos, and still nothing would work. Finally I narrowed it down to some log entries stating "The RF Kill switch is enabled. It must be disabled for Wireless to work". However I never could resolve that issue. I finally gave up and went back to just plugging into the hardwire LAN which had always worked fine.

When the alpha release of 8.04 became available I downloaded and installed that, and thought maybe it had fixed it because while the laptop was booting up the Wireless connection light would light up. Sadly, as the log in screen loaded the wireless light went out and I still could not get it to work.

The next day Update Manager said I had 150 (or so) updates to install. I installed the updates and rebooted and the wireless light stayed on this time! Using Wireless Assistant - Wireless LAN Manager I was able to detect the Wireless network at work, and was able to easily connect to the WPA2 network.

I hope you have better luck than I did getting it to work. I'm hoping it continues to work through to the final release of 8.04.

---

### Post by Meph1st0 on 2008-03-23
Thanks Superpup for that info.  I was hoping that it would be fixed with the next release of Ubuntu.  It should be coming out in a month so I'm going to just wait until then.  I can do what I need to do with a wired connection.

---

### Post by Meph1st0 on 2008-07-20
By the way, Hardy Heron has solved my networking problems.

---

