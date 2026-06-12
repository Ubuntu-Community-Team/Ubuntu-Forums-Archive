---
title: "VirtualBox Printing"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by jumpa72 on 2009-04-16
Hi,
I've installed VirtualBox 2.2 and created a Windows 2000 guest.
I've successfully installed in the guest a printer, the HP Designjet 70 (HP does not release Linux driver for this printer :( ): the problem is that I cannot print! If I try to print the test page I have an error msg. :(
The printer is connected through an USB 1.0 port.
Do you have some suggestions?
Thank you

---

### Post by xarquid on 2009-04-16
Please make sure that in your Settings, in VirtualBox, that USB is enabled.

>Power off your VM by going to Machine > ACPI Shutdown.
> Now right click on your VM (Windows) and go to Settings.
> Click on "Settings..."
> Click on the USB tab.
> Make sure "Enable USB Controller" is checked.
> If you have USB 2.0 support, which most computers (newer) do, you can check the second sub-box.
> You can add your devices individually here (using the second bottom with +) or add all devices using the first button. Hover over them for descriptions of what they do.

Now, in Windows, make sure to INSTALL the printer in Control Panel > Printers. This must be done in order to print from it. It's like having Windows running as an operating system on your machine. You will need the driver disk if Windows does not automatically detect it or download the Windows driver from the manufacturer's website.

Great VirtualBox guides/docs:
[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by jumpa72 on 2009-04-17
I've already installed the printer in Windows. The printer is in the printer control panel, and it is the default printer. It seems that I've only read permission, not write, on the USB device.
I'm running Ubuntu server version 8.10.
I don't find the usbusers group, so I create it. But I don't know where I have to set privilegies.

---

### Post by mlentink on 2009-04-17
Did you install VBox form the repo's or from the Sun site? If so, did you install the OSE version or the closed source version? Only the latter has USB-support...

---

### Post by jumpa72 on 2009-04-17
I've installed from SUN.I don't know if I have OSE or closed...
but the USB works: I've tried a flash memory and I can read n write on it.
The printer is recognized and installedby the guest OS, but it don't print...

---

