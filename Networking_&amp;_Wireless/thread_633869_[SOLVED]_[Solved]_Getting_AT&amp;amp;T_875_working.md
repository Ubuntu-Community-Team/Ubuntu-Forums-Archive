---
title: "[SOLVED] [Solved] Getting AT&amp;amp;T 875 working"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by sidcypher on 2007-12-07
I have been wanting to get my aircard working prior to actual install, seeing how I do not wish to dual boot vista. Not having internet wasn't a option since I am a truck driver this aircard is all I have 90% of the time.

After following EVERY tutorial I could find (printing out then booting live cd). I finally got it working without having a internet connection to be able to install software.

I DO NOT know if it will make a difference if you have never connected with card under windows, have read it will. So since I HAVE, I assume you need to. So make sure you have used the card on a windows install prior to trying this.

BTW I am pretty much a Linux newbie, and this will follow a newbie style.

First pull up a terminal window 
```
  # dmesg
```
verfiy modem was listed
scroll through and find something that looks like this
```
[  107.668000] sierra 6-1:1.0: Sierra USB modem (3 port) converter detected
[  107.668000] usb 6-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[  107.672000] usb 6-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[  107.672000] usb 6-1: Sierra USB modem (3 port) converter now attached to ttyUSB2
[  107.672000] usbcore: registered new interface driver sierra
[  107.672000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.0.6
```

now exit the terminal window, this is where tutorial goes WAY newbie (my mom could follow)

System > Adminstration > Network
select Modem then Properties

Check "Enable Connection"
Phone Number: *99***1#

Username: [email]wap@cingulargprs.com[/email]
Password: cingular1   (all lowercase)

Modem Tab
Modem Port: /dev/ttyUSB0

Options Tab
Check all three

Now since it worked on mine, I assume it worked on yours.
After acouple seconds your orange connection light should turn blue and you are ready to rock and roll.

At the time of this post I have 2g connection NOT 3g, do not know if it will work there...
Also at the Time of this post I am using the Live CD, NOT a install.

Just a simple quick online if using the live CD.

*edit
I am now officially installed and running from hard drive. So this method works for me on Gutsy!
Now completely solved....not just Live solved....

l8r
Cypher

---

### Post by capsid on 2008-01-14
I'm glad you got it worked out!  How did you determine your username and password?  I have service with AT&T, but when I asked them for that info they said they had no idea.  I checked the Connection Profile on the Windows side but there was no information in the username and password fields.  I'm using an 881U.

---

### Post by sidcypher on 2008-01-14
I was reading tutorials somewhere..maybe somewhere on here..and it had it listed...Cause I asked ATT and they had no idea either...


Does yours work with this method? I was thinking about upgrading cards later this year.

---

