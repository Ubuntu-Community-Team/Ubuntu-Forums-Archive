---
title: "Can't get on internet with USB modem"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2006-08-21
Can someone tell me how to install and use a SAGEM fast 800 E2L USB ADSL modem (or similar). I think I got the drivers/modules installed, but I don't know where to go from here, and can't find any wizard-style installers for net connections in Ubuntu.

---

### Post by dwarner30uk on 2006-08-21
Me too ! I've got ubuntu 6.06 installed on a partition, and I can dual-boot into XP or ubuntu. The Speedtouch 330 broadband modem is connected to USB port, and of course windows has got it installed.
I have got the install disc for speedtouch,but I don't know how to load that into linux. Please don't flame me if this subject is well known,just gently lead me into the paths of internet happiness.:confused:

---

### Post by norfred on 2006-08-21
That is my problem too. I have tried to get on the internet using 4 different distributions now and no go. The only advice so far has been to change to an ethernet modem. If ubuntu doesn't work I think it is time to call it a day.
norfred

---

### Post by crispy_420 on 2006-08-21
Try this link on google:

[Linux kernel driver for SpeedTouch USB modems]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

That was for the speed touch. Now for Sagem:

[eagle-usb driver for GNU/Linux]("http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport")

Just something I found online, I don't have this modem myself but post back your results to help others with this problem.

---

### Post by pickarooney on 2006-08-22
> **crispy_420 said:**
> Try this link on google:

[Linux kernel driver for SpeedTouch USB modems]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

That was for the speed touch. Now for Sagem:

[eagle-usb driver for GNU/Linux]("http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport")

Just something I found online, I don't have this modem myself but post back your results to help others with this problem.

Can you tell me what to do once I have the drivers installed? They're included on the Dapper CD, as far as I know, and I got them to show in lsmod using modprobe, but I've no ide what to do next.

---

### Post by divali on 2006-08-22
I was issued with a Sagem modem by tiscali and it was only after many hours of driver configuration and helpful advice from the eagleusb forum that I was finally able to get my fedora4 working on the net, and even then I would have to reset the settings after shutting down and starting up again.

My advice to you is **use an ethernet modem**.

 It will save you lots of headache and frustration. USB was developed by our friends over at Microsoft and it is very difficult for Linux to keep writing drivers for every damn fool usb device available, from modems to desktop goldfish tanks!

---

### Post by aces21 on 2006-08-22
I wrote a howto for getting the Sagem Fast 800 USB modem working with Dapper. You can find it [here.]("http://www.ubuntuforums.org/showthread.php?t=201127")

---

### Post by pickarooney on 2006-08-22
> **aces21 said:**
> I wrote a howto for getting the Sagem Fast 800 USB modem working with Dapper. You can find it [here.]("http://www.ubuntuforums.org/showthread.php?t=201127")

Obvious question - how am I supposed to apt-get anything if I don't have a working internet connection? :confused:

---

### Post by crispy_420 on 2006-08-23
Like others have said and I hate to be the one to advise spending more money, get an ethernet modem. It will save many a problems in the future. Imagine you decide to try another distro and have to do this all over again, assuming you get it up and running.

Do you want to spend more time messing around or do you want to be up and running? If it was me, I would spend the extra money and get an ethernet modem. Then you have the future of expanding your network too, think wireless and multiple computers sharing a network.

---

### Post by aces21 on 2006-08-23
> **pickarooney said:**
> Obvious question - how am I supposed to apt-get anything if I don't have a working internet connection? :confused:

Good point. You can apt-get the stuff you need from the install CD,  assuming you have one. I think this should be setup already and if not, you can do it via the synaptic pacakge manager. If you need help with this, just ask. For the ueagle stuff, you'll have to download it via some other method then copy it onto dapper via floppy, usb-stick or something.

---

### Post by MRND on 2006-09-08
there's an easy way to get the speedtouch usb 330 modem working, just follow the instructions given in this [link]("http://steve-parker.org/speedtouchconf/") anf you should be connected in minutes.

---

### Post by _chAos_ on 2006-09-19
> **MRND said:**
> there's an easy way to get the speedtouch usb 330 modem working, just follow the instructions given in this [link]("http://steve-parker.org/speedtouchconf/") anf you should be connected in minutes.

The script will complain about missing packages (gcclib and make i think, it is in the speedtouchconf faq).

So you will have to install these from the ubuntu cd. And i think it works like this:
apt-cdrom add
apt-get install ... 

My modem works perfectly in ubuntu (installed with the script), however it doesn't work in windows after it is used in ubuntu :). If i find a solution to that i'll post it.

---

### Post by Cryhavoc on 2006-09-19
How come my cd-rom thinga doesn't actually point to one of my cd drives? Both the drives are mounted under media, and I can't figure out how to assign one to the cd-rom link tpe thing?

---

