---
title: "ndiswrapper/wireless not working (Iknow, we've seen the 1000 times)"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by cjax1 on 2008-05-26
I don't know how many tutorials or how-to's I read on this subject of ndiswrapper and Broadcom cards in 8.04. I've been using ndiswrapper in three other releases. Each time having to figure out a different way of doing it. Each time hours of googling. Each time something changes. But this time it's a no go at all for me. I can't code but can't there be a way to figure out a way that works when someone like me installs ndiswrapper, like automatically blacklisting whatever needs blacklisting. After two full nights, a third after tonight, and at least 100 reboots my blood pressure is up. Each time I come across a new bit of info or how-to or tutorial I say That's it! That's gotta be it! But nothing works.

I had ndiswrapper working in 6.06. bcm43xx wasn't fast enough. I did the online upgrade to 8.04 recently and so far I think it's great. Wireless stopped after the upgrade but I did get it to work using another driver that came with 8.04. I forgot the name now, something like cutter. It was pretty easy but once again the speed isn't there. I mean it's OK but not quite what I need or got with ndiswrapper. I did a fresh 8.04 install on another partition two days ago. This time I do not want the native driver. I want ndiswrapper. Normally on this desktop I do not have an ethernet connection in the location I'm in. I have to be wireless. I took my computer to where there is an ethernet connection and installed all the ndiswrapper stuff via Synaptic. Then installed the Windows driver. Usually I have ndiswrapper on a thumb drive and install it from there. Anyway, that went well. ndiswrapper -l says hardware present and driver present.

But it is impossible to configure wireless in Administration Network. It keeps unchecking itself. I tried roaming mode, static IP, DHCP. According to various how-to's on this forum I added ndiswrapper to /etc/modules which I believe is pretty much what I did in the other releases. I tried blacklisting everything that came up in the how-to's. When I blacklist b43 the wireless doesn't even show in Network. Sometimes it didn't show up after blacklisting ssb.

Terminal outputs,

```
chris@hardy-desktop1:~$ sudo lshw -C network
  *-network:0            
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

**Under *-network:0 it used to have a line that said logical name wlan0 but no more.**

  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:16:76:9c:23:d7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:0b:cf:c0:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

chris@hardy-desktop1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ca1" 
          Mode:Managed  Channel:0  Access Point: Not-Associated  
          Tx-Power=0 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@hardy-desktop1:~$ sudo lsmod|grep -i -e b43 -e b44 -e bcm43xx -e ssb
b43                   115104  0
rfkill                  8592  9 rfkill_input,b43
mac80211              165652  1 b43
led_class                6020  1 b43
input_polldev        5896  1 b43
ssb                        32260  1 b43
chris@hardy-desktop1:~$
```


