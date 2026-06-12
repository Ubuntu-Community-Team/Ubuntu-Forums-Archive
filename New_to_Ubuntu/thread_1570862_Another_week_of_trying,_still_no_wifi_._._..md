---
title: "Another week of trying, still no wifi . . ."
date: 2010-09-08
forum: New to Ubuntu
---

### Post by hiloguy37 on 2010-09-08
Dell XPS M1530, with Ubuntu 9.04 dual boot with XP-Pro.  The wireless card, according to Windows, is Dell Wireless 1395 802.11 a/b/g/N Mini Card.  SourceForge.net shows several real close to that but no 1395.  The closest is 14e4:4311. I jumped through the hoops in my 983-page Ubuntu for Beginners book and followed the somewhat cryptic directions of many posts here to the best of my noobie ability and still, my computer will not even recognize that there is a driver installed.  I installed the .inf and .sys files with ndiswrapper and also tried to install the .inf file in the "windows drivers" box.  That gave me this message: "Hardware present: No."

The Drivers window finds ONLY my graphics drivers, nothing else.

The wifi works fine in Windows, so the hardware is indeed present.  Matter of fact, when I first booted up the new Ubuntu installation, the wifi worked for about one minute and then the wifi icon disappeared from the top of the screen.

Does anyone please-oh-please have a step-by-step instructions on how to get this thing going?  Everything else is great with the installation except without the wifi, the whole thing is worthless.  I have run into dozens of blind alleys following detailed instructions only to end up, after another few hours, being asked to work with a menu that does not exist.

Please?

---

### Post by GaryTheCat on 2010-09-08
what does ubuntu say the wireless card is?

Can you post the output of 

```
lspci
```

---

### Post by sandyd on 2010-09-08
try installing b43-fwcutter.

---

### Post by someoneinpnw on 2010-09-08
I got this same problem with hiloguy37. I have Dell Inspiron 1525 laptop using Dell Wireless 1395 WLAN Mini-card (This is what Windows Vista says I have). Here is the output using CODE: lspci

   hai@ubuntu:~$ lspci
  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
  00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
  00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
  00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
  00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
  00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
  00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
  00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
  00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
  00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
  00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
  00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
  00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
  00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
  00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
  02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
  09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
  0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  hai@ubuntu:~$

---

### Post by cranecreek on 2010-09-08
I also have a Dell. Not sure if this will help but... If my wireless is turned off during a session and I reboot, the wireless will not work by turning it back on. Make sure your wireless is turned on then reboot.

---

### Post by hiloguy37 on 2010-09-08
> **GaryTheCat said:**
> what does ubuntu say the wireless card is?

Can you post the output of 

```
lspci
```


"Pro Wireless 4965 AG or AGN (Kedron) Network Connection (rev61)"

---

### Post by Darkness Des on 2010-09-08
I have the exact same card. Connect with a wired connection to your router, make sure it's connected to the internet through there, and install the package *bcmwl-kernel-source* with Synaptic. Reboot, and it'll be working. I've also had trouble with MAC filtering on my router with this card, that may also be a problem. I never found a solution, I just switched to WPA2 (more security than the average user needs) and got a strong password. Either way, you have to install that package for your card to work at all.

---

### Post by anewguy on 2010-09-08
If it's a Broadcom chipset, as seems to be indicated by Darkness Des's latest post about using the bcmwl-kernel-source, I'd be curious if what normally works with Broadcom chipsets works with yours as well:

- do the hard wire connection to your router

- open a terminal window (applications/accessories/terminal)

- type:

sudo apt-get update <press enter>  enter your log in password when prompted.

Wait for this to finish.

- go to system/administration/hardware drivers.  There should be a driver listed there now for your wireless card - be sure to enable it.

- physically disconnect the hard wire connection

- right-click on the network manager icon and be sure "Enable Wireless" is checked.  Close out of network manager.

- left-click on network manager and see if you now have wireless networks showing.

Dave ;)

---

### Post by hiloguy37 on 2010-09-08
> **Darkness Des said:**
> I have the exact same card. Connect with a wired connection to your router, make sure it's connected to the internet through there, and install the package *bcmwl-kernel-source* with Synaptic. Reboot, and it'll be working. I've also had trouble with MAC filtering on my router with this card, that may also be a problem. I never found a solution, I just switched to WPA2 (more security than the average user needs) and got a strong password. Either way, you have to install that package for your card to work at all.


Well, ya got me all excited there.  I did as you suggested, the process seems to have worked, I rebooted, same old no-wifi.

The icon up at the upper right of the display is not there anymore.  Is that a clue?  I'll bet there's some little trigger I need to pull and it will be working . . . just have to find it.

How do I get the wireless icon back up there?  It used to be there but grayed out to a right click.  Now the icon has vanished, as if to say, "stop bothering me!"

