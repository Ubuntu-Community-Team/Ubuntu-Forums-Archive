---
title: "ubuntu, skype and a binatone cordless usb phone"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by techno-mole on 2009-01-16
i have bought a binatone cordless usb phone, its a dual phone, meaning it can be used on the pc or as a landline phone.

ive installed skype for linux, no errors and seems to be working fine, but i cant seem to get the phone to work, i also have a tesco internet phone account, but more often than not it drops calls, the people at the other end cant hear anything, or very little, ive been running it through kiax, and if im honest it actually runs better on linux than it does windows, really sucky on windows for want of a better expression.

as far as i can tell the system is detecting the phone, i have different sound options when i go to --> system --> preferences --> sound, there are the normal options, alsa, oss etc but once i connected the phone i now have " innoMax Technology Ltd, Cordless USB Phone USB Audio (ALSA) " there is an oss option as well.

i have tried clicking the test sound button, but im not getting any sound out of the phone, equally when i try using skype the phone makes no sounds.

so basically im looking for any help with getting it working, i have very little experience with internet phones, skype etc etc so any help would be handy.

im running 64 bit ubuntu intrepid (maybe this is the problem ?) the phone is a binatone s1545 dual function cordless telephone & skype phone.
 i downloaded and installed skype for linux with no problems, and as far as i can tell its working okay.

cheers

---

### Post by compiledkernel on 2009-01-16
I have had very hit or miss luck with corded USB phones and skype on an Ubuntu install. I almost dont recommend doing it, because of those issues. 

First thing would be to see if the system is actually seeing the device. 

What does the command lsusb tell you?

---

### Post by techno-mole on 2009-01-16
well im currently debating what to do about the phone, it wouldnt be run on my system, at the moment we have a file server of sorts, and the internet phone (tesco internet phone) is connected to that, its running kubuntu, but i have to rebuild it (upgrade) so i wondered whether to install windows on it, and then run the phone of it again like that, not sure, i guess if i cant get it working then i will.

as for running lsusb (i did this when i first plugged it in, sorry should have mentioned it)

lsusb - 

Bus 003 Device 008: ID 19af:694d S Life <-----this is the usb phone
Bus 003 Device 006: ID 050d:016a Belkin Components 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 002: ID 0dda:2026 Integrated Circuit Solution, Inc. USB2.0 Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

it doesnt really say much about it, which is a little concerning ?

---

### Post by unknown user on 2009-01-22
Hi techno-mole, I too am having a lot of issues with internet phones and setting up the tesco phone on ubunto. From what I can see there is very little help on this and some people have said that it is best to have a duel boot with windows and use the internet phone on that only.
Have you tried installing the setup disk that you had with the tesco phone via wine? I have done that and it works OK and you can access your account details and contacts. However, I too am unable to hear any sound through the handset and when I call a number like my land line, it rings all OK but when the call connects the usb phone dies.
Have a look on the internet for a site by John Hunt as he wrote that he got his tesco phone working all OK on Ubuntu, but I have not been able to follow it. Did you get kiax to access your tesco account all OK?

---

### Post by unknown user on 2009-01-22
Just found the link I mentioned, it may be of use to you:

[http://john-hunt.com/2007/01/04/tesco-internet-phone-for-linux/](http://john-hunt.com/2007/01/04/tesco-internet-phone-for-linux/)

[http://john-hunt.com/2006/08/29/voip-best-sip-provider-overall-solution/](http://john-hunt.com/2006/08/29/voip-best-sip-provider-overall-solution/)

Hope this is of help to you.
If you get it working please share the secrets as it is driving me mad :D

---

### Post by johncop on 2009-08-28
did any of you managed to make the phone ring in ubuntu?
ps: i`m have a s1085 on ubuntu 9.04

---

