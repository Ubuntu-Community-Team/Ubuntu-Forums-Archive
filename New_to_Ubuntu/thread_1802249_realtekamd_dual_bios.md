---
title: "realtek/amd dual bios"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by YellowBronco on 2011-07-11
i found a realtek RTL811B bios driver starting after the amd bios driver, 
i found this article explaining the problem , but i dont understand the solution.
[http://ubuntuforums.org/showthread.php?t=388403](http://ubuntuforums.org/showthread.php?t=388403)
I dont use realtek on any of my devices , why would i need it?
does this problem still apply in slowing down or stopping internet conectivity to ubuntu? i dont know if i need to del it or let it run with ubuntu?
thanks dan
specs

was-os vista ultimate ver 6.0.6002sp2
trying to install ubuntu 11.04 64
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors
dr A zid citizen tuv
hd B seagate st340810a 40g 
hd C crucial ssd 64g
hd E western digital 1600aajs 160g
dr q memorex 16x double layer 5395 cd-r/rw drive
dr r sony optiarc dvd rw ad-7190s ata 1.02

---

### Post by ratcheer on 2011-07-11
Isn't the Realtek your NIC? I don't understand why you would not need it.

Please post the output if: sudo lspci -v

My guess is that Ubuntu has loaded the wrong driver for your NIC.

Tim

---

### Post by YellowBronco on 2011-07-11
> **ratcheer said:**
> Isn't the Realtek your NIC? I don't understand why you would not need it.

Please post the output if: sudo lspci -v

My guess is that Ubuntu has loaded the wrong driver for your NIC.

Tim

what is " output if : sudo lspci -v " ??
how do i get it?
dan

---

### Post by thiebaude on 2011-07-11
Open a terminal and type sudo lspci -v and then you will see what the results of that command was. :)

---

### Post by ratcheer on 2011-07-11
> **YellowBronco said:**
> what is " output if : sudo lspci -v " ??
how do i get it?
dan

Sorry, it was a typo. It should have said "the output of". I admit it makes no sense the way I typed it.

Anyway, start Terminal. Type that exact command. Then copy all of the output and paste it into a new reply to this thread.

Tim

---

### Post by wildmanne39 on 2011-07-11
Hi, yes please post that information, that should be your network card if you get rid of that driver you will not be able to connect to the internet.

---

### Post by YellowBronco on 2011-07-13
i lost everything , cant boot to the output

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall   11.04, it was my own stupidity, i put a version 6 on top of 11.04. i   thought it was just info from the library , not a whole new install.   like i said^ i like ubuntu, ive been too enamored in the bill gates   world to fully get it all of ubuntu yet, i guess if u are starting out   fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,   re-installed a new os , xp not the vista stuff, had to re-find all   drivers this way and reinstall from bios, in order to do that i had to   take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

