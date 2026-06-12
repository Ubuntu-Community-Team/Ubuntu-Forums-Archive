---
title: "&quot;SIOCSIFFLAGS:  No buffer space available&quot; on ifup?"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by tenner on 2007-10-23
Hi all,

I just installed Gutsy (fresh install) and it's looking great so far.  Except when I get to networking.

I have an RT2500 wireless card and actually had it working for about an hour.  I got far enough to install some software.  After moving a bunch of files the system locked up, and when I rebooted I lost networking.

I use static IPs.  Knetworkmanager gives me "No active device".  If I go to the KDE Control Module to configure the network interface, I verify that everything is correct.  When I click "Enable interface", it appears to enable for 2-3 seconds and then goes back to "Disabled".

Thinking there was a problem with the GUI, I tried to bring up wlan0 from the console, and instead I get this cryptic error message:

```
SIOCSIFFLAGS: No buffer space available
SIOCSIFFLAGS: No buffer space available
SIOCSIFFLAGS: No buffer space available
Failed to bring up wlan0.
```

I did the ndiswrapper update, and everything appeared to work correctly, but it's still happening.

sudo iwconfig wlan0  gives:

```
wlan0     IEEE 802.11g  ESSID:"<my ess_id>"
        Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
        Retry min limit:7  RTS thr:off  Fragment thr=2346 B
        Encryption key:off
        Link Quality:0  Signal level:0  Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

My /etc/network/interfaces looks like:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid <my_ess_id>

auto wlan0
```

I'm just about to pull my hair out over this one.  Anyone got any ideas?  Thanks in advance for any help you can give!

---

### Post by kevdog on 2007-10-23
You using ndiswrapper or the native rt2500 driver?

---

### Post by tenner on 2007-10-23
ndiswrapper... I blacklisted the native rt2500 driver as specified here:  [http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419").

(I'm also kind of new at this, so if what I just said doesn't make sense, tell me.  :) )

Thanks!

---

### Post by kevdog on 2007-10-23
Any particular reason?? I use ndiswrapper for a broadcom card, however someone within the last day has posted a how-to to get the native rt2500 driver up and running with gusty.  If you're in a jam, you could try this approach.

---

### Post by tenner on 2007-10-23
No particular reason, other than that I had convinced myself that it would work.  :-)

I'll find the rt2500/gutsy article and respond (likely tomorrow, since it's getting late) if it doesn't work.  I'm assuming that to undo what I did with ndiswrapper I can just un-blacklist the rt2500 driver?

Thanks for the help, I really appreciate it!

---

### Post by kevdog on 2007-10-23
Blacklist ndiswrapper and unblacklist rt2500 and then reboot -- that will basically put you back to where you started (except you wont have to install ndiswrapper -- this only prevents the loading of ndiswrapper kernel module).

---

### Post by adem666 on 2007-10-26
i have same problem.
when i installed kubuntu, it was working. it was working in installing step. so, if i run kubuntu live version, it was working. also, before i installed kubuntu 7.10 beta, again it was working. but now, holly release version of 7.10 can not run my stupid wireless usb dongle. it is very funny. i could not upderstand this situation, but it s really funny. 
i m searhing solution, i hope find

---

### Post by tenner on 2007-10-27
> **kevdog said:**
> Blacklist ndiswrapper and unblacklist rt2500 and then reboot -- that will basically put you back to where you started (except you wont have to install ndiswrapper -- this only prevents the loading of ndiswrapper kernel module).

Okay, I did this as well as following Zoiks' instructions ([http://ubuntuforums.org/showthread.php?t=584657]("http://ubuntuforums.org/showthread.php?t=584657")) and now my machine won't boot.

Unfortunately, I can't see what the problem is because for some reason my monitor doesn't like the video mode that Kubuntu uses to show the start-up info.  My guess is that it's failing on networking.

I've booted into recovery mode, and if I blacklist the newly installed rt2500 driver, I'm able to re-boot successfully.  But now I'm back to where I started...

```
SIOCSIFFLAGS: No buffer space available.
```

Help!

---

### Post by kevdog on 2007-10-27
Anything give you hints in the boot log or in the system log:

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by tenner on 2007-10-27
> **kevdog said:**
> Anything give you hints in the boot log or in the system log:

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Well, now I can't even get that far.  Attempting booting into recovery mode from GRUB, it gets through most of the process, but then I get as far as about here:

```

...
[   44.298932] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   44.301959] parport_pc 00:09: reported by Plug and Play ACPI
[   44.302074] parport0: PC-style at 0x378 (0x778), irq 7, dma 3, [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   44.945404] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   44.945475] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   45.471310] NET: Registered protocol family 10
[   45.471674] lo: Disabled Privacy Extensions
                                                                                              [ OK ]
 * Setting the system clock

```

