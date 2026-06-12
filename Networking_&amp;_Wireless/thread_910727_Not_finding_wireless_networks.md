---
title: "Not finding wireless networks"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by snkngshps on 2008-09-04
I'm installing hardy on a roommates laptop and I haven't been able to get the wireless to work. We have a wireless router broadcasting and other computers in the house are connected but I haven't been able to find any networks with his laptop. Even by trying to manually type in the network's name, it won't connect. It's a Dell Inspiron 2200, and I've installed and enabled the driver for the Broadcom B43 wireless card. Any ideas?

---

### Post by snkngshps on 2008-09-04
By the way: ```
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```


I've been trying to followed a lot of guides with no luck. Here is the last one I followed: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by nolimit974 on 2008-09-04
use ndiswrapper with the windows drivers.  That is all i had to do to fix it on my cousins compaq.

---

### Post by falcon61102 on 2008-09-04
Check out this site.  It has a good walk through and links to good drivers if you need them.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

If you run into any trouble, post back here and we'll help you through.

---

### Post by pytheas22 on 2008-09-05
Please post the output of these commands:
```

lspci -nn | grep -e broadcom
lshw -C Network
ndiswrapper -l
```

I think that b43 tends not to really support most Airport cards, so that's probably the problem...you probably need to use ndiswrapper or bcm43xx (the older Broadcom native driver).  With the lspci -nn output we can find out for sure.

---

### Post by snkngshps on 2008-09-05
lspci -nn | grep -e broadcom didn't give me any output for some reason..

```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:0c:21:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:1e:04:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

```
 ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
```

---

### Post by falcon61102 on 2008-09-05
See where you ran the ndiswrapper -l command and it's using ssb as an alternate driver.  That may be one of your issues.  To avoid this try:
```
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
```

After you complete that, check if you can access the wireless networks.  If so, then all you need to do is blacklist ssb, which i would recommend doing anyway.  If not, then run:
```
ndiswrapper -l
```
And see if ssb was unloaded.  If it is still present, run the above commands again, blacklist ssb and restart.

---

### Post by rihannaisco on 2008-09-05
try this 
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by snkngshps on 2008-09-05
> **falcon61102 said:**
> See where you ran the ndiswrapper -l command and it's using ssb as an alternate driver.  That may be one of your issues.  To avoid this try:
```
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
```

After you complete that, check if you can access the wireless networks.  If so, then all you need to do is blacklist ssb, which i would recommend doing anyway.  If not, then run:
```
ndiswrapper -l
```
And see if ssb was unloaded.  If it is still present, run the above commands again, blacklist ssb and restart.

I got an error when running "sudo rmmod ssb". "ERROR: Module ssb is in use by b44"

I went ahead and ran the modprobe command but it's still not finding any networks.

---

### Post by falcon61102 on 2008-09-05
Ok, stop that one too:
```
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
```

Then, open up your blacklist file:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And add the following to the end of the file:
```
blacklist b44
blacklist b43
blacklist ssb
```

Finally, reload ndiswrapper:
```
sudo modprobe ndiswrapper
```

---

### Post by snkngshps on 2008-09-05
Ok all commands ran with no errors, blacklist was updated but I am still not seeing any networks :-/

---

### Post by falcon61102 on 2008-09-05
What is the output of:
```
ndiswrapper -l
```

And have you tried restarting?

---

### Post by jimmgunnz on 2008-09-05
i know this is elementary.... but you did set it to roaming mode right??
sorry if that's stupid, but i saw that you tried to manually configure and i didn't see a mention of enabling roaming.
and sometimes it's the littlest things...
i know i didn't do that at first =\

---

### Post by pytheas22 on 2008-09-06
> lspci -nn | grep -e broadcom didn't give me any output for some reason..

Yeah, sorry, I made a typo: the correct command should have been:
```

