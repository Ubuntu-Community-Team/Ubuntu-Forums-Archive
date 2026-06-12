---
title: "ndiswrapperless &gt;= WUSB54GSv2/GCv2  / WL169gE / USR5421 / USR5420 / F5D7051"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by cypher2k on 2007-09-02
For those having to lump using ndiswrapper (if you even managed to get it working which I didnt) with any of these devices:

    *  Asus WL169gE
    * US Robotics Wireless MAXg USB Adapter USR5421
    * US Robotics Wireless USB Adapter USR5420
    * Belkin F5D7051
    * Linksys WUSB54GS
    * Linksys WUSB54GSC

Then I may have a possible way out. A clever guy at the following site - [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/) has worked out that (and I think most of us with these working kinda got the impression) these are RNDIS devices and has written a RNDIS USB wifi driver that enables these devices to be used under Linux systems.

Now since a) Im with my girlfriend at my place right now,  I have no way of testing out how well this stuff works (she owns the WUSB54GSv2). b) I have no fruity RNDIS USB wifi devices lying around I have no ability to test right now. 

Would be good if people could test and report their results and get it stickied and stuff. Maybe even get a deb sorted :)

I havent seen this resource mentioned (after an admittedly quick search) so I hope this helps people.

---

### Post by bjd on 2007-09-17
Heh, i created this driver about a year ago because i could not get ndiswrapper to work on my 64bit system, but it hadn't really been updated since.
Although the old version more or less worked.. it had some problems, like hardlocking your system on some occasions and fiddly connection issues.
But this weekend I forced myself to get it updated and it seems to work a lot better now.
At least no more hardlocking for me :-)
So if you had problems before you might want to try again...
It does need a bit more recent kernel version now though, i believe 2.6.20 and up is ok.

---

### Post by heindsight on 2007-11-22
Thanx bjd! 
I bought a Belkin F5D7051 wireless adapter with my new amd64 system a few months ago and now I finally have a working wireless network!

:guitar:

---

### Post by Merk42 on 2007-11-29
```
    *  install the kernel source/headers package for your particular distro.
    * backup original kernel modules usbnet.ko, cdc_ether.ko and rndis_host.ko (find them under /lib/modules/<kernel-release>/...)
    * as root run clean.sh to remove the distro supplied version of the modified modules.
    * finally run make (as normal user) and make install (as root) this installs the modules in /lib/modules/<kernelversion>/extra
    * plug in the device and run iwconfig to see if a wireless device has appeared.
    * setup wireless networking in the normal way for your linux distro. 
```

Could someone explain this in exact terminal entries?  Also, does the first step involve Internet access? My Ubuntu doesn't have Internet access which is why I'm doing all this to begin with.  I am however dual booting with XP (where when it comes to wireless "It Just Works"). So I could download .deb. .tar whatever and transfer them to Ubuntu installation if neccesary.

---

### Post by Merk42 on 2007-11-30
BUMP

6 Pages of wireless problems in less than 24hrs.  Is this maybe a hint of what desperately needs to be worked on in Hardy?

---

### Post by heindsight on 2007-12-10
> **Merk42 said:**
> ```
    *  install the kernel source/headers package for your particular distro.
    * backup original kernel modules usbnet.ko, cdc_ether.ko and rndis_host.ko (find them under /lib/modules/<kernel-release>/...)
    * as root run clean.sh to remove the distro supplied version of the modified modules.
    * finally run make (as normal user) and make install (as root) this installs the modules in /lib/modules/<kernelversion>/extra
    * plug in the device and run iwconfig to see if a wireless device has appeared.
    * setup wireless networking in the normal way for your linux distro. 
```

Could someone explain this in exact terminal entries?  Also, does the first step involve Internet access? My Ubuntu doesn't have Internet access which is why I'm doing all this to begin with.  I am however dual booting with XP (where when it comes to wireless "It Just Works"). So I could download .deb. .tar whatever and transfer them to Ubuntu installation if neccesary.

[B][COLOR="Red"][SIZE="4"]WARNING:[/SIZE][/COLOR] Don't follow these instructions unless you either know what you're doing, or are willing to learn the hard way. 
While it should be possible to fix things if something does go wrong, there is a risk that you could hose your system and you 
may end up having to reinstall. Make sure you read the entire thread before proceeding (especially if you don't know exactly what you're doing)[/B]

For the first step you will need internet access. You need the linux-headers and linux-source packages for your kernel. 
You can use uname -r to find out what kernel version you have, and then get the corresponding packages.  Also make 
sure you have make and gcc (and all their dependencies) installed. You can download the .debs for all these from
[packages.ubuntu.com]("http://packages.ubuntu.com") and install them using dpkg -i <deb file>

Now, find out the full path to the old modules that you're going to be replacing and make a note of
it. You'll need it if you want to restore the old modules. The modules should all be in
/lib/modules/<kernel-version>/kernel/drivers/net/usb but it can't hurt to make sure, by using
the following command:
```

find /lib/modules/`uname -r`/ -name usbnet.ko -or -name cdc_ether.ko -or -name ndis_host.ko

```

Now do the following to actually back up the files:
```

cd
mkdir wifi_backup
find /lib/modules/`uname -r`/ \( -name usbnet.ko -or -name cdc_ether.ko -or -name ndis_host.ko \) -exec cp \{\} wifi_backup \;

```

Now (assuming you extracted the archive with the new modules in your home directory) do the following to actually install the new drivers:
```

cd rndis_wlan
sudo ./clean.sh
make
sudo make install
```

If your kernel is older than 2.6.21, you may also need to add a udev rule to get the modules to load automatically. 
You can use the following command for that (replace the idProduct and idVendor values with the appropriate values  for your device):
```

sudo -i
echo "BUS==\"usb\", SYSFS{idProduct}==\"7051\", SYSFS{idVendor}==\"050d\", RUN+=\"/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'\"" > /etc/udev/rules.d/85-usb-rndis.rules
exit

```
Note that this step might not be needed (particularly if you have a newer kernel). Try going without it first.