---

### Post by sandyd on 2010-09-09
> **anewguy said:**
> If it's a Broadcom chipset, as seems to be indicated by Darkness Des's latest post about using the bcmwl-kernel-source, I'd be curious if what normally works with Broadcom chipsets works with yours as well:

- do the hard wire connection to your router

- open a terminal window (applications/accessories/terminal)

- type:

sudo apt-get update <press enter>  enter your log in password when prompted.

Wait for this to finish.

- go to system/administration/hardware drivers.  There should be a driver listed there now for your wireless card - be sure to enable it.

- physically disconnect the hard wire connection

- right-click on the network manager icon and be sure "Enable Wireless" is checked.  Close out of network manager.

- left-click on network manager and see if you now have wireless networks showing.

Dave ;)

 hey can you do me a favour and teach him how to blacklist the bcmwl driver (the module is called "wl") and try ndiswrapper/ndisgtk instead? theirs many threads about that card, however most success stories, it seems deals with nspluginwrapper. However, I as you know have an adversion to it, and I dont think the OP wants me to use his computer to learn how to use ndiswrapper :D ;)

---

### Post by hiloguy37 on 2010-09-09
> **sandyd said:**
> hey can you do me a favour and teach him how to blacklist the bcmwl driver (the module is called "wl") and try ndiswrapper/ndisgtk instead? theirs many threads about that card, however most success stories, it seems deals with nspluginwrapper. However, I as you know have an adversion to it, and I dont think the OP wants me to use his computer to learn how to use ndiswrapper :D ;)


I got to: - "go to system/administration/hardware drivers.  There should be a  driver listed there now for your wireless card - be sure to enable it." and what I get is the same old "Hardware Drivers" box that lists only the two NVIDIA Graphics drivers (the one running and the alternate).  I've notyet been able to anywhere get Ubuntu to recognize that there is a driver installed.

Now what?  I just have this feeling that we're getting close . . .

---

### Post by anewguy on 2010-09-09
> **sandyd said:**
> hey can you do me a favour and teach him how to blacklist the bcmwl driver (the module is called "wl") and try ndiswrapper/ndisgtk instead? theirs many threads about that card, however most success stories, it seems deals with nspluginwrapper. However, I as you know have an adversion to it, and I dont think the OP wants me to use his computer to learn how to use ndiswrapper :D ;)

Not a problem!  We'll start with just ndiswrapper and ndisgtk, as ndisgtk seems to blacklist things on it's own.  If it doesn't work after ndisgtk we can always blacklist the module(s) ( I think there are 2 or 3 others - like SSB, B42, and "something").

For the OP, here's what we are going to try:  Linux has a utility called ndiswrapper that allows you to use the Windows XP wireless drivers for your adapter in Linux.  Ndiswrapper itself is based in the command line, and requires quite a bit of typing - easy, but still room for errors.  There is another utility called ndisgtk, which brings a GUI interface to ndiswrapper and handles all kinds of things on its own.  So, here are the prep steps you'll need to do:

- copy the .inf and .sys files for the XP driver for your adapter to your Ubuntu desktop.

- have your LiveCD that you installed from handy (or if you used a USb flash drive, have it handy)

Now we'll go into the steps to install the ndiswrapper and ndisgtk programs:

- place your LiveCD in the drive and let it spin up.  If you get a message about a software disk being found, just cancel it.  If you used a USB flash drive, be sure it is plugged in.

- using the file browser "Places", look at the LiveCD (or flash drive).  You want to go to the pool/main/n folder.  There you will find 2 folders:  ndisgtk and ndiswrapper.  Go to the ndiswrapper folder first.  There you will see 2 files - 1 for ndiswrapper common and 1 for ndiswrapper utilities.  Double-click the ndiswrapper common file to start its installation and wait for it to finish.  Next, double-click on the ndiswrapper utilities file to start its installation and wait for it to finish.

- now back up to the /pool/main/n folder, then go to the ndisgtk folder.  There you will find a file for ndisgtk.  Double-click on it to start its installation and wait for it to finish.

You have now completed the installation of ndiswrapper and its GUI'd front end ndisgtk, so you can remove the LiveCD (or flash drive).

Now to install the driver:

Go to System/Administration/Windows Wireless Drivers - this starts ndisgtk.  

If anything shows, delete/remove them until nothing shows.

Now click on the "new" (or is it "Add") and when the box comes up point it to your desktop and the .inf file.  When you finish, it should show the device as installed and ready.

Suppossedly at this point the driver should be installed.  Next we need to be sure you are "ready" for wireless:

- right-click the network manager icon and be sure the "Enable Wireless" is checked.

- close network manager

- left-click on the network manager icon - you should see wireless networks now.

Some things to be aware of:

