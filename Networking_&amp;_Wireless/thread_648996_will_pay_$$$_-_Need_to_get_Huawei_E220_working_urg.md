---
title: "will pay $$$ - Need to get Huawei E220 working urgently!"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by Persiancoffee on 2007-12-24
Hi guys,

Im not a ubuntu newbie to be honest, but for the past few weeks, i have spent about 2 to 3 hours every day trying to get my mobile broadband working. Its a usb modem supplied by Three UK. It works fine on Vista, just not on linux. Im just sick of trying to tackle it, i refuse to waste my life anymore. Needless to say this is exactly why i will never switch to linux as a desktop OS, because there simply arent enough drivers/apps for linux as a general purpose OS.

In any case, I do web development, which works much better on a LAMP stack. As such, i REALLY need to get this thing working. I have probably read every single tutorial on the net, so im not really looking for more links. I want to pay someone to get it working for me. Ill call you, you can tell me what to do. Im located in the UK, but i can call any country, no problem. Also, cost is not an issue, name ur price, i just want it fixed!

If you have done this before, please send me a PM with your phone number and a suitable time to call... note: i can only call during working hours GMT.

TIA

---

### Post by wieman01 on 2007-12-24
I see you are in a state of distress, but let's not overreact. I think there is a way to tackle it without long-distance calls.

First of all, what sort of modem are we talking about, what brand is it and what do you need it for? Does Vista come with a driver or do you have to install the modem separately?

Please post:
> sudo lsusb

_**EDIT:**_
Besides, you should have posted way earlier, support in here is for free.

---

### Post by tuggy on 2007-12-24
isnt this the one that comes with vodafone mobile connect box?
if it is, it is supported out of the box. i have friends who have the vodafone connection, and there is a software from vodafone to manage the connection using this modem.

---

### Post by Persiancoffee on 2007-12-24
There is no point in me posting earlier. I am in the same position as many many other people, you can do a search for "Huawei E220" and you will see how many different threads there are. I have already read/tried them all.

My modem is from Huchinson 3G UK (AKA three.co.uk)

They provide Windows and Mac drivers... but nothing for linux

---

### Post by bapoumba on 2007-12-24
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)
Looks like it worked for some users.

---

### Post by wieman01 on 2007-12-24
> **Persiancoffee said:**
> There is no point in me posting earlier. I am in the same position as many many other people, you can do a search for "Huawei E220" and you will see how many different threads there are. I have already read/tried them all.

My modem is from Huchinson 3G UK (AKA three.co.uk)

They provide Windows and Mac drivers... but nothing for linux
Ok, got it.

What does this yield after you have plugged in the device:
> sudo lsusb

---

### Post by Persiancoffee on 2007-12-24
Prior to modem being plugged in... lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

After modem is plugged in... lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 12d1:1003  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I think the modem is working, because it changes from flashing green to flashing blue (which is also what it does with vista. After it starts flashing blue, i can hit 'connect' in vista, and it will connect). 
i think i just dont have the correct settings in wvdial, but i have no idea where to get the settings for Three UK.

My current wvdial.conf settings:

[Dialer Defaults]

Modem = /dev/ttyUSB0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99#
Username = ppp
Password = ppp
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Idle Seconds = 0
ISDN = 0
Auto DNS = 1

When i try to dial, i get the following:

m@m$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Ive tried many different wvdial.conf settings, but I havent found anything that is actually for Three UK.

---

### Post by wieman01 on 2007-12-25
One more try, after the modem is plugged in, what does this say:
> dmesg
Have you asked 3 UK for the correct WVDial settings? What's their response?

---

