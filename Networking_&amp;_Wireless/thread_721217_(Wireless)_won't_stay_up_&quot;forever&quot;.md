---
title: "(Wireless) won't stay up &quot;forever&quot;"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2008-03-11
Hi guys,

set up a wireless router, and a USB dongle on an Ubuntu 7.10 pc. I have configured the dongle with the gtk-ndis-wrapper tool, and wiCD. The PC quite happily brings the network up as part of boot, so I can NXClient into it.

However, if I leave the PC on (with an NX session disconnected, if that's significant), then overnight (i.e. after 8 hours or so), then something happens and the network is lost. I can't PING or NXCLient back into it the next morning - I have to reboot it. After reboot, it's all fine again.

I can disconnect and reconnect the NXClient session over a few hours no problem.

The NX session is running the gnome-btorrent client, if that's significant. My eventual aim is to make this particular PC a media-server, and shove it in the loft to be on 24/7, so it's not annoying the wife when a slow download is running.

Can anyone suggest what's going on, or at the very least point me in the direction of a log file or configuration file to help diagnose further.

As always, thanks in advance

---

### Post by wblancqu on 2008-03-11
Try giving your interface a static IP, instead of using DHCP for obtaining an address. Otherwise try using another driver for your wireless card (I suppose it'll be a broadom-based chipset -> bcm43xx-fwcutter). Let me know if anything worked, because a couple of months ago I had the same problem, and just switched to ethernet cable.

Good luck!

---

### Post by Jethro_uk on 2008-03-11
hmmm, I'll have a look, there's no religious reason why I'm using DHCP ... I guess there's a POV that *all* my boxes should have static addresses, and DHCP turned off at the router.

Theoretically, I could wire the box in. However it would get me an ear bashing from the wife, as one of the reasons a gave to get the budget for the router approved was "no wires, no disruption, drilling etc".

The other option is to revert back to Windows, which I know will stay up forever (well it did for 2 weeks, before I installed Ubuntu). But I'm loath to, because I like the idea of learning more Linux, and I dislike the idea of a 24/7 PC on a wireless network being a windows box.

---

### Post by wblancqu on 2008-03-11
Normally routers can work with DHCP/STATIC simultaneously. At home I have a little server with static IP, but all the other PC's use DHCP.

Grtz

---

### Post by Jethro_uk on 2008-03-18
> **wblancqu said:**
> Try giving your interface a static IP, instead of using DHCP for obtaining an address. Otherwise try using another driver for your wireless card (I suppose it'll be a broadom-based chipset -> bcm43xx-fwcutter). Let me know if anything worked, because a couple of months ago I had the same problem, and just switched to ethernet cable.

Good luck!

Tried setting a static IP address. Still fell over :-(

When it does, it keeps saying it's connected to network "None" at 72 dBm%. When I bring up the wicd panel, and try and reconnect to my network, it goes through the motions, but ends up still "Connected to None".

When I power the box into XP, no problems - the wireless is rock steady (well, stayed up for 3 days) so it doesn't appear to be environmental ...

the chipset is a "Marvell 225" - and I had to use ndiswrapper to get it working.

Sadly, it looks like if I want to run ubuntu on this machine, I'll have to wire a network in :(

---

### Post by gulac on 2008-03-18
I'm doing the exact same thing: media server running Ubuntu 7.10, ndiswrapper with WICD, wireless connection with a usb dongle, remote connection using VNC, deluge bittorrent client, DHCP gives always the same IP address, etc.

I'm using a DLink WUA-2340 with WPA and when the connection drops; it's then impossible to reconnect unless I reboot. I wanted to try two things now and maybe someone here can help me: use native drivers or try without wpa ?

I already posted this problem on another thread without much luck: [http://ubuntuforums.org/showthread.php?t=714083](http://ubuntuforums.org/showthread.php?t=714083)

Thanks !

---

### Post by Jethro_uk on 2008-03-19
There may be a clue in the system log - loads of ndiswrapper errors about not being able to determine bitrates and frequencies ... if this is the case, it could be a driver issue.

It's quite consistent about how it drops the network, but there's no set timescale. Yesterday I was lucky enough to see it fail about 5 minutes after boot. I had the wicd page open. It was connected, then all of a sudden, the statusbar flashed from "Connected to MyNetwork at -62dBm" to "Connected to None at -62dBm". It then kept switching bewteen the two stages, and I had lost connectivity. After that, wicd just stops working, and can't see any wireless networks.

I can leave windows XP up for days, and not lose the network, so it's not a hardware issue.

The chipset is a Marvell 225 or somesuch, and their support seems pretty patchy. If my posting that here causes people to steer clear and helps convince them to support Linux, it'd be a good thing.

---