- if you use MAC filtering on the router, be sure your computers MAC address is in the allowed list in the router

- if you use encryption, be sure to specify the correct type and the password/passphrase when setting up the connection in network manager

- if your routers' network name (SSID or ESSID) is hidden (not broadcast by the router), you must manually set up the connection via network manager.

Please ask any questions you have, and let us know how this goes.

Dave ;)

---

### Post by hiloguy37 on 2010-09-09
> **sandyd said:**
> hey can you do me a favour and teach him how to blacklist the bcmwl driver (the module is called "wl") and try ndiswrapper/ndisgtk instead? theirs many threads about that card, however most success stories, it seems deals with nspluginwrapper. However, I as you know have an adversion to it, and I dont think the OP wants me to use his computer to learn how to use ndiswrapper :D ;)
   

Been there.  Done that.  It's hard to blacklist a driver that isn't there, and the ONLY drivers that show up are the NVIDIA display drivers (the one that's running and an option). I did the ndiswrapper/ndisgtk process, very carefully, three times, rebooted each time, and still no driver is showing up as being installed or even waiting to be installed.  It still seems strange to me that this process is still such a mindwarp after years and years of so many people having the same issue.

---

### Post by Peter09 on 2010-09-09
Don't like to butt in here but can I suggest you take stock of where you are and check that everything you think you have done is done. One of the problems found is that often the system gets into a state where people are trying to do too many things at once and there is no baseline to check against. Can I suggest that you post the output of```
 ifconfig
``` and```
 lshw -C network
``` again so that we know where you are and what is happening. NOTE: do the  ifconfig without a hardwired connection.

The point is that by this stage you should have a connection so we need to understand why you have not.

---

### Post by hiloguy37 on 2010-09-09
> **Peter09 said:**
> Don't like to butt in here but can I suggest you take stock of where you are and check that everything you think you have done is done. One of the problems found is that often the system gets into a state where people are trying to do too many things at once and there is no baseline to check against. Can I suggest that you post the output of```
 ifconfig
``` and```
 lshw -C network
``` again so that we know where you are and what is happening. NOTE: do the  ifconfig without a hardwired connection.

The point is that by this stage you should have a connection so we need to understand why you have not.
[B]
ifconfig:[/B] (with no internet connection)

          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:69:f7:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-69-F7-11-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**lshw -C network:**

hiloguy@hiloguy-XPS:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:df:49:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:29 memory:f9ffc000-f9ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:69:f7:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f9efe000-f9efffff

---

### Post by anewguy on 2010-09-09
If you notice your wireless in the last post, is says it is using the iwlagn driver either by default or by what you have tried to install.

You say you've done the ndiswrapper thing with nothing showing.  Be aware that one mistake with ndiswrapper and you can end up with a device defined but not working.  What we need to do is clean the slate and retry it:

- be sure you have the correct Windows _XP_ driver for your adapter.  I'm not sure any Broadcom driver is the way to go considering what it shows as the current driver.  If it was Broadcom, I would have thought it would show B42, SSB, something like that.

- open a terminal window and do the following:

sudo ndiswrapper -l <press enter> That's a lower case "L" for list.

That *should* return nothing at this point.  If not, you will see a driver/device listed, which you will need to delete:

sudo ndiswrapper -e xxxxx <press enter> Where xxxxx is the name of the driver/device showing in the list command.

Repeat the above until the ndiswrapper -l returns nothing.

Then try ndisgtk again, pointing to the correct .inf file (and being sure the appropriate .sys file(s) are in the same folder).  Do a screen print of what ndisgtk shows after you add your device and post it here.  Also post the names of the .inf and .sys files you are using.

Also:

lsmod <press enter> Post the output of that back here as well.

Sometimes it's best to completely back out anything you have tried and be sure you are back at a clean slate before trying anything else.

Dave

---

### Post by hiloguy37 on 2010-09-10
> **anewguy said:**
> If you notice your wireless in the last post, is says it is using the iwlagn driver either by default or by what you have tried to install.

You say you've done the ndiswrapper thing with nothing showing.  Be aware that one mistake with ndiswrapper and you can end up with a device defined but not working.  What we need to do is clean the slate and retry it:

- be sure you have the correct Windows _XP_ driver for your adapter.  I'm not sure any Broadcom driver is the way to go considering what it shows as the current driver.  If it was Broadcom, I would have thought it would show B42, SSB, something like that.

- open a terminal window and do the following:

sudo ndiswrapper -l <press enter> That's a lower case "L" for list.

That *should* return nothing at this point.  If not, you will see a driver/device listed, which you will need to delete:

sudo ndiswrapper -e xxxxx <press enter> Where xxxxx is the name of the driver/device showing in the list command.

Repeat the above until the ndiswrapper -l returns nothing.

Then try ndisgtk again, pointing to the correct .inf file (and being sure the appropriate .sys file(s) are in the same folder).  Do a screen print of what ndisgtk shows after you add your device and post it here.  Also post the names of the .inf and .sys files you are using.

Also:

lsmod <press enter> Post the output of that back here as well.

Sometimes it's best to completely back out anything you have tried and be sure you are back at a clean slate before trying anything else.

Dave

**lsmod:**

imer,snd_seq_device
sdhci                  17632  1 sdhci_pci
led_class               4096  2 iwlcore,sdhci
ricoh_mmc               3676  0 
nvidia               9587272  38 
dcdbas                  7332  1 dell_laptop
btusb                  11856  2 
lp                      8964  0 
parport                35340  2 ppdev,lp
iptable_filter          3100  0 
soundcore               7264  1 snd
ip_tables              11692  1 iptable_filter
cfg80211               93052  3 iwlagn,iwlcore,mac80211
x_tables               16544  1 ip_tables
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
usbhid                 38304  0 
ohci1394               30220  0 
ieee1394               86628  1 ohci1394
video                  19380  0 
output                  2780  1 video
sky2                   47040  0 
intel_agp              27748  0 
agpgart                35020  2 nvidia,intel_agp
hiloguy@hiloguy-XPS:~$ 

**The driver files I installed were:**

bcmwl5.inf
bcmwl5.sys

After I installed the driver files, I got this message: "hardware present: no."

I do love a good mystery, and thank you for your patience!

Someone else posting in this thread said that s/he had the same laptop with the same wireless card and this all seemed to work . . .

---

### Post by hiloguy37 on 2010-09-10
> **Darkness Des said:**
> I have the exact same card. Connect with a wired connection to your router, make sure it's connected to the internet through there, and install the package *bcmwl-kernel-source* with Synaptic. Reboot, and it'll be working. I've also had trouble with MAC filtering on my router with this card, that may also be a problem. I never found a solution, I just switched to WPA2 (more security than the average user needs) and got a strong password. Either way, you have to install that package for your card to work at all.


OK, you have the exact same card, so what drivers did you install to get it to work?  Seems like if I used the same exact .ini and .sys files, it oughta work?

---

### Post by Peter09 on 2010-09-10
Ok here is a thread that seems to be a solution
 
[http://ubuntuforums.org/showthread.php?t=969178](http://ubuntuforums.org/showthread.php?t=969178)
 
it seems to suggest that you need to install the backports module (you can do this through the sources manager)
 
However this thread suggests it may be an on-going problem
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708)

---

### Post by hiloguy37 on 2010-09-10
> **Peter09 said:**
> Ok here is a thread that seems to be a solution
 
[http://ubuntuforums.org/showthread.php?t=969178](http://ubuntuforums.org/showthread.php?t=969178)
 
it seems to suggest that you need to install the backports module (you can do this through the sources manager)
 
However this thread suggests it may be an on-going problem
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708)

What I'm hearing is that this, the third laptop on which I have not been able to get a wireless connection is kinda just the way it is and I shouldn't really expect it to ever work properly.  These are not some weird, brand-x laptops; they are Dell's most common laptops that use the world's most common wireless hardware.  Dell even shipped the XPS M1530's with Ubuntu brand new, so somebody has to know how to make it work.  What a shame.  Seems this is the Big Hurdle that keeps many, many people away from what would otherwise be THE OS of Choice.

---

### Post by anewguy on 2010-09-12
[QUOTE=hiloguy37

**The driver files I installed were:**

bcmwl5.inf
bcmwl5.sys

After I installed the driver files, I got this message: "hardware present: no."

I do love a good mystery, and thank you for your patience!

[/QUOTE]

Well, part of the problem is the broadcom drivers don't appear to be the correct drivers for your wireless - that's probably why it says no device present.

There are a few posts on the net that suggest you have to be sure the wireless is enabled (apparently some sort of switch or something) hardware wise first as well.

Also, with ndiswrapper you must use the Windows XP drivers.  I downloaded the latest set of drivers from Intel that are *supposed* to be for your adapter - they appears to be NETw5x32.inf and NETw532.sys.  *IF* you want to try these with ndiswrapper, be sure you do the command line ndiswrapper things I posted for removing any existing first, then use ndisgtk (System/Administration/Windows Wireless Drivers) to install them.  If there is a hardware switch for your adapter, be sure it is turned on BEFORE you try installing the driver.  After the driver is installed you will also need to be sure "Enable Wireless" is checked in network manager.

To get the driver:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=19146&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=19146&lang=eng)

Select the .zip file.  You will be asked to agree to license agreement, etc., and then eventually get to the actual download page - on this page you need to select the .zip file again.

If you have any questions please post back.

Dave ;)

---

