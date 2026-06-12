---
title: "Printer is connected to home internet but do i still need drivers to use it?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-12-15
the printer is a lexmark x4650, i know lexmark and ubuntu don't get on, but my network shows the printer and ubuntu see's it as a printer, has anyone been able to actually install the drivers for this printer by using the windows drivers? not sure if that's actually possible. I am really only looking to scan, i have a laser printer that works out of the box with ubuntu but i really need to use the scanner on the lexmark for various college projects.

---

### Post by Gordonbp531 on 2010-12-16
Lexmark and Linux DO get on! (It depends on the printer - my C540N was recognised and installed by Ubuntu perfectly!)
Try this for a deb driver for your printer:
[http://support.lexmark.com/index?productCode=LEXMARK_X4650&segment=DOWNLOAD&os=UBUNTU_9.10&oslocale=en_US&page=content&actp=DD_LIST&id=DR20523&locale=en&userlocale=EN_UK](http://support.lexmark.com/index?productCode=LEXMARK_X4650&segment=DOWNLOAD&os=UBUNTU_9.10&oslocale=en_US&page=content&actp=DD_LIST&id=DR20523&locale=en&userlocale=EN_UK)

---

### Post by Rave Gloves on 2010-12-16
Ive been trying this just now and it keeps telling my my root password is wrong, when it's clearly not :/

---

### Post by Rave Gloves on 2010-12-16
Other people have been having this problem i was told to run this
```
andrew@andrew-R610:~$ sudo sh lexmark-08z-series-driver-1.0-1.i386.deb.sh
sh: Can't open lexmark-08z-series-driver-1.0-1.i386.deb.sh

```

which as you can see didn't work, apparently your normal password doesn't work as you need to root password, by default is not put in.

---

### Post by Rave Gloves on 2010-12-16
Right i did this:


Right Click the Archive ---> Extract Here

It should extract it to a file called lexmark-08z-series-driver-1.0-1.i386.deb.sh

Copy this file to your desktop.

Then, open up Terminal ( Applications -> Accessories -> Terminal )

type "cd Desktop" (without quotation marks)

it should change the current directory to the Desktop ( Should look something like this: jaime@jaime-laptop-linux:~/Desktop$ )

Then type "./lexmark-08z-series-driver-1.0-1.i386.deb.sh"

Then follow the setup prompt that follows. 

If you get the password error then:

instead of typing "./lexmark-08z-series-driver-1.0-1.i386.deb.sh"

try typing "sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh" or "sudo lexmark-08z-series-driver-1.0-1.i386.deb.sh"

The terminal will prompt you for your password, enter it.

But when the install asks me to plug my printer in, i do and nothing happens. Im not notified that it's pluged in and when i click next it just tells me to plug it in, some people have said you can connect it wirelessly but i am not able to find my printers ip address.

---

