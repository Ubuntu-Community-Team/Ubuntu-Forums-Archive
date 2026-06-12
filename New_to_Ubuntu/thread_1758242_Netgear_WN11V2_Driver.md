---
title: "Netgear WN11V2 Driver"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by lkzd on 2011-05-14
Does anyone have it? I searched and searched and each "Solution" I've tried says either that I dont have the hardware the driver is for or that it can't find the software I need.
I'm writing this from windows 7 because there is no other way for me to connect using Ubuntu because of where our router is. I have ndiswrapper etc, but just not the driver.
Help!

---

### Post by lkzd on 2011-05-14
Bump. Someone must know what to do, I really need it!

---

### Post by dcsoldschool53 on 2011-05-14
> **lkzd said:**
> Does anyone have it? I searched and searched and each "Solution" I've tried says either that I dont have the hardware the driver is for or that it can't find the software I need.
I'm writing this from windows 7 because there is no other way for me to connect using Ubuntu because of where our router is. I have ndiswrapper etc, but just not the driver.
Help!
Have you tried going to Netgear's website to download  the driver. [Netgear]("http://kb.netgear.com/app/")

---

### Post by lkzd on 2011-05-14
> **dcsoldschool53 said:**
> Have you tried going to Netgear's website to download  the driver. [Netgear]("http://kb.netgear.com/app/")

There is only a windows specific version, which didn't work with ndiswrapper.

---

### Post by NoNameWill on 2011-05-14
Ok you have a chipset that isn't native to linux. 

[http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)

So have you tried using different windows drivers ie xp

---

### Post by fabricator4 on 2011-05-14
> **lkzd said:**
> Does anyone have it? I searched and searched and each "Solution" I've tried says either that I dont have the hardware the driver is for or that it can't find the software I need.
I'm writing this from windows 7 because there is no other way for me to connect using Ubuntu because of where our router is. I have ndiswrapper etc, but just not the driver.
Help!

Firstly, try Googling for the product.  You seem to be confused about the actual model name - it's WN111V2.  Googling for this returns a lot of replies, mostly to do with verifying the chipset (with lsusb command) and going from there.  

Secondly, it's considered bad form to bump your own thread less than 24 hours after you post it.  A bit harsh, I know, if you're desperate for an answer.  Bumping 4 times in 5 hours might get you ignored by those might be able to help however.

Chris.

---

### Post by uRock on 2011-05-14
Please open the Ubuntu Software Center and install the Linux-Software-Nonfree package. You may have to restart for the system to start using your card.

---

### Post by lkzd on 2011-05-14
> **uRock said:**
> Please open the Ubuntu Software Center and install the Linux-Software-Nonfree package. You may have to restart for the system to start using your card.

The Ubuntu Software Center does not work. I have no Internet connection at all when booting into Ubuntu. My router is far away and ethernet would be basically impossible.

> **fabricator4 said:**
> Firstly, try Googling for the product.  You seem to be confused about the actual model name - it's WN111V2.  Googling for this returns a lot of replies, mostly to do with verifying the chipset (with lsusb command) and going from there.  

Chris.

Sorry, the WN11V2 was a typo. I have googled for the WN111V2 drivers many times, and I found some downloads on this forum for the .inf and .sys files, but they did not work.

I am just asking if anyone has a working download of the files I need, becuase I can't seem to find them.

---

### Post by uRock on 2011-05-14
> **lkzd said:**
> The Ubuntu Software Center does not work. I have no Internet connection at all when booting into Ubuntu. My router is far away and ethernet would be basically impossible.

How are you communicating?

---

### Post by lkzd on 2011-05-14
I am currently booting into Windows 7.
I have a dual boot set up.

---

### Post by uRock on 2011-05-14
You can download the package using this [link]("http://archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.9_all.deb"), then copy to thumb drive or whatever, then boot Ubuntu and install it.

---

### Post by zealibib slaughter on 2011-05-14
you can do a google search for the Linux-Software-Nonfree ubuntu package and download the deb, then transfer it to ubuntu and install it that way.
 
Looks like uRock beat me to it :)

---

### Post by uRock on 2011-05-14
To install it, just right-click and select to Open with Ubuntu Software Center.

---

### Post by lkzd on 2011-05-14
> **uRock said:**
> You can download the package using this [link]("http://archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.9_all.deb"), then copy to thumb drive or whatever, then boot Ubuntu and install it.

Yeah it's been a massive pain testing all the drivers out because everything has to go onto the USB, reboot, try it out, reboot, etc. 

I will install this now and then post the results in a few minutes.

Edit: So I have installed that, rebooted, and I'm not sure what to do now :s If the internet is supposed to connect now, it hasn't.

---

### Post by uRock on 2011-05-14
Was just looking at the [Ubuntu Wiki]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB") and found that the firmware [in this link]("http://wireless.kernel.org/en/users/Drivers/ar9170") is supposed to work for that chipset. 


If those do not work, then the only thing I can recommend is finding a different brand card. If this is a desktop machine, then you might want to check out the card that is linked in my signature. It was about $30 and works flawlessly. Asus NICs advertise Linux support.

---

### Post by lkzd on 2011-05-14
I'm sorry, I'm really new to Ubuntu.
What do I do with those .fw files I downloaded?

---

### Post by lkzd on 2011-05-15
Sorry to double post, but I'm not using a card, I'm using a USB WN11V2. Should have mentioned that, doh.

---

### Post by NoNameWill on 2011-05-15
If your card is is of the Atheros 9k type. Then this might work. [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

I used this on a netgear wna 1100 usb stick.

---

### Post by lkzd on 2011-05-17
> **NoNameWill said:**
> If your card is is of the Atheros 9k type. Then this might work. [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

I used this on a netgear wna 1100 usb stick.

I installed this and rebooted and nothing changed, doesn't seem to work for me :S

---

### Post by lkzd on 2011-05-21
Slightly less frequent bump

---

### Post by rikugo1 on 2011-05-21
I am having this problem as well. Please assist. I'm running 11.04. Before that I used Mint, with (supposedly) the same wireless driver, and it worked flawlessly. I've tried just about everything I've seen suggested in other forums.

---

