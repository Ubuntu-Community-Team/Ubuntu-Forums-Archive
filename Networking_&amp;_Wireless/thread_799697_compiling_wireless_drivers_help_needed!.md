---
title: "compiling wireless drivers help needed!"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by tupactim on 2008-05-19
ok so for the past two days i have been trying to set up ubuntu on my desktop, (it runs fine on my laptop why cant it on my desktop?)
anyway i have a list of problems that need fixing, but the most important thing is getting my wireless usb stick working so i can connect to the internet,

I have tried using ndisgtk and that worked after hours of messing around, but that was on hardy and hardy doesn't like nVidia cards very much, i kept getting "out of range" every time i booted up, so im on gusty (7.10) now, and guess what ndisgtk doesn't work!(but out of range message has gone)

But i did get linux drivers on the cd that came with my usb stick and well i cant make any sense of what im to do, the instructions are not ubuntu specific and ubuntu is the only linux i no so if you could help me by telling me what to do inside of ubuntu and get my internet back on my main desktop it would be much appreciated thanks,

The drivers are attached below,

---

### Post by chili555 on 2008-05-19
In the README it says, in part: > SHANTOU Semiconductor Inc.				05/16/2003This driver is five years old! In Linux years, that's ancient history. That's like trying to fit the carburetor from your 1939 Dodge on to your 2008 Viper. It seems like, with a ton of work, it might work, but it never will.

Can we try to fine tune your ndiswrapper install or can you look for a better driver?

In your search, you might look right here:```
chili@LAPTOP60:~$ locate dm9601
/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/dm9601.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/dm9601.ko
```Did you have any luck with the built-in driver?

---

### Post by tupactim on 2008-05-19
> **chili555 said:**
> In the README it says, in part: This driver is five years old! In Linux years, that's ancient history. That's like trying to fit the carburetor from your 1939 Dodge on to your 2008 Viper. It seems like, with a ton of work, it might work, but it never will.

Can we try to fine tune your ndiswrapper install or can you look for a better driver?

In your search, you might look right here:```
chili@LAPTOP60:~$ locate dm9601
/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/dm9601.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/dm9601.ko
```Did you have any luck with the built-in driver?

Would there be no chance of an updated version of this driver? and what am i searching for? sorry i just don't get that bit lol, and no i had no luck with the built in driver :( thanks for the help,

---

### Post by tupactim on 2008-05-19
With ndiswrapper it just says invalid driver for all the windows drivers that are on the disk, but yesterday it didnt say that it said hardware found- yes, or something similar,

edit: yesterday i was using hardy

---

### Post by chili555 on 2008-05-19
I don't think anyone is working very hard on developing the driver, since it has been added to the kernel. I assume a subset of the kernel developers team have this under maintenance.

What was your experience with the built-in? Did you get it loaded and working? If you do:```
sudo rmmod -f ndiswrapper
sudo modprobe dm9601 usbnet mii usbcore
```Does you device spring to life? In or out of range?

---

### Post by tupactim on 2008-05-19
> **chili555 said:**
> I don't think anyone is working very hard on developing the driver, since it has been added to the kernel. I assume a subset of the kernel developers team have this under maintenance.

What was your experience with the built-in? Did you get it loaded and working? If you do:```
sudo rmmod -f ndiswrapper
sudo modprobe dm9601 usbnet mii usbcore
```Does you device spring to life? In or out of range?

No? instead i get whats below,

> tim@tim-desktop:~$ sudo rmmod -f ndiswrapper
ERROR: Removing 'ndiswrapper': No such file or directory

tim@tim-desktop:~$ sudo modprobe dm9601 usbnet mii usbcoreWARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with '&#8220;blacklist'
FATAL: Error inserting dm9601 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/dm9601.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by tupactim on 2008-05-19
any ideas?

---

### Post by chili555 on 2008-05-19
> **tupactim said:**
> any ideas?Sure. Let's take a look at */etc/modprobe.d/blacklist* and see what it doesn't like about line 27. Also, as suggested, let's see:```
dmesg | grep dm9
```Then we can troubleshoot.

---

### Post by tupactim on 2008-05-19
dmesg | grep dm9 gives below

> [  669.213801] dm9601: Unknown parameter `usbnet'

and line 27 on the blacklist is below,
> 
&#8220;blacklist ath_pci&#8221;

I have updated ndiswrapper to hardy's version on gusty and now it says its found hardware but the usb wireless stick still isnt working, it flashes a few times then stops but the light should stay on and go red when connected,,

Thanks for all your help so far.

---

### Post by chili555 on 2008-05-19
If the line in */etc/modprobe.d/blacklist* is really in quotes, I'd suggest you *sudo gedit /etc/modprobe.d/blacklist* and remove the quotes. Save and close. I don't think ath_pci really affects you, but there is no reason to have an easily fixable line keep throwing out error messages.

Next, I need some help from you. Are we trying to get the native driver working or fine-tune your ndiswrapper install? I felt like we were making progress on the native front and now I read that you have updated ndiswrapper. Am I trying to hit a moving target?

I am very happy, anxious even, to help you get going, but it's easier to pursue one course of action to a conclusion, either positive or negative, before we jump ship.

I actually wonder if you have a Network Manager issue. A lot of people here, it seems, have a wireless device working well, click the NM icon, make a transposition in the ESSID or encryption and can't connect. A lot of them then look for a different driver, install it and it still won't work. Call it a hunch, but your symptom:> it flashes a few times then stops but the light should stay on and go red when connectedsounds like an NM issue to me.

Please let me know what you'd prefer to do and we'll proceed.

---

### Post by tupactim on 2008-05-19
> **chili555 said:**
> If the line in */etc/modprobe.d/blacklist* is really in quotes, I'd suggest you *sudo gedit /etc/modprobe.d/blacklist* and remove the quotes. Save and close. I don't think ath_pci really affects you, but there is no reason to have an easily fixable line keep throwing out error messages.

Next, I need some help from you. Are we trying to get the native driver working or fine-tune your ndiswrapper install? I felt like we were making progress on the native front and now I read that you have updated ndiswrapper. Am I trying to hit a moving target?

I am very happy, anxious even, to help you get going, but it's easier to pursue one course of action to a conclusion, either positive or negative, before we jump ship.

I actually wonder if you have a Network Manager issue. A lot of people here, it seems, have a wireless device working well, click the NM icon, make a transposition in the ESSID or encryption and can't connect. A lot of them then look for a different driver, install it and it still won't work. Call it a hunch, but your symptom:sounds like an NM issue to me.

Please let me know what you'd prefer to do and we'll proceed.

I have already done *sudo gedit /etc/modprobe.d/blacklist* and removed the line and now i just realized i only updated the gui front end and not the ndiswrapper scripts so im going to go get the hardy scripts and try them, after all it did work yesterday after some time, so i may as well go try that, thanks for all the help so far and i will post back and let you no how things go.

---

### Post by tupactim on 2008-05-21
yeah i have given up on ubuntu for my desktop, it works fine on my laptop so i will keep using that until i get some money toghether for a wireless card that works with ubuntu out of the box, thanks for all the help chili555.

---

