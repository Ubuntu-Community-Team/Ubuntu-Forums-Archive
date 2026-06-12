---
title: "Installing USB dongle remotely help."
date: 2011-08-01
forum: New to Ubuntu
---

### Post by Smeeble on 2011-08-01
Hi, a friend of mine got given an old pc, but it was filled with numerous trojan's, had been infected and general rubbish. So we formatted it and installed the latest Ubuntu.
We are trying to install a USB dongle he has bought for the internet, but it only has a .exe file, that won't work on it.

I have looked and found that by installing WINE, it should them emulate it and hopefully then install, so we can then it on the internet for further installations etc.

How do I install WINE on it, without an internet connection on that PC...or is there another way to solve the problem?

I have never used Linux before, but I am ok with computers in general.

Thanks for any help, going to give it another go tonight.

---

### Post by nothingspecial on 2011-08-01
I take it by usb dongle you mean one of those mobile internet things.

Plug it into ubuntu, open a terminal (Ctrl-Alt-T) and type 

```
lsusb
```

and

```
dmesg | tail -n 20
```


after doing so, then post all the gobbldygook that it returns in a new post back here,

---

### Post by nothingspecial on 2011-08-01
By the way, there is a good chance that it will just work.

Have you actually tried connecting?

---

### Post by Smeeble on 2011-08-01
Cheers for the very quick reply.

It's a NetGear WNDA3100 v2 dongle to connect to a router, not a mobile internet dongle.

It doesn't just work, it does have an installation disk, but it only has autorun and setup .exe files, no linux based install.

---

### Post by nothingspecial on 2011-08-01
Have a look at this, I don't know if it will work, I haven't got one of those dongle things.

[http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)

You can install ndiswrapper from the live cd, to do this open up synaptic package manager and click edit > add cd (with the live cd in the drive)

you can download the 2 zip files to a usb stick on another computer and copy them across.

---

### Post by Smeeble on 2011-08-01
Cheers, that was a very good/quick find.

Will try it tonight and let you know.

---

### Post by Smeeble on 2011-08-01
Tried doing it tonight. I managed to install the files from the disk, and then install the .inf files for the dongle (verified that they were installed), but when the dongle is plugged in, it still says 'no hardware detected' for the drivers.
When I did the 'lsusb' command though, it did come up saying the dongle on one of the USB ports.

I had a look but couldn't find any other drivers for it, and so tried to install wine again, but I don't know how to without having an internet connection. I can get the files on the pc, but don't know what to do then.

Any more advice on either solution?

Cheers again.

---

### Post by westie457 on 2011-08-01
> **Smeeble said:**
> Tried doing it tonight. I managed to install the files from the disk, and then install the .inf files for the dongle (verified that they were installed), but when the dongle is plugged in, it still says 'no hardware detected' for the drivers.
When I did the 'lsusb' command though, it did come up saying the dongle on one of the USB ports.

I had a look but couldn't find any other drivers for it, and so tried to install wine again, but I don't know how to without having an internet connection. I can get the files on the pc, but don't know what to do then.

Any more advice on either solution?

Cheers again.

Could you run ```
lsusb
``` again and this time post the output here. There will be a number in the output which will give a clue to which driver is needed. Thank you.

---

### Post by Smeeble on 2011-08-02
Is it just the one line about the dongle you need, or everything that appears?
Only ask as I will have to get my mates girlfriend to run it, then type it all into an email to me.
 
Or is there an easy way to screenshot etc on Ubuntu?

---

### Post by nothingspecial on 2011-08-02
It's the one about the dongle.

Can you not copy and paste and transfer with a stick or plug the laptop in with a wire?

---

### Post by 3rdalbum on 2011-08-02
Wine only runs programs, not drivers. You can't install the driver in Wine and have it emulate.

---

### Post by Smeeble on 2011-08-02
I'll give wine a miss then if it won't run the setup.exe file.
 
It's on a PC so can't move it easily. I'll try and get them to copy and paste it into some built in reader, copy the file across to another PC, and email me it. If not I'll get them to just email me what the dongle line says.

---

### Post by walt.smith1960 on 2011-08-02
I did a quick search in the networking & wireless forum. The WNDA3100 **v2** appears to use the infamous Broadcom chip set.  v1 used Atheros which seems to be less problematic.  I'd wonder if looking at "activate drivers" or whatever it's called would show something.  Here's one thread, there are others relating to this device:

[http://ubuntuforums.org/showthread.php?t=1383708&highlight=netgear+wnda+3100](http://ubuntuforums.org/showthread.php?t=1383708&highlight=netgear+wnda+3100)

IMO ndiswrapper seems like a last resort.  I wonder if ndiswrapper will interfere with efforts to make a Linux driver work properly.  I used ndiswrapper once but copied the .inf & .sys files from a windows installation. It worked but performance using linux drivers was quite a bit better.  Also bear in mind that the windows drivers must be from WinXP (not Vista or 7) and must be 32 or 64 bit depending on the version of Linux.

---

### Post by westie457 on 2011-08-02
> **walt.smith1960 said:**
> I did a quick search in the networking & wireless forum. The WNDA3100 **v2** appears to use the infamous Broadcom chip set.  v1 used Atheros which seems to be less problematic.  I'd wonder if looking at "activate drivers" or whatever it's called would show something.  Here's one thread, there are others relating to this device:

[http://ubuntuforums.org/showthread.php?t=1383708&highlight=netgear+wnda+3100](http://ubuntuforums.org/showthread.php?t=1383708&highlight=netgear+wnda+3100)

IMO ndiswrapper seems like a last resort.  I wonder if ndiswrapper will interfere with efforts to make a Linux driver work properly.  I used ndiswrapper once but copied the .inf & .sys files from a windows installation. It worked but performance using linux drivers was quite a bit better.  Also bear in mind that the windows drivers must be from WinXP (not Vista or 7) and must be 32 or 64 bit depending on the version of Linux.

Thanks for that. The bit we now need is the xx part of the b43xx. Hopefully the OP will supply the info so he can be pointed in the right direction. Hopefully (fingers crossed) the drivers he needs will be available from the install cd.

---

### Post by Smeeble on 2011-08-02
Haven't had chance to look through that thread yet, will do tomorrow.
I did manage to get my mate to email me a photo of the info that lsusb threw up.
[http://i401.photobucket.com/albums/pp100/Smeeble09/Temporary/lsusb.jpg](http://i401.photobucket.com/albums/pp100/Smeeble09/Temporary/lsusb.jpg)

Doesn't seem to be of much use though.

---

### Post by westie457 on 2011-08-02
> **Smeeble said:**
> Haven't had chance to look through that thread yet, will do tomorrow.
I did manage to get my mate to email me a photo of the info that lsusb threw up.
[http://i401.photobucket.com/albums/pp100/Smeeble09/Temporary/lsusb.jpg](http://i401.photobucket.com/albums/pp100/Smeeble09/Temporary/lsusb.jpg)

Doesn't seem to be of much use though.

have you tried this from Netgear? [http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2](http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2)

---

### Post by walt.smith1960 on 2011-08-02
> **westie457 said:**
> have you tried this from Netgear? [http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2](http://support.netgear.com/app/answers/detail/a_id/18580/kw/wnda3100v2)

Still an .exe file. He'd have to find a way to extract the .inf & .sys files.

---

### Post by westie457 on 2011-08-03
Unless anyone has a simpler way to get these files they can be copied from an installed Windows system to a cd or usb stick. 

As for just downloading the necessary Ubuntu packages without installing I have no idea how to do that.

The simple answer is to move the pc to a place and connect an ethernet cable and install the necessary packages and point ndiswrapper to the cd that has the .inf and .sys files.

---

### Post by westie457 on 2011-08-03
The required drivers might be on the LiveCD. There are some there.

Boot into your normal system stick the cd in the tray. Open the File Browser > name of cd > pool > main > b > b43-fwcutter. there will be one package here. the other package is at pool > restricted > b > bcmwl. 

You might need just one or both of them. Or they might not work at all.

Hope this helps.

---

### Post by walt.smith1960 on 2011-08-03
It might depend on which the person in question has more of -- time or money.  The quickest solution is to buy a USB WiFi dongle that works as soon as it's plugged in. I have an old TrendNet TEW424UB v.3.1 which fits that description.  It's slow compared to N speed adapters but I use the Trendnet to download updates and software for the faster device that is not supported out-of-box.  Get the built-in device working then put the TrendNet back in the drawer until it's needed again.

---

### Post by Smeeble on 2011-08-03
Ok guessing if I connect a laptop up that has a WLAN on it via the Ethernet port to the pc I can then set it to share its connection with the pc, and then be able to get it on the internet to download the various programs etc I would need for it?
It does now have ndiswrwpper on it from the live cd already, but it didn't work. If I download wine via the above method and then run the .exe cd that came with it, it should sort it...or have I missed something?

---

### Post by Smeeble on 2011-08-21
Hi, went on holiday so haven't been able to reply for a while.
My mate only had a few days left in his 30 days refund so he has taken the dongle back.

Anyone recommed a dongle that will work/install fine and is compatible with Sky broadband Netgear router?

---