Now if you plug in your device, the modules should load automatically. If you run the command iwconfig, your wifi device should appear. 
Now you should be able to use network-manager to set up your wifi network.

Hope this helps...

---

### Post by Junglizer on 2007-12-10
> **Merk42 said:**
> BUMP

6 Pages of wireless problems in less than 24hrs.  Is this maybe a hint of what desperately needs to be worked on in Hardy?


Correction, 6 pages, of people who do not know how to use the "search" function.

---

### Post by Junglizer on 2007-12-10
Network Manager. bah! You've already done this much work, just stay in the term.

---

### Post by heindsight on 2007-12-10
> **Junglizer said:**
> Network Manager. bah! You've already done this much work, just stay in the term.

True enough. I don't use Network Manager for my wireless network either, but I figured someone who needs such detailed step-by-step instructions to install these modules is probably going to be more comfortable using network manager.

---

### Post by Junglizer on 2007-12-10
I suppose, but when it comes down to it, knowing how to do it from the CLI is much better then knowing how to do it from a specific GUI app. Don't get me started on the whole, un-editablity of plain-text configs while also using an app. But I suppose its what you know/want to know. Lots of Ubuntu users are looking for a Windows sit-in, I'm looking for something that is *different* and I don't even use Ubuntu anyways.

---

### Post by Bpa on 2007-12-16
I used the fix and now I can actually see the ESSIDs of access points in my area, so that is farther than anything else has gotten me.  Thanks for that.  However, I cannot connect to my access point with WPA protection.  I am sure that I am entering the passphrase correctly, but it just attempts to connect until it times out. I can connect to unprotected networks just fine. Is there a module I need to install so that WPA can run over these drivers?  Does anyone have a suggestion?

---

### Post by Modplanman on 2007-12-27
Sorry about reviving an older thread, and also sorry to say I tried this method and it seems to have messed up ubuntu somehow. Checked everything, right packages, followed it through to the letter, afterwards it couldn't load any ubuntu program apart from firefox, and after rebooting now ubuntu wont start up either. I put in my username and password and it just stops on the blank screen.

---

### Post by heindsight on 2007-12-27
> **Modplanman said:**
> Sorry about reviving an older thread, and also sorry to say I tried this method and it seems to have messed up ubuntu somehow. Checked everything, right packages, followed it through to the letter, afterwards it couldn't load any ubuntu program apart from firefox, and after rebooting now ubuntu wont start up either. I put in my username and password and it just stops on the blank screen.

