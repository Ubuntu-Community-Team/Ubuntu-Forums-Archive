---
title: "T-Mobile Dongle Set-up on Ubuntu"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by JVV on 2010-11-23
Hello, 

I'm a very recent convert to Ubuntu after my windows computer crashed. Yesterday I bought a T-Mobile dongle (UK) so I could surf the net. It doesn't work. 

Does anyone know how to set up this mobile dongle and could guide me through the steps in a very basic fashion. I have seen another post on this topic (it is two years old) and assumes a much higher understanding of Ubuntu than I have currently. 

Thanks in advance!

Jay, London UK

---

### Post by a quarter past seven on 2010-11-23
this is what i did for my 3connect dongle as the software on it wouldn't install properly

1. go to network connections which probably is in the system tools part of the menu
2.there should be a tab called mobile broadband, click on it
3. on the right hand side there should be an 'add' button click on that
4.now just follow the steps its really easy its just select type of dongle which it does for you then press forward, then which country your in and then what type of data plan your on which would probably be Internet and then click apply
5. at the top of the screen there should be a symbol that looks like a v shaped made out of bracket looking things on top of each other now click on that and it should drop down and you'll see your Internet option you have just made in the earlier steps just click on that and it should connect straight away pretty much.

(whenever you switch your computer on you might have to wait a few mins for your internet option to appear, so itll look like its disappeared for a few mins so just keep checking back every min or so and it will appear on its own)

or you could try installing wine and installing your dongle that way but i thought it was to much hassle,

---

### Post by JVV on 2010-11-23
Thank you for your reply, I followed your instructions but the stick did not pop up in the network section ("V"). 

I rang the support helpline and they said i need a linux driver for HUAWEI Model: E1752Cu

Do you know where I can find this driver?

---

### Post by sanderella on 2010-11-23
T-mobile dongles only work on MS Windows and MACs. I found that out today when I received one. We need to look for dongles that work with Linux.

---

### Post by Hippytaff on 2010-11-23
> **sanderella said:**
> T-mobile dongles only work on MS Windows and MACs. I found that out today when I received one. We need to look for dongles that work with Linux.

Not necessarily, there are ways - most of the time
this thread might be useful [http://newyork.ubuntuforums.org/showthread.php?t=1598902](http://newyork.ubuntuforums.org/showthread.php?t=1598902)

If you still have not luck post back :-)

---

### Post by gandaran on 2010-11-23
> **JVV said:**
> Thank you for your reply, I followed your instructions but the stick did not pop up in the network section ("V"). 

I rang the support helpline and they said i need a linux driver for HUAWEI Model: E1752Cu

Do you know where I can find this driver?
which ubuntu version do you have? if 10.04 you will need to install usb-modeswitch from package manager.
if it doesn't work for you with network manager there other ways to make it work, one of them is the vodafone [betavine]("http://www.betavine.net/home/main/home.html") mobile connect software, this vodafone software can be used with any 3g internet operator not just vodafone but you will have to know and fill in the required connection details of your internet provider.

---

### Post by a quarter past seven on 2010-11-23
> **JVV said:**
> Thank you for your reply, I followed your instructions but the stick did not pop up in the network section ("V"). 

I rang the support helpline and they said i need a linux driver for HUAWEI Model: E1752Cu

Do you know where I can find this driver?


did you have the stick in when you followed my instructions?

im not sure why it isnt working for you, you could always try creating a second plan and then see if that comes up on the v drop down menu, i dont know why it didnt appear though sorry,

---

### Post by radiosgalore on 2011-10-04
well i had to google as i have the same issue and no these options to not work. I was able to set the network selection and rang t-mobile for the technical details and although the first time i rang i spoke to a guy who had used it on ubuntu the second time they swore it was not supported. I grow very tired of seeing the constant red flashing light to say there is an issue when there does not appear to be. This is quite urgent as this dongle will be my only source of internet in 2 days maximum

---

### Post by little_penguin on 2012-05-26
Try the following settings in the Network Manager mobile broadband setup:

Username = user
Password = pass
APN = general.t-mobile.uk

These settings work for my t-mobile usb broadband stick. Hopefully they might work for yours too.

---

### Post by uRock on 2012-05-26
Necromancy

Thread Closed

---

