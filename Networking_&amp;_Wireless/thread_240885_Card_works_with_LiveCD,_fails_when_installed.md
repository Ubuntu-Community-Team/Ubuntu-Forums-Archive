---
title: "Card works with LiveCD, fails when installed"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by darkmika on 2006-08-21
I have a SMC 2532 PCMCIA wireless card. I have successfully gotten this card to work under Gentoo with wpa_supplicant (with some assistance from a linuxy friend), so I know it's possible to get the card to work.

The computer is a CF-27 Toughbook laptop. It has 192 meg of memory, 300 mhz, 6.2 gig of hard drive.

When I loaded up the livecd, the wireless card was detected and I could IM, search the web, etc. Then I installed xubuntu, and now my wireless card isn't working.

When I dmesg}less and scroll down to where hostap_cs is being loaded, it says (and I'm typing it by hand, so there may be typos)

```
hostap_cs: 0.4.4-kernel
hostap_cs: setting Vcc=33 (constant)
hostap_cs: CS_EVENT_CARD_INSERTION
hostap_cs: setting Vcc=50 (from config)
Checking CFTABLE_ENTERY 0x01 (default 0x01)
IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
io->flags=0x0047, io.base=0x0000, len=129
CardServices(RequestIO) returned 30
1.0 RequestIO: Resource in use
1.0: GetNextTuple: No more items
prism2_config() failed
```

Also, when I insert the card I get an error along the lines of "soft lock in CPU0".

Could someone please help me get this card working?

---

### Post by lupine_nickt on 2006-08-21
All that springs to mind is that the card is conflicting with something that wasn't being configured in the LiveCD... but that could be completely wrong. 

Can you reboot, then post the output of 'dmesg', lsmod, lspci and uname -r?

To save you all that typing ;), run <program> > ~/Desktop/<program>-broken-wlan.txt then reboot into the LiveCD. While you're there, run the same for the LiveCD environment (buit for <program>-working-wlan.txt, obviously ;)) and post those details as well. Then we can make some comparisons and see what's changing between the two environments...

xF,

...Nick

---

### Post by darkmika on 2006-08-21
I saved those logs to file, rebooted into the livecd, got more logs, and uploaded them all to my web space.

[Wireless Logs]("http://users.wpi.edu/~haponik/debug_wireless/")

Oh, and the livecd also locks up if I remove the card.

---

### Post by darkmika on 2006-08-21
In the morning, I think I'll going to copy the kernel from my boyfriend's gentoo system (same model laptop, same model card) to mine and see if that helps. From looking at dmesg, it looks like the card is failing in the kernel somewhere. I know his kernel works on his machine, so hopefully it'll work nicely on mine.

If anyone has anything less drastic for me to try, let me know.

I'm very anxious to get this laptop functional before school starts.

---

### Post by lupine_nickt on 2006-08-22
Hmm. So the only thing that seems different is the kernel - but are they even different???

A couple of things to try:

1. Roll your own hostap module
2. Use the kernel and modules from the livecd (they're less likely to foobar than the gentoo ones)

xF,

...Nick

---

### Post by darkmika on 2006-08-22
But... I've not downloaded anything off the network, everything on the machine is from the livecd. That's what I'm really not getting.

I just tried removing my cdrom drive to see if that was somehow interfering with the wireless card (I'm coming off of a similar conflict between a PCI card and my graphics card on my desktop, so it made sense at the time). Didn't help.

---