lspci -nn | grep -i broadcom
```

Please post that, along with the output of all of this (do it after a fresh reboot):

```
sudo rmmod b44
sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
dmesg | grep -e wlan -e ndis
lshw -C Network
iwlist scan
```

I know that's a lot of stuff, but it will be useful to see.  Those commands would kill your ethernet connection; if you need it to post the output here, save the output to a text file, then reboot, and your ethernet should work again, so that you can make a post here.  Otherwise, save the text file onto a USB drive and bring it to another machine to post here.

This is being made extra complicated by the presence of b44, which keeps ssb loaded as a dependency and tends to disobey the blacklist (blacklisting b44 never seems to do anything).  So we're going to have to write a boot script like we did for your other computer a few weeks back, but first let's figure out exactly which steps are necessary to get the card working (hopefully the ones above would make the connection work), then write the script.

There may also be issues with the Windows driver that you loaded into ndiswrapper, because falcon's post #9 should have dealt with the b44 complications, yet apparently it didn't.  The output that I ask you to post above should help to fully diagnose everything that's going wrong.

---

### Post by snkngshps on 2008-09-06
**falcon6110**:
```
:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
```
I did try restarting. Still no luck.

**jimmgunnz**: I actually don't know what roaming mode is. I've installed ubuntu on a few machines now and I've never had to turn anything on roaming mode. If that will help, let me know what I need to do.

**pytheas22**: Oddly enough this didn't kill my ethernet, but also didn't fix the problem. I think probably my biggest problem is that I followed a few guides, which never ended up working and I didn't completely undo all of the steps. I know it's a stupid thing to do, I won't make that mistake again. Here are the outputs:
```
michael@michaelubuntu:~$ lspci -nn | grep -i broadcom
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
michael@michaelubuntu:~$ sudo rmmod b44
[sudo] password for michael: 
michael@michaelubuntu:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
michael@michaelubuntu:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
michael@michaelubuntu:~$ sudo rmmod ssb
michael@michaelubuntu:~$ sudo rmmod ndiswrapper
michael@michaelubuntu:~$ sudo modprobe ndiswrapper
michael@michaelubuntu:~$ sudo ifconfig wlan0 up
michael@michaelubuntu:~$ dmesg | grep -e wlan -e ndis
[   24.793343] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   24.908164] usbcore: registered new interface driver ndiswrapper
[   77.618322] usbcore: deregistering interface driver ndiswrapper
[   29.124773] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   29.186295] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   46.725448] ndiswrapper: using IRQ 19
[   77.962405] wlan0: ethernet device 00:14:a5:0c:21:c1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   77.963260] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   77.963865] usbcore: registered new interface driver ndiswrapper
[   40.006301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  127.506532] ndiswrapper: device wlan0 removed
[  127.506663] usbcore: deregistering interface driver ndiswrapper
[  127.537597] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  340.317958] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  340.329082] ndiswrapper: using IRQ 19
[  340.383393] wlan0: ethernet device 00:14:a5:0c:21:c1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[  340.384257] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  340.384864] usbcore: registered new interface driver ndiswrapper
[  127.618697] ADDRCONF(NETDEV_UP): wlan0: link is not ready
michael@michaelubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:0c:21:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:1e:04:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
michael@michaelubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

michael@michaelubuntu:~$ 
```

---

### Post by pytheas22 on 2008-09-06
From everything that you posted, it looks like ndiswrapper should work correctly--the module loads and it claims the card.  I'm wondering if the Windows driver that you loaded into ndiswrapper has a problem, even though there are no error messages mentioned in dmesg.  Where did you get it from?  If you go to [this page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/") and search for "14E4:4318" (the PCIID of your card), there are several links to drivers that are affirmed as having worked for this particular card.  [This page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") also has instructions specific to your card (again, search by the PCIID).

Please remove the Windows driver that you currently have installed, and try a couple of different ones.

By the way, I don't actually think that b44 is a problem here, so running all of those "rmmod XXX" commands is not necessary.  The ndiswrapper module seems to be loading correctly on its own.  As long as the output of *lshw -C Network* looks like this:
```

  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:0c:21:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=**ndiswrapper+bcmwl5** driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 **module=ndiswrapper** multicast=yes wireless=IEEE 802.11g
```

then you're alright.

Another thing to check is that the wireless is turned on.  It should be, and if it weren't dmesg would probably say so, but if there's a button that you need to press to enable the wireless, make sure it's on.

Please let us know if switching to a different Windows driver makes any difference.

---

### Post by snkngshps on 2008-09-06
I got the windows driver from this thread: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) How do I uninstall that driver?

---

### Post by pytheas22 on 2008-09-06
You can uninstall drivers with "sudo ndiswrapper -r [driver-name]," so in your case:
```

sudo ndiswrapper -r bcmwl5
```

That link that you got the driver from seems to be for Broadcom 4312, but yours is 4318, so it may indeed be the case the you simply need to choose a different Windows driver.

Also, you're not on 64-bit, are you?

---

### Post by snkngshps on 2008-09-06
Ok I uninstalled the one I had originally and I followed the guide you gave me a link to ([this one]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")) but it's still not working. I used step 2C. I read that 2A might work also. Do I need to uninstall the 2C driver first?

---

### Post by Kevbert on 2008-09-06
That post should work.  The only problem is that some Broadcom drivers were updated in July.  If you have no luck you could take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13") as the drivers are newer.

---

### Post by pytheas22 on 2008-09-06
Yes, try 2a.  You'll need to uninstall the existing driver first.

If 2a still doesn't work, please reboot and then post the output of:
```

lsmod | grep ndis
sudo modprobe ndiswrapper
lshw -C Network
iwlist scan
dmesg | grep -e ndis
uname -m
```

---

### Post by snkngshps on 2008-09-06
No luck :-/

```
michael@michaelubuntu:~$ lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146412  5 ndiswrapper,cdc_acm,ehci_hcd,uhci_hcd
michael@michaelubuntu:~$ sudo modprobe ndiswrapper
[sudo] password for michael: 
michael@michaelubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:0c:21:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:1e:04:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
michael@michaelubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

michael@michaelubuntu:~$ dmesg | grep -e ndis
[   24.908889] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   25.017336] usbcore: registered new interface driver ndiswrapper
[   29.262850] usbcore: deregistering interface driver ndiswrapper
[   29.291375] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   33.578170] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   33.586696] ndiswrapper: using IRQ 19
[   78.388309] usbcore: registered new interface driver ndiswrapper
michael@michaelubuntu:~$ uname -m
i686

