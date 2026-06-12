---
title: "Finally able to install Ubuntu, need help getting started"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by bjnueva8623 on 2009-02-08
First of all, I'm a complete Linux/Ubuntu noob. First time ever with the OS but I am definitely ready to switch over. 

After struggling immensely to install Ubuntu, I was finally able to get it done last night, but a host of new problems arose. It seems that the only thing I can do is play the pre-installed games. I tried to install the NVIDIA driver's to allow better visual effects, but all that happens is a graphic pops up of the driver trying to download, although it never goes over 0%. The graphic then quickly disappears without any "changes applied" message popping up. instead I get a "changes couldn't be made" or something to that effect. I'm guessing I need to have internet access to install anything? 

I tried installing Linksys wireless internet (WUSB5GC). Ubuntu seemed to recognize the installation CD, but it could not run. I got a "autorun program could not be found" error message.

---

### Post by SuperSonic4 on 2009-02-08
try pressing ctrl+alt+F1 to drop into a console and then doing ```
sudo apt-get install nvidia-glx-177
``` to install the driver

---

### Post by LostMagix on 2009-02-08
Ubuntu is very depended on the internet, so the first thing you will want to do is find a hard line to install your wireless driver.

---

### Post by LostMagix on 2009-02-08
Under system/admin/hardware drivers/ do you have anything for your wireless card?

---

### Post by bjnueva8623 on 2009-02-08
Thanks for the replies guys. 

I'll try the ctrl+alt+F1 later. Hope it works. 

> Ubuntu is very depended on the internet, so the first thing you will want to do is find a hard line to install your wireless driver.

Any way to get my wireless usb adapter working? Thats the only source of Internet I have at the moment.

---

### Post by LostMagix on 2009-02-08
> **bjnueva8623 said:**
> 
Any way to get my wireless usb adapter working? Thats the only source of Internet I have at the moment.

You could look up the package for your particular usb wireless adapter and then transfer it to your laptop with a flash drive or something.

If you post your USB wireless adapter I will help you look for the right package.

---

### Post by bjnueva8623 on 2009-02-08
> **LostMagix said:**
> You could look up the package for your particular usb wireless adapter and then transfer it to your laptop with a flash drive or something.

If you post your USB wireless adapter I will help you look for the right package.

I have a Linksys Compact Wireless-G USB Adapter (WUSB54GC). 

