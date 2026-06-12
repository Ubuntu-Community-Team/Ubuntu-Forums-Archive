---
title: "Printer is not detected"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by mrphud on 2010-08-15
Hello,

I have a Brother HL-2170W printer hooked up to 10.04. The problem is, I cannot print.

I was able to print only once when I first hooked it up. Till then it will not detect the printer. I have tried to unplug and the plug in the usb with no success.

When I go to system->admin->printing I see no printer listed.

What should I do?

---

### Post by scrooge_74 on 2010-08-15
Hook it up, then open your web browser and type localhost:631 see if the printer gets detected.

Your user may not have usb privileges, can you hook any other usb device and it gets detected?

---

### Post by jtarin on 2010-08-15
Use the [CUPS ]("http://www.cups.org/articles.php?L274")web interface. Click this link [http://localhost:631](http://localhost:631). Then setup your printer from there.

---

### Post by mrphud on 2010-08-15
Hi scrooge,

OK so what I did first was reboot. I went back to sys->admin->printing and vwala. The printer showed up. I have no idea why it wasn't there before. 

I also did the localhost:631 and it showed up there to.

I am the only user on this comp. I guess for now the problem is solved. I just don't know why ubuntu is so fickle from boot to boot.

thanks

---

### Post by scrooge_74 on 2010-08-15
Is not ubuntu per se, could be a usb problem of some sort, I had issues in the past with cups not detecting stuff inside gnome and then having to use the web management tool of cups to add the printer.

If you have more PCs that need to use that printer you can use the webtool from each one to add the one you have.

In fact in most cases I find easier to set up printers on a network from the webtool or the gnome printing tool than doing that in a Windows network.

---