Well, it seems that ubuntu is starting up (if you're seeing a login screen), but somehow you can't
log into your GNOME session. Can you boot the machine in rescue mode?
 If you can do that then you can uninstall these modules by reversing the steps you took to install
them:

first delete cdc_ether.ko  rndis_host.ko  usbnet.ko from /lib/modules/`uname -r`/extra :
```
cd /lib/modules/`uname -r`
rm cdc_ether.ko  rndis_host.ko  usbnet.ko
```

Next, to restore the original modules, cd into the directory where you backed up the drivers
then do
```
cp usbnet.ko cdc_ether.ko ndis_host.ko /lib/modules/`uname -r`/kernel/drivers/net/usb 
```

If you also carried out the last step I listed to add a new udev rule, then undo that too:
```
rm /etc/udev/rules.d/85-usb-rndis.rules
```

Now you can exit from recovery mode, and hopefully things should be back the way they were
before you installed these modules.

**------------------------------------------EDIT------------------------------------------**
I just realised that I left out something important. After restoring the original modules you need to run ```
sudo depmod -ae
``` to get everything back to the way it was

---

### Post by Modplanman on 2007-12-27
Sorry, can't boot into recovery mode either, stopped right on the part where it showed messages about registering said files fom earlier too. I could try it again and note the messages if you want. Tried normal ubuntu again just in case and did the same. 

Hmmmm, maybe I did mess up somewhre.

---

### Post by heindsight on 2007-12-27
Yes, post those messages....

---

### Post by Modplanman on 2007-12-29
sorry about that very late reply.

Back to business: Turned out that after a very long time it paused on those messages it carried and booted into recovery mode, but reversal didn't work. I must've fecked up somewhere.

Anyway, re-installed ubuntu (now moved across to 64 bit). Despite how silly this next question might sound I just want to make sure nothing messes up this time. 

When doing as said earlier putting commands into terminal, where it has:

"find /lib/modules/`uname -r`/ \**(-name** usbnet.ko -or -name...."

The emboldened bit it points out as not being a command - my assumption is either there's a space missing between the bracket and hyphen or to put the kernel number in. Silly and  incredibly basic, but I just need to make absolute sure.

---

### Post by heindsight on 2008-01-07
yes, there needs to be a space between the ( and the -name

---

### Post by smulav on 2008-01-07
Hi! Im just trying linux out for the first time and am very interested to learn more about commands. Thankyou very much for the information. You've been a big help to me- a lot easier to follow than some of the forums I've read about ndiswrapper! I've tried everything you said and it seems as though everything's working fine until I get to the last code message (to automatically install drivers when device is plugged in). I keep getting the message: "Permission Denied"  Why is this? I would really appreciate any help as I just want to get online and then I'm going to switch permanently to linux. Please help!

---

### Post by heindsight on 2008-01-08
> **smulav said:**
> I keep getting the message: "Permission Denied"  Why is this?

That's happening because, like a fool, I didn't test everything thoroughly enough before posting.

If you have a recent kernel (later than 2.6.21) you shouldn't need that last step anyway, so try 
plugging in your device and using it without that last step first.

If it doesn't work, then try:
```

sudo -i
echo "BUS==\"usb\", SYSFS{idProduct}==\"7051\", SYSFS{idVendor}==\"050d\", RUN+=\"/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'\"" > /etc/udev/rules.d/85-usb-rndis.rules
exit

```

---

### Post by smulav on 2008-01-08
Something is not right! After I type the commands: sudo ./clean.sh
I get this message:
FATAL: Module rndis_wext not found. 
removed `/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/usbnet.ko' 
removed `/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/cdc_ether.ko' 
removed `/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/rndis_host.ko'
What causes this? I think this is what is causing the fact that I have had to re-install Ubuntu about 5 times Please help me heindsight!

---

### Post by heindsight on 2008-01-08
OK, I just tried the current (20071220) snapshot, and also ran into problems: all networking stopped
working, couldn't log out of my GNOME session, couldn't unload any kernel modules. Eventually
I had to do a hard reboot and remove the modules.

It's not necessary to do a complete reinstall to recover from this. Just follow the steps I described
in a previous post to remove the modules.

I suggest trying one of the older snapshots, I had no problems before, using the 20071213 snapshot.
It seems there is some sort of bug in the current snapshot, that causes problems working with
the current Ubuntu kernel.

---

### Post by smulav on 2008-01-13
I've got a wireless connection but nothing is working. It says I'm connected to the router when I hover over the network logo but I can't even get to my router IP address!

---

### Post by heindsight on 2008-01-13
Post the output from ifconfig and iwconfig here.

Do you connect using NetworkManager?

What encryption does your network use? Could you perhaps try to turn encryption off,
just to see if it works then?

---

### Post by smulav on 2008-01-13
keith@keith-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:47:58:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xee00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3568 (3.4 KB)  TX bytes:3568 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:C6:A8:41  
          inet6 addr: fe80::211:50ff:fec6:a841/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:732 (732.0 b)

keith@keith-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Bit Rate:36 Mb/s   Tx-Power=14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Yes I do use Network Manager.
How do I turn encryption off?

---

### Post by Buckleywood on 2008-02-16
Hi, I am pretty new to Ubuntu and Linux, and am running a WUSB54GSv2, so having installed Gutsy as a dual-boot have no wifi connection in Linux! I was hoping for great things using this approach, but like Smulav I have got a fatal error regarding rndis_wext. I have googled for it but most of the links relate to this thread, so I haven't got much further. I have used the 13th December snapshot as Heindsight recommended, but still get the fatal error (haven't tried the latest snapshot...).

Smulav seemed to get beyond this, but I am not sure how or what else I can do?

Anyone able to help? Thanks

EDIT - Ok managed it now, at least with unencrypted connection - and I'm posting this in Linux! Hooray....

---

### Post by paladaxar on 2008-02-18
There is a very nice tutorial (with very basic steps) for setting up the adapter on the 32bit distro using ndiswrapper.  Could some kind sole please give us a simple step by step process like that (including all of the actual commands) to set up the WUSB54GSv2 on a 64bit distro?  Please?

I want to learn more about Linux...but it would be nice to have the internet to do so...

---

### Post by lake2000 on 2008-03-06
I installed Gutsy on a laptop and finally got my Belkin f5d7051 working using the steps in this thread. I used the 20071107 snapshot (the most recent one didn't work for me and neither did ndiswrapper).

---

### Post by doobmaster on 2008-03-06
Hi, great tutorial, just a few noob questions, I'm runnin backtrack 3 off hard drive, i have a wusb54gsv2 with the broadcom 4320 chip, when i follow with the installation of this driver everything goes thru fine, when i plug the device and type lsmod it shows me that rndis_host, usbnet is present, but when i type iwconfig the device is not thr, it displays my internal wireless card which is ipw3945 as wlan0, but no sign of my usb dongle, plz anyone help, i'm ready to post more info

---

### Post by 0vermind on 2008-03-10
Okay on the first page the guy with the elephant avatar said to "download the corrisponding kernel packages"

What exactly does that mean? I have no idea what the crap that means, I thought you mean grab a new kernel, I didn't see any newer ones in Apt-get update.

What exactly do you mean?
Maybe this isn't the right thread for me?

I have a Linksys Wireless-G Speedboster Adapter **Model is WUSB54GS v2**, and I am running Ubuntu Hardy x64 (Ubuntu 64-bit). Now don't tell me that it won't work on hardy, just pretend I am on Ubuntu 7.10 cause it didn't work on there either for me.

I tried the NDISWRAPPER and the x64 drivers for my device and when I plug in my device it turns on and back off quickly.
I followed the instructions for the ndiswrapper from this topic here: [http://ubuntuforums.org/showthread.php?t=225206&page=1](http://ubuntuforums.org/showthread.php?t=225206&page=1)
Later I found out it was only for 32-bit so I tried to installed the x64 drivers. 

The drivers installed, I got no errors when installing the 64-bit drivers and NDISWARPPER says installed they are installed and when the device is plugged in NDISWRAPPER says present, but my Linksys WUSB54GSv2 does NOT turn on. :'(

Here is some information that might help you diagnose my problem:

**ndiswrapper -L**
```

desktop:~/Desktop$ ndiswrapper -L
wusb54gsv2-x64 : driver installed
	device (13B1:0014) present

```


**lsusb**
```

desktop:~/Desktop/rndis$ sudo lsusb
Bus 003 Device 019: ID 13b1:0014 Linksys 
Bus 003 Device 018: ID 083a:4505 Accton Technology Corp. 
Bus 003 Device 005: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 003 Device 003: ID 154b:0015  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 0  
```


**dmesg**
```
[   15.586836] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   15.586980] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   15.587125] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   15.587275] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
[   15.587424] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22) *0
[   15.587532] ACPI: Power Resource [ISAV] (on)
[   15.587567] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.587589] pnp: PnP ACPI init
[   15.587596] ACPI: bus type pnp registered
[   15.587803] pnpacpi: exceeded the max number of mem resources: 12
[   15.591125] pnp: PnP ACPI: found 12 devices
[   15.591127] ACPI: ACPI bus type pnp unregistered
[   15.591322] PCI: Using ACPI for IRQ routing
[   15.591326] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.591337] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   15.602435] NET: Registered protocol family 8
[   15.602436] NET: Registered protocol family 20
[   15.602490] agpgart: Detected AGP bridge 0
[   15.602495] agpgart: Setting up Nforce3 AGP.
[   15.607005] agpgart: AGP aperture is 128M @ 0xe0000000
[   15.607075] AppArmor: AppArmor Filesystem Enabled
[   15.610396] Time: tsc clocksource has been installed.
[   15.622409] system 00:00: ioport range 0x4000-0x407f has been reserved
[   15.622411] system 00:00: ioport range 0x4080-0x40ff has been reserved
[   15.622414] system 00:00: ioport range 0x4400-0x447f has been reserved
[   15.622415] system 00:00: ioport range 0x4480-0x44ff has been reserved
[   15.622417] system 00:00: ioport range 0x4800-0x487f has been reserved
[   15.622419] system 00:00: ioport range 0x4880-0x48ff has been reserved
[   15.622427] system 00:01: iomem range 0xf0000-0xf3fff could not be reserved
[   15.622429] system 00:01: iomem range 0xf4000-0xf7fff could not be reserved
[   15.622431] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[   15.622433] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
[   15.622435] system 00:01: iomem range 0x4fff0000-0x4fffffff could not be reserved
[   15.622439] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
[   15.622441] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[   15.622443] system 00:01: iomem range 0x100000-0x4ffeffff could not be reserved
[   15.622445] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.622447] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   15.622449] system 00:01: iomem range 0xfefff000-0xfeffffff could not be reserved
[   15.622451] system 00:01: iomem range 0xfff80000-0xfff80fff has been reserved
[   15.622456] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   15.622458] system 00:03: ioport range 0x800-0x805 has been reserved
[   15.622460] system 00:03: ioport range 0x290-0x297 has been reserved
[   15.622763] PCI: Bridge: 0000:00:0b.0
[   15.622765]   IO window: 9000-9fff
[   15.622768]   MEM window: e8000000-e9ffffff
[   15.622771]   PREFETCH window: d0000000-dfffffff
[   15.622774] PCI: Bridge: 0000:00:0e.0
[   15.622775]   IO window: a000-afff
[   15.622777]   MEM window: disabled.
[   15.622779]   PREFETCH window: disabled.
[   15.622787] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   15.622833] NET: Registered protocol family 2
[   15.658420] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.659271] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   15.664435] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.665704] TCP: Hash tables configured (established 262144 bind 65536)
[   15.665708] TCP reno registered
[   15.674479] checking if image is initramfs... it is
[   16.125683] Switched to high resolution mode on CPU 0
[   16.196515] Freeing initrd memory: 8053k freed
[   16.206097] audit: initializing netlink socket (disabled)
[   16.206111] audit(1205062045.120:1): initialized
[   16.207716] VFS: Disk quotas dquot_6.5.1
[   16.207786] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.207903] io scheduler noop registered
[   16.207905] io scheduler anticipatory registered
[   16.207907] io scheduler deadline registered
[   16.207996] io scheduler cfq registered (default)
[   16.261614] Boot video device is 0000:01:00.0
[   16.283414] Real Time Clock Driver v1.12ac
[   16.283513] Linux agpgart interface v0.102
[   16.283515] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.283626] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.284113] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.284675] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.284727] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.284797] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   16.284799] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   16.285336] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.285863] mice: PS/2 mouse device common for all mice
[   16.285894] cpuidle: using governor ladder
[   16.285895] cpuidle: using governor menu
[   16.286040] NET: Registered protocol family 1
[   16.286098] registered taskstats version 1
[   16.286217]   Magic number: 0:747:478
[   16.286351] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.286354] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.286355] EDD information not available.
[   16.286363] Freeing unused kernel memory: 316k freed
[   16.313395] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.449665] fuse init (API version 7.9)
[   17.454337] ACPI: Fan [FAN] (on)
[   17.460282] ACPI: Thermal Zone [THRM] (36 C)
[   18.083859] usbcore: registered new interface driver usbfs
[   18.083881] usbcore: registered new interface driver hub
[   18.094913] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   18.095193] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   18.095200] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 22
[   18.095206] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.095934] usbcore: registered new device driver usb
[   18.106153] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.133818] SCSI subsystem initialized
[   18.158955] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.158962] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.182920] libata version 3.00 loaded.
[   18.306580] Floppy drive(s): fd0 is 1.44M
[   18.326153] FDC 0 is a post-1991 82077
[   18.614491] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x20 @ 9, addr 00:16:ec:89:66:0b
[   18.614496] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[   18.614891] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   18.614899] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 21
[   18.615061] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.615068] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.615329] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   18.615347] ohci_hcd 0000:00:02.0: irq 21, io mem 0xea004000
[   18.672080] usb usb1: configuration #1 chosen from 1 choice
[   18.672101] hub 1-0:1.0: USB hub found
[   18.672108] hub 1-0:1.0: 4 ports detected
[   18.774181] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[   18.774190] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 20
[   18.774343] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   18.774350] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   18.774406] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   18.774423] ohci_hcd 0000:00:02.1: irq 20, io mem 0xea005000
[   18.831819] usb usb2: configuration #1 chosen from 1 choice
[   18.831840] hub 2-0:1.0: USB hub found
[   18.831846] hub 2-0:1.0: 4 ports detected
[   18.934446] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   18.934451] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 22
[   18.934615] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   18.934622] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   18.934680] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   18.934707] ehci_hcd 0000:00:02.2: debug port 1
[   18.934710] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   18.934719] ehci_hcd 0000:00:02.2: irq 22, io mem 0xea000000
[   19.077358] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   19.089334] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.089436] usb usb3: configuration #1 chosen from 1 choice
[   19.089455] hub 3-0:1.0: USB hub found
[   19.089460] hub 3-0:1.0: 8 ports detected
[   19.193605] NFORCE3-250: IDE controller (0x10de:0x00e5 rev 0xa2) at  PCI slot 0000:00:08.0
[   19.193703] NFORCE3-250: not 100% native mode: will probe irqs later
[   19.193706] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   19.193710] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   19.193716]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.193724]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   19.193730] Probing IDE interface ide0...
[   20.079937] usb 3-4: new high speed USB device using ehci_hcd and address 3
[   20.151867] hda: WDC WD1200JB-00GVC0, ATA DISK drive
[   20.151900] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   20.153105] hda: UDMA/100 mode selected
[   20.154376] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.169923] Probing IDE interface ide1...
[   20.221643] usb 3-4: configuration #1 chosen from 1 choice
[   20.459350] usb 3-5: new high speed USB device using ehci_hcd and address 4
[   20.593880] usb 3-5: configuration #1 chosen from 1 choice
[   20.830809] usb 3-6: new high speed USB device using ehci_hcd and address 5
[   20.963870] usb 3-6: configuration #1 chosen from 1 choice
[   20.964223] hub 3-6:1.0: USB hub found
[   20.964769] hub 3-6:1.0: 4 ports detected
[   21.067409] usbcore: registered new interface driver libusual
[   21.071519] Initializing USB Mass Storage driver...
[   21.370026] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   21.573797] hdc: TSSTcorpCD/DVDW SH-S182M, ATAPI CD/DVD-ROM drive
[   21.573829] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   21.574182] hdc: UDMA/33 mode selected
[   21.574639] ide1 at 0x170-0x177,0x376 on irq 15
[   21.580847] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   21.580853] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 21 (level, high) -> IRQ 21
[   21.580912] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.580922] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[   21.584047] sata_nv 0000:00:0a.0: version 3.5
[   21.584063] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 21 (level, high) -> IRQ 21
[   21.584110] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.586869] usb 2-1: configuration #1 chosen from 1 choice
[   21.587604] scsi0 : sata_nv
[   21.588895] scsi1 : sata_nv
[   21.589076] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[   21.589078] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[   21.613221] scsi2 : SCSI emulation for USB Mass Storage devices
[   21.614843] usbcore: registered new interface driver usb-storage
[   21.614848] USB Mass Storage support registered.
[   21.614852] usb-storage: device found at 3
[   21.614853] usb-storage: waiting for device to settle before scanning
[   21.617594] usbcore: registered new interface driver hiddev
[   21.624035] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-1/2-1:1.0/input/input2
[   21.637791] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.1-1
[   21.649889] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-1/2-1:1.1/input/input3
[   21.661633] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.1-1
[   21.661648] usbcore: registered new interface driver usbhid
[   21.661651] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.897254] ata1: SATA link down (SStatus 0 SControl 300)
[   22.364583] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.373602] ata2.00: ATA-7: Maxtor 6L250S0, BACE1G20, max UDMA/133
[   22.373604] ata2.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   22.389579] ata2.00: configured for UDMA/133
[   22.389709] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BACE PQ: 0 ANSI: 5
[   22.399813] hda: max request size: 512KiB
[   22.401229] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[   22.404448] hda: cache flushes supported
[   22.404481]  hda:<4>Driver 'sd' needs updating - please use bus_type methods
[   22.407571] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   22.407580] sd 1:0:0:0: [sda] Write Protect is off
[   22.407582] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.407594] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.407633] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   22.407639] sd 1:0:0:0: [sda] Write Protect is off
[   22.407640] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.407650] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.407653]  sda: hda1 < hda5 sda1 sda2 < hda6 hda7 >
[   22.452864]  sda5<6>hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   22.464916] Uniform CD-ROM driver Revision: 3.20
[   22.468030]  sda6 >
[   22.468132] sd 1:0:0:0: [sda] Attached SCSI disk
[   22.481531] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   22.851691] Attempting manual resume
[   22.851695] swsusp: Resume From Partition 3:6
[   22.851696] PM: Checking swsusp image.
[   22.862331] PM: Resume from disk failed.
[   26.613092] usb-storage: device scan complete
[   26.614088] scsi 2:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[   26.615697] sd 2:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[   26.616071] sd 2:0:0:0: [sdb] Write Protect is off
[   26.616074] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   26.616076] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   26.618939] sd 2:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[   26.619313] sd 2:0:0:0: [sdb] Write Protect is off
[   26.619315] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   26.619317] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   26.619320]  sdb: sdb1
[   26.620751] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   26.620791] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.326943] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   29.510266] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.548963] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.698018] parport_pc 00:0a: reported by Plug and Play ACPI
[   29.698060] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   29.766149] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   29.766166] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   29.789911] input: Power Button (FF) as /devices/virtual/input/input5
[   29.849727] ACPI: Power Button (FF) [PWRF]
[   29.849783] input: Power Button (CM) as /devices/virtual/input/input6
[   29.881688] ACPI: Power Button (CM) [PWRB]
[   29.881741] input: Sleep Button (CM) as /devices/virtual/input/input7
[   29.905644] ACPI: Sleep Button (CM) [SLPB]
[   30.849438] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   30.849444] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 20
[   30.849653] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   31.171761] intel8x0_measure_ac97_clock: measured 54779 usecs
[   31.171766] intel8x0: clocking to 46954
[   31.522945] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   31.522954] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   31.631438] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xa400, speed 1173kHz
[   32.191964] usbcore: registered new interface driver cdc_ether
[   32.200154] usb 3-5: bad CDC descriptors
[   32.200172] usbcore: registered new interface driver rndis_host
[   34.950302] lp0: using parport0 (interrupt-driven).
[   35.053420] Adding 10241256k swap on /dev/hda6.  Priority:-1 extents:1 across:10241256k
[   37.614318] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.966879] No dock devices found.
[   38.076220] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   38.323887] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[   38.323911] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   38.331561] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   38.360889] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   39.292272] NET: Registered protocol family 10
[   39.292447] lo: Disabled Privacy Extensions
[   39.396593] ppdev: user-space parallel port driver
[   39.604923] audit(1205087268.752:2): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5473 profile="/usr/sbin/cupsd" namespace="default"
[   41.295629] eth0: no link during initialization.
[   41.296799] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.401062] Bluetooth: Core ver 2.11
[   41.401922] NET: Registered protocol family 31
[   41.401926] Bluetooth: HCI device and connection manager initialized
[   41.401930] Bluetooth: HCI socket layer initialized
[   41.424877] Bluetooth: L2CAP ver 2.9
[   41.424881] Bluetooth: L2CAP socket layer initialized
[   41.468670] Bluetooth: RFCOMM socket layer initialized
[   41.470225] Bluetooth: RFCOMM TTY layer initialized
[   41.470235] Bluetooth: RFCOMM ver 1.8
[   44.483687] [drm] Initialized drm 1.1.0 20060810
[ 4893.608326] usb 3-2: new high speed USB device using ehci_hcd and address 6
[ 4893.740940] usb 3-2: configuration #1 chosen from 1 choice
[ 4893.805989] ieee80211_crypt: registered algorithm 'NULL'
[ 4893.810144] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 4893.810149] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 4893.935851] usb 3-2: reset high speed USB device using ehci_hcd and address 6
[ 4894.068942] zd1211rw 3-2:1.0: eth1
[ 4894.068966] usbcore: registered new interface driver zd1211rw
[ 4894.230422] zd1211rw 3-2:1.0: firmware version 4725
[ 4894.270372] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[ 4894.288536] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4894.622649] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[ 4894.635950] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 4904.943831] eth1: no IPv6 routers present
[ 4977.671472] NET: Registered protocol family 17
[ 4978.572241] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[ 4978.586063] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 4978.611146] ieee80211_crypt: registered algorithm 'TKIP'
[ 4995.927439] eth1: no IPv6 routers present
[ 5560.717605] zd1211rw 3-2:1.0: zd_chip_control_leds error -110
[ 5718.680745] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[ 5718.782960] eth0: no link during initialization.
[ 5718.784144] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5719.341679] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[ 5719.342288] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[ 5719.349952] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[ 5719.378705] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[ 5729.457578] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5731.308282] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[ 5731.322207] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5747.562451] eth1: no IPv6 routers present
[ 7819.289663] usb 3-5: USB disconnect, address 4
[ 9022.936697] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 9022.948845] usbcore: registered new interface driver ndiswrapper
[ 9059.028676] usb 3-5: new high speed USB device using ehci_hcd and address 7
[ 9059.163294] usb 3-5: configuration #1 chosen from 1 choice
[ 9059.163862] usb 3-5: bad CDC descriptors
[ 9059.280310] usb 3-5: reset high speed USB device using ehci_hcd and address 7
[ 9059.415194] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 9059.415206] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsv2'
[ 9059.418177] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[ 9126.484120] usb 3-2: USB disconnect, address 6
[ 9126.494545] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[ 9134.400090] usb 3-5: USB disconnect, address 7
[ 9141.428763] usb 3-5: new high speed USB device using ehci_hcd and address 8
[ 9141.563312] usb 3-5: configuration #1 chosen from 1 choice
[ 9141.563528] usb 3-5: bad CDC descriptors
[ 9141.680409] usb 3-5: reset high speed USB device using ehci_hcd and address 8
[ 9141.815161] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 9141.815174] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsv2'
[ 9141.818132] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[ 9306.125111] usb 3-2: new high speed USB device using ehci_hcd and address 9
[ 9306.257730] usb 3-2: configuration #1 chosen from 1 choice
[ 9306.388737] usb 3-2: reset high speed USB device using ehci_hcd and address 9
[ 9306.523976] zd1211rw 3-2:1.0: eth1
[ 9306.623999] zd1211rw 3-2:1.0: firmware version 4725
[ 9306.663943] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[ 9306.682117] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9307.011230] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[ 9307.024281] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9317.085163] eth1: no IPv6 routers present
[ 9319.437359] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[ 9334.971133] eth1: no IPv6 routers present
[ 9679.963364] usb 3-5: USB disconnect, address 8
[ 9952.352774] usb 3-5: new high speed USB device using ehci_hcd and address 10
[ 9952.487343] usb 3-5: configuration #1 chosen from 1 choice
[ 9952.502987] usb 3-5: bad CDC descriptors
[11277.495923] usb 3-5: USB disconnect, address 10
[11793.669448] usb 3-5: new high speed USB device using ehci_hcd and address 11
[11793.803985] usb 3-5: configuration #1 chosen from 1 choice
[11793.809943] usb 3-5: bad CDC descriptors
[11986.127948] usb 3-5: USB disconnect, address 11
[11997.712540] usb 3-5: new high speed USB device using ehci_hcd and address 12
[11997.847116] usb 3-5: configuration #1 chosen from 1 choice
[11997.852891] usb 3-5: bad CDC descriptors
[11997.964177] usb 3-5: reset high speed USB device using ehci_hcd and address 12
[11998.100792] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[12283.719525] usb 3-5: USB disconnect, address 12
[12299.329659] usb 3-5: new high speed USB device using ehci_hcd and address 13
[12299.464171] usb 3-5: configuration #1 chosen from 1 choice
[12299.470193] usb 3-5: bad CDC descriptors
[12302.485310] usb 3-5: USB disconnect, address 13
[12572.207750] usb 3-2: USB disconnect, address 9
[12572.212599] zd1211rw 3-2:1.0: zd_chip_control_leds error -22
[12572.216612] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[12586.867250] usb 3-5: new high speed USB device using ehci_hcd and address 14
[12587.001858] usb 3-5: configuration #1 chosen from 1 choice
[12587.008042] usb 3-5: bad CDC descriptors
[12590.243654] usb 3-5: USB disconnect, address 14
[12596.692953] usb 3-2: new high speed USB device using ehci_hcd and address 15
[12596.825559] usb 3-2: configuration #1 chosen from 1 choice
[12596.952581] usb 3-2: reset high speed USB device using ehci_hcd and address 15
[12597.087267] zd1211rw 3-2:1.0: eth1
[12597.174227] zd1211rw 3-2:1.0: firmware version 4725
[12597.214174] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[12597.232359] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12597.570694] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[12597.583503] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[12608.451829] eth1: no IPv6 routers present
[12609.998338] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[12628.482680] eth1: no IPv6 routers present
[12634.418861] usb 3-2: USB disconnect, address 15
[12634.430073] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[12641.228151] usb 3-2: new high speed USB device using ehci_hcd and address 16
[12641.360754] usb 3-2: configuration #1 chosen from 1 choice
[12641.483778] usb 3-2: reset high speed USB device using ehci_hcd and address 16
[12641.619008] zd1211rw 3-2:1.0: eth1
[12641.688203] zd1211rw 3-2:1.0: firmware version 4725
[12641.728151] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[12641.746316] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12642.083423] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[12642.097497] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[12652.260081] eth1: no IPv6 routers present
[12654.513664] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[12671.636500] eth1: no IPv6 routers present
[12846.568918] usb 3-2: USB disconnect, address 16
[12846.578822] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[12856.668118] usb 3-5: new high speed USB device using ehci_hcd and address 17
[12856.802624] usb 3-5: configuration #1 chosen from 1 choice
[12856.809667] usb 3-5: bad CDC descriptors
[12856.927818] usb 3-5: reset high speed USB device using ehci_hcd and address 17
[12857.064245] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[12857.064258] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsv2-x64'
[12857.067396] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2-x64; check system log for messages from 'loadndisdriver'
[12989.083424] usb 3-2: new high speed USB device using ehci_hcd and address 18
[12989.216097] usb 3-2: configuration #1 chosen from 1 choice
[12989.331070] usb 3-2: reset high speed USB device using ehci_hcd and address 18
[12989.466195] zd1211rw 3-2:1.0: eth1
[12989.540564] zd1211rw 3-2:1.0: firmware version 4725
[12989.583498] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[12989.601661] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13001.936947] usb 3-5: USB disconnect, address 17
[13002.371094] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[13002.385288] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[13021.156741] eth1: no IPv6 routers present
[13264.515335] nautilus[5844]: segfault at 18 rip 4b6eee rsp 7fffb00de7b0 error 4
[14457.187158] usb 3-5: new high speed USB device using ehci_hcd and address 19
[14457.321802] usb 3-5: configuration #1 chosen from 1 choice
[14457.327695] usb 3-5: bad CDC descriptors

