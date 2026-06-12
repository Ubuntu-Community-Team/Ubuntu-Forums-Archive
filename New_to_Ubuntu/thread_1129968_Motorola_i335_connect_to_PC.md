---
title: "Motorola i335 connect to PC?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by frimilden on 2009-04-19
Hi there and thanks for the help in advance. I just bought a Motorola i335 cell phone and am having trouble getting it to show up when I connect it to my PC VIA the USB data cable. It does nothing, I assume it should mount and show up as USB storage or similar? Any help is appreciated.

Running Ubuntu 8.10 if you need additional info please let me know. :popcorn:

---

### Post by halitech on 2009-04-19
first check and see if it is seen when you plug it in. open a terminal and post the putput of
```
lsusb
```
does the phone have a connection mode? you might need to set that to usb first.

---

### Post by frimilden on 2009-04-19
> **halitech said:**
> first check and see if it is seen when you plug it in. open a terminal and post the putput of
```
lsusb
```
does the phone have a connection mode? you might need to set that to usb first.

Thank you for the swift reply it is appreciated. :KS

Here is the outpout of 'lsusb' (seems to be detected)

```
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 062a:0003 Creative Labs 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 005: ID 0c44:0020 Motorola iDEN** 
Bus 003 Device 004: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

As for connection mode, no it does not to the best of my knowledge have this, at least I cannot find it...have scoured the inetz, manual, and phone itself. 

It seems to be a driver issue from what I can gather. So I am hoping you fine folks can help me figure this one out and I am sure many more will surely appreciate it as well. 

Also I have 'Moto4lin' installed and here is the output after I switch two P2K Mode (no other mode show any success) it seems to connect but does not list anything nor let me do anything :/

> [info] Phone is unpluged. Please connect it
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 
[info] Phone answer: OK 

Thanks again in advance for the help!!

---

### Post by halitech on 2009-04-20
I've got the Razr v3 and I've never had much success getting moto4lin or anything to work. the line about phone is unplugged doesnt look good. was it unplugged at that point and then you plugged it in?

---

### Post by frimilden on 2009-04-20
> **halitech said:**
> I've got the Razr v3 and I've never had much success getting moto4lin or anything to work. the line about phone is unplugged doesnt look good. was it unplugged at that point and then you plugged it in?

No it was plugged in. I have been trying everything I can think of and no dice. I am begging to think maybe the phone is to new and there simply is no way of connecting it. :(

---

### Post by halitech on 2009-04-20
that is a possibility if its new. I'm not sure but there might be info you can send to the developer of moto4lin that may help them out in supporting your phone. See if there is someway of contacting them in the software if you are interested in helping out that way.

---

### Post by frimilden on 2009-04-20
> **halitech said:**
> that is a possibility if its new. I'm not sure but there might be info you can send to the developer of moto4lin that may help them out in supporting your phone. See if there is someway of contacting 
them in the software if you are interested in helping out that way.

Yes I will do just that. Thank you for all of your help. :popcorn:

---

### Post by frimilden on 2009-06-25
Thought I would bump this old thread to let all you fine folks know that as of yet there is still no way that I have been able to find to get this working. :( 

Maybe in the future.....

---

### Post by halitech on 2009-06-28
I still haven't been able to get anything to connect to mine either. I did recently pick up a micro-sd card for storage in the phone and now when connecting to the computer, it does see the card and the folders inside and allow me to copy files to it. Not sure if this is any help or not but thought I'd mention it.

---

### Post by DPJ93 on 2009-06-28
I know this message might not fit in here, but.. I've used my cell phone to connect to the internet, and so has my brother. And my brother got an unexpected bill on almost 1400 $. So at least you shouldn't use it a lot unless you absolutely have to. Hey, why not buy mobile 3G broadband instead? :)

---

### Post by halitech on 2009-06-28
well, not sure about the OP but I want to connect to my phone to get pictures off, load ringtones to it and things of that nature, not actually use it to connect to the net.

---

### Post by DPJ93 on 2009-06-28
Oh. I misunderstood. Sorry. Doesn't it work using bluetooth?

---

### Post by halitech on 2009-06-28
it might but I don't have bluetooth on my desktop

---

### Post by frimilden on 2009-07-22
I am not looking to get it to act as a modem to get on the netz. I just want to be able to add ringtones, etc.... And still to this day I have not come up with any way of getting this thing mounted.:(

Plain and simple it is a drivers issue and until there is a driver made for it I am SOL

---

### Post by MADinMelbourne on 2009-07-24
Hi, I'm very very new here, so thanks in advance for your patience.  I followed the thread to check if the usb is connected and it doesn't look like it is.  What do I do next?  Thanks in advance.:confused:

---

### Post by amx401 on 2011-03-14
I'm having something of the same issue.  moto4lin doesn't accept that the phone is connected, but it shows up via lsusb.  Also, it shows up in my network connections as  New Mobile Broadband (GSM) connection. . . but I don't have the ASN for it.  

I would like to put pictures and such on here, but cannot find it, and am not sure how to mount it.  I've checked /media, /dev/usb and am drawing a blank.

If anyone can either help me with mounting (if that's even what I have to do to get data back and forth) or the Access Point Name (APN) I would greatly appreciate it.

Thanks.

---

### Post by tigron on 2011-04-22
I've been trying to figure this out as well. I have been able to connect using the bluetooth but not sure how to get the DUN working without using the GSM connection until I can find the APN info. Any info would help

---

