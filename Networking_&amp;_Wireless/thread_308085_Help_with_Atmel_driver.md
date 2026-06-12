---
title: "Help with Atmel driver"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by cawill on 2006-11-27
Hi, i am fairly new to Linux and need to get connected to my wireless network.

I have Ubuntu 6.10 and have a BT voyager 1010 usb wireless adaptor which i think has a ATMEL AT76C503A chipset.

I typed apt-get install at76c503a-source atmel-firmware into the terminal using a working eth0 link and everything seemed to work fine but i don't no what to do from now on.

Can someone please tell me how to get the driver working so i can use my wifi adaptor?

Thanks in advance.

Chris

---

### Post by FrodoB on 2006-11-27
Well if you have 6.06 or 6.10 the atmel usb devices just work as soon a you plug them in.  If you do an

$ iwconfig 

at a terminal prompt you should see a device called wlan0 and that is your wireless device.

Just go to System -> Administration -> Networking and configure it and go.

Oh, these devices do not like to to unplugged, at least mine does not.

---

### Post by aka47 on 2006-12-19
Sorry chris

But I have got to contradict you, iwconfig on my OQO does'nt show any wireless interfaces (and the 505a is definitely built in)

Module Assistant fails to build the source and install the module.

It actualy fails at the build phase with unable to open debian/changelog.

I checked the /usr/src etc etc and found that the file does'nt exist only a changelog.template

When I cp'd this template file to changelog the m-a build failed claiming that there was a syntax problem at line 1.

Can anyone offer any asistance with this ???

Is it a bug or package omision maybe ?? :confused: 

Cheers
aka47

PS I have tried reinstalling headers, module assistant, atmel source and all the usuals. The listed dependancies are all installed

---

### Post by aka47 on 2006-12-19
Sorry chris it's not you i am contradicting it's frodoB.

(PS I am happy to be proved wrong about this.....):KS 

Cheers aka47

---

