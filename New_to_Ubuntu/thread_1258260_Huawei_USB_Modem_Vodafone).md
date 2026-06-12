---
title: "Huawei USB Modem Vodafone)"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by CrisPedreira on 2009-09-04
Ubuntu came installed with my new netbook and I never gave a thought to the fact that my Vodafone USB Huawei modem (9.3.6.12095) would be incompatible.  I was told that I need a program or software code pack to run the modem on my system.  Does anyone know where I can get the information.  Vodafone (Spain) does not support Linux software).
 
Appreciate any help you can give!
:popcorn:

---

### Post by RabbitWho on 2009-09-04
I have another Huawei dongle, model E160G, and that works fine with Ubuntu, see if Vodafone use that? 

There is probably a list of compatible devices somewhere, I'm sure vodaphone will replace the modem if it doesn't work for you free of charge. 3 had to do it for us when the first dongle they gave us wouldn't work with mac.

---

### Post by CrisPedreira on 2009-09-04
I´m afraid Vodafone is not about to replace anything here in Spain!  They simply do not support the Linux software and leave it up to the client to figure it out.

---

### Post by Rhubarb on 2009-09-04
What version of Ubuntu are you running there?
What model huawei dongle do you have?

I've found that it's very easy to get these huawei 3G USB dongles work fine and easily with Ubuntu 8.10 and onwards.

There's no need to download a software pack or program to do this, as it's built in to Ubuntu's network manager (where you can configure it).

In previous versions of Ubuntu it's possible to get it working with KPPP (a dial-up modem app).

The Huawei 3G USB dongle presents itself as a regular dial-up modem usually something similar to /dev/ttyUSB0 - which is just a serial port.

Most wireless broadband companies / Telcos don't support linux, but it doesn't mean their products / services don't work in Linux - often it's quite the contrary.

---

### Post by CrisPedreira on 2009-09-05
I have Ubunto 8.04 (Hardy Heron) released April 2008.  It does come with a pre-configured connection for Vodafone but, after inputting the PIN/PUK (with help of Vodafone Technical Dept.) they indicated that the modem should work with that basic information.  However, the connection does not work "automatically".  There must be something that I must do to make a manual connection to the internet but I don´t seem to get it right.
 
If anyone can help with this, it will be much appreciated.  I´ll keep searching in the meantime to see if others had the same problem and found a viable solution.

---

### Post by shuttleworthwannabe on 2009-09-05
suggestion: if it is feasible, would upgrading to jaunty help? it works on this release of Ubuntu. I have H E220 and works fine (plug n play). otherwise there is a HOWTO [here]("http://ubuntuforums.org/showthread.php?p=3654996")

---

