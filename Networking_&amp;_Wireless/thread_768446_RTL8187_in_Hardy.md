---
title: "RTL8187 in Hardy"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Jexel on 2008-04-26
Every time I upgrade to a new version of Ubuntu I have to go through another nightmare.

I followed this guide [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958) to get my Ubuntu working in Gutsy and for the most it was working PERFECTLY.

Once I've upgraded it no longer works...

I've tried this [http://ubuntuforums.org/showthread.php?t=758840&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=758840&highlight=rtl8187) however it works for the most part but also disconnected after 5 minutes. Running the script can keep the connection up for around 5 seconds, long enough to load up one page before disconnecting again.

I've since removed ndiswrapper and tried to install it again from source. However, this time I can't even compile it. So I decided to install the version from the repos however when i type ```
sudo modprobe -m
``` I get ```
module configuration already contains alias directive

```

When I type ```
sudo modprobe ndiswrapper
``` I get ```
FATAL: Could not open '/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

```

I've been looking everywhere for a solution but cannot find any. Can anybody help me?

---

### Post by Jexel on 2008-04-27
bump!

---

### Post by podfish on 2008-04-27
i686 or AMD64?  :-)  I also have the rtl8187 driver and will probably put ndiswrapper to use starting tomorrow--for tonight i have fake wireless with a 1.5 Mbit "gamer" zero config wireless connection from logitech (two little black boxes that are a lifesaver for my unwired desktop.)

If you're amd64 i'll post anything i find on this.

You're not doing anything wrong, i'm sure--rtl8187 is just broken right now in the vanilla kernel.

---

### Post by Jexel on 2008-04-27
i can't even modprobe the ndiswrapper that's in the repos :| might have to go back to windows...that or i'll just buy another wireless card

---

### Post by AlexBellisBrown on 2008-04-27
Hello, I got your PM. I have it working, RTL 8187, on Hardy, but I don´t lnow if i have it working with NDISwrapper, or if its working natively. After installing NDISwrapper i installed the windows 98 version of the realtek driver from the Realtek website. I also sometimes have the same problem that is disconnects from time to time. To be honest im thinking of buying myself a usb wireless card to replace my Realtek one. It just seems this problem is "unfixable". PM me if you reply to the thread, im on holiday and dont have time to look the thread back up every day!!! lol.

---

### Post by Jexel on 2008-04-27
i've rolled back to gutsy and everything is working fine again. Don't think its worth the effort to get wireless working in hardy.

---

### Post by FlyingIsFun1217 on 2008-04-27
To see which version of wireless driver you are using (NDIS or RTL8187), type:

> 
lsmod | grep ndis*


If you get no listings, try using:

> 
lsmod | grep rtl8187


Personally, using the rtl8187 driver with Hardy, I've had very few problems so far (although I am starting to experience dropped connections recently).

Hope that helps!
FlyingIsFun1217

---

