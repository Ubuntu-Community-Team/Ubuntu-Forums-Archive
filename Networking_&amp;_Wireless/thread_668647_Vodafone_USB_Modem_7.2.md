---
title: "Vodafone USB Modem 7.2"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by fieldyweb on 2008-01-15
I'm putting this out there, before i nip down to the vodafone shop in oxford street.

[Vodafone]("http://www.vodafonebusinessshop.co.uk/index.cfm?fuseaction=MobileEmailAndData.UsbModem72&WT_ref=EBU_DEST_WOR_VSUSB") are offering a 3G USB Modem 7.2 can connect with speeds of up to 7.2Mbps.for £25, however a quick check of the web/goodle with the words "USB Modem 7.2 linux"  and a [fair few sites]("http://www.pocket-lint.co.uk/reviews/review.phtml/2741/3765/vodafone-mobile-broadband-usb-modem.phtml") return back that low and behold the device has LINUX drivers

> Once connected and the software is installed, it works with Windows, Mac and even Linux, the idea is that you then have the Internet in your bag where ever you are as long as you can get mobile phone coverage.

My question is simple really, has anyone out there got one of these working under Ubuntu? or any form of Linux? If so was it simple? and does this work?

If it does, i'd be happy to spend the £25 a month for 2 reasons

1) This is a good deal for mobile broadband, as i live in London
2) I'd happily support Vodafone for the support of Linux

---

### Post by ChasB on 2008-01-16
For 7.10 I use the Vodafone Linux Driver.... if this is the 7.2 version of the E220 (but looks different in the pic). If not they will have support soon, and you can email the developers. They also have** a list of the supported modems **on the Vodafone Linux web pages
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/]("https://forge.vodafonebetavine.net/projects/vodafonemobilec/")

See the thread also on:
[http://ubuntuforums.org/showthread.php?t=262867&highlight=e220&page=11 thread]("http://ubuntuforums.org/showthread.php?t=262867&highlight=e220&page=11 thread")
And it will work with other networks if it unlocked...
Cheers
ChasB

---

### Post by fatality_uk on 2008-02-20
According to our telecoms supplier, this should work with Linux (Ubuntu/Debian) out the box. I have ordered one on sale or return. Should be here within 48 hours so will let you know the result. Unless someone as one and can tell me if it all works ok?

---

### Post by fatality_uk on 2008-03-13
This modem works very well under Linux/Ubuntu. In 3G areas the speed is very good 2Mb+ p/s

---

### Post by pjhartt on 2008-03-13
I would be very interested in what modem you are using. I have the Vodafone E172 and it does not work on Ubuntu desktop.

I have only just started using Linux and this is the stumbling block. If you know where I can get drivers PLEASSSSE let me know.

If I get it working I will dump Windows Vista.

Peter

---

### Post by zobojoe on 2008-03-13
Hello Peter,

Go to ...

[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)

There are number of ways of installing the application however I recommend downloading the latest .run file and opening a terminal. Then...

cd to the directory in which you downloaded the .run file and

sudo ./<filename.run>

The application will then install

I use 7.10 and I set up my E172 very easily and the performance is excellent

Let me know how you get on.....

---

### Post by fieldyweb on 2008-03-17
OK, this is all good stuff, the next question however, is 64Bit Ubuntu 7.10..
I can't seem to get the Drivers to work on this at all. anyone had any success?

---

### Post by mips on 2008-03-17
> **fieldyweb said:**
> OK, this is all good stuff, the next question however, is 64Bit Ubuntu 7.10..
I can't seem to get the Drivers to work on this at all. anyone had any success?

Not sure but you might have to compile them from scratch.

---

### Post by fieldyweb on 2008-04-10
Well i got lucky, and got one of the Vodafone 7.2 Modems at work, and the drivers from Betavine (deb) work out of the box, straight away, no problems on i386 version, however the 64bit version of ubuntu 7.10 keeps getting an Elf error, which according to other posts might be a pain to fix..

however as of 10/04/2008 I can tell you that all of Vodafones currently for sale modems work on Ubuntu 7.10 i386

---

### Post by fieldyweb on 2008-04-21
Just a quick update, i've just retried the same drivers as above on Hardy 8.04 RC1 64bit and it works!

---

### Post by mips on 2008-04-21
Thats good news for others!

---

### Post by pseudo-random on 2008-05-01
FYI I've got the HUAWEI E272 model working with pon on vodafone. The Vodafone-mobile-connect software wouldn't connect with it (but works fine with my e220) so I used pon. 
Tut is here [http://wintolin.co.uk/content.php?c=tuts/e272](http://wintolin.co.uk/content.php?c=tuts/e272)

---

### Post by MattBD on 2008-05-25
I can confirm that I got the Vodafone Huawei E620 PCMCIA card working in Gutsy, using Vodafone's mobile connect card driver. However, the coverage is very poor where I live in Norfolk and the speed was rubbish so I wound up taking it back.

---

### Post by scorp123 on 2008-05-25
> **fieldyweb said:**
>  My question is simple really, has anyone out there got one of these working under Ubuntu? or any form of Linux? If so was it simple? and does this work? Please see here ... I think that Vodafone modem you got might be a re-branded Novatel Ovation MC950D ... and those just happen to work tip top on Linux :)

[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)

---

