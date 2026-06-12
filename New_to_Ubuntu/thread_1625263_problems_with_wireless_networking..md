---
title: "problems with wireless networking."
date: 2010-11-18
forum: New to Ubuntu
---

### Post by creepy steve on 2010-11-18
with 10.04 i am having issues connecting to my wireless network. i connect but it never goes out of loading mode.  using other os's it works just fine. wtf??? i feel so stupid here. can anyone help?

---

### Post by jimrz on 2010-11-18
it would likely help us to assist you if you were to post which version of ubuntu you are using and what wireless equipment you are trying to get going

---

### Post by creepy steve on 2010-11-18
sorry. i am running umbuntu 10.04 i installed from a live 9.10 i386 then updated. i have a belkin n wireless finding my network with a netgear router. even if i do connect to the network i cant pull up any sites. weird.

---

### Post by anewguy on 2010-11-19
I don't know if it would have anything to do with it, but normally I would recommend backing everything up, then deleting the old OS (9.10) before a clean install of the new OS(10.04) instead of an update as you say you did.  I have heard somethings about old libs, etc., sometimes get left behind that can mess some things up.

Also, did you have to install a driver for your Belkin wireless N adapter to work in 9.10?  If so, I would suspect you need to reinstall it.  If not, did you have to set any options in any type of configuration file?  If so, that may have been lost in your update.

Right-click on the network manager icon and be sure the "Enable Wireless" is clicked and enabled.

If the router is not broadcasting the ESSID (e.g, it is a "hidden" network"), you need to manually set that up in network manager.  

I would also suggest going through network manager and deleting any known connections to your network, then let it rescan and try a new connection definition in network manager.

Remember encryption must match, password/passphrase must match.  If MAC filtering is enabled on the router, and if this PC with it's current adapter has never connected to the router before, you must enter the adapters MAC in the router table.

For now, please post back the following:

- open a terminal window (Applications/Accessories/Terminal)
- type:

lspci <press enter> Post the output back here

lsusb <press enter> Post the output back here

ifconfig <press enter>  Post the output back here

lshw -C network <press enter>  Post the output back here

That should give us enough information to start looking more at this.

Dave ;)

---

### Post by creepy steve on 2010-11-30
No driver installed before. Just a bit of info. i also run mandriva and everything works fine on that OS. i have tried deleting any known networks and starting from scratch. no go there. my friend at work runs ubuntu and said that there are certain brands of routers that just dont mix with ubuntu. and that there might have to be a certain set up to do with it to make it compatible with ubuntu. 

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

eth0      Link encap:Ethernet  HWaddr 00:0a:e6:c8:12:01  
          inet addr:67.50.30.154  Bcast:67.50.30.159  Mask:255.255.255.240
          inet6 addr: fe80::20a:e6ff:fec8:1201/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:346268341 (346.2 MB)  TX bytes:23735833 (23.7 MB)
          Interrupt:5 Base address:0x6e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

is this what you are looking for? i just listed all of the results of each command in the order you gave me.

---

### Post by I2k4 on 2010-11-30
I'm another newcomer, but have been running wi-fi comfortably on a fresh install of 10.04 Desktop.  Can't speak to problems that might be caused by upgrading from another version.  (If you upgraded the OS without changing a working wi-fi installation, it might be that deleting it and creating a fresh wi-fi connection would solve the problem.) 

First thing is to be sure that when you right-click the icon on the panel, all three top checkboxes are enabled.  Then in Edit Connections / Wireless be sure something is there, or else create a new connection.  Then, using the Edit button, check that the connection correctly says the right SSID, and says Infrastructure.  In my system all the other first tab fields are blank.

On the Wireless Security tab, I have my router set up to WPA2 Personal with a passphrase so that is what it is set to - use the "show" checkbox so you can double-check the accuracy of the passphrase.  I suggest you should set WPA2 with your own router, but whatever you do be sure those security settings are configured correctly on Ubuntu to be perfectly consistent with the way the router is set.   I did not touch the IPV4 or IPV6 settings.  

With those settings it automatically connects to wi-fi on boot.  It's been very reliable so far.

---

### Post by creepy steve on 2010-11-30
yeah did all that stuff already. thanks for the info though.

---

### Post by creepy steve on 2010-12-02
im going to back everything up and try a fresh install. lets see how that works. thanks everyone for the help.

---

### Post by creepy steve on 2010-12-21
the fresh install of 10.04 did not help. i would just run a 25ft ethernet cable to my pc but the wife shot that idea down. so the computer is on the kitchen bar. (not ideal). also i tried running mint 9 xfce at the suggestion of a friend but that doesnt work properly either.

---

### Post by jendie on 2010-12-22
Do you by any chance have Comcast? I have the same problem at my boyfriend's house. Each time I start up the computer there I have to enter "sudo iwconfig wlan0 power off" to get it to stop the perpetual loading.

---

### Post by creepy steve on 2010-12-25
no i discovered it was compatability issues with my belkin n usb adapter. i am getting a new one that is compatible with linux.

---

### Post by creepy steve on 2010-12-30
stupid small towns  nothing here is compatable. i have a netgear wna1100 model i found about ndiswrapper and installed that so i have the command under system/admin windows wireless drivers but it wont install off the inf. (autorun.inf) file on the instal disc.but it says invalid driver OMG???? am i doing this right?

---