```




**And here is the highlights that I thought would be most helpful from the dmesg**
```

[ 5729.457578] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5731.308282] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[ 5731.322207] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5747.562451] eth1: no IPv6 routers present
[ 7819.289663] usb 3-5: USB disconnect, address 4
[ 9022.936697] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 9022.948845] usbcore: registered new interface driver ndiswrapper
[ 9059.028676] usb 3-5: new high speed USB device using ehci_hcd and address 7
[ 9059.163294] usb 3-5: configuration #1 chosen from 1 choice
[ 9059.163862] usb 3-5: bad CDC descriptors
[ 9059.280310] usb 3-5: reset high speed USB device using ehci_hcd and address 7
[ 9059.415194] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 9059.415206] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsv2'
[ 9059.418177] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2; check system log for messages from 'loadndisdriver'
[ 9126.484120] usb 3-2: USB disconnect, address 6
[ 9126.494545] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[ 9134.400090] usb 3-5: USB disconnect, address 7
[ 9141.428763] usb 3-5: new high speed USB device using ehci_hcd and address 8
[ 9141.563312] usb 3-5: configuration #1 chosen from 1 choice
[ 9141.563528] usb 3-5: bad CDC descriptors
[ 9141.680409] usb 3-5: reset high speed USB device using ehci_hcd and address 8
[ 9141.815161] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B


