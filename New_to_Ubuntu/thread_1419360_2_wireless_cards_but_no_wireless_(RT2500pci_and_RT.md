---
title: "2 wireless cards but no wireless (RT2500pci and RTL8192 usb)"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by hoptimusPrime on 2010-03-01
Hello everybody,

I am using an MSI notebook/netbook which has Karmic installed, and I want to connect wirelessly to the internet.  I have 2 wireless network adapters which I am trying to install.  


Device Manager tells me that the two cards are:


[LIST]
[*]**RTL8192 WLAN Adapter**, which is a usb wireless N (w/g/n, i think..)
[*]**RT2500 802.11g Cardbus/mini-PCI**, which was installed and working on Jaunty when i bought the computer
[/LIST]

When I first got the computer I reinstalled my os and upgraded to Karmic from Jaunty, and my pci wireless card was no longer functioning properly.  I can't remember if I did a wired install, although I think i did.  I've downloaded all possible updates and I still can not enable wireless.  I am now using the 2.6.31-19 kernel


Also, since upgrading, somehow my BIOS will no longer recognize my usb stick as a bootable drive.  And I have no cd/dvd drive to boot from..  So.. for now it seems like I'm stuck using Karmic, which isn't necessarily a bad thing.

I installed ndiswrapper and network manager, and tried to get the usb wireless to work.  I tried the XP drivers for the 8192U and 8192SU chips.  Also, with the pci adapter, I tried 'fooling around' with some driver packages from the realtek website with no luck (I didn't really know what I was doing).  Again, for some reason I can not enable wireless. 

Sorry if I worded that poorly..  in a nutshell, I have no wireless connectivity, only wired.

I will post some outputs of what i get in terminal, and perhaps someone out there can help diagnose the problem

if i type **lsusb** i get:

Bus 001 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. 

this is my wireless N, which shows it is plugged in.  The little green light on the adapter is on and blinking randomly as though it is connected.

if i type **lspci** i get:

02:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

this is my pci wireless G..

typing **dmesg** gives me a large output, but the last few lines say:

r 0
[    5.551730] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.551757] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.554836] 8139too Fast Ethernet driver 0.9.28
[    5.554884]   alloc irq_desc for 18 on node -1
[    5.554887]   alloc kstat_irqs on node -1
[    5.554894] 8139too 0000:02:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.557323] eth0: RealTek RTL8139 at 0xe800, 00:16:17:4e:7b:71, IRQ 18
[    6.598468] PM: Starting manual resume from disk
[    6.598475] PM: Resume from partition 8:5
[    6.598477] PM: Checking hibernation image.
[    6.598758] PM: Resume from disk failed.
[    6.631288] EXT4-fs (sda1): barriers enabled
[    6.662427] kjournald2 starting: pid 338, dev sda1:8, commit interval 5 seconds
[    6.662449] EXT4-fs (sda1): delayed allocation enabled
[    6.662453] EXT4-fs: file extents enabled
[    6.667824] EXT4-fs: mballoc enabled
[    6.667846] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.697203] type=1505 audit(1267483834.224:2): operation="profile_load" pid=361 name=/usr/share/gdm/guest-session/Xsession
[    7.700206] type=1505 audit(1267483834.228:3): operation="profile_load" pid=362 name=/sbin/dhclient3
[    7.700544] type=1505 audit(1267483834.228:4): operation="profile_load" pid=362 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.700729] type=1505 audit(1267483834.228:5): operation="profile_load" pid=362 name=/usr/lib/connman/scripts/dhclient-script
[    7.793383] type=1505 audit(1267483834.320:6): operation="profile_load" pid=363 name=/usr/bin/evince
[    7.799026] type=1505 audit(1267483834.324:7): operation="profile_load" pid=363 name=/usr/bin/evince-previewer
[    7.802465] type=1505 audit(1267483834.328:8): operation="profile_load" pid=363 name=/usr/bin/evince-thumbnailer
[    7.828439] type=1505 audit(1267483834.356:9): operation="profile_load" pid=365 name=/usr/lib/cups/backend/cups-pdf
[   23.849120] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k 
[   24.339843] EXT4-fs (sda1): internal journal on sda1:8
[   24.541056] udev: starting version 147
[   25.721863] msi-laptop: Identified laptop model 'MSI S270'.
[   25.776039] msi-laptop: driver 0.5 successfully loaded.
[   25.822408] lp: driver loaded but no devices found
[   26.304113] Disabling lock debugging due to kernel taint
[   26.309766] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   26.361069] psmouse serio2: ID: 10 00 64
[   26.444024] elantech.c: assuming hardware version 1, firmware version 1.33
[   26.492255] elantech.c: Synaptics capabilities query result 0x02, 0x02, 0x64.
[   26.698658] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input6
[   26.998974] cfg80211: Calling CRDA to update world regulatory domain
[   27.010971] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.075757] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.076621] ACPI: I/O resource piix4_smbus [0xc800-0xc807] conflicts with ACPI region SMI0 [0xc800-0xc80e]
[   27.076628] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   27.224059] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   27.252433] cfg80211: World regulatory domain updated:
[   27.252440]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.252444]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.252448]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.252451]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.252454]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.252457]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.557862] ndiswrapper: driver net8192u (Realtek Semiconductor Corp.,06/30/2008,5.1029.0630.2008) loaded
[   27.664851]   alloc irq_desc for 22 on node -1
[   27.664855]   alloc kstat_irqs on node -1
[   27.664863] rt2500pci 0000:02:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.817221] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   28.057526] phy0: Selected rate control algorithm 'minstrel'
[   28.058379] Registered led device: rt2500pci-phy0::radio
[   28.058400] Registered led device: rt2500pci-phy0::quality
[   28.071284] udev: renamed network interface wlan0 to wlan1
[   28.224194] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   28.384696] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   29.384844] wlan0: ethernet device 00:02:72:85:d6:f4 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   29.384881] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   29.384939] usbcore: registered new interface driver ndiswrapper
[   29.477419] ndiswrapper: changing interface name from 'wlan0' to 'wlan5'
[   29.477480] udev: renamed network interface wlan0 to wlan5
[   29.518631] ADDRCONF(NETDEV_UP): wlan5: link is not ready
[   30.124878] __ratelimit: 6 callbacks suppressed
[   30.124883] type=1505 audit(1267483856.652:12): operation="profile_replace" pid=1002 name=/usr/share/gdm/guest-session/Xsession
[   30.127016] type=1505 audit(1267483856.652:13): operation="profile_replace" pid=1003 name=/sbin/dhclient3
[   30.127414] type=1505 audit(1267483856.652:14): operation="profile_replace" pid=1003 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.127619] type=1505 audit(1267483856.652:15): operation="profile_replace" pid=1003 name=/usr/lib/connman/scripts/dhclient-script
[   30.135421] type=1505 audit(1267483856.660:16): operation="profile_replace" pid=1004 name=/usr/bin/evince
[   30.141686] type=1505 audit(1267483856.668:17): operation="profile_replace" pid=1004 name=/usr/bin/evince-previewer
[   30.145682] type=1505 audit(1267483856.672:18): operation="profile_replace" pid=1004 name=/usr/bin/evince-thumbnailer
[   30.153145] type=1505 audit(1267483856.680:19): operation="profile_replace" pid=1006 name=/usr/lib/cups/backend/cups-pdf
[   30.153644] type=1505 audit(1267483856.680:20): operation="profile_replace" pid=1006 name=/usr/sbin/cupsd
[   30.166134] type=1505 audit(1267483856.692:21): operation="profile_replace" pid=1008 name=/usr/sbin/tcpdump
[   30.336290] ADDRCONF(NETDEV_CHANGE): wlan5: link becomes ready
[   32.415839] [drm] Setting GART location based on new memory map
[   32.417006] [drm] Loading R300 Microcode
[   32.417027] [drm] Num pipes: 2
[   32.417034] [drm] writeback test succeeded in 1 usecs
[   33.076255] ppdev: user-space parallel port driver
[   38.084030] eth0: no IPv6 routers present
[   40.936023] wlan5: no IPv6 routers present
[   94.160036] Clocksource tsc unstable (delta = -233309101 ns)

