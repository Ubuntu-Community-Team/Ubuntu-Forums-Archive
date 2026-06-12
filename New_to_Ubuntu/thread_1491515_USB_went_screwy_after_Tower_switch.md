---
title: "USB went screwy after Tower switch"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by klinster on 2010-05-23
I don't know if this is the right spot but here it goes:

I'm new to Ubuntu and I switched towers recently because the old tower was small and the new  one is upgrade-able. The usb inputs on front and back worked fine on the  old tower but on the new tower I am experiencing transfer rate drops.  I've searched the forum and did the kernel update found here [http://ubuntuforums.org/showthread.php?t=1487590](http://ubuntuforums.org/showthread.php?t=1487590)

I've tried plugging in the usb/external hard drive straight to the  motherboard's usbs (the back of the computer) and I still get a slow  transfer rate.

Well the computer is a HP Pavillion a1240n with the only difference  being two new usb readers on the front: 1 being a card reader with 1 usb
the other has 2 usb inputs and 2 sound inputs which came with the tower.

I'm running Ubuntu 10 x86

---

### Post by nhasian on 2010-05-23
just to clarify, does this mean that you took all the guts out of your old case and moved the same parts to a NEW larger case for expandibility?  Or did you replace your tower with a new computer?

> **klinster said:**
> I switched towers recently because the old tower was small and the new  one is upgrade-able.

---

### Post by klinster on 2010-05-23
I took the guts out of the old case and put them in the new case. Sorry about that..

So just to restate, It's the same computer in a different case but now it has different front usb inputs.

If I try to copy big files to my external hard drive (500mb-1g) it takes forever. It used to take 1-2 minutes tops when I had the same computer on the old case. Even plugging the external hard drive on the back of the computer causes speed drops as well.

---

### Post by kmsalex on 2010-05-23
open up the case, disconnect the wires running from the motherboard to the front usb ports, start up the computer and test out the speed of the back ports, if the speed increases significantly then the front ports are drawing on the total band with the board can supply. if the speeds the same, maby you damaged something in the process of switching the cases.

---

### Post by lavinog on 2010-05-23
What brand case is it?
I have a couple of antec cases. 2 of them have an older date code and have a different front usb module than then ones with the newer date code.  I had a problem with the older design where plugging in a usb device that was recently plugged into another computer would cause the computer to restart.  I requested new modules from antec, and they quickly sent them out.  The problem is fixed now.
It may not be the issue in your case, but I figured I would share my experience to point out that it could be the case.

---

### Post by klinster on 2010-05-23
> **kmsalex said:**
> open up the case, disconnect the wires running from the motherboard to the front usb ports, start up the computer and test out the speed of the back ports, if the speed increases significantly then the front ports are drawing on the total band with the board can supply. if the speeds the same, maby you damaged something in the process of switching the cases.

Ok that did the trick. Seems like my card reader is sucking up too much power from the Motherboard.

Now if I want to use that card reader in the future do I need a new Motherboard?

---

### Post by anewguy on 2010-05-24
> **klinster said:**
> Ok that did the trick. Seems like my card reader is sucking up too much power from the Motherboard.

Now if I want to use that card reader in the future do I need a new Motherboard?

I could be way wrong here, but I think that what is happening is that you have a single USB controller, with 2 outputs directly on the motherboard rear and the other 2 by motherboard internal connection, and your card reader is USB 1 speeds, which is probably dragging the entire USB bus off the single controller down to USB 1 speeds.  I would assume that even if there is no card in the card reader, it is still recognized at boot and therefore the speed is USB 1 speeds.  If you don't know, there is a very considerable speed difference between USB 1 and USB2.

What can you do to correct this problem?  If you have an available PCI slot, buy a cheapy USB 2 adapter card and use it for the devices you currently plug into the rear USB.  Keep the existing rear USB for slower devices and leave your card reader connected.  A 4-port USB 2 card can be had fairly cheap - like $7.99 at MicroCenter, and no matter where you buy it a cheap card shouldn't cost more than $20 tops.



Dave ;)

---

### Post by klinster on 2010-05-24
> **anewguy said:**
> I could be way wrong here, but I think that what is happening is that you have a single USB controller, with 2 outputs directly on the motherboard rear and the other 2 by motherboard internal connection, and your card reader is USB 1 speeds, which is probably dragging the entire USB bus off the single controller down to USB 1 speeds.  I would assume that even if there is no card in the card reader, it is still recognized at boot and therefore the speed is USB 1 speeds.  If you don't know, there is a very considerable speed difference between USB 1 and USB2.

What can you do to correct this problem?  If you have an available PCI slot, buy a cheapy USB 2 adapter card and use it for the devices you currently plug into the rear USB.  Keep the existing rear USB for slower devices and leave your card reader connected.  A 4-port USB 2 card can be had fairly cheap - like $7.99 at MicroCenter, and no matter where you buy it a cheap card shouldn't cost more than $20 tops.



Dave ;)


The card reader is USB 2.0 according to the retail box and Ubuntu also recognized it as USB 2.0 when I did lsusb on terminal.

Anyway the card reader was free just wondering if this would be a problem in the future? I would need a higher-end Motherboard to be able to use it properly or might it be defective?

---

### Post by kmsalex on 2010-05-24
> **anewguy said:**
> I could be way wrong here, but I think that what is happening is that you have a single USB controller, with 2 outputs directly on the motherboard rear and the other 2 by motherboard internal connection, and your card reader is USB 1 speeds, which is probably dragging the entire USB bus off the single controller down to USB 1 speeds.  I would assume that even if there is no card in the card reader, it is still recognized at boot and therefore the speed is USB 1 speeds.  If you don't know, there is a very considerable speed difference between USB 1 and USB2.

try just conecting front ports, re-test them.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815153001&cm_re=usb_pci_card-_-15-153-001-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16815153001&cm_re=usb_pci_card-_-15-153-001-_-Product)

---

