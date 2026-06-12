---
title: "RTL8187L Wifi Help (Rosewill RNX-G1W)"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by chrisolof on 2008-09-05
Hello-

I just purchased a Rosewill RNX-G1W (USB wifi NIC) and thought it'd be easy to get working considering the chipset it uses: RTL8187L (the realtek website lists a driver for linux for the RTL8187L chipset).

Problem is - it doesn't seem to work in Ubuntu 8.04.  I plugged it in, saw no signal light from the led on the unit, but did see wifi networks under NetworkManager.  It also let me connect to my network successfully.  For about 15 seconds I was surfing the net fine - then the connection dropped to a snails pace - then it was not finding web pages.  Re-plugging the device would give me about another 15 seconds - then no throughput again.

Is there an issue with the driver for this wifi chipset?  Is there a workaround?

I've tried ndiswrapper with the XP and 2000 inf files from the bundled cd, but neither would make a successful connection - could just list the networks around me.  Since uninstalling ndiswrapper I no longer have any action when I plug this device in - I don't even have a wireless option in the manual network configuration anymore.

The bundled CD came with a "Linux" folder, which contains linux drivers, but following their readme instructions I'm getting nowhere - make is returning errors and not creating the ".ko" files I'm supposed to reference with "insmod."

Does anyone know what I could try next?

---

### Post by chrisolof on 2008-09-08
Just an update - the linux drivers that come on cd with this Rosewill USB wifi stick are the same ones available from Realtek's website.  The reason they weren't compiling right is because they're so old that they are no longer compatible with today's linux kernel.  Looks like they weren't even developed by Realtek - but instead by Andrea Merello ([here's his outdated sourceforge project]("http://sourceforge.net/projects/rtl8180-sa2400")), who stopped working on the project years ago.