if i type **ndiswrapper -l**:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8192u : driver installed
    device (0BDA:8192) present (alternate driver: r8192s_usb)

if i type **iwconfig**:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Stake's not free any more"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan5     IEEE 802.11g  ESSID:"Stake's not free any more"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:72:85:D4:23   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and finally, if i type **ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:16:17:4e:7b:71  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe4e:7b71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1785071 (1.7 MB)  TX bytes:179004 (179.0 KB)
          Interrupt:18 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan5     Link encap:Ethernet  HWaddr 00:02:72:85:d6:f4  
          inet6 addr: fe80::202:72ff:fe85:d6f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7456 (7.4 KB)  TX bytes:18887 (18.8 KB)

wlan5:avahi Link encap:Ethernet  HWaddr 00:02:72:85:d6:f4  
          inet addr:169.254.11.146  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

If I click Network Manager in the taskbar, it shows the RTL8192 adapter, and another called wlan1, which are both under Wireless Networks.  Below each it says 'wireless is disabled".  If I right-click Network Manager, I can see where it says 'Enable Wireless', but it is grey and not selectable..

If i go to System>Administration>Network, it shows me 2 Wireless connections: wlan1 and wlan5.  If I enter my SSID and key, it still does not connect and I can not enable wireless..


Anyways, thats all I can think of for now.
I know this is a very long post, and it probably doesn't even make any sense..

I would be so grateful for and feedback or suggestions, I've been working on this every day for weeks, I just dont know much about linux.

Thanks!

---

### Post by cariboo on 2010-03-02
It looks like the driver is loaded for the internal wireless device. I would suggest getting one device to work at a time.

