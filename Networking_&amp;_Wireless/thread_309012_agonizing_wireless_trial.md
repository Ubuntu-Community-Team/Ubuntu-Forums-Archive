---
title: "agonizing wireless trial"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by JFC on 2006-11-29
Hi and thanks in advance or your help.  

I've been struggling with this for hours and am close to giving up.

I recently updated to Edgy from Dapper, in which I managed, after some effort, to get my D-Link DWL-G650 card running in WPA mode under WPA Supplicant.

Now when I try to do the same with Edgy I can't manage it.

I've gone through every troubleshooting guide I can find and am still baffled.  And because the balky computer won't connect to the internet by any means, I won't be able to quote the terminal outputs.  But I will try to describe them.

The lights on the card blink alternately, but not together as they do when connected.

In the Connection Properties window, the only connection that appears is "lo."  

In System/Networking the card shows up but, when I open the Properties window, there's no list of Networks to choose from.

_sudo iwconfig_ gives:

ath1 ESSID="RAP1"
Access Point: Not-Associated
everything else normal except link quality=0/94

_sudo ifconig_ gives:

ath1 Link encap:Ethernet
HWaddr 00:13:46:02:81:2C
inet6 addr: e80::213:46:fe02:812c/64 Scope: Link
everything else is 0's


_iwlist ath1 scan_ gives:

10 diferent cells, with RAP1, the one I'm trying to connect to, on the list as follows (I've elided what seems normal):

Address: 00:0D:88:BA:6D:AE
ESSID: "RAP1"
Quality=46/94 . . . .
. . . .
IE: WPA Version 1
Group Cipher: TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1): PSK
Extra:ath_ie=dd0900037010100067f


_lshw_ gives:

logical name: wifil
configuration: broadcast=yes driver=ath_pci multicast=yes wireless=IEEE 802.11g


_sudo pccardctl ident_ gives:

Socket 0
no product info available

---