and then it just hangs.  I've rebooted four times now with the same results.  At this point there's no disk activity, so I can only assume it's just sitting there.

What do you do once recovery mode doesn't even work?  (I hate to ask, but I think I know the answer, and it ends with "indows XP"...)

---

### Post by kevdog on 2007-10-27
if you cant boot into recovery mode, maybe try the live cd, I dont know if I have ever seen this situation before.

---

### Post by tenner on 2007-10-28
Okay... I can boot using the LiveCD and can mount my hard drive.  If I go to /etc/modprobe.d/blacklist and blacklist rt2500 and ndiswrapper, I can boot.

The error messages I'm getting at boot look like this:

```

[   40.523895] parport_pc 00:09: reported by Plug and Play ACPI
[   40.523959] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.548291] ieee80211_init: failed to initialize WME (err=-17)
[   40.558900] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   40.559048] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   40.559172] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   40.559382] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   40.574724] wmaster0: Selected rate control algorithm 'simple'
[   41.181549] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   41.181561] PCI: setting IRQ 10 as level-triggered
[   41.181568] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   41.426737] phy0 -> rt2500pci_init_bbp: Error - BBP register access failed, aborting.
[   41.426754] phy0 -> rt2500pci_enable_radio: Error - Register initialization failed.
[   43.165294] lp0: using parport0 (interrupt-driven).
[   43.206382] ndiswrapper version 1.45 loaded (smp=yes)
[   43.265108] usbcore: registered new interface driver ndiswrapper
[   43.360834] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   43.852936] EXT3 FS on sda3, internal journal

```

It looks like there's some kind of problem with the rt2500pci module, so just to be sure I decided I should take out EVERYTHING relating to wireless, and I figure I can re-add it later.  

So, I did:

```
modprobe -r rt2500
modprobe -r rt2500pci
modprobe -r ndiswrapper
```

and it's still locking up if I don't have rt2500 blacklisted on startup.

Any further ideas?

---

### Post by tenner on 2007-10-28
New info...

One of the reasons I updated from Dapper to Gutsy was that I thought my network card (wired Ethernet card, not wireless) had failed.  So, I got a wireless card that was hanging around the house.

After having so much trouble with wireless over the past few days, I decided to put the wired card back in for the heck of it to see if it would work.

It ALMOST does.  And now, for some unknown reason, the wireless card ALMOST works too.

They can both be enabled in knetworkmanager.  I gave them different IP addresses in case they started conflicting with each other.

My /etc/network/interfaces now looks like this:

```
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
wireless-essid <my_ess_id>

```

ifconfig gives:

```

eth0    Link encap:Ethernet  HWaddr 00:01:03:DE:89:7C
        inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:72 errors:0 dropped:0 overruns:0 carrier:65
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b)  TX bytes:4536 (4.4 KB)
        Interrupt:11 Base address:0x4c00

wlan0    Link encap:Ethernet  HWaddr 00:12:17:86:8F:D0
        inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        RX packets:346 errors:0 dropped:0 overruns:0 frame:0
        TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:34679 (33.8 KB)  TX bytes:35949 (35.1 KB)
        Interrupt:11 Base address:ff9f4000-ff9f6000

```

To the untrained eye (mine), everything LOOKS like it's running fine.  But when I go into firefox and try to load a site, nothing.  I tried to ping my website from the command-line (it's pingable from other places), I get nothing.

It's not the wireless MAC filter, I've checked that.  Something isn't allowing either the wired ethernet or the wifi to do anything useful.  I've tried disabling each of them individually to see if they were interfering with each other, but alas, no dice.

Please help!  It feels so close!

---

### Post by tenner on 2007-10-28
It works!  I hadn't added the gateway for the wlan0 connection, only for eth0.  Then I had to disable eth0 since it was getting confused between the two.

It works, at least for now... though I'm remembering this thread in case it breaks (heck, last time I got it working it broke an hour later).

kevdog, thanks a lot for the help... I really appreciate it!

---

### Post by kevdog on 2007-10-28
Dont run wired and wireless at the same time for one.  So take one interface down

sudo ifconfig <interface> down

For the other interface (preferrably the wired)
sudo ifconfig <interface> down
sudo ifconfig <interface> up
sudo dhclient <interface>

Check if you have a gateway as designated by UG (universal gateway) with 
route -n

The only other reason you might not be able to use firefox is name resolution with dns servers.
Try pinging a known IP address since this does not require a dns lookup.  If this is successful, then we can monkey with your dns settings.

---

### Post by tenner on 2007-10-28
It works!  

Thanks so much.  I'm still a little nervous because I don't know exactly what I did to make it work.  But, so long as it works, I don't care.  :-)

Thanks again!

---

