---
title: "Help: DWL 650 revP 16 bit PC Card on Thinkpad T21"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by ymeng on 2006-10-19
I am a newbie in linux world. I have wasted countless
hours recently on a DLink DWL 650 RevP, Chipset Prism
3 (best I can confirm), 16-bit PC card on a new Ubuntu
6.06-1 install.

I wonder if some expert can tell me whether I'm
embarking on a impossible project tyring to get it
work on an IBM T21. (I also have a T20, same result).
 
Here is what I have observed and tried so far:
 
1. act LED on the card comes on when plugged in, link LED is off
2. iwconfig show "no wireless extension"
3. lspci doesn't show the device. I vaguely remember
some place mentioned that because this is a 16-bit
card, so lspci won't display the device?
 
4. I tried re-install ubuntu both with and without the
card plugged in
 
5. When the card is plugged in, cardctl can display:
product info: "D-Link", "DWL-650 Wireless PC Card
RevP", "ISL37101P-10", "A3"
  manfid: 0x000b, 0x7110
  function: 6 (network)

6. I tried ndiswrapper, I was able to see "netprism
driver installed" with "ndiswrapper -l " command, but
it didn't show "driver present".
 
7. I also see the card info shows up in
/etc/pcmcia/wlan-ng.conf:card "D-Link DWL-650 rev P
802.11b WLAN card"
   manfid 0x000b, 0x7110
#  version "D-Link", "DWL-650 Wireless PC Card RevP",
"ISL37101P-10", "A3"
   bind "prism2_cs"

None of these attempts worked. I posted around online,
no help so far.
 
I have been hesitating venturing into Linux world for
a couple of years. Most of the time get discouraged on
misc. hardware issues. (My Ubuntu on IBM T21 and on
another Sony desktop also have ACPI power issues,
drive me nuts!)
 
Any help is greatly appreciated.
Many thanks in advance.

---

### Post by bountikilla on 2007-09-21
I have the same issue. With the same computer and card. The driver installs in ndiswrapper but the computer won't recognize the card in lspci. Can anyone help us out?:confused:

---