```

---

### Post by pytheas22 on 2008-09-06
Still no idea why it won't work.  Every indication above suggests that it should.

At this point, the only thing I can think of is to reinstall Ubuntu so that you have a clean slate, then configure ndiswrapper by using step 2a of that tutorial.  Maybe something weird happened in the midst of all of your attempts to get this working.

Also, just to rule out some stupid stuff: you're positive that the wireless card works in Windows, right?  And it's operating on the appropriate frequency for your network (i.e., if the card were only in 11b mode, it wouldn't see 11g networks...you can use *iwconfig* to check which mode it's in, but it should be 11g by default)?

---

### Post by jimmgunnz on 2008-09-06
hey mang... i saw you didn't know what roaming mode was...
and if everything seems to be working then who knows?
when i first tried to connect, i couldn't see any networks at all.
so i wondered what the eff.  when i switched (through manual configuration) to roaming mode, i was able to see all the close networks.  
definitely simple.  
just open manual configuration.
click on wireless connection then click properties.
then just click the little square that says roaming mode.
i would save it as a setting, just as roaming mode, so you can toggle to another manually configured network at another point.
i dunno... like i said, sometimes it's the simplest things...

---

### Post by snkngshps on 2008-09-06
Ok, I did a full reinstall, followed that guide (steps 1, 2A and 3) and it's still not working. Unfortunately I can't verify that the wireless card is working. His computer has been broken for a while. I checked it out and it seemed like all that was wrong was a dead hard drive. I bought a new hard drive and installed Hardy immedeatly, so I haven't had Windows on the machine at all. Last time it was working though he said the wireless was working. I guess it's always the possibility that a broken wi-fi card is the problem. Here are the outputs you requested last. I haven't done a restart yet.. let me know if that needs to be done.

```
michael@michael-ubuntu:~$ lsmod | grep ndis
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
michael@michael-ubuntu:~$ sudo modprobe ndiswrapper
michael@michael-ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:1e:04:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.102 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:0c:21:c1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
michael@michael-ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

michael@michael-ubuntu:~$ dmesg | grep -e ndis
[ 2364.145235] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2364.154767] usbcore: registered new interface driver ndiswrapper
michael@michael-ubuntu:~$ uname -m
i686

```

---

### Post by pytheas22 on 2008-09-06
Restart, then please run this and post all of the output:
```

sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
iwconfig
dmesg | grep -e ndis -e wlan
```

---

### Post by snkngshps on 2008-09-06
```
michael@michael-ubuntu:~$ sudo rmmod b43
[sudo] password for michael: 
michael@michael-ubuntu:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
michael@michael-ubuntu:~$ sudo rmmod ssb
michael@michael-ubuntu:~$ sudo rmmod ndiswrapper
michael@michael-ubuntu:~$ sudo modprobe ndiswrapper
michael@michael-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@michael-ubuntu:~$ dmesg | grep -e ndis -e wlan
[   26.349983] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   26.477148] usbcore: registered new interface driver ndiswrapper
[   61.756321] Modules linked in: ipv6 i915 drm af_packet rfcomm l2cap bluetooth rfkill_input ppdev acpi_cpufreq cpufreq_ondemand cpufreq_powersave cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs dock container sbshc iptable_filter ip_tables x_tables ndiswrapper parport_pc lp parport pcmcia joydev arc4 ecb blkcipher rfkill mac80211 cfg80211 led_class input_polldev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss video output snd_pcm snd_seq_dummy serio_raw snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event yenta_socket rsrc_nonstatic pcmcia_core snd_seq button snd_timer snd_seq_device battery ac snd soundcore intel_agp snd_page_alloc agpgart dcdbas iTCO_wdt iTCO_vendor_support evdev psmouse pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic ata_piix pata_acpi libata scsi_mod e100 mii ssb ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  182.527952] usbcore: deregistering interface driver ndiswrapper
[   69.166392] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  185.217576] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  185.226867] ndiswrapper: using IRQ 19
[  185.247365] wlan0: ethernet device 00:14:a5:0c:21:c1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[  185.247485] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  185.247620] usbcore: registered new interface driver ndiswrapper
[   69.459924] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

(By the way jimmygunz I did make sure roaming mode was enabled)

---

### Post by pytheas22 on 2008-09-06
Alright, and now if you run:
```

iwlist scan; iwlist scan; iwlist scan
```

do you still not see any networks?  If so, if you have another Linux computer around, could you post the "iwlist scan" output on that one, please?  Maybe there's something about the wireless network that's making it impossible to see.

---

### Post by snkngshps on 2008-09-06
No results with the laptop we're working on. This is the output of my laptop:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:DB:17:BD
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by falcon61102 on 2008-09-06
One thing I noticed is that the Module=ssb again.  Did you complete the Hardy fix in the walk through?  If not, try this again:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then run:
```
sudo lshw -C network
```
Check if it still says module=ssb.  If not you should be good.  Check for your access points.

---

### Post by pytheas22 on 2008-09-06
> wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:DB:17:BD
                    ESSID:"linksys"
                    Protocol:**IEEE 802.11b**
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

Aha well that's it!  Your network is broadcasting in 11b mode only, but your card is operating in 11g mode only.  Sorry; we should have thought of this a long time ago.