Now, there's another project with newer drivers:
[http://rtl-wifi.sourceforge.net/wiki/Main_Page]("http://rtl-wifi.sourceforge.net/wiki/Main_Page")

These drivers are part of the current linux kernel - which is why this wifi stick initially connected to my network with no problems (for 15 or 20 seconds).

The problem seems to be known and there are some avenues to try.  Here's an archlinux solution that I tried:
[http://wiki.archlinux.org/index.php/Rtl8187_wireless#What_to_do_if_your_connection_always_times_out.3F]("http://wiki.archlinux.org/index.php/Rtl8187_wireless#What_to_do_if_your_connection_always_times_out.3F")

Basically the idea is that you limit the throughput to 5.5 Mbps once you've established a connection and that stops the timeout problem.  This solution doesn't seem to work for me (connection still hits 0 throughput) and seems more like a tape-it-up and hope it holds approach to the underlying problem - which I believe to be with the driver.  I'm going to try this solution next:

[https://sourceforge.net/forum/forum.php?thread_id=2024524&forum_id=652149]("https://sourceforge.net/forum/forum.php?thread_id=2024524&forum_id=652149")

Again, if anyone else has a solution to this or an idea to try I'm all ears.  Thanks,

---

### Post by chrisolof on 2008-09-18
So I'm giving up on this usb adapter.  The rtl8187 driver doesn't work for more than a few seconds, and ndiswrapper on the xp driver doesn't connect to anything with encryption, which isn't going to work.  If anyone else buys this adapter I wish you luck.  Maybe one day it will work.

---

### Post by sunkssss on 2008-10-26
If you don't need to be using Ubuntu, Kubuntu should work according to [http://ge.ubuntuforums.com/showthread.php?t=888120](http://ge.ubuntuforums.com/showthread.php?t=888120)

Though I assume you've already found that post since you seem to have spent a lot of time searching for a solution.

---

### Post by 3rdalbum on 2009-01-26
Just noticed this post from your reply to my Launchpad bug. Did you try these instructions for installing the Aircrack driver? ([http://zenzike.blogspot.com/2008/11/wireless-woes.html]("http://zenzike.blogspot.com/2008/11/wireless-woes.html"))

There is no WPA support, but the speed is reasonable, the reliability is very good and the range is superb.

---

### Post by chrisolof on 2009-01-30
Well at this point I'm using WPA2 so that's probably not the best option for my situation.  It does look promising for WEP or no encryption at all.

For now I've got a CAT5 running through the kitchen over to the workstation with the Rosewill RNX-G1W.  I'm still hoping that it might function properly one day (it's such a great card in Windows).

---

### Post by sabre2th on 2009-06-08
I just posted this in another thread.  I don't know if it applies to 8.04, but I've got the same adapter on Jaunty.  What worked for me was to install linux-backports-modules-jaunty.  Try installing linux-backports-modules-hardy and restarting.

I use it in my Mythbuntu box and it has dropped a few times when streaming, but I don't know what the cause is or if it's even a serious issue.  I changed channels on my router and it's been fine since, though I haven't used it much.  I'm using WPA2 btw.

---

### Post by chrisolof on 2009-06-11
Very Cool - that machine is running 9.04 now so I'll give linux-backports-modules-jaunty a try and report back.  Thanks!

---

### Post by chrisolof on 2009-06-16
Installing linux-backports-modules-jaunty does indeed load a more stable driver than the standard one and my connection strength is right where it should be.  I no longer lose my data throughput entirely, I can connect to my WPA2 network, and I'm posting this using the RTL8187L.

The only issue now is that I seem to be getting very low throughput.  The connection starts out at 54Mbps like it should - but over a bit of use drops down to 1Mbps (according to NetworkManager's "Connection Information").  I'm getting about 500Kbps on the dlsreports speed test ([http://www.dslreports.com/speedtest?flash=1](http://www.dslreports.com/speedtest?flash=1)) up and down.

So it isn't fixed 100% but good enough for some casual web browsing - which is what this particular machine is primarily used for anyway.  Great progress!

---

### Post by BuMRK on 2009-09-15
Helo,

I have a problem with the compilation rtl8187L drivers from the kernel 2.6.31 + there is such an error

root @ bum-laptop: / # make clean home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release
make [1]: Leaving directory `/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/rtl8187 '
rm-fr *. mod.c *. mod *. o .*. cmd *. ko * ~
rm-fr. tmp_versions
rm-fr Module.symvers
rm-fr modules.order
rm-fr Module.markers
"rm-rf tags
make [1]: Leaving directory `/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/rtl8187 '
make [1]: Leaving directory `/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211 '
rm-f *. mod.c *. mod *. o .*. cmd *. ko * ~
rm-rf / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/tmp
rm-fr Module.symvers
rm-fr modules.order
rm-fr Module.markers
make [1]: Leaving directory `/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211 '
root @ bum-laptop: / # home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release
root @ bum-laptop: / # make home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_softmac.o
/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_softmac.c: In function 'ieee80211_send_beacon':
/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_softmac.c: 278: warning: unused variable 'flags'
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_rx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_tx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_wx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_module.o
/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_module.c: In function 'alloc_ieee80211_rtl':
/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_module.c: 123: error: 'struct net_device' has no member named 'hard_start_xmit'
make [2]: *** [/ home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211/ieee80211_module.o] Error 1
make [1]: *** [_module_/home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release/ieee80211] Error 2
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
make: *** [all] Error 2
root @ bum-laptop: / # cd .. home/bum/sterowniki/rtl8187L_linux_26.1038.0626.2009.release
root @ bum-laptop: / home / bang / driver # cd rtl8187L_linux_26.1037.1217.2008_release /
root @ bum-laptop: / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release #. / makedrv
rm-f *. mod.c *. mod *. o .*. cmd *. ko * ~
rm-rf / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/tmp
make-C / M = lib/modules/2.6.31-9-generic/build / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211 CC = gcc modules
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_softmac.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_rx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_tx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_wx.o
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_module.o
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_module.c: In function 'alloc_ieee80211_rtl':
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_module.c: 121: error: 'struct net_device' has no member named 'hard_start_xmit'
make [2]: *** [/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_module.o] Error 1
make [1]: *** [_module_/home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/ieee80211] Error 2
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
make: *** [modules] Error 2
rm-fr *. mod.c *. mod *. o .*. cmd *. ko * ~
rm-fr. tmp_versions
make-C / M = lib/modules/2.6.31-9-generic/build / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187 CC = gcc modules
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
   CC [M] / home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.o
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: In function 'rtl8180_init':
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 3311: error: 'struct net_device' has no member named 'get_stats'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: In function 'rtl8187_usb_probe':
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4393: error: 'struct net_device' has no member named 'open'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4394: error: 'struct net_device' has no member named 'stop'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4396: error: 'struct net_device' has no member named 'tx_timeout'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4398: error: 'struct net_device' has no member named 'do_ioctl'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4399: error: 'struct net_device' has no member named 'set_multicast_list'
/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.c: 4400: error: 'struct net_device' has no member named 'set_mac_address'
make [2]: *** [/ home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187/r8187_core.o] Error 1
make [1]: *** [_module_/home/bum/sterowniki/rtl8187L_linux_26.1037.1217.2008_release/rtl8187] Error 2
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-9-generic '
make: *** [modules] Error 2

---

### Post by amorde on 2011-03-09
I'm new to Linux and running Ubuntu 10.10. I have the same problem with dropped connections and slow DL speed using the Rosewill RNX-G1W (RTL8187L). Does anyone know if the backport suggestion listed above work in 10.10 or would Ndiswrapper work better?

---

