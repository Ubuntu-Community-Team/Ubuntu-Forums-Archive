---
title: "net connection through USB"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by paulthomas07 on 2010-06-05
I recently installed Ubuntu 10.04 on my old desktop machine, the machine specifications are given below


[LIST=1]
[*]processor AMD ATHLONL XP
[*]motherboard A7V8X-MX SE
[*]Chipset VIA KM400
[*]Memory 256
[*]integrated VIA UniChrome Graphics
[/LIST]
first i encountered problem with the graphics driver as i was not able to get the right one for my system and i searched through the net and installed some and when restarted i was unable to boot to ubuntu 
Then i reinstalled ubuntu on my machine and this time some how the graphics went ok and i am not able to connect to internet.
I use USB port to connect to internet as my network card was not working and i dont know how to fix it 
Can somebody please help me to access the net as i am a new bee to ubuntu i totally relly on online helps and forums

---

### Post by lkraemer on 2010-06-05
You really should add more memory to get 512 or 1 Gig versus 256.....

Then, if I understand your question correctly, you want to use the
Ethernet port built into your Motherboard versus the USB Dongle you
are currently using to have access to the Internet.

Post the output of the following commands from a Terminal Window:
```

lspci
lsusb
lshw -C network
lsmod
iwconfig

```

Someone will respond....

lk

---

### Post by paulthomas07 on 2010-06-05
i dont want to access net thorough the ethernet port instead i wuld like to access it through my USB port so pls help in doing that as i was getting it before

---

### Post by gandaran on 2010-06-05
> **paulthomas07 said:**
> i dont want to access net thorough the ethernet port instead i wuld like to access it through my USB port so pls help in doing that as i was getting it before
and what type? mobile broadband, cable or dial-up?
modem brand?

---

### Post by paulthomas07 on 2010-06-05
i am using BSNL broadband (cable)

---

### Post by gandaran on 2010-06-05
have you tried setting up your modem to connect the the internet? or your modem does not support this? if it does you just insert the usb cable to the computer and should connect to the internet without doing anything on your computer.
well if it doesn't work that way then open the network manager go to the dsl tab and setup the connection there, you will need to enter some details like the username and password, thats about all, you fill in the correct details and the computer will do the internet connection.

or try this method it's easier
type in terminal
*sudo pppoeconf*

---

### Post by dineshs on 2010-06-05
I suggest you buy an ethernet card to connect your DSL modem

---