I'm actually not sure off the top of my head how to force your card to operate in 11g mode (maybe "sudo iwpriv wlan0 mode 11g," but I don't think that's the right), but if you go to your router's configuration page, you should have an option to tell it to operate in 11g mode, or 11b/11g (mixed) mode (provided that your router is not more than three or four years old).  Changing to mixed mode is probably your best option.  Try that; it should work.

I'm on my way out for now but hopefully this will solve the whole problem; I'll be back tomorrow.

You'll also need to write a script to remove the ssb module at boot, but for the time being you can just run those "sudo rmmod XXX" commands after each restart and ndiswrapper will kick in.

---

### Post by snkngshps on 2008-09-07
falcon61102: I didn't run that fix originally. I just tried to run the fix and I got errors on the first two commands so I stopped (ERROR: Module b43 does not exist in /proc/modules and ERROR: Module b44 does not exist in /proc/modules). I didn't want to run any more commands and mess something up since the first couple didn't work. Maybe since I had restarted, I need to run some of the original commands again? One of the frustrating things about following guides is that they list the commands but I don't know what each command is doing. So when something goes wrong I never know what to do to fix it.

pytheas22: Unfortunately my router is super old. It's simply a regular linksys wireless-b so I don't think it can broadcast G at all. I checked the settings to make sure and wasn't able to find and G or mixed options. So I just need to find a command that sets his card to find wireless B instead of G?

everyone: Thanks for the help!!

---

### Post by falcon61102 on 2008-09-07
I forgot to mention that those errors are fine.  Just continue.  You shouldn't have to run any of the original commands.  Run through that fix and ignore any errors from the rmmod commands.  All that is doing is unloading those modules and if they're not loaded you get an error, which is fine because we don't want them loaded.

---

### Post by snkngshps on 2008-09-07
Ok, ran the full fix and checked it and it now has ndiswrapper listed as the module but I still don't see any access points. Do you happen to know the command that pytheas was talking about that would make sure my card is connecting to 11b instead of 11g?

---

### Post by falcon61102 on 2008-09-07
I believe he listed it in his post.  Sorry, that one I don't know.

---

### Post by pytheas22 on 2008-09-07
Try:
```

sudo iwpriv wlan0 mode 11g
```

or if that doesn't work:
```

sudo iwpriv wlan0 mode 2
```

Unfortunately, the commands needed to make an interface operate in a certain mode vary by wireless driver.  I know that "iwpriv" works for the Ralink legacy drivers, but I'm not sure about ndiswrapper.

Also, if you want to write a script so that you don't have to worry about those "rmmod" commands anymore, first open up a blank file with:

sudo gedit /etc/init.d/wifi-fix.sh

Then add to the file these lines:

```
#!/bin/bash

rmmod b43
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
```

Then configure the script to run automatically at boot with:
```

cd /etc/init.d
sudo chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh
```

This should take care of unloading the b43 driver.

Let me know if the iwpriv commands do anything; otherwise I'll google around and see what I can figure out.

---

### Post by snkngshps on 2008-09-07
Neither command worked ("Invalid command: Mode"). Thanks for the script, I have that all set up now. One thing I noticed, shouldn't the command change the mode to 11b instead of 11g? Anyways, let me know if you are able to find how to change it. I've googled around and searched the forums and haven't been able to find anything.

---

### Post by pytheas22 on 2008-09-07
Does this work:
```

sudo iwconfig wlan0 modu 11b
```

