---
title: "wireless only works if manually brought up: broadcom"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by linuxuser187 on 2008-04-05
My wireless broadcom card has the driver installed with ndiswrapper and it works however if i reboot my wireless will not come back on unless i bring up the driver in terminal by doing sudo depmod -a then i do sudo modprobe ndiswrapper and the wireless card is now up and running. i guess when i reboot it's not loading up these commands so where can i insert these commands to let it bring up the wireless driver every time i reboot, what file should i edit?  any help is appreciated! Thx

---

### Post by kevdog on 2008-04-05
Thanks for doing an exhaustive search prior to asking this question that has been asked about 1000 times.

Its 
echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by linuxuser187 on 2008-04-05
sorry, i did check all ndiswrapper and broadcom threads that i could find and did not see it and i've been working on this stupid broadcom for the last couple of days and got fed up, finaly after doing a fresh install of 7.10 and installing ndiswrapper it worked (except for this small problem), thank you! i didn't mean to post something that was already posted several times but i couldn't find the threads and i was searching all night, i will try this

---

### Post by linuxuser187 on 2008-04-05
now that i did that and rebooted it didn't come on after booting up and no even if i run the command in terminal  sudo depmod -a then sudo modprobe ndiswrapper it gets stuck on sudo modprobe ndiswrapper and nothing happens, i have to ctrl-c, so now that the wireless   isn't working at all 

i checked ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
so ok good device is being detected


ndiswrapper version is  ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.22-14-generic SMP mod_unload 

lspci shows 
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

and lspci -n
03:00.0 0280: 14e4:4312 (rev 02)

so what to do now?
should i do a sudo apt-get remove ndiswrapper and/or make uninstall and reinstall the ndiswrapper and reconfigure it or am i missing sommething?

---

### Post by kevdog on 2008-04-05
After boot, just check if the module is loaded 

lsmod | grep ndis

and then check if ndiswrapper is associated with your card:

lshw -C network

---

### Post by linuxuser187 on 2008-04-05
lsmod | grep ndis gives me
ndiswrapper           244802  1 
usbcore               161584  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd

lshw -C network shows us

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0

so that looks fine as well no?

---

### Post by kevdog on 2008-04-05
Yes, and no.

What does
ndiswrapper -l 
show?

If no problem with that lets proceed!

Sorry just read your above post

Yes it looks good

verify
lsmod | grep bcm
does not come back with anything!

---

### Post by linuxuser187 on 2008-04-05
Nothing came back at all

---

### Post by kevdog on 2008-04-05
Ok so 

iwlist scan

Does this show any networks?

---

### Post by linuxuser187 on 2008-04-05
no wireless devices are showing up

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

the wireless card is not being turned on as the light remains yellow but if it's activated the light should be blue and the switch is to the on position

also i should not here that i used the no fluff howto broadcom @ [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
 and at a certain part it asks to do this

Move the 14E4:4324.5.conf file into .conf:

user@ubuntu:~/bcm4311$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
 however i had substituted 14E4:4324.5.conf for 14E4:4312.5.conf as others have suggested for whatever model chipset you have,

the reason why i ask is because i didn't see that on you're how to and juat wanted to let you know incase it has any impact on anything

---

### Post by kevdog on 2008-04-05
Sorry I just noticed one thing:

*-network
description: Network controller
product: BCM4312 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ndiswrapper latency=0

This doesnt come back with any assigned eth1 or wlan0.

Do me a favor

Do the following
sudo modprobe -r ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper

Then check dmesg and post only relevant info related to the ndiswrapper driver.  Thanks.

---

### Post by linuxuser187 on 2008-04-05
i'm going to check now

---

### Post by linuxuser187 on 2008-04-05
you're right, it should be showing up as wlan0, ok so sudo modprobe -r ndiswrapper just froze and i had to ctrl+c

sudo depmod -a went through ok

sudo modprobe ndiswrapper froze again and i had to ctrl+c


also i checked 

cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

it is set to wlan0 and that is the only thing appearing in there which is correct


i didn't realise you responded so fast and didn't check back right away, thanks for helping and i really appreciate it!

---

### Post by kevdog on 2008-04-05
If the modprobe statement is freezing the computer, then you have the wrong driver I believe.  Check dmesg to see if any error is being generated.

---

### Post by linuxuser187 on 2008-04-06
i'm going to check and report back here but also if it were the wrong driver how would my card still work? i was on and running and i was able to see other wireless ssid's through the network manager applet

---

### Post by linuxuser187 on 2008-04-06
;here's the section were concerned about unless you need the whole thing:

[   31.530220] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   31.623339] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   31.625197] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   31.625706] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 9
[   31.625709] PCI: setting IRQ 9 as level-triggered
[   31.625712] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 9 (level, low) -> IRQ 9
[   31.625745] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   31.632794] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: ffffffff8838148e
[   31.632798] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x110
[   31.632810] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   31.632815] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   31.632825] ndiswrapper (mp_halt:259): device ffff810077bb1780 is not initialized - not halting
[   31.632832] ndiswrapper: device eth%d removed
[   31.632840] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   31.632850] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[   31.635452] usbcore: registered new interface driver ndiswrapper

