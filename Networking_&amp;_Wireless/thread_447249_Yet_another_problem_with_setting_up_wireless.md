---
title: "Yet another problem with setting up wireless"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by squirrelmuphs on 2007-05-17
Hello there,

I am brand-spanking new to anything linux or Ubuntu for that matter and am in a bit of a jam.

I don't know much about coding and setting up my wireless is getting to be a 3 day trudge through goggle and a lot of mood swings for me on the other end.

I've had quite a few attempts at it and now when I check on my installed drivers I have one I named linksys that says is installed incorecctly, same with a lbncmd, and then I have a lbncmd that is installed correctly and I didn't know if those two were interfering with the good one.

Also when I searched for my wlan0 it said that that device didn't exist.

I also can't get the windows wireless driver windo to open up.

So pretty much I am frustrated and half ready to give up.

I have a Linksys wpc54g Ver. 5 wireless card and a compaq evo n410c laptop.

I don't know anything about the codes I have been typing in either, so if there is any replies would anyone be so kind to explain what I am doing as well?

Thank you very much,

Squirrelmuphs

---

### Post by gradedcheese on 2007-05-17
Well, here's an explanation of what I think you've been doing:
- you have a wireless card that uses a chipset from [a very bad chipset maker]("http://andrey.thedotcommune.com/wireless.html")
- you installed ndiswrapper, a clever hack that 'wraps' the calls that Windows drivers make and acts as a translation layer for them, so to speak
- you unpacked the Windows driver and handed its .inf files to ndiswrapper
- ndiswrapper should now load, wrap up the Windows driver, and present a wlan0 wireless device for use in Linux, but for some reason that isn't happening

You can start by asking ndiswrapper for a list of drivers that it has 'installed', like this:

```
ndiswrapper -l
```

You should also check that it's loaded:

```

lsmod | grep ndis

```

does that show anything?  If not:

```

sudo modprobe ndiswrapper

```

---

### Post by squirrelmuphs on 2007-05-18
I got this 
```
russell@Lappy-three-thousand:~$ ndiswrapper -l
linksys : invalid driver!
lsbcmds : invalid driver!
lsbcmnds : driver installed

```

and this

```
russell@Lappy-three-thousand:~$ lsmod | grep ndis
ndiswrapper           194608  0 
usbcore               134280  4 ndiswrapper,ehci_hcd,ohci_hcd

```

---

### Post by squirrelmuphs on 2007-05-18
Alright I found out that I could remove the invalid drivers with the command

```
sudo ndiswrapper -e <drivername>
```

So that part is covered

now when i type ```
sudo ndiswrapper -l
```

I just get the one driver that is installed

---

### Post by booticon on 2007-05-18
I'm trying to get my wifi card working, too (in fact, it's v3 of this card), and when I do "modprobe ndiswrapper", it comes back with:

```

FATAL: Could not open '/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko' No such file or directory

```

Oh sweet jesus, I got it working (v3 is the Broadcom 4318 chipset). I skipped out on ndiswrapper and just installed bcm43xx-fwcutter. Moved the new firmware files to /lib/hotplug/firmware, and I was good to go!

---

### Post by squirrelmuphs on 2007-05-19
Alright my lspci command shows that the version 5 card is not a broadcom chipset but rather a marvel technology 

```
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Linksys Unknown device 0040
        Flags: 66MHz, medium devsel, IRQ 11
        Memory at 38000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Memory at 38010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

anyone know what I can do from here?

---

### Post by squirrelmuphs on 2007-05-19
I've gotten the correct driver now and see this

```
russell@Lappy-three-thousand:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present

```

But when I type in iwconfig I still can't see anything but this

```
russell@Lappy-three-thousand:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Does this mean I don't have a wlan0?

---

### Post by squirrelmuphs on 2007-05-19
Got it working, reads my card and wireless connection all set up, but now I can't get on the internet even when it says I'm connected to my essid.

---

