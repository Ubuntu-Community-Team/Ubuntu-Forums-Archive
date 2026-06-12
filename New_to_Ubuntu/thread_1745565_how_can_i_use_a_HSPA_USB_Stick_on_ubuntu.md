---
title: "how can i use a HSPA USB Stick on ubuntu"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by shaquille110 on 2011-05-01
Hi,

i am currently wishing to discontinue using my current ISP. I wish to move to Vodafone AU, i have purchased a Huawei HSPA USB Stick.

The software it runs is for windows and Mac OSX. How can i get this device to run on ubuntu?

AKA, it is a USB 3G wireless modem. 

I am using ubuntu 10.04 Lucid LTS

---

### Post by turbodin on 2011-05-01
[http://www.muktware.com/man/1063](http://www.muktware.com/man/1063). ...i think you can check this website out on how to use u r 3g modem ...hope this helps

---

### Post by shaquille110 on 2011-05-01
Ubuntu isn't detecting the usb device for some reason, i click the networking logo on the top right hand corner of my screen and there is nothing related to the mobile device, only my wired Ethernet connnection

---

### Post by gandaran on 2011-05-01
> I am using ubuntu 10.04 Lucid LTS
you need to install the usb-modeswitch and usb-modeswitch data packages or upgrade to the new ubuntu version.
connect to cable internet to install them from the package manager or if you cant get them [here]("http://packages.ubuntu.com/lucid/")

---

### Post by 3rdalbum on 2011-05-01
> **shaquille110 said:**
> Ubuntu isn't detecting the usb device for some reason, i click the networking logo on the top right hand corner of my screen and there is nothing related to the mobile device, only my wired Ethernet connnection

No, there won't be until you actually tell Network Manager to set it up. Go to the network manager as you have done, and go to Edit Connections...

Then click on the Mobile Broadband tab and click Add, and follow the prompts to set it up assuming the stick is supported in Ubuntu 10.04.

Just to let you know, mobile broadband is a bit unreliable. Unfortunately, Vodafone's network in Australia is not the best; I couldn't get any better than a 2G signal where I live on my Three broadband stick, and my friend also had signal strength troubles on Three.

However, I could get a reasonable signal and HSDPA speeds where I used to work - so your milage may vary. Lots of fun keeping the torrent client open on my netbook in the lunch room while working :-)

---

### Post by ieee488 on 2011-05-01
> **shaquille110 said:**
> Hi,

i am currently wishing to discontinue using my current ISP. I wish to move to Vodafone AU, i have purchased a Huawei HSPA USB Stick.

The software it runs is for windows and Mac OSX. How can i get this device to run on ubuntu?

AKA, it is a USB 3G wireless modem. 

I am using ubuntu 10.04 Lucid LTS

Depends on which model of Huawei stick you have.
I have a UMG 181.
In Ubuntu 10.04, I use Gnome PPP and works just fine.
Ubuntu 10.10 did a better job of detecting it.

---