it's showing it can't initialize

---

### Post by kevdog on 2008-04-06
Ok, lets try a different driver -- that might be a problem.

sudo modprobe -r ndiswrapper
sudo rm -R /etc/ndiswrapper/*

Then go find the driver using this page -- I believe its step 2a:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Then just re-install and tell me what happens!

---

### Post by linuxuser187 on 2008-04-07
so i downloaded and extracted the exe and installed again, as soon as i did sudo modprobe ndiswrapper my system froze and went down, after rebooting i logged back in and my x server froze on me lol! i couldn't even switch to another telnet, so reboot again and it loaded ok this time and wireless was loaded by itself and i can see wireless networks that are in the air,

 i still did not do and don't know if i should 

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

i'm going to reboot again just to see how everything behaves without running any other command and will be right back

---

### Post by linuxuser187 on 2008-04-07
so far everything is looking ok, the network applet is showing 2 wireless networks present but iwlist scan shows nothing, is this normall?


luis@hacktop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

luis@hacktop:~$ lsmod | grep ndis
ndiswrapper           244608  0 
usbcore               161584  7 ndiswrapper,uvcvideo,usbhid,xpad,ohci_hcd,ehci_hcd

luis@hacktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:76:51:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

luis@hacktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

luis@hacktop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

---

### Post by kevdog on 2008-04-07
That is strange -- did you blacklist the bcm43xx driver?

---

### Post by linuxuser187 on 2008-04-07
the last time i installed ndiswrapper i did blacklist the bcm43xx driver, also it shows bcmwl5 : driver installed

---

### Post by kevdog on 2008-04-07
What channel is the router broadcasting on?  Is the ESSiD being broadcast?

---

### Post by linuxuser187 on 2008-04-07
i do not have a wireless connection at home, just needed the wireless working for when i go to school, these 2 other ssids's that i see now through the network applet are other peoples router's in my building so i could not tell you, does the scan command scan for every ssid the wireless card can see or only a programmed ssid, i'm not to familiar with that command, also just a question, if i install wifi radar will it cause any problems with the network applet?

---

### Post by kevdog on 2008-04-07
I'd go for WICD personally -- and yes either WICD or wifi radar uninstall the nm applet.  You could install it back later, but need to uninstall the other app.

---

### Post by linuxuser187 on 2008-04-07
ok cool, thanks for all you're help i appreciate it! and what does the iwlist scan command do exactly

---

### Post by kevdog on 2008-04-07
Shows broadcast networks in the area.

---

### Post by linuxuser187 on 2008-04-07
ok, i think i should be ok from here on out, i don't know why iwlist scan is not showing any networks but the network applet is showing them but i think i should be fine with some more playing around with, Thanks again!

---

### Post by linuxuser187 on 2008-04-07
just to let you know i rebooted and iwlist scan and the network applet are showing me the networks!

---

