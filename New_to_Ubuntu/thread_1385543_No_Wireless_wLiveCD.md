---
title: "No Wireless w/LiveCD"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by cmfeeney on 2010-01-19
Preparing to try Ubuntu 9.10 install on girlfriend's PC, I want to try it from Live CD on my HP NC8000 laptop. It boots from the CD and runs, but wireless network adapter does not work. No light to indicate power. Pretty limited without networking and can't really sell it on that basis.  Yes, I might be able to cable it to the Broadcom card and may try this later.
 
I've been reading these forums and have seen mention of the ath5k driver blacklisting. I'd try that but... from Live CD? Don't tell me I have to build a customized Live CD to comment out a single line in /etc/modules.d ! So, can I load this driver and turn on the adapter without rebooting and going back to square0?
 
Oh, it had looked so promising when it first started up.
 
Booting HER PC from the same LiveCD also didn't work, for some reason to be figured out in another thread.

---

### Post by warfacegod on 2010-01-19
I'm wondering if it's the disc.

Use:

```
lspci
```

to figure out what your wireless chipset is and then go to The Networking & Wireless forum to see if it's supported.

---

### Post by admiralspark on 2010-01-19
I've found that laptop wireless doesn't like to work from the CD. When Ubuntu is installed, and the wireless card is configured/driver is installed, it will set system start/stop points to start up the wireless card on boot. 

For example, I have a Broadcomm 4318 wireless card. The 'default' bcm43 driver doesn't work, I have to use ndiswrapper to set everything properly. When I boot from a LiveCD, it doesn't have the ndiswrapper settings implemented--I have to do it post-install. It's no big deal, it takes me 15 minutes with my scripts (most of that time spent d/ling the extras, since my internet is SLOW). 

Please post back the output of "lspci" so we can tell what the card is, then we can see if it will work.

---

### Post by alejaaandro on 2010-01-19
if your wireless card needs a proprietary driver i think you should get a prompt to install it (or an icon in the notification area) cause ubuntu searches for hardware that require that.. if not, i think there's an item in the system administration menu called "hardware drivers".. problem is, this is one of the few things that you need to restart in order to take effect and since this is a live cd, no changes are saved, so when you reboot you' ll be an a fresh system again (as if you never installed it).. unless there's a way to activate the driver without rebooting, i don't think this will work from a lice cd..

also know that when i installed 9.10 in my dell mini 9 i had to reinstall the "hardware drivers" application cause for some reason it wouldn't work correctly..

if you told us what the wifi card is, you might some better help

---

### Post by cmfeeney on 2010-01-19
> **warfacegod said:**
> I'm wondering if it's the disc.

Use:

```
lspci
```

to figure out what your wireless chipset is and then go to The Networking & Wireless forum to see if it's supported.
I will lspci and post output when I get home tonight. I think it is an AR5211 based Atheros.

---

### Post by warfacegod on 2010-01-19
> **cmfeeney said:**
> I will lspci and post output when I get home tonight. I think it is an AR5211 based Atheros.

I have the same card. Mine works fine. A bit weaker signal in 9.10 than 9.04 but never had to do a thing in either OS to get it to work.

---

### Post by itsbrad212 on 2010-01-19
Maybe try and download the driver from another computer, then put it on a flash drive, put it on your girlfriends PC, and try it then. Has it worked with other versions of Ubuntu?

---

### Post by admiralspark on 2010-01-19
> **warfacegod said:**
> I have the same card. Mine works fine. A bit weaker signal in 9.10 than 9.04 but never had to do a thing in either OS to get it to work.

Did you get works-out-of-the-box results from the LiveCD or an install?

---

### Post by warfacegod on 2010-01-19
> **admiralspark said:**
> Did you get works-out-of-the-box results from the LiveCD or an install?

Both. 9.10 LiveCD gave me marginally better signal strength.

---

### Post by cmfeeney on 2010-01-19
Sorry if post/reply is to wrong poster; still learning. lspci output follows:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

So I came home, turned on the laptop, caught the BIOS setup break, while I was looking for the LiveCD, then put it in the drive. Was reading my gas bill and missed the timer on the install. I let it finish startup. Lo and behold, the power light for the network adapter is ON! Established a connection and there it was... puzzling; as I did nothing to make it work. 

As I write this (on the laptop), I notice the power light just went out and while looking at it in disappointment, it is turning off and on every so often! :-(

Does any of this make sense?

So maybe a hardware problem with the card, or the power mgmt software? I hope this posts OK! I'll be back. (Girlfriend's PC is a different issue, the desktop never loads)

---

