---
title: "Spurious DSL problem: timeout waiting for PADO"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by danielgruen on 2007-03-15
Hi all,

I was trying to install Ubuntu (to be exact: the older version 5.04 of Kubuntu which I happen to have on CD) on one of my father's computers. After giving up on the newer one with a unrecognized hard disk driver, I decided to go for a pretty old 233 Pentium II.

Installation took some time but worked, the problem is DSL support. DSL did work on that particular computer with Windows 98 and a ethernet-cable connected DSL modem (Lucent Cell 19A-BX-AR). Note that this is a rather old modem to which you need a pppoe connection, none of these in-built router modems or something. I used to have no problems with the same kind of modem with the same cables and same version of Ubuntu on a different computer (yet not exactly the same).

Problem is: pppoeconf wouldn't find an access concentrator (while there was a functioning concentrator present, trying 3 minutes before and after the pppoeconf attempt with another computer on the same cable/modem). Error message was "Timeout waiting for PADO packet", after, according to the log pppoe-discovery offers, having sent 3 PADI packages without reply from the access concentrator.

How can that be? Or rather: what's the problem? 
Is it the modem's fault to not in any way work with the linux pppoe properly? Would a newer version of Ubuntu thus possibly work (or will I just have to abandon my quest to actually have internet access with this modem and linux)? Can it be the computer's/network card's fault (although for all I can see the network card seems to be supported), so that it would make sense to try again with a different computer?

Thanks in advance for your help & suggestions

Daniel

---

