---
title: "ubuntu doesnt detect my dongle!!!"
date: 2016-12-21
forum: Networking &amp; Wireless
---

### Post by danielwoods21 on 2016-12-21
hi everyone i have installed ubuntu on a 16 gig flash memory and it works well.when i connect my 3g modem 
to my laptop in windows 7 my laptop automatically detects modem but when i switch from windows to ubuntu 
and try modem nothing happens my laptop doesnt even detect the modem.i have tested isusb command in ubuntu.
but it doesnt show my modem driver.please help me i cant connect to internet in linux

---

### Post by RobGoss on 2016-12-21
Hello and welcome, I know you stated you have installed Ubuntu on a **16-GB** flash drive but are you trying to install Ubuntu on your machine / computer?

If the answer is yes, try booting up to the live desktop and try connecting to the internet using a wired connection then you will be able to install the appropriate drivers using **software & update, **then choose **additional drivers, **you should be good to go

It's also recommended to post the** specs **for your machine in order to get the help you need. You will also need to provide which version of Ubuntu you're are using because they have a few different distributions

I'm assuming you're trying to connect to a Wifi access point

---

### Post by SeijiSensei on 2016-12-21
Ask the modem manufacturer if they support Linux.

---

### Post by wildmanne39 on 2016-12-21
The command to see if a device is connected through the usb port is not isusb it is:
```
lsusb
```
please post the results here using code tags.
Thanks

---