[12597.232359] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12597.570694] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[12597.583503] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[12608.451829] eth1: no IPv6 routers present
[12609.998338] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[12628.482680] eth1: no IPv6 routers present
[12634.418861] usb 3-2: USB disconnect, address 15
[12634.430073] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[12641.228151] usb 3-2: new high speed USB device using ehci_hcd and address 16
[12641.360754] usb 3-2: configuration #1 chosen from 1 choice
[12641.483778] usb 3-2: reset high speed USB device using ehci_hcd and address 16
[12641.619008] zd1211rw 3-2:1.0: eth1
[12641.688203] zd1211rw 3-2:1.0: firmware version 4725
[12641.728151] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[12641.746316] ADDRCONF(NETDEV_UP): eth1: link is not ready
[12642.083423] SoftMAC: Open Authentication completed with 00:0f:66:c2:cb:f3
[12642.097497] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[12652.260081] eth1: no IPv6 routers present
[12654.513664] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[12671.636500] eth1: no IPv6 routers present
[12846.568918] usb 3-2: USB disconnect, address 16
[12846.578822] zd1211rw 3-2:1.0: error ioread32(CR_REG1): -22
[12856.668118] usb 3-5: new high speed USB device using ehci_hcd and address 17
[12856.802624] usb 3-5: configuration #1 chosen from 1 choice
[12856.809667] usb 3-5: bad CDC descriptors
[12856.927818] usb 3-5: reset high speed USB device using ehci_hcd and address 17
[12857.064245] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[12857.064258] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wusb54gsv2-x64'
[12857.067396] ndiswrapper (load_wrap_driver:112): couldn't load driver wusb54gsv2-x64; check system log for messages from 'loadndisdriver'
[12989.083424] usb 3-2: new high speed USB device using ehci_hcd and address 18
[12989.216097] usb 3-2: configuration #1 chosen from 1 choice
[12989.331070] usb 3-2: reset high speed USB device using ehci_hcd and address 18
[12989.466195] zd1211rw 3-2:1.0: eth1
[12989.540564] zd1211rw 3-2:1.0: firmware version 4725
[12989.583498] zd1211rw 3-2:1.0: zd1211b chip 083a:4505 v4810 high 00-13-f7 AL2230_RF pa0 g--N-
[12989.601661] ADDRCONF(NETDEV_UP): eth1: link is not ready
[13001.936947] usb 3-5: USB disconnect, address 17
[13002.371094] SoftMAC: Open Authentication completed with 00:1c:10:4b:b2:79
[13002.385288] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[13021.156741] eth1: no IPv6 routers present
[13264.515335] nautilus[5844]: segfault at 18 rip 4b6eee rsp 7fffb00de7b0 error 4
[14457.187158] usb 3-5: new high speed USB device using ehci_hcd and address 19
[14457.321802] usb 3-5: configuration #1 chosen from 1 choice
[14457.327695] usb 3-5: bad CDC descriptors

