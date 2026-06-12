---
title: "Getting wireless on a fujitsu lifebook"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by divadp on 2010-06-11
Running latest ubuntu on fujitsu lifebook s7210.

I am not a teckie! I have now managed to network linux laptop, and xp p on a wired peer to peer network. My ultimate aim is to be able to use the laptop on wieless (in the garden).

My next stage is to just try and pick up a wireless signal - from neighbours, or from my kodak photo frame.

I've downoaded swscanner and when I scan I get a message SIOCSIWMODE 1: operation not permitted
then SIOCSIFFLAGS 13 Permission denied
then INTERFACE DOES NOT SUPPORT SCANNING



I've searched various threads and seen lots of general problems with wireless, and seen an apparent lack of support for linux from Fujitsu. What do I do next? I am reluctant to start bashing stuff into the terminal until I know that its possible to get it working and that my machine will do it.

If wireless is going to be impossible with this machine under Linux I would like to know now so I can give up and go back to windows (with a heavy heart) and not spend more valuuable time on it.

Help! And thanks in anticipation.

---

### Post by Peter09 on 2010-06-11
first disconnect your wired network and then post the output of the terminal commands
 
```
ifconfig
```
and
```
 
lshw -C network

```

---

### Post by divadp on 2010-06-11
Thanks Peter. This was the result. All Greek to me I'm afraid.

