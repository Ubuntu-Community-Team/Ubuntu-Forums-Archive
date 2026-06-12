---
title: "ralink wireless woes"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by m0untainrebel on 2007-05-08
i just got a new averatec 2300 series laptop, and i'm having a lot of trouble getting my onboard wireless card working in feisty. i know it has a ralink chipset, but that's about all i know. when i installed feisty, it automatically recognized the card using the rt73usb, even though it's not a usb device. that driver can see some of the networks within range, but not as many as my other usb wireless card i've been using, and it fails to connect to any of them.

here's my lspci:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

here's my lsusb:
```
Bus 002 Device 002: ID 0db0:6877 Micro Star International 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

it's weird, but i can't find my wireless card in any of that. if i go to System, Preferences, Hardware Information, the hierarchy looks like this:

MCP51 USB Controller
- EHCI Host Controller
- - USB2.0 WLAN
- - 802.11 bg WLAN

that's the only mention of a wlan card i can find.

i've tried ndiswrapper with this driver: [ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_2kXP.zip](ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_2kXP.zip)
ndiswrapper said the driver was installed and the hardware existed, but when i modprobed it it never showed up in System, Administration, Network or in network-manager.

i would be happy with getting either the native driver working or getting ndiswrapper working (i prefer the native driver though, so i can go into monitor mode and whatnot), so any help is greatly appreciated. thanks!

---

### Post by m0untainrebel on 2007-05-08
ahh help, i've got more problems! so i just tried installing the rt73 cvs driver from here: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

i compiled and installed it, then did modprobe rt73. now when i type iwconfig it shows me this:

```
rausb0    RT73 WLAN  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

but network-manager still doesn't recognize the driver. then i looked at this howto called HOWTO: RT73 (RT71) serialmonkey drivers: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) and it said that

> Just one caveat: RT73 doesn't support SMP or PREEMPT. These are options that can be set when your kernel is being compiled. If that doesn't make any sense, don't worry, it's all been taken care of by the Ubuntu developers. What it boils down to is you can't use hyperthreading or dual-core capabilities alongside this driver.

my computer has a dual-core turion 64, but i'm running 32-bit ubuntu feisty. my current kernel is 2.6.20-15-generic. i don't want to go to the linux-386 kernel, so i tried removing the rt73 module. when i type rmmod rt73 it works fine, but then when i type iwconfig afterwards, this is what shows up:

```
Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] Oops: 0000 [#1]

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] SMP 

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] CPU:    0

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] EIP:    0060:[<f8da2000>]    Tainted: P      VLI

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] EFLAGS: 00010286   (2.6.20-15-generic #2)

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] EIP is at 0xf8da2000

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] eax: f4723800   ebx: 00000000   ecx: 00000000   edx: f8da2000

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] esi: 00000000   edi: 00000000   ebp: f4723800   esp: ca42bc64

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] Process sudo (pid: 8404, ti=ca42a000 task=ca1cca90 task.ti=ca42a000)

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] Stack: c028ad1e f4723938 00000001 c1148d20 c015c017 00000000 00000000 f7096ec0 

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]        cb3251f0 00000000 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]        000005dc f4723800 00000002 de0c5d00 00000000 c028af75 00000000 00000010 

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000] Call Trace:

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnl_fill_ifinfo+718/1200] rtnl_fill_ifinfo+0x2ce/0x4b0

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [get_page_from_freelist+679/880] get_page_from_freelist+0x2a7/0x370

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnl_dump_ifinfo+117/160] rtnl_dump_ifinfo+0x75/0xa0

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_dump+83/400] netlink_dump+0x53/0x190

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_dump_start+217/320] netlink_dump_start+0xd9/0x140

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnetlink_rcv_msg+0/592] rtnetlink_rcv_msg+0x0/0x250

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnetlink_rcv_msg+464/592] rtnetlink_rcv_msg+0x1d0/0x250

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnl_dump_ifinfo+0/160] rtnl_dump_ifinfo+0x0/0xa0

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnetlink_rcv_msg+0/592] rtnetlink_rcv_msg+0x0/0x250

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_run_queue+130/288] netlink_run_queue+0x82/0x120

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [rtnetlink_rcv+40/80] rtnetlink_rcv+0x28/0x50

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_data_ready+18/80] netlink_data_ready+0x12/0x50

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_sendskb+33/64] netlink_sendskb+0x21/0x40

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_sendmsg+547/768] netlink_sendmsg+0x223/0x300

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [sock_sendmsg+274/304] sock_sendmsg+0x112/0x130

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [get_page_from_freelist+679/880] get_page_from_freelist+0x2a7/0x370

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [__wake_up+56/80] __wake_up+0x38/0x50

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [copy_from_user+39/96] copy_from_user+0x27/0x60

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [sys_sendto+297/384] sys_sendto+0x129/0x180

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [filemap_nopage+753/928] filemap_nopage+0x2f1/0x3a0

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [__handle_mm_fault+633/2624] __handle_mm_fault+0x279/0xa40

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [sock_attach_fd+112/208] sock_attach_fd+0x70/0xd0

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [__sock_create+295/512] __sock_create+0x127/0x200

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [sys_socketcall+408/640] sys_socketcall+0x198/0x280

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000]  =======================

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000] Code:  Bad EIP value.

Message from syslogd@bee at Tue May  8 04:29:20 2007 ...
bee kernel: [ 1231.120000] EIP: [<f8da2000>] 0xf8da2000 SS:ESP 0068:ca42bc64

Message from syslogd@bee at Tue May  8 04:29:19 2007 ...
bee kernel: [ 1231.120000]  [netlink_insert+227/352] netlink_insert+0xe3/0x160

```