[http://shopping.msn.com/prices/linksys-compact-wireless-g-usb-adapter-wusb54gc-network-adapter/itemid572657599/?itemtext=itemname:linksys-compact-wireless-g-usb-adapter-wusb54gc-network-adapter](http://shopping.msn.com/prices/linksys-compact-wireless-g-usb-adapter-wusb54gc-network-adapter/itemid572657599/?itemtext=itemname:linksys-compact-wireless-g-usb-adapter-wusb54gc-network-adapter)

Thanks a lot, man.

---

### Post by Osamabingandhi on 2009-02-08
Don't think you need to install any drivers for you wireless network card. It is mostly fixed in the new ubuntu. But if you can write online can't you connect the computer you're trying to fix onto that connection?

---

### Post by bjnueva8623 on 2009-02-08
> **Osamabingandhi said:**
> Don't think you need to install any drivers for you wireless network card. It is mostly fixed in the new ubuntu. But if you can write online can't you connect the computer you're trying to fix onto that connection?

I'm actually using a different PC at the moment, lol. Can't go online at all on the one I have Ubuntu installed on.

---

### Post by Osamabingandhi on 2009-02-08
Ok, how do you try to connect to the internet with the ubuntu computer? Can't you do the same as you do with the other one? You need to get network access before you can do anything with ubuntu....

---

### Post by bjnueva8623 on 2009-02-08
> **Osamabingandhi said:**
> Ok, how do you try to connect to the internet with the ubuntu computer? Can't you do the same as you do with the other one? You need to get network access before you can do anything with ubuntu....

That's what I'm trying to find out. With XP, you can just install the program from a CD and in some cases just connect the Wireless Adapter into the USB port and surf the web in a matter of minutes. I'm not sure how to do it in Ubuntu. I tried to install the program just like you do with Windows, but it didn't want to run.

---

### Post by Osamabingandhi on 2009-02-08
ok you have a dongle that you connect with usb....No the installation don't work in linux it's made for windows. The support for linux is pretty bad when it comes to such things. But if you have the usb network card and start the computer with that in ubuntu hopefully will fix all the drivers for you....Lately most such things work.

Search on google on your dongle name and ubuntu and see what comes up. If it is working you should be able to press on the little network thingy on the panel right now i should be red-crossed

---

### Post by Osamabingandhi on 2009-02-08
you need to connect the usb-thingy and restart your computer and see if it makes any difference

---

### Post by bjnueva8623 on 2009-02-08
Thanks for the help, Osama. 

I Google'd what you told me and got some good although confusing and complex results (for a noob). Found something about rt2x00 drivers and ndiswrapper. I'll try those and also try connecting the adapter and restarting the computer. Hope it works. Thanks again.

---

### Post by Osamabingandhi on 2009-02-08
The ndiswrapper drivers you can install through synaptics. But then ofcourse you need an internet connection. The problem with linux that you can't just take a driver or program and put on a usb-drive or cd and then install it on another computer....

So you can not use a network-cable to plug it into a router or the internet connection? You only have wireless internet, is it 3G?

---

### Post by Osamabingandhi on 2009-02-08
that wasn't the whole truth, you can if you get the right installation file for ubuntu you can start it in and get it to install. Don't know if there is a resource on the internet where you can download ubuntu software and drivers....

---

### Post by Osamabingandhi on 2009-02-08
Also you have installed the normal version aka. 32-bit. The 64-bit has some more problems with drivers for hardware.

---

### Post by Osamabingandhi on 2009-02-08
I found [www.getdeb.net](www.getdeb.net) where you can search and download ubuntu software. If you find a driver that your usb-network need try to find it there and save it on a cd or such and then you just need to open the file with debi-istaller or such and it will install it for you

---

### Post by bjnueva8623 on 2009-02-08
Yeah I installed the 32-bit version and yes, unfortunately, the only source of internet I have at the moment is wireless. I'll try to search for the right installation file so that I can use a flash drive. Thats probably my best bet to get the wireless adaptor working.

---

### Post by bjnueva8623 on 2009-02-08
> **Osamabingandhi said:**
> I found [www.getdeb.net](www.getdeb.net) where you can search and download ubuntu software. If you find a driver that your usb-network need try to find it there and save it on a cd or such and then you just need to open the file with debi-istaller or such and it will install it for you

Thanks a lot. I'll try looking for the right driver. :)

---

### Post by Temposs on 2009-02-08
There is also the complete package library here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can look up any package that you can find on synaptic and download it manually.

---

### Post by Osamabingandhi on 2009-02-08
exactly what is the name of the usb wireless adaptor. the rt2x00 seems to be intergrated into linux...and should work out of the box

---

### Post by Osamabingandhi on 2009-02-08
i don't think you have to install any driver it should work....just start the computer with the thing plugged in. If your other computer work try that usb and see if there is any difference.

---

### Post by bjnueva8623 on 2009-02-08
> **Osamabingandhi said:**
> exactly what is the name of the usb wireless adaptor. the rt2x00 seems to be intergrated into linux...and should work out of the box

Linksys Compact Wireless-G USB Adapter (WUSB54GC).

---

### Post by bjnueva8623 on 2009-02-08
> **Temposs said:**
> There is also the complete package library here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can look up any package that you can find on synaptic and download it manually.

I've tried doing it but apparently I need access to the web before I am able to install anything from synaptic. I even tried installing other programs like Compiz but nothing was clickable.

---

### Post by Osamabingandhi on 2009-02-08
it should work....from what i can see

try to follow this guide: 

[http://ubuntuforums.org/showthread.php?t=885847&highlight=rt2x00](http://ubuntuforums.org/showthread.php?t=885847&highlight=rt2x00)

You need to start the terminal to be able to write commands.

---

### Post by bjnueva8623 on 2009-02-08
Osama, I found a program called Wine on the website you listed. It supposedly has a program loader that allows Windows programs to run.

---

### Post by Osamabingandhi on 2009-02-08
what i read it works but you need to set it up with the network manager somewhere under system and administration

---

### Post by Osamabingandhi on 2009-02-08
wine is the last resort mostly when you can't find it in ubuntu. If you have restarted the laptop with the usb plugged in you should be able to get the network to start working by going to the network manager

---

### Post by Osamabingandhi on 2009-02-08
network configuration i think the name is under system settings. there you need to put your settings

---

### Post by Osamabingandhi on 2009-02-08
Any luck?

---

### Post by bjnueva8623 on 2009-02-08
Sorry, I was taking notes and printing out that ndiswrapper guide. I only have one Wireless Adapter so I need to log out and use it for my other PC. I'll let you know what happens Tomorrow morning. Thanks for the help. Really appreciate it.

---

### Post by Osamabingandhi on 2009-02-08
Ok, but do the ndiswrapper thingy last, you should not need to mess around with that. Here is a good start:

[https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html)
Under wireless there should be some hint of how to get internet to work

then look and read a little bit on:
[https://help.ubuntu.com/8.10/index.html](https://help.ubuntu.com/8.10/index.html)
good basic stuff

Good luck and good night.

---

### Post by bjnueva8623 on 2009-02-09
](*,)I feel like kicking myself. After all this, the easiest way was to simply have the adapter plugged in before the computer started up (just like you said on the first page, lol). As soon as I got to my desktop, I was connected (well, after typing in the password of course). Thanks for all your help, Osama.:)

---

### Post by Osamabingandhi on 2009-02-10
You know the story about two computergeeks who are driving a car and it brakes down. They sit and look at another and concludes that the best way to fix the problem is to step out of the car and then get back in! I thought that was the problem for you. Good thing you got it going! 

Most things in ubuntu works pretty much without much problems. A lot easier than windows in many ways, sometimes too easy. The only weakside is when you start messing with a couple of computers an want to network with windowsmachines and such. The more advanced it gets it's a little harder. But when you just use as a "normal" computer user most things works very nicely.

Hope you'll like ubuntu as much as i do! And you're welcome.

---