```


Thanks!
-Mike

---

### Post by Modplanman on 2008-03-30
Overmind:

The problem is the same as I had. No matter which drivers you use, 64 or 32, Ndis still seems to recognise them as 32 bit, so basically doesn't work.

Uninstall Ndiswrapper completely, and follow what's said in this thread. 

Kernel headers does not mean a new kernel. Just run the update manager to make sure you're completely up to date and you should be fine. Alhough why you're using Hardy, which at the time of writing if I'm not mistaken was in Alpha when you don't seem to be the most technical of users (which is all an Alpha an OS should be for) I have no idea.

Btw, update on my own circumstances: It finally worked. The problem was idiocy on my part. I had proposed updates marked, so something amongst those unfinished updates must've caused the problem. The only other thing is occasionally when starting Ubuntu, sound doesn't work, but merely restarting again solves that, and might not even by related.

What I really came her to ask though: What with the final release of hardy imminent, will this still work once updated? Any signs of potential problems?

---

### Post by crazytrain1978 on 2008-04-07
> **heindsight said:**
> [B][COLOR="Red"][SIZE="4"]WARNING:[/SIZE][/COLOR] Don't follow these instructions unless you either know what you're doing, or are willing to learn the hard way. 
While it should be possible to fix things if something does go wrong, there is a risk that you could hose your system and you 
may end up having to reinstall. Make sure you read the entire thread before proceeding (especially if you don't know exactly what you're doing)[/B]

For the first step you will need internet access. You need the linux-headers and linux-source packages for your kernel. 
You can use uname -r to find out what kernel version you have, and then get the corresponding packages.  Also make 
sure you have make and gcc (and all their dependencies) installed. You can download the .debs for all these from
[packages.ubuntu.com]("http://packages.ubuntu.com") and install them using dpkg -i <deb file>

Now, find out the full path to the old modules that you're going to be replacing and make a note of
it. You'll need it if you want to restore the old modules. The modules should all be in
/lib/modules/<kernel-version>/kernel/drivers/net/usb but it can't hurt to make sure, by using
the following command:
```

