---
title: "Add wireless drivers to mini iso?"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2015-06-07
Hi all,

My question is about getting wireless drivers into a mini .iso for a machine that has no ethernet connection (as in it has nowhere on the machine to plug an ethernet cable, not that I can't get a cable to it). 
___

About a month ago I bought a HP Stream 11. Fits my needs perfectly and I love it. It currently has Xubuntu 14.04 LTS installed and runs great and fast.

But ... I ALWAYS install the Ubuntu minimal install and then create a customised hybrid of my choice. Unfortunately, the Stream has no ethernet port and the minimal install, naturally, has no wireless drivers for the Stream's wireless card. Consequently, as the mini install relies on a connection with the internet, I am stymied. Mini is out of the question for the moment, which is why I resorted to installing Xubuntu and dumping the apps I don't use.

My question is this. Is there any way to create the mini install media and add the wireless drivers for my device? My problem doesn't apply only to the minimal .iso. The server install (which I also tried) relies on an internet connection also, and when I tried Xubuntu core, same deal. That appears to need you to install the mini before anything also. Impossible situation.

Any Xubuntu core devs or aficionados who might have some suggestions about this? There must be a workaround else if you don't have an ethernet connection, forget install Xubuntu core (and possibly Ubuntu core also), the mini .iso or Ubuntu server.

I'm happy enough with the Xubuntu install, but have enough room on the eMMC in the Stream to install the mini also and would like to do that and set up my normal hybrid. 

Tnx in advance. ;)
___

PS: Not that it's got a lot to do with my support request, but the wireless card 'just worked' when I installed regular Xubuntu 14.04 LTS. ;)

---

### Post by TheFu on 2015-06-07
No answer from me. 

Could you install a full image as you prefer into VM with the network drivers you desire, then clone that over to the netbook storage using something like fsarchiver? Just a thought.

Had the same issue with mini a few weeks ago - the mini-installer found the wifi, did not find the USB3-to-GigE adapter, and after the install was done, I had zero networking on the installed OS. Had picked the "install kernel with drivers for my hardware" option. Clearly, that didn't do what was expected.

Was considering alternative methods to get the OS installed onto the storage, but decided to just go through it 1 more time and pick the bloated choice, "I want all drivers loaded" kernel. At the next reboot, both wifi and that usb3-to-GigE thingy worked.  When the install was all done (no GUI), it used 800MB of storage. A minimal Ubuntu is 800MB?  I've installed a few more programs since then. No DE, but a few WMs.
```
2.3G    usr
1.2G    var (over half is APT cache)
398M    lib
72M     boot
35M     root
16M     tmp
13M     sbin
9.8M    etc
9.1M    bin
```

---

### Post by sudodus on 2015-06-07
Yes, I do that all the time. I add 'automatic network' according to this thread

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

You do that in a computer with wired internet (ethernet), and then port the system to the computer without ethernet. ***network-manager*** and ***nm-applet*** can do the job, and as is written in that link, you may need to install them.

You can take a short-cut and install an already tweaked system from a tarball using the One Button Installer.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)
[B]
Trusty-mini-txt6.tar.xz[/B]

---

