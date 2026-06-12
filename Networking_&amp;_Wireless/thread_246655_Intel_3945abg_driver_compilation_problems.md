---
title: "Intel 3945abg driver compilation problems"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by loopjeremyloop on 2006-08-29
Originally posted in the HowTO: Network Manager w/ WPA thread at 
[http://www.ubuntuforums.org/showthread.php?p=1437785#post1437785](http://www.ubuntuforums.org/showthread.php?p=1437785#post1437785))


okay, i am completely at a loss here.

i have an intel 3945abg, and I have followed every guide I can find - and not only has NOTHING gotten wpa to work, but this guide has now completely removed my wireless card from my system.

I run lsmod to make sure that it's not loading, and it's not.  It used to, but... well...

Yeah.

So I downloaded the drivers from [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net) - great.  Unpacked them.  No problem.  Then, I run "make", and I get the following lovely error:

```

jeremy@jeremy-laptop:~/wpa/ipw3945-1.0.12$ make

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
jeremy@jeremy-laptop:~/wpa/ipw3945-1.0.12$

```

So... I've gone from working wireless (albeit no WPA) to no wireless at all and now can't get the drivers to install.

I am on a Dell Lattitude D820 (core duo / smp kernel / ipw3945).

Any ideas?

---

### Post by funchords on 2006-08-29
I think you and I went down the same path.  

I had just installed Dapper on a Dell Inspiron 6000 with the intel 2200BG card.  My next task was getting WPA to work.  I followed the same guide and started getting wrapped around the axel.  I went from no WPA to no wireless.

And then I said, WAIT A FRIGGIN' MINUTE, these drivers were working.  Why am I installing drivers? 

On a hunch, I reinstalled Dapper (to get the installation drivers back).  I then did 

**sudo apt-get install network-manager network-manager-gnome**

after it installed, I rebooted and logged in.  I double-clicked the wireless icon that appeared in the Notification Area, chose my network, and I was prompted for my WPA key.

YMMV since you have the ipw3945 instead of my ipw2200.  I took a gamble and, in my case, it worked out well.

---

### Post by loopjeremyloop on 2006-08-29
interesting.... 

I really, really don't want to go through the installation media again though... maybe i will.

argh.
:)

---

### Post by loopjeremyloop on 2006-08-29
yeah no.  not reinstalling.  I refuse to let this thing win. 


I WILL NOT GIVE IN.



( cue inspirational rocky-esque music )

if it ever boots back up....

---

### Post by loopjeremyloop on 2006-08-29
okay.... here's my dmesg | grep ipw - 

```

[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encodeext
[17179589.064000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encode
[17179589.064000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_wx_get_encode
[17179589.064000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_txb_free
[17179589.064000] ipw3945: Unknown symbol ieee80211_txb_free
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_wx_set_encodeext
[17179589.064000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_wx_get_scan
[17179589.064000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_freq_to_channel
[17179589.064000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_set_geo
[17179589.064000] ipw3945: Unknown symbol ieee80211_set_geo
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_rx
[17179589.064000] ipw3945: Unknown symbol ieee80211_rx
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_get_channel
[17179589.064000] ipw3945: Unknown symbol ieee80211_get_channel
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_channel_to_index
[17179589.064000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_rx_mgt
[17179589.064000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_get_geo
[17179589.064000] ipw3945: Unknown symbol ieee80211_get_geo
[17179589.064000] ipw3945: disagrees about version of symbol free_ieee80211
[17179589.064000] ipw3945: Unknown symbol free_ieee80211
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_tx_frame
[17179589.064000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_is_valid_channel
[17179589.064000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179589.064000] ipw3945: disagrees about version of symbol ieee80211_get_channel_flags
[17179589.064000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179589.064000] ipw3945: disagrees about version of symbol alloc_ieee80211
[17179589.064000] ipw3945: Unknown symbol alloc_ieee80211


```

and here's lshw -C network

```

jeremy@jeremy-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dcfff000-dcffffff irq:3
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:1f:53:2c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.47 duplex=full ip=10.1.10.82 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dcef0000-dcefffff irq:90
jeremy@jeremy-laptop:~$

```

and here's lshw -businfo 

