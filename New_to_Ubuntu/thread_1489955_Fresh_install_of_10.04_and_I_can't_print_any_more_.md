---
title: "Fresh install of 10.04 and I can't print any more ...... please help"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-05-21
I installed 10.04 onto a brand new HD, copied my /home folder onto a new partition and am having all kinds of trouble.

I really need to print some invoices and can't make anything work.

All help will be very very appreciated.

---

### Post by PunkLV on 2010-05-21
Could you please be a bit more specific?

---

### Post by sydbat on 2010-05-21
> **tahitiwibble said:**
> I installed 10.04 onto a brand new HD, copied my /home folder onto a new partition and am having all kinds of trouble.

I really need to print some invoices and can't make anything work.

All help will be very very appreciated.What kind of printer do you have?

---

### Post by tahitiwibble on 2010-05-21
> **PunkLV said:**
> Could you please be a bit more specific?

I have an Epson Stylus DX 4050 printer that has been working perfectly in 9.10 and now I can't see it in System> Administration> Printing any more.

I can't add any printers and if I go to troubleshooting in the "Printing" window , and am told that "Cups Service Stopped"

---

### Post by sydbat on 2010-05-21
> **tahitiwibble said:**
> I have an Epson Stylus DX 4050 printer that has been working perfectly in 9.10 and now I can't see it in System> Administration> Printing any more.Might have to reinstall them? [http://www.openprinting.org/printer/Epson/Epson-Stylus_DX4050](http://www.openprinting.org/printer/Epson/Epson-Stylus_DX4050)

---

