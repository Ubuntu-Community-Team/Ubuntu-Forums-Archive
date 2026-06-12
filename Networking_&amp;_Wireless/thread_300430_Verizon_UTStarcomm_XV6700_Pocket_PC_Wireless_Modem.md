---
title: "Verizon UTStarcomm XV6700 Pocket PC Wireless Modem"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by WillB on 2006-11-15
Hey folks..I have a Verizon UTStarcomm XV6700 Pocket PC with the wireless tether option all opened up on the phone.. On WinXP its a simple driver install, plug in the USB cord (which is what I want to use as opposed to bluetooth) and start the dialer..on the phone you simply start the WModem app.  I have my laptop dual booting xp and Edgy right now but would like to wipe XP for good.  The problem is this phone is my internet connection, period.  EVDO is fast and all I need around my area. Does anyone know of someone who has gotten this to work?  The Verizon CD only has win drivers.  Would the ndisWrapper work for this setup? And if so, how would I go about dialing the modem? 

Runnin on a Dell Inspiron 4150..I'm pretty savvy with windows and work as a software engineer, but have neglected unix forever until now.  I understand the concepts here that I will need but the implementation under Ubuntu is foreign.  Thank you all for any help I get.

---

### Post by gotmonkey on 2006-12-13
Unfortunately, you are in the same boat that I am.  The only distro that I have been able to get xv6700 working on as a modem is Fedora Core. From what I can tell it has something to do with the redhat networking tools. Debian based systems like ubuntu use a different network manager system

---

### Post by gotmonkey on 2006-12-13
another coffee drinker posted this:

[http://ubuntuforums.org/showpost.php?p=1866807&postcount=1](http://ubuntuforums.org/showpost.php?p=1866807&postcount=1)

hopefully it works for you. I will give it a try myself this weekend. I prefer ubuntu over fedora, but for my job, I needed to have an internet connection

---

### Post by WillB on 2006-12-14
Thank you, I'll give this a try tonight!

---

### Post by gotmonkey on 2006-12-15
> **WillB said:**
> Thank you, I'll give this a try tonight!


I just tried Craig's guide. Worked like a charm. Now I just need to create a launcher for it. It is nice to not be tied to fedora

---

### Post by toddunder on 2006-12-23
So, this isn't working for me and i'm not sure why.

i followed the instructions at 

[http://ubuntuforums.org/showpost.php?p=1866807&postcount=1](http://ubuntuforums.org/showpost.php?p=1866807&postcount=1)

but can't get the ipaq driver to see my verizon xv6700 phone.  i'm using 6.06 and got to the modprobe step.  two things seem wrong with that step.  the first, which i hope is trivial, is that 

touch /var/lock/subsys/local

doesn't work because ubuntu (at least my installation of it) doesn't have a /var/lock/subsys directory.  this was my first concern.

the next is that the driver loads but never sees the device.

root@durruti:~# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 009: ID 0bb4:00cf High Tech Computer Corp. SPV C500 Smart Phone
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

ok, so far so good.

/sbin/modprobe ipaq vendor=0x0bb4 product=0b020

so i put that in rc.local.  seems good.

now, when i plug in the devicei get:

Dec 23 16:26:49 localhost kernel: [17181247.472000] usbcore: deregistering driver ipaq
Dec 23 16:26:49 localhost kernel: [17181247.472000] drivers/usb/serial/usb-serial.c: USB Serial deregistering driver PocketPC PDA
Dec 23 16:27:07 localhost kernel: [17181265.052000] drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PD
A
Dec 23 16:27:07 localhost kernel: [17181265.052000] drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
Dec 23 16:27:07 localhost kernel: [17181265.052000] usbcore: registered new driver ipaq
Dec 23 16:27:14 localhost kernel: [17181272.236000] usb 1-2: new full speed USB device using uhci_hcd and address 10
Dec 23 16:27:19 localhost kernel: [17181277.288000] usb 1-2: USB disconnect, address 10
Dec 23 16:27:20 localhost kernel: [17181278.032000] usb 1-2: new full speed USB device using uhci_hcd and address 11
Dec 23 16:27:38 localhost kernel: [17181296.576000] usb 1-2: new full speed USB device using uhci_hcd and address 12

and so on.

so uhci_hcd driver seems to be trying take the device rather than the ipaq driver.  i can try unloading uhci_hcd (which seems to cause no end of problems) but i'm not sure if that's the right thing to do.  suggestions?

t.

---

### Post by toddunder on 2006-12-23
odd.  the lsusb numbers seem to have changed.  that's ok cause it's working now.  perhaps it had something to do with running wmodem on the device when scanning lsusb versus not.  anyway, on to the rest of the howto!

t.

---

### Post by eamlie on 2007-05-21
This guys thread WORKS LIKE A CHAMP!!! I am a total ubuntu newbie who just blew away his XP and replaced it w 7.04. I never thought in a MILLION years my 6700 would work with it but I Googled it just for $hits and giggles: [http://ubuntuforums.org/showthread.php?t=326727](http://ubuntuforums.org/showthread.php?t=326727)
The only exception to his notes is that if /dev/ttyUSB0 is NOT there, you WILL have to start WModem, hook it to your USB port and "detect" from within gnome-ppp in order to get /dev/ttyUSB0 created. "detect" will never finish, but the blue light flashes once or twice in WModem and I think that is when "detect" must create the directory. I am totally psyched!!! Thanks, whoever you are!

---