```

Bus info        Device      Class       Description
===================================================
                            system      Latitude D820
                            bus         0JF242
                            memory      BIOS
cpu@0                       processor   Genuine Intel(R) CPU           T2500  @ 2.00GHz
                            memory      L1 cache
                            memory      L2 cache
                            processor   Logical CPU
                            processor   Logical CPU
                            memory      System Memory
                            memory      DIMM DDR Synchronous [empty]
                            memory      DIMM DDR Synchronous 667 MHz (1.5 ns)
cpu@1                       processor   Genuine Intel(R) CPU           T2500  @ 2.00GHz
                            processor   Logical CPU
                            processor   Logical CPU
pci@00:00.0                 bridge      Mobile Memory Controller Hub
pci@00:01.0                 bridge      Mobile PCI Express Graphics Port
pci@01:00.0                 display     nVidia Corporation
pci@00:1b.0                 multimedia  82801G (ICH7 Family) High Definition Audio Controller
pci@00:1c.0                 bridge      82801G (ICH7 Family) PCI Express Port 1
pci@00:1c.1                 bridge      82801G (ICH7 Family) PCI Express Port 2
pci@0c:00.0                 network     Intel Corporation
pci@00:1c.2                 bridge      82801G (ICH7 Family) PCI Express Port 3
pci@09:00.0     eth0        network     NetXtreme BCM5752 Gigabit Ethernet PCI Express
pci@00:1c.3                 bridge      82801G (ICH7 Family) PCI Express Port 4
pci@00:1d.0                 bus         82801G (ICH7 Family) USB UHCI #1
usb@1           usb1        bus         UHCI Host Controller
usb@1:2                     bus         USB hub
pci@00:1d.1                 bus         82801G (ICH7 Family) USB UHCI #2
usb@2           usb2        bus         UHCI Host Controller
usb@2:1                     bus         USB hub
usb@2:1.2                   generic     O2Micro CCID SC Reader
pci@00:1d.2                 bus         82801G (ICH7 Family) USB UHCI #3
usb@3           usb3        bus         UHCI Host Controller
pci@00:1d.3                 bus         82801G (ICH7 Family) USB UHCI #4
usb@4           usb4        bus         UHCI Host Controller
pci@00:1d.7                 bus         82801G (ICH7 Family) USB2 EHCI Controller
usb@5           usb5        bus         EHCI Host Controller
usb@5:8                     bus         USB hub
usb@5:8.1                   bus         Dell USB Keyboard Hub
usb@5:8.1.1                 input       Dell USB Keyboard
usb@5:8.2                   input       Optical USB Mouse
pci@00:1e.0                 bridge      82801 Mobile PCI Bridge
pci@03:01.0                 bridge      O2 Micro, Inc.
pci@03:01.4                 bus         O2 Micro, Inc.
pci@00:1f.0                 bridge      82801GBM (ICH7-M) LPC Interface Bridge
pci@00:1f.2     scsi0       storage     82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE
scsi@0:0.0.0    /dev/sda    disk        ST96023AS
scsi@0:0.0.0,1  /dev/sda1   disk        Linux filesystem partition
scsi@0:0.0.0,2  /dev/sda2   disk        Extended partition
scsi@1:0.0.0    /dev/cdrom  disk        DVD+-RW DW-Q58A
                /dev/cdrom  disk
pci@00:1f.3                 bus         82801G (ICH7 Family) SMBus Controller
                            power       DELL YD62366

```

aaaand so we can see, i think, that somewhere along the lines in one of the howtos, I installed bad drivers.  
how do I get them out of there?

---

### Post by funchords on 2006-08-29
You still have the old ieee80211 mod installed.

Go back to this post ([http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)) and scroll down to/search for the phrase "ieee80211 Subsystem (for any driver)" and do that.

If you already did that, or part of that (The remove-old script should have removed the old module,) you could do **sudo modprobe -r ieee80211** ...

...word of caution, like you, I did not get through this process successfully.  So, I'm not sure whether this will lead to success for you.

---

### Post by loopjeremyloop on 2006-08-29
yeah, no difference yet.  :(  thank you though, good idea so far.

I have to leave the office, so I'll be thinking about this for an hour or two until I get home and can log back in,  please feel free to chime in on any ideas.

:)

---

### Post by loopjeremyloop on 2006-08-29
update:

well, i decided to just start yanking all the ieee80211 mods i could find, literally rm -rf'ing everything i can get my hands on that looks at me funny... and nothing yet.