(note that that's not a typing mistake; it is 'modu,' not 'mode')

As far as I can tell that's the argument that you're supposed to use with iwconfig to change operating mode.  Hopefully ndiswrapper supports it.

---

### Post by snkngshps on 2008-09-07
```
michael@michael-ubuntu:~$ sudo iwconfig wlan0 modu 11b
[sudo] password for michael: 
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.

```

---

### Post by pytheas22 on 2008-09-07
Alright, last shot:
```

sudo iwpriv wlan0 network_type b
```

If that doesn't work, we may have to go back to trying to use b43 or bcm43xx.

---

### Post by snkngshps on 2008-09-07
```
michael@michael-ubuntu:~$ sudo iwpriv wlan0 network_type b
[sudo] password for michael: 
Interface doesn't accept private ioctl...
network_type (8BF2): Invalid argument

```

:-/

---

### Post by pytheas22 on 2008-09-07
The only thing I can think to do is to switch back to b43.  Probably the reason that it didn't work with b43 in the first place was that, as with ndiswrapper, the card was operating in g mode, but your router is in b.  Perhaps the b43 driver would accept one of the arguments to change mode better than ndiswrapper does.

To go back to b43, you'd want first to open up that script you wrote:

sudo gedit /etc/init.d/wifi-fix.sh

and change it to:
```

#!/bin/bash

#rmmod b43
#rmmod b43legacy
#rmmod ssb
rmmod ndiswrapper
#modprobe ndiswrapper
#ifconfig wlan0 up
```

so that b43 will still be loaded.  Then, after a reboot, what is the output of:
```

dmesg | grep -e b43 -e wlan
iwconfig
```

---

### Post by snkngshps on 2008-09-08
```
michael@michael-ubuntu:~$ dmesg | grep -e b43 -e wlan
[   22.748764] b43-phy0: Broadcom 4318 WLAN found
[   22.792275] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   22.792298] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   36.725607] input: b43-phy0 as /devices/virtual/input/input9
[   27.753752] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   27.753761] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   46.184601] input: b43-phy0 as /devices/virtual/input/input10
[   28.905218] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   28.905227] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   36.893214] input: b43-phy0 as /devices/virtual/input/input11
[   36.952646] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   36.952655] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   46.910426] input: b43-phy0 as /devices/virtual/input/input12
[   46.968005] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   46.968016] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  130.977199] input: b43-phy0 as /devices/virtual/input/input13
[  131.037460] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  131.037476] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   49.492688] input: b43-phy0 as /devices/virtual/input/input14
[   49.555901] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   49.555909] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  139.112841] input: b43-phy0 as /devices/virtual/input/input15
[   52.199978] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   52.199987] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  143.503927] input: b43-phy0 as /devices/virtual/input/input16
[  143.568097] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  143.568114] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  146.422714] input: b43-phy0 as /devices/virtual/input/input17
[   54.928499] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   54.928508] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
michael@michael-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by snkngshps on 2008-09-08
I realized shortly after posting, that when I did the fresh hardy install I never installed the b43 driver again since we were working on ndiswrapper. Here are those commands again after installing b43:

```
michael@michael-ubuntu:~$ dmesg | grep -e b43 -e wlan
[   22.748764] b43-phy0: Broadcom 4318 WLAN found
[   22.792275] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   22.792298] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   36.725607] input: b43-phy0 as /devices/virtual/input/input9
[   27.753752] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   27.753761] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   46.184601] input: b43-phy0 as /devices/virtual/input/input10
[   28.905218] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   28.905227] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   36.893214] input: b43-phy0 as /devices/virtual/input/input11
[   36.952646] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   36.952655] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   46.910426] input: b43-phy0 as /devices/virtual/input/input12
[   46.968005] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   46.968016] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  130.977199] input: b43-phy0 as /devices/virtual/input/input13
[  131.037460] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  131.037476] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   49.492688] input: b43-phy0 as /devices/virtual/input/input14
[   49.555901] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   49.555909] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  139.112841] input: b43-phy0 as /devices/virtual/input/input15
[   52.199978] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   52.199987] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  143.503927] input: b43-phy0 as /devices/virtual/input/input16
[  143.568097] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  143.568114] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  146.422714] input: b43-phy0 as /devices/virtual/input/input17
[   54.928499] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   54.928508] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  201.659704] input: b43-phy0 as /devices/virtual/input/input18
[   75.637682] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   75.637691] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[   91.246257] input: b43-phy0 as /devices/virtual/input/input19
[   91.305133] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   91.305145] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  152.705108] input: b43-phy0 as /devices/virtual/input/input20
[  152.826797] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  152.826807] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  274.937561] input: b43-phy0 as /devices/virtual/input/input21
[  275.161704] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  275.161713] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  396.686815] input: b43-phy0 as /devices/virtual/input/input22
[  396.744106] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  396.744116] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  518.415413] input: b43-phy0 as /devices/virtual/input/input23
[  518.512259] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  518.512269] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  640.124986] input: b43-phy0 as /devices/virtual/input/input24
[  640.240629] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  640.240638] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  761.844645] input: b43-phy0 as /devices/virtual/input/input25
[  761.905813] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  761.905822] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[  883.732539] input: b43-phy0 as /devices/virtual/input/input26
[  883.789872] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  883.789880] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1005.740079] input: b43-phy0 as /devices/virtual/input/input27
[ 1005.837359] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1005.837368] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1128.178493] input: b43-phy0 as /devices/virtual/input/input28
[ 1128.549170] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1128.549179] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1250.066882] input: b43-phy0 as /devices/virtual/input/input29
[ 1250.148146] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1250.148156] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1372.091849] input: b43-phy0 as /devices/virtual/input/input30
[ 1372.149206] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1372.149216] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1494.127827] input: b43-phy0 as /devices/virtual/input/input31
[ 1494.186255] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1494.186267] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1615.963434] input: b43-phy0 as /devices/virtual/input/input32
[ 1616.012747] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1616.012756] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1737.796656] input: b43-phy0 as /devices/virtual/input/input33
[ 1737.842408] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1737.842417] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1859.435855] input: b43-phy0 as /devices/virtual/input/input34
[ 1859.518053] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1859.518062] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 1981.281826] input: b43-phy0 as /devices/virtual/input/input35
[ 1981.785359] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1981.785368] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2103.333090] input: b43-phy0 as /devices/virtual/input/input36
[ 2103.380624] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2103.380631] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2224.324489] input: b43-phy0 as /devices/virtual/input/input37
[ 2224.373814] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2224.373822] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2346.306302] input: b43-phy0 as /devices/virtual/input/input38
[ 2346.352381] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2346.352390] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2468.317466] input: b43-phy0 as /devices/virtual/input/input39
[ 2468.370061] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2468.370070] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2590.139680] input: b43-phy0 as /devices/virtual/input/input40
[ 2590.188833] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2590.188840] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2711.968403] input: b43-phy0 as /devices/virtual/input/input41
[ 2712.013521] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2712.013528] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2833.880795] input: b43-phy0 as /devices/virtual/input/input42
[ 2833.962868] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2833.962877] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 2954.081015] input: b43-phy0 as /devices/virtual/input/input43
[ 2954.200908] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2954.200916] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 3076.143039] input: b43-phy0 as /devices/virtual/input/input44
[ 3076.188393] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 3076.188399] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 3197.861694] input: b43-phy0 as /devices/virtual/input/input45
[ 3197.910300] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 3197.910308] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 3320.244406] input: b43-phy0 as /devices/virtual/input/input46
[ 3320.326671] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 3320.326679] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4).
[ 3440.860599] b43-phy1: Broadcom 4318 WLAN found
[ 3440.904290] b43-phy1 debug: Found PHY: Analog 3, Type 2, Revision 7
[ 3440.904312] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[ 3441.108124] printing eip: c031b43b *pde = 00000000 
[ 3441.108134] Modules linked in: binfmt_misc af_packet ipv6 i915 drm rfcomm l2cap bluetooth rfkill_input ppdev acpi_cpufreq cpufreq_ondemand cpufreq_powersave cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace sbs dock container sbshc iptable_filter ip_tables x_tables ndiswrapper parport_pc lp parport pcmcia joydev arc4 ecb blkcipher b43 rfkill mac80211 cfg80211 led_class input_polldev snd_intel8x0 snd_ac97_codec yenta_socket rsrc_nonstatic ac97_bus snd_pcm_oss snd_mixer_oss pcmcia_core snd_pcm snd_seq_dummy video output snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event serio_raw snd_seq battery button snd_timer snd_seq_device ac snd soundcore intel_agp snd_page_alloc agpgart iTCO_wdt iTCO_vendor_support dcdbas evdev psmouse pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic ata_piix pata_acpi libata scsi_mod e100 mii ssb ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 3441.108200] EIP: 0060:[<c031b43b>] EFLAGS: 00010246 CPU: 0
[ 3441.108246]  [<e03e3d54>] b43_rfkill_poll+0x24/0xf0 [b43]
[ 3441.108402] EIP: [<c031b43b>] mutex_lock+0xb/0x20 SS:ESP 0068:de275f54
[ 3441.970692] input: b43-phy1 as /devices/virtual/input/input47
[ 3442.174543] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 3444.243200] b43-phy1 debug: Chip initialized
[ 3444.243459] b43-phy1 debug: 32-bit DMA initialized
[ 3444.261591] Registered led device: b43-phy1:tx
[ 3444.261612] Registered led device: b43-phy1:rx
[ 3444.261633] Registered led device: b43-phy1:radio
[ 3444.261668] b43-phy1 debug: Wireless interface started
[ 3444.261672] b43-phy1 debug: Adding Interface type 2
[ 3444.262114] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3444.312880] b43-phy1 debug: Removing Interface type 2
[ 3444.349074] b43-phy1 debug: Wireless interface stopped
[ 3444.349171] b43-phy1 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[ 3444.349224] b43-phy1 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[ 3444.356842] b43-phy1 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[ 3444.364898] b43-phy1 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[ 3444.372820] b43-phy1 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[ 3444.380810] b43-phy1 debug: DMA-32 0x0220 (TX) max used slots: 0/128
[ 3444.388803] b43-phy1 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[ 3444.427275] input: b43-phy1 as /devices/virtual/input/input48
[ 3444.555941] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 3446.384549] b43-phy1 debug: Chip initialized
[ 3446.384811] b43-phy1 debug: 32-bit DMA initialized
[ 3446.417129] Registered led device: b43-phy1:tx
[ 3446.417152] Registered led device: b43-phy1:rx
[ 3446.417174] Registered led device: b43-phy1:radio
[ 3446.417211] b43-phy1 debug: Wireless interface started
[ 3446.417215] b43-phy1 debug: Adding Interface type 2
[ 3446.417656] ADDRCONF(NETDEV_UP): wlan0: link is not ready
michael@michael-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by pytheas22 on 2008-09-08
Alright, now that b43 is working again, let's try using those commands to change the mode...hopefully b43 will support one of them:
```

sudo iwconfig wlan0 modu 11b
sudo iwpriv wlan0 mode 11b
sudo iwpriv wlan0 mode 2
sudo iwpriv wlan0 network_type b
```