find /lib/modules/`uname -r`/ -name usbnet.ko -or -name cdc_ether.ko -or -name ndis_host.ko

```

Now do the following to actually back up the files:
```

cd
mkdir wifi_backup
find /lib/modules/`uname -r`/ \( -name usbnet.ko -or -name cdc_ether.ko -or -name ndis_host.ko \) -exec cp \{\} wifi_backup \;

```

Now (assuming you extracted the archive with the new modules in your home directory) do the following to actually install the new drivers:
```

cd rndis_wlan
sudo ./clean.sh
make
sudo make install
```

If your kernel is older than 2.6.21, you may also need to add a udev rule to get the modules to load automatically. 
You can use the following command for that (replace the idProduct and idVendor values with the appropriate values  for your device):
```

sudo -i
echo "BUS==\"usb\", SYSFS{idProduct}==\"7051\", SYSFS{idVendor}==\"050d\", RUN+=\"/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'\"" > /etc/udev/rules.d/85-usb-rndis.rules
exit

```
Note that this step might not be needed (particularly if you have a newer kernel). Try going without it first.

Now if you plug in your device, the modules should load automatically. If you run the command iwconfig, your wifi device should appear. 
Now you should be able to use network-manager to set up your wifi network.

Hope this helps...



I am having a bit of trouble getting this going.

I have all the requirements and have tried this with both the rndis_wlan-snapshot-20071213.tar.gz and rndis_wlan-snapshot-20071220.tar.gz snapshots and each time i get this error:


john@linux-usb:~/Documents/rndis_wlan$ make
make -C /lib/modules/2.6.24-15-generic/build SUBDIRS=/home/john/Documents/rndis_wlan modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-15-generic'
  CC [M]  /home/john/Documents/rndis_wlan/usbnet.o
/home/john/Documents/rndis_wlan/usbnet.c: In function â€˜usbnet_probeâ€™:
/home/john/Documents/rndis_wlan/usbnet.c:1161: error: implicit declaration of function â€˜SET_MODULE_OWNERâ€™
make[2]: *** [/home/john/Documents/rndis_wlan/usbnet.o] Error 1
make[1]: *** [_module_/home/john/Documents/rndis_wlan] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-15-generic'
make: *** [default] Error 2
john@linux-usb:~/Documents/rndis_wlan$ 



does anyone know why? I am a bit lost. I am trying this to get my ASUS wl-169gE working.

if anyone has any suggestions I would be most obliged. :)

Cheers,
John

---

### Post by crazytrain1978 on 2008-04-08
anyone?

---

### Post by evilspy on 2008-04-21
rndis_wlan driver have been included into 2.6.25. So either compile 2.6.25 kernel or you could try use compat-wireless-2.6 package from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

I checked rndis_wlan in compat-wireless-2.6-2008-04-01 and it seems to be broken (I can almost certainly tell it will crash computer). Next compat-wireless version should have rndis_wlan fixed, I'veI reported compat-wireless maintainer about the problem.

---

### Post by Unix_Slayer on 2008-05-04
I hate to kill this discussion again but anyone have an answer to this? I got the Linksys wusb54gs.v1 adapter installed, and working using the following webpage ==> [http://linuxwireless.org/en/users/Download#Checkingoutcompat-wireless-2.6.gittree]("http://linuxwireless.org/en/users/Download#Checkingoutcompat-wireless-2.6.gittree"). Problem is KwiFiManager wont let me switch to the various wifi networks I have up. I see them, and they are visible. The button is greyed out for switching to a visible network. Any clues?

---

