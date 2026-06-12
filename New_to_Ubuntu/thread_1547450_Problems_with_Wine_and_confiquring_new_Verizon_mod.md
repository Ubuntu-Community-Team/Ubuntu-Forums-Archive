---
title: "Problems with Wine and confiquring new Verizon modem"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Humanities Major on 2010-08-06
I was trying to configure my new modem from Verizon using Wine to run the installation software and I encountered a weird and seemingly unsolvable (to me at least) problem.  When I run any exe files the window opens but is completely blank, now matter how long I leave it for.  Wine ran the installer fine but the actual software just does not open in any functional sense.  It is not just the verizon software either.  I tried opening the internet explorer that is packaged with wine but I get the same blank window.  I have never had to use wine before so as far as I can tell it has never worked.  I installed it from the synaptic package manager if that makes any difference.  My question is does anyone either no how to fix this or know how to hack a modem to configure it without the software.

Oh, I have a dell inspiron 1420 and am currently running Ubuntu 9.04

---

### Post by davidmohammed on 2010-08-06
you should not use wine to run devices - they mostly, if ever, do not work.

what sort of modem is it - usb/pci?

assuming this is a usb device then

in a terminal session

plugin your usb device

type 

lsusb

copy and paste the output in a reply here (within code tags please).


type 

dmesg

copy and paste the screenful of text displayed here (within code tags please).

---

### Post by S.R on 2010-08-06
While your computer is connected to the modem type in your browser 192.168.1.1
If I am remembering correctly your user name is admin and password is either admin or password.

I am not at my home computer so I can't give you the details of the setup and really wouldn't know where to begin with out knowing your modem make and model.

---