Does any of those commands run without an error?  If not, trying to use bcm43xx is going to be the last resort, beyond getting a new router...

---

### Post by gerryl7 on 2008-09-08
without reading the entire post have you seen

_https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions

---

### Post by snkngshps on 2008-09-08
no luck:

```
michael@michael-ubuntu:~$ sudo iwconfig wlan0 modu llb
[sudo] password for michael: 
Error for wireless request "Set Modulation" (8B2F) :
    invalid argument "llb".
michael@michael-ubuntu:~$ sudo iwpriv wlan0 mode 11b
wlan0     no private ioctls.

michael@michael-ubuntu:~$ sudo iwpriv wlan mode2
wlan      no private ioctls.

michael@michael-ubuntu:~$ sudo iwpriv wlan mode 2
wlan      no private ioctls.

michael@michael-ubuntu:~$ sudo iwpriv wlan network_type b
wlan      no private ioctls.

michael@michael-ubuntu:~$ 

```

---

### Post by snkngshps on 2008-09-08
> **gerryl7 said:**
> without reading the entire post have you seen

_https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions

Yeah I tried that. Thanks though!!!

---

### Post by pytheas22 on 2008-09-08
Alright, the last thing I can think to try then is to install bcm43xx by running:

echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install bcm43xx-fwcutter

