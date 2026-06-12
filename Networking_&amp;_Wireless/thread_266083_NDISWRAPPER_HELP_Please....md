---
title: "NDISWRAPPER HELP Please..."
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by knichel on 2006-09-26
I have been reading and re reading anything I can find on getting a USB Wireless Adapter (Linksys WUSB54GSC) to work.

I installed ndiswrapper and ndiswrapper-utils (several times).  When I try...

knichel@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
wusb54gsc       invalid driver!

I got the driver off of the disk that came with the card as the directions said. 

Is there anybody that can help me or can you suggest a USB Dongle that works with Ubuntu?

--
Mike

---

### Post by danish_demon on 2006-10-13
i bought this stupid wireless card tonight after looking at the list of supported usb dongles and (stupidly) assuming this one would work because the basic wusb54gs ones do work well apparently.   

to solve your problem, you need to look here:
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

that will at least get it to say that it is installed correctly (at least i was able to), but it still doesn't work (the light never goes on and when i try to do a command like:

sudo ndiswrapper -d XXXX:XXXX wusbg54sc

i get an error about the driver not being installed correctly.  basically, i think we are s.o.l. and need to find another card to try.  dealing with this card almost makes me look back wistfully on the days when i tried to get my dwl-g122 usb wireless dongle to work (it crapped out on me today so that's why i got a new one).

back to best buy tomorrow for me, i believe....

---

### Post by pjbgravely on 2006-10-21
You need to look in the ndiswrapper wiki.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page")
They have links to drivers that have worked for them. Sometimes you need to try many diffrent versions of the Windows xp drivers to find one that works. 

Paul

---

### Post by MalaX3 on 2006-10-30
can't for the life of me get ndiswrapper 1.8 to say anything but invalid driver. tried this thread and several others with no success. any pointers?](*,) 

Dongle: WUSB54GSC
Ndis ver: 1.8

NOTE: The compiuter this is being installed on has ABSOLUTELY NO INTERNET until i get ndis working. i have a 128mb flash drive but there are no free hardwire ports on the router and its in a room thats inaccessable to me anyways. my laptop has wifi capabilities so if theres something i need to download let me know... in the mean time im limited to the dapper cd i have and this flash drive.......](*,) 

thanks for the help everyone.

---

### Post by MalaX3 on 2006-10-31
alright i got ndiswrapper to recognize the driver... but now my system fails to load at the "Configuring Network Interfaces..." portion of the Ubuntu boot screen so long as my WUSB54GSC Wireless dongle is plugged in... any guesses? The wireless requires WEP 128bit and I know for fact i haven't set it up yet since i just got the drivers working

---

### Post by pjbgravely on 2006-11-01
Ndiswrapper causes problems at boot if the device isn't configured. Just plug it in after booting and then configure in system/administration/networking. WEP is a pain sometimes, I usually type in the hex code instead of the passphrase. Networkmanger does a better job, and you can install that after you get it connected. You will have to disable all devices in Networking if you want to use networkmanager after installing it.

Paul

---

### Post by MalaX3 on 2006-11-02
yes but now upon reboot when i try to use the ndiswrapper -l command the first time when the device isnt connected it says driver found, however if i attach the device and use the same command it thinks for a while and then freezes the prompt. requiring me to force quit the gnome-terminal application. it does the same thing in the TTY prompts only then i ahve to swap promtps or reset.
another problem i'm having is that even after i got it working in ndiswrapper it doesn't show up in /system/administration/networking at all. any ideas? i mean considering i havent spent all sorts of time configureing this installation i'm open to any sudgestions including reformat/reinstall. however thats a last resort, as i'd much rather fix the existing installation if possible. plus its better to learn the give up and start all over

---

### Post by bjd on 2006-11-02
I've been working on a driver for my US Robotics MAXg usb wlan adapter for the past few weeks and have that one in a reasonable working state. 

Judging from the windows drivers these Linksys WUSB54GS/GSC usb adapters
seem more or less the same as my US Robotics, so it may also work with
my driver (same goes for other devices using rndismp.sys and usb8023.sys under windows).

It's still a very experimental driver, but if your willing to try it, look here: [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

---

### Post by pjbgravely on 2006-11-02
MalaX3,

 Are you remembering to depmod -a and if no errors modprobe ndiswrapper? Just installing the windows driver doesn't get it started. If you have done that check the type dmesg and check for the device at the end on the output. You can also  tail -f var/log/messages to see in real time what is happening. As soon as you modprobe the device should start blinking.

If all works well than you should see the device in Networking. Make sure ndiswrapper is in the file /etc/modules, and not add it. The the device should automatically come up when it is plugged in. 

If none of this helps then I still don't see a need to clean reinstall, unless you have made a lot of changes trying to get this to work. If it still doesn't work then it probably still has the wrong windows driver. If so see if ndisgtk is on the disc, and if so install it. It will install and modprobe Ndiswrapper with a GUI. Once installed it will be in system/administration/

Paul

---

### Post by MalaX3 on 2006-11-04
did the depmod -a command worked fine. proceeded to modprobe ndiswrapper and it worked fine. but the device still isnt blinking and i can't get ndiswrapper -l to work still. the device still isnt showing up in networking either. i tried to cd to /etc/modules and it says Not a Directory

any other sudgestions?

P.S. the device driver is the one off the CD. and the only files in /etc/ndiswrapper/wusb54gsc are rndismp.sys, usb8023.sys, and wusb54gsc.inf

---

### Post by pjbgravely on 2006-11-04
There doesn't seem to be anyone using your dongle with ndiswrapper. You should try the driver that BJD linked too and see if that works. The drivers off the CD usually don't work. When you get this working post the instructions on the ndiswrapper so others can be helped. It will probably be just trial an error. Maybe you can get a USB LAN dongle so you can do the work online.

Paul

---

### Post by MalaX3 on 2006-11-05
i don't know if i mentioned it or not earlier but the LAN ports are full and in a room i don't have access too. i am considering hsaring my laptops wireless though

---

### Post by mavr on 2006-11-05
i had troubles, my ndiswrapper was working properly but i couldn't get my wlan usb light to blink. I followed the advice to reboot without the usb connected and then when i connected it all worked. Try it too people. It seems like ndiwsrapper didn't load properly at boot if the usb was connected.  Thanks to everybody for the help

---

### Post by MalaX3 on 2006-11-06
> **mavr said:**
> i had troubles, my ndiswrapper was working properly but i couldn't get my wlan usb light to blink. I followed the advice to reboot without the usb connected and then when i connected it all worked. Try it too people. It seems like ndiwsrapper didn't load properly at boot if the usb was connected.  Thanks to everybody for the help
so yeah, i tried the reboot thing.. tried that awhile ago. still working on the issue at hand.. while i gotta say thanks for the advice i already heard that on page one about a week ago. anyone thats got ideas let me know. but until then its trial and error till i get it to work... when i do ill make a new post with the instructions though

---

### Post by MalaX3 on 2006-11-08
***Bumps***

---

### Post by pjbgravely on 2006-11-10
Sorry, I forgot you didn't have LAN. You are correct, this is an untested device in Ndiswrapper, and you might be the first one to get it going. Post to the Ndiswrapper wiki also when you have success.

Here is a site that might help you find other drivers that might work.

[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")
All I can find on your device is how the windows driver messes up fast user switching on windows. That tells me the xp driver is junk. The chipset was used in may other devices, it even has an Linux driver but that driver doesn't work for USB. 

Paul

---

### Post by MalaX3 on 2006-12-31
**Bumps**

---