eth0      Link encap:Ethernet  HWaddr 00:17:42:79:3c:38  
          inet6 addr: fe80::217:42ff:fe79:3c38/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5532678 (5.5 MB)  TX bytes:822376 (822.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:8f:d7:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B

------------------------------------------------


*-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:17:42:79:3c:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:fe300000-fe303fff ioport:2000(size=256) memory:88000000-8801ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 04
       serial: 00:16:44:8f:d7:32
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:fe200000-fe20ffff

---

### Post by Peter09 on 2010-06-11
Look at this thread
 
[http://ubuntuforums.org/showpost.php?p=8896751&postcount=3](http://ubuntuforums.org/showpost.php?p=8896751&postcount=3)
 
you will need to use the terminal, but its quite simple. You can cut and paste the commands into the terminal if you want.
 
EDIT: before you do that have you looked in System->Admin->Hardware
 
to see if a driver needs enabling?

---

### Post by divadp on 2010-06-11
OK Peter I've looked at that thread. I take it I need to do all the things in the thread.

I looked at the hardware drivers under system/admin as you suggested and it says there are no proprietary drivers in use.

So - what is happening then? I take it that I am short of drivers for the wirelsss part of my laptop?

Sorry to be a bit thick but this is an absolute beginners forum.

---

### Post by Peter09 on 2010-06-11
Also what do you see when you have the hard wired connection unplugged and you click on the network icon (top right).

---

### Post by divadp on 2010-06-11
Oh Peter this gets more difficult by the moment.

I did the thing in the post which applies the driver, and I saved it. But when I go back to tools admin drivers it again says there are no proprietary drivers. Yet when I run the command in the terminal it appears in the changed form.

With regard to network manager - I don't think I have that, and certainly not top right.

I've tried the suggested vthings of adding it to the panel but it just doesn't appear in the add panel list.


David

---

### Post by Peter09 on 2010-06-11
Network manager should look like a little fan, near the top right corner. It may not be there when your hard wired connection is active.

---

### Post by Peter09 on 2010-06-11
Try rebooting - by the way have you done an upgrade (using upgrade manager yet - you should do as sometimes drivers are downloaded when you do this.
Do these commands in a terminal, with your hardwired connection plugged in.
 
```
sudo apt-get update
```
and then
```
sudo apt-get upgrade
```

---

### Post by divadp on 2010-06-11
I have network tools, I have network connections but don't recall ever having network manager. I know what it looks like i just isn't there and can't be added to a panel.And yes I do have a notification area.

So why the problem getting the driver going?

---

### Post by Peter09 on 2010-06-11
It may be just that you do not have the right driver from the LiveCD. Make sure you do the update and upgrade - this will not only bring your system up to the latest bugfixes but will also grab any additional software needed. 
 
Best do that before anything else.

---

### Post by divadp on 2010-06-11
OK.

I've done the updates.

I've also deleted and re-installed network manager (it isn't called network connections is it?) and still don't get the option to add network manager to the panel.

I still can't get swscanner to pick up anything.

I still have no proprietary drivers on my system


In 10 minutes I'm off to play golf  which will probably be even more frustrating than ubunti !


If anyone has any more thoughts I'd be glad to hear them

Peter - thanks for your help I only wish I lived closer to Bedford - I'd probably leave this laptop on your doorstep!

David

---

### Post by Peter09 on 2010-06-11
you find network manager by right clicking on the top panel and adding it from the list of applets. Removing network manager may not have been a good idea

---

### Post by divadp on 2010-06-11
Networkmanager doesn't appear in the list of applets when I try to add it to the panel.

But when I go to applications/ubuntu software centre/internet  it is there with a tick by it to say it is installed.

I deleted and re-installed it in the expectation that it had become currupt.

David

Aghh

I'm off now - catch you all over the eekend when I will resume my quest

---

### Post by Peter09 on 2010-06-11
you need to go to system->admin->startup programs 
and make sure that network manager is selected to start up when you boot.

---

### Post by divadp on 2010-06-12
<snip>

For the sake of clarity I don't need or intend to steal bandwidth or anything else from my neighbours. 

I want my laptop to work wirelessly under Linux. At present I have a stable and effective wired network running under windows. Before I include a wireless router in the system I want to be able to demonstrate that the laptop can _see_ a wireless signal - from my kodak photoframe, or some other source. I mentioned neighbours because when the laptop had windows on it, it could do just that - not that I ever attempted to log on to it.

This is a help forum, and I'm a beginner who needs help. If you care to offer help I would be most grateful. <snip>

---

### Post by divadp on 2010-06-12
Peter

Thanks again for trying to help.

When I go to system/preferences/startup application.s network manager appears with a tick against it. 

When I go through the process of adding something I can't find where network manager is located on my system.

Any ideas?

---

### Post by Elfy on 2010-06-12
> My next stage is to just try and pick up a wireless signal - from neighbours, or from my kodak photo frame.If I had seen this post before it had been answered it is likely I would have closed the thread prior to getting some sort of confirmation from you regarding it. 

We get many threads/posts that try and get help in illegal activity - this is not the placed for that.

In future try and make your point in a less ambiguous way - it will lead to more productive support for you.

---

### Post by Peter09 on 2010-06-12
Try going to System->preferences->network

you may see your wired connection there. I suspect you are not seeing network manager because you have no wireless connection.

Check that you have the notifications applet installed on the top panel.

---

### Post by divadp on 2010-06-14
On system preferences network the tab for wireless is showing nothing

Curiously I have also not got a connection to my wired network any more. I must have done something to remve it. I can't access the ubuntu laptop from the windows machine, and the connection in the laptop has gone.

I have the notification applet installed.

I'm really struggling at this. Would it be sesible to remove ubuntu, reinstall it and start again?

Maybe I need to buy a book to help me.

---

### Post by Peter09 on 2010-06-14
I think, because you are now not in a good state, and we really do not know what has happened, the best thing would be a re-install. 
 
Don't think you need a book yet, reinstall, asses the situation and come back. Don't actually do anything to your system.

---

### Post by divadp on 2010-06-14
Ok I'm back.

I have re-installed ubuntu.

I now have network manager (up arrow and down arrow ikon)

Without loading additional software it has recognised my wired windows network. Though the windows network can't see the ubuntu network. Clearly I need to re-set the permissions etc.

I tried to add a wireless connection and gave the new network a name and key and now when I go to network manager I get that wireless is disconnected.

David

---

### Post by Peter09 on 2010-06-14
How are you trying to add a wireless network? All you need to do is left click on the network manager icon and select one of the visible networks in the list. You should not have to name any network.

---

### Post by divadp on 2010-06-14
When I go to network manager the wireless networks entry is greyed out.

Since the last message I have installed the networking software and SW scanner, and gone through the thing we did before about hardware drivers. There are still no hardware drivers showing though!



David

---

### Post by Peter09 on 2010-06-14
An up and down arrow icon suggests that you are connected, hard wired.

---

### Post by lkraemer on 2010-06-15
What is the Ubuntu Version? 8.04x, 8.10, 9.04, 9.10, 10.04, ????
32 bit or 64 Bit? .....Yes, it makes a difference!...Depending....
Laptop or Desktop?
USB Wifi Dongle or onboard Wifi?

**How do I know what Wifi Hardware is installed in my Computer?**

Open a Terminal Window, and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lspci -nn
lspci -vvx    (These give more detail)
lspci -vvxxx  (These give more detail)
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
ifconfig
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

**WHAT DRIVERS DO I USE?:**
Your Driver options will depend on your specific installed Hardware:
1. Ndiswrapper and a Windows Driver....maybe...bcmwl5.inf & sys
2. Default Drivers installed from the LiveCD
3. Madwifi Drivers
4. BROADCOM: bcm43xx module and some Firmware.... B43 & B43legacy *.fw
5. BROADCOM: b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.

**NDISWRAPPER & WINDOWS DRIVERS INFORMATION:**
Ndiswrapper and a Windows Driver....maybe...bcmwl5.inf & sys
The correct 32/64 Bit drivers must be used to match Ubuntu's 32/64 Bit.

**#1 - NDISWRAPPER**
To install the Windows Drivers that are located on your Desktop/Laptop
in a folder named broadcom (.sys & .inf files):
```

cd ~/Desktop/broadcom
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

**HOW TO REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. The command is:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Open a Terminal & Check for errors:
```

dmesg tail
lsmod

```
You may have to remove other modules depending on what lsmod shows:......example only.....
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using ndiswrapper.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

REF:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


**#2 - LIVECD DEFAULT DRIVERS**
```

lsmod

```
Look through the modules and see what is use as the default.........
for the Installed Version of Ubuntu, or from the LiveCD.
The default may/may not work with your hardware........

The first thing you need to do is to connect via Ethernet and enable
the Universe repository at SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
then Update the system at STSYEM -> ADMINISTRATION -> UPDATE MANAGER

Then look for any HARDWARE DRIVERS that can be installed.  Maybe your
Wifi will be fully functional after doing this.


**#3 - Madwifi Drivers**
**MADWIFI** - is yours supported:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility)

Current Drivers are located here:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
```

lsmod
cat /etc/modprobe.d/blacklist.conf

```
Will show what modules are currently installed.  You also need to view what modules
have been blacklisted........and maybe add modules that will conflict with madwifi....

If you download and compile the Mad Wifi Drivers you will need to have the following
installed:

build-essential 
Linux-headers (for your kernel version)

You will need to blacklist the ath & athk5 modules, then reboot.
```

sudo nano /etc/modprobe.d/blacklist.conf

```
adding the following at the end of the file:
```

blacklist ath
blacklist ath5k

```

Create a Subdirectory for the CURRENT madwifi Version:
I created a subdirectory named madwifi-AR5007 under my home directory.

I used the following commands for Ubuntu 8.04.4 with the Wifi Drivers:
```

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
sudo mkdir madwifi-AR5007
cd madwifi-AR5007
wget -O driver.tar.gz http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
tar xf driver.tar.gz
cd madwifi-*
make clean
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

```
Once this is all straightened up..........
I'd try:
```

sudo /etc/init.d/networking restart

```
Then also do a re-boot.......
Finally make sure that the Wifi is ENABLED by right clicking on the Wifi ICON
in the Top Right Menu and VERIFYING that Wireless has a Check Mark.

**MADWIFI PROBLEMS: **
[http://ubuntuforums.org/showthread.php?t=1257103&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1257103&highlight=madwifi)

**HOW TO UPDATE MADWIFI DRIVERS:**
[http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi)

REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

REF: 32 Bit - Reference URL'S:
[http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/](http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/)
[http://www.linuxforums.org/articles/wlan-cards-and-linux_58.html](http://www.linuxforums.org/articles/wlan-cards-and-linux_58.html)
[http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver](http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver)

REF: 64 Bit Info:
[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278)


**#4 - BROADCOM b43xx**
If you just need the Broadcom firmware for b43xx it can be found on
the internet.
 
Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [http://www.omattos.com/node/6](http://www.omattos.com/node/6)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```


**#5 - BROADCOM b43**
B43 doesn't appear to be supported by 9.04 according to searches of
the forum. It most likely is the best way to go with 9.10 as B43 is
installed. So all you would need to do is download the Firmware,
extract the folders/files and copy them to /lib/firmware and to /lib/firmware/b43
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

You may need to Blacklist some driver to get it working. Look at
the results of lsmod to see what was installed..........
If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to remove them and blacklist them, since you are going to
be using b43. Be sure to insert a # at the beginning of the line if
any of the existing driver modules are blacklisted, and you will be
using them. You may have to remove the following depending on what lsmod
shows: (DON'T BLACKLIST SSB)
```

modprobe -r b44
modprobe -r b43legacy

```

OK, let's verify that everything is placed as it should be. In a Terminal Window do:
```

cd /
cd /lib/firmware/b43
ls -alt

```
You should see a listing of the *.fw files. Then do:
```

cd ..
cd /b43legacy
ls -alt

```
You should see more *.fw files. You should have used some command similar to this to copy the files:
```

sudo cp -r /home/loginname/Desktop/b43* /lib/firmware

```
If the folders are present and filled with *.fw files do the following
ndiswrapper command in lowercase (last letter is a lowercase "L"):
```

ndiswrapper -l
lsmod
cat /etc/modprobe.d/blacklist.conf

```
Post the output of these commands. The first command should show as an
error if you correctly removed ndiswrapper. Look for modules that need
to be removed. Module b43xx, and ndiswrapper shouldn't be found.
If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to blacklist them, since you are going to be using b43.
IF b43 SHOWS AS BEING BLACKLISTED, INSERT A # IN FRONT OF EACH
TO ENABLE THE USE OF b43. You may have to remove some (one) of
the following depending on what lsmod shows as being loaded:
```

modprobe -r b43xx
modprobe -r b43legacy
ifconfig
iwconfig

```
Post the output of the last two commands.


**MANUAL CONFIGURATION:**
iwconfig should display something like the following:
```

ath0      IEEE 802.11g  ESSID:"Airlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:A3:91:B0:B2   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:57687  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
At this point you know your Router's ESSID, that ath0 (in my case) is the
router, and you should be able to bring it up manually.
Replace the <interface> below with your actual interface.
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
In my case it would look like this:
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo iwconfig ath0 essid "Airlink"
sudo iwconfig ath0 mode Managed
sudo ifconfig ath0 up
sudo dhclient ath0

```
You may want to do
```

sudo /etc/init.d/networking restart

```

Good Luck!
Completed..... 06-16-2010

lk

---

### Post by lkraemer on 2010-06-15
1.  What version of Ubuntu ????

From what you sent me.......
```

cat /etc/modprobe.d/blacklist.conf

```
```

This file lists those modules which we don't want to be loaded by
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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```
I don't see anything that looks questionable.

```

lshw -C network

```

```

*-network
description: Ethernet interface
product: 88E8055 PCI-E Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 14
serial: 00:17:42:79:3c:38
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.0.4 latency=0 multicast=yes
resources: irq:27 memory:fe300000-fe303fff ioport:2000(size=256) memory:88000000-8801ffff(prefetchable)
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:14:00.0
logical name: wlan0
version: 04
serial: 00:16:44:8f:d7:32
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:19 memory:fe200000-fe20ffff

```
Looks good too....

```

lsmod

```

```

Module Size Used by
binfmt_misc 6587 1
snd_hda_codec_realtek 203168 1
fbcon 35102 71
tileblit 2031 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
joydev 8708 0
snd_hda_intel 21877 2
snd_hda_codec 74201 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70662 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0
arc4 1153 2
usbhid 36110 0
pcmcia 33024 0
snd_seq_oss 26726 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
i915 282354 3
drm_kms_helper 29297 1 i915
ppdev 5259 0
snd 54148 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_se q_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid 67032 1 usbhid
ath5k 121792 0
yenta_socket 20408 4
intel_agp 24177 2 i915
rsrc_nonstatic 10015 1 yenta_socket
parport_pc 25962 1
drm 162471 4 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
soundcore 6620 1 snd
sdhci_pci 5470 0
sdhci 15462 1 sdhci_pci
fujitsu_laptop 10889 0
mac80211 204922 1 ath5k
psmouse 63245 0
ath 7611 1 ath5k
serio_raw 3978 0
cfg80211 126485 3 ath5k,mac80211,ath
led_class 2864 3 ath5k,sdhci,fujitsu_laptop
agpgart 31724 2 intel_agp,drm
pcmcia_core 32964 3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
video 17375 1 i915
output 1871 1 video
lp 7028 0
parport 32635 3 ppdev,parport_pc,lp
sky2 40775 0

```
shows that ath5k is being used for the Atheros Wifi.  I'd expect it to
work out of the box, but it doesn't.

```

lspci

```

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 04)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```
Shows AR5001 (Rev 04) as existing.

If you left click on the Network/Wifi Icon in the Top right Menu, is Wired and Wifi Networking
"ENABLED".  If so, at this point I'd suggest you try blacklisting ath5k & ath, and try using the
MadWifi Drivers as they should work fine.  Google searches of your Make & Model didn't find
any good information.

lk

---

### Post by divadp on 2010-06-15
Firstly and most important a big thank you for your extensive posts lk.

Context for me is that I haven't done this kind of stuff since I learnt  to use DOS on a TRS 80, and basic programming on a commodore 64! I have grown accustomed to windows, and plug and play where I know as little about my pc as I do about how my tv works.

I have version 10.04. of UBUNTU and have loaded the updates. Its running on a laptop with built in Wifi (I think). The wifi is Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 04) which I learned from lspci

At this time the network manager ikon has disappeared again and I can't get it back by moving the location of the panel around as I have done before, and I won't re-install unless advised to do so. If I go to 'add to panel', Network manager isn't listed. Agh why does this happen? Previously though although wired is enabled wifi is not.

I'll go and look at madwifi drivers to find to find out if the AR5001 is supported. I take it I then follow #3 in your previous post.

David

---

### Post by divadp on 2010-06-15
Oh dear!

I'm finding installing a driver from madwifi hard going.

The organisation name should have given me a clue! The language they use is a bit odd. Am I the only one who doesn't know what a tar ball is? 

So Anyone prepared to give me an idiots guide to installing madwifi?

---

### Post by lkraemer on 2010-06-16
It is all spelled out in #3 above.  You shouldn't have any trouble.
Just read one line, and work one line at a time.  Shouldn't be a 
problem.

I've updated #3 a bit to make it more detailed, just print it out,
go step by step, and you will be fine.

Post if you have any problems/questions.......

TRS-80 Model I or III or what model?  I used to run CP/M on my
Model 4 (Montezuma Micro), Also have a Model I still in the basement
with three 5 1/4" Drives that would write on the back side of floppy's.
Last time I tried to boot it it wouldn't come up....
 
lk

---

### Post by lkraemer on 2010-06-16
NetworkManager Applet 0.8 Missing:
I found this information, so give it a try.....

I think NM has issues when
1)nm-system-settings.conf says managed=false
To solve this
```

gksudo gedit /etc/NetworkManager/nm-system-settings.conf

```
and set
```

managed=true

```
**OR**
2)/etc/network/interfaces contain anything other than
```

auto lo
iface lo inet loopback

```
To solve this comment other lines(or backup the file and edit it so that it contains only those lines)
Restart the machine after doing this
Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
Note :Always backup files before editing

lk

---

### Post by divadp on 2010-06-16
I went to [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

"We generate tarballs containing the latest subversion revision of various repository branches once a day. Use them if you want to avoid to get in touch with the subversion tools,  

It may be a cultural thing but I really have trouble deciphering this. This isn't written for folk like me! What on earth is a tarball?

So I go to [http://madwifi-project.org](http://madwifi-project.org)

So there are three versions. Do I need madwifi, ath5k, or ath9k?

madwifi needs HAL version 0.9.4 ( I also need to know if I'm using kernel 2.6.25 or newer. I haven't a clue!

i guess I need ath5k. I deduce this because my wireless adapter is described as AR5001 (when I ran lshw).


I go to the about ath5k page and find this is still in development and they need help. That doesn't fill me with confidence.

If I do install ath5k I'll need to enable mac80211:

The code is given. Should I do this or check wether I really ought to use madwifi. It is comforting that there is a download button for this. Maybe this is a better bet!

Before I do I'll check cat /etc/modprobe.d/blacklist.conf
OK I don't see problems.

lk says I need 
build-essential
linux-header (for my kernel version) - which I don't know how to find.
I'll look for these!

I've found on google that I need to do

gksudo aptitude install build-essential.

I did it!


Except it says Linux-headers will be removed.

The following NEW packages will be installed:
  build-essential dpkg-dev{a} fakeroot{a} g++{a} g++-4.4{a} 
  libstdc++6-4.4-dev{a} patch{a} xz-utils{a} 
The following packages will be REMOVED:
  linux-headers-2.6.32-21{u} linux-headers-2.6.32-21-generic{u} 
0 packages upgraded, 8 newly installed, 2 to remove and 31 not upgraded.
Need to get 7,571kB of archives. After unipacking 60.6MB will be freed.
Do you want to continue? [Y/n/

I decided o go with it. Perhaps the Linux-header removed are ones I don't need or can be added back.

This seems to hang or go in a loop, or be taking a long time to do something. If I try to close the terminal it says a process is still running.

I need to find my kernel. Google says uname -a will do it.

ok its 2.6.32-22 so later than 2.6.25.
Have I compiled it? Don't know!

Time to blacklist.

Ok this seems to have worked but I still can't close the terminal without the message about a process running.

I've pressed on and put the folder I downloaded inside a folder in my home directory

OK this looks all wrong. The install build-essential is still hung and I have to close it.

So where now? I don't feel confident to run the commands listrd unde #3. The one that started sudo aptitude update &&u etc etc

I'll try to install build-essential from cd

Wow this caused lots to happen. This is what I did
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

OK time for bed. Does all this sound ok?

---