(when you're asked if you want to download firmware automatically, say yes)

Reboot, and please post the output of:

```
iwconfig
dmesg | grep -e bcm -e eth1
lshw -C Network
sudo iwconfig wlan0 modu 11b
sudo iwpriv wlan0 mode 11b
sudo iwpriv wlan0 mode 2
sudo iwpriv wlan0 network_type b
```

And you're absolutely sure that your router can't broadcast in anything besides b mode, right?  Can you upgrade it to support g mode by updating the firmware?  What is the model of the router?

---

### Post by snkngshps on 2008-09-08
```
michael@michael-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

michael@michael-ubuntu:~$ dmesg | grep -e bcm -e eth1
michael@michael-ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:1e:04:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.102 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
michael@michael-ubuntu:~$ sudo iwconfig wlan0 modu 11b
[sudo] password for michael: 
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; No such device.
michael@michael-ubuntu:~$ sudo iwpriv wlan0 mode 11b
wlan0     no private ioctls.

michael@michael-ubuntu:~$ sudo iwpriv wlan0 mode 2
wlan0     no private ioctls.

michael@michael-ubuntu:~$ sudo iwpriv wlan0 network_type b
wlan0     no private ioctls.

```

I'm 99% sure it only broadcasts in B. It's a Linksys BEFW1154 and it's super old. If nothing else, my girlfriend has a wireless G router and next time I'm at her place I can test the laptop on her router. If it works then we'll just get a new router.

---

### Post by snkngshps on 2008-09-08
*BEFW11S4 (not 54)

---

### Post by pytheas22 on 2008-09-08
The card is still using b43 for some reason.  Please run this and post output:
```

sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo modprobe bcm43xx
sudo ifconfig eth1 up
iwconfig
dmesg | grep -e bcm -e eth1
sudo iwconfig wlan0 modu 11b
sudo iwpriv wlan0 mode 11b
sudo iwpriv wlan0 mode 2
sudo iwpriv wlan0 network_type b
```

---

### Post by snkngshps on 2008-09-08
```
michael@michael-ubuntu:~$ sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
[sudo] password for michael: 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

#blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ndiswrapper
michael@michael-ubuntu:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
michael@michael-ubuntu:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
michael@michael-ubuntu:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
michael@michael-ubuntu:~$ sudo rmmod ssb
michael@michael-ubuntu:~$ sudo modprobe bcm43xx
michael@michael-ubuntu:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
michael@michael-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@michael-ubuntu:~$ dmesg | grep -e bcm -e eth1
[  533.784725] bcm43xx driver
[  200.098111] udev: renamed network interface eth1 to wlan0
[  200.295972] bcm43xx: Radio disabled by hardware
michael@michael-ubuntu:~$ sudo iwconfig wlan0 modu 11b
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.
michael@michael-ubuntu:~$ sudo iwpriv wlan0 mode 2
Invalid command : mode
michael@michael-ubuntu:~$ sudo iwpriv wlan0 network_type b
Invalid command : network_type

```

---

### Post by pytheas22 on 2008-09-08
I'm encouraged by the fact that iwconfig reads:
```

wlan0     IEEE **802.11b/g**  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

b/g is better than just g.

Also, it looks like the wireless card is turned off by a physical switch, according to dmesg:
```

[  200.295972] bcm43xx: Radio disabled by hardware
```

Make sure the switch is on, and also run:
```

sudo ifconfig wlan0 up
sudo iwpriv wlan0 mode 11b

```

to make sure the interface is up and to try switching the radio mode again.  Then try scanning with:
```

iwlist scan
```

Any luck?

---

### Post by snkngshps on 2008-09-08
To turn on/off the wireless card you hit "Fn F2" but I've tried that and then tried running dmesg and it still says it's turned off. Maybe it's a hardware issue after all? 

```
michael@michael-ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for michael: 
michael@michael-ubuntu:~$ sudo iwpriv wlan0 mode 11b
Invalid command : mode
michael@michael-ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

michael@michael-ubuntu:~$ dmesg | grep -e bcm -e eth1
[  533.784725] bcm43xx driver
[  200.098111] udev: renamed network interface eth1 to wlan0
[  200.295972] bcm43xx: Radio disabled by hardware
michael@michael-ubuntu:~$ dmesg | grep -e bcm -e eth1
[  533.784725] bcm43xx driver
[  200.098111] udev: renamed network interface eth1 to wlan0
[  200.295972] bcm43xx: Radio disabled by hardware
michael@michael-ubuntu:~$ 

```

---

### Post by pytheas22 on 2008-09-08
That's strange that you can't turn the card on.  Did you try it several times and look at the output of 'dmesg' and 'iwlist scan' after each try?

I guess the only way to know for sure whether it's hardware failure is to bring the laptop somewhere where there's an 11g connection.

---

### Post by snkngshps on 2008-09-09
Yeah I tried it a few times. I know on my laptop there is a little "Wi-Fi" light that lights up when the card is turned on and turns off when the card is off. Unfortunately his computer is a little bit older and doesn't have that light but I've tried turning it off/on and checking to no avail. I will test it on a G network when I get a chance. Is there anything I need to do to get it set up for G or should it be good to go?

---

### Post by lilmale1 on 2008-09-09
i'm also having a similar problem
can someone help
i use wifi radar.
now I only show one network when I turned of the computer from the back swith today.

it doen't even show me all networks. just one call ssid
wich i know isn't one i've seen before

---

### Post by lilmale1 on 2008-09-09
i can tell you how to start from scratch and fix your computer
just let me know what driver are u using does it have a inf file
for linux, which is the same file u can use for hardy

let me know mean while i try fixing my own connection i posted something from scratch here [http://ubuntuforums.org/showthread.php?t=915169](http://ubuntuforums.org/showthread.php?t=915169) 

just star by adding your ubuntu cd to your computer first
and putting first then do this

you have to install build essential to get ndiswrapper

by typing after you got your cd in the laptop

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

then the rest is int that web. if your run into some problem let me know

---

### Post by lilmale1 on 2008-09-09
also to let you know. don't worry about the same command you were using because wifi radar does all that for you and you can just connect to your network. let me know if you need detail info for installing the right driver. my computer just doesn't work cuz i turn off by the back swith. but was working.

---

### Post by lilmale1 on 2008-09-09
im writing as i read your thread because you wifi card wont turn on till you install ur driver then try swithing it on.
let me know bye

---

### Post by lilmale1 on 2008-09-09
[http://www.bioticaindia.com/bcm4312.html](http://www.bioticaindia.com/bcm4312.html)

thats the driver u should get unix driver will work on ubuntu

---

### Post by pytheas22 on 2008-09-09
> Yeah I tried it a few times. I know on my laptop there is a little "Wi-Fi" light that lights up when the card is turned on and turns off when the card is off. Unfortunately his computer is a little bit older and doesn't have that light but I've tried turning it off/on and checking to no avail. I will test it on a G network when I get a chance. Is there anything I need to do to get it set up for G or should it be good to go?

Right now the laptop should still be running under bcm43xx, but I think it's best to try it under ndiswrapper, since at least with ndiswrapper dmesg didn't mention that error about radio being disabled (in other words, it might only be when the card is running under bcm43xx that there's the radio problem, although not necessarily).  To switch things back to ndiswrapper, run:
```

sudo sed 's/blacklist ndiswrapper/blacklist bcm43xx/g' /etc/modprobe.d/blacklist
```

Then, after you reboot in a place where an 11g network is available, run these commands to make sure that ndiswrapper will work:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

That should enable ndiswrapper (you can look at *lshw -C Network* to check) and allow you to scan for networks using the GUI or the *iwlist scan* command (iwlist is probably best; if at first it returns nothing, try running a few times more).

Please let us know if the laptop is able to see 11g networks.
> 
[http://www.bioticaindia.com/bcm4312.html](http://www.bioticaindia.com/bcm4312.html)

thats the driver u should get unix driver will work on ubuntu

I don't think the problem is with drivers.  We've already gotten the interface to come up and appear to be working under three different drivers (ndiswrapper, bcm43xx and b43).  I think the problem has to do with the card's ability to see 11b networks and/or the radio being physically disabled (which could be a driver issue, but since it occurs with each of the three different drivers, I'm inclined to believe that it has to do with hardware more than software--so I don't think that trying a fourth driver is going to help, as far as I can see).

Also, it's generally not a good idea to install drivers from random untrusted websites (where did you find that site?) unless you like spyware etc.

---

### Post by snkngshps on 2008-09-24
I tried getting on a G network and there was still no luck. It just doesn't see any networks. For some reason I'm not convinced that it's a hardware failure. The computer was used a year ago and the wireless worked. Eventually the hard drive failed and he stopped using it. I helped him replace the hard drive and instead of putting on Windows we just put on Ubuntu instead. I guess it's possible that through its time of unuse that wireless card could have died also, but I have a feeling I just haven't set up something correctly. Can you think of any other ways that could test this card? I've never tried to install windows on a machine only running linux but how difficult would it be to set up a small partition and install XP on it?

---

### Post by pytheas22 on 2008-09-25
Yes, I doubt that the hardware is broken as well--it doesn't seem very likely that it would just break from sitting around unused.

What I think might be happening is that the radio was turned off via Windows, and none of the Linux drivers is able to turn it back on.  I've seen this before (for the latest example, read through the posts by sagesparrow on the last couple pages of [this thread]("http://ubuntuforums.org/showthread.php?p=5561757") that I was involved in earlier today--this user seems to have the problem where the card won't work in Ubuntu if the radio gets disabled in Windows).

I can't really think of anything else to do on Ubuntu's end to try to make the card work--we tried everything already, as far as I can tell.  So as you suggest, perhaps the last thing to try is to install Windows on this laptop.

Installing Windows with Ubuntu already installed is difficult, because Windows will not play nicely and will overwrite the boot record, etc.  But it's not really that hard to do if you follow instructions; [these]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") are good ones.

If you get Windows installed, see if the card works there, of course, and try rebooting without disabling the radio or anything.  Does it work in Ubuntu then?

If I can think of anything else that you might try in Linux, I'll post, but I really don't know what else to say other than to see if it works in Windows.

---

