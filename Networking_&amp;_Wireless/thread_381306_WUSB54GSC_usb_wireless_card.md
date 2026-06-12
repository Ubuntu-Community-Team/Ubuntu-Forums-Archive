---
title: "WUSB54GSC usb wireless card"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2007-03-10
I just bought a linksys WUSB54GSC wireless card but I am not able to get it working despite other people having success with it.

I tried this tutorial: [http://www.ubuntuforums.org/showthread.php?t=2d25206](http://www.ubuntuforums.org/showthread.php?t=2d25206)

but without success. I don't know if I have a v1 or v2 card, I dont even think I have either siince it has a C at the end of the name.

the card shows up fine when I do lsusb I get:

> Bus 005 Device 003: ID 13b1:0026 Linksys 

and with the drivers from that tutorial I was able to get this from ndiswrapper -l
> shiznatix@shiznatix-laptop:~$ ndiswrapper -l
installed drivers:
wusb54gsc               driver installed, hardware (13B1:0026) present 

but the card does not show up in the network admin and the tutorial has no more information. I am running Edgy and I put in both of those lines into the file to get the usb enough power but neither did anything.

Any help would be great. Thanks.

---

### Post by ncappel1 on 2007-03-10
Can this be of any help?

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by shiznatix on 2007-03-12
Ok after much pain and anger I formatted and installed dapper form the beginning. I then got the card to work just fine in dapper, yay!

Then I upgraded to edgy because most of the awesome programs out there are for edgy. Sadly I am not able to get this to work now. I am aware that I have to modprobe ndiswrapper but every time I try I get this error:

> shiznatix@shiznatix-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

the tutorial that I followed was the same one in my first post ([http://www.ubuntuforums.org/showthread.php?t=2d25206](http://www.ubuntuforums.org/showthread.php?t=2d25206)) and it says that if you get that error then you probably did not install any drivers. This does not make sense to me because the drivers are there and I did all the steps no problems.

When I plug in the device and do ndiswrapper -l I get this:

> shiznatix@shiznatix-laptop:~$ ndiswrapper -l
wusb54gsc : driver installed
        device (13B1:0026) present

but it won't show up in ifconfig. Any help would be most appreciated.

---

### Post by shiznatix on 2007-03-12
**bump**

---

### Post by leetcharmer on 2007-03-12
I'm having problems w/ the same USB wireless card.  I'm in edgy, but I did get everything to show up.  It just won't ever scan and get results :/  I had to add usb .sys files to my ndiswrapper config folder to get that far, did you do that?

---

### Post by shiznatix on 2007-03-12
yes I did do that. I got everything to work on dapper before I did an upgrade so I knew for sure that it does actually work. The instructions are the same for both dapper and edgy except edgy has a 'you gotta add this file to give it power' which I did do.

I still don't see why it won't work, what is your line in the power management file thing?

---