### Post by tahitiwibble on 2010-05-21
Sydbat, sorry but I don't know what to download there. I have a sick to the stomach feeling right now. I'm trying to sort out another problem and don't even get a response from ```
fdisk -l
```

---

### Post by sydbat on 2010-05-21
> **tahitiwibble said:**
> Sydbat, sorry but I don't know what to download there. I have a sick to the stomach feeling right now. I'm trying to sort out another problem and don't even get a response from ```
fdisk -l
```Hmmm...

What version of 10.04 are you running? 32bit? 64bit? On the page I linked, in the Gutenprint area near the bottom, choose the .deb for your install.

As for not getting anything from fdisk...I don't get anything either, but that's because I don't think it is the correct command...but I can't remember what the correct one is right now...

---

### Post by tahitiwibble on 2010-05-21
> **sydbat said:**
> Hmmm...

What version of 10.04 are you running? 32bit? 64bit? On the page I linked, in the Gutenprint area near the bottom, choose the .deb for your install.

As for not getting anything from fdisk...I don't get anything either, but that's because I don't think it is the correct command...but I can't remember what the correct one is right now...

I can't quite believe it but while thinking of how to reply to yourself, I un-installed/reinstalled CUPS in the Software Centre and all of a sudden a window pops up saying that the printer is ready to go :lolflag: .......... and it works perfectly.

A big THANKS for the shoulder ...... :)

---

### Post by sydbat on 2010-05-21
> **tahitiwibble said:**
> i can't quite believe it but while thinking of how to reply to yourself, i un-installed/reinstalled cups in the software centre and all of a sudden a window pops up saying that the printer is ready to go :lolflag: .......... And it works perfectlyYay!!!

---

### Post by tahitiwibble on 2010-06-08
Good morning to all.

I just marked this thread as "unsolved" again because my printer keeps disappearing :confused:

I am having to continually uninstall and reinstall CUPS a few times a day in order to print. 

Can anyone help to "fix" my printer?

Many thanks for any suggestions.

---

### Post by RJ12 on 2010-06-08
It won't "fix" your printer, but you could try making a script to uninstall/reinstall CUPS.:popcorn:

---

### Post by tahitiwibble on 2010-06-08
> **RJ12 said:**
> It won't "fix" your printer, but you could try making a script to uninstall/reinstall CUPS.:popcorn:

Oh how I wish :(  ............ I would if I could but I can't. Is a script simply a series of commands written in terminal?

---

### Post by mlinder on 2010-06-08
[Here]("http://www.hondatwins.com/junk/recups.zip") is a tiny script, if you want to use it. Unzip, double click the unzipped file. Make sure the file is allowed to execute.

---

### Post by jnorthr on 2010-06-08
just an idea. it would be useful to look into your system log to see what messages are being created when your cups printer falls over.

go to system>admin>log file viewer

scroll to the bottom of the panel. look for msgs related to cups or a printer failure.

is your printer hooked up by physical cables or are you using a wireless printer ?

---

### Post by tahitiwibble on 2010-06-08
> **mlinder said:**
> [Here]("http://www.hondatwins.com/junk/recups.zip") is a tiny script, if you want to use it. Unzip, double click the unzipped file. Make sure the file is allowed to execute.

My thanks to you mlinder. That should be a big help and time saver. :)

---

### Post by tahitiwibble on 2010-06-08
> **jnorthr said:**
> just an idea. it would be useful to look into your system log to see what messages are being created when your cups printer falls over.

go to system>admin>log file viewer

scroll to the bottom of the panel. look for msgs related to cups or a printer failure.

is your printer hooked up by physical cables or are you using a wireless printer ?

Thanks for the idea. I'll take a look at the log file the next time the printer, which is cabled, disappears.

I Like your signature a lot .......... no spoon! ..very good indeed :)

---

### Post by tahitiwibble on 2010-07-02
> **jnorthr said:**
> just an idea. it would be useful to look into your system log to see what messages are being created when your cups printer falls over.

go to system>admin>log file viewer

scroll to the bottom of the panel. look for msgs related to cups or a printer failure.

is your printer hooked up by physical cables or are you using a wireless printer ?

Hello, I'd be surprised in jnorthr is around but conform to his suggestion here is what I just found in the log file viewer just after the printer disappeared and I had to delete/reinstall CUPS again to be able to print.

Would anyone have a clue as to what's going on? Thanks in advance for any help. :)

from system>admin>log file viewer>syslog```
Jul  2 11:36:39 dad-desktop AptDaemon: INFO: Initializing daemon
Jul  2 11:38:56 dad-desktop kernel: [  237.728044] usb 2-1: new full speed USB device using uhci_hcd and address 3
Jul  2 11:38:56 dad-desktop kernel: [  237.906515] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 11:38:56 dad-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1
Jul  2 11:38:56 dad-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:10.0/usb2/2-1
Jul  2 11:38:56 dad-desktop udev-configure-printer: Device vendor/product is 04B8:082F
Jul  2 11:38:56 dad-desktop kernel: [  238.007612] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x082F
Jul  2 11:38:56 dad-desktop kernel: [  238.007680] usbcore: registered new interface driver usblp
Jul  2 11:38:56 dad-desktop udev-configure-printer: failed to claim interface
Jul  2 11:38:56 dad-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jul  2 11:38:56 dad-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/usb/lp0
Jul  2 11:38:56 dad-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:10.0/usb2/2-1
Jul  2 11:38:56 dad-desktop udev-configure-printer: MFG:EPSON MDL:Stylus DX4000 SERN:- serial:HU77D0701130227010
Jul  2 11:38:57 dad-desktop udev-configure-printer: failed to connect to CUPS server; giving up
Jul  2 11:40:16 dad-desktop AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String(u'cups')], signature=dbus.Signature('s'))'
Jul  2 11:40:17 dad-desktop anacron[1172]: Job `cron.daily' started
Jul  2 11:40:17 dad-desktop anacron[1586]: Updated timestamp for job `cron.daily' to 2010-07-02
Jul  2 11:40:23 dad-desktop AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/8fa2e2d455cf49aaa49bd88ba2af25a6
Jul  2 11:40:23 dad-desktop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/8fa2e2d455cf49aaa49bd88ba2af25a6
Jul  2 11:40:23 dad-desktop AptDaemon.Worker: INFO: Removing packages: 'dbus.Array([dbus.String(u'cups')], signature=dbus.Signature('s'))'
Jul  2 11:40:42 dad-desktop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/8fa2e2d455cf49aaa49bd88ba2af25a6
Jul  2 11:41:00 dad-desktop AptDaemon: INFO: InstallPackages() was called: dbus.Array([dbus.String(u'cups')], signature=dbus.Signature('s'))
Jul  2 11:41:07 dad-desktop AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/09b0778cbb3d4567a23e54ad01e58c38
Jul  2 11:41:07 dad-desktop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/09b0778cbb3d4567a23e54ad01e58c38
Jul  2 11:41:58 dad-desktop kernel: [  419.303525] type=1505 audit(1278106918.194:5):  operation="profile_load" pid=1889 name="/usr/lib/cups/backend/cups-pdf"
Jul  2 11:41:58 dad-desktop kernel: [  419.305590] type=1505 audit(1278106918.198:6):  operation="profile_load" pid=1889 name="/usr/sbin/cupsd"
Jul  2 11:41:58 dad-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1
Jul  2 11:41:58 dad-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:10.0/usb2/2-1
Jul  2 11:41:58 dad-desktop udev-configure-printer: Device vendor/product is 04B8:082F
Jul  2 11:41:58 dad-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/usb/lp0
Jul  2 11:41:58 dad-desktop udev-configure-printer: failed to claim interface
Jul  2 11:41:58 dad-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jul  2 11:41:58 dad-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:10.0/usb2/2-1
Jul  2 11:41:58 dad-desktop udev-configure-printer: MFG:EPSON MDL:Stylus DX4000 SERN:- serial:HU77D0701130227010
Jul  2 11:41:59 dad-desktop kernel: [  420.659816] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Jul  2 11:42:01 dad-desktop udev-configure-printer: URI matches without serial number: usb://EPSON/Stylus%20DX4000
Jul  2 11:42:01 dad-desktop udev-configure-printer: No serial number URI matches so using those without
Jul  2 11:42:01 dad-desktop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Jul  2 11:42:01 dad-desktop udev-configure-printer: URI of print queue: usb://EPSON/Stylus%20DX4000, normalized: epson stylus dx4000
Jul  2 11:42:01 dad-desktop udev-configure-printer: URI of detected printer: usb://EPSON/Stylus%20DX4000, normalized: epson stylus dx4000
Jul  2 11:42:01 dad-desktop udev-configure-printer: Queue ipp://localhost:631/printers/Stylus-DX4000 has matching device URI
Jul  2 11:42:03 dad-desktop AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/09b0778cbb3d4567a23e54ad01e58c38
Jul  2 11:47:40 dad-desktop AptDaemon: INFO: Quiting due to inactivity
Jul  2 11:47:40 dad-desktop AptDaemon: INFO: Shutdown was requested
Jul  2 11:47:40 dad-desktop AptDaemon: INFO: Initializing daemon
Jul  2 11:52:41 dad-desktop AptDaemon: INFO: Quiting due to inactivity
Jul  2 11:52:41 dad-desktop AptDaemon: INFO: Shutdown was requested
Jul  2 11:52:41 dad-desktop AptDaemon: INFO: Initializing daemon
Jul  2 11:57:42 dad-desktop AptDaemon: INFO: Quiting due to inactivity
Jul  2 11:57:42 dad-desktop AptDaemon: INFO: Shutdown was requested
Jul  2 12:00:17 dad-desktop cracklib: no dictionary update necessary.
Jul  2 12:00:28 dad-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="824" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```


from system>admin>log file viewer>messages```
Jul  2 11:38:56 dad-desktop kernel: [  237.728044] usb 2-1: new full speed USB device using uhci_hcd and address 3
Jul  2 11:38:56 dad-desktop kernel: [  237.906515] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 11:38:56 dad-desktop kernel: [  238.007612] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x082F
Jul  2 11:38:56 dad-desktop kernel: [  238.007680] usbcore: registered new interface driver usblp
Jul  2 11:41:58 dad-desktop kernel: [  419.303525] type=1505 audit(1278106918.194:5):  operation="profile_load" pid=1889 name="/usr/lib/cups/backend/cups-pdf"
Jul  2 11:41:58 dad-desktop kernel: [  419.305590] type=1505 audit(1278106918.198:6):  operation="profile_load" pid=1889 name="/usr/sbin/cupsd"
Jul  2 11:41:59 dad-desktop kernel: [  420.659816] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1

```

---

