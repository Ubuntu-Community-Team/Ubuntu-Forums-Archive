---
title: "dwl-g120(D-link) on edgy eft"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by frustratedandnewtolinux59 on 2007-02-04
:shock: Hi,
I installed ubuntu on my compaq presario about a week ago and have been constanly trying to install a dwl-g120 (not rev1 or + or anything else) d-link card ever since. I already have ndis wrapper installed and my machine recognizes when the card is plugged in (as eth1) or not however, when i type (in terminal):

sudo iwlist eth1 scan

it returns:

eth1        No scan results

Please help me asap! Before my head explodes! :shock:

---

### Post by bnuytten on 2007-02-18
As it says. It cannot find wireless networks. I once had this one I (deliberatly) removed the antenna from the wireless card. Can you post the output of iwconfig?

Check your router if it is broadcasting it's SSID.

---

### Post by mraudiofreak on 2007-06-02
I just got this card working, I posted what I did [here]("http://ubuntuforums.org/showthread.php?t=461668&highlight=dwl-g120").

---

