---
title: "toshiba satellite a215 ubuntu 8.10 wireless problems"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by futuresiinz on 2008-11-25
okay first of all i'd like to state im VERY new to linux...as in i didnt know anything at all before today...i've read alot about it and decided to make the switch and am very happy with the wired performance already...however i seem to have ran into an issue...

spending all days on the forums and toying with ndiswrapper i've gotten it to "claim" my wireless card which is a drastic improvement from this morning and me trying 12 different drivers and failing to even get that all day...however after running the dmesg | grep -e ndis -e wlan command i got yet another error...the forum post on the ndiswrapper trouble shooting which has been my friend all day didnt seem to have anything about the error i received which is:

[   17.292871] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.494125] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   17.499388] ndiswrapper (link_pe_images:603): **DLL initialize failed for athwx.sys**
[   17.499446] ndiswrapper: driver netathwx (,05/20/2008,7.6.0.224) loaded
[   17.499936] ndiswrapper 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.499945] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[   17.500030] usbcore: registered new interface driver ndiswrapper

in bold font above...as i said i am new to linux so im not 100% sure but my common PC knowledge tells me thats not a good thing...if anyone has any insight into this error or a way to fix it i would greatly appriciate it

---

