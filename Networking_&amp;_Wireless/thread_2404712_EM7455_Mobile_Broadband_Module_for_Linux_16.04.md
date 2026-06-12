---
title: "EM7455 Mobile Broadband Module for Linux 16.04"
date: 2018-10-27
forum: Networking &amp; Wireless
---

### Post by jhcnh on 2018-10-27
Hello,

I am trying to connect my computer to my mobile plan.  I have a [NUVO-5104VTC]("https://www.neousys-tech.com/Resource/Product_Document/Nuvo-5100VTC-series/Nuvo-5100VTC-Series-User-Manual-Rev-1_0.pdf") computer, with an [EM7455]("https://www.logicsupply.com/nwk200/") module installed.  I am trying to utilize the external SIM slot with a Verizon SIM card which is activated.

I am unable to complete the activation steps for connecting to my SIM card.  I tried to complete the following steps:

Change active SIM slot to be the external slot
&#9675; sudo minicom -s
&#9632; Serial port setup
&#9679; Press a - change name to ‘/dev/ttyUSB2’
&#9679; Press g to change software flow control to YES
&#9679; Exit (this will drop you to a new shell)
&#9632; Enter these commands one at a time
&#9679; ate1
&#9679; AT!CUSTOM="UIM2ENABLE",1
&#9679; AT!UIMS=1
&#9632; Press CTRL+A, Q


I receive an error when I try the command: AT!CUSTOM="UIM2ENABLE", 1

When I try AT+ICCID, I get an error.

The packages I have installed for this are:
ModemManager
lbqmi 1.16
lbmbim 1.14
minicom

I am not sure if my modem recognizes my SIM card, or if my SIM card is not working, or if the physical SIM card slot is broken.

Could someone help me with some steps to diagnose the issue, and what I could possibly do to fix it?  I do not have access to internet on the computer so any sudo apt install/update commands will need to be done offline.

Thank you!

---

