---
title: "CDMA phone with Usb Adapter"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by mimoh_mi on 2006-09-27
[I][SIZE="4"]
Pls can somebody help me out. I have an LG CDMA phone.
I been trying to connect my Ubuntu system to the net with this phone.The phone has a serial port but my laptop (AMD) doesn't a serial adapter. So I had to get a usb serial adapter.
My system was able to identify the adapter, and attached
it to ttyUSB0, i have tried to use wvdialconf and wvdial to
setup the connection, the modem was deteched by wvdialconf.
Have also tried the network GUI utility tool to setup the connection, it just blink modem on the phone and cut.
Pls am waiting, just want to get it up and running fast.
Thanks
[/SIZE][/I]

---

### Post by mimoh_mi on 2006-09-30
[I][B]Hey, after sleepless night, i finally fixed myself up.
ok, it wasn't an easy task but the solution was just simple.
Ubuntu supports hot plugin for usb devices, so just plugin
the USB adapter to my laptop.Then kill all the tty stuff, the system
will just restart. The usb adapter should now be detected.
Do a dmesg command, look through, see things like usb core, serial adapter
and co. The most important thing is to check the port that has
been assigned to the adapter.(like ttyUSB0), that's the modem port.
Then do the wvdialconf stuff, if it doesn't detect the modem
just keep running the command until it done. then run the wvdial
stuff, all this is just to make sure the modem is deteched
by the system. Look at the phone, you should see modem data on
the display.OK, now run the pppconfig and follow the instructions.
and finally do pon command, hulala you are up...8)  [/B][/I]

---

### Post by imranmalik on 2006-10-11
hi "mimoh_mi";
i tried to follow ur steps to up my CDMA modem but i could not get all into ur details caz i m new to linux. i could not understand how can i kill "ALL THE tty STUF". i could not find mt ttyUSB0 port. i also checked the device manager and tried to locate the CDMA Device (i m using huewei phone set and it works fine in XP). so kidly can u do a favor and write the details again ??????????????

---