and then my computer messes up a lot. this last time i tried, for some reason it disabled the keyboard (though the mouse still worked). completely logging out didn't fix it, so i had to reboot. then it wouldn't reboot, and i had to turn off my computer by pressing the button.

so i guess my questions are 1) how do i completely remove my rt73 module without crashing my computer any more, and 2) how do i install working drivers for this wireless card?

---

### Post by mjgumbley on 2007-05-08
Hi, to remove the driver, I'd try booting your system in recovery (single user) mode from the GRUB list of kernels. If this starts to activate your driver (and crash your kernel), then try the following:

In the GRUB boot kernel list, highlight the latest kernel (Recovery) - and press 'e' to edit the line (this change won't be permanent). The end of the kernel line may read 'ro single' - change this to 'rw init=/bin/bash'

Press return to acceot this change, and 'b' to boot it. This will give you a shell as quickly as possible, without going through the boot procedure.

Then, cd /lib/modules/<your kernel version number here>
Then find your rt73 module file (a .o or .ko file) - not sure where, and delete/rename them.

If this complains about / being read-only, then do
mount / -o rw,remount
and try again.

Then run sync a few times, and reboot.

I'll try to find my old ndiswrapper config and help you getting that working - I never used NetworkManager for wireless (I have a Ralink 2500 clone) - but configured it all manually. I've started using NetworkManager - but it's not associating with my AP yet.

I wrote up some notes...
[http://ccgi.gumbley.plus.com/blog/?page_id=25](http://ccgi.gumbley.plus.com/blog/?page_id=25)
Hope this helps,
Matt

---

### Post by m0untainrebel on 2007-05-08
i've found the rt73.ko file and renamed it to rt73.ko.bak and rebooted (even when i booted up normally it wouldn't actually crash the kernel unless i ran iwconfig). now it didn't load the driver, and iwconfig no longer crashes. thanks!

i've actually seen several posts of message boards about using the driver that you link to on your blog, [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip) -- only that is now a broken link. i spent a good time looking for WL54driver2.2.6.0.zip, but the best i can tell a-link replaced it with WL54H_WL54PC_2kXP.zip instead, which doesn't work with ndiswrapper on my computer.

the [ftp://ftp.a-link.com/wl54h/](ftp://ftp.a-link.com/wl54h/) also has linux drivers, which i downloaded but they won't compile without errors, so i can't see if they'd work or not.

can you send me the actual older windows drivers you're using for ndiswrapper?

thanks so much for helping!

---

### Post by mjgumbley on 2007-05-10
Hi again,
Just looked at that FTP site, and there's no mention of those drivers, as you say.,.. but there are some drivers at [ftp://ftp.a-link.com/wl54h/](ftp://ftp.a-link.com/wl54h/) - I haven't tried these, but there's a Linux driver there. Might be useful - don't know. Also [ftp://ftp.a-link.com/wl54pc/WL54H_WL54PC_RT2500_Linux.tar.gz](ftp://ftp.a-link.com/wl54pc/WL54H_WL54PC_RT2500_Linux.tar.gz) and [ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_RT2500_Linux.tar.gz](ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_RT2500_Linux.tar.gz)

I do have the WL54driver2.2.6.0.zip drivers that are no longer available from a-link - but I don't know what the licensing restrictions might be on me redistributing it. Really sorry about that - if the drivers above don't work, we could perhaps contact A-Link and see if they'd agree to release the drivers - MANY people reference these all over the net - just a Google for the zip file shows that... (Really should update the ndiswrapper page to say that the link's dead).

However, the card I have has the drivers online - Belkin's own. I haven't tried these with ndiswrapper, perhaps it's worth a try:
[http://www.belkin.com/uk/support/product/?lid=enu&pid=F5D7010uk](http://www.belkin.com/uk/support/product/?lid=enu&pid=F5D7010uk)

Hope this helps,
Matt

---

### Post by m0untainrebel on 2007-05-10
i've already tried the native linux driver at [ftp://ftp.a-link.com/wl54h/](ftp://ftp.a-link.com/wl54h/) -- i can't get it to compile without errors. maybe i'll try contacting a-link to see if they'll let me have the older drivers. i'm about to try the belkin drivers you use. thanks!

hopefully this will work.

---

### Post by mjgumbley on 2007-05-10
You say you've tried the XP drivers they supply in the new package under ndiswrapper but they don't show up in NetworkManager... Just get wlan0 present first - getting NetworkManager working seems like high-level stuff compared :-)

If I blacklist the rt2500 driver, and ensure ndiswrapper is in my /etc/modules, and the modules get resolved at boot, then upon inserting the card, I see ndiswrapper with lsmod, and tail -f /var/log/kern.log shows ndiswrapper loading up the rt2500 ndis driver - I recall that my initial tinkerings edited /etc/modprobe.d/ndiswrapper to contain alias wlan0 ndiswrapper. After inserting the card, I see wlan0 in ifconfig, and can do iflist wlan0 scan to see the various networks...


I don't use the Belkin drivers under ndiswrapper - I just used what the ndiswrapper wiki suggested.

---

### Post by m0untainrebel on 2007-05-13
i got it working with ndiswrapper! the native drivers never worked, and i the windows drivers i was trying in ndiswrapper weren't working either. this laptop actually didn't come with a driver cd (i bought it refurbished i guess?), so i went to the averatec website and downloaded the wireless driver there. it was a windows exe though and wine wouldn't wouldn't work correctly, and neither would cabextract, so i ended up having to actually install indows xp on another computer just to install this driver so i could get the .inf and .sys files. so i did that and ndiswrapper said the hardware was present and it looked like it would all work fine.... only it didn't find any networks when it tried scanning them. it took me about 2 days before i realized that my wireless radar was actually turned off. i turned it back on today (with the little switch on the laptop) and it worked fine! hurray, no more carrying around a usb wireless card!

---

### Post by mjgumbley on 2007-05-29
Excellent - you're lucky!
Mine's broken again at the moment, it just won't connect to my WPA network. Gets the the GROUP_HANDSHAKE, then falls back to the 4WAY_HANDSHAKE, then never recovers.

Looks like it's a known problem, with a workaround (which unfortunately, requires removal of network mnager):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37120](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37120)

Regards,
Matt

---

### Post by m0untainrebel on 2007-05-29
actually, what's interesting with my ndiswrapper driver is that with certain unsecure networks, network-manager doesn't ever connect, but just using network-admin the old way works fine. with WEP or WPA networks, and some open networks, network-manager works fine though.

i have no idea... but i've just been using network-admin for the ones that it won't work.

---

