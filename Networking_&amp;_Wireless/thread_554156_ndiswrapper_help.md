---
title: "ndiswrapper help"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by ats1080s on 2007-09-18
[  209.316000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  209.316000] usbcore: deregistering interface driver ndiswrapper
[  214.512000] ndiswrapper version 1.47 loaded (smp=yes)
[  214.528000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  214.528000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 9 (level, low) -> IRQ 9
[  214.528000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  214.532000] ndiswrapper: using IRQ 9
[  214.872000] wlan0: ethernet device 00:14:a5:f6:52:13 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[  214.872000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  214.872000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  214.876000] usbcore: registered new interface driver ndiswrapper
[  214.908000] ADDRCONF(NETDEV_UP): eth1: link is not ready


when i modprobe ndiswrapper this is what i get in dmesg and i can never connect.  right when i installed ndiswrapper it worked, but as soon as i restarted, it stopped working.  ive tryied reinstalling and it didnt do anything.

---

### Post by ats1080s on 2007-09-18
bump

---

### Post by kevdog on 2007-09-19
Can you post the following:

ndiswrapper -l
ndiswrapper -v
cat /etc/iftab
cat /etc/network/interfaces

---

### Post by ats1080s on 2007-09-19
root@CIA:/home/adam# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

root@CIA:/home/adam# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

root@CIA:/home/adam# cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:36:a1:5a:bc arp 1
eth1 mac 00:14:a5:f6:52:13 arp 1

root@CIA:/home/adam# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

this is really odd....im at school now and it did connect once to the AP.  i couldnt get to the internet, but it said i was connected.    it got an ip and everything.  heres the dmesg from when that happened:

[  620.148000] usbcore: deregistering interface driver ndiswrapper
[  630.416000] ndiswrapper version 1.47 loaded (smp=yes)
[  630.444000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  630.444000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 9 (level, low) -> IRQ 9
[  630.444000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  630.448000] ndiswrapper: using IRQ 9
[  630.792000] wlan0: ethernet device 00:14:a5:f6:52:13 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[  630.792000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  630.792000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  630.792000] usbcore: registered new interface driver ndiswrapper
[  630.828000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  634.788000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  645.516000] eth1: no IPv6 routers present
[  659.644000] eth0: link up.
[  659.644000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  670.032000] eth0: no IPv6 routers present
[  676.276000] cdrom_pc_intr, write: dev hda: type=d, flags=88
[  676.276000] 
[  676.276000] sector 0, nr/cnr 0/0
[  676.276000] bio 00000000, biotail 00000000, buffer 00000000, data 00000000, len 0
[  676.276000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0xd0). Trying to recover by ending request.
[  680.316000] hda: packet command error: status=0xd0 { Busy }
[  680.316000] ide: failed opcode was: unknown
[  684.116000] eth0: link down.
[  685.520000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  690.436000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  691.092000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
root@CIA:/home/adam# 


also: my boot options are noapic nolapic irqfixup.  that might have something to do with it.  my laptop will not boot without these though.  there is a bios bug with the pci.  see here for my other thread about the bios bug: [http://ubuntuforums.org/showthread.php?t=550150](http://ubuntuforums.org/showthread.php?t=550150)  one last random thing, my cd drive pops up saying i put in a cd about every 10-15 mins even though the tray was never even opened.  im not a complete n00b to linux but ive never had any of this happen before.  other than these problems ubuntu is the best distro ive used and hopefully we can get this figured out because i really like it.

one last thing i forgot: i have a wusb54g v4 wireless adapter which i have NEVER had a problem with in linux (every distro i simply plugged it in and it worked) and that doesnt even work.

---

### Post by kevdog on 2007-09-19
Easy fix --

eth1 is your wireless interface -- but you want to change this to wlan0.

With your /etc/iftab file, change eth1 to wlan0 (need to gksu gedit /etc/iftab).

Back up your /etc/network/interfaces file
sudo cp /etc/network/interfaces /etc/network/interfaces.original

Then edit your interfaces file (gksu gedit /etc/network/interfaces) to have it contain only the following:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Last thing --- reboot, and if you want to run the wireless interface, unplug the network cable at the time of reboot.  Without doing some configuring, you cant run wired and wireless at the same time.

---

### Post by ats1080s on 2007-09-19
getting ready to reboot now...ill let you know how it goes.

SUCESS!!!  at least for now...i connected and and using my wireless conetion right now.  ill let you know after a week if it works or not.  thanks a lot!

but back to the wusb54g v4 wireless adapter, why isnt that working?  and why does my cd drive keep popping up saying i put in a cd when the drive wasnt opened or even accessed?

and something else i was just reminded of: it will randomly insert 3 characters when im typing.  ex: ttthe  this is pretty rare but annoying none the less.


sigh, it didnt last long...its doing the "link is not ready again" but at least all i had to do was rmmod and modprobe ndiswrapper to get it to work

---

### Post by ats1080s on 2007-09-19
wtf...everything was working fine at school and now that im home, it will NOT connect to the AP.  at school we have a linksys with dd-wrt on it and WPA encription.  at home i have a belkin and a linksys both with WPA and cannot connect to EITHER of them...this is perplexing and annoying.

---

### Post by ats1080s on 2007-09-24
its been almost a week and my wireless still works at school but still not at home.  but i think its actually the router.  my friend came over and tried to get on with this winblows laptop and it wouldnt connect either.  guess i got some resetting to do...

---

### Post by kevdog on 2007-09-24
If you want the ndiswrapper module to load at startup without typing the modprobe statement

do the following
echo "ndiswrapper" | sudo tee -a /etc/modules

Try power cycling or hard resetting your router.

---

