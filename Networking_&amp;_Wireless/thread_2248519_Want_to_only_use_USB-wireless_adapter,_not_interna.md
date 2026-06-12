---
title: "Want to only use USB-wireless adapter, not internal"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by bugbear6502 on 2014-10-15
short version:

I want to have wireless internet that ONLY uses an outboard USB
wireless adapter, making no reference to the fitted wireless hardware.

Some historical context:

I have a quite old, but still useful Amipro laptop. It's internal wireless
is horribly insensitive, so I bought a nice USB/outboard adapter.

Under Lubuntu 12.04 I (eventually) discovered that to get "things" working I had to:

* enable the internal wireless hardware. Without this Ubuntu seems to disable the
   whole of wire-less-ness.

* the USB adapter always worked, it's great!!

* stop the network manager ever choosing, offering or using the internal wireless

Here's the old thread where I worked all this out, with help from others;

[http://ubuntuforums.org/showthread.php?t=2132306](http://ubuntuforums.org/showthread.php?t=2132306)

I skipped Ubuntu 13, due to PAE issues, and have now installed 14.04.
During the install I had a NIGHTMARE with something called
westron_btns.

[http://ubuntuforums.org/showthread.php?t=2248182](http://ubuntuforums.org/showthread.php?t=2248182)

I eventually diagnosed the culprit, disabled it, and 14.04 runs OK,
at least with a wired connection.

Next step - wireless. :p

It turns out that fsam7400 (which turns on my hardware wireless, see above)
is no longer part of Ubuntu. It's been replaced by something newer and better.

Yes, you've guessed, westron_btns. :(

So my nemesis is what I need to make my wireless work.

However, I don't really WANT to turn on my internal wireless
hardware. What I really want to do is turn on the wireless MANAGER
and for it to use the wireless adapter out in USB land.

So before I attempt to re-implement my Ubuntu 12 solution
(enable internal hardware to enable wireless manager, but stop
wireless manager using internal hardware), can I "just"
turn on the wireless manager in a more direct fashion?

Otherwise I'm going to have to do work to get westron_btns
to NOT kill my machine, just so I can turn on a piece
of hardware I don't want to use (!!).

 BugBear

---

### Post by TheFu on 2014-10-15
TL;DR - just blacklist the onboard wifi driver.

Put the driver into:
  /etc/modprobe.d/blacklist.conf

---

### Post by tgalati4 on 2014-10-15
Pull the bottom cover and pull out the original wireless card.  The original card's problem could be a worn out antenna wire.  The antennae feed through the hinge and get shorted.  If you have two antenna connections, pull one and see if reception improves.

---

### Post by bugbear6502 on 2014-10-15
> **TheFu said:**
> TL;DR - just blacklist the onboard wifi driver.

Put the driver into:
  /etc/modprobe.d/blacklist.conf

No need - it's already "not loaded"; but this means that the network manager
is convinced I'm not using wireless, and don't want to use wireless, despite
the (rather nice) USB wireless adapter I've got.

Ideally I just want to enable ***wire-less-ness*** in the network manager
without enabling the built in wireless card.

 BugBear

---

### Post by bugbear6502 on 2014-10-15
> **tgalati4 said:**
> Pull the bottom cover and pull out the original wireless card.  The original card's problem could be a worn out antenna wire.  The antennae feed through the hinge and get shorted.  If you have two antenna connections, pull one and see if reception improves.

That might help the internal card, but the driver (westron_btns) for the card
KILLS my machine (see link in first post for details)

 BugBear

---

### Post by chili555 on 2014-10-15
> **bugbear6502 said:**
> That might help the internal card, but the driver (westron_btns) for the card
KILLS my machine (see link in first post for details)

 BugBearI have read post #1 and the links carefully and I'm still not quite sure I fully understand the problem. wistron_ btns is *NOT* a driver for your internal wireless card; it is a helper that is supposed to translate laptop buttons ( btns!!) into usable requests such as Fn+F4 means 'please turn on the danged wireless.' 

wistron_btns is not included by default in Ubuntu 14.04 and hasn't been for several versions prior. How old is your Ubuntu version? Have you tried the latest live DVD? Does the problem remain?

Are you saying that any wireless key combination cannot enable the wireless? If you unload wistron_btns, then does the wireless spring to life?```
sudo modprobe -r wistron_btns
```What is the actual driver for the internal card?```
sudo lshw -C network
```

---

### Post by TheFu on 2014-10-15
I use wicd-curses to manage my network connections instead of network-manager. The important part is recognizing when both wired and wifi are enabled and forcing 1 of them "down" using ifconfig.  Sometimes rfkill is needed to stop/enable the wifi too.

Doubt any of this is useful for a seamless GUI experience. It is just how I do it on a minimal GUI desktop.

---

### Post by weatherman2 on 2014-10-15
You might actually be able to replace the wireless card with a different one that works.  If this is an old laptop, maybe 802.11g is the fastest internal card that will work, however.  But it can probably be done pretty cheaply and, depending on the laptop design (if the card is easy to access say from the bottom) fairly easily.

Some laptop manufacturers (Lenovo/IBM and HP are the only ones I know of for sure) will "whitelist" their wireless cards, so you can't install any card but a few approved by the manufacturer for that model.  Other manufacturers (Dell, Acer, Toshiba, etc.) do not do this, and it is possible to install almost any wireless card that will fit in the slot.  I have upgraded a lot of laptop wireless cards successfully.  I don't know if your Amipro would use a whitelist or not or how old it is...

---

### Post by bugbear6502 on 2014-10-16
Heh. The story moves forward.

I pushed the (wireless) button.

Wireless leapt into life, both on board and USB adapter.

westron_btns IS installed, appears to do what it's meant to (interface the
button to the built-in card), and isn't killing the CPU, which it DID
when I ran the installer CD.

I am at a loss to (as yet) explain almost all of this.

 BugBear

---

### Post by chili555 on 2014-10-16
We're almost there! Now please run:```
sudo lshw -C network
```Please extract the details about the internal wireless card and post them all here. We'll blacklist its driver and you'll be all set.

---

### Post by bugbear6502 on 2014-10-16
> **chili555 said:**
> We're almost there! Now please run:```
sudo lshw -C network
```Please extract the details about the internal wireless card and post them all here. We'll blacklist its driver and you'll be all set.

```
 *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:65:c3:c6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:e0203000-e0203fff

```
```
sudo lsmod | grep ipw2200
ipw2200               136401  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
cfg80211              409394  5 ath,mac80211,libipw,ath9k_htc,ipw2200


```

   BugBear

---

### Post by chili555 on 2014-10-16
Almost done! From a terminal:```
sudo -i
echo "blacklist ipw2200"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ipw2200
exit
```Please type and proofread carefully. No typos allowed!!

Solved?

---

### Post by bugbear6502 on 2014-10-16
> **chili555 said:**
> Almost done! From a terminal:```
sudo -i
echo "blacklist ipw2200"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ipw2200
exit
```Please type and proofread carefully. No typos allowed!!

Solved?

Yes!

Interestingly, it's also no longer showing westron_btns, and the USB wireless is permanently on.

Which is what I want :D


So - thanks to all who helped, and how do I mark this "solved"?
 
BugBear

---

### Post by chili555 on 2014-10-16
Please use thread tools at the top to mark Solved.

Glad its working!

---

### Post by bugbear6502 on 2014-10-16
> **chili555 said:**
> Please use thread tools at the top to mark Solved.

Glad its working!

Thanks for your help - and Ubuntu for bringing back support for non-PAE!

My laptop is both useful and up to date again.

 BugBear

---

