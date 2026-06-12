---
title: "huawei E220 - more issues."
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by Jitsun on 2008-08-04
This is the third day in my struggle to get my 3 Australia Wireless Broadband USB Modem working with Ubuntu hardy Heron.

Day one; eventually got it to connect flawlessly and then called it a night.

Day two; ttyUSB0 not found... retraced steps and eventually (by some fluke) got it to connect again. Cannot leave it connected ALL the time so I decided to pull the modem out, reinsert it and attempt to reconnect - No good, ttyUSB0 not found.

Day three (today) still trawling websites looking for info and still no connection. I'm using a WinVis pc connected via wireless so i cannot apt-get install gnome ppp (or whatever.. or anything els!) so i'm stuck with manually configuring my Ubuntu box.

So here's where i'm at, lsusb = usb modem recognized as Bus 001 Deice 003

wvdialconf = Sorry no modem was detected! Is it in use by another program? Did you configure it properly with Setserial?

I've done the modprobe -r usbserial and get
FATAL: Module usbserial is in use

Automount, is turned on but the modem does not mount so there is nothing to eject.

modprobe usbserial vendor=0x12d1 product=0x1003
doesn't seem to 'do' anything.

here's my /etc/wvdial.conf - fairly certain it's correct as i've connected to the net with it twice already.

[Dialer justin]
Init2 = ATZ
Init3 = ATQ V1 E1 SO=0 $C1 &D2 +FCLASS=0
Stupid mode = 1
modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = ''
Password = ''
Dial Command = ATDT
Baud = 466600
Init = AT+CGDCONT=1,"IP","3netaccess"

.. If i modrpobe -r airprime and then modprobe usbserial vendor=0x12d1 product=0x1003... ttyUSb0 is then recognised however when i do a wvdalconf or wvdial justin i get;
"Cannot get information from serial port"

Any help is greatly appreciated. I've trawled the forums and i did manage to get ths thing working twice and yeah, I cannot download any GUI's as i do not have net access without wireless :D

Cheers,

J.

---

### Post by GeorgeVita on 2008-08-05
Hi,

your wvdial.conf seems ok, but it is more typical to place at least a letter on user and password instead of double quotes. Double quotes tells to the modem that something follows and then CR+LF auto-correct etc. Not very good practice.

I propose to minor-fix the wvdial.conf, remove the E220 and also any other modem (in case of conflict), reboot, open a terminal window, use the double cable to connect the E220 (if it comes with the modem), try the lsusb at the terminal and when you see the Huawei in the list, just:
sudo wvdial justin

In any problem, copy paste here the text results from the terminal window.

---

### Post by Jitsun on 2008-08-05
Hi GeorgeVita an thanks for your reply.

I now have username = username and password = password.

As per your instructions i rebooted machine, connected e220 and lsusb'd and then ran sudo wvdial justin

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

It sees to be the same problem a lot of others have had. (USB modem is being recognised as a storage device???)as soon as i can get the computer connected i'll be able to apt get install gnome ppp and problem solved (according to other posts).

Any other suggestions greatly appreciated.

J

---

### Post by sqasl1! on 2008-08-05
Hi there

Got the same problem, I suspect, and posted a new thread here [http://ubuntuforums.org/showthread.php?t=880650]("http://ubuntuforums.org/showthread.php?t=880650")

Does this sound like something that could have happened in your case?

---

### Post by Sealbhach on 2008-08-05
Try 

```
sudo wvdialconf
```

after booting up with the modem attached.

That should detect it.

.

---

### Post by Jitsun on 2008-08-05
> **Sealbhach said:**
> Try 

```
sudo wvdialconf
```

after booting up with the modem attached.

That should detect it.

.

Thanks mate but not detected...

Sorry no modem was detected! Is it in use by another program? Did you configure it properly with Setserial?

---

### Post by Jitsun on 2008-08-06
hate to bump but i'm that desperate to get my laptop online that i'm reaching for the windows system restore cd and about to give ubuntu the flick for another 12 months... so.... bump!

Anyone able to help me with the missing ttyUSB0??? greatly appreciated,

J

---

### Post by GeorgeVita on 2008-08-06
Hi, let's conclude briefly. You have Ubuntu 8.04, the E220 modem, a good wvdial.conf, the lsusb command lists your modem but after issuing the wvdial justin command the modem is not there (at the usb or the ttyUSB0).

Can you try the following simple but possibly long test?

Disconnect E220, reboot, open a terminal window, lsusb, insert E220 to the USB port, lsusb again (you can do this faster by pressing up arrow and ENTER at the terminal prompt), lsusb, ... till it shows the "Huawei..." on the list, then lsusb, lsusb some times (every 5-10 secs) WITH NO OTHER program running.  If the modem exists on the list try again after 1 or 2 minutes (lsusb, lsusb). Stop when tired or IF disappears!  If disappears, lsusb after 10-15 secs to see if connected again.
This test will show if the modem is disconnected by itself (H/W reason).

Also if Sealbhach (or any other) can answer:
Ubuntu 8.04 is polling the USB ports automatically (timed ?) or searches (polls) after a new command or application-task runs?
This will determine if the modem can appear-disappear by a S/W reason.

Regards

---

### Post by Sealbhach on 2008-08-07
Try these commands:

```

sudo rmmod option
sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```

The try sudo wvdialconf



.

---

### Post by sqasl1! on 2008-08-08
Hi

Had exact same problem as you, and managed to get things working.  For now at least - we'll see how stable it is.

Check [my post]("http://ubuntuforums.org/showthread.php?p=5546813#post5546813") and see if the same works for you.  I realise that to do this you need an internet connection, but perhaps you can download the packages somewhere else (at work?), copy them to your disk and install from there.  I don't know how to do this, but I'm sure there are plenty of bright people out there who do know how ;-)

Anyways, let me know if you have any success.

---

