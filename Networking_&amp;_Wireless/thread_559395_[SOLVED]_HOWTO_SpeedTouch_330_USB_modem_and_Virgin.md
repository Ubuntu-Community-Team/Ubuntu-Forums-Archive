---
title: "[SOLVED] HOWTO SpeedTouch 330 USB modem and Virgin under UBUNTU in the UK"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by matogrosso on 2007-09-25
HOWTO SpeedTouch 330 USB modem and Virgin under UBUNTU in the UK.

If you've signed for the cheapest broadband plan with Virgin in the UK and got the free USB modem that comes with it, then this post is for you.

Please read the SpeedTouch_linux_Guide.htm file. Nearly all files you need to get your modem working are attached to this thread. I could not attach all of them because there are restrictions regarding the number of files attached to a thread and also to their extensions. I've made them all .txt before uploading them here. All you need is to follow the instructions in the SpeedTouch_linux_Guide file and change the user id and password when necessary in the files named secrets, dial and speedtch. PLEASE remove the .txt extension from all files here attached. 

These forums below are here for your reference. I used them to get my USB modem working. Now I am attaching my own configuration files to make your life easier.

PLEASE PLEASE PLEASE remove the .txt extension from all files here attached. You still need to go to these forums and get the SpeedTouch330_fimware file and the firmware-extractor. Please follow the instructions in the SpeedTouch_linux_Guide.htm file.

Original post:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

And this one:
[http://forums.hexus.net/showthread.php?t=97337](http://forums.hexus.net/showthread.php?t=97337)

Official Ubuntu:
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

---

### Post by dmacdonald111 on 2007-09-26
matogrosso, thank you for these instructions! I changed over to virgin broadband today and when I couldn't connect to the internet, I was just about to scream, but after a little hunting, I found your how to steps here and I followed them and they worked first time!

I would just like to add, it would seem that the version 4.0 is the current standard for firmware and would I would tend to ignore anything before that if you have a new speedtouch330 from virgin.

Rock on matogrosso :guitar:

After a new install, I found that I couldn't connect using your instructions. I don't know what went wrong the second time, but I used the usbadslmodemmanager deb package and this worked perfectly!

---

### Post by matogrosso on 2007-10-01
Dmacdonald111,

I am glad to help. usbadslmodemmanager seems to be a far more comprehensive and elegant solution. But I am lazy and yes, sometimes my connection fails when I start up the computer. All that I need in this case is to run the "dial" file manually:

> cd
> sudo ./dial

Cheers,
Matogrosso

---

