---
title: "Need help getting a PCTel Inc HSP MicroModem 56 working"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-14
Hello.  I've just installed Ubuntu on an older system that has a PCI modem in it that doesn't seem to be detected by wvdialconf right away.

According to the lspci output, the type of card is:

PCTel Inc HSP MicroModem 56

Anyone know how I can get this modem to work in Ubuntu?

---

### Post by anewguy on 2009-03-14
This is just one of many links returned when I do a search in Yahoo! using Ubuntu PCTel Inc HSP MicroModem 56 driver:

[http://www.newtnotes.com/item/2007/01/pctel-modem-on-linux]("http://www.newtnotes.com/item/2007/01/pctel-modem-on-linux")

The trick here is needing internet access to do it:

sudo apt-get install build-essential linux-source

then get the download of the driver from linmodem and follow their instructions.

Dave :)

---

### Post by diablo75 on 2009-03-15
Before you replied I managed to find this:

[http://ubuntuforums.org/showthread.php?t=368862](http://ubuntuforums.org/showthread.php?t=368862)

Basicly, you download the tar.gz from here:

[http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)

(The latest version they had was pctel-0.9.7-9-rht-10.tar.gz)

Extract the contents.

Then you open a terminal, become root for the session by typing sudo -s, then cd into the folder of the extracted tar, and type ./setup

And that was pretty much it.  The setup program was smart enough to detect the type of modem and install the correct drivers, and ubuntu then recognized the device as /dev/modem

Perfect!

---