### Post by podfish on 2008-04-27
I'm still having problems--and the ndiswrapper amd64 driver (from my mobo website) is a nightmare, as well--it shows up, but then everything starts locking up, and I have to go to a tty term and ctrl-alt-del to affect an actual shutdown.  Of course, the 32-bit driver doesn't work with ndiswrapper at all (get "32-bit doesn't work with 64-bit, stupid" kernel messages via dmesg and the system log.  So, nogo for now.

I'm considering moving to wireless N anyway, just to get mo betta range in my house.  Anyone recommend a card?

SK

---

### Post by podfish on 2008-04-27
so, doing some research seems to help me understand this driver a little more.  It's a new driver, and it depends on the mac80211 kernel module to operate and maintain control over its transactions.  However, for some reason, hardy does not load this module as a dependency.  (I don't have a gutsy install anymore--could someone check to see if it is loaded and i'm not just blowin smoke?)

My experience is that, once I did a "sudo modprobe mac80211" I stopped getting all these nasty dropped packet/signal strength problems.  I also blacklisted ipv6 on a whim, but that seems to make no difference.  It's been running about 40 minutes straight with no degradation of performance.

Can someone please attempt to verify?  I'll post something on one of the launchpad bugs.

---

### Post by geraldo5002 on 2008-04-29
podfish:

I loaded the module and the connection doesn't drop anymore using bittorrent.

It seems you found the solution!

:lolflag:

---

### Post by Psyphre on 2008-05-01
I tried using

sudo modprobe mac80211

but it still doesnt work.

---

### Post by podfish on 2008-05-01
Is it persistent?  Does it survive a reboot?

I noticed after the fact that mac80211 is already present after boot.  Not sure what doing it again would do--most likely nothing.  I'm still having serious issues.

SK

---

### Post by geraldo5002 on 2008-05-01
Well, in theory the mac driver is loaded at boot time but running depmod makes the connection more stable. But is not ok. It takes more time to drop using torrents. But still drops. I'm using windows right now... :confused:

---

### Post by JCasper on 2008-05-04
I get the same error when modprobing ndiswrapper. I have no idea what to do... :(

---

### Post by Desterie on 2008-05-07
Kind of a newbie around these parts.  I have a RTL8187 external USB adapter.  I never did get it to work on 7.10.  It showed a connection, but never would connect to any of the available networks.  I tried messing with the Linux driver on my disk, but couldn't get that to work either.  I heard it had broken kernels in the driver, or it may have been my own ineptitude.  In any case, I did a fresh install of Heron.  I was dreading trying to install drivers and such (I find the Terminal intimidating) I plugged the RTL8187 in and it appeared that it wasn't working.  Like before it detected my networks... I tried clicking one and POOF I had internet.  None of the lights flash on my wireless adapter, but it works.

It seems alot of folks here get kinda excited and are even eager to use that terminal monster and programs like ndiswrapper.  By any chance did anyone try just plugging it in and going with it?  (For reference purposes I am using a Dell 1521)

Desterie

---

### Post by scholzilla on 2008-06-23
please check if you have the 8187L or 8187B chipset. The ONLY way to do this is to open up your box and look at what's written on your wireless card. If you are using 8187L, neither the linux drivers offered on the realtek website nor the ndiswrapper solutions offered within this forum will work for you. Instead, remove all drivers that you've installed and just let the native driver set that comes with hardy do the driving. 8187L and 8187B are fundamentally different chipsets.

---

### Post by panurge77 on 2008-06-28
Hello. I wrote this guide a long time ago, and it used to work. I have not tested it in 8.04 yet, but I'll do it soon. It's for RTL8187L. Native drivers are always frustrating with realtek wireless. 


[http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

---

### Post by scholzilla on 2008-06-28
i'm not sure this will work with 8187L. ndiswrapper apparently works with 8187b, but i never got it to work with 8187L

---

### Post by mikebryantwi on 2008-06-29
Ok... Relatively new to linux, so be nice!  Got a new laptop (Gateway T-1625) as a gift...  Came with Vista loaded.  Immediately got rid of that pathetic excuse for an operating system after having connectivity problems on the wireless (8187B).  Tried XPx64, wireless worked perfectly, but there are no audio drivers for 64 bit :(  Gateway support was absolutely no help, just told me to reinstall Vista and bring it back to factory default... Then basicly told me "TOUGH" when I mentioned the wireless connectivity problems.  Needless to say at that point I was quite pissed off and getting ready to chuck this laptop.  Read up on some forums, and saw that perhaps Linux was the way to go.  Ubuntu installed flawlessly, sound/video worked just fine.  And now for the wireless...  I've been on multiple forums, followed about 6 different "guides" on how to get this worthless wifi card working...  nothing is working.  I'm sure it's something I'm doing wrong, or not doing period...  The ndiswrapper shows the driver is installed, but i get no wireless connection in network manager.  the interfaces files is modified to add wlan0, BUT when I ifconfig, all I get is eth0 and lo...  I'm sure I haven't given enough information, but it's now 4am. I've been working on this for a good 8 hours straight, and I'm completely out of ideas... Someone please come to my rescue!  Thanks in advance...  [email]--mike.bryant.wi@gmail.com[/email]--

---

### Post by panurge77 on 2008-06-29
I've always used ndiswrapper with rtl8187L but now in hardy I get a kernel freeze... I'm using 64bits and that can be a problem too.

---

### Post by mikebryantwi on 2008-06-29
well, at it again... still no luck...


update-pciids
Done.

lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

lshw -C network

  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:59:05:55
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.0.108 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=10MB/s


Refuses to even acknowledge my wirless card... I think I'm going to cry.

---

### Post by WeEatVista on 2008-06-29
For How To: RTL8187B in Ubuntu, even Hardy, check out this thread:

[http://ubuntuforums.org/showthread.php?t=844455]("http://ubuntuforums.org/showthread.php?t=844455")


Hope this Helps,

We Eat Vista

---

### Post by Jexel on 2008-07-12
After digging around the internet some more, I've finally gotten somewhere.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/225851](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/225851)

Following the comments on that link I installed wicd and everything seems to be working perfectly. Currently I've had zero disconnections but would still have to test it further.

To install Wicd you just need to do the following:

1. Add "deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras" to your list of sources.
Where hardy can also be gutsy, feisty, etc

2. Run the commands
```

sudo apt-get update
sudo apt-get install wicd

```

3. Finally, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

Edit:

Well, after days of testing, Wicd doesn't seem to have "fixed" the problem. It still tends to drop the connection but the drops are unpredictable. Sometimes I can last several hours without a drop however other time it would drop out couple of minutes after connecting. Torrents would work for around 10-15 minutes.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

