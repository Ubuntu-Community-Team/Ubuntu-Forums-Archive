---
title: "Netgear N300 Wireless USB Adapter WNA3100"
date: 2017-11-17
forum: Networking &amp; Wireless
---

### Post by mcpaulo on 2017-11-17
Hi all, I have very recently just installed linux on an old computer of mine and enjoy it, the old computer does not have any kind of Wireless Card installed so a bought a USB adapter, the usb adapter came with a dvd to install the software and obviously a usb adapter. When I insert the DVD into my computer it rejects all the files on the dvd and says "An error occures while loading the archive". How do I install the hardware and use the adapter?

---

### Post by Bucky Ball on 2017-11-18
Welcome.

> **mcpaulo said:**
> Hi all, I have very recently just installed linux on an old computer of mine ...

Linux what? Ubuntu? Which release (16.04 LTS, 17.10, etc.) and which flavour (Xubuntu, Ubuntu, Kubuntu or something else)?

For a start, forget the wireless dongle install DVD. Nothing to do with Linux and you won't need it. Linux is NOT like Win in as much as you don't need to install drivers manually for every single bit of hardware you connect (or punch in 25 digit authorisation codes!). Generally, the driver is already in the Ubuntu kernel.

You need Linux drivers, not Windows drivers which is probably all that are on that DVD.

You particular donlgle (WNA3100) has been notoriously difficult to get going in Ubuntu in the past. Perhaps that has changed in the present as haven't seen many threads on it for awhile.

If you let us know which Linux OS you are running we can move further. Assuming you're using Ubuntu, switch off the computer, pull the wireless dongle out, switch on the computer and when at a desktop, open a terminal.

Plug the wireless dongle in and, in the terminal, type this and hit return.

```
dmesg
```

Do you see any info at the bottom of that output regarding your wireless dongle or Ubuntu installing a driver for it (or failing to)?

---

### Post by wildmanne39 on 2017-11-18
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by danstafford on 2018-03-06
I just spent six hours trying to get a Netgear N300 / WNA3100 to run on Ubuntu 16.04.4 LTS and no joy. The thing is going back to the return desk at Target. I ordered a [COLOR=#000000]TP-LINK TL-WN723N N150.

That was reported in another thread on the Netgear (there must be about 10 threads at least on this so-called wifi adapter) as being plug-n-play.

I'll have to wait on the TP-Link to ship via Amazon, but it beats banging my noob head against the wall.[/COLOR]

---

