---
title: "Wireless SUDDENLY stopped working"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by jjdarling on 2008-05-21
I'm using a system76 PC that i've had for about 9 months and have never had a problem with the wireless. I updated to 8.04 a few weeks ago, and it was working fine before. Suddenly, as I was surfing the web, my wireless stopped working. My roommates who are on the same network have not changed anything, and their wireless still works fine. I have no idea what could have changed, so I'm trying to diagnose the problem.

The network is a WEP wireless network. When I click on "Manual Configuration" in my Network Manager, it doesn't even have the wireless option, simply the "Wired Connection" and "Point to Point" connection. My list of wireless networks is still up to date. Also, I live in a busy apartment complex, and usually I can see like 10 other networks, but I don't see them.

Anybody have any idea what the problem could be? Or at least where I should start looking?

---

### Post by jjdarling on 2008-05-21
Oh, and if it helps, I'm using an Ethernet cable right now, and it works fine.

---

### Post by jjdarling on 2008-05-22
Sorry to keep bumping my own thread (well, I'm not really sorry), but I've made a little bit of progress, but it might be one of those 1 step forward 2 steps back things.

So after resetting the factory settings on this computer, updating everything on my update manager, and then reinstalling the manufacturer's drivers, and then rebooting a couple times, the wireless connection came up on my Network Manager. However, I can't really seem to do anything with it. Here are the results of when I type in lshw -C network:

```
jjdarling@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 02
       serial: 00:1b:38:4c:60:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.1.103 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:72:5a:93
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
```

and here is the result of when I type in ifconfig -a:

```
jjdarling@ubuntu:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:1b:38:4c:60:bb  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe4c:60bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4888628 (4.6 MB)  TX bytes:1460854 (1.3 MB)
          Interrupt:17 

eth3      Link encap:Ethernet  HWaddr 00:19:d2:72:5a:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145736 (142.3 KB)  TX bytes:145736 (142.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-72-5A-93-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

And finally, here is what my /etc/network/interface file says: 

```
# The loopback interface
# Interfaces that comes with Debian Potato does not like to see
# "auto" option before "iface" for the first device specified.   
iface lo inet loopback
auto lo

auto eth0 
iface eth0 inet dhcp

```


So it seems there is a big mismatch between what everything is calling my wireless connection. Also, in the Network Manager manual configuration, it calls my wireless setting "eth3", which iirc was what it was also called when it worked.

Anyway, I'm pretty new to linux, so hopefully somebody can identify the problem.

Oh...and just to show how noobish I am, I tried to change my /etc/network/interface file and I was told I didn't have the permissions to do that, and I don't know how to get around that. Even when i try to access it via the terminal saying sudo /etc/network/interface it says "Permission Denied".

---

### Post by chili555 on 2008-05-22
How about letting us see:```
sudo cat /var/log/messages | grep switch
```Also, you need to tell the terminal what you want to do to *interfaces:*```
sudo **gedit** /etc/network/interfaces
```And it's interfaces, not interface. There are usually several interfaces listed in there, so it's plural.

---

### Post by jjdarling on 2008-05-22
```
jjdarling@ubuntu:~$ sudo cat /var/log/messages | grep switch
[sudo] password for jjdarling: 
May 18 22:24:47 ubuntu kernel: [   13.777633] SMP alternatives: switching to UP code
May 18 22:24:47 ubuntu kernel: [   14.063463] SMP alternatives: switching to SMP code
May 18 22:24:47 ubuntu kernel: [   29.911251] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 20 23:50:51 ubuntu kernel: [   13.749517] SMP alternatives: switching to UP code
May 20 23:50:51 ubuntu kernel: [   14.035596] SMP alternatives: switching to SMP code
May 20 23:50:51 ubuntu kernel: [   29.515969] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 20 23:50:51 ubuntu kernel: [   33.177096] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x10e90000
May 21 10:10:22 ubuntu kernel: [   13.424927] SMP alternatives: switching to UP code
May 21 10:10:22 ubuntu kernel: [   13.712542] SMP alternatives: switching to SMP code
May 21 10:10:22 ubuntu kernel: [   13.980977] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 21 18:03:17 ubuntu kernel: [ 8906.180899] Kill switch must be turned off for wireless networking to work.
May 21 18:10:41 ubuntu kernel: [   16.147061] SMP alternatives: switching to UP code
May 21 18:10:41 ubuntu kernel: [   16.433228] SMP alternatives: switching to SMP code
May 21 18:10:41 ubuntu kernel: [   16.721153] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 21 18:10:41 ubuntu kernel: [   35.201982] Kill switch must be turned off for wireless networking to work.
May 21 18:10:41 ubuntu kernel: [   35.505968] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x10e90000
May 21 19:52:37 ubuntu kernel: [   15.729885] SMP alternatives: switching to UP code
May 21 19:52:37 ubuntu kernel: [   16.016819] SMP alternatives: switching to SMP code
May 21 19:52:37 ubuntu kernel: [   16.582167] checking if image is initramfs...<6>ACPI: EC: non-query interrupt received, switching to interrupt mode
May 21 19:52:37 ubuntu kernel: [   34.724021] Kill switch must be turned off for wireless networking to work.
May 22 00:47:23 ubuntu kernel: [   14.057173] SMP alternatives: switching to UP code
May 22 00:47:23 ubuntu kernel: [   14.351773] SMP alternatives: switching to SMP code
May 22 00:47:23 ubuntu kernel: [   14.925443] checking if image is initramfs...<6>ACPI: EC: non-query interrupt received, switching to interrupt mode
May 22 00:47:23 ubuntu kernel: [   33.097890] Kill switch must be turned off for wireless networking to work.
May 22 01:30:24 ubuntu kernel: [   15.975025] SMP alternatives: switching to UP code
May 22 01:30:24 ubuntu kernel: [   16.261023] SMP alternatives: switching to SMP code
May 22 01:30:24 ubuntu kernel: [   16.819149] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 22 01:30:24 ubuntu kernel: [   34.608168] Kill switch must be turned off for wireless networking to work.
May 22 10:49:02 ubuntu kernel: [   13.350817] SMP alternatives: switching to UP code
May 22 10:49:02 ubuntu kernel: [   13.638451] SMP alternatives: switching to SMP code
May 22 10:49:02 ubuntu kernel: [   13.918721] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 22 10:49:02 ubuntu kernel: [   32.438381] Kill switch must be turned off for wireless networking to work.
May 22 10:54:07 ubuntu kernel: [   14.259060] SMP alternatives: switching to UP code
May 22 10:54:07 ubuntu kernel: [   14.545431] SMP alternatives: switching to SMP code
May 22 10:54:07 ubuntu kernel: [   14.821830] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 22 10:54:11 ubuntu kernel: [   38.271115] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:54:13 ubuntu kernel: [   40.061831] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:57:40 ubuntu kernel: [  127.958647] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:57:40 ubuntu kernel: [  127.963327] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:57:40 ubuntu kernel: [  127.999292] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:57:40 ubuntu kernel: [  127.999844] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:57:43 ubuntu kernel: [  129.076347] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:07 ubuntu kernel: [  134.690072] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:15 ubuntu kernel: [  137.260344] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:30 ubuntu kernel: [  149.464079] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:30 ubuntu kernel: [  149.520440] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:30 ubuntu kernel: [  149.523741] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:30 ubuntu kernel: [  149.538425] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:30 ubuntu kernel: [  149.541286] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:58:57 ubuntu kernel: [  156.206459] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:59:04 ubuntu kernel: [  158.221351] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:59:13 ubuntu kernel: [  167.414363] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:59:13 ubuntu kernel: [  167.510483] iwl3945: Radio disabled by HW RF Kill switch
May 22 10:59:15 ubuntu kernel: [  168.785440] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:01 ubuntu kernel: [  231.895373] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:01 ubuntu kernel: [  231.897943] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:01 ubuntu kernel: [  231.914284] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:01 ubuntu kernel: [  231.915227] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:03 ubuntu kernel: [  233.100934] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:27 ubuntu kernel: [  239.380949] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:03:33 ubuntu kernel: [  241.115199] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:31 ubuntu kernel: [  259.434931] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:31 ubuntu kernel: [  259.471618] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:31 ubuntu kernel: [  259.483173] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:31 ubuntu kernel: [  259.503558] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:31 ubuntu kernel: [  259.504106] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:33 ubuntu kernel: [  260.407357] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:04:58 ubuntu kernel: [  266.409936] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:05:03 ubuntu kernel: [  268.296550] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:08:54 ubuntu kernel: [  345.448431] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:09:00 ubuntu kernel: [  347.690367] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:09:00 ubuntu kernel: [  347.723809] iwl3945: Radio disabled by HW RF Kill switch
May 22 11:09:03 ubuntu kernel: [  349.247556] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:00 ubuntu kernel: [ 1410.386079] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:00 ubuntu kernel: [ 1410.406486] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:00 ubuntu kernel: [ 1410.413558] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:00 ubuntu kernel: [ 1410.415834] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:02 ubuntu kernel: [ 1411.748630] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:26 ubuntu kernel: [ 1418.744438] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:12:36 ubuntu kernel: [ 1421.652522] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:20:13 ubuntu kernel: [ 1554.517972] iwl3945: Radio disabled by HW RF Kill switch
May 22 12:27:31 ubuntu kernel: [ 1904.002998] iwl3945: Radio disabled by HW RF Kill switch

```

So it seems something happened yesterday evening that disabled it. I have no idea what it means though.

---

### Post by chili555 on 2008-05-22
> iwl3945: Radio disabled by HW RF Kill switchThat means there is a switch or key combination on your laptop that turns the wireless on or off. It's turned off right now. Find that switch or key combo and flip it.

---

### Post by jjdarling on 2008-05-22
Hmmm...I didn't even know I had a button that could do that.

Regardless, I think I went and messed things up quite badly. After your last post, I edited my interfaces file in sudo, simply switching where it says "eth0" to "eth3" in two places. I restarted the computer after saving, hoping that would have some effect, and when it rebooted, after logging in instead of the desktop loading as normal, I get the standard light-brown background color and a white box taking up the entire top-left quadrant. The cursor moves around but nothing else happens. I left it for about 7-8 minutes and then the white box turns into an error message that reads:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Sure enough, my theme is completely out of whack. Furthermore, it won't let me run "sudo gedit /etc/network/interfaces". I type it in, then the password, and then nothing, until I hit Ctrl-C. It will let me access the file without "sudo", but that is useless. Any idea what I've done to my machine or how I can fix it?

---

### Post by jjdarling on 2008-05-22
Ok, I fixed that little problem. Turns out it was working, it was just being incredibly slow. Now, however, I have to find how I deactivated my wireless. Any idea on how I would do this? The image on my keyboard corresponding to Function+F2 looks like a little wireless tower emanating signals. When I press it though, nothing happens.

Nothing has really changed when I check "sudo cat /var/log/messages | grep switch"

---

### Post by chili555 on 2008-05-22
Open up a terminal and do:```
sudo tail -f /var/log/messages
```Press the key combination and see if any messages appear. Beyond that, I'd suggest researching the model of your laptop on its manufacturer's website.

---

### Post by jjdarling on 2008-05-22
Thanks. I realized my problem would be better dealt with by the computer manufacturer, so I took my problem to their forum. Thanks for you help!

---

### Post by altf2o on 2008-05-27
I'm not sure if this thread will still be watched, but i had this same exact problem. I've been on Ubuntu 8.04 64bit for a little while. I ran the "beta" while it was still in development just to test it. 

About 1-2 weeks or so ago i started noticing my network was VERY slow, or completely unresponsive. It would ALWAYS connect however. Weirdest part is my laptop would connect via wireless right next to my desktop with no worries.

I tried both my:
Linksys WUSB54GC USB wireless network card and
D-Link WUA-1340 USB wireless network card

neither worked any differently. Wired internet was just fine however. So i did a bit of troubleshooting, and I've narrowed it down to one thing. Within the last couple weeks i upgraded Ubuntu via the normal upgrade manager available on KDE. It installed 2.6.24-17-generic SMP kernel for my x86_64 box. This is the problem. I rebooted, at the GRUB prompt selected my old 2.6.24-16-generic SMP x86_64 kernel, wireless is back to 100% with EITHER USB network cards.

I'm not sure what the hell they did in the kernel, but it totally jacked my wireless networking. Until a patch is released I'm definitely staying one back. Hope it helps.

altf2o...

---

### Post by kylemallory on 2008-06-05
Yeah, there is definitely something going on with the latest kernels, and 8.04.  Wireless has been working fine on my Dell Latitude (ilw3945) for years.  In the last two weeks, it has been very intermittent, and today, after the latest kernel updates (2.6.24-18) it has failed to connect at all.

I've tried with my "RF Kill" switch, and no luck.

I'm on another machine, but I'll post a follow-up with the relevant log messages.  But it seems that the latest wireless module says that the card doesn't support scanning ESSIDs, and that the module is unable to set half of the network parameters to properly configure it, when I specify the settings manually.

---