I blacklist or do a modprobe -r command on them according to one how-to like bcm43xx (which by the way bcm43xx IS ALREADY blacklisted but bcm43xx doesn't know it sometimes) and on ssb and b43. Nothing worked. Oh yeah, can't forget b43legacy.

I also found my old notes from a long time ago on installing ndiswrapper and did these commands that I remember worked back then.

sudo -i
depmod -a
modprobe ndiswrapper
ndiswrapper -m

Then restarted but nothing.

I turned off encryption on the router. The ssid broadcast is turned off but I entered that manually in networking. If I get this working then I'll try to get encryption set up.

I'm back to 6.06 again d*** it unless someone that really knows how to troubleshoot this can tell me how to get this working. I'm simply done with spending hours and hours on this searching. Please help. I don't care if I have to start from scratch one more time. I wouldn't doubt if I would need to reinstall after all I did. I'll be going back to 6.06 for a while yet. At least 6.06 is still supported and it's been working great for me.

Whatever. This is truly getting sickening. :( I feel like I'm wasting my time and everyone else's. I hope I get this going or there's no more new Ubuntu releases for me. Even if I do get this going in 8.04 I'm not thinking of trying to upgrade again unless I happen to see news of some type of major breakthrough in Ubuntu. That's what really sickens me. Please, someone fix this wireless stuff in Ubuntu. I'm talking about the GUI's or managers. At least make it easier to configure when we already have the damn drivers for the card even if it's the proprietary drivers. No GUI or manager in the world will work if the driver can't be loaded right? Hell with it. I don't even care if no one responds to this. Most people in their right mind would never put the hours I have put into it these last three nights being up late and I've been using ndiswrapper for a while.

Never mind. Don't even bother. It's 6.06 for me for now. Bye. Sorry. I'm done.

---

### Post by cjax1 on 2008-05-26
Sorry, one more thing. Before I posted the outputs of the terminal above I had un-blacklisted everything that I had blacklisted before. I hope that the developers aren't deliberately making it very hard to install proprietary drivers trying to push their own reverse engineered drivers. I know they work very hard at this and it actually works pretty good but it's just not quite fast enough especially for a streaming video channel I watch. Also some pages do load a little slower. The biggest deal is the streaming video. I guess I could look for a card that comes with native Linux drivers. It's just that my card works very well with ndiswrapper but it seems each release I try it keeps getting harder and harder to get ndiswrapper working. I would think it should get better not harder. There's a couple other distros that I can still use ndiswrapper with no problem. And I did not like the fact that the 8.04 upgrade killed the ndiswrapper driver that was already installed. I keep wondering why that is. OK, I'm done. I didn't do this just to bump up this thread. I still love Ubuntu but I can't keep dealing with this each time.

---

### Post by bluefrog on 2008-05-26
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist

sudo -i
cat >/etc/init.d/ndiswrapper <<eof
#! /bin/sh
### BEGIN INIT INFO
# Provides: ndiswrapper
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable to load ndiswrapper
# Description: enable to load ndiswrapper
### END INIT INFO

rmmod b44
#rmmod ohci_hcd  #uncomment if necessary
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
#modprobe ohci_hcd  #uncomment if necessary
modproble b44
eof
exit

sudo chmod 755 /etc/init.d/ndiswrapper
sudo update-rc.d ndiswrapper start 99 S 1 2 3 4 5 . stop 99 0 6 .

---

### Post by cjax1 on 2008-05-26
Thanks bluefrog but still no go. Throwing my hands in the air. I've threatened to move on before but this time I feel it's real close to actually happening. :( This wireless isn't the only thing. ARRRRRRGH!

OK so the script doesn't work for me. I tried it even not fully understanding it but I said what the heck. The thing is, after blacklisting b43 the wireless connection doesn't show in Network.

BTW, of the many things I read and tried one was the terminal way of manually trying to bring wlan0 up and down and trying to configure the ssid and so on. The thread on this forum was called **How To: Manual Network Configuration without the need for Network Manager.** 

But I only got as far as bringing it down but when I gave the command to bring it up it said something along the lines of the directory didn't exist. It wasn't worded exactly like that but similar.

I just found the thread. The commands were,

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

I replaced <interface> with wlan0. That was when wireless was showing in Network. I didn't get any errors when I gave the down command. Just when I gave the up command.

Also in the script I uncommented #rmmod ohci_hcd.

And #modprobe ohci_hcd was uncommented although I don't understand those lines and had no idea if it was necessary.

Also didn't understand this line at all.
**sudo update-rc.d ndiswrapper start 99 S 1 2 3 4 5 . stop 99 0 6 .**

Although I appreciate the help I can not believe I'm having to mess around with a script just to use the proprietary drivers. What's blocking the usage of the ndiswrapper drivers? I bet when that is found out there will be no need for a script. Or is there a major bug in the networking or wireless thing in Ubuntu? I think that's what I *might* look in to. I think network connections have always been a bit buggy especially when trying to switch from one access point to another. God I wish I could code. I would completely redo that part. Completely.

EDIT: I was even wondering if my wireless card is something other than wlan0 despite what the terminal says.

---

### Post by Ayuthia on 2008-05-26
It might be possible that there is an error message showing up in dmesg.  I am not sure if you have checked it out or not.  If you haven't can you try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
dmesg
```The information for ndiswrapper should show up at the end of the dmesg results.

---

### Post by psychotux on 2008-05-27
> **cjax1 said:**
> Sorry, one more thing. Before I posted the outputs of the terminal above I had un-blacklisted everything that I had blacklisted before. I hope that the developers aren't deliberately making it very hard to install proprietary drivers trying to push their own reverse engineered drivers. I know they work very hard at this and it actually works pretty good but it's just not quite fast enough especially for a streaming video channel I watch. Also some pages do load a little slower. The biggest deal is the streaming video. I guess I could look for a card that comes with native Linux drivers. It's just that my card works very well with ndiswrapper but it seems each release I try it keeps getting harder and harder to get ndiswrapper working. I would think it should get better not harder. There's a couple other distros that I can still use ndiswrapper with no problem. And I did not like the fact that the 8.04 upgrade killed the ndiswrapper driver that was already installed. I keep wondering why that is. OK, I'm done. I didn't do this just to bump up this thread. I still love Ubuntu but I can't keep dealing with this each time.


I agree this is why I've chased around different Distro's on countless releases.
Time and Time again.

I even went back to Winblows for awhile, I just plud got sick of it.
Mine started with Dapper which I helped test on up, On a different Desktop then I have now.
So I decided to get me a Dell Vostro 1000 Laptop in the hopes I could start to fool around with Linux again, I don't mind Tweaking because even in Winblows you do a certain amount to get it all working the way you want/need.

But this constent ](*,) gets tiring....
I realize no OS is perfect but you'd think this goes for Winblows too, they'd make sure the fix in one wouldn't have to be redone in the next release...

Like you don't get me wrong I "LOVE" Linux and Ubuntu but it does get to be a headache afterall....

I could turn my Desktop into Linux and the Laptop into Windows, but can't for business reasons.
But there's a catch there to, Even the wireless on my desktop doesn't work in Ubuntu... :mad:

I didn't do this to start a war....  It's just a rant...

---

### Post by cjax1 on 2008-05-27
Man I hear you psychotux. I'm not going back to Windows and thankfully I don't need Windows for business reasons. I'm glad I'm not the only one thinking the same thing. :)

Ayuthia, I ran dmesg according to your post. 
Here's the output. I only pasted the last part that seemed to be relevant to ndiswrapper otherwise this post would be a mile long. I'm still looking through it and see there is some problem/s but don't know what it all means. Maybe you or some one else does.

[   24.497540] EXT3 FS on sdb3, internal journal
[   25.233514] VFS: Can't find ext3 filesystem on dev sdb1.
[   25.729049] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.152556] NET: Registered protocol family 17
[   27.416894] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[   27.420470] usbcore: deregistering interface driver ndiswrapper
[   27.442650] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.476932] ndiswrapper: driver bcmwl5 (Motorola,03/22/2004, 3.60.7.0) loaded
[   27.477151] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.484273] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: e0478779
[   27.484277] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[   27.484359] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   27.484364] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   27.484375] ndiswrapper (mp_halt:259): device dd378480 is not initialized - not halting
[   27.484378] ndiswrapper: device eth%d removed
[   27.484388] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[   27.484405] ndiswrapper: probe of 0000:03:01.0 failed with error -22
[   27.486023] usbcore: registered new interface driver ndiswrapper
[   27.528825] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.550929] ssb: Sonics Silicon Backplane found on PCI device 0000:03:01.0
[   27.586922] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.708087] usb-storage: device scan complete
[   27.712453] scsi 4:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.00 PQ: 0 ANSI: 0
[   27.715815] scsi 4:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.00 PQ: 0 ANSI: 0
[   27.719562] scsi 4:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.00 PQ: 0 ANSI: 0
[   27.724071] scsi 4:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.00 PQ: 0 ANSI: 0
[   27.729989] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   27.730060] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   27.735363] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   27.735431] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   27.740072] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   27.740133] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   27.798545] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   27.798615] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   28.119974] No dock devices found.
[   29.224432] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.224440] apm: disabled - APM is not SMP safe.
[   29.383487] ppdev: user-space parallel port driver
[   29.502782] audit(1211863988.821:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5127 profile="/usr/sbin/cupsd" namespace="default"
[   31.562200] Bluetooth: Core ver 2.11
[   31.563024] NET: Registered protocol family 31
[   31.563031] Bluetooth: HCI device and connection manager initialized
[   31.563037] Bluetooth: HCI socket layer initialized
[   31.580350] Bluetooth: L2CAP ver 2.9
[   31.580356] Bluetooth: L2CAP socket layer initialized
[   31.624282] Bluetooth: RFCOMM socket layer initialized
[   31.624300] Bluetooth: RFCOMM TTY layer initialized
[   31.624304] Bluetooth: RFCOMM ver 1.8
[   34.048030] [drm] Initialized drm 1.1.0 20060810
[   34.051901] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.051913] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   34.052022] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.073779] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[   34.082090] usbcore: deregistering interface driver ndiswrapper
[   34.083581] ndiswrapper (ntoskernel_exit:2708): object df1a4f20(2) was not freed, freeing it now
[   34.112845] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.127373] ndiswrapper: driver bcmwl5 (Motorola,03/22/2004, 3.60.7.0) loaded
[   34.128670] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.136104] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: e0604779
[   34.136110] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[   34.136213] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   34.136219] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   34.136233] ndiswrapper (mp_halt:259): device dda71480 is not initialized - not halting
[   34.136236] ndiswrapper: device eth%d removed
[   34.136249] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[   34.136269] ndiswrapper: probe of 0000:03:01.0 failed with error -22
[   34.146483] usbcore: registered new interface driver ndiswrapper
[   34.173473] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.196699] ssb: Sonics Silicon Backplane found on PCI device 0000:03:01.0
[   34.207477] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.744048] NET: Registered protocol family 10
[   40.744524] lo: Disabled Privacy Extensions
[   40.745283] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   96.418207] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[   96.473440] usbcore: deregistering interface driver ndiswrapper
[   96.474910] ndiswrapper (ntoskernel_exit:2708): object deb0a120(2) was not freed, freeing it now
[  128.845338] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  128.859766] ndiswrapper: driver bcmwl5 (Motorola,03/22/2004, 3.60.7.0) loaded
[  128.860053] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[  128.867483] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: e0636779
[  128.867491] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10e
[  128.867636] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  128.867645] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  128.867663] ndiswrapper (mp_halt:259): device de850480 is not initialized - not halting
[  128.867669] ndiswrapper: device eth%d removed
[  128.867683] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[  128.867706] ndiswrapper: probe of 0000:03:01.0 failed with error -22
[  128.869741] usbcore: registered new interface driver ndiswrapper
chris@hardy-desktop1:~$ 


I don't know why it says device eth%d removed nor do I know what error -22 is. PCI interrupt for device 0000:03:01.0 disabled? I made no changes to hardware if that's what that means.

Whatever.

---

### Post by bluefrog on 2008-05-27
it says "ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (".

Are you sure to use the right windows driver? (try the xp one not the vista one).

---

### Post by cjax1 on 2008-05-27
Disregard the last dmesg output. I temporarily deleted bluefrog's script. BTW bluefrog, the last modprobe line was misspelled. But even after fixing it wireless still did not work. I got a totally different dmesg output after deleting the script and un-blacklisting b43 and rebooting. I was going to post the new dmesg output but I got the wireless working after running by typing

```
sudo ifdown wlan0
sudo ifup wlan0
```

I thought wow. But after a reboot those commands did not work. So my brain fired back up. I did numerous things like blacklisting b43legacy and ssb and so on. Nothing. I don't know how many time I rebooted after trying one change after another. But here's what I got it boiled down to.

b43 can not be blacklisted otherwise the wireless connection just isn't there and no other commands will work at all. the wireless connection will not show in Network.

The blacklist file is back to defaults. There is still an entry in /etc/modules for ndiswrapper but not sure if that's doing anything. I didn't try taking out that entry.

Two of the lines ayuthia gave me have to be run before ifdown and up are run. with all the above said here's what gets wireless going.

```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifdown wlan0
sudo ifup wlan0
```

Those four have to be run after booting. bluefrog's script is not in place and /etc/modprobe.d/blacklist is back to default.

The first line in the code above has to have ndiswrapper included. I'm assuming it would not have to be included if I did not have an entry for ndiswrapper in the /etc/modules file.

So, can anyone tell me what's still wrong? After rebooting I have to run those commands to get wireless back up. Maybe I can modify bluefrogs script to run just those commands?

---

### Post by cjax1 on 2008-05-27
Turns out only the first two lines are needed to get the wireless going.

```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
```

Blacklisting b43legacy and ssb in /etc/modprobe.d/blacklist doesn't do anything. Still have to run those two commands.

---

### Post by kevdog on 2008-05-27
Ok great work, you've done all the hardwork, and no what modules to unload, and then what to reload.  To make things stick across reboot, your going to customize the ndiswrapper modprobe statement, in order to basically boil this thing down to one line. 

```

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
``` 

So basically this adds the following to the /etc/modprobe.d/ndiswrapper file (if you already have this file then you either want to delete it or simply delete everything prior to running the above command.  After running the above command it should look like the following:

#Hardy ssb/ndiswrapper workaround, added <date>
install ndiswrapper 
modprobe -r b43 b44 b43legacy ssb;
modprobe --ignore-install ndiswrapper $CMDLINE_OPTS;
modprobe ssb;
modprobe b44;

Basically now everytime you type (or the system uses the command):
sudo modprobe ndiswrapper 

That entire script is run.  modprobe ndiswrapper is simply now an alias for a series of commands.

I hope that was informative.  Borrowed from Jamie Jackson, who was informed by another user, which information was originally collected from the man modprobe.conf instructions: [http://linux.die.net/man/5/modprobe.conf](http://linux.die.net/man/5/modprobe.conf)

---

### Post by cjax1 on 2008-05-27
Sorry kevdog that didn't work either. I read your post carefully. Tried different things. Googled more. Too worn out about this to list everything. This is nuts. Besides this wireless stuff there's several other things that is really ticking me off. I'm not sure about gnome. I still have to learn a bunch of sh** about udev and why editing fstab doesn't work. I look for GUI's but no. (besides the GUI for GRUB) I still don't like the UUID way of doing things in fstab and menu.lst. I learned how to find the UUID of partitions and edit the files before and learned why they are used, I guess, but still don't like them for certain reasons. Maybe they are better for some people for certain reasons. I know other distros are using the same system and I'll learn more about it but it's not just one or two things with Ubuntu, it's several now.

I didn't like a beta release of FF included with the final release of Ubuntu. Before, unless you knew how to update FF it was several versions behind, now it's just the other extreme. And when I uninstall FF beta and install FF 2.0.0.14 the extensions I've come to rely on no longer work, even though they are made for 2.0.0.14. I do like the new features in FF3 but I'll wait for the final release and for certain extensions to catch up. I've been looking into how extensions are made. Who knows, maybe sometime I'll write my own. :)

I'm not afraid of learning new things and new ways of doing things. I love Linux and won't give up on it. I like getting in deep when required but it seems like I'm hitting one road block after another in this latest Ubuntu release. I'm sure I'll check later releases because I'll always have a special place in my heart for Ubuntu but right now I'm done. I hope Ubuntu stays true to what it's been all the years before. I'm know the developers are excellent at what they do but I just hope they are not rushing things.

Thanks for the help everyone. I can't mark this as solved but there's no reason for anyone else to reply from here on out. I was going to refrain from getting into any more long rants but I just wanted to say I am done and for what reasons. It's not just the reasons I stated above, it's several little things and some big things. It's just too much for me. Maybe I'll check out the next Ubuntu release but I'm done with Ubuntu for now. I'm going to look for something that works for me.

---

