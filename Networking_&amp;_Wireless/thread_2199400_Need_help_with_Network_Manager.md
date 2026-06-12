---
title: "Need help with Network Manager"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by dave2001 on 2014-01-13
For my "upgrade" to 13.10 I did a fresh, base-system install of ubuntu, from the minimal-cd, in order to build a lean system and learn more about linux in the process. I chose KDE as my desktop, since Kubuntu has been my favored choice for the last several releases.

During installation I put in my wireless network id and password, and connection set itself up fine. However, after the base system install, I installed the "kde-plasma-desktop" package. This provides the KDE workspace with a bare minimum of applications.

I installed the "plasma-nm" package, since this is what I understand to be the Network Manager interface for KDE4. Strangely enough, it shows no connections, or any available ones (even my home network, which I know is broadcasting), I'm actually sending this post from this very computer. left-clicking the system tray applet shows that wireless and networking are enabled, but the rest of the window is blank.

I'm guessing I just need to configure the network manager to connect with whatever it acts as a gui for. Any help appreciated. If I can post anything helpful, I'd be happy to do so.

Here's the output of "lshw -C network" if that helps any

[HTML]*-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:68:11:85:e1
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:fc200000-fc21ffff memory:fc224000-fc224fff ioport:1800(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:7e:28:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-15-generic firmware=8.83.5.1 build 33692 ip=192.168.254.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f4200000-f4201fff
[/HTML]

---

### Post by Bucky Ball on 2014-01-13
Is this the only desktop environment you have installed?

IMHO, dragging in *-desktop anything defeats the purpose of a minimal install as it drags in a whole heap of apps and dependencies you may not need/want/use. With a mini, your best to install the desktop environment of choice ONLY (xfce4 for me) and then 'sudo apt-get' only what you want/find you need. Keeps it as minimal as possible. You want it so there isn't anything you don't use (at least that's my aim, even though it is still not possible unless you build from scratch (see Linux From Scratch)).

Having said that, your install would still be on the lighter side.

How exactly did you install? Did you choose the kind of system profile you wanted (gives you a big list toward end of install) or did you ignore that and reboot to a CLI then 'sudo apt-get' the packages you needed (including kde-plasma-desktop)? If you did the latter did you install network-manager or network-manager-gnome and now have plasma-nm installed as well? If so, remove one, reboot.

PS: Just re-reading the details for kde-plasma-desktop; yea, that should be fine as it is basically kde-core (I was going to ask if one existed, had a look and this is pretty much it). The inclusion of 'desktop' in its title threw me as this usually means dragging in bunches of default applications and  dependenices.

---

### Post by dave2001 on 2014-01-13
> **Bucky Ball said:**
> 
How exactly did you install? Did you choose the kind of system profile you wanted (gives you a big list toward end of install) or did you ignore that and reboot to a CLI then 'sudo apt-get' the packages you needed (including kde-plasma-desktop)? If you did the latter did you install network-manager or network-manager-gnome and now have plasma-nm installed as well? If so, remove one, reboot.

PS: Just re-reading the details for kde-plasma-desktop; yea, that should be fine as it is basically kde-core (I was going to ask if one existed, had a look and this is pretty much it). The inclusion of 'desktop' in its title threw me as this usually means dragging in bunches of default applications and  dependenices.

I used the minimal install disc to install a base cli system, configure apt,and install grub2. Then after rebooting, i used apt-get install to pull in other needed packages. The "kde-plasma-desktop" is indeed pretty minimalistic. It really only includes basic apps like dolphin, kwrite, konsole, and a couple others.

Anyway, to answer your other question. Yes, the network-manager package is installed, however, if i select it for it for uninstallation, i'm informed that plasma-nm will also be uninstalled.. so I'm thinking that plasma-nm is the new KDE frontend for network-manager.

---

### Post by Bucky Ball on 2014-01-13
Perhaps experiment. Install them both then just install nm-plasma and see if it drags in network-manager.

---

### Post by steeldriver on 2014-01-13
Are you sure it's not just because your pre-desktop install set up the interfaces via /etc/network/interfaces? network-manager will ignore these by default (regardless of what desktop you're using afaik)

---

### Post by dave2001 on 2014-01-14
Thanks for the suggestions!

Unfortunately, no luck. I tried uninstalling and reinstalling (used purge actually). Reboot for thoroughness. Then apt-get installing either network-manager or plasma-nm pulls in the other as well, so I'm guessing this is the intended functionality. Then after another reboot just for thoroughness, still no luck with the tray applet recognizing any available networks or existing connections.

One bit of info that may or may not be useful: If I uncheck either of the boxes for "Networking Enabled" or "Wireless Enabled" in the tray applet, my internet connection will be lost, and does not auto-reconnect after rechecking said box.

---

### Post by dave2001 on 2014-01-15
I tried this question over in kde-land, but got little help, so I thought maybe this would be a more appropriate place. I have just done a base-system install of 13.10 on my T500 using the minimal install cd. Install went wonderfully, including wifi-setup. I then installed kde-plasma-desktop using apt-get. The kde-plasma-desktop metapackage has a VERY limited number of associated applications, so I'm thinking maybe I'm missing one, or I just don't know the appropriate way to configure the networking.

Upon logging into kde for the first time, wireless network hooks up fine, just as before, since it was configured by cli during install. But there's no way in kde to configure it should i take my laptop somewhere else. So I also used apt-get to install the default Kubuntu solution: network-manager and plasma-nm (the system tray applet), which install together.

Network manager recognizes that I have a connection, but it thinks it's a wired connection, and has no options to control it. It does not recognize that I have a home wireless network which is broadcasting it's ssid for anyone to see.

I've poked around the forums here and other sites like kde.org, but have really only found a couple other threads with problems like this, not solutions. Or I've more often found threads pertaining to knetwork-manager, the default opensuse solution.

I'm sure I could just do a regular ol' Kubuntu installation and things would work fine, as they did with 12.04, but that would defeat much of my purpose in doing a more "from scratch" installation. I've learned a lot and solved a few issues on my own already, but this one is stumping me.

Any help much appreciated!

---

### Post by dave2001 on 2014-01-15
Apologies to Admins and moderators, but there didn't seem to be much progress here, and I thought this thread might get better help in the networking and wireless section of the forums, so I reposted there. 
[URL="http://ubuntuforums.org/showthread.php?t=2199676"]http://ubuntuforums.org/showthread.php?t=2199676 

[/URL]I'll try to figure out if I can mark thread this closed or something...

---

### Post by steeldriver on 2014-01-15
If by "configured by cli" you mean that your interfaces were (and still are) defined in the /etc/network/interfaces file, then (regardless of desktop) the network-manager service will ignore them (technically it treats them as 'unmanaged'). If you want network-manager and its associated GUI applet to take control of them you will need to revert the /etc/network/interfaces file so that it contains only the loopback interface

```

auto lo
iface lo inet loopback

```

---

### Post by Bucky Ball on 2014-01-15
*Threads merged.*

In future, just ask a staff member to move your thread to a different area of the forum. Thanks.

---

### Post by dave2001 on 2014-01-15
> **Bucky Ball said:**
> *Threads merged.*

In future, just ask a staff member to move your thread to a different area of the forum. Thanks.

I will indeed, Thanks you very much for merging my threads! 

Hopefully in the future I will just think a bit harder about where to post in the first place :)

---

### Post by dave2001 on 2014-01-15
> **steeldriver said:**
> If by "configured by cli" you mean that your interfaces were (and still are) defined in the /etc/network/interfaces file, then (regardless of desktop) the network-manager service will ignore them (technically it treats them as 'unmanaged'). If you want network-manager and its associated GUI applet to take control of them you will need to revert the /etc/network/interfaces file so that it contains only the loopback interface

```

auto lo
iface lo inet loopback

```


This was the problem exactly! Thank you so very much my good sir. Network manager is plugging happily along now. I did look through [http://ubuntuguide.org/wiki/Ubuntu:Saucy](http://ubuntuguide.org/wiki/Ubuntu:Saucy) and several other documentation type resources before coming to the forums, but I didn't see anything this basic addressed.

Once again, thanks to all who chimed in.

---

### Post by steeldriver on 2014-01-15
... I think I mentioned it already (post #5)

---

### Post by dave2001 on 2014-01-15
> **steeldriver said:**
> ... I think I mentioned it already (post #5)

So you did, and somehow I missed your point in that first post. I didn't realize I actually needed to remove them from the file, I thought I was somehow needing to get network manager to recognize they were there. Suppose I didn't read carefully enough.

---

