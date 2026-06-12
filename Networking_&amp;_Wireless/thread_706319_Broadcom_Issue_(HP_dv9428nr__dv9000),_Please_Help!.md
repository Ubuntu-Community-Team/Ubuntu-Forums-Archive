---
title: "Broadcom Issue (HP dv9428nr / dv9000), Please Help!"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by SeanInSeattle on 2008-02-24
OK, I'm annoyed.  I've followed the [instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6").  I even compiled my ndiswrapper from the source (when I had access to a wired connection, yesterday).  

I have the following information to provide about what I've done so far:

[INDENT]Confirmed LSPCI lists my card:  

	[INDENT]"03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)"[/INDENT]

Confirmed ndiswrapper showing my driver installed:  

	[INDENT]"bcmwl5 : driver installed, device (14E4:4311) present (alternate driver: bcm43xx)"[/INDENT]

Confirmed ifconfig info using following command:  ifconfig

	[INDENT]eth0 [/INDENT]    [INDENT] Link encap:Ethernet  HWaddr 00:1B:24:6A:51:5A  
		  UP BROADCAST MULTICAST  MTU:1500  Metric:1
		  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:1000 
		  RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
		  Interrupt:10 Base address:0xe000 [/INDENT]

	[INDENT]lo[/INDENT]        [INDENT]Link encap:Local Loopback  
		  inet addr:127.0.0.1  Mask:255.0.0.0
		  UP LOOPBACK RUNNING  MTU:16436  Metric:1
		  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:0 
		  RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT]

Confirmed Broadcom WIFI card still not working by the following command:  "iwconfig eth1 essid any"

	[INDENT]Error for wireless request "Set ESSID" (8B1A) :
	    SET failed on device eth1 ; Operation not permitted.[/INDENT]

seanochoa@SeanInSeattle:~$ lspci | grep Broad

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

seanochoa@SeanInSeattle:~$ cat /etc/modprobe.d/blacklist

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



blacklist bcm43xx





seanochoa@SeanInSeattle:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



seanochoa@SeanInSeattle:~$ iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



seanochoa@SeanInSeattle:~$ ndiswrapper -l

bcmwl5 : driver installed

        device (14E4:4311) present (alternate driver: bcm43xx)

seanochoa@SeanInSeattle:~$ dmesg | grep ndis

[   65.700056] ndiswrapper version 1.45 loaded (smp=yes)

[   65.788825] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver

[   65.790377] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded

[   65.800159] ndiswrapper (IoConnectInterrupt:567): request for irq 0 failed

[   65.800163] ndiswrapper: request for IRQ 0 failed

[   65.800309] ndiswrapper (mp_init:263): couldn't initialize device: C000009A

[   65.800317] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)

[   65.800332] ndiswrapper (mp_halt:305): device ffff810071f61780 is not initialized - not halting

[   65.800342] ndiswrapper: device eth%d removed

[   65.800359] ndiswrapper: probe of 0000:03:00.0 failed with error -22

[   65.804600] usbcore: registered new interface driver ndiswrapper

[/INDENT]

So, at this point, my card isn't showing up in the ubuntu network desk-widget, either. :(

I'm wondering if someone has a recommendation as to where I should go from here (please!).

Any help is appreciated.

---

### Post by spd106 on 2008-02-25
Try running ```
ndiswrapper -v
``` If it says the utils version is wrong then you'll probably have to delete the ndiswrapper.ko file it mentions and re-"sudo make install" to get the correct kernel module installed. You'll then have to repeat this every time there is a kernel update.

Or you could try bcm43xx again.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by Ayuthia on 2008-02-25
Are you using any kernel parameters to get Ubuntu to run on your HP?  Some HP laptops that have the AMD/Nvidia chips need some kind of noapic combo to make it work with Ubuntu.  If you are, which ones are you using?  It is possible that some of your interrupts might be turned off causing your problem.

---

