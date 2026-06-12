---
title: "usb communication problems with hp photosmart printer"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by woody1 on 2009-03-02
Been having a problem with this printer for a while, works fine on Win98!!.
Various suggestions tried, modified 55-hpmud.rules ,downloaded latest driver, etc.
Thinking about the intermittent nature of the problem I realised that I had not checked the basics. Took a lot of digging then found lsusb. The printer shows up on 03f0:b802 when it is first turned on, running lsusb over a period of a few minutes, still there. Start HPsetup printer appears in the box then immediatley says it has a problem, then popup box says printer may not be connected. lsusb confirms this, unplugging and replugging the usb cable seems to have no effect.Refreshing the HP device manager gives "ERROR No device found or unsuported device" ,the only way to get the printer to be recognised by lsusb is to remove power from the printer, restore power and turn on.This enabled me to print a test page , the popup box on the printer icon at the top of the screen said printer ready, with an option to "Configure", I selected "Print test page" , the HP Document print status is still showing pending jobs. lsusb still shows "03f0:b802 Hewlett Packard". Sending another document after clearing the print queue gives a 

"**Printer error** Printer'Photosmart_7400_series':'media jam'"

 . Lsusb no longer reports a printer.

I am getting to the stage of Samba share and leave the printer on the Windoze machine.

What am I doing Wrong. How do I logically fault find this?

I tried plugging the printer into another usb port, it was then recognised and worked for a short while.  I have tried all of the usb ports with different devices and they all work. The printer still works reliably on a Windoze98 machine

---

