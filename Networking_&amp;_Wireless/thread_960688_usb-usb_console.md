---
title: "usb-usb console"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by neilblue on 2008-10-27
Hello

I would like to connect two ubuntu machines via USB in a similar way to a serial com port connection and minicom. Please could anyone tell me if this is possible and how I may be able to set it up.

Thanks
Neil

---

### Post by GeorgeVita on 2008-11-06
Hi, as USB is a complicate serial interface (in both h/w and s/w) I think you have the following options:

a. Use a **USB to USB bridge cable** which includes special h/w interface and you must find the appropriate driver for linux (if any).

b. Use two **USB to serial cables** connected in the "traditional" way (DB9 pin 2 to 3, pin 3 to 2, pin 5 to 5). After attaching the USB to serial converter you will find the port name (/dev/ttyxxx) from the terminal command **grep -e /dev/tty /var/log/messages** (this command lists all system activity on **/dev/tty**). Then you can setup **minicom** and try it.

Regards,
George

(... and also are other ways to connect 2 computers as ethernet)

---

### Post by neilblue on 2008-11-07
Thanks George,

I wasn't sure if it was difficult to do, or just difficult to find information on, so you have cleared that up for me. I guess now I will need to look at setting up a ttyUSB console in the new kernel as the machines I am using don't have serial ports at all :)

Cheers
Neil

---

### Post by Martin von Wittich on 2009-01-15
Hi,

I've written a Perl udev helper "usbconsole" some time ago to support USB-to-USB console cables (2xUSB-to-Serial cables connected by a RS232 cable) for the company I'm working for. We're using it to administer headless servers on location; a real serial console would be nicer because it also works during boot, but that would have to be configured before use and that was not an option for us.

The implementation is a rather simple 7k perl script that gets spawned by udev as soon as a USB-to-Serial cable is connected (downside: you can't use USB-to-Serial cables for anything else on servers running usbconsole); it waits for the usbtty device to settle and then spawns a getty on it.
You can then use screen or minicom on the other computer to connect to the server.

The project is hosted on LP: [https://launchpad.net/usbconsole](https://launchpad.net/usbconsole)

Go to Code, lp:usbconsole, Source Code, and download file files 85-usbconsole.rules, usbconsole and README and follow the instructions. If I find the time, I'll try to create a deb package for it, then it could be possible to put it as a package into Ubuntu itself.

---

### Post by sej7278 on 2010-02-19
i'm interested in this, as i could do with console access during init, before udev for entering a luks passphrase, on a machine that doesn't have a serial port.

most machines don't have serial ports anymore, so not sure why usb consoles don't seem to exist, i guess everyone is supposed to fork out for a LOM/ILO card and terminal server for their machines, but i'd prefer not to do it over IP anyway.

---

### Post by Martin von Wittich on 2010-04-24
> **sej7278 said:**
> i'm interested in this, as i could do with console access during init, before udev for entering a luks passphrase, on a machine that doesn't have a serial port.


On the one hand, you can run userspace code in the initramfs so it should be possible to spawn a getty; on the other hand, the current usbconsole implementation depends on udev for triggering, so it won't work from initramfs. Also, usbconsole opens up a new shell, so you can't just directly type in your passphrase. There should be another server-based solution for unlocking LUKS volumes over network, you should have a look at that.

Martin

---