(using this thread to track my work and keep my head straight.  if anyone has any ideas, please feel free to share )


](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by loopjeremyloop on 2006-08-29
/lib/modules/2.6.15-26-686/modules.dep
  just went through there, commented out the line loading ieee stuff since it just WON'T GO AWAAAAAAAY

---

### Post by loopjeremyloop on 2006-08-29
hokay.

```

jeremy@jeremy-laptop:~$ dmesg | grep ipw
[17179587.264000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17179587.264000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17179587.264000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17179587.264000] ipw3945: Unknown symbol ieee80211_txb_free
[17179587.264000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17179587.268000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17179587.268000] ipw3945: Unknown symbol escape_essid
[17179587.268000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17179587.268000] ipw3945: Unknown symbol ieee80211_set_geo
[17179587.268000] ipw3945: Unknown symbol ieee80211_rx
[17179587.268000] ipw3945: Unknown symbol ieee80211_get_channel
[17179587.268000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17179587.268000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17179587.268000] ipw3945: Unknown symbol ieee80211_get_geo
[17179587.268000] ipw3945: Unknown symbol free_ieee80211
[17179587.268000] ipw3945: Unknown symbol ieee80211_tx_frame
[17179587.268000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17179587.268000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17179587.268000] ipw3945: Unknown symbol alloc_ieee80211

```

so there's SOME progress kinda.

did a quick google search and found this gem of a french site-
[http://alionet.org/lofiversion/index.php/t10876.html](http://alionet.org/lofiversion/index.php/t10876.html)

and i know exactly 2 french words... but i'm kinda getting the idea, reading it, that the driver still needs to be installed.

check this out - 
```

jeremy@jeremy-laptop:~$ sudo modprobe ipw3945
FATAL: Error inserting ipw3945 (/lib/modules/2.6.15-26-686/kernel/drivers/net/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2006-08-29 20:21:00: ERROR: opening /sys/bus/pci/drivers/ipw3945:
No such file or directory (2)
2006-08-29 20:21:00: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
FATAL: Error running install command for ipw3945
jeremy@jeremy-laptop:~$

```

now, i KNOW the driver DID work before I started trying to get WPA to work... so what's changed?  I wonder if the driver was included directly in the kernel already, and that my ipw3945 module is conflicting.... and i think that maybe the driver compile / install really did get screwed up... so...

so, off to delete the module altogether, depmod, and reboot.

---

### Post by loopjeremyloop on 2006-08-29
OKAY

new things I've done.

```

sudo apt-get --reinstall install network-manager network-manager-gnome

sudo make clean

sudo make check_old

sudo make

sudo make install

```

no errors this time.  be back sooner or later, reeeeebooting.  :D

---

### Post by loopjeremyloop on 2006-08-29
oookay.  now it's still not working, but there are no errors in dmesg at all - so that's a start.

i depmod'd and ensured that the ipw driver was installed and all, but it's not loading - I think I need to install the ieee80211 thing next.  we'll see.  

:)  gettin' there!

---

### Post by loopjeremyloop on 2006-08-29
yeah i'm stuck. not a damn thing happening now.  i'm out of ideas. 


i refuse to reinstall.  someone has to know what to do here...

---

### Post by Andrew Olney on 2006-08-30
I borked my ipw3945 driver that came with 6.06 by trying to build the latest drivers (and the associated ieee module).

I started with something that almost worked and ended up with something that didn't even recognize my wireless hardware anymore.

What I did was to back out of that kernel. I booted into an old kernel, lauched synaptic, and then uninstalled the latest kernel that I had been using. Most importantly, I removed the restricted-modules package that went along with that kernel. Then I rebooted, and reinstalled what I had just uninstalled. This reloaded all of the proprietary drivers.

If you want to back out and regain the functionality that you've lost, this may be useful

---

### Post by loopjeremyloop on 2006-08-30
okay - this is a good last resort, thanks Andrew Olney.

I'll try that when all else fails - looks like it should return me to where i was, anyway.  We'll see.  

right now though, I am going to try the steps as listed in this post - [http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196](http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196) as suggested by Jeff250 in the other thread.

---

### Post by loopjeremyloop on 2006-08-30
OKAY

so that worked, at least to get me back to where I was.  Of course, now eth0 (wired) isn't picking up dhcp addresses automatically anymore (remedied with sudo dhclient3 eth0, but still - next on the fixing list).

next to try recompiling and installing the driver again.  :)  we'll see how that goes... this time I am skipping the IEEE80211 driver.

---

