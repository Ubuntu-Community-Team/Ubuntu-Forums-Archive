---
title: "Wireless adaptor Help? Please?"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by the_flood502 on 2008-05-26
Hey

1) I'm new to linux so please be...er... less technical please ^^

2) New To the forum, hey ^^


---


Ok... so i got this USB stick for my wireless network and... well... i don't even know where to begin with installing the drivers...

[http://pluscom.cn/forum/forum_posts.asp?TID=301](http://pluscom.cn/forum/forum_posts.asp?TID=301) - this is where i got the drivers for the USB thingy...

the model number is: "WU-ZD1211B" and is Made by 'pluscom'

I'm running it on an OLD G3 Slot Loading iMac (i would prefer linux (than smelly OSX) on it... but can't get the darn drivers to install)

need help please =)

I'll answer any questions about the system, etc that i can... i'm quite fluent with Windows... but i just can't seem to get the hang of linux... :confused:

Help?


Thanks

Dean

---

### Post by chili555 on 2008-05-26
We can only be so less technical; it's bred in us!

Seriously, open a Applications->Accessories->Terminal and type:```
sudo tail -f /var/log/messages
```Leave it open. When you type your password, it may look like it's not taking, but it is. Open another terminal, jam that USB thingy in the slot and type:```
sudo modprobe zd1211rw
```Did your USB thingy come to life? If not, look in the first terminal and see if it found or failed to find the firmware. Let us know and we'll see if we can whip it into action. We will need the exact wording from *messages* if it can't load firmware.

---

### Post by the_flood502 on 2008-05-27
eto... *tries*

ok...

now i'm more confuzzled =(

> /var/lib/gconf/defaults" to a read-only configuration source at position 4
May 27 15:02:03 dean-desktop gconfd (dean-4747): Resolved address "xml:readwrite:/home/dean/.gconf" to a writable configuration source at position 0
May 27 15:03:30 dean-desktop kernel: [  290.586316] usb 2-1: new full speed USB device using ohci_hcd and address 11
May 27 15:03:31 dean-desktop kernel: [  290.793676] usb 2-1: configuration #1 chosen from 1 choice
May 27 15:03:31 dean-desktop kernel: [  290.795523] vendor_id = ce0a
May 27 15:03:31 dean-desktop kernel: [  290.795536] product_id = 1512
May 27 15:03:31 dean-desktop kernel: [  290.795542] USB 1.1 Host
May 27 15:03:31 dean-desktop kernel: [  290.795762] Release Ver = 1048
May 27 15:03:31 dean-desktop kernel: [  290.795773] Something wrong. Mostly, it's a endian issue
May 27 15:03:31 dean-desktop kernel: [  290.795790] EEPORM Ver = 4810
May 27 15:03:31 dean-desktop kernel: [  290.808353] Finsih download Firmware. Ready to reboot 
May 27 15:03:31 dean-desktop kernel: [  291.063360] ##### Warning! ####
May 27 15:03:31 dean-desktop kernel: [  291.063387] usb_control_msg doesn't send all data out
May 27 15:03:31 dean-desktop kernel: [  291.063396] You need to decrease the message amount in each send
May 27 15:03:31 dean-desktop kernel: [  291.063468] zd1211b: probe of 2-1:1.0 failed with error -5


thats what i got... does that mean anything to you... because i can't make sense of any of it =(


---

I've connected the ethernet cable to the imac and i'm now download the ubuntu updates for it... i'll tell you if this fixes this problem... although i doubt it =(

forgot to mention i'm running ubuntu 7.04 


More help?

Thanks

Dean

---

### Post by mapes12 on 2008-05-27
Hi Dean

You did download the Linux driver and not Mac I assume?

Did you then follow the Linux installation guide to load the driver (link under the download link)?

Please could we have a look at the output from

```
sudo lshw -C network
```

from a Terminal window as before.

---

### Post by chili555 on 2008-05-27
> You did download the Linux driverI was hoping the built-in module might work.

---

### Post by the_flood502 on 2008-05-27
... i'm not that technically impaired... i understand what the operating system is and what it does... and the types... i just have no idea how to install it. strange as it may seem lol

I'm quite computer literate (having GCSES and ALEVELs in ICT...) but we never really got told how to compile any drivers in linux...

Linux drivers for linux OS

Mac drivers for Mac OS

anybody can guess that... although... you never know i guess...

i tried the drives, attempted to follow the manual... but when i typed 'make' it just kinda went 'nah i don't feel like it' and then gave up =S


---

*attempts the sudo lshw -C network thing*

> dean@dean-desktop:~$ sudo lshw -C network 
  *-network                
       description: Ethernet interface 
       product: UniNorth GMAC (Sun GEM) 
       vendor: Apple Computer Inc. 
       physical id: f 
       bus info: pci@20:0f.0 
       logical name: eth0 
       version: 00 
       serial: 00:0a:27:b3:78:d8 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10MB/s 
       resources: iomemory:f5200000-f53fffff irq:41 


this what you wanted?

Thanks for your aid so far... if i can't iron out the problem... i'll just have to buy a more dependable wi-fi adaptor =/ tis a little frustration though that it advertises linux compatablity and yet it's so confusing to install =(

Dean

---

### Post by chili555 on 2008-05-27
> Finsih download Firmware. Ready to rebootAnd did you reboot with the device iinserted? Please try and then let us see:```
sudo cat /var/log/messages | grep zd1211
```Also, your *lshw* tells us about your very healthy ethernet interface and nothing about your wireless. Let us also see:```
lsusb
```Thanks.

---

### Post by the_flood502 on 2008-05-28
ok... so i tried it again...

and guess what... it came up with something else... i have NO idea what it means... and another 'eth0' (called 'eth0:avahi) has shown up when i click on 'Network Tools'... 

heres the log:

> dean@dean-desktop:~$ sudo tail -f /var/log/messages 
Password: 
May 28 22:01:38 dean-desktop kernel: [39662.250030] usb 1-1.1: new full speed USB device using ohci_hcd and address 6 
May 28 22:01:38 dean-desktop kernel: [39662.360364] usb 1-1.1: configuration #1 chosen from 1 choice 
May 28 22:01:38 dean-desktop kernel: [39662.366707] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input6 
May 28 22:01:38 dean-desktop kernel: [39662.366837] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:18.0-1.1 
May 28 22:01:38 dean-desktop kernel: [39662.373297] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input7 
May 28 22:01:38 dean-desktop kernel: [39662.373418] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:18.0-1.1 
May 28 22:01:38 dean-desktop kernel: [39662.578050] usb 1-1.2: new low speed USB device using ohci_hcd and address 7 
May 28 22:01:38 dean-desktop kernel: [39662.691368] usb 1-1.2: configuration #1 chosen from 1 choice 
May 28 22:01:38 dean-desktop kernel: [39662.698568] input: Fujitsu Takamisawa Component Apple Optical USB Mouse as /class/input/input8 
May 28 22:01:38 dean-desktop kernel: [39662.698793] input: USB HID v1.10 Mouse [Fujitsu Takamisawa Component Apple Optical USB Mouse] on usb-0001:10:18.0-1.2 
May 28 22:18:30 dean-desktop kernel: [40674.287334] ieee80211: 802.11 data/management/control stack, git-1.1.13 
May 28 22:18:30 dean-desktop kernel: [40674.287360] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
May 28 22:18:30 dean-desktop kernel: [40674.345880] usbcore: registered new interface driver zd1211rw 
May 28 22:18:55 dean-desktop kernel: [40699.673848] usb 2-1: new full speed USB device using ohci_hcd and address 2 
May 28 22:18:55 dean-desktop kernel: [40699.881204] usb 2-1: configuration #1 chosen from 1 choice 
May 28 22:18:56 dean-desktop kernel: [40700.841845] usb 2-1: reset full speed USB device using ohci_hcd and address 2 


also... another question ... if it has worked... how do i connect to my wireless connection?

Thanks

Dean

---

### Post by chili555 on 2008-05-28
Looks pretty hopeful! Try System -> Administration -> Network. Unlock, enable your wireless device and configure. DHCP is usually best to get it going.

---

### Post by the_flood502 on 2008-05-28
hmm... remember that 'eth0' thing that was added... well... it appears that it's dissapeared...


when i got into network it just shows the wired connection and the modem =(

help?

*cries*

you said to try those things after a reboot... heres the results:

> dean@dean-desktop:~$ sudo cat /var/log/messages | grep zd1211 
May 27 22:28:46 dean-desktop kernel: [  324.188326] usbcore: registered new interface driver zd1211rw 
May 28 22:18:30 dean-desktop kernel: [40674.345880] usbcore: registered new interface driver zd1211rw 
May 28 22:38:00 dean-desktop kernel: [   73.903413] usbcore: registered new interface driver zd1211rw 
dean@dean-desktop:~$ lsubb 
bash: lsubb: command not found 
dean@dean-desktop:~$ sudo lsusb 
Bus 002 Device 003: ID 0ace:1215 ZyDAS  
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 004: ID 05ac:0302 Apple Computer, Inc. Apple Optical Mouse [Fujitsu] 
Bus 001 Device 003: ID 05ac:0205 Apple Computer, Inc. Apple Extended Keyboard [Mitsumi] 
Bus 001 Device 002: ID 05ac:1002 Apple Computer, Inc. Apple Extended Keyboard Hub [Mitsumi] 
Bus 001 Device 001: ID 0000:0000   


---

### Post by chili555 on 2008-05-29
I believe eth0 *is* your wired ethernet device. We are hoping a new interface gets created, like eth1, wlan0, wifi0, etc. I am going to try to put several approaches in one post instead of posting one thing, finding out it didn't work, posting another, etc.

We are hoping a new interface was created. When you run *iwconfig*, do you see any interfaces listed with text other than 'no wireless extensions'? If you do, let's try:```
sudo ifconfig eth1 up
sudo iwlist eth1 scan
```If you get a scan result, it will show the ESSID, in other words, the radio station identification, of your router. Then do:```
sudo iwconfig eth1 essid <ur_routers_essid>
sudo dhclient eth1
```If there is no encryption here, you will probably connect. Substitute the interface you found if it's not eth1.

If you do not see a new interface, we'd like to know why. Open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open and watch while you remove and wait a few moments, then insert your Zydas device. Tell us what the kernel said about the insertion. Did it look for and find firmware? Did it register a new interface, eth1? Or what is it doing instead of getting busy with torrents, email, Shoutcast, etc.?

---

