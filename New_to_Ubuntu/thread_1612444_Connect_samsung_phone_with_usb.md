---
title: "Connect samsung phone with usb ?"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Cha0sBG on 2010-11-03
Alright , i wanna ask how to connect to my phone's mass storage from my machine via USB cable. I select mass storage from my phone ( samsung soul ) and the folder appears for a little while , but it desapears in 2 secs . Any suggestions ? :)

---

### Post by Hippytaff on 2010-11-03
Have you got an SD card in the phone...mass storage only works if thisis the case. (as I found out to my annoyance)
 
[http://ubuntuforums.org/showthread.php?t=1611266&highlight=hippytaff+windows](http://ubuntuforums.org/showthread.php?t=1611266&highlight=hippytaff+windows)

---

### Post by Cha0sBG on 2010-11-03
yeah i do have a microSD card in the phone at the moment

---

### Post by Cha0sBG on 2010-11-03
~bumb~

And if this helps:
```
root@cha0sbg-Dev:/home/cha0sbg# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2624 Pixart Imaging, Inc. Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05c6:1000 Qualcomm, Inc. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And 1 more thing, recently when i tryed to connect to my mass storage it sayd "Unable to open MEMORYSTCIK maybe it was recently deleted, the name of the memory stick folder is &MEMORYSTICK

---

### Post by Hippytaff on 2010-11-03
Ok...so you need to look into mode_switch (if this is lsusb with the wireless usb plugged in)...ubuntu thinks its a usb storage device.

[http://manpages.ubuntu.com/manpages/maverick/en/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/usb_modeswitch.1.html)

---

### Post by Cha0sBG on 2010-11-03
i tryed 

```
usb_modeswitch -v 04e8 -p 6601
```

but the output is: No devices in default mode or class found. Nothing to do. Bye.
Any suggestions what to do now ? :/ sry for my many question, but i haven't done anything related to this topic in linux before.

---

### Post by Hippytaff on 2010-11-03
omg...sorry, I got confused between two seperate threads...was helping someone with a usb wireless dongle and got confused...

ubuntu seems to recognise your phone as mass storeage. try

```

cd /media/

```
```

ls

```

---

### Post by Cha0sBG on 2010-11-03
When i type ```
ls
``` nothing happens ... just a new line

---

### Post by Hippytaff on 2010-11-03
I had similar problems with a Samsung phone...in the end I had to use a windows machine :-)

Didn't like it but...

---

### Post by Cha0sBG on 2010-11-03
:/ guess i'll have to get my blue tooth back from my friend ... i still hope i can resolve the problem somehow

---

### Post by gandaran on 2010-11-03
try the 'bitpim' software, not sure but I think it supports samsung phones or at least some samsung models.
install from ubuntu software center or synaptic.

---

### Post by theozzlives on 2010-11-03
My old Samsung Delve worked fine in mass storage, but Samsung Phones are crap (I owned two). If you have an SD card reader on your printer or computer, and an adapter, you can read/write to your card that way.

---

### Post by Hippytaff on 2010-11-03
Hi gadran and theozzlives, thanks for you input :-)

Though I was here alone for a second

---

### Post by Hippytaff on 2010-11-03
> **Cha0sBG said:**
> :/ guess i'll have to get my blue tooth back from my friend ... i still hope i can resolve the problem somehow

You might have more luck with Bluetooth

---

### Post by leroim8 on 2012-11-05
i just reboot my phone connected with my PC

---