### Post by loopjeremyloop on 2006-08-30
okay


it seems to work.

except.

the network manager is fighting with the old network control, looks like.  :/  how do i tell the old network-admin to back the heck off?

---

### Post by funchords on 2006-08-30
I don't remember having this problem, exactly.  Does the old Network Monitor still come up after a reboot?  If so, then you can remove it.

The Network Monitor is a seperate applet/utility that you can remove from a gnome panel.  The NetworkManager is not a gnome applet, and you can't remove it from the toolbar in the same way as you can an applet.  This is because NetworkManager displays itself in the Notification Area (which you don't want to remove).

---

### Post by Pdj79 on 2006-08-31
I was going through all the same troubles as you.  Then I followed the instructions to reinstall the linux headers and kernel and reboot.  From there, I skipped installing new ieee80211 drivers and the ipw3945 drivers and just continued following the howto on setting up NetworkManager to accept WPA.  I restarted my PC, and I noticed it was recognizing my wifi again (I have a Dell E1505), so I clicked on the NetworkManager app and was surprised to see that it had scanned and located my network and the surrounding networks in my area...clicked on mine, and it asked for my WPA password.  Typed it in, assigned a password for the key, and boom, connected.  So give that a try and see what happens (if you're still having issues).

---

### Post by robinsingh on 2006-09-01
Hi Pdj79 
Can you please provide me the instructions for  re-installing the linux headers and kernel (or point me to some source that has them). I just installed a fresh 606 Ubuntu. I am now getting the error reported initially in this thread...
---------------------------------
make

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.

---------------------------------

thanks, 
robin

---

### Post by Pdj79 on 2006-09-03
-robinsingh

First I uninstalled the new ieee80211 files by navigating to the untarred ieee80211 folder and then doing the following in Terminal:

sudo make uninstall

Then open Synaptic, locate, right-click and select reinstall on each of the following:

inux-image-2.6.15-26-[whatever processor you have chosen]
linux-headers-2.6.15-26
linux-headers-2.6.15-26-[whatever processor you have chosen]

This will reinstall the original ieee80211 and ipw3945 drivers.  Then, follow the NetworkManager instructions that this thread references and skip replacing the ieee80211 and ipw3945 drivers and just work on the nm applet installation that follows.  This is how I got it to work...it should work for you as well.

---

### Post by robinsingh on 2006-09-07
hi Pdj79,
Thanks for your helpful suggestion. 
But I only had to follow it partially.
I only reinstalled the kernel and linux headers as suggested below.
> First I uninstalled the new ieee80211 files by navigating to the untarred ieee80211 folder and then doing the following in Terminal:

sudo make uninstall

Then open Synaptic, locate, right-click and select reinstall on each of the following:

inux-image-2.6.15-26-[whatever processor you have chosen]
linux-headers-2.6.15-26
linux-headers-2.6.15-26-[whatever processor you have chosen]

After that, I just went to my Network Admin Utility , 
it was showing my network SSId, I just entered my hexadecimal WEP key and activated my eth1 interface (wireless card Interl 3945) and it worked as-is.

Aint that cool.. :-)
Thanks for your help, 

P.S - Is Network Manager a better tool than NetworkAdmin(*System->Administration->Networking) ?
If YEs, then I can probably follow the NetworkManager setup article to set it up . Please suggest. 

robin

---

### Post by robinsingh on 2006-09-07
hi Pdj79,
Thanks for your helpful suggestion. 
But I only had to follow it partially.
I only reinstalled the kernel and linux headers as suggested below.
> First I uninstalled the new ieee80211 files by navigating to the untarred ieee80211 folder and then doing the following in Terminal:

sudo make uninstall

Then open Synaptic, locate, right-click and select reinstall on each of the following:

inux-image-2.6.15-26-[whatever processor you have chosen]
linux-headers-2.6.15-26
linux-headers-2.6.15-26-[whatever processor you have chosen]

After that, I just went to my Network Admin Utility , 
it was showing my network SSId, I just entered my hexadecimal WEP key and activated my eth1 interface (wireless card Interl 3945) and it worked as-is.

Aint that cool.. :-)
Thanks for your help, 

P.S - Is Network Manager a better tool than NetworkAdmin(It was installed by default with Ubuntu 606 and can be accessed from *System->Administration->Networking) ?
If YEs, then I can probably follow the NetworkManager setup article to set it up . Please suggest. 

robin

---

