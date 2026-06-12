---
title: "Log message : txs packet size do not coinsist with txd"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by PsyCHZZZ on 2007-10-09
Hi there, 

I'm having an issue trying to figure out what these messages meant. I found these messages in my **/var/log/kern.log** and they seem to repeat over a number of times in an hour.

It'll always start with the 
> Oct  9 14:00:46 noob kernel: [88341.182541] eth0: txs packet size do not coinsist with txd txd_:0x000044ba, txs_:0x000105c4!

and then ends with

> Oct  9 14:00:58 noob kernel: [88352.663199] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>

and after like 10 minutes or so... the same loop happens again.

Although it doesn't really affect my network (not that I know of anyway), I don't think it's normal messages.

Can anyone help shed some light on these messages??? Thanks :)

> 
Oct  9 14:00:46 noob kernel: [88341.182541] eth0: txs packet size do not coinsist with txd txd_:0x000044ba, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.182547] txd read ptr: 0x740
Oct  9 14:00:46 noob kernel: [88341.182548] txs-behind:0x000105b6
Oct  9 14:00:46 noob kernel: [88341.182550] txs-before:0x000100d8
Oct  9 14:00:46 noob kernel: [88341.182947] eth0: txs packet size do not coinsist with txd txd_:0x1c855537, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.182951] txd read ptr: 0xc00
Oct  9 14:00:46 noob kernel: [88341.182953] txs-behind:0x800105c4
Oct  9 14:00:46 noob kernel: [88341.182954] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.182956] eth0: txs packet size do not coinsist with txd txd_:0xcbebe90f, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.182959] txd read ptr: 0x113c
Oct  9 14:00:46 noob kernel: [88341.182960] txs-behind:0x800105c4
Oct  9 14:00:46 noob kernel: [88341.182962] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.182964] eth0: txs packet size do not coinsist with txd txd_:0xff87466e, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.182966] txd read ptr: 0x1250
Oct  9 14:00:46 noob kernel: [88341.182968] txs-behind:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.182969] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.183353] eth0: txs packet size do not coinsist with txd txd_:0xc4eacedf, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.183355] txd read ptr: 0x18c4
Oct  9 14:00:46 noob kernel: [88341.183357] txs-behind:0x80010316
Oct  9 14:00:46 noob kernel: [88341.183358] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.183360] eth0: txs packet size do not coinsist with txd txd_:0x958c3820, txs_:0x00010316!
Oct  9 14:00:46 noob kernel: [88341.183363] txd read ptr: 0x1fa8
Oct  9 14:00:46 noob kernel: [88341.183364] txs-behind:0x000103f7
Oct  9 14:00:46 noob kernel: [88341.183366] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.184196] eth0: txs packet size do not coinsist with txd txd_:0xbd0f33f5, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.184199] txd read ptr: 0x1fcc
Oct  9 14:00:46 noob kernel: [88341.184200] txs-behind:0x800105c4
Oct  9 14:00:46 noob kernel: [88341.184202] txs-before:0x00010316
Oct  9 14:00:46 noob kernel: [88341.184204] eth0: txs packet size do not coinsist with txd txd_:0x1d99c10a, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.184206] txd read ptr: 0x3c8
Oct  9 14:00:46 noob kernel: [88341.184208] txs-behind:0x0001003e
Oct  9 14:00:46 noob kernel: [88341.184209] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.185434] eth0: txs packet size do not coinsist with txd txd_:0x8e286136, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.185437] txd read ptr: 0x4d8
Oct  9 14:00:46 noob kernel: [88341.185438] txs-behind:0x0001003e
Oct  9 14:00:46 noob kernel: [88341.185440] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.242761] eth0: txs packet size do not coinsist with txd txd_:0xae56f1f7, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.242767] txd read ptr: 0x614
Oct  9 14:00:46 noob kernel: [88341.242769] txs-behind:0x000105b6
Oct  9 14:00:46 noob kernel: [88341.242770] txs-before:0x000105c4
Oct  9 14:00:46 noob kernel: [88341.243167] eth0: txs packet size do not coinsist with txd txd_:0x32e968ef, txs_:0x000105c4!
Oct  9 14:00:46 noob kernel: [88341.243170] txd read ptr: 0x810
Oct  9 14:00:46 noob kernel: [88341.243171] txs-behind:0x00010233
Oct  9 14:00:46 noob kernel: [88341.243173] txs-before:0x000105c4
Oct  9 14:00:56 noob kernel: [88350.516632] NETDEV WATCHDOG: eth0: transmit timed out
Oct  9 14:00:58 noob kernel: [88352.663199] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>


---

### Post by noob12 on 2007-10-09
Check cables and physical seating of the card in its slot if it is not an onboard device; I think most Attansics are onboard.  If you've done those things, this suggests a bug in the driver, a problem with timing, a problem with IRQ assignment (or a combination of these).   You should file a bug on launchpad.  They may suggest some boot flags you can use to test/workaround the issue.

---

### Post by PsyCHZZZ on 2007-10-09
Thanks a lot for the suggestions... it's an onboard NIC (on an Asus P5GC-MX) so i can only pray that it is seated properly. But I shall try with a different network cable and see if that help.

If it doesn't, then I shall follow your suggestion and file it on launchpad as a possible bug.

Cheers~

---

### Post by PsyCHZZZ on 2007-10-09
Oh... what do you know... it seems like I was not the only person facing this problem. There seems to be a submission on Launchpad already on a very similar issue... although i do not get the problems with connecting to any website; but his error messages do look alike and very similar.

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639)

Unfortunately, there's no reply yet... hmmm... i guess I might have to wait for this one.

---