It looks like becuase you are trying to setup all three network devices at once, avahi is giving the internal device a null ip address

---

### Post by hoptimusPrime on 2010-03-02
Thank you for replying!

I'm not sure if I undestand completely,

My wired ethernet is already set up and seems to be working fine.  So you're saying maybe one or both of the wireless adapters are conflicting with the ip for the ehternet?

I'm not sure how to go about fixing that.  I started by uninstalling the windows driver for the RTL8192 in ndiswrapper.  Now it should just be the pci driver and my wired connection.

Do I need to configure the driver or enable it somehow?  Or do I have to manually assign each device an ip?

I would really love to have both wireless cards working one day, but at this point I would be so happy just to use one of them

---

### Post by hoptimusPrime on 2010-03-03
Oh geeze

Things keep getting worse and worse..

I don't know what I did, but now I have no wired ethernet connection on my laptop!  so no more internet at all!  right now my laptop is pretty much useless

I'm thinking I need to reinstall my os from scratch and somehow do a wired install of Jaunty again... except i still cant boot from usb in BIOS.  

My only 2 options in BIOS are boot from network (?) and boot from the hard drive.  Booting from network does nothing

Should I flash my BIOS and do an upgrade?  I'm very scared of doing that...  but maybe a newer version of BIOS would recognize my usb Startup Disk

Or can I reformat and reinstall Jaunty from within Karmic somehow?

I think the main problem is I really have no idea what I'm doing half the time, and I'm attempting things way beyond my skill level.

any help please??

---

### Post by bkratz on 2010-03-03
> **hoptimusPrime said:**
> Oh geeze

Things keep getting worse and worse..

I don't know what I did, but now I have no wired ethernet connection on my laptop!  so no more internet at all!  right now my laptop is pretty much useless

I'm thinking I need to reinstall my os from scratch and somehow do a wired install of Jaunty again... except i still cant boot from usb in BIOS.  

My only 2 options in BIOS are boot from network (?) and boot from the hard drive.  Booting from network does nothing

Should I flash my BIOS and do an upgrade?  I'm very scared of doing that...  but maybe a newer version of BIOS would recognize my usb Startup Disk

Or can I reformat and reinstall Jaunty from within Karmic somehow?

I think the main problem is I really have no idea what I'm doing half the time, and I'm attempting things way beyond my skill level.

any help please??



Not an expert, so for what it is worth some of the posts in the latter part of this thread look familiar to yours

[http://ubuntuforums.org/showthread.php?t=1420589&highlight=8139too](http://ubuntuforums.org/showthread.php?t=1420589&highlight=8139too)


[ 5.551757] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too

---

### Post by hoptimusPrime on 2010-03-03
> **bkratz said:**
> Not an expert, so for what it is worth some of the posts in the latter part of this thread look familiar to yours

[http://ubuntuforums.org/showthread.php?t=1420589&highlight=8139too](http://ubuntuforums.org/showthread.php?t=1420589&highlight=8139too)


[ 5.551757] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too


My output was a little different but I tried it and it worked.  I have ethernet again, but still no wireless.  

I just sold my RTL8192 driver, so that gets rid of that option.

The RT2500 pci is supposed to be very happy with linux, i don't understand why it stopped working when I upgraded to Karmic. 

I still can't enable wireless using the Network Manager icon.  Is there a way to do it manually?

---

### Post by hoptimusPrime on 2010-03-03
Ok I'm back on my laptop using a wire, thank you bkratz.

I followed the the link [http://ubuntuforums.org/showthread.p...hlight=8139too]("http://ubuntuforums.org/showthread.php?t=1420589&highlight=8139too") and tried the same with my wireless card now..

I typed **dmesg | grep -e 2500 -e eth**, to see what it said about the RT2500pci

I got this:


[    4.472500] ACPI: Sleep Button [SLPB]
[    5.560255] eth0: RealTek RTL8139 at 0xe800, 00:16:17:4e:7b:71, IRQ 18
[   26.765090]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.319857] rt2500pci 0000:02:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.455375] Registered led device: rt2500pci-phy0::radio
[   27.455394] Registered led device: rt2500pci-phy0::quality
[   28.013418] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.512039] eth0: no IPv6 routers present


Anybody out there know what this means, or why I am unable to enable wireless?

---

### Post by hoptimusPrime on 2010-03-03
So how dumb am I...

I was reading over the above output, and i noticed where it says sleep button at the top..  

On my MSI laptop, there is a little tiny button by the power button that has a litle antenna icon on it.

This is the Wireless sleep buton, or the enable wireless button.

I clicked the button, and voila!

3 weeks of forums and code and stress and beer temper tantrums, all because of a button

If all goes well I will send this post with my RT2500 wireless pci card.

As silly as it may sound, check for a wireless button on your haptop! HAHAHA!!

---

### Post by bkratz on 2010-03-03
Glad you got the wired working and don't feel bad about the switch it happens to everyone. You really should go to the thread tools and mark as [solved] just in case it helps someone else.

Congratulations!

---

